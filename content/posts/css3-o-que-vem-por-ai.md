---
title: CSS3 – O que vem por aí…
author: Thaiana Poplade
type: post
date: 2010-11-22
excerpt: 'Além da linguagem de marcação, a semântica e a utilização de bibliotecas Javascript no desenvolvimento HTML5, as folhas de estilo também serão reestruturadas para atender as diversas possibilidades que os novos padrões permitirão. Portanto, com vocês: o CSS3.'
url: /css3-o-que-vem-por-ai/
aktt_notify_twitter:
  - yes
tweetbackscheck:
  - 1356419740
shorturls:
  - 'a:3:{s:9:"permalink";s:45:"http://tableless.com.br/css3-o-que-vem-por-ai";s:7:"tinyurl";s:26:"http://tinyurl.com/3kz68rr";s:4:"isgd";s:19:"http://is.gd/NDOjx6";}'
twittercomments:
  - 'a:6:{i:10012283849670658;s:6:"136227";i:10365828440530944;s:6:"136246";i:12480490867007488;s:6:"136274";i:11459776504397824;s:7:"retweet";i:10366813237940224;s:7:"retweet";i:10120186254336000;s:7:"retweet";}'
tweetcount:
  - 13
dsq_thread_id: 503039757
categories:
  - CSS
  - CSS3
  - HTML
tags:
  - 2010
  - CSS3
  - desenvolvimento web
  - padroes web

---
O grande papel do desenvolvedor Front-End, na minha opinião, é traduzir em tags html, folhas de estilos e programação Javascript ou até mesmo uma linguagem backside, aquilo que o designer de interface criou e espera estar disponível a clicks e à leitura dos usuários. Ao meu ver, este é o nosso grande trabalho, recriar interfaces de forma adaptada aos diversos browsers de mercado e às diversas possibilidades tecnológicas que temos na web respeitando os limites dos padrões online e a essência da criação visual.

Com a “quase” padronização entre browsers, as infinitas possibilidades Front-End e a atualização do html, nós teremos a chance de ampliar conhecimento saindo do estigma de “recortes de imagens” ou criadores de códigos não planejados e nada semânticos. Já <a href="http://tableless.com.br/afinal-o-que-muda-com-o-html-5" target="_blank">comentei algo a respeito em outro artigo</a> e reforço a mensagem neste, pois o assunto é novas tecnologias e novo aprendizado, sendo assim, esta questão de mercado também deverá vir à tona quando o desenvolvimento web começar a exigir o uso do HTML5 e seus companheiros.

De fontes não pertencentes ao grupo das <a href="http://www.w3.org/TR/WD-font/" target="_blank">WebFonts</a> à sombras e gradientes, o CSS3 promete revolucionar e dar ao desenvolvedor ainda mais possibilidades de traduzir elementos visuais em códigos dentro de folhas de estilo diminuindo consideravelmente o “recorte de imagens”.

De antemão, eu alerto: não vamos sair por aí já utilizando essas possibilidades, salvo em casos de testes, pois as devidas documentações normativas ainda estão sendo escritas pela W3C e muitos browsers ainda não conseguem renderizar algumas propriedades.

Afinal o que vamos poder realizar com o CSS3?!

Primeiramente, enfatizo duas das novas possibilidades do CSS3 já descritas aqui no Tableless &#8211; o uso das propriedades “font-face” e do “background gradient”.
  
Imaginou poder colocar em seu website uma fonte da família “Butter” e fazer um gradiente radial sem precisar recortar imagens de repetição? Pois estas duas propriedades nos auxiliarão nesta missão. Abaixo, o link para os dois artigos &#8211; tutoriais criados pelo Diego falando melhor sobre o assunto:

@font-face &#8211; <a href="http://tableless.com.br/font-face-fonts-externas-na-web" target="_blank">http://tableless.com.br/font-face-fonts-externas-na-web</a>
  
Gradientes em CSS3 &#8211; <a href="http://tableless.com.br/gradientes-em-css" target="_blank">http://tableless.com.br/gradientes-em-css</a>

<a href="http://tableless.com.br/gradientes-em-css" target="_blank"></a>No seletor “background”, duas novas possibilidades que prometem resolver parte dos problemas que tínhamos com layouts e vários tipos de imagens de fundo são &#8211; o uso de múltiplos background’s e a inserção de dimensões para imagens de fundo. Dessa maneira, com o CSS3 vamos poder adicionar mais de uma url de uma imagem de fundo para um mesmo elemento:

<pre lang="css" line="1">background:url (fundo1.png) no-repeat 0px 0px, url(fundo2.jpg) repeat-x 0px 0px;</pre>

E especificar o tamanho de imagens de fundo:

<pre lang="css" line="1">background-size: 50% auto;</pre>

Textos poderão receber fontes “não padrão” utilizando a propriedade @font-face, anteriormente comentada, e poderão também receber a propriedade “text-shadow” que adicionará sombra ao texto e será declarada da seguinte forma:

<pre lang="css" line="1">text-shadow: 2px 2px 2px #000;</pre>

Além de famílias de fontes e sombra, ainda serão permitidas algumas propriedades relacionadas ao redimensionamento de elementos que contenham textos, como div’s, por exemplo, permitindo adicionar reticências automaticamente a textos que vão além das dimensões do elemento onde estão contidos, como na declaração abaixo de exemplo:

<pre lang="css" line="1">text-overflow: ellipsis-word;</pre>

As bordas também ganharão novas propriedades com grande expectativa para as bordas arredondadas. Além desta propriedade, as bordas poderão receber url de imagens como valores, tanto para top, bottom, left e right, quanto para o cantos. Exemplos das propriedades e valores para bordas:
  
ex 1:

<pre lang="css" line="1">border-image: url(border.png) 27 27 27 27 round round;</pre>

ex 2:

<pre lang="css" line="1">border-radius: 15px;</pre>

As cores também poderão ser declaradas não apenas em números hexadecimais, mas também em RGB e RGBA, além de valores para HSL e HSLA. Exemplo:

<pre lang="css" line="1">background: rgb(243, 191, 189);</pre>

Para finalizar essa breve introdução ao que nos será possível realizar com a chegada do CSS3, tão importante quanto as demais propriedades, será a propriedade “column”, que vai permitir ao desenvolvedor já estabelecer em quantas colunas um determinado conteúdo deverá ser divido, bem como o espaçamento e a largura que existirá entre elas. Esta propriedade, por enquanto, é aceita apenas pelo Firefox e pelo Safari. As declarações serão feitas desta forma:

<pre lang="css" line="1">-moz-column-width: 13em;
-webkit-column-width: 13em;
 -moz-column-gap: 1em; -webkit-column-gap: 1em;</pre>

Ao que tudo indica, nosso trabalho tende a se direcionar muito mais a arquitetura das propriedades que utilizaremos nas folhas de estilo buscando fazer uma tradução perfeita das interfaces criadas pelos designers, do que à adição desenfreada de “slices” em PSD’s.
  
Essas novidades ainda estão em estudo, testes e em padronização pela W3C, de qualquer forma, vale já começar a se familiarizar com que está por vir, principalmente no que diz respeito aos companheiros do HTML5 que prometem revolucionar o “jeito de se fazer websites”.