---
title: 'JavaScript: Dicas de bolso – parte 1'
author: Raphael Fabeni
type: post
date: 2015-05-21
excerpt: Dicas rápidas de JavaScript, uma linguagem beeem legal mas cheia de pegadinhas do malandro.
url: /dicas-de-bolso-de-javascript-parte-1/
categories:
  - Código
  - JavaScript
tags:
  - JavaScript
  - Técnicas e Práticas

---
#  JavaScript e suas pegadinhas

JavaScript é uma linguagem bem legal mas cheia de _pegadinhas_. A idéia desse post é documentar alguma dessas pegadinhas, para que possamos evitar dores de cabeça principalmente à galera que ainda não se deparou com alguma delas.

## Guarde o tamanho do array

No JavaScript temos nossos brothers loops `for`, que conseguem iterar em arrays ou também em objetos semelhantes a arrays. Semelhantes? Como assim!? Por exemplo os objetos `arguments` e `HTMLCollection`. Provavelmente você já deve ter se deparado com um loop `for` (já deve ter escrito alguns):

<pre class="lang-js">for(var i = 0; i &lt; arrayFabeni.length; i++) {
    // magic
}
</pre>

De bate pronto, conseguimos perceber algo não tão bacana no código acima. O comprimento (`length`) do array é acessado em toda iteração do loop. Isso não fica tão legal quando por exemplo, o objeto é um `HTMLCollection`. Lembra o que são esses caras? Eles que são retornados quando a gente chama:

  * `getElementsByName()`
  * `getElementsByClassName()`
  * `getElementsByTagName()`

Tá! Legal! Mas eaí né?! A zica mesmo é que toda vez que a gente itera sobre esses caras significa que estamos consultando o nosso _DOM_ ao vivo e a cores, e a \*toda hora\*, o que não é nada bacana.

Com base nisso, uma solução que podemos chegar seria _guardarmos_ o comprimento do array; algo parecido com isso:

<pre class="lang-js">for(var i = 0, max = arrayFabeni.length;  i &lt; max; i++) {
    // magic
}
</pre>

O que fizemos acima foi armazenar o valor da propriedade `length`, evitando assim ter que calculá-la a cada iteração do loop.

## Verifique se a propriedade pertence àquele objeto

Além do nosso amigo do exemplo anterior, no JavaScript temos o loop `for-in` que usamos pra iterar em objetos. Uma coisa bacana de se fazer e que pode evitar que algo que você não queira aconteça, é usar o método `hasOwnProperty()`. Esse método simplesmente vai filtrar apenas as propriedades do objeto em si, excluindo as propriedades herdadas pelo `prototype`.

Um exemplo rápido:

<pre class="lang-js">var burger = {
    queijo: 'cheddar',
    pao: 'integral',
    hamburguer: 'picanha',
    molho: 'barbecue'
};
</pre>

Aí em uma parte obscura, aparece algo que adiciona uma propriedade a todos os objetos.

<pre class="lang-js">if(!Object.prototype.feijao) {
  Object.prototype.feijao = 'preto';
}
</pre>

O que aconteceu acima foi que verificamos se existe a propriedade `feijao` em `Object` e, caso ela não exista definimos ela com o valor `preto`. Aí que está o negócio <del>da coisa</del> do JavaScript, nosso objeto `burger`, já herda a propriedade `feijao` via `prototype`.

Com isso, para evitarmos que `feijao` apareça quando listarmos as propriedades de `burger` (até porque feijão, na minha opinião, não combina muito com hamburguer), fazemos o seguinte:

<pre class="lang-js">for(var i in burger) {
  if(burger.hasOwnProperty(i)) {
     console.log(i + ' =&gt; ' + burger[i]);
  }
}

// Resultará no seguinte:
// queijo =&gt; cheddar
// pao =&gt; integral
// hamburguer =&gt; picanha
// molho =&gt; barbecue
</pre>

Do contrário, caso não fizéssemos essa verificação, teríamos algo assim:

<pre class="lang-js">for(var i in burger) {
    console.log(i + ' =&gt; ' + burger[i]);
}

// Resultará no seguinte:
// queijo =&gt; cheddar
// pao =&gt; integral
// hamburguer =&gt; picanha
// molho =&gt; barbecue
// feijao =&gt; preto
</pre>

* * *

Era isso! Dicas rápidas sobre a linguagem, que para alguns podem ser básicas, mas que muita gente ainda pode não conhecer e, que podem evitar alguns problemas no futuro.

Referências
  
<a href="http://www.amazon.com/Learning-JavaScript-Edition-Shelley-Powers/dp/0596521871" target="_blank">Learning JavaScript</a> | <a href="http://www.amazon.com/JavaScript-Good-Parts-Douglas-Crockford/dp/0596517742" target="_blank">JavaScript: The Good Parts</a> | <a href="http://shop.oreilly.com/product/0636920011460.do" target="_blank">JavaScript: Pocket Reference</a> | <a href="http://shop.oreilly.com/product/9780596806767.do" target="_blank">JavaScript Patterns</a>