---
title: Cuidado onde você enfia essa tag aí!
author: Elcio Ferreira
type: post
date: 2006-10-27
url: /cuidado-onde-voce-enfia-essa-tag-ai/
tweetbackscheck:
  - 1355926493
shorturls:
  - 'a:3:{s:9:"permalink";s:59:"http://tableless.com.br/cuidado-onde-voce-enfia-essa-tag-ai";s:7:"tinyurl";s:26:"http://tinyurl.com/3e5bt5a";s:4:"isgd";s:19:"http://is.gd/t2JAzQ";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 503036224
categories:
  - Geral
tags:
  - cotidiano
  - Técnicas e Práticas

---
Tenho respondido muito essa dúvida ultimamente. É o seguinte, se você tiver que usar formulários e tabelas, isso aqui:

`Tenho respondido muito essa dúvida ultimamente. É o seguinte, se você tiver que usar formulários e tabelas, isso aqui:

` 

É código inválido, errado, e não funciona no Firefox. Quando ele encontra a tag tr, ele fecha automaticamente o form para você. É como se você estivesse criando um formulário vazio e colocando uma série de campos na tabela fora do formulário. Se você tem um submit comum, não via conseguir nem submeter o formulário. Se submete via javascript, por exemplo, ao final da função de validação, vai dar submit num formulário vazio. Não chega nada no server-side. O certo é fazer:

``Tenho respondido muito essa dúvida ultimamente. É o seguinte, se você tiver que usar formulários e tabelas, isso aqui:

`Tenho respondido muito essa dúvida ultimamente. É o seguinte, se você tiver que usar formulários e tabelas, isso aqui:

` 

É código inválido, errado, e não funciona no Firefox. Quando ele encontra a tag tr, ele fecha automaticamente o form para você. É como se você estivesse criando um formulário vazio e colocando uma série de campos na tabela fora do formulário. Se você tem um submit comum, não via conseguir nem submeter o formulário. Se submete via javascript, por exemplo, ao final da função de validação, vai dar submit num formulário vazio. Não chega nada no server-side. O certo é fazer:

`` 

A gente usava do jeito anterior na era pré-Tableless, porque sem CSS era impossível remover aquele espaço antes e depois do formulário. Vício do século passado, do qual você precisa se livrar. Hoje, basta:

```Tenho respondido muito essa dúvida ultimamente. É o seguinte, se você tiver que usar formulários e tabelas, isso aqui:

`Tenho respondido muito essa dúvida ultimamente. É o seguinte, se você tiver que usar formulários e tabelas, isso aqui:

` 

É código inválido, errado, e não funciona no Firefox. Quando ele encontra a tag tr, ele fecha automaticamente o form para você. É como se você estivesse criando um formulário vazio e colocando uma série de campos na tabela fora do formulário. Se você tem um submit comum, não via conseguir nem submeter o formulário. Se submete via javascript, por exemplo, ao final da função de validação, vai dar submit num formulário vazio. Não chega nada no server-side. O certo é fazer:

``Tenho respondido muito essa dúvida ultimamente. É o seguinte, se você tiver que usar formulários e tabelas, isso aqui:

`Tenho respondido muito essa dúvida ultimamente. É o seguinte, se você tiver que usar formulários e tabelas, isso aqui:

` 

É código inválido, errado, e não funciona no Firefox. Quando ele encontra a tag tr, ele fecha automaticamente o form para você. É como se você estivesse criando um formulário vazio e colocando uma série de campos na tabela fora do formulário. Se você tem um submit comum, não via conseguir nem submeter o formulário. Se submete via javascript, por exemplo, ao final da função de validação, vai dar submit num formulário vazio. Não chega nada no server-side. O certo é fazer:

`` 

A gente usava do jeito anterior na era pré-Tableless, porque sem CSS era impossível remover aquele espaço antes e depois do formulário. Vício do século passado, do qual você precisa se livrar. Hoje, basta:

``` 

Ah, sim, se você validar seu código, vai detectar esse problema. Mais uma razão para validar.