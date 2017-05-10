---
title: O que são Media Types do CSS?
author: Diego Eis
type: post
date: 2006-02-06
excerpt: Media Types servem para direcionar um determinado CSS para um determinado tipo de meio de acesso.
url: /o-que-sao-media-types/
aktt_notify_twitter:
  - no
tweetbackscheck:
  - 1356446588
shorturls:
  - 'a:3:{s:9:"permalink";s:45:"http://tableless.com.br/o-que-sao-media-types";s:7:"tinyurl";s:26:"http://tinyurl.com/3v79y6k";s:4:"isgd";s:19:"http://is.gd/Oi4big";}'
twittercomments:
  - 'a:1:{i:52705573715722240;s:6:"137424";}'
tweetcount:
  - 1
dsq_thread_id: 503034623
categories:
  - Código
  - CSS
  - O Básico
  - Técnicas e Práticas
  - Tecnologia e Tendências
tags:
  - CSS
  - CSS3
  - desenvolvimento web
  - html
  - media queries
  - Media Types
  - Na Prática
  - tableless
  - web standards
  - xhtml

---
O CSS foi feito para que pudéssemos dizer como o documento irá se apresentar ao usuário em diferentes meios de acesso. Seja ele na tela do seu monitor, na sua impressora, no seu PDA, no seu sintetizador de voz, celular, smartphone, microondas etc e etc&#8230; Não importa com qual dispositivo o usuário esteja acessando seu site, ele deve ser bem apresentado. 

O [W3C][1] criou uma forma para fazermos isso com a maior facilidade. Você pode criar um CSS específico para cada tipo de meio de acesso, com a mesma facilidade que você cria um CSS para ser visto em um Desktop. Você pode personalizar um site para ser visto em um Smartphone ou até mesmo quando o visitante imprimir uma página de texto do seu site. Utilizando o caso da impressão: não é interessante para o visitante, que o menu, banners e outros elementos do site sejam impressos no papel.

Para isso, basta definir para qual tipo de media que você está dirigindo um arquivo CSS especifico. Existem dois jeitos:

**1.** O primeiro jeito é usado ao importar um arquivo CSS com o @import:

<pre lang="css" line="1">@import url("impressao.css") print;</pre>

Primeiro vem o arquivo que você quer importar, e logo depois você define para qual media ele será usado.

**2.** No segundo modo você usará o @media. É muito usado internamente no código CSS. Muito útil quando você quer definir apenas poucas linhas para uma media especifica:

<pre lang="css" line="1">@media print {
  /* Código CSS */
}</pre>

**3.** Neste modo você usará quando linkar o arquivo CSS no Cabeçalho do documento:

<pre lang="css" line="1"><link rel="stylesheet" type="text/css" media="print" href="impressao.css" />
</pre>

### Tipos de Medias

Na especificação você pode definir CSS para um bocado de dispositivos, veja a lista abaixo:

screen
:   Para computadores, PC´s. Ou algum dispositivo que tenha uma boa tela colorida.

print
:   Para impressoras. Muito usado para dar uma versão de impressão do site.

handheld
:   Para PDAs, celulares e aparelhos que geralmente tem uma tela pequena.

projection
:   Para projetos de apresentações. Você pode transformar seu site em uma apresentação estilo PowerPoint!

aural
:   Para Sintetizadores de Tela.

braille 
:   Para dispositivos táteis. Impressionante, ahn? Um cego poder &#8220;imprimir&#8221; um artigo para poder ler onde quiser.

tv
:   Para televisões. A resolução da televisão é muito inferior a um monitor CRT, eles merecem um tratamento especial.

tty
:   Para dispositivos que usam uma grade fixa de caractéres, terminais, dispositivos portáteis, etc&#8230;

O **screen** agora pode ser direcionado para Smartphones, com telas bacanas como o iPhone e celulares com Android por meio das [Media Queries][2]. O **handheld** é largamente usado para celulares que não são smartphones, mas são celulares menores, com telas bacanas. Normalmente, estes celulares utilizam Opera Mini, o que é uma vantagem por conta da larga compatibilidade que o Opera tem com Padrões Web. 

O **projection** foi primeiramente idealizado pelo Opera, foi conhecido também como Opera Show &#8211; para ver isso funcionando, visite o site do [Opera Show][3] com o [Opera][4] e aperte <kbd>F11</kbd>.

**TV** e **TTY** são pouco utilizados hoje. Quem tem uma televisão bacana em casa, consegue ter a mesma experiência de um monitor comum. Na minha opinião, não sei se ela sobrevive. A TTY talvez seja bem utilizada em nichos específicos já que é para aparelhos que tem uma tela bem limitada e que executam tarefas específicas. Talvez terminais pequenos, geralmente monocromáticos e etc. Também não tenho certeza da sua utilidade no futuro.

A idéia é dar para todos os meios de acesso uma boa experiência de utilização. O visitante pode iniciar a visitação do seu site em um smartphone ou celular, e terminar em um desktop. Não importa, ele precisa ter uma boa experiência nos dois meios.

Para ter mais detalhes:

  * [Media types Contents][5]
  * [Minimo Project][6]
  * [Opera Show Tutorial][3]
  * [Google: O que são Media Types?][7]

 [1]: http://w3c.org/
 [2]: http://tableless.com.br/introducao-sobre-media-queries
 [3]: http://www.opera.com/support/tutorials/operashow/
 [4]: http://www.opera.com/
 [5]: http://www.w3.org/TR/REC-CSS2/media.html
 [6]: http://www.mozilla.org/projects/minimo/
 [7]: http://www.google.com.br/search?q=O+que+s%C3%A3o+Media+Types