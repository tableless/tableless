---
title: Propriedade background-clip
author: Diego Eis
type: post
date: 2012-01-03
excerpt: Entenda como a propriedade background-clip do CSS3 funciona.
url: /propriedade-background-clip/
tweetbackscheck:
  - 1356443205
dsq_thread_id: 525035568
shorturls:
  - 'a:3:{s:9:"permalink";s:52:"http://tableless.com.br/propriedade-background-clip/";s:7:"tinyurl";s:26:"http://tinyurl.com/772snvm";s:4:"isgd";s:19:"http://is.gd/bKWwhc";}'
twittercomments:
  - 'a:15:{i:154172494906003456;s:7:"retweet";i:154195363039952896;s:7:"retweet";i:154177824259964929;s:7:"retweet";i:154177745398673408;s:7:"retweet";i:154177218552135680;s:7:"retweet";i:154173734192812032;s:7:"retweet";i:154173122260635648;s:7:"retweet";i:154173088337108993;s:7:"retweet";i:154172257743273984;s:7:"retweet";i:154171996534620160;s:7:"retweet";i:154171699632414720;s:7:"retweet";i:157976183714230272;s:7:"retweet";i:157775068523544576;s:7:"retweet";i:169914962419003392;s:7:"retweet";i:169914879979962368;s:7:"retweet";}'
tweetcount:
  - 32
categories:
  - CSS3
  - HTML
  - Técnicas e Práticas
tags:
  - 2012
  - Na Prática
  - tecnicascss
  - tutorial

---
A propriedade background-clip é muito simples de se entender. Até agora nós nunca tínhamos como controlar onde o background começaria a ser desenhado. Imagine que temos um elemento com um determinado padding e que você queira que o background, seja ele uma imagem ou uma cor, aparecesse somente onde está o conteúdo, ignorando a parte do padding. 

O background-clip tem 4 valores: border-box, content-box, padding-box e text. O valor text foi [inserido pelo pessoal do Webkit][1] em 2008 e dave ser incluída no padrões em algum momento por conta da sua utilidade!

[Este exemplo de como funciona a propriedade][2] dispensa maiores explicações.

[Aqui tem a documentação oficial.][3]

 [1]: http://www.webkit.org/blog/164/background-clip-text/
 [2]: http://tableless.github.com/exemplos/background-clip/
 [3]: http://www.w3.org/TR/css3-background/#the-background-clip