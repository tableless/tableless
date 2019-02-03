---
title: Continuous Integration & Delivery no Gitlab.com
authors: Morais Junior
type: post
image: https://about.gitlab.com/images/ci/ci-cd-test-deploy-illustration_2x.png
date: 2019-02-05
excerpt: Continuous Integration & Delivery é uma das partes mais importantes no trabalho de qualquer dev-ops, nesta artigo irei abordar como funciona este recurso no Gitlab. 
categories:
  - DevOps
  - Infra
  - Gitlab
---
# Continuous Integration & Delivery no Gitlab.com
Creio que de todas as ferramentas que já trabalhei o gitlab-ci é uma das mais simples, basta incluir um arquivo chamado* .gitlab-ci.yml* na raiz do repositório e pronto sempre que tiver um commit ou deploy o gitlab vai subir maquinas e executar as tarefas descritas na sua configuração, a baixo vou explicar como montar esse arquivo.
## Pipeline
No gitlab uma pipeline é um conjunto de tarefas e procedimentos a serem executados quando tiver alguma alteração no repositório, sejam eles, rodar o gulp, atualizar uma imagem docker, limpar um cache, fazer upload no seu bucket s3, qualquer coisa :)
## Jobs
Job é cada tarefa dentro da pipeline, essas terefas podem ser dependentes umas das outras ou não, pode ser chamandas quando se faz um push ou via schedules, podem ser manuais e etc. Basicamente é um containner que o gitlab sobe execultando uma sequencia de comandos.
Ex:
```python
job1:
  script: "execute-script-for-job1"

job2:
  script: "execute-script-for-job2"
```
para esse exemplo sempre que ouver um push, a pipeline vai conter essas duas jobs, simples né?

Ainda falando sobre jobs podemos ter *hidden jobs* que são tarefas que não aparecem na pipeline, pra isso é só colocar um . *ponto* no nome.
Ex:
```python
.job1:
  script: "tarefa oculta"

job2:
  script: "execute-script-for-job2"
```
Nesse exemplo o job1 não será mostrado na pipeline. (mais a diante vocês vão entender como isso ajuda nossa vida)

Outro item importante sobre tareflas são os *Anchors* que nada mais são do que modelos de tarefas que servem como uma especie de templates para evitar re-escrita de código. Ex:
```python
.job1: &modelo1
  key:value

job2:
	<<: *modelo1
  script: "execute-script-for-job2"
```
No exemplo acima a tarefa 2 vai herdar as configurações da tarefa que tem a ancora modelo1.

por ultimo, porem não menos importarnte são os *stages* nada mais é que uma forma de vc controlar a sequencia que suas tarefas serão execultadas. Ex:
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
No exemplo acima as tarefas seram executadas uma apos da outra, caso não tenha a definição de stages as tarefas entram em paralelo, isso é ruim pois por exemplo o deploy pode terminar antes de rodarem os testes.

tendo entendido estes conceitos, iremos entrar nos detalhes sobre a criação de uma tarefa no gitlab:
## script
Nessa configuração vão os comandos que precisam ser executados em cada tarefa. Ex:
```python
tarefa:
  script:
    - echo "hello!" 
```
## before_script and after_script
Aqui são comandos que vc precisa rodar antes ou depois do script. Ex:
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
Aqui temos o mesmo conceito da chamada de um container, o exemplo creio que é auto-explicativo:
```python
tarefa:
  image: ruby:2.1
  script:
    - test1 project  
```
No exemplo acima ele vai iniciar um container com base na imagem *ruby* e rodar o comando *test1 project*, isso é muito comum nas pipelines pos normalmente você tem que iniciar um PHP da vida, gerar alguma coisa, depois sobe um NodeJS e roda algum gulp, cada tarefa pode receber uma imagem diferente.

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
Existem varias opções nesse item que não vou entrar em detalhe, porem vale a pena dar uma olhada na documentação oficial do gitlab pois da pra fazer muita coisa com isso :)

## allow_failure
Aqui é simples, em uma papeline linear, uma tarefa só será execultada se a anterior tiver tido sucesso, essa configuração faz com que uma tarefa que tiver falha não pare toda a pipeline, utilizamos muito isso para o caso de crowlers pois cada job tem um timeout padrão de 1h.

## environment
Durante o desenvolvimento de um projeto é comum termos varias etapas, esté atributo é responsavel por fazer esse controle, podemos indicar varios ambientes em estagios diferentes, incluindo um para cada commit por ex.
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
Aqui definimos o nomero de tentativas que o Gitlab deve tentar para rodar um job em caso de falha:
```python
test:
  script: rspec
  retry: 2
```
## Parallel
Este é simples, podemos execultar até 50 instancias do job em paralelo:
```python
test:
  script: rspec
  parallel: 5
```
## Artifacts
Artifactis é utilizado para definir uma lista de arquivos ou diretórios para serem anexado ao job diferentimente do "cache" nesse atributo o job precisa terminar, os arquivos serão visualizados pelo job seguinte ex:
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
Automatizar deploy é praticamente uma obrigação em tempos de entregas constantes, o Gitlab nos fornece uma ferramenta simples de configurar e com todos os recursos nescessarios para qualquer infra, recomendo lerem a documentação completa em: [https://docs.gitlab.com/ee/ci/yaml/](https://docs.gitlab.com/ee/ci/yaml/ "https://docs.gitlab.com/ee/ci/yaml/")
OBS:
Para completar ainda tem o plano free com runners compartilhados que atendem bem até projetos grandes :)
