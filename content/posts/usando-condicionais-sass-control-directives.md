---
title: Usando condicionais no Sass – Control Directives
author: Diego Eis
type: post
date: 2014-08-25
excerpt: Saiba como funcionam as condicionais if, else, while, for e each no SASS.
url: /usando-condicionais-sass-control-directives/
dsq_thread_id: 2919289861
categories:
  - CSS
  - SASS
tags:
  - condicionais
  - CSS
  - SASS

---
Ter a possibilidade de usar condicionais no CSS é uma daquelas coisas que fazem os pré-processadores de CSS tão sensuais.

No Sass essas condicionais são chamadas de [\*\*Diretivas de controle\*\*][1], ou em inglês, que é mais chique, &#8220;Control Directives&#8221;. As funções são **@if**, **@for**, **@each** e **@while**. São as condicionais tradicionais que estamos acostumados a usar nas outras linguagens.

## @if

Se algo for qualquer coisa diferente de falso, execute determinado comando.

Um uso bastante simples é da própria documentação do Sass:

<pre class="lang-sass">$type: monster;
p {
  @if $type == ocean {
    color: blue;
  } @else if $type == matador {
    color: red;
  } @else if $type == monster {
    color: green;
  } @else {
    color: black;
  }
}
</pre>

Como era de se esperar, existe um **@else** para nos dar todo o apoio. Esse exemplo acima é bastante simples. Se você tem uma variável qualquer, no nosso caso **monster**, e essa variável pode mudar de valor em determinado lugar do código. Se mudar, há uma série de condições ali.

Um exemplo mais real:

<pre class="lang-sass">$color1: #f9f9f9;
p {
	@if (lightness($color1) &lt; 30) {
  	background-color: white
	} @else {
  	background-color: black
	}
}
</pre>

Ali estamos medindo a quantidade de branco que há na variável **$color1**, que irá receber um código de cor. Se for menor que 30% de luz (claridade), background black no elemento, caso contrário, background white.

## @for

Inicia uma variável e executa uma ação, incrementando essa variável um determinado número de vezes. Para cada repetição, um a variável de contador é usada para ajustar o código de saída.

Muito útil. Para você fazer códigos como o de baixo:

<pre class="lang-css">.item-1 {
  width: 10px;
  font-size: 10px; 
}
.item-2 {
  width: 20px;
  font-size: 20px; 
}
.item-3 {
  width: 30px;
  font-size: 30px; 
}
.item-4 {
  width: 40px;
  font-size: 40px; 
}
</pre>

Você faria uma condição assim:

<pre class="lang-sass">@for $i from 1 through 4 {
  .item-#{$i} { 
		width: 10px * $i; 
		font-size: 10px * $i;
	}
}
</pre>

Outro truque interessante é que se você colocar o primeiro número maior que o segundo, assim: `@for $i from 4 through 1`, a função irá decrementar em vez de incrementar a variável. O resultado:

<pre class="lang-css">.item-4 {
  width: 40px;
  font-size: 40px; 
}

.item-3 {
  width: 30px;
  font-size: 30px; 
}

.item-2 {
  width: 20px;
  font-size: 20px; 
}

.item-1 {
  width: 10px;
  font-size: 10px; 
}
</pre>

Simple like that.

## @each

Define uma variável para item de uma lista de valores, produzindo blocos de código utilizando os valores da lista.

Neste artigo fala sobre [Maps Structure do Sass][2], e dá uma boa noção do que o **@each** pode fazer. Mas um exemplo rápido. Para um código assim:

<pre class="lang-css">.tema-azul body {
  background-color: #0176bb;
}

.tema-vermelho body {
  background-color: #e3413e;
}

.tema-amarelo body {
  background-color: #f8e042;
}
</pre>

Você teria um Sass assim:

<pre class="lang-sass">$cores: (
  azul: #0176bb, 
  vermelho: #e3413e, 
  amarelo: #f8e042
);

@each $tema, $cor in $cores {
  .tema-#{tema} body {
     background-color: $cor;
  }
}
</pre>

Você gerencia basicamente um bloco de CSS e as variáveis para adicionar ou remover cores.

## @while

Repete um determinado bloco e código enquanto determinado estado for verdadeiro.

O exemplo mais bacana que pode ser mostrado aqui é a criação de um grid básico. Para ter um código como este abaixo:

<pre class="lang-css">.column-grid-1{
  width: 60px;
}

.column-grid-2 {
  width: 150px;
}

.column-grid-3 {
  width: 240px;
}

.column-grid-4 {
  width: 330px;
}

.column-grid-5 {
  width: 420px;
}

.column-grid-6 {
  width: 510px;
}

.column-grid-7 {
  width: 600px;
}

.column-grid-8 {
  width: 690px;
}

.column-grid-9 {
  width: 780px;
}

.column-grid-10 {
  width: 870px;
}

.column-grid-11 {
  width: 960px;
}

.column-grid-12 {
  width: 1050px; 
}

</pre>

O código seria algo mais ou menos assim:

<pre class="lang-sass">$i: 1
$column-width: 60px

@while $i &lt; 13 {
  .grid-#{$i} { 
    column-width: $column-width; 
   }
  $column-width: $column-width + 90px;
  $i: $i + 1;
}
</pre>

Claro, para fazer um grid um pouco mais complexo, usando porcentagens, guardando o valor do gutter em uma variável, roas e etc você precisa de um pouco mais. [Veja esse artigo aqui][3].

## Conclusão

Eu não gosto de usar pré-processadores. [Eu já falei disso aqui há muito tempo][4]. Se você for fazer um site simples, sem muitas grandes ambições, nada muito complicado, talvez não seja necessário usar um Sass da vida. Contudo, em várias ocasiões, ter essas e outras funções que citamos aqui, o ganho na produtividade é enorme. Aí sim esses penduricalhos começam a valer a pena. 😉

 [1]: http://sass-lang.com/documentation/file.SASS_REFERENCE.html#control_directives__expressions "Control Directives"
 [2]: http://tableless.com.br/utilizando-maps-sass/
 [3]: http://bjorkoy.com/2010/05/css-grids-with-sass/
 [4]: http://tableless.com.br/pre-processadores-usar-ou-nao-usar/