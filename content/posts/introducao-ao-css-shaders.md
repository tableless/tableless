---
title: Introdução ao CSS Shaders – Parte 1
author: Giovanni Keppelen
type: post
date: 2011-10-03
excerpt: 'Shaders CSS é um complemento para Filter Effects. Além disso, shaders CSS introduz uma noção de Vertex Shader para um modelo de filtro. '
url: /introducao-ao-css-shaders/
tweetbackscheck:
  - 1356408574
shorturls:
  - 'a:3:{s:9:"permalink";s:31:"http://tableless.com.br/?p=4297";s:7:"tinyurl";s:26:"http://tinyurl.com/687bdec";s:4:"isgd";s:19:"http://is.gd/RjQdnN";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 503016117
categories:
  - Código
  - CSS3
  - HTML

---
O recurso de shaders CSS é proposto à consideração da <a title="FX Task Force" href="http://www.w3.org/Graphics/fx/" target="_blank">FX Task Force</a> que pode ser integrado na especificação de <a title="Filter Effects" href="https://dvcs.w3.org/hg/FXTF/raw-file/tip/filters/publish/Filters.html" target="_blank">Filter Effects</a>.

### Introdução

Um Shader é essencialmente um pequeno programa que proporciona um efeito particular e cujo comportamento é controlado com parâmetros de entradas.

Arquiteturas de gráficos, tais como <a title="Microsof 3D" href="http://msdn.microsoft.com/en-us/library/bb219679(v=vs.85).aspx" target="_blank">Microsoft Direct3D</a> ou <a title="Open GL" href="http://en.wikipedia.org/wiki/OpenGL" target="_blank">OpenGL </a>tem uma noção de <a title="Vertex Shaders" href="http://en.wikipedia.org/wiki/Vertex_shader" target="_blank">vertex shaders</a> que são operadas em coordenadas de ponto(vértices). Vertex shaders opera em uma malha de vértices e fornece uma ampla variedade de efeitos e distorção (Onda, oscilação). Shaders permitem varios efeitos per-pixel, como por exemplos, um efeito de florescer e vários outros efeitos de imagem (borrão, brilhos, detecção de bordas).

Quando aplicado para um conteúdo do documento, como o HTML ou elementos SVG, shaders podem ser usados de formas interessantes. Esses elementos 2D podem ser desenhados conceitualmente sobre uma malha de vértices que podem ser processados através de um <a title="vertex shader" href="http://en.wikipedia.org/wiki/Vertex_shader" target="_blank">Vertex Shader</a> para a distorção e depois para um <a title="Introdução ao Shader CSS" href="http://tableless.com.br/introducao-ao-css-shaders/" target="_blank">shader</a> de fragmento para o processamento de pixel.

Shaders são particulamente interessantes no contexto de transições animadas e um complemento para o <a title="Filter Effects 1.0" href="https://dvcs.w3.org/hg/FXTF/raw-file/tip/filters/publish/Filters.html" target="_blank">Filter Effects 1.0</a>, <a title="CSS Animation" href="http://tableless.com.br/introducao-ao-css-animation/" target="_blank">CSS Animations</a>, CSS Transitions entre outras.

Este documento propõe:

  * Modelo e uma sintaxe CSS para fazer a vertex shaders ao conteúdo de marcação arbitrária.
  * Sintaxe CSS para fazer fragmentos de shaders para operar com outros filtros de efeitos primitivos.
  * Uma sintaxe CSS para passar parâmetros para fragmentar e vertex shaders.
  * Uma sintaxe CSS para controlar a granularidade da malha processada pelo CSS.
  * Uma sintaxe CSS para definir um efeito de filtro (aplicável a shaders CSS, mas geralmente útil para efeitos de filtro).

### Exemplos de CSS Shaders

<div id="attachment_4303" style="width: 310px" class="wp-caption aligncenter">
  <a href="http://tableless.com.br/uploads/2011/10/intro-filtered-element.png"><img class="size-medium wp-image-4303" src="http://tableless.com.br/uploads/2011/10/intro-filtered-element-300x194.png" alt="" width="300" height="194" srcset="uploads/2011/10/intro-filtered-element-300x194.png 300w, uploads/2011/10/intro-filtered-element.png 544w" sizes="(max-width: 300px) 100vw, 300px" /></a>
  
  <p class="wp-caption-text">
    Elemento antes de aplicar o Shaders
  </p>
</div>

<div id="attachment_4304" style="width: 310px" class="wp-caption aligncenter">
  <a href="http://tableless.com.br/uploads/2011/10/intro-example-1.png"><img class="size-medium wp-image-4304" src="http://tableless.com.br/uploads/2011/10/intro-example-1-300x202.png" alt="" width="300" height="202" srcset="uploads/2011/10/intro-example-1-300x202.png 300w, uploads/2011/10/intro-example-1.png 550w" sizes="(max-width: 300px) 100vw, 300px" /></a>
  
  <p class="wp-caption-text">
    Elemento com um vértice shader aplicado
  </p>
</div>

[cce lang=&#8221;css&#8221;]
  
.waving {
  
filter: custom(url(&#8216;wave.vs&#8217;), 20 20, phase 0, amplitude 50);
  
transition-property: filter;
  
transition-duration: 0.2s;
  
}

.waving:hover {
  
filter: custom(url(&#8216;wave.vs&#8217;), 20 20, phase 90, amplitude 20);
  
}
  
[/cce]

[cce lang=&#8221;html&#8221;]

<div class="waving">
  <h2>
    Hello CSS Shaders
  </h2>
</div>

[/cce]

_url(&#8216;wave.vs&#8217;)_ faz referencia ao vértice shader customizada que calcula o efeito de ondulação. O parametro _20 20_ controla a _<a title="Vertex Mesch" href="https://dvcs.w3.org/hg/FXTF/raw-file/tip/custom/index.html#vertex-mesh" target="_blank">Vertex mesh</a>_, de modo que a onda é suave. Finalmente a _amplitude_ paraametros de controle a forma  e a força da curva utilizada para o efeito de ondulação.

### Combinado vértice e fragmento

&nbsp;

[cce lang=&#8221;css&#8221;]
  
.old-book-page {
  
filter: grayscale(1.0) custom(url(&#8216;book.vs&#8217;) url(&#8216;old-page-paper.fs&#8217;));
  
}
  
[/cce]

[cce lang=&#8221;html&#8221;]

<div class="old-book-page">
  <h2>
    Hello CSS Shaders
  </h2>
</div>

[/cce]

A figura mostra uma combinação de um vertex shader (para dar forma um &#8220;livro aberto&#8221; ) e um shader de fragmento (para dar a imagem um estilo de &#8216;papel velho&#8217;, com uma sombra sutil no meio).

Note como a propriedade &#8216;filter&#8217; é estendida com um costume () função e como essa função pode ser combinada com uma das funções existentes filtrantes (tais como tons de cinza () no exemplo acima)

Cada shader define seu próprio conjunto de parâmetros. Normalmente, os shaders terão diferentes parâmetros com tipos diferentes. Por exemplo, &#8220;box-blur&#8221; e &#8220;box-size&#8221;.

**Na parte 2, mostrarei mais exemplos práticos sobre como usar melhor os Shaders, nesse artigo, quiz mesmo fazer uma introdução sobre o elemento.**