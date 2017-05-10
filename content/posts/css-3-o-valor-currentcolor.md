---
title: CSS 3 – O valor currentColor
author: Diego Eis
type: post
date: 2011-05-02
excerpt: O currentColor copia a cor da propriedade color e a aplica em outras propriedades de cor, como background, border e etc.
url: /css-3-o-valor-currentcolor/
tweetbackscheck:
  - 1356387766
shorturls:
  - 'a:3:{s:9:"permalink";s:50:"http://tableless.com.br/css-3-o-valor-currentcolor";s:7:"tinyurl";s:26:"http://tinyurl.com/3oxo8a8";s:4:"isgd";s:19:"http://is.gd/ELc6iB";}'
twittercomments:
  - 'a:6:{i:129006088900182016;s:7:"retweet";i:128919657284509697;s:7:"retweet";i:128816152628568064;s:7:"retweet";i:159648388789436418;s:7:"retweet";i:159634576417890304;s:7:"retweet";i:159617514630950915;s:7:"retweet";}'
tweetcount:
  - 12
dsq_thread_id: 503040254
categories:
  - CSS
  - Técnicas e Práticas
tags:
  - 2011
  - cores
  - CSS
  - CSS3
  - desenvolvimento web

---
O valor currentColor é muito simples de se entender e pode ser muito útil para diminuirmos o retrabalho em alguns momentos da produção. Imagine que o currentColor é uma variável cujo seu valor é definido pelo valor da propriedade color do seletor. Veja o código abaixo:

<pre lang="css" line="1">p {
		background:red;
		padding:10px;
		font:13px verdana;
		color: green;
		border:1px solid green;
	}
</pre>

Note que o valor da propriedade color é igual ao valor da cor da propriedade border.
  
Há uma redundância de código, que nesse caso é irrelevante, mas quando falamos de dezenas de arquivos de CSS modulados, com centenas de linhas cada, essa redundância pode incomodar a produtividade. A função do currentColor é simples: ele copia para outras propriedades do mesmo seletor o valor da propriedade color. Veja o código abaixo para entender melhor:

<pre lang="css" line="1">p {
		background:red;
		padding:10px;
		font:13px verdana;
		color: green;
		border:1px solid currentColor;
	}
</pre>

Veja que apliquei o valor currentColor onde deveria estar o valor de cor da propriedade border. Agora, toda vez que o valor da propriedade color for modificado, o currentColor aplicará o mesmo valor para a propriedade onde ela está sendo aplicada. 

Isso funciona em qualquer propriedade que faça utilização de cor como background, border, etc. Obviamente não funciona para a propriedade color. O currentColor também não funciona em seletores separados, ou seja, você não consegue atrelar o valor da propriedade color ao currentColor de outro seletor.