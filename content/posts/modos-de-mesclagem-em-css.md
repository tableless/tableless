---
title: Modos de Mesclagem em CSS – Blend Mode CSS
author: Dani Guerrato
type: post
date: 2013-07-16
excerpt: Neste artigo entenda como funcionam os modos de mesclagem e saiba como utilizar cada um deles através de simples parâmetros de CSS.
url: /modos-de-mesclagem-em-css/
dsq_thread_id: 1503259694
categories:
  - Artigos
  - CSS
  - CSS3
tags:
  - 2013
  - blending modes
  - CSS
  - modos de mesclagem
  - photoshop
  - tecnicascss

---
Uma das funções mais interessantes do Photoshop é a capacidade de alterar imagens em camadas através de diversos modos de mesclagens (blending modes). Utilizando este recurso é possível criar composições de cores sobrepondo imagens em camadas diferentes.

Infelizmente, ao converter o layout para HTML e CSS, não possuíamos classes ou ferramentas para chegar no mesmo resultado de softwares de edição de imagens. A única saída era achatar as camadas e exportar a imagem no modo padrão. Mas este problema pode acabar! A própria empresa responsável pelo desenvolvimento do Photoshop, a Adobe, propôs uma série de parâmetros para utilizar modos de mesclagem diretamente através de CSS.

**Importante:** ainda não existe suporte para esta aplicação em nenhum browser. Nenhum mesmo! Isso não significa que não podemos testar! A Adobe fez um fork do Chromium e disponibilizou para [download no GitHub][1] para podermos ver o código funcionando e já existe um [rascunho na W3C][2] mostrando também exemplos de uso. Mesmo assim é legal conhecer (e aprender a utilizar!) desde agora pois é muito provável que estas especificações façam em breve parte dos novos parâmetros de CSS e sejam aceitas pelas próximas versões dos principais navegadores.

## O que são os Modos de Mesclagem

Blending, ou em português mesclagem, é a capacidade de calcular a mistura de cores em duas (ou mais) imagens sobrepostas. Isto ocorre através de dados matemáticos que podem subtrair, adicionar, multiplicar ou dividir o valor das cores ou de seus aspectos como matiz, saturação e luminosidade.

Quem trabalha com manipulação de imagens já está acostumado com este conceito. Basicamente os softwares editores, como o Photoshop, utilizam imagens em camadas sobrepostas. Estas imagens podem ser misturadas, clareadas, escurecidas, etc para formar uma nova imagem. Os modos de mesclagem controlam como os pixels desta imagem resultante vão ser coloridos.

### Como fazíamos até então&#8230;

Designers gostam de modos de mesclagem. E não é a toa. Eles são muito úteis para dar efeitos de iluminação ou fazer sombras bacanas nas imagens, mas é impossível reproduzi-los usando apenas CSS. É até difícil, para quem é desenvolvedor, explicar para um designer empolgadinho que ele não pode utilizar aquele efeito bacana na internet. O único jeito, até então, para desenvolver o código de maneira fiel ao protótipo criado era achatar as camadas e exportar a imagem. Esta prática, quando utilizada com abuso, pode prejudicar o desenvolvimento em alguns pontos. A utilização excessiva de imagens pode deixar o layout mais pesado, não é possível dar qualquer tratamento para texto sem perder a marcação HTML (ninguém em 2013 leitor do Tableless ainda acha que deve utilizar imagens no lugar de texto&#8230; certo?!), tirando o fato de que alguns modos de mesclagem simplesmente perdem a funcionalidade em imagens achatadas&#8230; Enfim, o fato é que com esta sugestão é possível mesclar os elementos de seu site criando novos efeitos e indo muito além das inúmeras opções que já temos. Usando o novo parâmetro **blend mode** conseguimos um resultado 100% fiel ao mock-ups no Photoshop..

### Como funciona

Em CSS nós temos o parâmetro &#8220;z-index&#8221; que nos permite usar os elementos como camadas, escolhendo os que ficarão por cima e os que estarão por baixo de tudo. Usando os parâmetros **blend-mode** ou **background-blend-mode** é possível misturar as cores dos elementos do nosso site. Como usar uma DIV escura junto com uma imagem e dar o efeito de sombreamento, ou clarear elemento sobrepondo-o com um outro de fundo branco.

Podemos aplicar o modo de mesclagem em qualquer elemento do HTML que possua um preenchimento. Este preenchimento, correspondente a layer inferior no Photoshop, é a **cor base**. Se o elemento escolhido não estiver sobrepondo outro, considere a cor base o background do site. A **cor de mesclagem** é a da camada superior. É esta camada que pretendemos misturar. A cor de mesclagem irá se misturar com a cor base formando um novo resultado, que, para fins de explicação, vamos chamar de **cor resultante**. É esta a cor que vai aparecer no resultado final.

Este conceito pode ser explicado através de umas [fórmulas matemáticas][3], mas não vou entrar neste mérito aqui. O interessante no nosso contexto é saber o que cada modo faz e como aplica-lo no CSS.

Quer conferir ao vivo? Preparei uma [demo completa destes modos de mesclagem no CodePen][4]. Lembrando que você precisa de um dos browsers especiais citados no inicio do post para visualizar, ok?

### O código

Para o meu exemplo, estou considerando como base uma div sólida com a cor azul com o hexadecimal #00c0ff.

<img class="alignnone size-full wp-image-38139" alt="base" src="http://tableless.com.br/uploads/2013/07/base.jpg" width="660" height="400" srcset="uploads/2013/07/base.jpg 660w, uploads/2013/07/base-277x168.jpg 277w, uploads/2013/07/base-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />

Por padrão, todos os elementos estão no modo de mesclagem &#8220;normal&#8221;, o que significa que ele não irá interagir com elementos das camadas inferiores. Na prática isto quer dizer que o visual é o referente a cor de mesclagem.

<img class="alignnone size-full wp-image-38151" alt="normal" src="http://tableless.com.br/uploads/2013/07/normal.jpg" width="660" height="400" srcset="uploads/2013/07/normal.jpg 660w, uploads/2013/07/normal-277x168.jpg 277w, uploads/2013/07/normal-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />

Para aplicar um modo de mesclagem a sintaxe em CSS é bem simples.

<pre class="lang-css">* { -webkit-blend-mode: normal; blend-mode: normal; }</pre>

## Os Modos de Mesclagem

Infelizmente não foram todos os modos do Photoshop que foram introduzidos no CSS. Eis aqui uma listinha básica com todos os propostos, a sintaxe em CSS e um resumo geral do seu funcionamento.

### **Multiply** (Multiplicação)

&nbsp;

<img class="alignnone size-full wp-image-38150" alt="multiply" src="http://tableless.com.br/uploads/2013/07/multiply.jpg" width="660" height="400" srcset="uploads/2013/07/multiply.jpg 660w, uploads/2013/07/multiply-277x168.jpg 277w, uploads/2013/07/multiply-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />

<pre class="lang-css">* { -webkit-blend-mode: multiply; blend-mode: multiply; }</pre>

Este parâmetro multiplica a cor base pela cor de mesclagem. Imagine que você está pintando uma foto com uma caneta marcadora de texto. É este o efeito do multiply! Qualquer cor multiplicada por branco resulta nela mesma. Quando multiplicadas por matizes escuras, as cores ficam progressivamente mais escuras. Quando multiplicada pelo preto, o resultado será sempre o próprio preto. É ótima para fazer efeitos de sombreamento e vinhetas.

### Screen (Divisão)

&nbsp;

<img class="alignnone size-full wp-image-38154" alt="screen" src="http://tableless.com.br/uploads/2013/07/screen.jpg" width="660" height="400" srcset="uploads/2013/07/screen.jpg 660w, uploads/2013/07/screen-277x168.jpg 277w, uploads/2013/07/screen-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />

<pre class="lang-css">* { -webkit-blend-mode: screen; blend-mode: screen; }</pre>

Você pode pensar no screen como o contrário do multiply. Este parâmetro multiplica o inverso das cores de mesclagem e de base. A cor resultante é sempre mais clara. Quando dividido por preto a cor permanece inalterada e quando dividido por branco o resultado é o próprio branco.

### Overlay (Sobrepor)

&nbsp;

<img class="alignnone size-full wp-image-38152" alt="overlay" src="http://tableless.com.br/uploads/2013/07/overlay.jpg" width="660" height="400" srcset="uploads/2013/07/overlay.jpg 660w, uploads/2013/07/overlay-277x168.jpg 277w, uploads/2013/07/overlay-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />

<pre class="lang-css">* { -webkit-blend-mode: overlay; blend-mode: overlay; }</pre>

Reticula as cores. A cor de base não é substituída, clareada ou escurecida, mas sim misturada com a cor de mesclagem. Por exemplo, se você misturar Azul e Verde, resultará no amarelo.

### Darken (Escurecer)

&nbsp;

<img class="alignnone size-full wp-image-38143" alt="darken" src="http://tableless.com.br/uploads/2013/07/darken.jpg" width="660" height="400" srcset="uploads/2013/07/darken.jpg 660w, uploads/2013/07/darken-277x168.jpg 277w, uploads/2013/07/darken-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />

<pre class="lang-css">* { -webkit-blend-mode: darken; blend-mode: darken; }</pre>

Examina as cores dos elementos sobrepostos e seleciona a cor mais escura como a resultante. Se você tem um elemento escuro (como um logotipo monocromático, por exemplo) e está trabalhando sobre um fundo claro, você pode usar o Darken para retirar da imagem todos os pixels claros e deixar apenas os escuros inalterados.

### Lighten (Clarear)

&nbsp;

<img class="alignnone size-full wp-image-38148" alt="lighten" src="http://tableless.com.br/uploads/2013/07/lighten.jpg" width="660" height="400" srcset="uploads/2013/07/lighten.jpg 660w, uploads/2013/07/lighten-277x168.jpg 277w, uploads/2013/07/lighten-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />

<pre class="lang-css">* { -webkit-blend-mode: lighten; blend-mode: lighten; }</pre>

O oposto do Darken. Examina os elementos sobrepostos e o resultante é a tonalidade mais clara. Os pixels mais escuros que a cor de mesclagem são substituídos.

### Color-Dodge (Subexposição de cor)

&nbsp;

<img class="alignnone size-full wp-image-38141" alt="color-dodge" src="http://tableless.com.br/uploads/2013/07/color-dodge.jpg" width="660" height="400" srcset="uploads/2013/07/color-dodge.jpg 660w, uploads/2013/07/color-dodge-277x168.jpg 277w, uploads/2013/07/color-dodge-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />

<pre class="lang-css">* { -webkit-blend-mode: color-dodge; blend-mode: color-dodge; }</pre>

Clareia a cor de base para refletir a cor de mesclagem, diminuindo o contraste entre elas. A mesclagem com o preto não altera a imagem.

### Color-Burn (Superexposição de cor)

&nbsp;

<img class="alignnone size-full wp-image-38140" alt="color-burn" src="http://tableless.com.br/uploads/2013/07/color-burn.jpg" width="660" height="400" srcset="uploads/2013/07/color-burn.jpg 660w, uploads/2013/07/color-burn-277x168.jpg 277w, uploads/2013/07/color-burn-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />

<pre class="lang-css">* { -webkit-blend-mode: color-burn; blend-mode: color-burn; }</pre>

Como o nome indica, faz o contrário da subexposição de cor. Este parâmetro escurece a cor de base para refletir a cor de mesclagem, aumentando o contraste entre as duas. A mesclagem com o branco não altera a imagem.

### Hard-Light (Luz Direta)

&nbsp;

<img class="alignnone size-full wp-image-38146" alt="hard-light" src="http://tableless.com.br/uploads/2013/07/hard-light.jpg" width="660" height="400" srcset="uploads/2013/07/hard-light.jpg 660w, uploads/2013/07/hard-light-277x168.jpg 277w, uploads/2013/07/hard-light-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />

<pre class="lang-css">* { -webkit-blend-mode: hard-light; blend-mode: hard-light; }</pre>

O efeito Hard-Light é semelhante a iluminar o elemento com uma luz direta. Se a cor do elemento superior for mais clara que 50% de cinza, ele irá iluminar a cor base. Se a cor de mesclagem for próxima do preto (50% de cinza &#8220;para baixo&#8221;), a cor base será escurecida. Utilizar preto ou branco puro como cores de mesclagem produz respectivamente preto ou branco puro como cores resultantes.

### Soft-Light (Luz Indireta)

&nbsp;

<img class="alignnone size-full wp-image-38155" alt="soft-light" src="http://tableless.com.br/uploads/2013/07/soft-light.jpg" width="660" height="400" srcset="uploads/2013/07/soft-light.jpg 660w, uploads/2013/07/soft-light-277x168.jpg 277w, uploads/2013/07/soft-light-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />

<pre class="lang-css">* { -webkit-blend-mode: soft-light; blend-mode: soft-light; }</pre>

É o efeito de aplicar uma iluminação difusa na imagem, sendo que a cor de mesclagem é a fonte da luz. Se esta cor for mais clara que 50% de cinza, a cor resultante clareará (subexposição). Se a cor de mesclagem for mais escura do que 50% de cinza, a imagem ficará mais escura (superexposição). É ótimo para fazer leves realces ou sombras no elemento.

### Difference (Diferença)

&nbsp;

<img class="alignnone size-full wp-image-38144" alt="difference" src="http://tableless.com.br/uploads/2013/07/difference.jpg" width="660" height="400" srcset="uploads/2013/07/difference.jpg 660w, uploads/2013/07/difference-277x168.jpg 277w, uploads/2013/07/difference-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />

<pre class="lang-css">* { -webkit-blend-mode: difference; blend-mode: difference; }</pre>

Retira os pigmentos da cor do canal que tiver mais brilho e subtrai pelo outro. Por exemplo: Retirar o amarelo do verde resultará em azul. Qualquer cor mesclada com branco resultará em preto (branco é a presença de todas as cores). Agora, quando misturar com o preto, o resultado é sempre a própria cor base (preto é a ausência de cor).

### Exclusion (Exclusão)

&nbsp;

<img class="alignnone size-full wp-image-38145" alt="exclusion" src="http://tableless.com.br/uploads/2013/07/exclusion.jpg" width="660" height="400" srcset="uploads/2013/07/exclusion.jpg 660w, uploads/2013/07/exclusion-277x168.jpg 277w, uploads/2013/07/exclusion-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />

<pre class="lang-css">* { -webkit-blend-mode: exclusion; blend-mode: exclusion; }</pre>

Funciona de maneira semelhante ao modo de mesclagem Difference, mas com menor contraste.

### Saturation (Saturation)

&nbsp;

<img class="alignnone size-full wp-image-38153" alt="saturation" src="http://tableless.com.br/uploads/2013/07/saturation.jpg" width="660" height="400" srcset="uploads/2013/07/saturation.jpg 660w, uploads/2013/07/saturation-277x168.jpg 277w, uploads/2013/07/saturation-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />

<pre class="lang-css">* { -webkit-blend-mode: saturation; blend-mode: saturation; }</pre>

A cor resultante possuirá o valor de matiz e luminosidade da base, com a saturação da cor de mesclagem. Quando aplicada em áreas cinzas (saturação 0), não produz nenhum efeito.

### Color (Cor)

&nbsp;

<img class="alignnone size-full wp-image-38142" alt="color" src="http://tableless.com.br/uploads/2013/07/color.jpg" width="660" height="400" srcset="uploads/2013/07/color.jpg 660w, uploads/2013/07/color-277x168.jpg 277w, uploads/2013/07/color-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />

<pre class="lang-css">* { -webkit-blend-mode: color; blend-mode: color; }</pre>

Preserva os níveis de luminosidade da cor base, mesclando com a matiz e a saturação da cor de mesclagem. Como os níveis de cinza são preservadas é ótimo para colorir imagens monocromáticas.

### Luminosity (Luminosidade)

&nbsp;

<img class="alignnone size-full wp-image-38149" alt="luminosity" src="http://tableless.com.br/uploads/2013/07/luminosity.jpg" width="660" height="400" srcset="uploads/2013/07/luminosity.jpg 660w, uploads/2013/07/luminosity-277x168.jpg 277w, uploads/2013/07/luminosity-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />

<pre class="lang-css">* { -webkit-blend-mode: luminosity; blend-mode: luminosity; }</pre>

A cor resultante possui a luminosidade da cor de mesclagem com a matiz e saturação da base. Pode ser considerado o contrário do Color, já que substitui os tons de cinza mas preserva as cores bases.

### Hue (Matiz)

&nbsp;

<img class="alignnone size-full wp-image-38147" alt="hue" src="http://tableless.com.br/uploads/2013/07/hue.jpg" width="660" height="400" srcset="uploads/2013/07/hue.jpg 660w, uploads/2013/07/hue-277x168.jpg 277w, uploads/2013/07/hue-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />

<pre class="lang-css">* { -webkit-blend-mode: hue; blend-mode: hue; }</pre>

A cor resultante possui a matiz da cor de mesclagem com a luminosidade e saturação da base. É ótimo para alterar cores de imagens sem deixa-las mais claras ou escuras.

### Multiplos backgrounds

Você pode também utilizar os modos de mesclagens no background, em Divs com múltiplas imagens de fundo. A sintaxe em CSS é a seguinte:

<pre class="lang-css">.suaclasse { 
    background: url(img/bg1.jpg), url(img/bg2.jpg);
    background-repeat: repeat-x, no-repeat; 
    background-size: auto, cover;
    background-position: center bottom, left top;
    background-blend-mode: multiply, normal;
}</pre>

### Propriedade Knock-Out

Esta propriedade é especialmente útil em grupos de elementos. Quando usamos o parâmetro Knock-Out, utilizamos os modos de mesclagem apenas com os compostos com a primeira camada base (backdrop) e a cor de mesclagem, ignorando a &#8220;pilha&#8221; de camadas sobrepostas.

<pre class="lang-css">.suaclasse {
    knock-out: knock-out;
}</pre>

## Conclusão

Como dito anteriormente, os Modos de Mesclagem em CSS ainda são apenas um rascunho inicial. Não há suporte em nenhum navegador para este parâmetro, por isso, por enquanto, não é possível utilizar em um produto final.  Mesmo assim este é um assunto que vale a pena ser estudado já que pode revolucionar a maneira como desenvolvemos layouts para a web.

Já é possível fazer experiências dentro do [Fork do Chromium disponibilizado pela própria Adobe][1], no [Chrome Canary][5] e no [Webkit Nightly Build][6]. No Canary Chrome você deve habilitar os itens experimentais do webkit, digitando &#8220;chrome://flags&#8221; na barra de endereço, apertando &#8220;Enter&#8221; e dando &#8220;Enable&#8221; na opção &#8220;Experimental Webkit Features&#8221;.

#### Links Úteis

[Documentação na W3C][7]
  
[PhotoShop In The Browser: Understanding CSS Blend Modes][8]
  
[A Modern Look at Classic Blend Modes Changing How Elements Relate Visually][9]
  
[Fork do Chromium na Adobe][1]
  
[Chrome Canary][5]

 [1]: https://github.com/adobe/webkit/downloads
 [2]: http://dev.w3.org/fxtf/compositing-1/
 [3]: http://dev.w3.org/fxtf/compositing-1/#blending
 [4]: http://codepen.io/daniguerrato/pen/jGqrB
 [5]: http://www.google.ca/intl/en/chrome/browser/canary.html
 [6]: http://nightly.webkit.org/builds/trunk/mac/1
 [7]: http://www.w3.org/TR/compositing/
 [8]: http://demosthenes.info/blog/707/PhotoShop-In-The-Browser-Understanding-CSS-Blend-Modes?utm_source=CSS-Weekly&utm_campaign=Issue-66&utm_medium=web
 [9]: http://adobe.github.io/web-platform/demos/compositing/blend-photogallery/index.html