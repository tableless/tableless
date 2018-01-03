---
title: Gerenciando suas aplicações Node com PM2
authors: Breno Panzolini
type: post
date: 2017-12-28
excerpt: Como gerenciar suas aplicações em NodeJS em produção com o PM2.
categories:
  - NodeJS
  - JavaScript
tag
  - NodeJS
  - JavaScript
image:  https://raw.githubusercontent.com/unitech/pm2/master/pres/pm2.20d3ef.png
---

Nesse post vou explicar o básico para se fazer o deploy de uma aplicação Node.js utilizando o [**PM2**](http://pm2.keymetrics.io/), que é um serviço avançado e altamente utilizado para gerenciar os seus processos Node.

## Por que utilizar o PM2?

O PM2 é uma ferramenta open source completa para o gerenciamento e deploy de aplicações Node.js em ambientes de produção. Dentro os principais recursos disponíveis podemos citar:

- Monitoramento das aplicações
- Integração com containers
- *Hot reload* das aplicações
- Fácil integração com serviços de deploy contínuo
- Logs das aplicações
- Facilidade em escalar as aplicações

Citei apenas alguns recursos, porém o PM2 tem muita coisa legal disponível que pode ser encontrada na [documentação oficial](http://pm2.keymetrics.io/docs/usage/cluster-mode/).

## Instalando o PM2

A instalação do PM2 é muito simples, basta digitar o comando abaixo:

```sh
$ npm install pm2 -g
```

Existe também a opção de baixar uma imagem oficial do docker com o PM2 já instalado e assim usá-la junto com um gerenciador de containers, como por exemplo o kubernetes, porém como o objetivo desse post é mostrar o básico do PM2 vamos deixar esse assunto para um outro momento.

## Subindo suas aplicações no PM2

Pois bem, chegou a hora de colocar em prática o básico das funcionalidades do PM2, para isso vamos fazer uma aplicação extremamente simples em Node.js.

Nossa aplicação irá monitorar uma pasta e de tempos em tempos logar no console todos os arquivos que estão na pasta. É uma aplicação extremamente simples e praticamente sem nenhuma utilidade "real", porém podemos focar no objetivo do post que é o **PM2**.

Primeiro vamos criar uma estrutura básica de pastas:

```sh
$ mkdir projeto-pm2
$ cd projeto-pm2
$ mkdir arquivos
$ npm init -y
$ touch index.js
```

Agora, abra o arquivo index.js e cole o seguinte código:

```js
const fs = require('fs')

function monitorar () {
  const arquivos = fs.readdirSync('./arquivos')
  console.log(`${arquivos.length} arquivos encontrados!`)
  
  for (let arquivo of arquivos) {
    console.log(arquivo)
  }
}

setInterval(monitorar, 5000)
```

Vamos primeiramente inicar a aplicação da maneira "tradicional", para ver que está funcionando corretamente:

```
$ node index.js
```


