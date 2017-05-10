---
title: Elevação ou JavaScript hoisting
author: Jonatan Santos
type: post
date: 2014-06-04
excerpt: |
  Elevação é nada mais, nada menos do que trazer para o início do escopo a declaração de variáveis e funções.
  
  Ta, mas como funciona?
  
  Calma, vamos aos poucos. De primeira vista pode parecer extremamente complicado mais depois de saber o que está acontecendo, você vai dizer "poxa era só isso!".
url: /elevacao-ou-javascript-hoisting/
dsq_thread_id: 2715165926
categories:
  - Código
  - JavaScript
tags:
  - aprenda
  - como funciona
  - cotidiano
  - declaração
  - declarações
  - Elevação
  - Elevação em Javascript
  - escopo
  - funcoes
  - hoisting
  - inicialização
  - JavaScript
  - Javascript hoisting
  - Jonatan Santos
  - joridos
  - tableless
  - variaveis
  - web standards

---
## Um pouco de Teoria antes da diversão.

Muitas vezes, um simples princípio não compreendido, pode confundir novatos ou especialistas em JavaScript. Neste artigo, vamos tentar entender melhor um problema comum, que é mais simples do que parece.

## Declarações na frente

Antigamente em linguagens como C, se usavam funções ou procedimentos para dividir um programa, mas havia um problema: as declarações deveriam ficar sempre na frente.

Suponha que você queira usar uma função que junta palavras:

<pre class="lang-javascript">juntarPalavras('Arco', 'íris');</pre>

Mas temos um problema aqui, não? Essa função não foi definida antes de ser chamada!
  
O programa retornará um erro, pois **juntarPalavras()** não foi criada, ou acha que a linguagem deve permitir que você use funções que são definidas no final do código?

Declarar funções no início do programa resolveu o problema por um tempo, pois todas as funções e variáveis eram declaradas antes de serem usadas, sendo assim não se tinha erros de referência.

Com o tempo os programadores pensaram: &#8220;Mas por que cargas d&#8217;água não fazemos isso mais amigável e fácil de ler?&#8221;, &#8220;por que ler o código de baixo para cima e, não de cima para baixo?&#8221;. Agora podemos colocar as definições em qualquer lugar do código e usá-los, mesmo antes de realmente serem definidos, que maravilha não?

O que acontece agora é que os compiladores ou até mesmo linguagens runtime leem todo o programa para saber que funções e variáveis você declarou no código. Após isso, a execução real acontece e ele já sabe onde está cada coisa. JavaScript faz exatamente isso, o que chamamos de Hoisting.

## Hora da diversão

Vamos começar com algo leve, para ir aquecendo os neurônios, veja o seguinte código:

<pre class="lang-javascript">nome = 'Jonatan';
console.log(nome);
// Jonatan
</pre>

Até aqui nada de novo, apenas iniciamos a variável nome com o valor jonatan e mostramos na tela;

Certo, e que tal tentarmos isso:

<pre class="lang-javascript">var nome = meunome;
console.log(nome);
// ReferenceError: meunome is not defined
</pre>

Recebemos um erro bem obvio não acha? Como vamos definir o **nome** com o valor de **meunome** se essa variável nem existe ainda?

Agora, deste jeito:

<pre class="lang-javascript">var nome = meunome;
console.log(nome);
var meunome;
// undefined
</pre>

Opa! “undefined”, sacam a jogada?

Isso acontece porque o JavaScript não obriga você a declarar variáveis, ​​permite que você defina as funções em qualquer lugar que você queira, o que lhe permite usar uma função antes de sua definição. O nome hoisting, elevação ou até mesmo içamento, é só um termo especificado, pois ele arranca as declarações até o topo do seu escopo.

Beleza, agora qual a diferença entre declaração e inicialização? Simples:

Aqui apenas declaramos a variável **meunome**.

<pre class="lang-javascript">var meunome;
//undefined
</pre>

Já nesta parte iniciamos seu conteúdo como **Jonatan**.

<pre class="lang-javascript">meunome = 'Jonatan';
//Jonatan
</pre>

Este é o mesmo procedimento feito com as funções:

<pre class="lang-javascript">console.log(multiplicaNumero(10,10));
var multiplicaNumero = function(a,b) {
  return a*b;
}
//TypeError: undefined is not a function
</pre>

Viram? Ele elevou a declaração var multiplicaNumero, mas como chamamos antes de ele ser iniciado recebemos um erro.

Se mudarmos para:

<pre class="lang-javascript">console.log(multiplicaNumero(10,10));
multiplicaNumero = function(a,b) {
  return a*b;
}
//ReferenceError: multiplicaNumero is not defined
</pre>

Recebemos o erro nos dizendo que **multiplicaNumero** não foi declarado.

Alteramos novamente:

<pre class="lang-javascript">console.log(multiplicaNumero(10,10));
function multiplicaNumero (a,b) {
  return a*b;
}
// 100
</pre>

E agora o código executou sem erro porque toda declaração de função não anônima é elevada para o topo do escopo.

Fácil não é? Com isso aprendemos que é uma boa prática declarar e/ou iniciar variáveis e funções no início do escopo:

<pre class="lang-javascript">var a, foo = 'bar';
var bar = function(){
  var foo = 'foo';
  console.log('local: '+foo);
};
bar();
console.log('global: '+foo);
//local: foo
//global: bar 
</pre>

Boas práticas nos levam a caminhos melhores.