---
title: 'Sections: elemento nav – Parte 2'
author: Diego Eis
type: post
date: 2010-09-30
excerpt: O elemento NAV agrupa blocos de links de um mesmo assunto ou links internos do website. Ele indica que um determinado bloco é um bloco de navegação.
url: /sections-elemento-nav/
aktt_notify_twitter:
  - yes
tweetbackscheck:
  - 1356406647
shorturls:
  - 'a:3:{s:9:"permalink";s:45:"http://tableless.com.br/sections-elemento-nav";s:7:"tinyurl";s:26:"http://tinyurl.com/3fb7dsx";s:4:"isgd";s:19:"http://is.gd/aRROWm";}'
twittercomments:
  - 'a:1:{i:12674706184347648;s:6:"136333";}'
tweetcount:
  - 1
dsq_thread_id: 503039546
categories:
  - Código
  - HTML5
  - Técnicas e Práticas
tags:
  - 2010
  - CSS
  - html5
  - Na Prática
  - Semântica
  - tableless

---
Se você não leu o [primeiro artigo da série][1], é interessante que o faça agora.

O elemento `nav` representa uma seção da página que contém link para outras páginas ou partes do mesmo website. Resumindo: `nav` é uma seção de links de navegação.

Essa definição é muito mais complexa do que se imagina. A tag `nav` pode agrupar uma série de elementos que anteriormente faríamos com `div`. Nem todos os grupos de links da página precisam ser um elemento `nav`, mas apenas as seções que consitem em blocos principais. Imagine uma sidebar (agora descrito com a tag `aside`) com uma série de links, como por exemplo uma sidebar de um portal como o G1, R7, UOL e etc&#8230; Nestas sidebars é normal você encontrar os diversos links das diversas categorias de assuntos. Anteriormente, se quiséssemos agrupar por exemplo um Título e uma lista de links faríamos assim:

<pre class="lang-html">&lt;div class="categ categ-esporte"&gt;
  &lt;h3&gt;Esporte&lt;/h3&gt;
  &lt;ul&gt;
    &lt;li&gt;&lt;a href="#"&gt;Copa 2014&lt;/a&gt;&lt;/li&gt;
    &lt;li&gt;&lt;a href="#"&gt;Brasileir&atilde;o&lt;/a&gt;&lt;/li&gt;
    &lt;li&gt;&lt;a href="#"&gt;F&oacute;rmula 1&lt;/a&gt;&lt;/li&gt;
    &lt;li&gt;&lt;a href="#"&gt;Baskete&lt;/a&gt;&lt;/li&gt;
  &lt;/ul&gt;
&lt;/div&gt;
</pre>

Resolvia nosso problema de formatação. Poderíamos utilizar `div` que envolve o título e a lista para fazer algum detalhe visual e etc. Mas a nível de informação, não havia nenhuma indicação de que o título estivesse ligado ao conteúdo. Não há nenhuma referência de que o título ESPORTE apresenta a lista de links sobre esporte abaixo. Os sistemas de busca não podem se basear apenas na posição dos elementos, é algo muito genérico para eles confirmarem que a lista e o título que a precede estão ligados em um mesmo assunto.
  
Com o HTML5, isso muda. Veja o código abaixo:

<pre class="lang-html">&lt;nav class="categ categ-esporte"&gt;
  &lt;h3&gt;Esporte&lt;/h3&gt;
  &lt;ul&gt;
    &lt;li&gt;&lt;a href="#"&gt;Copa 2014&lt;/a&gt;&lt;/li&gt;
    &lt;li&gt;&lt;a href="#"&gt;Brasileir&atilde;o&lt;/a&gt;&lt;/li&gt;
    &lt;li&gt;&lt;a href="#"&gt;F&oacute;rmula 1&lt;/a&gt;&lt;/li&gt;
    &lt;li&gt;&lt;a href="#"&gt;Baskete&lt;/a&gt;&lt;/li&gt;
  &lt;/ul&gt;
&lt;/nav&gt;
</pre>

Com a tag `nav`, há uma indicação de que aquele grupo é uma seção (`nav` é um tipo de `section`. Enquanto a tag `section` serve para indicar seções no site, a tag `nav` indica que um determinado grupo é uma seção de navegação) é um bloco de navegação.

Dentro da `nav` você pode agrupar uma série de listas de links. 

<pre class="lang-html">&lt;nav&gt;
  &lt;ul&gt;
    &lt;li&gt;&lt;a href="#"&gt;Copa 2014&lt;/a&gt;&lt;/li&gt;
    &lt;li&gt;&lt;a href="#"&gt;Brasileir&atilde;o&lt;/a&gt;&lt;/li&gt;
    &lt;li&gt;&lt;a href="#"&gt;F&oacute;rmula 1&lt;/a&gt;&lt;/li&gt;
    &lt;li&gt;&lt;a href="#"&gt;Baskete&lt;/a&gt;&lt;/li&gt;
  &lt;/ul&gt;

  &lt;ul&gt;
    &lt;li&gt;&lt;a href="#"&gt;Educa&ccedil;&atilde;o&lt;/a&gt;&lt;/li&gt;
    &lt;li&gt;&lt;a href="#"&gt;Dicion&aacute;rios&lt;/a&gt;&lt;/li&gt;
    &lt;li&gt;&lt;a href="#"&gt;Vestibular&lt;/a&gt;&lt;/li&gt;
  &lt;/ul&gt;

  &lt;ul&gt;
    &lt;li&gt;&lt;a href="#"&gt;Cotidiano&lt;/a&gt;&lt;/li&gt;
    &lt;li&gt;&lt;a href="#"&gt;Pol&iacute;tica&lt;/a&gt;&lt;/li&gt;
    &lt;li&gt;&lt;a href="#"&gt;Jornais&lt;/a&gt;&lt;/li&gt;
  &lt;/ul&gt;
&lt;/nav&gt;
</pre>

A tag `nav` também pode estar em todos os elementos do HTML. Você pode colocá-la no `header` para definir menus, no `footer` para definir grupos de links, sidebars, articles e etc.

 [1]: http://tableless.com.br/sections-html5