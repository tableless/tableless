---
title: Realizando testes de stress em sua API de maneira simples
authors: Breno Panzolini
type: post
date: 2018-04-19
excerpt: Como realizar testes de stress em suas aplicações na sua máquina local com o wrk.
categories:
  - Tooling
  - Back-end
tags:
  - Tooling
image:  https://fredericoporto.com.br/wp-content/uploads/2017/07/post-alta-performance-head-banner.jpg
---

Nesse post vou mostrar como podemos executar de maneira muito simples e fácil testes de stress nas nossas APIs utilizando o nosso próprio computador.

## Introdução

Cada vez mais como desenvolvedores precisamos nos preocupar com a performance das nossas APIs, não importa o quão bom o nosso front-end foi arquiteturado e desenvolvido, se nossas APIs demorarem para responder isso irá se refletir para o usuário final.

### O que são testes de stress?

Testes de stress (ou _load tests_ como o termo é conhecido em inglês) são testes de performance que visam testar o nosso software sobre condições extremas de uso em um curto período de tempo.

Esse tipo de teste é uma importante forma de mensurar, medir e identificar o quanto a nossa aplicação consegue responder diante de condições extremas. Além disso, esse tipo de teste pode nos ajudar a escolher determinada tecnologia ou linguagem de programação na hora do desenvolvimento das nossas APIs.
