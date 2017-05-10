---
title: Flexbox – Organizando seu layout
author: Diego Eis
type: post
date: 2012-10-01
excerpt: Entenda como a recomendação de Flexbox poderá nos ajudar a organizar a estrutura de sites e aplicações
url: /flexbox-organizando-seu-layout/
tweetbackscheck:
  - 1356400672
shorturls:
  - 'a:3:{s:9:"permalink";s:31:"http://tableless.com.br/?p=7022";s:7:"tinyurl";s:26:"http://tinyurl.com/9nvk4om";s:4:"isgd";s:19:"http://is.gd/liUWge";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 865932208
categories:
  - CSS3
  - Técnicas e Práticas
tags:
  - 2012
  - Browsers
  - CSS
  - CSS3
  - flexbox
  - float
  - html5

---
O CSS Flexible Box Layout Model ou simplesmente **Flexbox** faz parte da especificação do CSS3 que promete organizar elementos na página previsivelmente quando o layout precisa ser visualizado em diversos tamanhos de tela e em diversos dispositivos.
  
O Flexbox nos ajuda a organizar esses elementos sem a ajuda do float e também nos ajudam a sanar problemas de [Box Model][1] que normalmente acontecem quando acrescentamos, padding, margin e border além da largura do elemento.

A ideia é simples: os filhos de um elemento com flexbox pode se posicionar em qualquer direção e pode ter dimensões flexíveis para se adaptar. Você pode posicionar os diversos elementos independente da sua posição na estrutura do HTML, o que é muito bom. Um dos problemas do float a sua dependência com os elementos na estrutura do HTML. Estes elementos precisam estar em uma ordem específica, se não o layout não dá certo. Com o Flexbox essa ordem não importa, isso quer dizer que você pode organizar a informação do seu HTML de beneficiando o SEO e Acessibilidade. O código da estruturação destes elementos fica mais simples e fácil de manter.

**Atenção:** O Flexbox ainda é uma especificação e ainda deve ser usada com prefixos como -webkit-, -moz-, -ms-, -o-.

[Veja o exemplo completo no nosso GITHUB.][2]

### Elementos e Vocabulário

Você precisa entender que o Flexbox é uma nova maneira de posicionar elementos do seu layout e por isso precisamos de novos nomes para identificar os elementos da estrutura. 

**Flex container** é o elemento que envolve sua estrutura. Você define que um elemento é um Flex Container com a propriedade _display_ com os valores _flex_ ou _inline-flex_.

**Flex Item** são os elementos filho do **flex container**.

**Eixos ou Axes** são as duas direções básicas que existem em um Flex Container: _main axis_, que seria o eixo horizontal ou o eixo principal e o _cross axis_ que seria o eixo vertical.

**Directions** determina a origem e o término do fluxo dos ítens. Eles seguem o vetor estabelecido pelo modo traidicional de escrita: esquerda para direita, direita para esquerda etc.

A propriedade _order_ determina o lugar que os elementos aparecerão.
  
A propriedade _flex-flow_ determina a ordem do fluxo em que os elementos aparecerão.

Você pode definir se os elementos serão forçados a ficar em uma mesma linha ou se eles irão quebrar em várias linhas com a propriedade **flex-wrap**.

### Definindo uma estrutura Flexbox

Para iniciarmos, segue o HTML básico abaixo:

<pre class="lang-html">&lt;!DOCTYPE html&gt;
&lt;html lang="pt-br"&gt;
&lt;head&gt;
    &lt;title&gt;Exemplo Flexbox&lt;/title&gt;
    &lt;meta charset="utf-8"&gt;
&lt;/head&gt;
&lt;body&gt;

&lt;div class="main"&gt;
    &lt;div&gt;Um div&lt;/div&gt;
    &lt;div&gt;Segundo div&lt;/div&gt;
    &lt;div&gt;Terceiro Div&lt;/div&gt;
&lt;/div&gt;

&lt;/body&gt;
&lt;/html&gt;
</pre>

Agora vamos para o CSS. Primeiro definimos para o div MAIN virar um Flex Container. Para isso definimos a propriedade display com os valores _flex_ ou _inline-flex_. O valor FLEX faz o elemento ser um BLOCO, com o valor inline-flex, o elemento vira um inline-block com as propriedades de Flex Container.

<pre class="lang-css">.main {
    display: -webkit-flex;
    display: flex;
}

/** Para deixar uma corzinha de fundo nos divs filhos **/
.main div {
    background:#CCC;
    margin-right:10px;
}
</pre>

Se fizermos isso automaticamente os divs dentro do nosso **.main** já ficarão um ao lado do outro.

Para você fazer com que os **flex items** (filhos do Flex Container) comecem a ter uma largura distribuída, basta definir para eles a propriedade _flex_, como abaixo:

<pre class="lang-css">.main {
    width:500px;
    background:#EFEFEF;
    height:500px;
    display: -webkit-flex;
    display: flex;
}

.main div {
    background:#CCC;
    margin-right:10px;

    -webkit-flex:1 1 auto;
    flex:1 1 auto;
}
</pre>

Até agora está ficando assim:



A propriedade **flex** é um atalho para as propriedades _flex-grow, flex-shrink e flex-basis_. O flex-basis define a largura dos flex items. Deixemos eles quietinhos por enquanto. 

Suponha agora que você queira modificar a ordem com que os elementos apareçam. Simples, use a propriedade **order** e modifique a ordem das colunas:

<pre class="lang-css">.main div.primeiroDiv {-webkit-order:2;}
.main div.segundoDiv {-webkit-order:3;}
.main div.terceiroDiv {-webkit-order:1;}
</pre>



Nada de float para lá e float para cá. Só uma mudança de números e pronto. Simple like that.

Vamos pular para o **.main** novamente.

### Flex-flow &#8211; definindo colunas ou linhas

Agora suponha que você queira linhas em vez de colunas. Tipo, você quer fazer uma versão para mobiles, em mobiles ter colunas é ruim, então você quer colocar uma coluna em cima da outra, coisa básica. Fazemos isso toda hora retirando os floats e as larguras das colunas. Aqui você define apenas a propriedade **flex-flow** com o valor **column** e pronto!

<pre class="lang-css">.main {
    width:500px;
    background:gray;
    height:500px;
    display: -webkit-flex;
    display: flex;

    -webkit-flex-flow: column;
    flex-flow: column;
}
</pre>

Os outros valores da propriedade **flex-flow** são row, row-reverse e column-reserve. O row-reverse e o column-reserve invertem a ordem dos elementos automaticamente sem a obrigação de modificar novamente a propriedade order definido em cada elemento. Coisa linda, fala aí.



### Conclusão e referências

O Flexbox hoje roda em Chrome. Fiz testes no Safari 6 e não funcionou. No IE10 dizem que funciona com o -ms- aplicado. Acho que não ficaremos muito tempo sem utilizar essa recomendação. Ano que vem, talvez? 😉

[Veja o exemplo completo no nosso GITHUB.][2]

Será recomendado que o flexbox seja utilizado para layouts simples e organização de elementos internos. Para layouts mais complexos e maiores, a sugestão é que o método de Grid Layout seja utilizado. Temos um exemplo aqui de como funcionaria mais ou menos o [Grid Layout][3] &#8211; na verdade seria o Template Layout.

Isso é um grande avanço para a Arquitetura de Layouts. Não vamos mais depender da estrutura do HTML para fazermos nossos layouts. Fazer layouts responsivos ficará muito mais fácil e aplicações que precisam ter suas estruturas totalmente mudadas nos diversos dispositivos serão simples de manter. Reutilizaremos totalmente nosso HTML já programado e o CSS controlará de fato a camada visual das nossas aplicações e sites.

  * [Link para a documentação][4]
  * [Flexbox Playground &#8211; veja um exemplo modificando seus valores][5]

 [1]: http://tableless.com.br/css_box_model/
 [2]: http://tableless.github.com/exemplos/flexbox.html
 [3]: http://tableless.com.br/css3-modulo-template-layout/
 [4]: http://www.w3.org/TR/css3-flexbox/
 [5]: http://demo.agektmr.com/flexbox/