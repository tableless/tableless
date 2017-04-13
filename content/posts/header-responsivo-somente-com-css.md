---
title: Header responsivo somente com css
author: Palloi Hofmann
type: post
date: 2014-12-08
excerpt: A cada novo projeto queremos alcançar o máximo de usuários, não importa se o dispositivo seja grande ou pequeno, tem que funcionar.
url: /header-responsivo-somente-com-css/
categories:
  - CSS
  - CSS3
  - HTML
  - Responsive Web Design (RWD)
  - Técnicas e Práticas
tags:
  - CSS
  - CSS3
  - html
  - responsive

---
[<img src="http://tableless.com.br/uploads/2014/12/header-responsive-only-css.png" alt="header-responsive-only-css" class="alignnone size-full wp-image-46175" srcset="uploads/2014/12/header-responsive-only-css.png 750w, uploads/2014/12/header-responsive-only-css-265x106.png 265w, uploads/2014/12/header-responsive-only-css-400x160.png 400w" sizes="(max-width: 750px) 100vw, 750px" />][1]

A cada novo projeto queremos alcançar o máximo de usuários, não importa se o dispositivo seja grande ou pequeno, tem que funcionar.

Com uma abordagem simples e rápida, esse tutorial vai te fazer pensar antes de querer usar o bootstrap só para ter o menu responsivo, claro que ele tem suas vantagens mas procuro sempre desenvolver do zero.

Estarei criando uma serie de tutoriais abordando o assunto e espero que gostem do meu primeiro artigo.

## Valendo!!!

Hoje em dia quando o cliente diz que o site é responsivo, quem aqui pensa no bootstrap?

> _&#8220;Fazer menu responsivo é só com bootstrap&#8221; ou &#8220;vamos precisar de javascript.&#8221;_

Nada contra o bootstrap, mas prefiro o <a title="Locawebstyle" href="http://locaweb.github.io/locawebstyle/" target="_blank">Locawebstyle</a> que está lindo e o javascript é maravilhoso.

## O HTML

Vamos criar primeiro nosso html com header simples:

<pre class="lang-html">&lt;header&gt;
  &lt;h1 class="fL"&gt;
    &lt;a href="#" title="A TURMA DO CHAVES"&gt;A TURMA DO CHAVES&lt;/a&gt;
  &lt;/h1&gt;

  &lt;nav class="fR"&gt;
    &lt;ul class="l2"&gt;
      &lt;li&gt;
        &lt;a href="#Chaves" title="Chaves"&gt;Chaves&lt;/a&gt;
      &lt;/li&gt;
      &lt;li&gt;
        &lt;a href="#Chiquinha" title="Chiquinha"&gt;Chiquinha&lt;/a&gt;
      &lt;/li&gt;
      &lt;li&gt;
        &lt;a href="#Seu-Madruga" title="Seu Madruga"&gt;Seu Madruga&lt;/a&gt;
      &lt;/li&gt;
      &lt;li&gt;
        &lt;a href="#Quico" title="Quico"&gt;Quico&lt;/a&gt;
      &lt;/li&gt;
    &lt;/ul&gt;
  &lt;/nav&gt;
&lt;/header&gt;
</pre>

​Agora com o nosso html pronto, vamos fazer o primeiro teste olhando nosso html puro e formatar usando poucas linhas de css.
  
<a title="Ver demo sem style." href="http://palloi.github.io/responsive-header-only-css/demo-only-elements.html" target="_blank">Ver demo sem style.</a>

## O CSS

Como nosso header ficará sempre fixo no topo, vamos formatar da seguinte maneira:

<pre class="lang-css">header {
  min-height: 60px;
  position: fixed;
  top: 0;
  right: 0;
  left: 0;
  border-bottom: 1px solid #ccc;
  background: #ECECEC;
  z-index: 2;
}
</pre>

Agora com o header formatado, o segundo teste é redimensionar o navegador para perceber que o header sempre acompanha e ao diminuir muito tem quebra por falta de espaço.
  
<a title="Ver demo com style." href="http://palloi.github.io/responsive-header-only-css/demo-basic-header.html" target="_blank">Ver demo com style.</a>

Montamos um header simples e funcional, com mais 3 elementos e CSS teremos um header simples e responsivo.

Esses elementos são dois label&#8217;s e um checkbox, com o selector &#8216;~&#8217; do css3 vamos transformar o header.

## Começando o responsivo

Vamos adicionar os elementos antes da nav e o html fica assim:

<pre class="lang-html">&lt;header&gt;
  &lt;h1 class="fL"&gt;
    &lt;a href="#" title="A TURMA DO CHAVES"&gt;A TURMA DO CHAVES&lt;/a&gt;
  &lt;/h1&gt;
  
  &lt;input type="checkbox" id="control-nav" /&gt;
  &lt;label for="control-nav" class="control-nav"&gt;&lt;/label&gt;
  &lt;label for="control-nav" class="control-nav-close"&gt;&lt;/label&gt;

  &lt;nav class="fR"&gt;
    &lt;ul class="l2"&gt;
      ...
    &lt;/ul&gt;
  &lt;/nav&gt;
&lt;/header&gt;
</pre>

Nesse ponto o checkbox tem o papel de substituir o javascript.

Conseguimos também por css saber se o elemento está marcado com o famoso &#8220;:checked&#8221; que todos já usaram com jQuery.

## Seu projeto, suas medidas

Para nosso exemplo adicionei no head:

<pre class="lang-html">&lt;meta name="viewport" content="width=device-width, height=device-height, initial-scale=1, maximum-scale=1, user-scalable=no" /&gt;
</pre>

e no css:

<pre class="lang-css">@media screen and (max-width: 767px)
</pre>

Quando redimensionar o navegador menor que 768px, a formatação do header vai se comportar de outra maneira e já escondida utilizando transform:

<pre class="lang-css">@media screen and (max-width: 767px) {
  header .control-nav {
    position: absolute;
    right: 20px;
    top: 20px;
    display: block;
    width: 30px;
    padding: 5px 0;
    border: solid #333;
    border-width: 3px 0;
    z-index: 2;
    cursor: pointer;
  }

  header .control-nav:before {
    content: "";
    display: block;
    height: 3px;
    background: #333;
  }

  header .control-nav-close {
    position: fixed;
    right: 0;
    top: 0;
    bottom: 0;
    left: 0;
    display: block;
    z-index: 1;
    background: rgba(0,0,0,0.4);
    -webkit-transition: all 500ms ease;
    transition: all 500ms ease;
    -webkit-transform: translate(100%, 0);
    -ms-transform: translate(100%, 0);
    transform: translate(100%, 0);
  }

  header nav {
    position: fixed;
    top: 0;
    right: 0;
    bottom: 0;
    width: 250px;
    border-left: 1px solid #ccc;
    background: #fff;
    overflow-x: auto;
    z-index: 2;
    -webkit-transition: all 500ms ease;
    transition: all 500ms ease;
    -webkit-transform: translate(100%, 0);
    -ms-transform: translate(100%, 0);
    transform: translate(100%, 0);
  }
}
</pre>

Formatei o &#8220;label .control-nav&#8221; para ser o botão responsivo, o &#8220;label .control-nav-close&#8221; para ser a cortina bloqueando o fundo e o &#8216;nav&#8217; para ficar fixo e redimensionável.

## Agora o pulo do gato

Utilizando dos seletores do CSS3 que são os &#8216;:checked&#8217; e &#8216;~&#8217;, conseguimos formatar elementos de acordo com a necessidade, <a title="Veja a documentação" href="http://www.w3.org/TR/css3-selectors/#selectors" target="_blank">veja a documentação</a>.

Sendo mais claro, com o seletor &#8216;~&#8217; você consegue selecionar elemento do mesmo pai declarado depois dele.

Ao marcar o input, no css usando o transform vamos exibir suavemente o menu, veja:

<pre class="lang-css">#control-nav:checked ~ .control-nav-close {
  -webkit-transform: translate(0, 0);
  -ms-transform: translate(0, 0);
  transform: translate(0, 0);
}

#control-nav:checked ~ nav {
  -webkit-transform: translate(0, 0);
  -ms-transform: translate(0, 0);
  transform: translate(0, 0);
}
</pre>

## Pronto

Agora o menu é responsivo e bem simples com poucos elementos.

<a title="Veja como ficou o resultado final" href="http://palloi.github.io/responsive-header-only-css/" target="_blank">Veja como ficou o resultado final</a>.

<a title="código completo no github" href="https://github.com/palloi/responsive-header-only-css" target="_blank">Veja o código completo no github</a>.

É isso ae pessoal, obrigado

 [1]: http://tableless.com.br/uploads/2014/12/header-responsive-only-css.png