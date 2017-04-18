---
title: Introdução ao Ionic Framework
author: grillorafael
type: post
date: 2015-02-26
excerpt: Ionic é um framework para desenvolvimento de aplicações para dispositivos móveis que visa o desenvolvimento de apps híbridas e de rápido e fácil desenvolvimento. Este artigo irá dar uma breve introdução à ferramenta e como dar o primeiro passo com ela.
url: /introducao-ao-ionic-framework/
categories:
  - AngularJS
  - Mobile
tags:
  - android
  - app
  - hibrido
  - ionic
  - ios
  - iphone
  - mobile

---
## O que é o Ionic?

[Ionic][1] é um framework criado no final de 2013 que visa a criação de aplicações híbridas para dispositivos móveis. Hoje o Ionic encontra-se na versão 1.0.0-beta.14 que segundo a equipe por trás do desenvolvimento, será o último release beta.

Ele nada mais é do que uma pilha de componentes e outros frameworks. Estes componentes são:

  * [Cordova][2]: Integração com recursos nativos dos dispositivos
  * [AngularJS][3]: Criação da parte Web da App
  * Ionic Module e o Ionic CLI: Ferramentas e Componentes disponibilizados pelo framework

## Pré-requisitos

Para utilizar o Ionic e desenvolvedor aplicações móveis com o Cordova é necessário ter instalado as seguintes dependências:

  1. NodeJS
  2. NPM

Vou pular a parte em que diz como instalar o NodeJS e o NPM pois são coisas simples de se encontrar na internet.

## Objetivo do artigo

O objetivo deste artigo é dar uma breve introdução do que é o Ionic e o que ele usa como tecnologias.

## Como começar

Uma vez com NodeJS e o NPM instalados, é necessário instalar 2 módulos globais.

<pre class="lang-bash">npm install -g ionic cordova</pre>

Uma vez com esses dois módulos instalados, usaremos o gerador do Ionic CLI para criar um novo projeto.

<pre class="lang-bash">ionic start appName tabs</pre>

A sintaxe para a criação de uma nova aplicação é _ionic start NOME\_DO\_APP TIPO\_DO\_GENERATOR_. Existem hoje 3 tipos de projeto base que são _tabs_, _blank_ e _sidemenu_.

Cada gerador irá iniciar seu projeto de uma forma diferente porém todos seguem a mesma estrutura de pastas exibida abaixo.


![Ionic Folders](http://tableless.com.br/uploads/2015/02/Screen-Shot-2015-02-18-at-5.33.43-PM.png) 

Uma vez com o projeto criado, podemos roda-lo com o comando _ionic serve_.

Como podemos ver pela imagem, o ionic utiliza o Gulp como ferramenta de automatização de tarefas mas não se preocupe que ele tem objetivos muito simples como compilar o SCSS, CoffeeScript e rodar um servidor para visualização do projeto. **O uso do SCSS e do CoffeeScript é opcional.**

O desenvolvimento da aplicação a partir daí é bastante _straightforward_. Em nada difere de desenvolver um sistema Web tradicional.

## E se eu quiser utilizar recursos nativos do dispositivo?

Caso seja necessário utilizar recursos nativos do celular como Câmera, Push Notification, Leitor de Código de Barra entre outros, você pode utilizar todos os recursos do Cordova que estão disponíveis e além disso utilizar um outro módulo do AngularJS que a equipe do Ionic criou para facilitar o uso de plugins que é o [ngCordova][5].

## Conclusão

A grande vantagem do Ionic é que seu desenvolvimento foi pensado em utilizar os recursos mais novos do CSS, HTML e JavaScript com o objetivo de prover para o desenvolvedor uma gama de componentes pré-prontos de alta qualidade e desempenho.

A equipe por trás da ferramenta está trabalhando a todo vapor lançando correções e melhorias continuamente e ouvindo bastante os desenvolvedor que a estão utilizando.

É também um ótimo projeto para contribuir pois o desenvolvimento é bastante simples e a comunidade é bastante receptiva.

 [1]: http://ionicframework.com/
 [2]: http://cordova.apache.org/
 [3]: https://angularjs.org/
 [4]: http://tableless.com.br/uploads/2015/02/Screen-Shot-2015-02-18-at-5.33.43-PM.png
 [5]: http://ngcordova.com/