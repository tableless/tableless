---
title: 'JavaScript: entendendo o this'
author: Davi Ferreira
type: post
date: 2013-07-25
excerpt: 'Conheça mais sobre a palavra reservada this e entenda  como funciona o escopo de um objeto JavaScript.'
url: /javascript-entendendo-o-this/
dsq_thread_id: 1527272460
categories:
  - JavaScript
tags:
  - 2013
  - ecmascript
  - JavaScript

---
O operador **this** é um dos maiores responsáveis por erros e pegadinhas em um código JavaScript. Entender o seu mecanismo de funcionamento e criação é um grande passo para tirar maior proveito da linguagem. 

## Contexto de execução

Toda função JavaScript, ao ser executada, gera uma associação do objeto criado pelo interpretador através da palavra reservada **this**. A especificação da ECMAScript chama isso de **ThisBinding**, um evento que acontece toda vez que um código JavaScript é executado e um novo contexto de execução é estabelecido. O valor do **this** é constante e ele existe enquanto este contexto de execução existir. 

No browser, o **this** &#8220;padrão&#8221; referencia o objeto global **window**. Toda função declarada no escopo global também vai possuir o objeto **window** como valor do **this** (no <a href="http://loopinfinito.com.br/2013/07/16/javascript-strict-mode/" title="http://loopinfinito.com.br/2013/07/16/javascript-strict-mode/" target="_blank">strict mode</a> vai ser **undefined**). 

<pre class="lang-javascript">function myFunc () {
     console.log(this);   
}

var myFunc2 = function () {
     console.log(this);   
}

myFunc(); // Window (...)
myFunc2();  // Window (...)</pre>

## Objetos

Quando uma função representa um método de um objeto, o valor do **this** passa a ser o objeto referenciado. Por exemplo: 

<pre class="lang-javascript">var myObj = {
    init: function () {
        console.log(this);   
    }
};

myObj.init(); // Object {init: function}</pre>

O mesmo acontece quando um objeto é criado utilizando uma <a href="http://tableless.com.br/javascript-objetos-literais-vs-funcoes-construtoras/" title="http://tableless.com.br/javascript-objetos-literais-vs-funcoes-construtoras/" target="_blank">função construtora</a>, só que nesse caso o **this** representa o objeto instanciado. 

<pre>function MyObj () {
    console.log(this);   
}

var obj = new MyObj(); // MyObj {}</pre>

## Callbacks & Eventos

Um dos erros mais comuns acontece quando utilizamos a palavra reservada **this** dentro de um _callback_ e confundimos seu valor. O **this** dentro do _callback_ vai guardar o valor do objeto pai da função _callback_ e não da função que recebe o _callback_.

<pre class="lang-javascript">var myObj = {
    init: function (callback) {
        callback(); 
    }
};

myObj.init(function () {
    console.log(this); // Window (...)  
});</pre>

Para esses casos especiais, podemos definir o valor do **this** utilizando os métodos **call** e **apply** (falo mais sobre eles logo, logo).

Outro ponto que merece atenção é o uso do **this** na hora de anexar eventos a um elemento. Nesse caso, o valor da palavra reservada representa o elemento e não a função. 

<pre class="lang-javascript">var myObj = {
    init: function () {
        this.link = document.querySelector('a');
        this.link.onclick = function (e) {
            console.log(this);   
        };
    }
};

myObj.init();
// clique no link: &lt;a href="#"&gt;link&lt;/a&gt;</pre>

Aqui a solução é armazenar o estado do objeto em uma variável, normalmente chamada de **that** ou **self** e utilizá-la na função do evento.

<pre class="lang-javascript">var myObj = {
    init: function () {
        var that = this;
        this.link = document.querySelector('a');
        this.link.onclick = function (e) {
            console.log(that);   
        };
    }
};

myObj.init();
// clique no link: Object {init: function, link: a}</pre>

## call & apply

Os métodos **call** e **apply** permitem que seja definido um valor para o **this** de uma função. Vejamos o nosso exemplo de _callback_, agora utilizando uma chamada com o método **call**:

<pre class="lang-javascript">var myObj = {
    init: function (callback) {
        callback.call(this); 
    }
};

myObj.init(function () {
    console.log(this); // Object {init: function}
});</pre>

Notem que o valor retornado pelo log do console agora foi o próprio objeto ao invés do objeto global **window**. Isto porque executamos o _callback_ através do método **call**, definindo o valor do **this** no contexto de execução como sendo o **this** do objeto.

Sobre os métodos **call** e **apply**, a principal diferença entre eles é que um permite a passagem de argumentos utilizando um _array_ enquanto o outro aceita os argumentos como _strings_:

<pre class="lang-javascript">fun.apply(thisArg[, argsArray])

fun.call(thisArg[, arg1[, arg2[, ...]]])</pre>

## Referências

  * <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/this" target="_blank">MDN &#8211; this</a>
  * <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/apply" target="_blank">MDN &#8211; apply</a>
  * <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/call" target="_blank">MDN &#8211; call</a>
  * <a href="http://www.digital-web.com/articles/scope_in_javascript/" target="_blank">Scope in JavaScript</a>