---
title: Programação funcional em Javascript. Implementando Curry e Compose, com bind e reduce.
authors: Bruno Gonçalves
type: post
date: 2016-06-29
url: /programacao-funcional-em-javascript-implementando-curry-e-compose-com-bind-e-reduce/
categories:
  - Código
  - Geral
  - Javascript
  - Tecnologia e Tendências
tags:
  - Javascript
  - programação funcional

---
Nos últimos tempos só se fala em programação funcional, seus benefícios, funções puras, dados imutáveis, composição de funções, etc.

Atualmente temos diversas libs que auxiliam o javascript na missão de ser funcional, Lodash, Underscore e Ramda são uma delas. Então porque estarei falando do [Pareto.js][1]? Simples como o Princípio de Pareto, a lib criada tem o objetivo de ser leve e resolver 80% dos seus problemas com 20% de código.

Geralmente procuro aprender algo desmitificando a “mágica” por tras da implementação. Foi assim quando comecei a aprender Angular, e agora o mesmo está sendo aplicado à programação funcional. Por isso nesse post vamos avaliar as implementações de Curry e Compose do Pareto.js.

### Curry {.graf--h3.graf-after--p}

<p class="graf-after--h3">
  Curry é a ação de pegar uma função que receba múltiplos argumentos e transforma-la em uma cadeia de funções, em que cada uma receba somente um parâmetro.
</p>

<pre class="lang-javascript">const curry = (fn, ...args) =&gt; {
    if (args.length === fn.length) {
        return fn(...args)
    }
    return curry.bind(this, fn, ...args)
}</pre>

Vamos agora ver o teste dessa função:

<pre class="lang-javascript">describe('curry', () =&gt; {
  it('returns the curried function', () =&gt; {
      const add = (a, b) =&gt; a + b

      expect(FunctionUtils.curry(add, 1, 2)).toBe(3)
      expect(FunctionUtils.curry(add)(1)(2)).toBe(3)
      expect(FunctionUtils.curry(add)(1, 2)).toBe(3)
      expect(FunctionUtils.curry(add, 1)(2)).toBe(3)
  })
})

</pre>

Para começarmos a desmitificar a mágica, temos duas perguntas a serem feitas:

<ul class="postList">
  <li>
    Como a nossa função curry irá armazenar os parâmetros já passados?
  </li>
  <li>
    O que o Function.prototype.bind() tem a ver com isso?
  </li>
</ul>

#### Function.prototype.bind()

Comumente usamos .bind() para passarmos para uma função um contexto para sua execução, porém nos esquecemos de algo importante, como dito na documentação do <a href="https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Function/bind" rel="nofollow">developer.mozilla.org</a>:

> Partial Functions
> 
> The next simplest use of bind() is to make a function with pre-specified initial arguments. These arguments (if any) follow the provided this value and are then inserted at the start of the arguments passed to the target function…

<p class="graf-after--blockquote">
  Resumindo:
</p><p Um dos usos de bind() é construir uma função 

<strong class="markup--strong markup--p-strong">com argumentos iniciais pré-especificados</strong>. Esses argumentos, serão passados após o valor de <strong class="markup--strong markup--p-strong"><em class="markup--em markup--p-em">This</em></strong> e <strong class="markup--strong markup--p-strong">serão inseridos no inicio dos argumentos passados para a função de destino</strong>…</p> <p Difícil de entender? Então vamos a mais um exemplo (em ES5 para que você possa abrir o <em class="markup--em markup--p-em">devtools </em>e já testar).</p> 

<pre class="lang-javascript">"use strict";

function myNumbers(x, y, z){
  console.log(x);
  console.log(y);
  console.log(z);
}

var foo = myNumbers.bind(this, 1);
foo(); 
// 1
// undefined
// undefined

var bar = foo.bind(this, 2);
bar();
// 1
// 2
// undefined

var baz = bar.bind(this, 3);
baz();
//1
//2
//3
</pre>

Reparem que a função <strong class="markup--strong markup--p-strong">myNumbers </strong>espera três parâmetros, a cada vez que chamamos <strong class="markup--strong markup--p-strong">.bind(this, val)</strong>, a função retornada pelo método .bind() <strong class="markup--strong markup--p-strong">automagicamente </strong>guarda o argumento passado.<p E com isso chegamos à implementação do curry no pareto.js, que irá chamar curry.bind(this, fn, ...args), empilhando os parâmetros no 

<em class="markup--em markup--p-em">spread operator &#8230;args </em>até que a quantidade de argumentos seja a mesma que a função espera <strong class="markup--strong markup--p-strong">(args.length === fn.length)</strong>. Caso não tenha entendido o que é <strong class="markup--strong markup--p-strong"><em class="markup--em markup--p-em">…args</em></strong><em class="markup--em markup--p-em">,</em> dê uma lida em <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_operator" rel="nofollow"><em class="markup--em markup--p-em">spread operator</em></a><em class="markup--em markup--p-em">.</em></p> 

### Compose {.graf--h3.graf-after--p}

<p class="graf-after--h3">
  Como o próprio nome sugere, <strong class="markup--strong markup--p-strong"><em class="markup--em markup--p-em">Compose </em></strong>é construir funções mais complexas através de funções mais simples, compondo-as. Vamos à implementação no Pareto.js:
</p>

<pre class="lang-javascript">const compose = (...fns) =&gt; fns.reduce((f, g) =&gt; (...args) =&gt; f(g(...args)))

</pre>

Vamos ao teste dessa função:

<pre class="lang-javascript">describe('compose', () =&gt; {
    it('composes functions', () =&gt; {
        const toUpperCase = x =&gt; x.toUpperCase()
        const exclaim = x =&gt; `${x}!`
        const moreExclaim = x =&gt; `${x}!!`

        expect(FunctionUtils.compose(toUpperCase, exclaim)('test')).toBe('TEST!')
        expect(FunctionUtils.compose(toUpperCase, exclaim, moreExclaim)('test')).toBe('TEST!!!')
    })
})

</pre>

E assim temos uma pergunta:

<ul class="postList">
  <li>
    O que Array.prototype.reduce() está fazendo aí no meio ?
  </li>
</ul>

#### Array.prototype.reduce()

Em geral pensamos no .reduce() como um acumulador, porém somente no sentido de soma de valores e não de <strong class="markup--strong markup--p-strong">composição</strong>. Sabemos que o .reduce() aplica uma função de callback sobre um <strong class="markup--strong markup--p-strong">acumulador</strong>, varrendo <strong class="markup--strong markup--p-strong">todos os elementos do array</strong>. Vamos começar a desconstrução do nosso compose:

<ul class="postList">
  <li>
    Sabemos que ele recebe um array de funções como argumentos, através do spread operator …args;
  </li>
  <li>
    A função de <em class="markup--em markup--li-em">callback </em>do .reduce(), que será executada sobre cada item do nosso array, pode receber até 4 parâmetros, sendo eles: <strong class="markup--strong markup--li-strong"><em class="markup--em markup--li-em">previousValue, currentValue, index, array</em></strong>. Porém aqui só iremos utilizar os dois primeiros (<strong class="markup--strong markup--li-strong"><em class="markup--em markup--li-em">previousValue</em></strong> e <strong class="markup--strong markup--li-strong"><em class="markup--em markup--li-em">currentValue</em></strong>). Lembrando que na primeira chamada à nossa função de callback, <strong class="markup--strong markup--li-strong"><em class="markup--em markup--li-em">previousValue</em> será o valor do primeiro elemento do array e <em class="markup--em markup--li-em">currentValue</em> será o valor do elemento seguinte;</strong>
  </li>
  <li>
    A nossa função de <em class="markup--em markup--li-em">callback</em> irá compor a função passada em <strong class="markup--strong markup--li-strong"><em class="markup--em markup--li-em">previousValue</em></strong> com a que está em <strong class="markup--strong markup--li-strong"><em class="markup--em markup--li-em">currentValue</em></strong>, adicionando na declaração da função que ela poderá receber <strong class="markup--strong markup--li-strong">N</strong> argumentos (…args). Resultando em <strong class="markup--strong markup--li-strong"><em class="markup--em markup--li-em">previousValue(currentValue(…args))</em>.</strong>
  </li>
</ul>

De acordo com o nosso testes, vamos observar os passos de execução em uma tabela:

<img class="alignnone size-full wp-image-53670" src="https://raw.githubusercontent.com/diegoeis/tableless-static-images/master/2016/04/compose-print.png" alt="compose-print" width="737" height="83" />

E com isso temos o resultado da função mais interna (<em class="markup--em markup--p-em">moreExclaim</em>) alimentando as funções mais externas (<em class="markup--em markup--p-em">exclaim</em> e depois <em class="markup--em markup--p-em">toUpperCase</em>).

<

p E é isso pessoal. Espero que tenha ajudado à vocês a entenderem a relação de curry e compose com .bind() e .reduce(). Feedbacks são mais do que bem-vindos e incentivados. Até a proxima.

Fontes:

  * <a href="https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Function/bind" rel="nofollow">https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Function/bind</a>
  * <a href="https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Function/bind" rel="nofollow">https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce</a>
  * <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_operator" rel="nofollow">https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_operator</a>
  * [https://medium.com/@matheusml/entendendo-programa%C3%A7%C3%A3o-funcional-em-javascript-de-uma-vez-c676489be08b#
  
    https://github.com/concretesolutions/pareto.js][2]

 [1]: https://github.com/concretesolutions/pareto.js
 [2]: https://medium.com/@matheusml/entendendo-programa%C3%A7%C3%A3o-funcional-em-javascript-de-uma-vez-c676489be08b#%20https://github.com/concretesolutions/pareto.js