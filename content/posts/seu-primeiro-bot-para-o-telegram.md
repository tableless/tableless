---
title: Seu primeiro bot para o Telegram
author: Rafael Augusto
type: post
image: https://cdn-images-1.medium.com/max/1000/1*M0bDjag4DJovh0imf9nYKQ.png
date: 2017-05-12
excerpt: Nesse artigo vamos mostrar o desenvolvimento de um BOT muito simples utilizando a API do Telegram.
url: /seu-primeiro-bot-para-o-telegram/
categories:
  - JavaScript
  - NodeJS
  - Tecnologia e Tendências
  - Código
tags:
  - ChatBot
  - Telegram
  - API
---

Os BOTS de chats hoje já são uma realidade, eles já estão presentes nos aplicativos de mensagens do seu celular, e com certeza você já ficou curioso em como alguns deles são desenvolvidos. Nesse artigo, vamos mostrar o desenvolvimento de um BOT muito simples utilizando a API do Telegram.

Artigo adaptado de [Bot Telegram](https://github.com/suissa/bot-telegram)

## Criando o seu BOT

Para esse simples exemplo será utilizado o JavaScript na plataforma NodeJS em conjunto com a API do Telegram, caso você não esteja familiarizado com essa plataforma, você pode conferir esse ótimo artigo aqui do Tableless [Como instalar Node.js no Linux corretamente](https://tableless.com.br/como-instalar-node-js-no-linux-corretamente-ubuntu-debian-elementary-os/)

Execute o seguinte comando no terminal/prompt de comando, para fazer a instalação da API do Telegram:

```
npm install node-telegram-bot-api --save
```

Depois, vamos incluir o mesmo em nosso index.js da seguinte forma:

```js
const TelegramBot = require( `node-telegram-bot-api` )

const TOKEN = `SEU TOKEN`

const bot = new TelegramBot( TOKEN, { polling: true } )
```

## Gerando o Token

Para gerar o nosso token, será necessário falar com o [@BotFather](https://telegram.me/botfather)

![@BotFather](http://i.imgur.com/3dvVOwT.png)

Execute o seguinte comando: `/newbot` e siga as instruções:

![Criando o Bot](http://i.imgur.com/q5GsuRY.png)

Agora, vou incluir o token na minha configuração:

```js
const TelegramBot = require( `node-telegram-bot-api` )

const TOKEN = `373045955:AAGvpCeqMocpkDgrdqjebqK5ZiV24vDifZU`

const bot = new TelegramBot( TOKEN, { polling: true } )
```
## Entenda como o BOT funciona

Agora que já temos o nosso BOT configurado, vamos entender um pouco como ele funciona. Vamos começar criando o comando mais básico que ele possa entender.

```js
bot.on('message', function(msg){
  console.log('msg', msg)
})
```

Inicie o nosso BOT com o seguinte comando:

```
node index.js
```

Abra a conversa com o seu BOT e digite alguma mensagem para ele da seguinte forma:

![Falando com o Bot](http://i.imgur.com/nocVBto.png)

O resultado no console do Node será o seguinte:

```
{ message_id: 2,
  from:
   { id: 77586615,
     first_name: 'Rafael',
     last_name: 'Vicio',
     username: 'rafaelvicio' },
  chat:
   { id: 77586615,
     first_name: 'Rafael',
     last_name: 'Vicio',
     username: 'rafaelvicio',
     type: 'private' },
  date: 1492093704,
  text: 'Ola Bot!' }
}
```

Com essa estrutura você consegue perceber algumas informações importantes, como quem mandou, o que mandou, entre outras informações.

## Criando o seu primeiro comando

O BOT trabalha escutando alguns eventos, para esse simples BOT, nós vamos trabalhar apenas com um comando básico, que escuta as mensagens enviadas pelo chat e retorna a mesma mensagem para quem enviou.

Para isso, vamos utilizar o evento onText, que, como você deve estar imaginando, escuta os textos enviados nas mensagens.

Para mais detalhes sobre os de eventos suportados, você pode consultar a documentação da API: [Usage - node-telegram-bot-api](https://github.com/yagop/node-telegram-bot-api/blob/master/doc/usage.md)

Um detalhe desse evento é que ele recebe como primeiro parâmetro uma RegEx, o que nos permite verificar o texto enviado. Vamos ao exemplo:

```js
bot.onText( /\/echo (.*)/, function(msg, match){
  console.log( `echo msg: `, msg )
  console.log( `echo match: `, match )
})
```

Rodando a aplicação novamente, e enviando a mensagem '/echo oi' para o BOT, temos o seguinte retorno:

```
echo msg:  { message_id: 7,
  from:
   { id: 77586615,
     first_name: 'Rafael',
     last_name: 'Vicio',
     username: 'rafaelvicio' },
  chat:
   { id: 77586615,
     first_name: 'Rafael',
     last_name: 'Vicio',
     username: 'rafaelvicio',
     type: 'private' },
  date: 1492093704,
  text: '/echo oi',
  entities: [ { type: 'bot_command', offset: 0, length: 5 } ] }

echo match:  [ '/echo oi',
  'oi',
  index: 0,
  input: '/echo oi' ]
```

A estrutura do 'msg' já foi apresentada a você anteriormente, agora fique atento a estrutura do objeto match:

```
echo match:  [ '/echo oi',
  'oi',
  index: 0,
  input: '/echo oi' ]
```

Ele é simplesmente um array que contém o resultado do match testando a mensagem recebida com a RegEx que foi definida no onText.

Com isso podemos identificar o que está em cada posição do array:

* na posiçao 0: temos o valor total do texto
* na posiçao 1: o texto sem a RegEx
* na posiçao 2: o índice onde foi encontrada a RegEx
* na posiçao 3: a entrada

Como o objetivo do comando /echo é responder com o mesmo texto enviado, o que nos interessa é o item na posição 1 desse array.

Para fazer o BOT enviar uma mensagem, vamos utilizar a função bot.sendMessage, da seguinte maneira:

```js
bot.sendMessage( id, text )
```

Portanto, nosso código funciona da seguinte forma:

```js
var logErrorEcho = function logErrorEcho(msg) {
  return function (err) {
    return console.log(msg, err);
  };
};

var logSuccessEcho = function(msg, match){
  return function(data){
    console.log( 'Success:', data);
  };
};

var sendEcho = function(msg, match){
  bot.sendMessage( msg.chat.id, match[ 1 ] )
      .then( logSuccessEcho( msg, match ) )
      .catch( logErrorEcho( 'Error:') );
};

bot.onText( /\/echo (.*)/, sendEcho);
```
Com isso, o seu BOT vai ter a função /echo que funciona da seguinte forma:

![Comando /echo](http://i.imgur.com/nocVBto.png)

O código desse projeto está disponível no [GitHub](https://github.com/rafaelvicio/primeiro-bot) do autor.

Aos interessados em continuar os estudos sobre esse assunto, junte-se ao nosso [grupo no Telegram](https://t.me/brbotdevs).