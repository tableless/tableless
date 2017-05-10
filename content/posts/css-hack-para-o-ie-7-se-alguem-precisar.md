---
title: CSS Hack para o IE 7 – se alguém precisar
author: Diego Eis
type: post
date: 2007-04-26
url: /css-hack-para-o-ie-7-se-alguem-precisar/
tweetbackscheck:
  - 1356400844
shorturls:
  - 'a:3:{s:9:"permalink";s:63:"http://tableless.com.br/css-hack-para-o-ie-7-se-alguem-precisar";s:7:"tinyurl";s:26:"http://tinyurl.com/3luxwvo";s:4:"isgd";s:19:"http://is.gd/ufyRIx";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 503014851
categories:
  - Browsers
tags:
  - cotidiano
  - Técnicas e Práticas

---
Ontem precisei de um hack para IE7. Fiz uma busca rápida e encontrei algo bem fácil.

Lembra do csshack para IE que você colocava um _ (underline) na frente da propriedade que você gostaria que só o IE entendesse? Pois é&#8230; ele não funciona no IE7. Mas&#8230; se trocarmos o _ (underline) por * (asterísco) ele passa funcionar! 🙂

`div {<br />
background:green;<br />
*background:red; /* essa linha funciona no IE7 */<br />
}`

Fizeram o underline parar de funcionar, mas esqueceram do asterísco. 😉