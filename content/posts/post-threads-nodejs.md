---
title: Threads no Node.js 10
authors: Breno Panzolini
type: post
date: 2018-01-07
excerpt: Uma introdução prática às threads no Node.js.
categories:
  - NodeJS
  - JavaScript
tags:
  - NodeJS
  - JavaScript
image: https://pre00.deviantart.net/52b2/th/pre/f/2017/092/7/4/nodejs_dark_by_wfuller-db4e1ip.png
---

Agora no final de junho (mais precisamente no dia 20/06/2018), foi feito o *release* da versão 10.5.0 do Node.js e uma das *features* principais foi a inclusão inicial (e ainda experimental, diga-se de passagem), do **suporte às threads**.

Nesse post vou tentar simplificar ao máximo a documentação do *[pull request]*(https://github.com/nodejs/node/pull/20876) e alguns detalhes técnicos, porém acredito ser suficiente para entendermos o básico da funcionalidade.

## Por que Threads?

Muita gente deve estar se perguntando do porque se utilizar threads em uma linguagem que sempre se orgulhou de nunca precisar desse tipo de mecanismo especialmente por conta do fantástico **event loop** e do **async I/O**.

O motivo disso é que o Node nunca foi a melhor opção para computação "pesada" de CPU, e por isso mesmo raramente é utilizado em projetos de *machine learning*, inteligência artificial e *data science*.

Não estou dizendo que com essa implementação de **threads** vamos poder jogar todos os nossos projetos fora e já sair implementando todas essas coisas, porém como um entusiasta de Node.js fico feliz em ver que a comunidade está progredindo tentando resolver esse tipo de problema.

## Por onde começar?
