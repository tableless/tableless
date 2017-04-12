---
title: Carrossel descomplicado com HTML, CSS
author: Leonardo Camp
type: post
date: 2016-09-04
url: /carrocel-descomplicado-com-html-css/
categories:
  - CSS
  - HTML
  - JavaScript

---
Não é difícil perceber que muitos desenvolvedores tanto iniciantes como os veteranos de guerra ainda sofrem quando o assunto é carrossel, mesmo utilizando frameworks como BootStrap. Mas seus problemas acabaram! (música de chegada milagrosa), com o conhecimento de poucas técnicas podemos resolver esse &#8220;gigante&#8221; problema facilmente.

### Pseudo classe :target &#8211; CSS

Para resolver o grande problema de transição do carrossel, vamos utilizar a pseudo classe `:target`, que atribui algumas características do CSS para o elemento HTML.

Para quem ainda não conhece a pseudo classe &#8220;:target&#8221; aqui vai um exemplo bem alto explicativo.

###### HTML

<pre class="lang-html">&lt;a href="#texto-exemplo-1"&gt;Seleciona o texto exemplo 1&lt;/a&gt;
&lt;a href="#texto-exemplo-2"&gt;Seleciona o texto exemplo 2&lt;/a&gt;

&lt;p id="texto-exemplo-1" class="text" &gt;Texto exemplo 1&lt;/p&gt;
&lt;p id="texto-exemplo-2" class="text" &gt;Texto exemplo 2&lt;/p&gt;
</pre>

###### CSS

<pre class="lang-css">.text:target{
    border: 1px solid #000;
}
</pre>

Você pode conferir o resultado no CODEPEN <a href="http://codepen.io/lleonardoll/pen/BzBdWB?editors=1100" target="_blank">aqui.</a>

O Tableless tem [um artigo que ensina a fazer abas usando apenas CSS3 com o pseudo classe :target][1].

### Estrutura HTML

A estrutura que iremos utilizar também é bem simples. Primeiramente uma DIV como &#8220;container&#8221; que é onde irá acontecer o carrossel, também utilizaremos outras DIVs que chamaremos de &#8220;wall-x&#8221; onde x é o valor da DIV no carrossel.

## Mão na massa

Vamos começar pelo HTML definindo a estrutura do nosso carrossel.

<pre class="lang-html">&lt;div class="container"&gt;
    &lt;div class="wall wall-1" id="wall-1"&gt;
        &lt;h1&gt;carrosel numero - 1&lt;/h1&gt;
    &lt;/div&gt;

    &lt;div class="wall wall-2" id="wall-2"&gt;
        &lt;h1&gt;carrosel numero - 2&lt;/h1&gt;
    &lt;/div&gt;

    &lt;div class="wall wall-3" id="wall-3"&gt;
        &lt;h1&gt;carrosel numero - 3&lt;/h1&gt;
    &lt;/div&gt;
&lt;/div&gt;
</pre>

Terminado a estrutura, devemos deixar todas as DIVs wall com &#8220;display: none;&#8221; ( sim, todas! ) para não serem listadas de uma vez.

<pre class="lang-css">.container{
    width: 150px;
    height: 150px;
}

.wall{
    display: none;
    width: 100%;
    height: 100%;
}

/* Corzinha de fundo para diferenciar */
.wall-1{ background-color: #f00; }
.wall-2{ background-color: #0f0; }
.wall-3{ background-color: #00f; }

.wall:target{
    display: block;
}
</pre>

###### Explicando&#8230;

Basicamente, definimos o tamanho do &#8220;container&#8221;. Deixamos todas as DIVs &#8220;wall&#8221; com &#8220;display: none;&#8221; e definimos que todo &#8220;target&#8221; terá o &#8220;display: block;&#8221;. Se nada estiver aparecendo na sua tela, não se assuste, tudo está funcionando, o que acontece é que você não tem nem um &#8220;target&#8221; definido, mas você pode fazer um teste adicionando &#8220;#wall-1&#8221; na sua url.

Ok, já temos 90% do carrossel pronto. Para finalizarmos o carrossel precisamos adicionar as setas (ou botões como preferir) para fazer a transição de uma tela para outra, e é ai que vem a outra parte fácil. A unica coisa que precisamos fazer é adicionar links que setam para o target anterior ou seguinte, neste caso, se você estiver no &#8220;#wall-2&#8221; o anterior seria &#8220;#wall-1&#8221; e o seguinte &#8220;#wall-3&#8221; (precisava explicar?).

<pre class="lang-html">&lt;div class="container"&gt;
    &lt;div class="wall wall-1" id="wall-1"&gt;
        &lt;a href="#wall-3"&gt;Voltar&lt;/a&gt;
        &lt;h1&gt;carrosel numero - 1&lt;/h1&gt;
        &lt;a href="#wall-2"&gt;Avançar&lt;/a&gt;
    &lt;/div&gt;

    &lt;div class="wall wall-2" id="wall-2"&gt;
        &lt;a href="#wall-1"&gt;Voltar&lt;/a&gt;
        &lt;h1&gt;carrosel numero - 2&lt;/h1&gt;
        &lt;a href="#wall-3"&gt;Avançar&lt;/a&gt;
    &lt;/div&gt;

    &lt;div class="wall wall-3" id="wall-3"&gt;
        &lt;a href="#wall-2"&gt;Voltar&lt;/a&gt;
        &lt;h1&gt;carrosel numero - 3&lt;/h1&gt;
        &lt;a href="#wall-1"&gt;Avançar&lt;/a&gt;
    &lt;/div&gt;
&lt;/div&gt;
</pre>

Para facilitar a exibição do primeiro target (sem ter que criar um link personalizado) você pode simplesmente colocar uma linha de javascript para todo o carrossel ficar ativa 😉

<pre>window.location = "#wall-1";
</pre>

Você pode ver o código em ação no CODEPEN <a href="http://codepen.io/lleonardoll/pen/pbvdRZ" target="_blank">aqui.</a>

Pronto! Uma maneira muito simples para resolver um grande problema.

## Possível problema que você poderá encontrar

Caso você esteja utilizando algum link com target &#8220;#&#8221; para executar alguma ação, o &#8220;#wall-x&#8221; que está sendo setado perderá o foco, e logicamente terá a atribuição &#8220;display: none;&#8221; retomada. Neste caso é recomendável que não utilize targets na mesma pagina do carrossel e substitua os links &#8220;#&#8221; por funções onclick via JavaScript ou JQuery.

 [1]: http://tableless.com.br/css3-abas-com-a-pseudo-classe-target/