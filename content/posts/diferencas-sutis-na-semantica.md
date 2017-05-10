---
title: Diferenças sutis na semântica
author: Diego Eis
type: post
date: 2006-05-15
url: /diferencas-sutis-na-semantica/
tweetbackscheck:
  - 1356453483
shorturls:
  - 'a:3:{s:9:"permalink";s:53:"http://tableless.com.br/diferencas-sutis-na-semantica";s:7:"tinyurl";s:26:"http://tinyurl.com/3t44xgl";s:4:"isgd";s:19:"http://is.gd/oz3uFD";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 503035281
categories:
  - Geral
tags:
  - acessibilidade

---
Existem alguns elementos no HTML que parecem ser redundantes, como por exemplo a tag STRONG e a tag EM. Se você já tentou usá-las, percebeu que visualmente elas não mostram nenhuma diferença das tags B e I. Apenas visualmente.

Estas tags tem uma função semântica que é percebida apenas pelos deficientes visuais (pelo menos deveriam). Visualmente o STRONG e o B não tem nada de diferente, eles apenas marcam uma parte do texto como negrito. Mas a diferença entre os dois é invisivel para você.

Veja&#8230; Quando você usa STRONG, você dá um significado para aquela parte especifica do texto. Você diz que ela deve ser lida com mais força, com mais intensidade. Já com o elemento B você apenas marca em negrito o texto, e só. Ou seja, quando um browser para cegos (acho que ainda não existe nenhum assim) lê aquela parte com STRONG, a &#8220;voz dele&#8221; será alterada, ele passará a ler com mais força, já com o B isso não deve acontecer.
  
A mesma coisa acontece com o EM e o I. Quando uma parte do texto é marcada com EM, você dá um significado ao texto, você diz que aquela determinada parte deve ser lida com mais ênfase.