---
title: Manipulando o uso de classes com classList API
author: Guilherme Bayer
type: post
date: 2016-04-18
excerpt: Manipule facilmente suas classes com o uso da classList API, uma API pequena e simples, porem de grande utilidade.
url: /manipulando-o-uso-de-classes-com-classlist-api/
categories:
  - JavaScript
tags:
  - JavaScript

---
Uma tarefa muito simples de se fazer com o JQuery, é a troca e manipulação de classes nos elementos HTML. Talvez você não saiba, mas é tão fácil quanto fazer essas manipulações usando JavaScript puro. Para tanto, vamos usar a API classList do JavaScript. Assim como as conhecidas funções `addClass()`, `removeClass()`, `hasClass()` e o `toggleClass()` do nosso conhecido Jquery, possuímos métodos nativos que executam a mesma função.

## Métodos do classList

O `classList` conta com os seguinte métodos:

<pre class="lang-javascript">add('class');
remove('class');
contains('class');
item(index);
toggle('class');
length;
</pre>

`add()`, adiciona uma ou mais classes ao elemento.

<pre class="lang-javascript">var el = document.querySelector('element');
    el.classList.add('classOne', 'classTwo');
    console.log(el.classList); // ["classOne", "classTwo", value: "classOne classTwo"]
</pre>

`remove()`, remove uma ou mais classes do elemento.

<pre class="lang-javascript">el.classList.remove('classOne');
    console.log(el.classList); // [ "classTwo", value: "classTwo"]
</pre>

`contains()`, verifica se possui certa classe no elemento.

<pre class="lang-javascript">if(el.classList.contains('classFour') == true) 
  console.log('Não possui a classe!'); // Não possui a classe!
</pre>

`item()`, retorna a classe que se encontra naquele índice.

<pre class="lang-javascript">el.classList.item(0);
    console.log(el.classList.item(0)); // classTwo
</pre>

`toggle()`, se a classe existir naquele elemento, ele a remove, se não existir ele a adiciona.

<pre class="lang-javascript">el.classList.toggle('classThree')
console.log(el.classList); // ["classTwo", "classThree", value: "classTwo classThree"]

el.classList.toggle('classThree')
console.log(el.classList); // ["classTwo", value: "classTwo"]
</pre>

`length`, retorna a quantidade de classes naquele elemento.

<pre class="lang-javascript">el.classList.length;
console.log(el.classList.length); // 2
</pre>

## Quanto ao suporte

A classList API possui um excelente suporte aos browsers modernos, e apenas o internet explorer com suporte a versão +10, para algo mais detalhado, <http://caniuse.com/#feat=classlist>