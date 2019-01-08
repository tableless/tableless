---
title: CSS3 — Trabalhando com Múltiplas imagens background-images
authors: Moisés Lopes Ferreira
type: post
date: 2016-09-07
excerpt: Quem nunca se deparou com o um layout com imagens “sobrepostas” que precisavam ficar suspensas sobre múltiplas imagens de fundo, com CSS3, você pode aplicar aos elementos múltiplas imagens como plano de fundo sobrepostas. Sem a utilização do Z-index, é isso mesmo “necas de pitibiriba” de Z-index. Que Z-index que nada, agora a MODA é Background-image !!!
categories:
  - Adaptive Web Design (AWD)
  - Artigos
  - Código
  - CSS
  - CSS3
  - Design
  - HTML
  - HTML5
  - Semântica
tags:
  - CSS3
  - background
  - CSS
  - html
  - z-index
---

  Quem nunca se deparou com um layout com múltiplas imagens “sobrepostas” ou mesmo com títulos ou parágrafos que precisavam ficar suspensos sobre múltiplas imagens de fundo? Essa semana me deparei com o mesmo problema.


  Com <a class="markup--anchor markup--p-anchor" title="CSS3" href="https://developer.mozilla.org/en/CSS/CSS3">CSS3</a>, você pode aplicar aos elementos múltiplas imagens sobrepostas como plano de fundo. Sem a utilização do Z-index! É isso mesmo, “necas de pitibiriba” de Z-index.

## Velho dilema de sobrepor imagens com div’s com Z-index…


  A primeira solução que vem à cabeça é o velho e bom “Z-index”, Veja um exemplo de implementação:

<pre class="lang-html">&lt;div&gt;
    &lt;span class="red"&gt;Red&lt;/span&gt;
&lt;/div&gt;
&lt;div&gt;
    &lt;span class="green"&gt;Green&lt;/span&gt;
&lt;/div&gt;
&lt;div&gt;
    &lt;span class="blue"&gt;Blue&lt;/span&gt;
&lt;/div&gt;</pre>



<pre class="lang-css">.red, .green, .blue {
    color: #fff;
    display: block;
    line-height: 100px;
    position: absolute;
    text-align: center;
    width: 100px;
}
.red {
    background: red;
    left: 20px;
    top: 20px;
    z-index: 0;
    opacity:0.5;
}
.green {
    background: green;
    left: 60px;
    top: 60px;
    z-index: 1;
    opacity:0.6;
}
.blue {
    background: blue;
    left: 100px;
    top: 100px;
    z-index: 2;
    opacity:0.7;
}
body {
    color: #777;
}</pre>

{{< codepen
  hash="grvvLw"
  user="selique"
  author="Moisés lopes ferreira"
>}}

### Funciona?!… <em class="markup--em markup--h4-em">SIM!</em> Mas espere um momento, essa não é a única solução…


  … Você já tava pensando num “workaround” safadinho, a mão da gambiarra chega a tremer nessas horas, mas nada de programação orientada a “Go-Horse”, hoje em dia temos “solucionática” pra quase tudo hehe…

<div style="width: 510px" class="wp-caption aligncenter">
  <img src="https://cdn-images-1.medium.com/max/800/1*pAiFtxYHdjg4-HP6e46wZA.gif" alt="www.gohorseprocess.com.br/extreme-go-horse-(xgh)" width="500" height="374" />

  <p class="wp-caption-text">
    www.gohorseprocess.com.br/extreme-go-horse-(xgh)
</div>

### Conhecendo as propriedades CSS do Background:

<pre>background-color.........define a cor do fundo;
background-image.........define uma imagem de fundo;
background-repeat........define a maneira como a imagem de fundo é posicionada;
background-attachment....define se a imagem de fundo "rola" ou não com a tela;
background-position......define como e onde a imagem de fundo é posicionada;
background-clip..........define a área do box onde a imagem de fundo é aplicada;
background-origin........define a posição de origem da imagem no box;
background-size..........define as dimensões da imagem no box;
background...............maneira abreviada para declarar todas as propriedades anteriores;</pre>


  O nosso grande mestre <a class="markup--user markup--p-user" href="https://medium.com/u/addb7196c9b9">Maurício Samy Silva</a> #Maujor explica melhor as aplicações das propriedades <a class="markup--anchor markup--p-anchor" href="https://maujor.com/tutorial/propriedade-css-para-estilizacao-de-background.php" rel="nofollow">https://maujor.com/tutorial/propriedade-css-para-estilizacao-de-background.php</a>


  Agora que conhecemos suas propriedades e características… agora vamos ver como o “background-image” funciona para entendermos nosso horizonte de possibilidades:

## Background-image VS Z-index — A BATALHA:


Quando trabalhamos 2 ou 3 elementos (sejam `<img>`, `<div>`, `<etc…>`) temos um controle até tolerável, mas… quando utilizamos 6, 10 ou mais elementos numa mesma div ou aninhamento próximo, o z-index começa a se tornar “linguiçento” demais e somos obrigados a utilizar mais classes e ids para organizarmos nosso CSS, pensando nisso que escrevi esse post!



  <em>Às vezes não necessariamente queremos ou podemos utilizar o z-index.</em>


  Sem contar que quebramos o conceito de <a class="markup--anchor markup--p-anchor" href="https://tableless.com.br/oocss-smacss-bem-dry-css-afinal-como-escrever-css/">DRY</a> em nosso documento CSS e não queremos isso, não é amiguinhos?

<div style="width: 495px" class="wp-caption aligncenter">
  <img src="https://cdn-images-1.medium.com/max/800/1*xt8qqJopHwF-Gcg9xM6t3w.gif" alt="Vida de um Front-end" width="485" height="364" />

  <p class="wp-caption-text">
    Front-end Lifestyle
</div>

### Z-index — Quando usar?


  Quando temos muitos elementos e precisamos especificar propriedades e características CSS que vão além do propósito de uma “imagem de fundo” ou “sobreposição” então o Z-index é a melhor opção!


  Mas se você quer simplesmente sobrepor uma imagem de um logo (ou uma composição de camadas que formam um logo) sobre um uma ou mais imagem de preenchimento de fundo o background-image é a melhor solução!


  Estes elementos ficam empilhados em camadas uma acima da outra, onde o primeiro fundo dado será desenhado no topo e apenas o último elemento da lista poderá definir uma cor sólida de fundo, ou não, aí fica ao seu critério.

<pre class="lang-css">.minhaClasse {
  background: fundo1, fundo2, ..., fundoN;
}</pre>


  <a class="markup--anchor markup--p-anchor" href="https://tableless.com.br/tag/css3/">CSS3</a> permite especificar imagens de fundo para múltiplos elementos, usando nada mais do que uma única lista separada por vírgulas.


  Você pode fazer isso com a propriedade reduzida <a class="markup--anchor markup--p-anchor" title="The documentation about this has not yet been written; please consider contributing!" href="https://developer.mozilla.org/pt-BR/docs/Web/CSS/background">background</a> e também com as propriedade individuais, com a exceção de <a class="markup--anchor markup--p-anchor" title="The documentation about this has not yet been written; please consider contributing!" href="https://developer.mozilla.org/pt-BR/docs/Web/CSS/background-color">background-color</a>. Isto é, as seguintes propriedades de plano de fundo podem ser especificadas com uma lista, uma por fundo: <a class="markup--anchor markup--p-anchor" title="The documentation about this has not yet been written; please consider contributing!" href="https://developer.mozilla.org/pt-BR/docs/Web/CSS/background">background</a>, <a class="markup--anchor markup--p-anchor" title="The documentation about this has not yet been written; please consider contributing!" href="https://developer.mozilla.org/pt-BR/docs/Web/CSS/background-attachment">background-attachment</a>, <a class="markup--anchor markup--p-anchor" title="A propriedade CSS background-clip especifica se o fundo de um elemento, seja cor ou imagem, se extende debaixo de sua borda." href="https://developer.mozilla.org/pt-BR/docs/Web/CSS/background-clip">background-clip</a>, <a class="markup--anchor markup--p-anchor" title="The documentation about this has not yet been written; please consider contributing!" href="https://developer.mozilla.org/pt-BR/docs/Web/CSS/background-image">background-image</a>, <a class="markup--anchor markup--p-anchor" title="The documentation about this has not yet been written; please consider contributing!" href="https://developer.mozilla.org/pt-BR/docs/Web/CSS/background-origin">background-origin</a>, <a class="markup--anchor markup--p-anchor" title="The documentation about this has not yet been written; please consider contributing!" href="https://developer.mozilla.org/pt-BR/docs/Web/CSS/background-position">background-position</a>, <a class="markup--anchor markup--p-anchor" title="The documentation about this has not yet been written; please consider contributing!" href="https://developer.mozilla.org/pt-BR/docs/Web/CSS/background-repeat">background-repeat</a>, <a class="markup--anchor markup--p-anchor" title="The documentation about this has not yet been written; please consider contributing!" href="https://developer.mozilla.org/pt-BR/docs/Web/CSS/background-size">background-size</a>. (rola até gradiente!)

## Exemplos


  Neste exemplo, três planos de fundos estão empilhados: um texto estilizado, o logo da Tableless.com.br, e uma imagem de fundo ilustrando uma cidade:



<pre class="lang-html">&lt;header&gt;
  &lt;div class="intro-text"&gt;
    &lt;h1 class="name-index"&gt;BEM-VINDO À&lt;/br&gt;&lt;span&gt;INTERNET&lt;/span&gt;&lt;/h1&gt;
  &lt;/div&gt;
&lt;/header&gt;</pre>



<pre class="lang-css">header {
  background: url(<a class="markup--anchor markup--pre-anchor" href="https://raw.githubusercontent.com/diegoeis/tableless-static-images/master/2013/04/logo-tableless-01.png" rel="nofollow">https://raw.githubusercontent.com/diegoeis/tableless-static-images/master/2013/04/logo-tableless-01.png</a>) no-repeat center center, url(<a class="markup--anchor markup--pre-anchor" href="https://lorempixel.com/output/city-q-g-1024-768-10.jpg" rel="nofollow">https://lorempixel.com/output/city-q-g-1024-768-10.jpg</a>) no-repeat center top;
  height: 100vh;
  width: auto;
  box-sizing: border-box;
}
header .intro-text {
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}
header .intro-text &gt; h1 {
  text-shadow: 8px 5px 5px #00181c;
  color: #fff;
  text-transform: uppercase;
  text-align: center;
}
header .intro-text .name-index {
  font-size: 7vw;
}
header .intro-text .name-index span {
  font-size: 9.2vw;
}</pre>

{{< codepen
  hash="vKddRK"
  user="selique"
  author="Moisés lopes ferreira"
  title="Multiple backgrounds backgroud-image"
>}}


  Suporte do navegador para múltiplas imagens com a propriedade CSS background-image é relativamente difundido na implementação do recurso citado acima:

<ul class="postList">
  <li class="graf--li">
    Mozilla Firefox (3.6 ou superior)
  </li>
  <li class="graf--li">
    Safari / Chrome (1.0 / 1.3 +)
  </li>
  <li class="graf--li">
    Opera (10.5+)
  </li>
  <li class="graf--li">
    até mesmo no Internet Explorer (9.0+)
  </li>
</ul>


##  Bibliografia (Fontes)

<div class="graf--mixtapeEmbed">
  <a class="markup--anchor markup--mixtapeEmbed-anchor" title="https://developer.mozilla.org/pt-BR/docs/Web/CSS/background-image" href="https://developer.mozilla.org/pt-BR/docs/Web/CSS/background-image"><strong class="markup--strong markup--mixtapeEmbed-strong">background-image</strong> &#8211; <em class="markup--em markup--mixtapeEmbed-em">The CSS background-image property sets one or several background images for an element. The images are drawn on…</em>developer.mozilla.org</a>
</div>

<div class="graf--mixtapeEmbed">
  <a class="markup--anchor markup--mixtapeEmbed-anchor" title="https://developer.mozilla.org/pt-BR/docs/Web/CSS/CSS_Background_and_Borders/Using_CSS_multiple_backgrounds" href="https://developer.mozilla.org/pt-BR/docs/Web/CSS/CSS_Background_and_Borders/Using_CSS_multiple_backgrounds"><strong class="markup--strong markup--mixtapeEmbed-strong">Multiple backgrounds</strong> &#8211; <em class="markup--em markup--mixtapeEmbed-em">Com CSS3 , você pode aplicar aos elementos multiplos planos de fundo. Estes ficam em camadas empilhadas uma acima da…</em>developer.mozilla.org</a>
</div>