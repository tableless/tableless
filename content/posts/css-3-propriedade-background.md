---
title: CSS3 – Propriedade background
author: Diego Eis
type: post
date: 2006-07-24
url: /css-3-propriedade-background/
tweetbackscheck:
  - 1356463097
shorturls:
  - 'a:3:{s:9:"permalink";s:52:"http://tableless.com.br/css-3-propriedade-background";s:7:"tinyurl";s:26:"http://tinyurl.com/3dvs32t";s:4:"isgd";s:19:"http://is.gd/K0ONeN";}'
twittercomments:
  - 'a:2:{i:10322156047048704;s:7:"retweet";i:10410348850974720;s:7:"retweet";}'
tweetcount:
  - 2
dsq_thread_id: 503035730
categories:
  - Artigos
  - Browsers
  - Geral
  - Tecnologia e Tendências
tags:
  - Na Prática

---
A propriedade background terá suporte a múltiplas imagens. Ou seja, você poderá colocar várias imagens de background em um elemento. Conseqüentemente a separação por vírgulas das propriedades aumentará um bocado. Você terá códigos do tipo:

<pre class="lang-html">div {background-image: url(tl.png), url(tr.png), url(tr2.png);}
</pre>

Se você for definir tudo numa mesma linha e com o resto das propriedades, ficaria mais ou menos assim:

<pre class="lang-html">div { 
	background: url(t1.png) no-repeat left top, 
	url(tr.png) no-repeat center center, 
	url(tr2.png) no-repeat center top;
}
</pre>

Outra nova propriedade que surge é a background-origin. Ela determina como o background-position será calculado. Suponha que você tenha um elemento com borda e padding. Se o background-origin tiver o valor **border**, por exemplo, o background será desenhado tomando como referência o ponto &#8216;0 0&#8217; do limite da borda. Se o valor for **padding**, então a referência será tomada como o ponto &#8216;0 0&#8217; do limite do padding. Interessante, não é?

Você também poderá definir uma dimensão para a imagem de background. Veja o código de exemplo:

<pre class="lang-html">div {
	background-size: 15px 30px;
	background-image: url(tile.png);
}</pre>

Neste código, definimos que a imagem de background terá 15px de largura por 30px de altura.

Para fazer a imagem cobrir todo o background do elemento, utilize o valor **cover** no background-size. Dessa forma se a imagem for menor do que o elemento, a imagem vai se redimensionar pelo elemento inteiro.

Para mais informações interessantes sobre a propriedade Background no CSS3, visite o site do W3C, onde há mais detalhes e comentários dos editores: <http://www.w3.org/Style/CSS/current-work#background>.