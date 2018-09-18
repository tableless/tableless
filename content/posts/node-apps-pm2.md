---
title: Gerenciando aplicações Node.js com PM2
authors: Breno Panzolini
type: post
date: 2018-01-04
excerpt: Como gerenciar aplicações Node.js em produção com PM2.
categories:
  - NodeJS
  - Javascript
tags:
  - NodeJS
  - Javascript
image:  https://raw.githubusercontent.com/unitech/pm2/master/pres/pm2.20d3ef.png
---

Nesse post vou explicar o básico para se fazer o deploy de uma aplicação desenvolvida em Node.js utilizando o [**PM2**](https://pm2.keymetrics.io/), que é uma ferramenta avançada e altamente utilizada para gerenciar aplicações em produção.

## Por que utilizar o PM2?

O PM2 é uma ferramenta open source completa para o gerenciamento e deploy de aplicações Node.js em ambientes de produção. Dentro os principais recursos disponíveis podemos citar:

- Monitoramento das aplicações
- Integração com containers
- *Hot reload* das aplicações
- Fácil integração com serviços de deploy contínuo
- Logs das aplicações
- Facilidade em escalar as aplicações (modo cluster ou fork)

Citei apenas alguns recursos, porém o PM2 tem muita coisa legal disponível que pode ser encontrada na [documentação oficial](https://pm2.keymetrics.io/docs/usage/cluster-mode/).

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

![app node](https://i.imgur.com/96V7vNe.png)

### Iniciando a aplicação pelo PM2

Agora que tudo está funcionando, vamos iniciar a nossa aplicação através do PM2:

```
$ pm2 start index.js --name monitor
```

![pm2 start](https://i.imgur.com/QhCkJyZ.png)

O comando **start** é responsável por iniciar a nossa aplicação. No exemplo acima passei "monitor" como nome da minha aplicação.

Além disso o start também é responsável por fazer o *auto-restart*, ou seja, caso aconteça algum erro inesperado e a nossa aplicação "morra" o PM2 irá reiniciar ela automaticamente, sem que tenhamos que nos preocupar com isso.

### Explorando o PM2

Existem diversos comandos para monitorar, escalar, acompanhar as nossas aplicações, porém como o objetivo desse post é fazer uma introdução dessa ferramente, vou listar apenas os mais básicos e que irão ajudar bastante.

1. list: mostra todos os processos gerenciados pelo PM2

```
$ pm2 list
```

![pm2 list](https://i.imgur.com/X0ceSBr.png)

2. monit: é um monitor que mostra toda a CPU e memória consumida por cada processo iniciado através do PM2, por esse comando também é possível acompanhar o log da nossa aplicação.

```
$ pm2 monit
```

![pm2 monit](https://i.imgur.com/A8WEmAb.png)

3. log \[nome-app\]: mostra os logs específicos de uma aplicação.

```
$ pm2 log monitor
```

![pm2 log](https://i.imgur.com/VQVq4zF.png)

4. stop \[nome-app\]: *stopa* o processo específico.

```
$ pm2 stop monitor
```

![pm2 stop](https://i.imgur.com/Ivo3sKJ.png)

5. delete \[nome-app\]: exclui o processo específico do PM2.

```
$ pm2 delete monitor
```

![pm2 delete](https://i.imgur.com/MDid7As.png)

## Conclusão

Esse post foi para mostrar apenas o básico de uma das ferramentas existentes para realizarmos o deploy das nossas aplicações Node.js em produção. Grandes empresas como PayPal, Best Buy e IBM utilizam o PM2 exatamente pelo seu grande poder no gerenciamento e manutanção das nossas aplicações no ambiente de produção.

Aconselho para quem se interessou consultar o [site oficial](https://pm2.keymetrics.io/) e o repositório no [GitHub](https://github.com/Unitech/pm2), pois tem muita coisa legal que é possível fazer com o PM2.
