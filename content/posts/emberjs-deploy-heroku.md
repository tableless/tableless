---
title: 'Ember.js: Deploy no Heroku'
excerpt: Como configurar deploy automático no Heroku integrado com GitHub.
image: https://cdn-images-1.medium.com/max/800/1*BdMP7mksQuW62opnS2AYUA.png
authors: Aurélio Saraivas
type: post
date: 2017-11-30
categories:
  - Javascript
tags:
  - emberjs
  - Técnicas e Práticas
  - Tooling
  - reactjs
  - angularjs
---

Esse é um post bem rápido, vou mostrar como configurar deploy automático no
Heroku integrado com GitHub.

Se você é novo no Ember, recomendo você ler esse post anterior: <br> [Criando
uma aplicação Ember.js em 2 minutos](https://medium.com/@aureliosaraiva/criando-uma-aplicaÃ§Ã£o-ember-js-em-2-minutos-ec15f4c2036f)

Estou considerando que você já tem uma conta no Heroku, caso não tenha você pode
criar neste link:
[https://signup.heroku.com/login](https://signup.heroku.com/login)

Para continuar precisamos ter um repositório no GitHub com um projeto Ember.
Vamos usar esse respositório como exemplo:<br>
[https://github.com/aureliosaraiva/project-heroku-example](https://github.com/aureliosaraiva/project-heroku-example)

Faça um fork para sua conta no GitHub antes de continuar.

Vamos começar então!

## 1. Criando um app no Heroku

No dashboard do heroku, clique em **Create new app.**Depois que escolher um nome
para seu app, clique em Create App.

![](https://cdn-images-1.medium.com/max/800/1*E8H73Bn-hH08hliBe4kExA.png)

Seu app foi criado, você deve ver uma tela similar a esta:

![](https://cdn-images-1.medium.com/max/800/1*o5FpKHrNjPuIFQYo4qvtYA.png)

## 2. Configurando buildpacks do Ember

A equipe do Heroku criou um buildpacks com todas as dependências do Ember capaz
de detectar que é uma aplicação Ember e rodar automaticamente:

1.  npm install
1.  bower install
1.  ember build

Voltando, clique em **Settings**.

Vá até a seção Buildpacks

![](https://cdn-images-1.medium.com/max/800/1*PRMKrs-YoMHz3rOFX5pfbg.png)

Clique em Add buildpack. Quando abrir a tela abaixo, adicione o link do
buildpack do Ember.

[https://codon-buildpacks.s3.amazonaws.com/buildpacks/heroku/emberjs.tgz](https://codon-buildpacks.s3.amazonaws.com/buildpacks/heroku/emberjs.tgz)

![](https://cdn-images-1.medium.com/max/800/1*QXZfm5IVaFecdHcfBwZDfw.png)

Feito isso, seu app já está configurado para detectar automaticamente uma
aplicação Ember.

## 3. Configurando Deploy automático integrado com Github

Podemos usar um recurso muito útil do Heroku para fazer deploy automático
integrado com GitHub. O funcionamento é bem simples, sempre que você fizer um
**git push** na **master** do seu repositório, o Heroku será notificado
automaticamente, assim ele irá fazer o deploy sempre tiver alteração.

Acesse a aba **Deploy**

![](https://cdn-images-1.medium.com/max/800/1*o5FpKHrNjPuIFQYo4qvtYA.png)

Vá até a seção **Deployment Method**

![](https://cdn-images-1.medium.com/max/800/1*hhxgRE3bGRN_AgL8M0dtgA.png)

Você vai precisar dar acesso ao Heroku no Github. Depois de liberar acesso ao
Heroku, vamos conectar o repositório ao nosso app.

Digite o nome do seu repositório e clique em **Connect**.

![](https://cdn-images-1.medium.com/max/800/1*54G0RI_Y-QuEMBiBkiNIdg.png)

Pronto, nosso app do Heroku já está integrado com nosso repositório.

Para habilitar o deploy automático clique em **Enable Automatic Deploys**. Você
pode habilitar a verificação de CI, dessa forma o deploy vai aguardar os testes
passarem.

![](https://cdn-images-1.medium.com/max/800/1*r7j2Wj-Mqm5JZvjnXjHCIA.png)

Vamos agora fazer o primeiro deploy manualmente. <br> Clique em **Deploy
Branch**.

![](https://cdn-images-1.medium.com/max/800/1*KvgPvOewoXevb5w6aE1oUg.png)

Tudo pronto, só aguardar o deploy concluir.

## 4. Conclusão

Sei que alguns podem pensar que o Heroku não é o melhor host para hospedar uma
aplicação estática, e realmente não é o ideal. Porém essa solução permite você
criar uma integração continua rápida em poucos passos.

Se você tiver seu projeto integrado ao Circle-CI ou Travis-CI por exemplo, você
pode configurar o Heroku para que ele aguarde até que todas as pré-condições
sejam verificadas.

Bom, espero te ajudado você com essa dica simples!
