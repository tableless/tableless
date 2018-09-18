---
title: Ouigo - Pinball em WebGL
authors: Diego Eis
type: post
date: 2017-07-31
excerpt: Um pinball rodando direto do seu browser.
categories:
  - webgl
  - Javascript
  - Browser
tags:
  - webgl
  - Javascript
  - Browser
image: https://i.imgur.com/WIGQpbR.png
---

Estava navegando no [AWWWARDS](https://awwwards.com/) hoje e vi um [case muito interessante](https://www.awwwards.com/case-study-merci-michel-rosapark-win-sotm-june-with-ouigo-let-s-play.html) sobre uma agência que resolveu fazer um Pinball, que rodasse no browser. Os desafios que eles queriam alcançar eram:

1. Criar um jogo de pinball, criativo, que rodasse no browser;
2. Ele teria que rodar também nos smartphones mais recentes, ainda baseado no browser e não um app;
3. Como o conceito surgiu de um comercial de TV, eles deveriam criar pinball com essa mesma temática original;
4. Criar uma verso física do pinball;

Eles usaram uma série de bibliotecas para conseguir faze o jogo, segue aí:

* [p2.js](https://github.com/schteppe/p2.js/): 2D physics engine
* [three.js](https://threejs.org/): 3D library
* [glTF](https://github.com/KhronosGroup/glTF/) : runtime asset delivery format for WebGL that optimizes loading and also processing of 3D assets.
* [PreloadJS](https://www.createjs.com/preloadjs/): assets loader
* [GSAP](https://greensock.com/gsap/): animation library
* [mm-packer](https://www.npmjs.com/package/mm-packer/): concatenates files in order to minimize HTTP requests

O negócio funciona *muito* bem no desktop e mobile. Para os puristas e já para evitar a briguinha boba de Nativo vs Web: obviamente a performance não é 100%. Não estamos falando de um SPA que lê uma API, estamos falando de um jogo com render 3D, que usa diretamente a GPU da máquina, simulação de física e colisão, rodando no Browser. E pasme: rodou melho no meu iPhone 6 (o básico mesmo), do que no meu Macbook.

Eu não vou entrar no detalhe do case aqui, mas você pode ler na na íntegra no site do [Awwwards](https://www.awwwards.com/case-study-merci-michel-rosapark-win-sotm-june-with-ouigo-let-s-play.html). Se quiser ver como ficou o jogo, [basta clicar nesse link](https://letsplay.ouigo.com)!
