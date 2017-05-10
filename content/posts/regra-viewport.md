---
title: Entendendend a regra @viewport do HTML
author: Diego Eis
type: post
date: 2012-06-04
excerpt: Você poderá manipular o viewport diretamente do seu código CSS.
url: /regra-viewport/
shorturls:
  - 'a:3:{s:9:"permalink";s:39:"http://tableless.com.br/regra-viewport/";s:7:"tinyurl";s:26:"http://tinyurl.com/83gbvva";s:4:"isgd";s:19:"http://is.gd/cZJUGy";}'
twittercomments:
  - 'a:53:{i:211216799151308800;s:7:"retweet";i:210931280991358976;s:7:"retweet";i:210831873449009154;s:7:"retweet";i:210827712443584513;s:7:"retweet";i:210794826369732609;s:7:"retweet";i:210475205380943873;s:7:"retweet";i:209966522737766400;s:7:"retweet";i:209966520267325442;s:7:"retweet";i:209832112638009344;s:7:"retweet";i:209821939122970625;s:7:"retweet";i:209650215773409280;s:7:"retweet";i:209640703326826496;s:7:"retweet";i:209640653716594688;s:7:"retweet";i:209640572397420545;s:7:"retweet";i:209639211748442115;s:7:"retweet";i:215303511750082560;s:7:"retweet";i:215173442704642051;s:7:"retweet";i:215171560036765697;s:7:"retweet";i:215142824486768642;s:7:"retweet";i:215142116282728448;s:7:"retweet";i:218776835260026881;s:7:"retweet";i:218773597483831297;s:7:"retweet";i:218766550390411266;s:7:"retweet";i:218766233137446912;s:7:"retweet";i:223182387838844933;s:7:"retweet";i:223124817656815616;s:7:"retweet";i:223118693595496449;s:7:"retweet";i:223115100293300224;s:7:"retweet";i:230106682611597312;s:7:"retweet";i:230073719706488832;s:7:"retweet";i:230002897088290816;s:7:"retweet";i:236167976083132417;s:7:"retweet";i:236165949978464256;s:7:"retweet";i:236164033319931904;s:7:"retweet";i:241296232084017152;s:7:"retweet";i:248487648900026369;s:7:"retweet";i:248482457031172096;s:7:"retweet";i:254445792927043585;s:7:"retweet";i:253975234049351681;s:7:"retweet";i:253929145392832512;s:7:"retweet";i:253927324859371520;s:7:"retweet";i:253920498675752960;s:7:"retweet";i:253918625294069760;s:7:"retweet";i:253918239430684672;s:7:"retweet";i:266743339397832704;s:7:"retweet";i:266742358157168640;s:7:"retweet";i:266712811814662144;s:7:"retweet";i:266608611155902464;s:7:"retweet";i:266601566641987584;s:7:"retweet";i:271226367440465920;s:7:"retweet";i:270666842329194498;s:7:"retweet";i:270649352421257216;s:7:"retweet";i:270596697015607296;s:7:"retweet";}'
tweetbackscheck:
  - 1356404667
dsq_thread_id: 713377318
tweetcount:
  - 149
categories:
  - Acessibilidade
  - Código
  - CSS
  - HTML
  - Mobile
tags:
  - 2012
  - CSS
  - CSS3
  - mobile
  - tecnicascss
  - viewport

---
Faz algum tempo que podemos manipular o viewport dos browsers para podermos entregar um website mais adequado e confortável para os usuários. Essa manipulação era feita diretamente via uma metatag no head do documento, algo assim:

<pre class="lang-html">&lt;meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1.0"&gt;
</pre>

Isso é necessário por que você tem uma resolução gigante em aparelhos com a tela &#8220;relativamente&#8221; pequena, com 320&#215;480. Lembre-se que a resolução é uma coisa, o tamanho da tela é outra. Um iPhone tem uma resolução gigante (para mobiles, claro), de algo em torno de 900&#215;640, mas o tamanho da tela é de 320&#215;480. É por isso que quando você abre um website sem manipulação de viewport, ele aparece miniaturizado. Por que embora você esteja vendo o site em uma tela pequena, o site aparece como se estivesse numa resolução alta.

Quando manipulamos o viewport do browser, nós &#8220;diminuímos&#8221; essa resolução. Na linha do exemplo acima eu diminui a resolução do viewport do browser mobile para ter exatamente a mesma largura e altura da tela do aparelho. Logo, em vez de uma resolução de 900&#215;640, você verá o site em um resolução de 320&#215;480, no caso do iPhones 4S que mencionamos logo acima.

Assim fica bem mais fácil planejar um website para mobiles. O usuário não vai precisar ficar fazendo zoom ou gestos para procurar informações no site. Você planejará o design para que caiba nesse limite.

O pessoal do W3C está expandindo essa ideia e agora nós podemos aplicar a regra Viewport dentro de um código CSS em vez de ter que colocá-lo sempre no head.

A sintaxe é simples. Veja um exemplo:

<pre class="lang-css">@viewport {
  width: device-width;
  zoom: 1;
}
</pre>

Depois de determinar o viewport, você pode definir suas media queries normalmente, também diretamente de dentro do seu código CSS.

<pre class="lang-css">@viewport {
  width: device-width;
  zoom: 1;
}

@media screen and (min-width: 400px) {
  div { color: red; }
}

@media screen and (max-width: 400px) {
  div { color: green; }
}
</pre>

Lembrando que as media queries podem ser também definidas vida tag link, no head, assim:

<pre class="lang-html"><link rel="stylesheet" type="text/css" href="screen.css" media="screen and (min-width: 400px)" />

<link rel="stylesheet" type="text/css" href="mobile.css" media="screen and (max-width: 400px)" />
</pre>

Assim você pode chamar apenas um CSS e a partir dele distribuir seu código para as telas determinadas, tipo assim:

<pre class="lang-css">@viewport {
  width: device-width;
  zoom: 1;
}

@media screen and (min-width: 400px) {
  @import url(desktop.css);
}

@media screen and (max-width: 400px) {
  @import url(mobile.css);
}

</pre>

Toda essa informação faz parte da documentação que o W3C mantém chamda [CSS Device Adaptation][1].

O **@viewport** é suportado hoje pelo Internet Explorer 10 e pelo Opera, ainda sob seus respectivos prefixos. Mesmo assim, não demora muito para que os browsers Webkit suportem também, já que a ideia da manipulação de viewport originou-se na Apple com a vinda do iPhone.

Mais informações? Leia [aqui][1] e [aqui][2].

 [1]: http://dev.w3.org/csswg/css-device-adapt/
 [2]: http://dev.opera.com/articles/view/an-introduction-to-meta-viewport-and-viewport/