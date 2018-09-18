---
title: Criando uma API Express
authors: Tailo Mateus Gonsalves
type: post
date: 2017-11-17
excerpt: Ou apenas me aventurando no Back-end.
image: https://i.imgur.com/nfwlTfm.png
categories:
  - NodeJS
  - Javascript
  - Tecnologia e Tendência
tags:
  - API Express
  - Express
  - Node
---

Primeiramente, o Front-end sempre me chamou mais a atenção e acredito que sou
melhor nisso. Porém, me aventurei no lado escuro da força (Back-end) e posso
dizer que em muitos casos não foi algo bom.

Meu objetivo não é falar qual linguagem ou framework é bom ou ruim, mas que cada
pessoa tem uma preferência, não tem nada demais não gostar de alguma tecnologia.


Durante os últimos cinco anos estudei ou trabalhei com Java, C#, Zend. Confesso
que fiquei decepcionado, a quantidade de tempo para configurar o ambiente e
construir algo visível. 

Além dessas tecnologias, me aventurei em algo mais ágil, tentei aprender Ruby on
Rails e Laravel, apesar de gostar bastante, percebi que ainda não tinha
encontrado o ideal para mim. Apesar dessas frustrações em nenhum momento deixei
de participar de algum projeto ou aprender, todo o conhecimento adquirido será
reutilizado em algum outro momento. Enquanto não encontrei a linguagem e o
framework backend continuei estudando sobre front-end.

Faz algum tempo que comecei a estudar sobre o [Node.js](https://nodebr.com/) e o
framework [Express](https://expressjs.com/) e como em poucos passos consigo
criar uma API. Segundo o próprio site do Express é um framework web rápido,
flexível e minimalista para Node.js.

OBS: Se você não conhece o NPM, comece por os links abaixo:

[Your first Node.js
package](https://nodesource.com/blog/your-first-nodejs-package/)

[O que é a NPM do Node.JS](https://nodebr.com/o-que-e-a-npm-do-nodejs/)

**PASSO 1— Instalar o Express**

<script src="https://gist.github.com/TailoMateus/858d0a56f79f2c1b64cf10d2bc5be36e.js"></script>

**PASSO 2— Criar o arquivo server.js**

No inicio do código é importado o módulo `express` e criado um `app`. Após ele
cria uma rota baseado no método HTTP. Os objetos `req` e `res` são fornecidos
pelo Node, equivalentes a um pedido HTTP e uma resposta (request, response).
Para finalizar estou dizendo para a instância criada ouvir na porta 8080.

<script src="https://gist.github.com/TailoMateus/b044d31c4df4a1084d1466d095b728ba.js"></script>

**PASSO 3— Inicie o servidor Express**

Se tudo correu bem, basta acessar localhost:8080.

<script src="https://gist.github.com/TailoMateus/048c6e714bf9bf6dd367c4fc48704453.js"></script>

Ou caso prefira utilize [nodemon](https://github.com/remy/nodemon) para
automatizar esse processo.

Obviamente que, com o Node.Js e o Express você pode fazer varias coisas legais,
a introdução desse assunto é justamente para você pesquisar mais e não ter medo
em aprender algo novo :D

**CONCLUSÃO**

Após tanto tempo testando linguagens e frameworks para o Back-end, acredito que
encontrei um que mais me agradou. Mas como comentei no inicio do artigo, as
pessoas possuem preferencias diferentes, e no meu caso é essencial ter um inicio
rápido com uma tecnologia, pequenas recompensas me motivam a continuar
estudando.

Além disso, não deixe de testar algo novo ou de participar de algum projeto pelo
o que estão usando. Não existe nada pior que um fanboy. Tem coisas boas para
algumas coisas e ruins para outras. Simples!

**LEIA MAIS**

[Primeiros passos com Express em
Node.js](https://nodebr.com/primeiros-passos-com-express-em-node-js/)

[Build Node.js RESTful APIs in 10
Minutes](https://www.codementor.io/olatundegaruba/nodejs-restful-apis-in-10-minutes-q0sgsfhbd)

[Building a Node.js REST API with
Express](https://medium.com/@jeffandersen/building-a-node-js-rest-api-with-express-46b0901f29b6)

[Site em português](https://expressjs.com/pt-br/)

<br> 