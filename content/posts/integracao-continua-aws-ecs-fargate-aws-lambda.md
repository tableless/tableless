---
title: Integração contínua no AWS ECS Fargate com AWS Lambda
authors: Allan Sene
type: post
date: 2018-10-22
excerpt: Um guia de como configurar um deploy automático a partir de uma imagem disponibilizada no AWS Container Registry.
image: https://i.imgur.com/FGTwjFc.jpg
categories:
  - Backend
  - Técnicas e Práticas
tags:
  - Devops
  - AWS
---

## Um guia de como configurar um deploy automático a partir de uma imagem
disponibilizada no AWS Container Registry.

Uma coisa que ainda [falta no AWS
CodePipeline](https://docs.aws.amazon.com/AWSGettingStartedContinuousDeliveryPipeline/latest/GettingStarted/ECS_CD_Pipeline.html)
é um fluxo de deploy no ECS a partir da disponibilização de uma imagem no AWS
ECR. E fazer um deploy na clicação ou subir um Jenkins só pra resolver esse
problema, não dá né!

Neste post vou ensinar uma forma simples e prática de automatizar seus deploys
no [AWS ECS Fargate](https://aws.amazon.com/fargate/), a partir de uma imagem
disponibilizada no ECR, registro de containeres da AWS.

**** Importante: **Considero aqui que você já tenha cluster, service e task
definitions já configuradas e que só queira **automatizar** o processo.

# Passo 1: Criar Role no IAM

![](https://cdn-images-1.medium.com/max/800/0*9qMLmJhyT_gLZ2m5)
<span class="figcaption_hack">“white security camera on post” by [Paweł
Czerwiński](https://unsplash.com/@pawel_czerwinski?utm_source=medium&utm_medium=referral)
on [Unsplash](https://unsplash.com/?utm_source=medium&utm_medium=referral)</span>

Antes de criar nossa Lambda, vamos criar a [IAM
Role](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles.html) que dá
permissão para que ela utilize os serviços da AWS necessários. Pra facilitar,
utilizaremos as [AWS Managed
Policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_managed-vs-inline.html)
abaixo:

* **AmazonEC2ContainerRegistryReadOnly**: Autoriza a leitura da imagem publicada
nos repositórios do ECR.
* **AmazonEC2ContainerServiceFullAccess**: Autoriza a criação, atualização e
deleção de Tasks Definitions e Serviços.

![](https://cdn-images-1.medium.com/max/1000/1*hBxdTypI5PiPN0D6z6yavQ.png)
<span class="figcaption_hack">Exemplo de uma Role com as policies criadas.</span>

Além das permissões citadas acima, sua Lambda vai precisar de permissões para
escrever Logs no [CloudWatch](https://aws.amazon.com/cloudwatch/). Então,
adicione também o seguinte trecho como
[inline](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_managed-vs-inline.html)
na sua IAM Role:

# Passo 2: Criar Lambda Function

Neste passo, você vai escolher a **IAM Role** criada no passo anterior. Nosso
script é em **Python**, pode rodar tanto na versão 2.7 quanto na 3.6:

![](https://cdn-images-1.medium.com/max/1000/1*LOp30lJzn9PVu_mgOO_0pg.png)
<span class="figcaption_hack">Criando uma Lambda na mão lá no console.</span>

O Script tem 4 pontos principais:

* Verifica se o evento
[PutImage](https://docs.aws.amazon.com/AmazonECR/latest/APIReference/API_PutImage.html)
foi no repositório do projeto que você quer automatizar. Isso é uma **garantia**
que você não saia dando deploy em todos os projetos automaticamente.
* Pega o **número da conta** de acordo com a [IAM
Role](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles.html) utilizada.
Dessa forma esse script pode ser reaproveitado em ambiente de dev, homologação e
produção.
* Registra uma nova [Task
Definition](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/task_definitions.html)
com a última imagem disponibilizada. Observe que ele **mantem todas as outras
configurações da task**.
* Atualiza o
[Serviço](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/ECS_GetStarted.html#first-run-service)
com a Task Definition recém-criada.

Copie o script aí embaixo, **substituindo o valor de PROJECT_PREFIX com o nome
do seu projeto/cluster **e cole no editor da AWS:

# Passo 2: Testando sua Lambda

Para testar sua lambda, basta configurar um novo payload de teste, clicando em
“**Configure Test Events**” lá no topo do console da AWS. Utilizaremos este
json, que explicarei melhor o que representa no próximo passo.

* **Importante:** Obviamente, você tem que substituir os valores
**repositoryName** e **imageTag** de acordo com o seu projeto.

Se tudo deu certo, seu cluster já está atualizando o serviço com a nova taskdef.
[Olha aqui pra você
ver…](https://console.aws.amazon.com/ecs/home?region=us-east-1#/clusters/)

# Passo 3: Criação da Regra no CloudWatch

Agora que sua Lambda está **testada** e **pronta** para dar o deploy no ECS,
precisamos estruturar o **acionamento** dela. Pra tal, utilizaremos as
**CloudWatch Rules**. Com esse serviço, podemos “escutar” eventos da API da AWS
via [CloudTrail](https://aws.amazon.com/cloudtrail/) e disparar ações a partir
deles. Neste caso, vamos trackear o evento
“[PutImage](https://docs.aws.amazon.com/AmazonECR/latest/APIReference/API_PutImage.html)”,
que acontece no AWS ECR.

Em “**Targets**”, escolha a sua Lambda Function, criada no passo 2. Somente o
**requestParameters** é importante pra gente, então vamos filtrar o restante do
evento, em **Configure input**. Olha aí embaixo como configurar:

![](https://cdn-images-1.medium.com/max/800/1*Mer1_meC9phX3GibtWKGGg.png)
<span class="figcaption_hack">Criando uma regra na mão lá no CloudWatch.</span>

Se estiver utilizando o aws-cli, use o json abaixo pra criar a regra:

Pronto! Agora é só executar um *push* de uma nova imagem pro repositório e ver
tudo rodando juntinho! Você também tem métricas de acionamento das rules no
próprio CloudWatch.

Caso tenham alguma crítica ou correção pra fazer, não deixem de comentar =)

Valeu, galera! Até a próxima!
