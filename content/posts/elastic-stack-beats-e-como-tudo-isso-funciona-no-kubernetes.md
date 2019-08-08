---
type: post
title: Elastic Stack + Beats e como tudo isso funciona no Kubernetes
excerpt: O que é o Elastic Stack e o que são os Beats
authors: Gabriel Prestes
date: '2019-08-07'
publishDate: '2019-08-07'
image: 'https://tableless.com.br/images/uploads/illustration-beats-header-overflow.png'
categories:
  - >-
    tooling, front-end
tags:
  - >-
    elasticsearch
---
Começo explicando o que é o Elastic Stack e o que são os Beats, parece falar sobre mais do mesmo, mas algumas pessoas não sabem seu funcionamento real e arquitetura, e ainda que deem esse questionamento como respondido, erram principalmente na aplicação dos Beats Packages, disponibilizando-os neste mundo com IaC (InfraasCode) na mesma role e aplicando ao mesmo server de destino, o que não é conveniente, uma vez que faz mais sentido aplicar os Beats nos servers que enviarão informações ao ElasticSearch/LogStash.

Elastic Stack se entende aqui por ELK ou EFK + Beats packages. Tais nomenclaturas significam:

* **ELK:** ElasticSearch + LogStash + Kibana
* **EFK:** ElasticSearch + Fluentd + Kibana

Beats Packages:

![](/images/uploads/captura-de-tela-de-2019-06-18-19-13-41.png)

Até o momento e já exposto aqui, uma das motivações da publicação é a correta aplicação da stack + beats, ou seja, os componentes dos beats precisamos instalar no servidor ou serviço que queremos monitorar, cujo destino das métricas, logs, eventos e etc é o ELK ou EFK.  

A segunda motivação é a implantação do Filebeat no Kubernetes, o material disponível que atende em grande parte a configuração de um cluster baremetal e com a imagem da versão 6.x do Filebeat orienta a configuração de coleta por daemonset por type : log e para coletar os STDOUT e STDERR dos contêineres/pods monitoram logs dos nodos, exemplo ‘/var/lib/containers…’. O problema que me ocorreu aqui foi que o AKS (Managed Service Kubernetes da Azure) não se comportou muito bem com isso, não obtendo alguns logs de outros namespaces. 

Confesso que no momento não nos aprofundamos afundo nesse evento para descobrir uma alternativa, então foquei na versão 8.x da imagem do Filebeat e uma feature de ‘hints’ baseados em autodiscovery para o Kubernetes. 

A partir dessa feature criei uma configuração válida que atende o AKS, assim como permite através dos annotations do Kubernetes fazer o multiline por aplicação, ou até mesmo deixar uma configuração comum entre os pods caso não exista uma definida no annotations. 

Como ficou o yaml a ser aplicado via helm ou kubectl: 

```
—
apiVersion: v1
kind: ConfigMap
metadata:
  name: filebeat-config
  namespace: kube-system
  labels:
    k8s-app: filebeat
data:
  filebeat.yml: |-
    filebeat.config:
      inputs:
        # Mounted `filebeat-inputs` configmap:
        path: ${path.config}/inputs.d/*.yml
        # Reload inputs configs as they change:
        reload.enabled: false
      modules:
        path: ${path.config}/modules.d/*.yml
        # Reload module configs as they change:
        reload.enabled: false
    filebeat.autodiscover:
      providers:
        – type: kubernetes
          hints.enabled: true
          include_annotations: ‘*’
          templates:
              config:
                – type: docker
                  containers.ids:
                    – “${data.kubernetes.container.id}”
    processors:
      – add_cloud_metadata:
    cloud.id: ${ELASTIC_CLOUD_ID}
    cloud.auth: ${ELASTIC_CLOUD_AUTH}
    output.elasticsearch:
      hosts: [‘${ELASTICSEARCH_HOST:elasticsearch}:${ELASTICSEARCH_PORT:9200}’]
—
apiVersion: v1
kind: ConfigMap
metadata:
  name: filebeat-inputs
  namespace: kube-system
  labels:
    k8s-app: filebeat
data:
  kubernetes.yml: “”
—
apiVersion: extensions/v1beta1
kind: DaemonSet
metadata:
  name: filebeat
  namespace: kube-system
  labels:
    k8s-app: filebeat
spec:
  template:
    metadata:
      labels:
        k8s-app: filebeat
    spec:
      serviceAccountName: filebeat
      terminationGracePeriodSeconds: 30
      containers:
      – name: filebeat
        image: docker.elastic.co/beats/filebeat:8.0.0
        args: [
          “-c”, “/etc/filebeat.yml”,
          “-e”,
        ]
        env:
        – name: ELASTICSEARCH_HOST
          value: meuelastic.athome.org
        – name: ELASTICSEARCH_PORT
          value: “9200”
        – name: ELASTIC_CLOUD_ID
          value:
        – name: ELASTIC_CLOUD_AUTH
          value:
        securityContext:
          runAsUser: 0
        resources:
          limits:
            memory: 400Mi
          requests:
            cpu: 200m
            memory: 200Mi
        volumeMounts:
        – name: config
          mountPath: /etc/filebeat.yml
          readOnly: true
          subPath: filebeat.yml
        – name: inputs
          mountPath: /usr/share/filebeat/inputs.d
          readOnly: true
        – name: data
          mountPath: /usr/share/filebeat/data
        – name: varlibdockercontainers
          mountPath: /var/lib/docker/containers
          readOnly: true
      volumes:
      – name: config
        configMap:
          defaultMode: 0600
          name: filebeat-config
      – name: varlibdockercontainers
        hostPath:
          path: /var/lib/docker/containers
      – name: inputs
        configMap:
          defaultMode: 0600
          name: filebeat-inputs
      – name: data
        hostPath:
          path: /var/lib/filebeat-data
          type: DirectoryOrCreate
—
apiVersion: rbac.authorization.k8s.io/v1beta1
kind: ClusterRoleBinding
metadata:
  name: filebeat
subjects:
– kind: ServiceAccount
  name: filebeat
  namespace: kube-system
roleRef:
  kind: ClusterRole
  name: filebeat
  apiGroup: rbac.authorization.k8s.io
—
apiVersion: rbac.authorization.k8s.io/v1beta1
kind: ClusterRole
metadata:
  name: filebeat
  labels:
    k8s-app: filebeat
rules:
– apiGroups: [“”]
  resources:
  – namespaces
  – pods
  verbs:
  – get
  – watch
  – list
—
apiVersion: v1
kind: ServiceAccount
metadata:
  name: filebeat
  namespace: kube-system
  labels:
    k8s-app: filebeat
—
```

Para a parte de deploy dos PODs basta incluir as annotations conforme o multiline desejado:

```
apiVersion: v1
kind: Pod
metadata:
name: order-commerce-service
annotations:
 co.elastic.logs/multiline.pattern: ‘^\[‘
 co.elastic.logs/multiline.negate: true
 co.elastic.logs/multiline.match: after
```

É comum não saber qual o multiline se aplica por aplicação, para isto a Elastic disponibiliza um simulador e patterns e uma documentação bem completa, explicando comportamento de negate e match. Abaixo compartilho estes links que apoiarão o time de desenvolvimento nesse processo, ou até mesmo se quiser definir um template de config no hint do Kubernetes: 

* [Simulador](https://play.golang.org/p/uAd5XHxscu)
* [Documentação do multiline](https://www.elastic.co/guide/en/beats/filebeat/master/configuration-autodiscover-hints.html#configuration-autodiscover-hints)
* [Exemplos de multiline](https://www.elastic.co/guide/en/beats/filebeat/master/_examples_of_multiline_configuration.html)

Caso queira utilizar PacketBeat, AuditBeat, MetricBeat, ou outros no Kubernetes o processo em vias práticas é bem semelhante, com ressalva ao conteúdo e ajustes dos configmaps, daemonset e imagem utilizados. Mas não muda o cenário e nem mesmo o fluxo. 

**Gabriel Prestes**, arquiteto de middleware e cloud da ilegra com experiência de mais de 8 anos em suítes de middleware Oracle e RedHat.
