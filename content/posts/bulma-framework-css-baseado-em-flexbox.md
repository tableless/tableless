---
title: 'Bulma: framework CSS baseado em flexbox'
author: Gabriel Prates
type: post
date: 2016-06-28
url: /bulma-framework-css-baseado-em-flexbox/
titulo_personalizado:
  - 'Um grid feito com <strong>flexbox</strong>'
categories:
  - CSS
  - CSS3
  - Destaques
  - SASS

---
> &#8220;Inspirado pelo Bootstrap, o Bulma visa oferecer a todos a alegria de fazer o design do site, com a simplicidade do flexbox e a elegância de Sass.&#8221; &#8211; [Jeremy Thomas][1], criador do projeto Bulma.io.

&nbsp;

Como o título diz, o [Bulma][2] é um framework CSS baseado na tecnologia flexbox, que já tem uma grande [compatibilidade][3] entre os navegadores. O pacote contém todos os elementos mais comuns como botões, formulários, menus, tabelas, títulos, notificações, barras de progresso e um simples sistema de grid (basta adicionar uma coluna, o resize das colunas é automático).

Vou mostrar alguns exemplos para que você possa entender o poder do Bulma.

Primeiramente, faremos a instalação que não precisa de nada mais que um link para o arquivo de estilos do Bulma:

<pre class="lang-html">&lt;link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/bulma/0.0.26/css/bulma.css"&gt;
</pre>

Claro que você pode baixar e deixar no seu diretório local, e também baixar com o NPM: `npm install bulma`; mas o que quero mostrar é que tudo que você precisa é apenas de um arquivo de CSS.

Baixando com o NPM você terá como personalizar facilmente com SASS.

O Bulma não vem com nenhum pacote de icon-fonts acoplado, então, caso você pretenda usar algum, como o Font Awesome, você deve inserí-lo também.

## O Grid

Lembrando: como o Bulma foi baseado no Bootstrap, uma das semelhanças é o sistema de grid com 12 colunas.

Como falei, o grid funciona de forma muito simples. Tudo que você precisa é ter uma `div` com a classe `.columns` e suas filhas `.column`, como no exemplo abaixo:

<pre class="lang-html">&lt;div class="columns"&gt;
  &lt;div class="column"&gt;.column&lt;/div&gt;
  &lt;div class="column"&gt;.column&lt;/div&gt;
  &lt;div class="column"&gt;.column&lt;/div&gt;
  &lt;div class="column"&gt;.column&lt;/div&gt;
&lt;/div&gt;
</pre>

Você pode entender melhor como funciona com [esse exemplo][4].

Mas e se você quiser que uma coluna ocupe o espaço de duas? Ou três? Ou quatro? Simples!!!

Podemos utilizar as classes `is-2`, `is-3`, `is-4`, `is-5`, `is-6`, `is-7`, `is-8`, `is-9`, `is-10` e `is-11` para especificar qual a área ocupada pela `.column`.

Para entender melhor, aconselho a dar uma olhada [neste][5] e [neste][6] links.

## Hero

Você já teve problemas com alinhar elementos verticalmente ao centro? O Bulma é um verdadeiro herói para essas situações! Veja este exemplo:

<pre class="lang-html">&lt;section class="hero is-large"&gt;
    &lt;div class="hero-body"&gt;
      &lt;div class="container"&gt;
        &lt;h1 class="title"&gt;
          Título
        &lt;/h1&gt;
        &lt;h2 class="subtitle"&gt;
          Exemplo do uso do hero
        &lt;/h2&gt;
      &lt;/div&gt;
    &lt;/div&gt;
  &lt;/section&gt;
</pre>

Aqui o Bulma centraliza os títulos na vertical, qualquer conteúdo seria alinhado também. [Clique aqui][7] mais exemplos.

## Level

Por último, quero falar um pouco sobre as navbars. Veja esse código:

<pre class="lang-html">&lt;nav class="level"&gt;
    &lt;p class="level-item has-text-centered"&gt;
      &lt;a class="link is-info"&gt;Home&lt;/a&gt;
    &lt;/p&gt;
    &lt;p class="level-item has-text-centered"&gt;
      &lt;a class="link is-info"&gt;Menu&lt;/a&gt;
    &lt;/p&gt;
    &lt;p class="level-item has-text-centered"&gt;
      &lt;img src="http://bulma.io/images/bulma.png" alt="" style="height: 33px;"&gt;
    &lt;/p&gt;
    &lt;p class="level-item has-text-centered"&gt;
      &lt;a class="link is-info"&gt;Reservations&lt;/a&gt;
    &lt;/p&gt;
    &lt;p class="level-item has-text-centered"&gt;
      &lt;a class="link is-info"&gt;Contact&lt;/a&gt;
    &lt;/p&gt;
  &lt;/nav&gt;

</pre>

Ele gera uma navbar em que os elementos são divididos com a largura igual e com alinhamento vertical no centro, mesmo com imagem ou até mesmo um `form`, ele manteria esse alinhamento.

Veja mais [aqui][8].

## Enfim&#8230;

Estes foram alguns exemplos do poder do Bulma mas há muito mais que você pode conferir na própria [documentação do projeto][9].

Existem vários componentes legais, como cards, menus, paginação, mensagens, e várias outras coisas fáceis de usar e simples de compreender.

Isso é tudo pessoal (:

 [1]: http://jgthms.com/
 [2]: http://bulma.io/
 [3]: http://caniuse.com/#search=flexbox
 [4]: http://codepen.io/gabsprates/full/PNVJrP/
 [5]: http://bulma.io/documentation/grid/columns/
 [6]: http://bulma.io/documentation/grid/tiles/
 [7]: http://bulma.io/documentation/layout/hero/
 [8]: http://bulma.io/documentation/components/level/
 [9]: http://bulma.io/documentation/overview/start/