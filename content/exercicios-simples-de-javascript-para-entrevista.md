---
title: Exercícios Simples de JavaScript para Entrevista
author: Wendell Adriel
type: post
date: 2016-01-26
excerpt: Nesse artigo iremos ver alguns exercícios simples e rápidos de JavaScript que podem ser usados para ajudar a você a selecionar candidatos ou para você se dar bem em uma entrevista.
url: /exercicios-simples-de-javascript-para-entrevista/
categories:
  - Artigos
  - JavaScript
  - Traduções
tags:
  - Adriel
  - entrevista
  - JavaScript
  - traducoes
  - Wendell
  - Wendell Adriel

---
Qualquer um pode aprender teoria lendo posts de blogs, mas muitas pessoas nunca a entendem. Então para ter certeza que o(a) candidato(a) realmente entende sobre o tópico que ele(a) está falando, é uma boa ideia testar o seus conhecimentos através de exercícios. Exercícios não devem demorar muito e eles podem mostrar o nível de proficiência do candidato imediatamente.

Estes são alguns exercícios que podem ser aplicados em entrevistas.

## Contexto(call, apply)

Essa é a forma que queremos usar &#8220;someFn&#8221;. O(a) candidato(a) deve implementá-la:

<pre class="lang-javascript">var result = someFun({ someProperty: 'interview' }, function() {
	console.log('This pointing to'. this);
});

console.log('Result is', result);

// Resultado esperado
This pointing to { someProperty: 'interview' }
Result is 1
</pre>

Solução:

<pre class="lang-javascript">var someFn = function(obj, cb) {
	cb.call(obj);
	return 1;
</pre>

### Adicional

Você pode modificar a função para checar se o(a) candidato(a) sabe como usar o &#8220;apply&#8221;.

<pre class="lang-javascript">var result = someFn({ someProperty: 'interview' }, function (param1, param2) {
	console.log('This pointing to', this);
	console.log('Param 1 is', param1);
	console.log('Param 2 is', param2);
}, ['cool', 'interview']);

console.log('Result is', result);

// Resultado esperado
This pointing to { someProperty: 'interview' }
Param 1 is "cool"
Param 2 is "interview"
Result is 1
</pre>

Solução:

<pre class="lang-javascript">var someFn = function (obj, cb, params) {
	cb.apply(obj, params);
	return 1;
}
</pre>

## Prototype e Iteração

Definir um método nativo chamado &#8220;each&#8221; para iterar em um array, com a opção de passar o contexto como segundo argumento.

<pre class="lang-javascript">var arr = [1, 2, 3];
arr.each(function (arrayItem, counter) {
	console.log('index', counter);
	console.log('item', arrayItem);

	arr[counter] = arrayItem + 1;
}, this);
</pre>

Solução:

<pre class="lang-javascript">Array.prototype.each = Array.prototype.each || function (cb, context) {
    for (var i = 0; i &lt; this.length; i++) {
        cb.call(context || this, this[i], i);
    }
};
</pre>

## Escopo

Definir &#8220;someFn&#8221; que irá funcionar da seguinte maneira:

<pre class="lang-javascript">var counter = someFn(1);
console.log('First call', counter(3));
console.log('Second call', counter(1));
console.log('Third call', counter(5));

// Resultado esperado
First call 4
Second call 5
Third call 10
</pre>

Solução:

<pre class="lang-javascript">var someFn = function (start) {
	var private = start;

	return function (increment) {
		private += increment;

		return private;
	}
}
</pre>

Traduzido de: http://goschevski.com/simple-javascript-interview-exercises/