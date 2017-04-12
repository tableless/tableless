---
title: Destaques responsivos
author: Palloi Hofmann
type: post
date: 2014-12-29
excerpt: Estou de volta como prometido anteriormente com uma séria de artigos, hoje criaremos 3 destaques com um comportamento totalmente responsivo.
url: /destaques-responsivos/
categories:
  - Código
  - CSS
  - CSS3
  - HTML
  - Mobile
  - Responsive Web Design (RWD)
  - Técnicas e Práticas
tags:
  - CSS
  - CSS3
  - html
  - página responsiva
  - responsivo

---
Hoje criaremos três destaques com um comportamento totalmente responsivo.

Com um crescimento das SPAs e seguindo o mesmo conceito do artigo anterior, vou passar agora de uma forma simples de como usar, o input radio para transformar nossos destaques em galeria navegável.

## Aproveitando

Como já temos um header responsivo, vamos continuar com a mesma estrutura até o final dos artigos só com css e html. Se você ainda não viu como criar um <a href="http://tableless.com.br/header-responsivo-somente-com-css/" title="Header responsivo somente com css" target="_blank">header responsivo, clique aqui</a>.

## O HTML

Vamos iniciar realocando a foto do Chaves para um novo formato:

<pre class="lang-html">&lt;div class="highlights"&gt;
  &lt;div class="highlights-item"&gt;
    &lt;img src="assets/images/chaves.jpg" /&gt;
    &lt;p&gt;Olha o Chaves sorrindo&lt;/p&gt;
  &lt;/div&gt;

  &lt;div class="highlights-item"&gt;
    &lt;img src="assets/images/chaves-2.jpg" /&gt;
    &lt;p&gt;Pensando na Paty&lt;/p&gt;
  &lt;/div&gt;

  &lt;div class="highlights-item"&gt;
    &lt;img src="assets/images/chaves-3.jpg" /&gt;
    &lt;p&gt;Quero tanto esse sanduiche iche iche&lt;/p&gt;
  &lt;/div&gt;
&lt;/div&gt;
</pre>

Temos um simples html para 3 itens, deixei os nome das classes mais compreensível e semântico, observado pelo amigo Shankar.
  
<a href="http://palloi.github.io/responsive-header-only-css/demo-only-elements.html" target="_blank">Ver demo sem style</a>.

## O CSS

Sempre pensando no responsivo, vamos deixar nossos itens em % para 3 colunas seguindo dessa forma:

<pre class="lang-css">.highlights-item {
  float: left;
  margin: 0 0 0 2%;
  width: 32%;
}

.highlights-item:first-of-type {
  margin-left: 0;
}

.highlights-item img {
  display: block;
  width: 100%;
  margin: 0 0 5px;
}

.highlights-item p {
  font-size: 14px;
  text-align: center;
}
</pre>

Para cada item apliquei 32% em width + 2% em margin-left, se multiplicarmos por 3 a soma é 102% que passa os 100% representado pelo elemento pai. Por estourar o tamanho do pai o terceiro item sempre cai.
  
Então selecionamos o primeiro item para zerar o margin usando o seletor &#8220;:first-of-type&#8221;, por que mais adiante vamos adicionar mais elementos e já evitamos quebrar o css se caso usássemos os &#8220;first-child&#8221;.
  
<a href="http://palloi.github.io/responsive-header-only-css/demo-basic-highlights.html" target="_blank">Ver demo com style</a>.

## O RESPONSIVO

Já apresentada a forma de como usar os seletores, agora vamos adicionar antes de cada item um input radio, veja:

<pre class="lang-html">&lt;div class="highlights"&gt;
  &lt;input type="radio" id="radio-img1" name="highlights" checked="checked" /&gt;
  &lt;div class="highlights-item"&gt;
    &lt;img src="assets/images/chaves.jpg" /&gt;
    &lt;p&gt;Olha o Chaves sorrindo&lt;/p&gt;
  &lt;/div&gt;
  ...
&lt;/div&gt;
</pre>

## O CSS PARA TRANSFORMAR

Com o html simples para 3 colunas, vamos transformar em uma galeria suave com o &#8216;media screen&#8217;, &#8216;transition&#8217; e &#8216;transform&#8217;.

<pre class="lang-css">@media screen and (max-width: 767px) {
  .highlights-item {
    width: 100%;
    margin-left: 0;
    position: absolute;
    top: 0;
    left: 0;
    opacity: 0;
    visibility: hidden;
    -webkit-transition: all 500ms ease-in-out;
    transition: all 500ms ease-in-out;
    -webkit-transform: scale(0.9);
    -ms-transform: scale(0.9);
    transform: scale(0.9);
  }
}
</pre>

Nesse css deixei todos os itens com &#8216;position absolute&#8217;, mas isso faz que todo o conteúdo abaixo dele suba ocupando seu espaço. Mas como teremos um ativo vamos resolver logo abaixo.

Importante lembrar que sempre precisamos de um radio marcado com &#8216;checked&#8217;, quando responder ao responsivo teremos sempre um ativo. Para mostrar o item ativo vamos adicionar as seguintes linhas:

<pre class="lang-css">@media screen and (max-width: 767px) {
   /*checked*/
  .highlights input:checked + div {
    position: relative;
    opacity: 1;
    visibility: visible;
    z-index: 1;
    -webkit-transform: scale(1);
    -ms-transform: scale(1);
    transform: scale(1);
  }
}
</pre>

O item que estiver ativo, recebe o &#8216;position relative&#8217; para bloquear sua área e outras propriedades para exibir suavemente.

Como os type&#8217;s dos input&#8217;s são &#8216;radio&#8217;, teremos somente um &#8216;:checked&#8217; por grupo &#8216;name&#8217;.

## NAVEGAÇÃO COM LABEL

Para selecionar cada radio, precisamos relacionar cada label usando o for e vamos adicionar o seguinte html:

<pre class="lang-html">&lt;div class="highlights"&gt;
  ...
  &lt;input type="radio" id="radio-img3" name="highlights" /&gt;
  &lt;div class="highlights-item"&gt;
    ....
  &lt;/div&gt;

  &lt;div class="highlights-buttons"&gt;
    &lt;label for="radio-img1"&gt;Image 1&lt;/label&gt;
    &lt;label for="radio-img2"&gt;Image 2&lt;/label&gt;
    &lt;label for="radio-img3"&gt;Image 3&lt;/label&gt;
  &lt;/div&gt;
&lt;/div&gt;
</pre>

Por padrão defino &#8216;display none&#8217; para os botões e com resoluções menores 768px mudamos para &#8216;block&#8217; para exibir.

## LABEL E SEU CSS

Agora que adicionamos os label&#8217;s que tem a missão dos botões, vamos inserir uma formatação bem simples.

<pre class="lang-css">.highlights-buttons {
  display: none;
  clear: both;
  text-align: center;
}

.highlights-buttons label {
  display: inline-block;
  width: 15px;
  height: 15px;
  margin: 0 10px; 
  border-radius: 10px;
  background-color: #ccc;
  cursor: pointer;
  position: relative;
  overflow: hidden;
  text-indent: -9999px;
  -webkit-transition: background-color 300ms ease-in-out;
  transition: background-color 300ms ease-in-out;
}
/*exibindo os botões*/
@media screen and (max-width: 767px) {
  .highlights-buttons {
    display: block;
  }
}
</pre>

Estamos falando de css puro e sempre precisamos definir o que vai ser feito, veja como aplicar o label ativo nessa estrutura que criamos:

<pre class="lang-css">.highlights input:nth-of-type(1):checked ~ .highlights-buttons label:nth-child(1),
.highlights input:nth-of-type(2):checked ~ .highlights-buttons label:nth-child(2),
.highlights input:nth-of-type(3):checked ~ .highlights-buttons label:nth-child(3) {
  background-color: #000;
}
</pre>

Para evitar a repetição manual a cada novo item, se você usa SASS ou LESS vai tirar de letra com alguma função.

## E PRONTO

Mais uma vez com poucos elementos e css, conseguimos deixar nossos destaques em uma galeria navegável e responsivo.

<a title="Veja como ficou o resultado final" href="http://palloi.github.io/responsive-header-only-css/responsive-highlights.html" target="_blank">Veja como ficou o resultado final</a>.

<a title="Código completo no github" href="https://github.com/palloi/responsive-header-only-css" target="_blank">Veja o código completo no github</a>.

## CONCLUINDO

Existe diversas maneiras de aplicar no css e quantidades de itens, espero que todos possam aproveitar um pouco do que foi apresentado.

É isso ae pessoal, obrigado