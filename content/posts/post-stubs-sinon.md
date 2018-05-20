---
title: Fazendo o stub de dependências com Sinon
authors: Breno Panzolini
type: post
date: 2018-05-19
excerpt: Como realizar o stub de suas dependências com o Sinon para simplificar seus testes.
categories:
  - NodeJS
  - JavaScript
tag
  - NodeJS
  - JavaScript
image: https://cdn-images-1.medium.com/max/1600/0*HERF9Ii9f_M3OzQQ.
---

Muitas vezes queremos testar funções que tem dependências externas, como por exemplo uma função que faz o request para uma API.

Nesse post vou mostrar como podemos criar stubs dessas dependências para facilitar os nossos testes e até mesmo conseguir testar todos os tipos de comportamentos dessas dependências.
