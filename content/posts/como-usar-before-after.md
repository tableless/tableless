---
title: Como usar os pseudo elementos :before e o :after
author: Diego Eis
type: post
date: 2012-07-23
excerpt: Como utilizar os pseudo-elementos :before e :after com a propriedade content.
url: /como-usar-before-after/
tweetbackscheck:
  - 1356409155
dsq_thread_id: 776755199
shorturls:
  - 'a:3:{s:9:"permalink";s:47:"http://tableless.com.br/como-usar-before-after/";s:7:"tinyurl";s:26:"http://tinyurl.com/d8fuy2s";s:4:"isgd";s:19:"http://is.gd/veZvuf";}'
twittercomments:
  - 'a:12:{i:227464509395189760;s:7:"retweet";i:227392267093164032;s:7:"retweet";i:227385027426672640;s:7:"retweet";i:231018323461152768;s:7:"retweet";i:230764490201894912;s:7:"retweet";i:230763824305815553;s:7:"retweet";i:230377812429774848;s:7:"retweet";i:230292768524750849;s:7:"retweet";i:230281665841360896;s:7:"retweet";i:230281605665677312;s:7:"retweet";i:243824350191558659;s:7:"retweet";i:243817083832500224;s:7:"retweet";}'
tweetcount:
  - 27
categories:
  - CSS
  - HTML
  - Técnicas e Práticas
tags:
  - 2012
  - CSS
  - html

---
Muito parecido com as pseudo-classes os pseudo-elementos são elementos inseridos dinamicamente via CSS. No caso das pseudo-classes, o browser finge que insere uma classe dinâmica em um elemento para que você customize um determinado estado do elemento. Por exemplo, a pseudo-classe **:hover** estiliza o estado de quando o mouse é colocado em cima dos elementos. Os pseudo-elementos funcionam quase da mesma forma. Existem vários, mas eu vou me focar agora apenas no **:before** e no **:after**. Ambos funcionam da mesma forma.

Os pseudo-elementos **:before** e **:after** trabalham em parceria com uma propriedade chamada **content**. Veja o pedaço de código abaixo:



Eu começo selecionando o elemento **a**. Com o pseudo-elemento **:before** eu digo ao navegador que quero fazer algo no início deste elemento. A propriedade **content** serve para inserir conteúdo dinâmico no HTML. Nesse caso, estou inserindo uma &#8220;setinha&#8221; antes do objeto. É mais ou menos como no JQuery, quando você utiliza as funções **prepend** (**:before**) e **append** (**:after**).

Eu posso estilizar da maneira que eu quiser novo elemento. É como se você colocasse um **span** com algum conteúdo. Logo, você pode fazer algo como o código abaixo:



Tem algumas limitações, por exemplo, eu não posso colocar vários elementos e também não consigo colocar código HTML.
  
Mesmo assim, podemos &#8220;criar&#8221; este elemento e colocar uma imagem de background ou até mesmo inserir uma font-icon para facilitar a inserção de ícones no layout.

Lembrando que isso só funciona a partir do IE8.