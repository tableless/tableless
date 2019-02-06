---
title: Continuous Integration & Delivery no Gitlab.com
authors: Morais Junior
type: post
image: https://about.gitlab.com/images/ci/ci-cd-test-deploy-illustration_2x.png
date: 2019-02-05
excerpt: Continuous Integration & Delivery é uma das partes mais importantes no trabalho de qualquer dev-ops. 
categories:
  - Tecnologia e Tendências
tags:
 - DevOps
 - Infra
 - Gitlab
---
# Continuous Integration & Delivery no Gitlab.com
De todas as ferramentas que trabalhei, o gitlab-ci é uma das mais simples. Basta incluir um arquivo chamado _.gitlab-ci.yml_ na raiz do repositório. Com isso, ao ter um commit ou deploy, o gitlab vai executar as tarefas descritas na sua configuração, abaixo vou explicar como configurar esse arquivo.
## Pipeline
No gitlab uma pipeline é um conjunto de tarefas e procedimentos a serem executados quando tiver alguma alteração no repositório, sejam eles, rodar o gulp, atualizar uma imagem docker, limpar um cache, fazer upload no seu bucket s3, qualquer coisa :)
## Jobs
Job é cada tarefa dentro da pipeline, essas tarefas podem ser dependentes umas das outras e chamadas quando se faz um push, via schedules,  manuais e etc. Basicamente é um container que o gitlab sobe executando uma sequência de comandos.
## Runner
Um Runner é o host onde o gitlab sobe as imagens da sua pipeline, ele já tem vários runners compartilhados de graça, mas pode incluir/registrar o seu particular.
Ex:
```python
job1:
  script: "execute-script-for-job1"

job2:
  script: "execute-script-for-job2"
```
Neste exemplo, sempre que houver um push, a pipeline vai conter essas duas jobs, simples né?

Ainda sobre jobs, podemos ter tarefas que não aparecem na pipeline, conhecidas como hidden jobs. Basta colocar um ponto no nome.
Ex:
```python
.job1:
  script: "tarefa oculta"

job2:
  script: "execute-script-for-job2"
```
Nesse exemplo o job1 não será mostrado na pipeline. (mais adiante vocês vão entender como isso ajuda nossa vida)

As *Anchors* é outro item importante das tarefas, elas são modelos de tarefas que servem como uma espécie de templates, com isso, evitar re-escrita de código.
```python
.job1: &modelo1
  key:value

job2:
	<<: *modelo1
  script: "execute-script-for-job2"
```
No exemplo acima a tarefa 2 vai herdar as configurações da tarefa que tem a âncora modelo1.

Por último, temos os stages. Stages são uma forma para controlar a sequência que as tarefas serão executadas. Ex:
```python
stages:
  - test
  - deploy
  
job1:
  stage: build
  script: "primeiro-comando"

job2:
  stage: test
  script: "comando-depois-do-primeiro"
```
No exemplo acima, as tarefas serão executadas consecutivamente. Porém, se não houver a definição de stages, as tarefas entram em paralelo. Isso torna-se ruim, pois o deploy pode terminar antes dos testes serem executados.

Após entender estes conceitos, podemos entrar nos detalhes sobre a criação de uma tarefa no gitlab:
## script
Nessa configuração vão os comandos que precisam ser executados em cada tarefa. Ex:
```python
tarefa:
  script:
    - echo "hello!" 
```
## before_script and after_script
Comandos que você precisa rodar antes ou depois do script: Ex:
```python
before_script:
  - global before script

job:
  before_script:
    - execute this instead of global before job
  script:
    - my command
  after_script:
    - execute this after my script
```
## image
O mesmo conceito da chamada de um container: o exemplo creio que é auto-explicativo:
```python
tarefa:
  image: ruby:2.1
  script:
    - test1 project  
```
Neste exemplo, vai iniciar um container com base na imagem ruby e rodar o comando test1 project. Isso é muito comum nas pipelines, pois normalmente você deve iniciar o PHP e gerar alguma coisa. Após sobe o NodeJS e roda o gulp, cada tarefa pode receber uma imagem diferente.
## only and except
Nessa configuração controlamos quando a tarefa vai rodar, se é só quando fizermos commit no master, ou via schedules, ou manual e etc. Ex:
```python
job:
  only:
    - schedules 
```
```python
job:
  # use special keywords
  except:
    - schedules 
```
Existem várias opções nesse item que não vou entrar em detalhe, porém vale a pena dar uma olhada na documentação oficial do gitlab, dá pra fazer muita coisa com isso :)

## allow_failure
Aqui é simples, em uma papeline linear, uma tarefa só será executada se a anterior tiver tido sucesso, essa configuração faz com que uma tarefa que tiver falha não pare toda a pipeline, utilizamos muito isso para o caso de crowlers pois cada job tem um timeout padrão de 1h.

## environment
Durante o desenvolvimento de um projeto é comum termos várias etapas, este atributo é responsável por fazer esse controle, podemos indicar vários ambientes em estágios diferentes, incluindo um para cada commit por ex.
```python
embiente:
  stage: deploy
  script: git push production HEAD:master
  environment:
    name: production
	url: https://prod.example.com
```

## Cache
Esta opção é utilizada para definir arquivos ou diretórios compartilhados entre os jobs.
```python
job:
  script: test
  cache:
    paths:
      - binaries/*.apk
      - .config
```
## Retry
Aqui definimos o número de tentativas que o Gitlab deve tentar para rodar um job em caso de falha:
```python
test:
  script: rspec
  retry: 2
```
## Parallel
Este é simples, podemos executar até 50 instâncias do job em paralelo:
```python
test:
  script: rspec
  parallel: 5
```
## Artifacts
Artifactis é utilizado para definir uma lista de arquivos ou diretórios para serem anexado ao job diferentemente do "cache" nesse atributo o job precisa terminar, os arquivos serão visualizados pelo job seguinte ex:
```python
default-job:
  script:
    - mvn test -U
  except:
    - tags

release-job:
  script:
    - mvn package -U
  artifacts:
    paths:
      - target/*.war
  only:
    - tags
```

# Conclusão
Automatizar deploy é praticamente uma obrigação em tempos de entregas constantes, o Gitlab nos fornece uma ferramenta simples de configurar e com todos os recursos necessários para qualquer infra, recomendo lerem a documentação completa em: [https://docs.gitlab.com/ee/ci/yaml/](https://docs.gitlab.com/ee/ci/yaml/ "https://docs.gitlab.com/ee/ci/yaml/")
OBS:
Para completar ainda tem o plano free com runners compartilhados que atendem bem até projetos grandes :)
