---
title: Criando uma aplicação de Chat simples com NodeJS e Socket.io
author: Daniel Campos
type: post
date: 2017-01-05
excerpt: Neste tutorial iremos abordar alguns conceitos do Socket.io criando um simples sistema de chat para browser.
url: /criando-uma-aplicacao-de-chat-simples-com-nodejs-e-socket-io/
titulo_personalizado:
  - 'Criando uma aplicação de Chat simples com <strong>NodeJS e Socket.io</strong>'
categories:
  - Código
  - Destaques
  - HTML
  - HTML5
tags:
  - html5
  - JavaScript
  - NodeJS
  - socket.io
  - sockets

---
Neste tutorial iremos abordar alguns conceitos do Socket.io criando um simples sistema de chat para browser.

![https://raw.githubusercontent.com/dericeira/Simple-Chat-Socket.io/master/example.gif][1]

## O que é Socket.io?

[Socket.io][2] é um uma biblioteca Javascript feita para construir aplicações real-time, possibilitando uma comunicação bi-direcional entre cliente e servidor. O socket.io utiliza as especificações de Web Sockets (para quem quer saber mais, recomendo dar uma olhada [neste ótimo artigo][3] da HTML5 Rocks).

O Socket.io roda, no lado do servidor, em NodeJS, e, no lado do cliente, ele roda diretamente no browser, possibilitando uma enorme gama de possibilidades de aplicações, como jogos, sistemas de notificações, real-time analytics e sistemas de chats e conversas em tempo real.

## Setando o projeto

Primeiramente, temos que instalar algumas bibliotecas que iremos utilizar no projeto, para isso usarei o [yarn][4].

Em primeiro lugar, vou adicionar ao projeto a biblioteca do Socket.io que rodará do lado do servidor.

<pre class="prettyprint">yarn add socketio</pre>

Também iremos utilizar o express:

<pre class="prettyprint">yarn add express</pre>

Também precisamos adicionar o Socket.io para o cliente (você pode utilizar a CDN oficial disponibilizada no site deles também):

<pre class="prettyprint">yarn add socket.io-client</pre>

E, por último, usarei a biblioteca jQuery para manipular a DOM.

<pre class="lang-bash">yarn add jquery</pre>

## Fazendo o HTML+CSS

Vamos criar um arquivo index.html e já deixar preparado o nosso template do sistema de chat.

<pre class="lang-html">&lt;!DOCTYPE html&gt;
&lt;html lang="en"&gt;
&lt;head&gt;
 &lt;meta charset="UTF-8"&gt;
 &lt;title&gt;Simple chat&lt;/title&gt;
 &lt;link rel="stylesheet" href="assets/css.css"&gt;
&lt;/head&gt;
&lt;body&gt;
&lt;div class="nickname_container" id="nick"&gt;

 &lt;span&gt;Type your nickname:&lt;/span&gt;
 &lt;form id="submit"&gt;&lt;input type="text" id="nickname" /&gt;&lt;/form&gt;

&lt;/div&gt;

&lt;div id="chat" hidden&gt;

 &lt;div class="menu" =&gt;
 &lt;div class="name" id="name"&gt;Alex&lt;/div&gt;
 &lt;div class="last" id="time"&gt;18:09&lt;/div&gt;
 &lt;/div&gt;

 &lt;ol class="chat"&gt;
 
 &lt;/ol&gt;
 
 &lt;input class="textarea" type="text" placeholder="Type here!" id="textarea" /&gt;
&lt;/div&gt;
 &lt;script src="node_modules/jquery/dist/jquery.min.js"&gt;&lt;/script&gt;
 &lt;script src="node_modules/socket.io-client/socket.io.js"&gt;&lt;/script&gt;
 &lt;script src="assets/js.js"&gt;&lt;/script&gt;
&lt;/body&gt;
&lt;/html&gt;
</pre>

Repare que eu também criei o diretório assets, e criei os arquivos css.css e js.js.

Não entrarei na parte do CSS, pois o foco aqui é o javascript, mas você pode ver o resultado no [github][5]. Eu utilizei como base [este pen][6] para construir o layout.

## Server-side

Vamos iniciar com a criação da parte de servidor do Socket.io, ou seja, iremos lidar com os eventos server-side.

Iniciaremos criando um arquivo **app.js** no diretório raíz e importaremos os módulos e faremos algumas operações iniciais:

<pre class="lang-javascript">var app = require('express')();
var http = require('http').Server(app);
var io = require('socket.io')(http);

var clients = {};

app.get('/', function(req, res){
res.send('server is running');
});

//SocketIO vem aqui

http.listen(3000, function(){
console.log('listening on port 3000');
});
</pre>

Este script implementa um servidor Node utilizando os módulos http e express (para roteamento).

A variável clientes que está sendo criada servirá para armazenar nossa lista de clientes.

Agora iremos adicionar o nosso primeiro evento do Socket.io, que será o **connection**, que dispara a cada vez que um cliente se conecta ao socket.

<pre class="lang-javascript">io.on("connection", function (client) {
    console.log('user connected');
});</pre>

Para nossa sala de chat, precisaremos implementar outros 3 eventos: **join**, **send** e **disconnect**:

<pre class="lang-javascript">io.on("connection", function (client) {
  client.on("join", function(name){
    console.log("Joined: " + name);
    clients[client.id] = name;
    client.emit("update", "You have connected to the server.");
    client.broadcast.emit("update", name + " has joined the server.")
  });

  client.on("send", function(msg){
    console.log("Message: " + msg);
    client.broadcast.emit("chat", clients[client.id], msg);
  });

  client.on("disconnect", function(){
    console.log("Disconnect");
    io.emit("update", clients[client.id] + " has left the server.");
    delete clients[client.id];
  });
});
</pre>

O evento join deverá ser disparado quando o cliente entrar no servidor, adicionando o id do cliente no array e emitindo dois novos eventos, nomeando-os de **update**.

Note que há uma diferença entre o método **client.emit** e o **client.broadcast.emit**. O client.emit enviará a notificação somente para o cliente atual, ou seja, o cliente que acabou de entrar na sala de chat. O **client.broadcast.emit** irá emitir para todos os clientes conectados, com exceção do que está executando a ação. Se utilizássemos o método **io.emit**, a mensagem seria enviada a todos os clientes conectados ao socket. Abaixo uma série de exemplos de métodos disponíveis:

<pre class="lang-javascript">// enviar apenas para o cliente atual
client.emit('message', "this is a test");

// enviar para todos os clientes, inclusive o atual
io.emit('message', "this is a test");

// enviar para todos os clientes, exceto o atual
client.broadcast.emit('message', "this is a test");

// enviar para todos os clientes (com exceção do atual) para uma sala específica
socket.broadcast.to('game').emit('message', 'nice game');

// enviar para todos os clientes em uma sala específica
io.in('game').emit('message', 'cool game');

// enviar para o atual, caso ele esteja na sala
client.to('game').emit('message', 'enjoy the game');

// enviar para todos os clientes em um namespace 'namespace1'
io.of('namespace1').emit('message', 'gg');

// enviando para um socketid individual
client.broadcast.to(socketid).emit('message', 'for your eyes only');</pre>

Com todos esses métodos, conseguiríamos implementar salas específicas, mensagens individuais, etc. Porém nosso foco é mostrar a parte mais básica e entender o funcionamento.

## Client-side

Com nosso servidor concluido e rodando, vamos passar para a parte de client-side de nossa aplicação de chat. Vamos ao **js.js**.

Primeiramente, inicializaremos o socket.io e criaremos uma variável **ready**, setada como false. Esta variável será responsável por indicar se o usuário já informou ou não o seu nickname.

<pre class="prettyprint">$(document).ready(function(){
    var socket = io.connect("http://localhost:3000");
    var ready = false;
});
</pre>

Com esta implementação, já conseguimos disparar o evento **connection** em nosso servidor. Porém, precisamos fazer com que o servidor receba a informação cada vez que um novo usuário entrar na sala informando o seu nickname.

<pre class="lang-javascript">$("#submit").submit(function(e) {
    e.preventDefault();
    $("#nick").fadeOut();
    $("#chat").fadeIn();
    var name = $("#nickname").val();
    var time = new Date();
    $("#name").html(name);
    $("#time").html('First login: ' + time.getHours() + ':' + time.getMinutes());

    ready = true;
    socket.emit("join", name);
});
</pre>

A função jQuery acima captura a submissão do formulário de nickname, fecha a tela de seleção de nick, mostra a tela de chat, seta a variável ready para true e executa um comando de socket, o **socket.emit**, que informa para o nosso servidor que um novo usuário acabou de entrar na sala.

Nada irá acontecer, pois ainda não temos o receptor do evento **update**, que está sendo disparado no nosso servidor, então vamos criá-lo:

<pre class="lang-javascript">socket.on("update", function(msg) {
    if (ready) {
        $('.chat').append('&lt;li class="info"&gt;' + msg + '&lt;/li&gt;')
    }
});
</pre>

Este código fará com que, a cada vez que o servidor emitir um update, o jQuery adicione uma nova linha no chat com a mensagem retornada.

Agora, iremos fazer com que nossa aplicação envie as mensagens ao servidor a cada vez que o cliente apertar o enter no input de texto:

<pre class="prettyprint">$("#textarea").keypress(function(e){
    if(e.which == 13) {
         var text = $("#textarea").val();
         $("#textarea").val('');
         var time = new Date();
         $(".chat").append('&lt;li class="self"&gt;&lt;div class="msg"&gt;&lt;span&gt;'
                      + $("#nickname").val() + ':&lt;/span&gt;    &lt;p&gt;' + text + '&lt;/p&gt;&lt;time&gt;' + 
                      time.getHours() + ':' + time.getMinutes() + '&lt;/time&gt;&lt;/div&gt;&lt;/li&gt;');
         socket.emit("send", text);
    }
});
</pre>

E, para concluir, precisamos fazer com que o socket.io observe todas as mensagens referente ao chat em si, e adicione à DOM:

<pre class="prettyprint">socket.on("chat", function(client,msg) {
 if (ready) {
    var time = new Date();
    $(".chat").append('&lt;li class="other"&gt;&lt;div class="msg"&gt;&lt;span&gt;' + 
                 client + ':&lt;/span&gt;&lt;p&gt;' + msg + '&lt;/p&gt;&lt;time&gt;' + time.getHours() + ':' + 
                 time.getMinutes() + '&lt;/time&gt;&lt;/div&gt;&lt;/li&gt;');
 }
});</pre>

## Conclusão

Na minha opinião,  as sockets são uma das melhores funcionalidades do HTML5, e possuem uma infinidade de aplicação. O ganho de performance é espetacular se bem aplicado, uma vez que evita o uso de requisições HTTP em aplicações onde a necessidade de atualização é grande (baixa latência).

Disponibilizei o código do tutorial no [github][7] para quem se interessar, e estou aberto a tirar dúvidas.

 [1]: https://raw.githubusercontent.com/dericeira/Simple-Chat-Socket.io/master/example.gif
 [2]: http://socket.io
 [3]: https://www.html5rocks.com/pt/tutorials/websockets/basics/
 [4]: https://github.com/yarnpkg/yarn
 [5]: https://github.com/dericeira/Simple-Chat-Socket.io/blob/master/assets/css.css
 [6]: https://codepen.io/Varo/pen/gbZzgr
 [7]: https://github.com/dericeira/Simple-Chat-Socket.io