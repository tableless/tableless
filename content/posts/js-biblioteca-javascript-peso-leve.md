---
title: 'Zepto.js: JavaScript peso-leve'
author: Davi Ferreira
type: post
date: 2013-03-20
excerpt: Inicialmente lançado para aplicações mobile, o framework Zepto.js começa a ganhar espaço também no desktop graças ao seu peso reduzido e a sua alta compatibilidade com jQuery.
url: /zepto-js-biblioteca-javascript-peso-leve/
dsq_thread_id: 1149184803
categories:
  - JavaScript
  - JQuery
tags:
  - 2013
  - JavaScript
  - JQuery
  - zepto

---
Em tempos em que performance é muito valorizada, a escolha de bibliotecas e plugins extras influencia diretamente no peso do seu site ou aplicativo. 

Com aproximadamente 10kb em sua versão minificada (jQuery, por exemplo, tem 94kb), o framework **Zepto.js** pode ser o mais indicado para quem deseja melhorar a performance e manter a compatibilidade com a API do jQuery.

## Se você sabe jQuery, você já sabe Zepto

Além de ser leve, o Zepto.js é também compatível com a maioria dos métodos jQuery. Todos os seletores e métodos para manipulação de CSS/HTML são praticamente idênticos.

No entanto, é importante frisar que o framework Zepto.js não é 100% compatível (e nem pretende ser) com a API do jQuery. Alguns métodos, inclusive, possuem assinaturas diferentes.

## Funciona apenas em browsers modernos

Para ser leve, o código do Zepto.js precisou abdicar de _hacks_ e _workarounds_ para navegadores mais antigos. Seu foco é funcionar em browsers modernos, tanto em suas versões desktop como mobile.

O _fallback_ para fazer uso do framework nos navegadores mais antigos é aplicar o seguinte trecho de código:

<pre class="lang-javascript">&lt;script&gt;
document.write('&lt;script src=' +
('__proto__' in {} ? 'zepto' : 'jquery') +
'.js&gt;&lt;\/script&gt;')
&lt;/script&gt;</pre>

Caso o navegador não dê suporte à propriedade **proto** em objetos JavaScript, o framework carregado será o jQuery.

## Base

Os métodos do core do Zepto são muito parecidos com os métodos do core do jQuery. Por exemplo, para alterar o html de um elemento, utilizamos o seguinte código: 

<pre class="lang-javascript">$('#home').html('&lt;a href="index.html"&gt;home&lt;/a&gt;');</pre>

Para alterar o CSS de um ou mais elementos com a classe _item-menu_:

<pre class="lang-javascript">$('.item-menu').css('background-color', 'red');</pre>

Ou ainda:

<pre class="lang-javascript">$('.item-menu').css({backgroundColor: 'red', color: '#fff'});</pre>

Para adicionar um novo elemento a um elemento existente:

<pre class="lang-javascript">$('&lt;a href="index.html"&gt;home&lt;/a&gt;').appendTo('nav');</pre>

Notaram a semelhança com jQuery? Esse é um dos pontos fortes do Zepto.js, uma curva de aprendizado quase nula para quem já desenvolve com jQuery.

## Eventos & Efeitos

A associação de eventos também segue a API do jQuery:

<pre class="lang-javascript">$('a').on('click', function(e){ console.log('clique'); });
$('#home').click(function(e){ e.preventDefault(); });</pre>

A parte de efeitos é composta do objeto **$.fx**, responsável pelas configurações globais de animação e do método _animate_:

<pre class="lang-javascript">$("#top-nav").animate({
  marginTop: '30px',
  backgroundColor: '#000',
  rotateX: '10deg'
}, 300, 'linear')</pre>

A diferença principal é que as animações do framework Zepto.js são todas feitas utilizando transições e transformações CSS3.

## Ajax

Assim como o módulo de efeitos, as configurações globais para Ajax também ficam armazenadas em um objeto, o **$.ajaxSettings**. É possível alterar o tipo padrão de requisição (o default é GET), o timeout, o tipo de dados entre outros.

Também é possível configurar os callbacks para as seguintes operações: _beforeSend_, _success_, _error_ e _complete_.

Chamadas Ajax são realizadas utilizando o método **$.ajax** ou seus atalhos **$.get**, **$.post** e **$.getJSON**.

<pre class="lang-javascript">$.post('/projeto/novo', {titulo: 'Novo projeto'}, function(response){
  console.log('Projeto criado com sucesso');
});</pre>

As operações Ajax também disparam eventos que podem ser utilizados por elementos da sua aplicação, entre eles _ajaxStart_, _ajaxError_ e _ajaxComplete_.

<pre class="lang-javascript">$(document).on('ajaxError', function(e, xhr, options, error){
  console.log(';Erro: '; + error);
});</pre>

O trecho de código acima captura qualquer evento de erro disparado por uma chamada Ajax e exibe o motivo do erro no console.

## Touch & Mobile

Originalmente criado para atender especificamente dispositivos mobile, o framework Zepto.js oferece suporte aos seguintes eventos de dispositivos de toque:

  * tap, singleTap, doubleTap e longTap 
  * swipe, swipeLeft, swipeRight, swipeUp, swipeDown 

Os eventos são associados como qualquer outro tipo de evento:

<pre class="lang-javascript">$('#home').tap(function() {
  $(';.home-nav';).toggle();
});

$('#galeria').swipe(function() {
  $(this).animate({marginLeft: "-100px"}, 300, "ease-out");
});</pre>

O módulo touch é opcional e não acompanha o build default do Zepto.js.

## Plugins

Como era de se esperar, o desenvolvimento de plugins para Zepto.js segue o padrão jQuery de estender o objeto $.fn:

<pre class="lang-javascript">$.extend($.fn, {
  meuPlugin: function(){&lt;/p>
  // this é a coleção obtida no seletor
  return this;
});</pre>

A base de plugins ainda é infinitamente menor do que a base de plugins jQuery. O desenvolvedor brasileiro Jean Carlo Emer possui dois plugins interessantes que podem servir de base para você criar os seus próprios plugins:

  * [Zepto Carousel][1] 
  * [Zepto Range][2] 

## Referências

  * _Site oficial:_ [zeptojs.com][3]
  * _Código-fonte:_ [github.com/madrobby/zepto][4]

 [1]: http://jcemer.com/zepto-carousel/
 [2]: http://jcemer.com/zepto-range/
 [3]: http://zeptojs.com/
 [4]: https://github.com/madrobby/zepto