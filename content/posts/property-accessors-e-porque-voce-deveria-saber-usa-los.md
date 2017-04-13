---
title: Property accessors e porque você deveria saber usá-los
author: filipemerker
type: post
date: 2015-09-11
excerpt: Notações diferentes para acessar as propriedades de um mesmo objeto em JavaScript
url: /property-accessors-e-porque-voce-deveria-saber-usa-los/
categories:
  - Código
  - JavaScript
  - Técnicas e Práticas
tags:
  - JavaScript

---
Este é um artigo que se propõe a explicar uma forma mais eficaz de utilizar Objetos em JavaScript.

Muitos talvez conheçam este conteúdo, outros tantos nunca ouviram falar, justamente por aprenderem jQuery antes de aprender JavaScript. Mas enfim, esperamos que todos possam tirar algum proveito desta matéria.

## Lidando com objetos em JavaScript

Um objeto em JavaScript nada mais é do que um array associativo onde cada &#8220;associação&#8221; é uma propriedade do objeto. Isso dito, todo sabemos que para acessar um array, precisamos fornecer um índice. É nesse momento que entram os _property accessors_.

Existem duas notações para acessar o índice desejado em um objeto JavaScript:

<pre class="lang-javascript">var meuObj = {indice1: 'foo', indice2: 'bar'};
//Bracket Notation
meuObj['indice1']; //retorna foo
//Dot Notation
meuObj.indice2;    //retorna bar
</pre>

A notação que acabou se tornando o mais popular é a _Dot Notation_ porque também ela é usada para encadeamento de métodos, por exemplo:

<pre class="lang-javascript">$('.myEl').addClass('sticky').stop().fadeIn();
</pre>

Essa notação é muito poderosa e certamente deve ser adotada como padrão, mas há limitações e casos onde o mais aconselhado é utilizar _Bracket Notation_. Vamos a alguns exemplos:

### Acessando múltiplas propriedades:

Se você utiliza modularização de JavaScript, já deve ter deparado com o seguinte cenário:

<pre class="lang-javascript">var PROD = {};
PROD.clients = {
  init: function(){},
  method1: function(){}
};
PROD.pages = {
  init: function(){},
  method1: function(){}
};
PROD.accounts = {
  init: function(){},
  method1: function(){}
};

//roda tudo
PROD.clients.init();
PROD.pages.init();
PROD.accounts.init();
</pre>

Ok, tudo certo, mas suponhamos que, ao invés de apenas _clients_, _pages_ e _accounts_, como no exemplo acima, eu tenha 15 módulos para iniciar.

<pre class="lang-javascript">//roda tudo
PROD.clients.init();
PROD.pages.init();
PROD.accounts.init();
PROD.wow.init();
PROD.such.init();
PROD.code.init();
PROD.much.init();
PROD.lines.init();
PROD.wowwow.init();
PROD.ta.init();
PROD.ficando.init();
PROD.chato.init();
PROD.isso.init();
PROD.aqui.init();
PROD.chega.init();
</pre>

Mas isso é horrível! E se eu quiser rodar métodos de forma dinâmica? Quem poderá nos ajudar? Aí que entra a beleza do Bracket Notation. Vamos ver duas formas de fazer isso:

<pre class="lang-javascript">//roda tudo
var keys = Object.keys(PROD);
var len  = keys.length;
for(var i = 0; i &lt; len; i++){
  PROD[keys[i]].init();
}
</pre>

O código acima utiliza o método nativo _keys()_ do objeto JavaScript. Esse método retorna um array com todos os índices do nosso objeto. Baseado nisso, fazemos um _for_ para executar o método _init()_ que definimos para cada um dos módulos.

Outra forma de fazer isso é utilizando o _for&#8230;in_. Vejamos:

<pre class="lang-javascript">//roda tudo
for(var key in PROD){
  PROD[key].init();
}
</pre>

Muito melhor, não? Outra possibilidade é você executar apenas os módulos que deseja. Suponhamos que você queira carregar módulos por página, basta fazer:

<pre class="lang-javascript">//roda tudo
var home = ['clients', 'pages', 'wow', 'chato'];
for(var key in home){
  PROD[home[key]].init();
}
</pre>

Quando o laço _for&#8230;in_ é executado em um array, ele retorna como _key_ sempre o índice numérico, logo, nosso código está rodando o método init de cada módulo que tem o nome naquele array. Isso é muito legal.

### Executando métodos de forma dinâmica:

Quando entendemos o conceito, muitas possibilidades se abrem. Vamos a outro exemplo prático: um _sticky menu_. Esses dias me deparei com o seguinte código:

<pre class="lang-javascript">if($(window).scrollTop() &gt; 300){
  $("#header").addClass('sticky');
}else{
  $("#header").removeClass('sticky');
}
</pre>

O que está errado? Nada. Mas poderíamos fazer isso de forma mais simples com _bracket notation_ utilizando um ternário:

<pre class="lang-javascript">var action = ($(window).scrollTop() &gt; 300) ? 'addClass' : 'removeClass';
$('#header')[action]('sticky');
</pre>

Isso é possível porque um objeto jQuery tem as suas propriedades como qualquer outro objeto, logo, nós podemos acessá-las da forma como bem entendermos.

Enfim, estes são apenas exemplos simples da liberdade que temos quando compreendemos de fato como funcionam os _property accessors_. Este simples conceito pode mudar a forma como desenvolvemos e nos fornecer uma liberdade incrível.

E quanto a performance? Nunca tema usar a _Bracket Notation_: ela é mais performática. Veja em <a href="http://jsperf.com/filipe-property-accessors" target="_blank">http://jsperf.com/filipe-property-accessors</a>.

[<img class="alignnone wp-image-50898 size-full" src="http://tableless.com.br/uploads/2015/08/property.jpg" alt="Comparação de performance usando brackets notation" width="683" height="438" />][1]

 [1]: http://tableless.com.br/uploads/2015/08/property.jpg