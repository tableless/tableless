---
title: Provent – Promises e Eventos… combinados.
author: Mauricio Soares
type: post
date: 2015-10-07
url: /provent-promises-e-eventos-combinados/
categories:
  - JavaScript
tags:
  - eventos
  - JavaScript
  - promises

---
Hoje, quando não estamos usando jQuery para lidar com eventos no DOM, nós presenciamos muito este trecho de código:

<pre class="lang-javascript">document.querySelector('a').addEventListener('click', function() {
// amazing stuff
});
</pre>

Embora funcione muito bem, nos trás alguns limites&#8230;

Dentro do parâmetro de callback, é onde você define toda a sua lógica&#8230; Não tem uma maneira simples de adicionar mais callbacks dentro daquele evento de maneira dinâmica, sem que você salve algum tipo de estado dentro daquele callback&#8230; por exemplo:

<pre class="lang-javascript">document.querySelector('a').addEventListener('click', function() {
  if(condition) {
    doSomething();
  } else {
    doSomethingElse();
  }

  // code
});
</pre>

E se você usar o mesmo evento deste botão em algum módulo que está em outro arquivo? Provavelmente outro evento será adicionado a aquele mesmo botão.

Isso não parece ser muito prático nem escalável, e foi com esse problema que eu decidi criar um wrapper para lidar com eventos no DOM chamado _Provent_.

_Provent_ lida com eventos no DOM, mas com uma sintaxe parecida com a de promises, e com a mesma flexibilidade de encadear callbacks e mover a promise para qualquer lugar do seu código.

Então vamos ver como ficaria o primeiro exemplo de código, usando _Provent_:

<pre class="lang-javascript">var linkClick = Provent(document.querySelector('a'), 'click');
</pre>

Até ai tudo bem, um evento foi adicionado ao elemento correspondente a querySelector, mas nenhum callback é chamado, podemos fazer isso usando o famoso _then_.

<pre class="lang-javascript">linkClick.then(function(event) {
  console.log(this);
  console.log(event);
});
</pre>

Os valores dentro desse callback são os mesmos que o callback default de um _addEventListener_, o primeiro argumento aponta para o evento, e o _this_ aponta para o elemento que foi clicado.

Até ai é a mesma coisa que usar addEventListener, mas temos algumas flexibilidades a mais:

<pre class="lang-javascript">linkClick.then(function(event) {
  // some code
});

linkClick.then(function(event) {
  // more code here
});
</pre>

Adicionamos mais um callback no mesmo evento de _click_, sem precisar adicionar mais um evento no elemento, legal né?!

Podemos encadear varios _then_, e passar o retorno de cada callback para o próximo da fila, assim:

<pre class="lang-javascript">linkClick.then(function(param) {
  console.log(param); // event
  return true
}).then(function(param) {
  console.log(param); // true
  return {};
}).then(function(param) {
  console.log(param); // {}
});
</pre>

E você também consegue cancelar esses callbacks a qualquer momento usando o método _reject_:

<pre class="lang-javascript">linkClick.then(function(param) {
  console.log(param); // event
  return true
});

linkClick.reject();
</pre>

Executando o _reject_ sem passar nenhum parâmetro, você cancela todos os callbacks que foram adicionados aos _then_, e também remove o eventListener do botão, prevenindo assim qualquer forma de memory leak indesejado.

O _reject_ também pode ser usado passando um ID, no caso de você definir um callback do _then_ usando o mesmo ID, da seguinte maneira:

<pre class="lang-javascript">linkClick.then(function(param) {
  // code
}).then('123', function(param) { // essa linha mudou
  // code
}).then(function(param) {
  // code
});

linkClick.reject('123');
</pre>

Nesse ultimo exemplo, todos os callbacks menos o que contem o id _123_ vai ser executado, e o evento no elemento também não será removido.

Resumindo.

Provent é uma lib que foi criada para facilitar a manipulação de eventos no DOM, diminuindo a complexidade de adicionar e remover callbacks a qualquer momento.

Você pode instalar o _Provent_ usando _npm _ou _bower_:

<pre>npm install provent
bower install provent
</pre>

A documentação está no repositório do Github: <http://github.com/mauriciosoares/provent>

Deixem seu feedback e sugestões.