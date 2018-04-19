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

# Introdução

Cada vez mais como desenvolvedores precisamos nos preocupar com a performance das nossas APIs, não importa o quão bom o nosso front-end foi arquiteturado e desenvolvido, se nossas APIs demorarem para responder isso irá se refletir para o usuário final.

## O que são testes de stress?

Testes de stress (ou _load tests_ como o termo é conhecido em inglês) são testes de performance que visam testar o nosso software sobre condições extremas de uso em um curto período de tempo.

Esse tipo de teste é uma importante forma de mensurar, medir e identificar o quanto a nossa aplicação consegue responder diante de condições extremas. Além disso, esse tipo de teste pode nos ajudar a escolher determinada tecnologia ou linguagem de programação na hora do desenvolvimento das nossas APIs.

# Realizando testes de stress

Existem diversas formas de realizarmos testes de stress nas nossas aplicações, muitas delas necessitam que ambientes inteiros sejam montados para isolar nossa aplicação de quaisqueres fatores externos.

Eu concordo que a maneira mais correta e eficaz de realizar esse tipo de teste é realmente executá-lo em um ambiente totalmente separado e exclusivo para que fatores externos não impactem o teste. Porém, muitas vezes como desenvolvedores precisamos de uma maneira rápida, simples e eficaz de executarmos esse tipo de teste. Além disso, muitas vezes estamos na fase inicial da arquitetura de uma nova API e precisamos coletar dados iniciais para decidir com qual linguagem específica ou caminho seguir.

## Instalando o wrk

O **wrk** é uma ferramenta opensource que está disponível no [GitHub](https://github.com/wg/wrk) e que possibilita a execução completa de testes de stress na nossa máquina local.

Você pode instalar o wrk em todos os sistemas operacionais, e todas elas podem ser encontradas no [wiki do projeto](https://github.com/wg/wrk/wiki). Como estou utilizando o sistema OS X, vou realizar a instalação através do **brew**.

```
$ brew install wrk
```

Após isso teremos a ferramenta **wrk** à nossa disposição.

```
$ where wrk
/usr/local/bin/wrk
```

# Montando nossa aplicação

Como o objetivo desse artigo não é entrar no desenvolvimento em si das aplicações, vou apenas explicar bem brevemente o que vou fazer.

Vou realizar o teste de stress em duas APIs muito simples, uma delas será desenvolvida em **Node.js** e a outra em **Go**, o objetivo aqui não é comparar qual das duas linguagens é melhor, mas sim mostrar como executar os testes de stress. Ambas as APIs irão realizar uma tarefa bem simples, que será executar a sequência de Fibonacci.

## Aplicação Node

```javascript

```

## Aplicação Go

```go

````
