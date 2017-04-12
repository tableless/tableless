---
title: Iterators ES6
author: Bruno Belarmino
type: post
date: 2015-03-20
excerpt: Uma nova forma de interagir com collections no Javascript
url: /iterators-es6/
categories:
  - JavaScript
tags:
  - ES6
  - JavaScript
  - Novidades

---
A partir de hoje iniciaremos uma série de posts falando sobre as novidades da nova versão do Javascript, conhecida como ES6 (EcmaScript 6). Que esta recheada de novidades e contemplando features muito legais como você verá na série.

Como post de abertura vou falar hoje sobre iterators.

### O que são?

Iterator é um objeto com uma determinada interface. E essa interface consiste de um método chamado _next()_ que retorna um objeto como resultado.

Esse objeto de resultado, tem duas propriedades _value_ referente ao valor corrente e _done_ que é um valor booleano qual é setado para _true_ quando não existem mais valores para serem retornados.

O iterator mantém uma referência à posição correta do próximo valor dentro da coleção de valores. Deste modo, toda vez que o método _next()_ é chamado ele retorna o valor correto. Caso o método _next()_ for chamado após o último valor ser retornado o iterator irá retornar o objeto de resultado com os seguintes valores: _done_ = _true_ e _value_ = _undefined_.

#### Show me the code!

Com esse entendimento vamos ver na prática a implementação de um iterator:

    
    	var criarIterator = function(items){
    		var i = 0;
    
    		return {
    			next: function(){
    
    				var done = (i>= items.length);
    				var value = !done ? items[i++] : undefined;
    
    				return {
    					done: done,
    					value: value
    				};
    			}
    		}
    	};
    
    	var iterator = criarIterator([1, 2, 3]);
    
    	console.log(iterator.next());  // "{ value: 1, done: false}"
    	console.log(iterator.next());  // "{ value: 2, done: false}"
    	console.log(iterator.next());  // "{ value: 3, done: false}"
    	console.log(iterator.next());  // "{ value: undefined, done: true}"
    
    

Simples, neh!?
  
Imagino que se você tenha conhecimentos em Java ou C# já tenha se perguntado, será? E a resposta é sim! Iterator em Javascript funciona de uma maneira bem semelhante ao iterator dessas linguagens.

#### Legal! Mas e onde eu uso isso?

Iterator é uma peça fundamental na nova forma de manipular coleções de dados no ES6. Sendo assim, todos os tipos de coleções (_Arrays_, _Sets_, _Maps_ e até mesmo _Strings_) já vem com essa interface implementada. Liberando novas formas de interação com esses objetos.

Além disso um bom entendimento sobre iterators irá te dar uma base sólida e te ajudar muito no entendimento de outras features do ES6. Assim como _collections_, _for of_ e _generators_ que serão assuntos dos próximos posts da série.

Até a próxima!