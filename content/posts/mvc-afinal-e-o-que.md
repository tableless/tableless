---
title: MVC – Afinal, é o quê ?
author: Allan Ramos
type: post
date: 2015-02-26
excerpt: Explicando o MVC, um padrão de arquitetura para organizar sua aplicação.
url: /mvc-afinal-e-o-que/
categories:
  - Artigos
tags:
  - Architectural Pattern
  - mvc

---
> **Model–view–controller (MVC)** is a software **architectural pattern** for implementing user interfaces. It **divides** a given **software** application into **three** interconnected **parts**, so as to separate **internal** representations of **information** from the ways that **information** is **presented** to or accepted from the user. &#8211; Wikipedia

Leia atentamente:  **architecture pattern**. Reforcei isso pois no início de meus estudos deparei-me com alguns sites dizendo que MVC era um **design pattern**, padrão sobre o design do código.

**MVC** é nada mais que um padrão de arquitetura de software, separando sua aplicação em 3 camadas. A camada de interação do usuário(**view**), a camada de manipulação dos dados(**model**) e a camada de controle(**controller**).

## Model

Sempre que você pensar em manipulação de dados, pense em model. Ele é **responsável** pela **leitura** e **escrita** de **dados,** e também de suas **validações**.

## View

Simples: a camada de interação com o usuário. Ela apenas faz a  **exibição** dos **dados**, sendo ela por meio de um **html** ou **xml**.

## Controller

O responsável por **receber** todas as **requisições** do **usuário**. Seus métodos chamados actions são responsáveis por uma página, controlando qual model usar e qual view será mostrado ao usuário.

[<img class="aligncenter size-full wp-image-47324" src="http://tableless.com.br/uploads/2015/02/laravel-introducao.jpg" alt="laravel-introducao" width="505" height="367" srcset="uploads/2015/02/laravel-introducao.jpg 505w, uploads/2015/02/laravel-introducao-191x139.jpg 191w, uploads/2015/02/laravel-introducao-400x291.jpg 400w" sizes="(max-width: 505px) 100vw, 505px" />][1]

Caso você ainda esteja um pouco confuso, espero que esse diálogo possa te &#8220;dar a luz&#8221;.

## O diálogo das camadas

<p style="padding-left: 30px">
  <strong>View </strong>&#8211; Fala Controller ! O usuário acabou de pedir para acessar o Facebook ! Pega os dados de login dele ai.
</p>

<p style="padding-left: 30px">
  <strong>Controller</strong> &#8211; Blz. Já te mando a resposta. Ai model, meu parceiro, toma esses dados de login e verifica se ele loga.
</p>

<p style="padding-left: 30px">
  <strong>Model</strong> &#8211; Os dados são válidos. Mandando a resposta de login.
</p>

<p style="padding-left: 30px">
  <strong>Controller</strong> &#8211; Blz. View, o usuário informou os dados corretos. Vou mandar pra vc os dados dele e você carrega a página de perfil.
</p>

<p style="padding-left: 30px">
  <strong>View</strong> &#8211; Vlw. Mostrando ao usuário&#8230;
</p>

 [1]: http://tableless.com.br/uploads/2015/02/laravel-introducao.jpg