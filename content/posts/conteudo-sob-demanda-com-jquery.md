---
title: Conteúdo sob demanda com jQuery
author: Davi Ferreira
type: post
date: 2011-04-19
excerpt: Veja como exibir o conteúdo do seu site acabando com a necessidade de paginação e atualização da página.
url: /conteudo-sob-demanda-com-jquery/
tweetbackscheck:
  - 1356413464
shorturls:
  - 'a:3:{s:9:"permalink";s:55:"http://tableless.com.br/conteudo-sob-demanda-com-jquery";s:7:"tinyurl";s:26:"http://tinyurl.com/3eqvk69";s:4:"isgd";s:19:"http://is.gd/OWnGrs";}'
twittercomments:
  - 'a:12:{i:131435907017478144;s:7:"retweet";i:131374410035765248;s:7:"retweet";i:131362657344303104;s:7:"retweet";i:131358684302422016;s:7:"retweet";i:131344200401821696;s:7:"retweet";i:131343466121805824;s:7:"retweet";i:131342785608556544;s:7:"retweet";i:131341845082013696;s:7:"retweet";i:131341779235647488;s:7:"retweet";i:144800582710988800;s:7:"retweet";i:167415950839267328;s:7:"retweet";i:279221338042929152;s:7:"retweet";}'
tweetcount:
  - 38
dsq_thread_id: 503014231
categories:
  - JavaScript
  - JQuery
  - Técnicas e Práticas
tags:
  - JavaScript
  - JQuery

---
Nem sempre uma paginação é a melhor maneira de limitar o conteúdo exibido em um site. Às vezes pode ser bem chato ficar indo de página em página procurando alguma coisa, você acaba se perdendo. O Twitter é um bom exemplo. Na interface do aplicativo, o botão &#8220;load more&#8221; faz as vezes de uma paginação e carrega a próxima sequência de tweets em sua timeline.

Neste artigo, além do link para carregar os próximos conteúdos, veremos também uma abordagem mais dinâmica onde o conteúdo é carregado assim que o scroll atinge o final da página.

E por falar em Twitter, nossos exemplos utilizarão sua API para carregar os dados de exemplo, mas é claro que eles funcionam com qualquer script que forneça os dados em JSON.

### Carregando tweets

A API do Twitter oferece a possibilidade de baixar os últimos tweets de um usuário utilizando apenas JavaScript. A API oferece opção de saída em vários formatos, entre eles XML, Atom e JSON (formato utilizado em nosso exemplo).

Na nossa chamada ajax passamos ainda o nome da conta no Twitter e o número da página dos tweets.

<pre class="lang-javascript">var usuario = 'tableless';
var formato = 'json';
var url = 'http://api.twitter.com/1/statuses/user_timeline.'+formato+"?callback=?";

$.getJSON(url, {screen_name:usuario, page:pagina}, function(tweets){
  // nosso código
});
</pre>

O retorno, o objeto com os tweets:

<pre class="lang-javascript">[
   {
      "favorited":false,
      "text":"http:\/\/bit.ly\/esqJUw Trabalha com TI?\u00a0N\u00e3o importa seu campo de atua\u00e7\u00e3o, confira essa oportunidade da Intel\u00a0 #ad",
      "retweet_count":0,
      "in_reply_to_screen_name":null,
      "in_reply_to_status_id_str":null,
      "place":null,
      "contributors":null,
      "retweeted":false,
      "in_reply_to_user_id":null
     ...
  }
]
</pre>

### Load more

Vamos então ao nosso primeiro exemplo, o botão para carregar mais tweets. Ao acessar a página são carregados automaticamente 12 tweets e os novos tweets só são carregados quando o usuário clica no link.

O HTML, que também será utilizado em nosso segundo exemplo, é esse:

<pre class="lang-html">&lt;ul id="lista-tweets"&gt;&lt;/ul&gt;

&lt;a href="#" id="carrega-tweets"&gt;Mais!&lt;/a&gt;
</pre>

O primeiro passo é associar a função para exibir mais tweets ao elemento &#8220;#carrega-tweets&#8221;, impedindo também o funcionamento padrão do clique (que nesse caso seria ir para o link &#8220;#&#8221;) com o método preventDefault.

<pre class="lang-javascript">$('#carrega-tweets').click(function(e){
  retorna_tweets($(this).data('pagina'));
  e.preventDefault();
});
</pre>

Ao clicar no link, nosso site executa a funcão retorna_tweets, recebendo como parâmetro a página dos tweets a serem carregados. A página fica armazenada no próprio elemento e é incrementada toda vez que ocorre um clique (o método data merece um outro artigo, por isso não vou falar muito sobre ele aqui).

<pre class="lang-javascript">function retorna_tweets(pagina){
  $('#carrega-tweets').hide();
  $('#lista-tweets').append('

<li class="carregando">
  Aguarde, carregando...
</li>');
  var screen_name = 'tableless';
  var formato = 'json';
  var url = 'http://api.twitter.com/1/statuses/user_timeline.'+formato+"?callback=?";

  $.getJSON(url, {screen_name:screen_name, page:pagina}, function(tweets){
    $('.carregando').fadeOut(function(){
      for(x in tweets)
        $('#lista-tweets').append('

<li>
  '+tweets[x].text+'
</li>');
      $(this).remove();
      $('#carrega-tweets').data('pagina', pagina + 1).fadeIn();
    });
  });
}
</pre>

A função retorna_tweets segue o seguinte fluxo:

  1. Oculta o link de carregamento para evitar que a ação seja executada mais de uma vez ao mesmo tempo; <pre class="lang-javascript">$('#carrega-tweets').hide();
</pre>

  2. Adiciona um ítem à lista de tweets para informar ao usuário que o conteúdo está sendo carregado; <pre class="lang-javascript">$('#lista-tweets').append('

<li class="carregando">
  Aguarde, carregando...
</li>');
</pre>

  3. Através do método getJSON, recebe a lista de tweets da conta informada (no nosso caso, a conta do Tableless); <pre class="lang-javascript">$.getJSON(url, {screen_name:screen_name, page:pagina}, function(tweets){
</pre>

  4. Quando a API termina de enviar os dados pra gente, escondemos e removemos o loader e ao mesmo tempo adicionamos ítems à lista com o texto de cada tweet; <pre class="lang-javascript">$('.carregando').fadeOut(function(){
  for(x in tweets)
    $('#lista-tweets').append('

<li>
  '+tweets[x].text+'
</li>');
    $(this).remove();
});
</pre>

  5. E, finalmente, incrementamos o número da página atual no link e voltamos a exibí-lo. <pre class="lang-javascript">$('#carrega-tweets').data('pagina', pagina + 1).fadeIn();
</pre>

### Infinite Scrolling

Outra maneira interessante é carregar o conteúdo quando o scroll atinge o final da página. Essa abordagem é um pouco mais agressiva já que o usuário não tem total controle sobre o conteúdo que deseja ver. Por outro lado, ele não precisa se preocupar em clicar em nada para exibir mais conteúdo.

<pre class="lang-javascript">var ajax = "";
$(function(){
  retorna_tweets(1);
  $('body').data('pagina', 1);
  inicializa_scroll();
});

function inicializa_scroll(){
  $(window).scroll(function() {
    if(($(window).scrollTop() + $(window).height() + 20) &gt;= $(document).height()) {
      $(window).unbind('scroll');
      ajax.abort();
      retorna_tweets($('body').data('pagina'));
    }
  });
}
</pre>

Nesse caso, como não possuímos um link, armazenamos o número da página a ser carregada no elemento body e iniciamos, é claro, o carregamento com a página 1. A função inicializa_scroll é responsável por associar o evento scroll da janela com nosso carregamento de tweets.

Dois detalhes importantes de usabilidade: quando o carregamento é executado nós removemos a associação do método scroll da janela para evitar duplicidades ($(window).unbind(&#8216;scroll&#8217;)) e, além disso, interrompemos alguma chamada anterior (ajax.abort();). A variável global ajax foi criada no início do nosso javascript e ela vai receber a chamada ajax na função retorna_tweets.

Vamos analisar agora a comparação do scroll com a altura do documento:

<pre class="lang-javascript">$(window).scrollTop() + $(window).height() + 20) &gt;= $(document).height()
</pre>

O método scrollTop retorna a altura da parte oculta da página, que está acima da parte atual, acima do scroll. Já a chamada $(window).height() retorna a altura do viewport, da parte visível da página. A soma dos dois, quando o scroll está no final da página, resulta em $(document).height(), que é a altura total do documento. Alguns navegadores apresentam diferenças mínimas nesses valores, entre 1 e 5px. Por isso o adicionamos 20 pixels para uma &#8220;margem de erro&#8221;. 

Pra finalizar, o método retorna\_tweets sofreu algumas alterações com relação ao nosso primeiro exemplo. A primeira é a incrementação do número da página nos dados do elemento body e não em um link. Também armazenamos nossa chamada getJSON na variável ajax, conforme citado anteriormente. E, ao invés de exibir novamente o link, associamos novamente a função retorna\_tweets ao scroll da janela através do método inicializa_scroll.

<pre class="lang-javascript">function retorna_tweets(pagina){
  $('#lista-tweets').append('

<li class="carregando">
  Aguarde, carregando...
</li>');

  var screen_name = 'tableless';
  var url = 'http://api.twitter.com/1/statuses/user_timeline.json?callback=?';

  $('body').data('pagina', pagina + 1);

  ajax = $.getJSON(url, {screen_name:screen_name, page:pagina}, function(tweets){
    $('.carregando').fadeOut(function(){
      for(x in tweets)
        $('#lista-tweets').append('

<li>
  '+tweets[x].text+'
</li>');
      inicializa_scroll();
      $(this).remove();
    });
  });
}
</pre>