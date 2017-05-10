---
title: font-face
author: Diego Eis
type: post
date: 2007-08-14
url: /font-face/
aktt_notify_twitter:
  - no
tweetbackscheck:
  - 1356425651
shorturls:
  - 'a:3:{s:9:"permalink";s:33:"http://tableless.com.br/font-face";s:7:"tinyurl";s:26:"http://tinyurl.com/44w2yoa";s:4:"isgd";s:19:"http://is.gd/2g5v8m";}'
twittercomments:
  - 'a:2:{i:15586719831166977;s:7:"retweet";i:48430804329697280;s:6:"137268";}'
tweetcount:
  - 2
dsq_thread_id: 503037311
categories:
  - Artigos
  - CSS
  - Técnicas e Práticas
tags:
  - CSS
  - html
  - tecnicascss

---
A propriedade @font-face permite que usemos famílias de fontes que não estão instaladas no computador do usuário. Estamos acostumados a usar (os designers que o digam) um [pacote de fontes muito limitado][1] de fonts.
  
O @font-face faz com que o browser baixe, instale e renderize uma font na página.
  
Nem preciso falar que isso pode deixar o site um pouco mais lerdo. Outro ponto é que nenhum dos browsers tem suporte para isso hoje.

Veja um exemplo:

`@font-face {<br />
font-family: Nome da Fonte, Verdana, Arial, Tahoma, Sans-Serif;<br />
src: url(enderecodafonte);<br />
}`

Existem outras maneiras usando flash. Acontece que a página fica lerdíssima dependendo de quatno texto o camarada aplicou a técnica. Para mim é uma manobra muito trabalhosa.

Links para visitar:

  * [CSS Typography][2]
  * [Common Fonts][1]
  * [Fonts do OS X][3]
  * [Fonts do OS 9][4]
  * [@font-face: fonts the way you want them][5]
  * [Fonts instaladas com o IE][6]
  * [Fonts dos Win98][7]
  * [Fonts no Windows XP][8]

 [1]: http://www.ampsoft.net/webdesign-l/WindowsMacFonts.html
 [2]: http://www.digital-web.com/articles/css_typography/
 [3]: http://www.wpdfd.com/editorial/osxfonts.htm
 [4]: http://www.wpdfd.com/editorial/os9fonts.htm
 [5]: http://www.css3.info/font-face-fonts-the-way-you-want-them/
 [6]: http://www.wpdfd.com/editorial/iefonts.htm
 [7]: http://support.microsoft.com/default.aspx?scid=kb;en-us;195708
 [8]: http://www.wpdfd.com/editorial/xpfonts.htm