---
title: Collections ES6 – parte 1
author: Bruno Belarmino
type: post
date: 2015-05-12
excerpt: Novas estruturas de dados do Javascript
url: /collections-es6-parte-1/
categories:
  - JavaScript
  - Tecnologia e Tendências
tags:
  - collections
  - ES6
  - JavaScript
  - Novidades
  - Set
  - WeakSet

---
Fala Amigos!

Dando continuidade a nossa série sobre as novidades do Javascript, vamos falar hoje sobre collections.

#### Sets e Maps

Historicamente a única collection que vinha por padrão no Javascript era o _Array_. Mas a partir do ES6 temos novos tipos como: _Set_, _WeakSet_, _Map_ e _WeakMap_.

#### Set

Para quem tem conhecimento em linguagens de programação como C#, Java, Ruby e Python esta collection não é uma novidade, mas para quem tem conhecimento somente em Javascript, sim. Sendo assim, segue a definição:

_Set_ é um tipo de collection que permite a inserção de qualquer tipo de valor (Ex: objeto, function, número, string, etc) e não permite valores duplicados. Outra particularidade é que utilizando _Set_ não é possível acessar um valor diretamente como é feito com _Array_, normalmente você valida para ver se o valor está presente ou itera sobre os valores.

Um exemplo de uso para _Sets_ é uma lista de pedidos onde cada pedido do usuário deve ser único e ocasionalmente é necessário verificar se aquele pedido já esta incluso.

Simples!? Vamos ver na prática a utilização do _Set_:

    
    		//inicialização de um Set
    		var set = new Set(); //cria um novo Set vazio
    		var set2 = new Set([1, 2, 3]); //cria um novo Set a partir de um Array
    
    		set.add(1); //adiciona um valor
    
    		//número de valores no set
    		set.size; // 1
    		set2.size; // 3
    
    		//verifica se o valor existe dentro do Set
    		set.has(1); // true
    
    		set.add(1); //adiciona um valor duplicado e nada acontece
    
    		set.size; // 1
    
    		set.delete(1); //remove um determinado valor do Set
    
    		set.has(1); // false
    		set.size; // 0
    
    		//itera sobre os valores do Set
    		for (let valor of set2) {
    		  console.log(valor);
    		}
    
    		//itera sobre os valores do Set
    		set2.forEach(function(valor) {
    		  console.log(valor); 
    		});
    
    		//output das iterações: 
    		// 1
    		// 2
    		// 3
    
    		set2.clear(); //remove todos os valores do Set
    		set2.size; // 0
    	
    

#### WeakSet

É um _Set_ de objetos que não previne que seus elementos/valores sejam coletados pelo garbage collector do Javascript. Além disso a sua api também é reduzida. Deste modo, não é permitido iterar sobre os valores do _Set_ e/ou limpar os mesmos usando o método _clear_.

Na prática, ao utilizar um objeto como valor do seu _WeakSet_ e o mesmo não estiver sendo usado em mais nenhum lugar na sua aplicação, o garbage collector poderá limpar a sua referência e com isso magicamente o valor deixaria de existir.

A api do _WeakSet_ é composta de apenas 3 métodos quais funcionam da mesma forma que o _Set_:

  * add(valor)
  * has(valor)
  * delete(valor)

No próximo post falaremos de _Map_ e _WeakMap._

Até a próxima!