---
title: Web.br 2014 – Throttle e Debounce
author: Diego Eis
type: post
date: 2014-09-25
excerpt: Anotações da palestra sobre Throttle e Debounce feito pelo Almir Filho no Web.br 2014.
url: /web-br-2014-throttle-e-debounce/
categories:
  - Eventos e Workshops
tags:
  - anotacoes
  - webbr2014

---
O [Almir Filho][1] falou um pouco sobre dois métodos de JS que nos permite controlar o fluxo de eventos disparados pelos usuários.

  * Throttle e Debounce nos defende com a frequencia de eventos que os usuários ativam no seu site/sistema como eventos de click, resize, scroll, mouseover, etc…
  * Por exemplo, quando o cara clica várias vezes em um botão que ativa algo em AJAX. Uma submissão de form ou uma compra.
  * Você não pode prever que o usuário clique apenas uma vez no botão. Ele sempre vai clicar várias vezes, por motivos diversos.
  * Como algiém que é novo na web, que acha que tem que clicar duas vezes na internet para ativar alguma coisa.
  * No momento do resize da janela, por exemplo, o quando redimensionamos a janela, esse evento é disparado milhares de vezes.
  * Hoje todos os browsers tem ferramentas para vermos as taxas de custo de rendering e painting
  * Como você controla a frequência de eventos disparados pelos usuários?
  * Throttle veio da engenharia mecânica. Ela é uma válvula que controla o fluxo de combustivel no motor.
  * Podemos usar a mesma ideia do Throttle para controlar o fluxo de eventos disparados pelo usuários. Controlando a execução.
  * Por exemplo, a quantidade de frequência que o evento de scroll é disparado.
  * O debounce cancela os eventos anteriores e executa apenas o último.
  * Um caso comum: quando o fulano clica ou aperta uma tecla vezes seguidas.
  * Caso de uso: auto complete. Quando você faz um auto complete com requisições ajax. O usuário digita tudo de uma vez.
  * Você não pode executar o auto complete a partir do momento que o usuário digita cada tecla.
  * Leia sobre Throttle e Debounce aqui! http://loopinfinito.com.br/2013/09/24/throttle-e-debounce-patterns-em-javascript/

 [1]: http://twitter.com/almirfilho