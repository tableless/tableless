---
title: Criando um aplicativo simples de chat com Firebase
author: Cosme Lopes
type: post
date: 2014-07-17
excerpt: Um exemplo de utilização dessa poderosa plataforma de armazenamento e sincronização de dados em tempo real.
url: /criando-um-aplicativo-simples-de-chat-com-firebase/
dsq_thread_id: 2847349797
categories:
  - JavaScript
  - Técnicas e Práticas
tags:
  - Chat
  - Firebase
  - Sincronização

---
[Firebase][1] é uma plataforma para desenvolvimento de aplicativos baseados em armazenamento e sincronização de dados em tempo real utilizando apenas código _client-side_. Utilizando o Firebase você será capaz de armazenar e sincronizar os dados da aplicação de uma maneira extremamente simples e direta, o que é extremamente conveniente quando pensamos em aplicações como chats e jogos. 

**Firebase** oferece integração com várias plataformas como **Angular**, **Ember** e **Node.js**, mas você pode simplesmente incluir a biblioteca javascript em uma página html simples e começar a desenvolver uma aplicação com transmissão de dados em tempo real. 

## Primeiros passos

Para iniciar uma aplicação web com Firebase partimos de uma página html simples e importamos a biblioteca JavaScript do **Firebase**: 

<pre class="lang-html">&lt;html&gt;
  &lt;head&gt;
    &lt;script src=‘https://cdn.firebase.com/js/client/1.0.17/firebase.js'&gt;&lt;/script&gt;
  &lt;/head&gt;
  &lt;body&gt;
  &lt;/body&gt;
&lt;/html&gt;
</pre>

Antes de continuar com o tutorial, acesse a página do **Firebase** e crie uma conta gratuita. Após acessar sua conta, escolha a opção de criar um novo aplicativo, e em seguida copie a _url_ do novo aplicativo. A _url_ tem o formato _seu-app.firebaseIO.com_. 

Em seguida insira dentro da tag `body` uma tag `script` e insira o código para criar uma referência à sua aplicação da seguinte maneira: 

<pre class="lang-html">&lt;html&gt;
  &lt;head&gt;
    &lt;script src='https://cdn.firebase.com/js/client/1.0.17/firebase.js'&gt;&lt;/script&gt;
  &lt;/head&gt;
  &lt;body&gt;
    &lt;script&gt;
      var APP = new Firebase('https://seu-app.firebaseIO.com/');   
    &lt;/script&gt;
  &lt;/body&gt;
&lt;/html&gt;
</pre>

Pronto, seu aplicativo já está conectado com o **Firebase**, mas seu chat ainda não está pronto para ser o próximo sucesso da internet. 

## Enviando uma mensagem

Na sequência, para possibilitar que o usuário envie uma mensagem, vamos adicionar um campo para que seja escrita as mensagens e um para o nome do usuário e vamos enviar para o servidor sempre que o usuário pressionar enter. Para obter o conteúdo da mensagem assim como o evento do envio, vamos utilizar um pouco de <a href="http://jquery.com/" rel="noreferrer">jQuery</a>, portanto não esqueça de incluí-lo em sua página. 

Até agora temos a seguinte estrutura:

<pre class="lang-html">&lt;html&gt;
&lt;head&gt;
  &lt;script src='https://cdn.firebase.com/js/client/1.0.17/firebase.js'&gt;&lt;/script&gt;
  &lt;script src='https://ajax.googleapis.com/ajax/libs/jquery/1.9.0/jquery.min.js'&gt;&lt;/script&gt;
&lt;/head&gt;
&lt;body&gt;
  &lt;input type="text" id="nomeusuario" placeholder="Seu nome..."&gt;
  &lt;input type="text" id="mensagem" placeholder="Sua mensagem..."&gt;
  &lt;script&gt;
    var APP = new Firebase('https://seu-app.firebaseIO.com/');
  &lt;/script&gt;
&lt;/body&gt;
&lt;/html&gt;
</pre>

Precisamos então capturar o evento do pressionar da tecla enter e em seguida chamar o método push da nossa referência à nossa aplicação **Firebase** para enviar um objeto ao servidor contendo os dados da mensagem. Para fazer isso incluímos o seguinte código na página: 

<pre class="lang-javascript">$('#mensagem').keypress(function (e) {
  if (e.keyCode == 13) {

    var msg = $('#mensagem').val();
    var usr = $('#nomeusuario').val();
    APP.push({ nomeusuario: usr, mensagem: msg });

    $('#mensagem').val('');
  }
});
</pre>

Obtendo o seguinte resultado: 

<pre class="lang-html">&lt;html&gt;
&lt;head&gt;
  &lt;script src='https://cdn.firebase.com/js/client/1.0.17/firebase.js'&gt;&lt;/script&gt;
  &lt;script src='https://ajax.googleapis.com/ajax/libs/jquery/1.9.0/jquery.min.js'&gt;&lt;/script&gt;
&lt;/head&gt;
&lt;body&gt;
  &lt;input type="text" id="nomeusuario" placeholder="Seu nome..."&gt;
  &lt;input type="text" id="mensagem" placeholder="Sua mensagem..."&gt;
  &lt;script&gt;
    var APP = new Firebase('https://seu-app.firebaseIO.com/');

    $('#mensagem').keypress(function (e) {
      if (e.keyCode == 13) {

        var msg = $('#mensagem').val();
        var usr = $('#nomeusuario').val();
        APP.push({ nomeusuario: usr, mensagem: msg });

        $('#mensagem').val('');
      }
    });
  &lt;/script&gt;
&lt;/body&gt;
&lt;/html&gt;
</pre>

Com o que foi construído até agora, já conseguimos que as mensagens cheguem até o servidor. Para conferir este resultado basta acessar o _Dashboard_ da sua conta no **Firebase** e selecionar seu app. 

Nessa página é possível ver uma representação gráfica da fila de objetos que está sendo criada quando você envia as mensagens, como na imagem a seguir: 

<img class="aligncenter size-full wp-image-43526" src="http://tableless.com.br/uploads/2014/07/Captura-de-Tela-2014-07-16-às-00.52.241.png" alt="Captura de Tela 2014-07-16 às 00.52.24" srcset="uploads/2014/07/Captura-de-Tela-2014-07-16-às-00.52.241.png 1344w, uploads/2014/07/Captura-de-Tela-2014-07-16-às-00.52.241-198x139.png 198w, uploads/2014/07/Captura-de-Tela-2014-07-16-às-00.52.241-400x279.png 400w" sizes="(max-width: 1344px) 100vw, 1344px" />

Entretanto, ainda precisamos mostrar essas mensagens para todos usuários conectados ao chat em seus navegadores. 

## Recebendo as mensagens

Garantir que todos usuários do seu chat recebam todas as mensagens é muito simples, basta ouvir ao evento `child_added` da biblioteca do **Firebase**. Este evento evento é disparado sempre que uma nova mensagem é enviada ao servidor e sua função de _callback_ recebe como parâmetro o objeto que contém as informações dessa mensagem. Escrevemos o seguinte código para tal operação: 

<pre class="lang-javascript">APP.on('child_added', function(snap) {
  var novamensagem = snap.val(); //Nova mensagem recebida.
});
</pre>

Em seguida criamos uma `div` para carregar as mensagens na página e criamos uma função para adicionar as mensagens recebidas dentro dessa `div`. Com o auxílio do **jQuery** podemos escrever o seguinte: 

<pre class="lang-javascript">function carregaMensagem(nome, mensagem) {
  $('&lt;div/&gt;').text(mensagem)
    .prepend($('&lt;strong/&gt;').text(nome + ': '))
    .appendTo($('#mensagens'));

  $('#mensagens')[0].scrollTop = $('#mensagens')[0].scrollHeight;
};
</pre>

Agora podemos utilizar essa função para carregar a mensagem na página utilizando o _handler_ que criamos para o evento `child_added` da seguinte maneira: 

<pre class="lang-javascript">APP.on('child_added', function(snap) {
  var novamensagem = snap.val(); //Nova mensagem recebida.
  carregaMensagem(novamensagem.nomeusuario, novamensagem.mensagem);
});
</pre>

Com isso, temos o seguinte resultado final: 

<pre class="lang-html">&lt;html&gt;
&lt;head&gt;
  &lt;script src='https://cdn.firebase.com/js/client/1.0.17/firebase.js'&gt;&lt;/script&gt;
  &lt;script src='https://ajax.googleapis.com/ajax/libs/jquery/1.9.0/jquery.min.js'&gt;&lt;/script&gt;
&lt;/head&gt;
&lt;body&gt;
  &lt;div id='mensagens'&gt;&lt;/div&gt;
  &lt;input type="text" id="nomeusuario" placeholder="Seu nome..."&gt;
  &lt;input type="text" id="mensagem" placeholder="Sua mensagem..."&gt;
  &lt;script&gt;
    var APP = new Firebase('https://seu-app.firebaseIO.com/');

    $('#mensagem').keypress(function (e) {
      if (e.keyCode == 13) {

        var msg = $('#mensagem').val();
        var usr = $('#nomeusuario').val();
        APP.push({ nomeusuario: usr, mensagem: msg });

        $('#mensagem').val('');
      }
    });

    APP.on('child_added', function(snap) {
      var novamensagem = snap.val(); //Nova mensagem recebida.
      carregaMensagem(novamensagem.nomeusuario, novamensagem.mensagem);
    });

    function carregaMensagem(nome, mensagem) {
      $('&lt;div/&gt;').text(mensagem)
        .prepend($('&lt;strong/&gt;').text(nome + ': '))
        .appendTo($('#mensagens'));

      $('#mensagens')[0].scrollTop = $('#mensagens')[0].scrollHeight;
    };
  &lt;/script&gt;
&lt;/body&gt;
&lt;/html&gt;
</pre>

E é isso, seu chat está pronto! 

Caso não esteja funcionando como previsto, confira se seu app foi criado corretamente no **Firebase** e sua _url_ foi inserida corretamente no seu código, e também se o **jQuery** foi importado na sua página. 

Este é apenas um pequeno exemplo de aplicação do **Firebase**, então não deixe de visitar a <a href="https://www.firebase.com/docs/" rel="noreferrer">documentação</a> para descobrir outros recursos e informações sobre essa plataforma, assim como outros exemplos de aplicações.

 [1]: https://www.firebase.com/