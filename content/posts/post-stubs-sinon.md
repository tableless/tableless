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

## O que são Stubs?

Stubs em resumo são funções com um comportamento pré-programável que será fixo e previsível.

Nos nossos testes podemos utilizar stubs principalmente em dois casos:
* Quando queremos evitar a chamada de alguma dependência, por exemplo uma chamada a uma API externa.
* Quando queremos testar determinados caminhos específicos na nossa aplicação, e com isso conseguir testar os diversos cenários, por exemplo retornar *null* na chamada de determinada função.

## O Sinon

O Sinon é um pacote open-source que fornece diversas funcionalidades (como mocks, spies e stubs) que facilitam os nossos testes no JavaScript.

O Sinon por sí só não é um framework de testes, ele deve ser utilizado em conjunto com outra ferramenta para execução de testes, como por exemplo o Mocha ou Ava.

A documentação do Sinon é bem completa com diversos exemplos práticos e pode ser encontrada no [site oficial](http://sinonjs.org/), lá também podemos encontrar o passo a passo para realizar a instalação do pacote no nosso projeto.

