---
title: Gerenciando suas aplicações Node com PM2
authors: Breno Panzolini
type: post
date: 2017-12-28
excerpt: Como gerenciar suas aplicações em NodeJS em produção com o PM2.
categories:
  - NodeJS
  - JavaScript
tag
  - NodeJS
  - JavaScript
image:  https://raw.githubusercontent.com/unitech/pm2/master/pres/pm2.20d3ef.png
---

Nesse post vou explicar o básico para se fazer o deploy de uma aplicação Node.js utilizando o [**PM2**](http://pm2.keymetrics.io/), que é um serviço avançado e altamente utilizado para gerenciar os seus processos Node.

## Por que utilizar o PM2?

O PM2 é uma ferramenta open source completa para o gerenciamento e deploy de aplicações Node.js em ambientes de produção. Dentro os principais recursos disponíveis podemos citar:

- Monitoramento das aplicações
- Integração com containers
- *Hot reload* das aplicações
- Fácil integração com serviços de deploy contínuo
- Logs das aplicações
- Facilidade em escalar as aplicações

Citei apenas alguns recursos, porém o PM2 tem muita coisa legal disponível que pode ser encontrada na [documentação oficial](http://pm2.keymetrics.io/docs/usage/cluster-mode/).
