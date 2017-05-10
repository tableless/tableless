---
title: CSSHack para IE7, IE 6 e browsers de verdade
author: Diego Eis
type: post
date: 2007-05-02
url: /csshack-para-ie7-ie-6-e-browsers-de-verdade/
tweetbackscheck:
  - 1356431446
shorturls:
  - 'a:3:{s:9:"permalink";s:67:"http://tableless.com.br/csshack-para-ie7-ie-6-e-browsers-de-verdade";s:7:"tinyurl";s:26:"http://tinyurl.com/3v2jfx7";s:4:"isgd";s:19:"http://is.gd/1L8oTw";}'
twittercomments:
  - 'a:1:{i:33511365796831232;s:7:"retweet";}'
tweetcount:
  - 1
dsq_thread_id: 503037019
categories:
  - Tecnologia e Tendências
tags:
  - cotidiano
  - Técnicas e Práticas

---
Um aluno estava tendo um problema de compatibilidade: o layout funcionava em Firefox e IE6, mas quebrava em IE7. Para resolver, ele utilizou aquele hack do * (asterísco) no começo da propriedade. O problema é que este csshack do asterísco também funciona no IE6. Se ele arrumasse o IE7, o IE6 que quebrava por causa do hack. Isso é fácil de resolver, veja o código:
  
`Um aluno estava tendo um problema de compatibilidade: o layout funcionava em Firefox e IE6, mas quebrava em IE7. Para resolver, ele utilizou aquele hack do * (asterísco) no começo da propriedade. O problema é que este csshack do asterísco também funciona no IE6. Se ele arrumasse o IE7, o IE6 que quebrava por causa do hack. Isso é fácil de resolver, veja o código:
  
` 

Primeiro você usa a linha de código normal. Esta linha todos os browsers entendem.
  
Depois, logo abaixo, você coloca o csshack do asterísco, que funcionará em IE6 e IE7.
  
Para forçar o IE6 a ter o valor correto, você usa o csshack do &#8216;underline&#8217; no começo da propriedade. Como essa linha está vindo logo após do hack do asterísco, o valor do IE6 vai ser sobreescrito.

Horrível né? Paciência.

Fiz uma busca rápida para ver se encontrava outra solução, mas [achei este site][1] com a mesma solução acima.

 [1]: http://snook.ca/archives/html_and_css/targetting_ie7/