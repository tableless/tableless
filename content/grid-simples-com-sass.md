---
title: Grid simples com SASS
author: Diego Eis
type: post
date: 2015-04-29
excerpt: Criando um grid simples com SCSS.
url: /grid-simples-com-sass/
categories:
  - SASS
  - Técnicas e Práticas
tags:
  - grid
  - SASS
  - scss

---
Algumas vezes você vai preferir usar um sistema de grid feito por você e não algum framework do mercado como o Bootstrap ou o Foundation. Isso tem suas vantagens e desvantagens. Mas se você preferir um grid presonalizado, fazer isso com SASS é mole.

Existe uma série de soluções em SASS aí fora. Algumas mais completas que essa, mas essa acaba ganhando por ser muito simples, com menos recursos, mas muito funcional para projetos pequenos. 

O HTML básico de exemplo será esse:

<pre class="lang-html">&lt;div class="container"&gt;
  &lt;div class="grid-4"&gt;Coluna de 4&lt;/div&gt;
  &lt;div class="grid-4"&gt;Coluna de 4&lt;/div&gt;
  &lt;div class="grid-4"&gt;Coluna de 4&lt;/div&gt;
&lt;/div&gt;
</pre>

Primeiro, como qualquer sistema de grid em SASS, defina as variáveis que comandarão o gerenciamento do Grid.

<pre class="lang-sass">$grid-gutter: 10px // espaçamento entre as colunas
$grid-columns: 12 // Quantidade de colunas
$grid-max: 980px // Tamanho do container

// Código básico das colunas do grid
[class*="grid-"]
  float: left
  padding: 0 $grid-gutter
  margin-bottom: 20px
</pre>

Agora basta fazer um `for` simples no SASS. Esse for vai calcular a largura de todas as colunas, que no nosso exemplo tem apenas 12:

<pre class="lang-sass">@for $i from 1 through $grid-columns
  .grid-#{$i}
    width: 100% / $grid-columns * $i
</pre>

O output desse `for` é algo mais ou menos assim:

<pre class="lang-css">.grid-1 {
  width: 8.33333%;
}

.grid-2 {
  width: 16.66667%;
}

.grid-3 {
  width: 25%;
}

.grid-4 {
  width: 33.33333%;
}

.grid-5 {
  width: 41.66667%;
}

.grid-6 {
  width: 50%;
}

.grid-7 {
  width: 58.33333%;
}

.grid-8 {
  width: 66.66667%;
}

.grid-9 {
  width: 75%;
}

.grid-10 {
  width: 83.33333%;
}

.grid-11 {
  width: 91.66667%;
}

.grid-12 {
  width: 100%;
}
</pre>

O resultado você pode ver abaixo: