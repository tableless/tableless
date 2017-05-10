---
title: 'Web Components: Introdução'
author: Diego Eis
type: post
date: 2014-05-13
excerpt: Entenda os principais tópicos e as informações iniciais sobre Web Components.
url: /web-components-introducao/
dsq_thread_id: 2680881717
categories:
  - Artigos
  - HTML
  - JavaScript
  - Técnicas e Práticas
tags:
  - CSS
  - html5
  - web components

---
O que um plugin JavaScript/jQuery tem em comum com frameworks CSS como o Bootstrap? Resposta: Grandes pedaços de código HTML, CSS e Javascript.

Todas as vezes que você precisa implementar um slider ou elementos de um framework que você gosta, invariavelmente você precisa copiar um grande pedaço de código HTML, CSS e Javascript para depois aplicar em seu projeto. Todos estes códigos estão sempre separados e sofrem, principalmente, efeitos do código externo do seu projeto ou de outros plugins. Muitas vezes você deve ter tido algum problema de conflito entre códigos do plugin e do seu projeto. Isso gera retrabalho e outros problemas.

Mesmo se você cria seus próprios plugins ou frameworks de CSS, você ainda precisa tomar uma série de cuidados para que o código não sofra nenhum conflito e que seja o mais flexível e reutilizável possível. Mas acredite, mesmo que você faça um trabalho perfeito, alguma coisa sempre foge do controle.

Os Web Components podem ajudar nesses problemas e em muitos outros.

## O que são os Web Components

A ideia de criar componentes na web não é nova. A cada novo framework ou a cada novo plugin, tentamos fazer isso. O problema é que um componente só é um componente se ele pode ser reutilizado, diversas vezes, em qualquer lugar do projeto, sem sofrer alterações acidentais por códigos externos e também sem modificar outros elementos. É aí que entram os Web Components.

> The component model for the Web (also known as Web Components) consists of four pieces designed to be used together to let web application authors define widgets with a level of visual richness not possible with CSS alone, and ease of composition and reuse not possible with script libraries today.

Os Web Components são por enquanto um grupo de 5 especificações, que formam o guarda-chuva dos Web Components, são eles:

  1. **[Templates][1]**: definem pedaços de código que são totalmente inertes à página até que seu Javascript os ative.
  2. **[Decorators][2]**: aplicam os templates baseando-se em seletores para criar mudanças visuais ricas e comportamentos.
  3. **[Custom Elements][3]**: são elementos customizados, com nomes e scripts criados por você.
  4. **[Shadow DOM][4]**: é onde uma parte do código do seu elemento é encapsulada e escondida pelo browser, ou seja, não é visível no código normal do DOM, mas que monta todo seu componente &#8220;por baixo dos panos&#8221;.
  5. **[Imports][5]**: definem quais elementos customizados são empacotados e lidos como um recurso.

Cada uma dessas partes são individualmente úteis, mas se tornam realmente importantes quando combinadas. Assim você consegue fazer um componente totalmente funcional, com o visual e o código customizados.

Para facilitar o entendimento, aqui vai um exemplo bem tosco: pense que a independência dos web components funcionam como um iframe. O Facebook, Twitter e Google+ usam iframes para colocar seus botões nas páginas. Sendo um iframe eles podem usar o Javascript, o CSS e o HTML customizados sem que o código da sua página quebre os botões deles e vice-versa.

Você precisa entender dois conceitos essenciais e importantes dentro dos Web Components: Shadow DOM e Custom Elements.

## Custom Elements

E se você pudesse criar suas próprias tags?

O HTML tem muitos elementos que usamos todos os dias. O problema é que a Web cresceu demais e a verdade é que não temos mais elementos que cobrem todas as nossas necessidades. Por exemplo: como você faz uma modal? Como você faz tabs? Como você faz um collapse? Não existem elementos no HTML que criam estes módulos e suas interações. Por isso você usa listas, divs, parágrafos, títulos e o que der na telha para fazer estes elementos funcionarem.

Quem precisa lidar com interfaces pesadas de aplicações baseadas em web, como por exemplo um tocador de músicas online, tipo o Spotify, Rdio e Deezer, sente esse problema todos os dias. Na verdade, para criar qualquer aplicação baseada em web, você vai precisar de uma boa dose criatividade usando os elementos existentes do HTML para produzir o layout que foi planejado. Muitas vezes o código vira um punhado de DIVs e SPANs. Aí eu te pergunto: nesses casos a semântica é importante? Quando você ler logo abaixo sobre Shadow DOM, você vai entender que a semântica pode ser bem surrada em ambientes assim. Ela se torna tão subjetiva que pode fazer você pensar que ela realmente não existe.

Voltando ao assunto: como fazer seus próprios elementos?

Quando criarmos um elemento, precisamos que ele herde as mesmas possibilidades que os elementos normais do HTML. Isso quer dizer que você precisa poder formatar com CSS e também manipular com Javascript.

Quando criarmos o elemento, precisamos fazer com que o browser reconheça esse elemento. No Javascript, você usará o `documento.registerElement()` para fazer isso:

<pre class="lang-javascript">var yourElement = document.registerElement('nome-elemento');
</pre>

O argumento do **document.registerElement()** define o nome do seu elemento, da sua nova tag. O nome sempre tem que ter um traço (-). Se você quiser, o nome pode ter mais do que duas palavras também, tipo: <list-combo-select>. Agora, um nome assim: <list> ou <list_combo> não são válidos. Essa restrição permite que o parser do browser entenda o que é um elemento customizado dos elementos default do HTML, garantindo compatibilidades futuras.

Para que um elemento seja realmente um elemento, além de registrar o elemento no browser como fizemos acima, nós precisamos que ele herde as características de funcionamento que o Javascript tem sobre um elemento HTML convencional. Difícil de entender né? Mas pense assim: você quer que seu elemento possa ser manipulado como um div, p, img e etc. Para isso você vai criar via javascript um objeto, que herda as características do elemento HTML e o prototype Javascript:

<pre class="lang-javascript">var yourElement = document.registerElement('seu-elemento', {
  prototype: Object.create(HTMLButtonElement.prototype),
  extends: 'button' // Define que o elemento button pode herdar as características do seu elemento.
});
</pre>

Isso faz com que você possa adicionar eventos de click, hover e etc no seu elemento customizado.

Não quero me estender agora, mas haverá outro artigo explicando como criar os elementos, inclusive usando as bibliotecas X-Tag ou o Polymer para ajudar.

## Shadow DOM

O Shadow DOM é uma parte interessante e importante do processo.

Quando você liga um carro, você não pensa no processo que faz tudo aquilo funcionar. Na verdade só nos preocupamos no que acontece debaixo do capô se halgo dá errado quando giramos a chave. A mesma coisa acontece com as tags do HTML. Pare um momento e pense: do que é feito o input de texto?

<input type="text" />

Quais os elementos que o browser usa para montá-lo na tela?

E se eu dissesse que ele é basicamente um elemento DIV?

<pre class="lang-html">&lt;input type="text"&gt;
  &lt;div id="inner-editor"&gt;&lt;/div&gt;
&lt;/input&gt;
</pre>

Isso se chama **Shadow DOM**. Para você entender melhor, veja como é feito a tag de Vídeo:

Essa é a versão original, que você já deve conhecer:

<pre class="lang-html">&lt;video controls poster="poster.png"&gt;
	&lt;source src="video.webm" type='video/webm;codecs="vp8, vorbis"' /&gt;
	&lt;source src="video.mp4" type='video/mp4;codecs="avc1.42E01E, mp4a.40.2"' /&gt;
	&lt;track src="video.vtt" label="Portuguese subtitles" kind="subtitles" srclang="pt-br" default&gt;&lt;/track&gt;
&lt;/video&gt;
</pre>

Essa é a versão escondida:

<pre class="lang-html">&lt;video controls poster="poster.png"&gt;
	&lt;div&gt;
		&lt;div style="display: none"&gt;&lt;/div&gt;
		&lt;div&gt;
			&lt;div&gt;
				&lt;input type="button"&gt;
				&lt;input type="range" step="any" max="70.112"&gt;
				&lt;div style="display: none;"&gt;0:00&lt;/div&gt;
				&lt;div&gt;1:10&lt;/div&gt;
				&lt;input type="button"&gt;
				&lt;input type="range" step="any" max="1"&gt;
				&lt;input type="button"&gt;
				&lt;input type="button"&gt;
			&lt;/div&gt;
		&lt;/div&gt;
	&lt;/div&gt;

  &lt;source src="video.webm" type='video/webm;codecs="vp8, vorbis"' /&gt;
  &lt;source src="video.mp4" type='video/mp4;codecs="avc1.42E01E, mp4a.40.2"' /&gt;
  &lt;track src="video.vtt" label="Portuguese subtitles" kind="subtitles" srclang="pt-br" default&gt;&lt;/track&gt;
&lt;/video&gt;
</pre>

Pois é. Não confie em ninguém!

É assim, com esse código nada elegante, que o browser monta os elementos. Esse código parece ser ruim e você pode levar um susto quando começar a fuçar códigos de outros elementos, mas não é errado e pode mudar de browser para browser. Lembre-se que ali é um DOM escondido, o que importa não é a beleza do código, mas a funcionalidade.

E não, você não precisa escrever um código assim pra criar seus próprios componentes.

Pense em como fazer um slider de imagem. Um código de slider geralmente é algo assim:

<pre class="lang-html">&lt;div id="carousel-example-generic" class="carousel slide" data-ride="carousel"&gt;
  &lt;!-- Indicators --&gt;
  &lt;ol class="carousel-indicators"&gt;
    &lt;li data-target="#carousel-example-generic" data-slide-to="0" class="active"&gt;&lt;/li&gt;
    &lt;li data-target="#carousel-example-generic" data-slide-to="1"&gt;&lt;/li&gt;
    &lt;li data-target="#carousel-example-generic" data-slide-to="2"&gt;&lt;/li&gt;
  &lt;/ol&gt;

  &lt;!-- Wrapper for slides --&gt;
  &lt;div class="carousel-inner"&gt;
    &lt;div class="item active"&gt;
      &lt;img src="..." alt="..."&gt;
      &lt;div class="carousel-caption"&gt;
        ...
      &lt;/div&gt;
    &lt;/div&gt;
    ...
  &lt;/div&gt;

  &lt;!-- Controls --&gt;
  &lt;a class="left carousel-control" href="#carousel-example-generic" data-slide="prev"&gt;
    &lt;span class="glyphicon glyphicon-chevron-left"&gt;&lt;/span&gt;
  &lt;/a&gt;
  &lt;a class="right carousel-control" href="#carousel-example-generic" data-slide="next"&gt;
    &lt;span class="glyphicon glyphicon-chevron-right"&gt;&lt;/span&gt;
  &lt;/a&gt;
&lt;/div&gt;
</pre>

Imagine fazer algo assim:

<pre class="lang-html">&lt;img-slider&gt;
  &lt;img src="./image1.jpg" alt="a dramatic sunset"&gt;
  &lt;img src="./image2.jpg" alt="a rock arch"&gt;
  &lt;img src="./image3.jpg" alt="some neat grooves"&gt;
  &lt;img src="./image4.jpg" alt="an interesting rock"&gt;
&lt;/img-slider&gt;
</pre>

Entende? Toda a parafernália que fica atrapalhando e que provavelmente você nem vai mexer, fica escondida. As imagens, que são o que realmente importa, estão logo ali.

### Como mostrar o Shadow DOM?

Se você não encontrar no seu Chrome, tente baixar o [Chrome Canary][6].

Abra o Developer Tools, clique no ícone da engrenagem para abrir a tela de configurações. Procure a opção, habilite e pronto, você já tem super poderes.

<img src="http://tableless.com.br/uploads/2014/05/shadow-dom-chrome-config.png" alt="shadow-dom-chrome-config" class="alignnone size-full wp-image-42548" srcset="uploads/2014/05/shadow-dom-chrome-config.png 2372w, uploads/2014/05/shadow-dom-chrome-config-400x165.png 400w" sizes="(max-width: 2372px) 100vw, 2372px" />

## Suporte

E o suporte dos browsers? Cara, até que é ótimo. [Veja essa tabela][7]. Tirando o Safari e o IE que ainda não tem suporte algum, os outros browsers tem problemas apenas com o HTML Imports. Owl, Yeah!

[Polymer][8] é uma biblioteca construída em cima de Web Components e projetada para fazer com que os navegadores modernos entendam os Web Components.

[X-Tag][9] é uma biblioteca Javascript pequenininha, criada e mantida pela Mozilla, que traz as capacidades do Custom elements do Web Components para todos os browsers modernos.

## Slides e leituras obrigatórias

Este artigo foi uma introdução para você começar a se interessar e a pesquisar sobre Web Components. Existem milhares de sites por aí que eu aconselho você ler. Os links estão logo abaixo:

  * [webcomponents.org][10]
  * [A Detailed Introduction To Custom Elements][11]
  * [About Custom Elements][12]
  * [A Guide to Web Components][13]
  * [Why Web Components?][14]
  * [Documentação do W3C][15]

 [1]: http://www.w3.org/TR/components-intro/#template-section
 [2]: http://www.w3.org/TR/components-intro/#decorator-section
 [3]: http://www.w3.org/TR/custom-elements/
 [4]: http://www.w3.org/TR/shadow-dom/
 [5]: http://www.w3.org/TR/2013/WD-html-imports-20130514/
 [6]: http://www.google.com/intl/pt-BR/chrome/browser/canary.html
 [7]: http://jonrimmer.github.io/are-we-componentized-yet/
 [8]: http://www.polymer-project.org/
 [9]: http://x-tags.org/
 [10]: http://webcomponents.org/
 [11]: http://www.smashingmagazine.com/2014/03/04/introduction-to-custom-elements/
 [12]: http://www.html5rocks.com/en/tutorials/webcomponents/customelements/?redirect_from_locale=pt
 [13]: http://css-tricks.com/modular-future-web-components/
 [14]: http://robdodson.me/blog/2013/03/17/why-web-components/
 [15]: http://www.w3.org/TR/components-intro/#introduction