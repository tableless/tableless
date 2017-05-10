---
title: 'Lições sobre Semântica #4 – Listas'
author: Diego Eis
type: post
date: 2007-03-12
url: /licoes-sobre-semantica-4-listas/
tweetbackscheck:
  - 1356378423
shorturls:
  - 'a:3:{s:9:"permalink";s:55:"http://tableless.com.br/licoes-sobre-semantica-4-listas";s:7:"tinyurl";s:26:"http://tinyurl.com/3oyotbh";s:4:"isgd";s:19:"http://is.gd/psfrQJ";}'
twittercomments:
  - 'a:2:{i:12864226771075073;s:7:"retweet";i:18164952137203712;s:7:"retweet";}'
tweetcount:
  - 2
dsq_thread_id: 503036806
categories:
  - Artigos
tags:
  - Técnicas e Práticas

---
Recebi por email uma dúvida simples mas que muitas vezes o pessoal faz confusão:

> Bem, gostaria de saber semânticamente como vocês tratam uma sequência de ações, exemplo:
> 
> Ler comentário Ler todo o Artigo Deixar Comentários Versão para impressão
> 
> Já vi o pessoal por ai na web fazendo de diversas maneiras, usando um <p> seguido de 1 <a> para cada ação dessas, exemplo: <p><a href=&#8221;/&#8221; title=&#8221;&#8221;>Ler comentário><a href=&#8221;&#8221; title=&#8221;&#8221;>Ler todo o artigo</a><a href=&#8221;&#8221; title=&#8221;&#8221;>Deixar comentários</a></p>

Essa seqüencia é feita com Listas.
  
Existem 3 tipos de listas, listas ordenadas, listas não ordenadas e listas de definição. Talvez, no caso acima seria usada listas não ordenadas. O código HTML ficaria:

`<ul><br />
<li><a href="">Ler comentário</a></li><br />
<li><a href="">Ler todo o Artigo</a></li><br />
<li><a href="">Deixar Comentários</a></li><br />
<li><a href="">Versão para impressão</a></li><br />
</ul>`

Claro que há sempre aquele papo da [Subjetividade da Semântica][1].

 [1]: http://tableless.com.br/subjetividade-na-semantica