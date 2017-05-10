---
title: 'jQuery: métodos desconhecidos'
author: Davi Ferreira
type: post
date: 2012-01-31
excerpt: Conheça alguns métodos pouco utilizados mas que podem ser grandes aliados dos desenvolvedores jQuery.
url: /jquery-metodos-desconhecidos/
tweetbackscheck:
  - 1356439207
shorturls:
  - 'a:3:{s:9:"permalink";s:31:"http://tableless.com.br/?p=5315";s:7:"tinyurl";s:26:"http://tinyurl.com/7sf6yg3";s:4:"isgd";s:19:"http://is.gd/3omKze";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 559084614
categories:
  - JavaScript
  - JQuery
  - Técnicas e Práticas
tags:
  - 2012
  - JavaScript
  - JQuery

---
No meu [último artigo][1] falei sobre dicas de otimização e performance de códigos jQuery. Na versão inicial do texto eu havia planejado um tópico sobre os métodos não muito conhecidos, já que alguns, como o ajaxSetup, podem também atuar na performance da sua aplicação.

Acabei descobrindo que este tópico ficaria enorme e, por isso, preferi escrever sobre o assunto em um artigo próprio.

Com vocês, alguns dos métodos menos populares do jQuery!

## proxy()

O método proxy() permite executar um outros método forçando um determinado contexto. Seu objetivo principal é evitar a confusão do &#8216;this&#8217; causada quando um objeto é utilizado dentro de um método de outro objeto.

Por exemplo:

<pre class="lang-javascript">$(".botao").click(function() {
  setTimeout(function() {
    console.log(this); //window
  }, 400);
});

$(".botao").click(function() {
  setTimeout($.proxy(function() {
    console.log(this); //.botao
  }, this), 400);
});
</pre>

É possível utilizar o proxy() através de duas assinaturas. A primeira recebe como parâmetros uma função e o escopo. A segunda funciona passando o escopo e o nome do método como uma string.

<pre class="lang-javascript">$.proxy( funcao(){}, 'objeto' );
$.proxy( 'objeto', 'metodo' );
</pre>

Quem sabe agora você para de usar o truque do &#8216;var that = this&#8217;, hein?

## isArray() e isFunction()

Esses dois métodos fazem parte da família de utilitários do jQuery. Como seus nomes sugerem, o primeiro verifica se o objeto é um array JavaScript e o segundo se o objeto é uma função.

<pre class="lang-javascript">var jogadores = ['Obina', 'Vagner Love', 'Zico'];
var chutar = function(jogador){
  console.log("Gol de " + jogadores[jogador]);
};
console.log($.isArray(jogadores)); // true
console.log($.isFunction(chutar)); // true
</pre>

Uma observação: a função isArray retorna _true_ apenas para verdadeiros Arrays (e não objetos &#8220;tipo array&#8221;, como um objeto jQuery, por exemplo).

<pre class="lang-javascript">var jogadores = $('.jogadores');
console.log($.isArray(jogadores)); // false
</pre>

A [lista de utilitários][2] possui outros métodos interessantes, tais como grep(), map(), merge() etc. 

## queue() e dequeue()

Apesar de terem sido desenvolvidos originalmente para o uso de animações, os métodos queue() e dequeue() podem ser utilizados para qualquer tipo de fila.

A fila padrão é chamada de &#8216;fx&#8217;: essa é a fila das animações. Ela será utilziada caso não seja passado nos parâmetros o nome de uma fila. No exemplo abaixo, estamos criando a fila &#8216;ajaxRequests&#8217;.

<pre class="lang-javascript">$(document).queue('ajaxRequests', function(){
  $.ajax({
    type: 'GET',
    url: '/tableless',
    complete: function(jqXHR, textStatus){
      $(document).dequeue("ajaxRequests");
    }
  });
});

$(document).queue('ajaxRequests', function(){
    $.post('/tableless', {categoria: 'jquery'});
});
</pre>

Para dar sequência no andamento da fila, você precisa utilizar o método dequeue(). Ele deve ser chamado no final da execução de um processo da fila (e como essa é uma fila de processos AJAX, utilizamos o dequeue no evento _complete_).

Outro recurso interessante é a possibilidade de saber o tamanho da fila, ou seja, quantos eventos ainda serão executados. Para isso, basta utilizar a propriedade _length_ após o método queue().

<pre class="lang-javascript">$(document).queue('ajaxRequests').length; // 2
$(document).dequeue("ajaxRequests"); // executa fila
$(document).queue('ajaxRequests').length; // 0
</pre>

## detach()

Assim como o remove(), o detach() retira um elemento do DOM. No entanto, esse método guarda as referências, eventos e dados associados ao elemento retornando um objeto jQuery que pode ser re-inserido no DOM.

<pre class="lang-javascript">$('.link').click(function(e){
  e.preventDefault();  
  console.log('clique');
});
$('.link').click(); // 'clique'
var link = $('.link').detach();
$('body').append(link);
$('.link').click(); // 'clique'
$('.link').remove();
$('body').append('&lt;a href="#" class="link"&gt;link&lt;/a&gt;');
$('.link').click(); // []
</pre>

## ajaxSetup() e afins

Talvez esses sejam os métodos mais injustiçados do jQuery. É muito comum a repetição de chamadas AJAX, incluindo seus parâmetros. Esses métodos de configuração permitem definir valores padrão para qualquer evento AJAX em sua aplicação.

Com o ajaxSetup() é possível, por exemplo, habilitar ou desabilitar o _cache_ e definir o tipo de requisição: POST ou GET.

<pre class="lang-javascript">$.ajaxSetup({
  type: 'POST',
  dataType: 'json',
  cache: true
});
</pre>

Você ainda pode configurar uma URL padrão e também parâmetros passados durante a chamada:

<pre class="lang-javascript">$.ajaxSetup({  
  data: {
      origem: 'tableless'
  },
  url: '/tableless'
});
</pre>

Para conferir uma lista completa das propriedades configuráveis, visite a [página do método AJAX na API do jQuery][3].

Os _callbacks_ e eventos relacionados à execução de métodos AJAX também podem ser configurados. No entanto, essa configuração deve ser feita através dos seguintes métodos específicos: ajaxStart(), ajaxStop(), ajaxComplete(), ajaxError(), ajaxSuccess() e ajaxSend(). 

Por exemplo, você poderia utilizar a configuração abaixo para exibir um indicador de carregamento no início da execução de um método AJAX.

<pre class="lang-javascript">$('.carregando')
  .ajaxStart(function(){
    $(this).show();
  })
  .ajaxStop(function(){
    $(this).hide();
  });
</pre>

Você pode associar os eventos a qualquer elemento e o jQuery se encarregará de encontrar e executar todos os métodos associados.

## delay()

O método delay() serve para adiar a execução de uma função, método ou animação. Ele é especialmente útil para controlar o tempo de animações.

<pre class="lang-javascript">$('.alerta').fadeIn().delay(1000).slideUp();
</pre>

No exemplo acima, o elemento com a classe &#8220;alerta&#8221; é exibido através de uma transição _fade_ e, um segundo depois, ocultado através do método slideUp().

## replaceWith() e replaceAll()

Imagine que você queira substituir todos os elementos que tenham a classe &#8220;pontos&#8221;. Com o método replaceWith() fica fácil. O que ele faz é buscar todos os objetos que se encaixem no seletor indicado e substituir seu conteúdo.

<pre class="lang-javascript">$('.pontos').replaceWith('&lt;h2&gt;1 milhão de pontos!&lt;/h2&gt;');
</pre>

O replaceWith() também funciona com elementos que não estejam presentes no DOM, ou seja, você pode criar um objeto jQuery e substituir/manipular seu conteúdo antes de inserí-lo no DOM.

<pre class="lang-javascript">$('&lt;div class="carregando" /&gt;').replaceWith('&lt;p class="carregando"&gt;Carregando...&lt;/p&gt;');
</pre>

Da mesma forma, o método replaceAll() também substiui o conteúdo de elementos, mas a origem e o destino são invertidos. Você também pode passar seletores como conteúdo. Nesse caso o funcionamento é um pouco diferente já que o elemento não é clonado e sim movido no DOM. 

<pre class="lang-javascript">$('&lt;h2&gt;Carregamento completo!&lt;/h2&gt;').replaceAll('.carregando');
$('.titulo').replaceAll('.carregando');
</pre>

Note que a diferença dos métodos acima para os métodos tradiconais html() e text() é que o próprio elemento também é substituído e não só o seu conteúdo.

* * *

Estes foram alguns métodos que pouca gente conhece ou utiliza. Pode até ser que você nunca tenha sentido falta deles, mas é sempre bom ter umas cartas extras na manga.

E se você gostou, garanto que ao consultar a [API do jQuery][4] você descobrirá vários outros métodos desconhecidos, mas que podem ser úteis em algum momento do desenvolvimento dos seus projetos.

 [1]: http://tableless.com.br/jquery-dicas-de-otimizacao-e-performance/ ""
 [2]: http://api.jquery.com/category/utilities/ ""
 [3]: http://api.jquery.com/jQuery.ajax/ ""
 [4]: http://api.jquery.com/ ""