---
title: Gerenciando suas aplicações Node com PM2
authors: Breno Panzolini
type: post
date: 2017-12-28
excerpt: Como gerenciar suas aplicações em NodeJS em produção com o PM2.
categories:
  - NodeJS
  - JavaScript
tags:
  - NodeJS
  - JavaScript
image:  https://raw.githubusercontent.com/unitech/pm2/master/pres/pm2.20d3ef.png
---

Em alguns ambientes corporativos não temos nenhuma solução de containers ou nenhuma solução PaaS *(platform as a service)*, como o [Heroku](https://www.heroku.com/) por exemplo, para o deploy de nossas aplicações Node.

Muitas vezes precisamos fazer o dpeloy de nossas aplicações em uma máquina na nuvem ou em um servidor interno no próprio ambiente da sua empresa. Nesse post vou explicar o básico sobre o **PM2**, que é um serviço avançado e altamente utilizado para gerenciar os seus processos Node.js.
