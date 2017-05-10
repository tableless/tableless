---
title: Múltiplos backgrounds com CSS
author: Diego Eis
type: post
date: 2011-03-28
excerpt: Testando múltiplos backgrounds no CSS3. Isso realmente funciona! ;-)
url: /multiplos-backgrounds-com-css/
tweetbackscheck:
  - 1356398544
shorturls:
  - 'a:3:{s:9:"permalink";s:53:"http://tableless.com.br/multiplos-backgrounds-com-css";s:7:"tinyurl";s:26:"http://tinyurl.com/3pmvyde";s:4:"isgd";s:19:"http://is.gd/QV1ueJ";}'
twittercomments:
  - 'a:51:{i:53148945731428353;s:6:"137470";i:53879488567709696;s:6:"137498";i:53329936085303296;s:7:"retweet";i:52732623591710720;s:7:"retweet";i:52691320833179648;s:7:"retweet";i:52587052901990400;s:7:"retweet";i:52548639389790208;s:7:"retweet";i:52479688320364544;s:7:"retweet";i:52458679701737472;s:7:"retweet";i:52457797656387584;s:7:"retweet";i:52455735111593984;s:7:"retweet";i:52454789900021761;s:7:"retweet";i:52454675911409664;s:7:"retweet";i:52452350639603713;s:7:"retweet";i:52451636550959104;s:7:"retweet";i:52451318471737344;s:7:"retweet";i:52450714726825984;s:7:"retweet";i:52450617620303872;s:7:"retweet";i:52450414515335168;s:7:"retweet";i:52450342905978880;s:7:"retweet";i:52450265143574528;s:7:"retweet";i:52449957784977408;s:7:"retweet";i:60756092384313344;s:7:"retweet";i:60648164201463808;s:7:"retweet";i:60570834212896768;s:7:"retweet";i:60532668533719040;s:7:"retweet";i:60531969611669504;s:7:"retweet";i:60523832141824000;s:7:"retweet";i:60523765083291649;s:7:"retweet";i:60523266443460608;s:7:"retweet";i:147536434750959616;s:7:"retweet";i:147536048841428992;s:7:"retweet";i:147535720268038145;s:7:"retweet";i:147657264944250880;s:7:"retweet";i:169849728748621824;s:7:"retweet";i:169822905134358528;s:7:"retweet";i:169815165313880064;s:7:"retweet";i:169809058990272512;s:7:"retweet";i:169800652560670720;s:7:"retweet";i:169792635781914624;s:7:"retweet";i:169791980497408001;s:7:"retweet";i:169791332418723841;s:7:"retweet";i:169789879327272960;s:7:"retweet";i:169789752881577984;s:7:"retweet";i:193098847067713537;s:7:"retweet";i:193073182046035968;s:7:"retweet";i:193066642157219841;s:7:"retweet";i:193062295373492225;s:7:"retweet";i:268314972818391041;s:7:"retweet";i:268300661890887681;s:7:"retweet";i:268164589039013889;s:7:"retweet";}'
tweetcount:
  - 259
dsq_thread_id: 503040142
categories:
  - Código
  - CSS
  - CSS3
  - HTML
  - Técnicas e Práticas
tags:
  - 2011
  - CSS
  - CSS3
  - desenvolvimento
  - html5
  - Na Prática
  - tecnicascss

---
Uma das features mais esperadas por mim é sem dúvida a possibilidade de podermos definir múltiplos backgrounds via CSS. Chega de elementos extras e gambiarras. No CSS3 a propriedade background ganha várias funções, dentro elas a possibilidade de definirmos várias imagens como background em um único elemento.

A sintaxe é muito simples. Na verdade, é idêntica a sintaxe existente. Segue abaixo:

[cc lang=&#8221;css&#8221;]
  
div {
	  
width:600px;
	  
height:500px;
	  
border:1px solid black;
	  
background:
	  
url(gradiente-top.png) top left repeat-X,
	  
url(gradiente-baixo.png) bottom left repeat-X,
	  
url(gradiente-esquerda.png) top left repeat-Y,
	  
url(gradiente-direita.png) top right repeat-Y;
  
}
  
[/cc]

Veja que basta definirmos diversas vezes a propriedade URL com as imagens que escolher e pronto. Os atributos de posição e repetição continuam iguais!
  
É tão simples que dispensa grandes explicações. No exemplo acima usei 4 imagens em gradiente transparente. Duas para os lados e as outras duas para o topo e baixo. 

<a href="http://tableless.github.com/exemplos/multiple-background/index.html" rel="external">Testando com o HTML</a>