---
title: Web.br 2014 – Internacionalização na Booking
author: Diego Eis
type: post
date: 2014-09-26
excerpt: Anotações da palestra sobre internacionalização da Booking na Web.br 2014.
url: /web-br-2014-internacionalizacao-na-booking/
categories:
  - Eventos e Workshops
tags:
  - anotacoes
  - booking
  - eventos
  - internacionalizacao

---
A palestra do [Shiota][1] nos trouxe uma realidade difícil de encontrar em qualquer site aqui no Brasil. O trabalho de internacionalização da Booking é no mínimo fantástico para qualquer um que nunca trabalhou em um ambiente com tantos idiomas e variáveis. 

Abaixo seguem as anotações da palestra:

  * Por volta de 75.4% da população mundial, não falam inglês
  * Algumas vezes você precisa mostrar os preços na moeda local.
  * As vezes você precisa entender a cultura local para vender melhor naquele país.
  * Quando você faz um site para o mundo todo, qualquer evento mundial, pode afetar suas vendas.
  * Quando fazemos um ecommerce no brasil, o preço está em real, português e etc.
  * A joelhada no Neymar afetou as visitações da Booking. O.o
  * O site da Booking está presente em 207 países, tem 135 escritórios pelo mundo, fala 42 idiomas, com 54 moedas.
  * Existem alguns atributos do HTML que te ajudam a criar um site que dá suporte a vários idiomas.
  * Por exemplo o atributo **dir**.
  * No CSS tem a propriedade direciton:
  * <div lang=&#8221;pt-br&#8221; xml:lang=&#8221;pt-br&#8221;></div>
  * html {direction: rtl;}
  * O atributo lang também é muito usado.
  * Você também consegue colocar uma classe no body para facilitar o suporte para browsers antigos.
  * Você já acessou o site em árabe? Você já viu as posições de colunas, imagens, textos e etc? Tenha a curiosidade: http://www.booking.com/index.ar.html?sid=b5a9190f11814df8a0a64fcc61b35862;dcid=4
  * Entenda as diferentes soluções de CSS para implementar websites multi-idiomas. Existem vários impactos nas posições dos elementos. #webb2014
  * Prefira usar inline-block em vez de float.
  * Use também display table/table-cell… é coisa linda. É difícil falar isso, mas ele ajuda muito.
  * Flexbox é o nosso próximo sonho. Já já ele aparece. Assim que os IEs antigos morrerem.
  * Uma palavra pequena no seu idioma, pode ser uma palavra enorme em outro idioma.
  * Nunca use texto direto no HTML. Textos sempre passam pela equipe de copywriting.
  * Há um fluxo pré definido que envolve uma equipe de tradutores e coywriters para criar textos para websites multi-idioma.
  * UTF-8 All Things

 [1]: http://twitter.com/shiota/