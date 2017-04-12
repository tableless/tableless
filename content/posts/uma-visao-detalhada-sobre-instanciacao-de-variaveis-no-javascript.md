---
title: Uma visão detalhada sobre instanciação de variaveis no JavaScript
author: Alex Miranda
type: post
date: 2015-12-09
excerpt: 'Sabe quando a variável acaba ganhando um valor que você não esperava ? Pois bem, o JavaScript tem algumas formas de tratar variáveis e é sobre isso que vamos tratar aqui neste artigo. Escrevi este texto para o curso beMEAN - Instagram criado pelo Jean Suissa, fundador da Webschool. Gostaria de compartilhar com a comunidade, especialmente com os iniciantes. Vamos la! ;)'
url: /uma-visao-detalhada-sobre-instanciacao-de-variaveis-no-javascript/
categories:
  - JavaScript
  - Técnicas e Práticas
tags:
  - JavaScript
  - js

---
## Hoisting

Antes de falarmos sobre hoisting é importante lembrar como funciona escopo em JavaScript. Escopo nada mais é do que um contexto criado para os valores e expressões terem sua validade. Em JavaScript o escopo é criado com a declaração de funções. Vamos a um exemplo:

<pre class="lang-javascript">// Escopo global
var num = 0; 

// Escopo criado pela função
function imprimir(){
	var num = 1;
	console.log(num);
}

// Executar a função e o que tem em seu escopo
imprimir(); // 1

// Imprimindo a variável do escopo global
console.log(num); // 0
</pre>

No exemplo acima temos o seguinte: A variável &#8220;num&#8221; foi declarada com o mesmo nome em 2 lugares diferentes: No escopo global e no escopo criado pela função imprimir. Por elas estarem em escopos diferentes, não tem problema terem o mesmo nome.

Mas cuidado! As variáveis declaradas sem a palavra reservada &#8220;var&#8221; passam a ser parte do escopo global. Olha só:

<pre class="lang-javascript">// Escopo global
var num = 0;

// Escopo criado para a função imprimir
function imprimir(){
	num = 1; 
	console.log(num);
}

// Executar a função e o que tem no escopo
imprimir(); // 1

// Acessando a variável do escopo global
console.log(num); // 1
</pre>

Uma das boas praticas em JavaScript é sempre declarar as variáveis com a palavra reservada &#8216;var&#8217; para conter o valor em seu escopo local e manter o escopo global limpo. 

Legal, agora que já relembramos o escopo em JavaScript vamos entender o que é o hoisting.

_Hoisting pode ser traduzido como levantar, erguer ou içar._

Esse comportamento na linguagem JavaScript vale para funções e variáveis. Vamos falar primeiro sobre o hoisting de variáveis. Quando declaramos uma variável em JavaScript a mesma é erguida, ou hoisted, para o topo do escopo, no caso de variaveis somente a sua declaração é levada para o topo do escopo mas sua inicialização não. Por exemplo:

<pre class="lang-javascript">function nome(){
	var nome = "Alex";
	console.log(nome + " " + sobreNome);
	var sobreNome = "Miranda";
}
nome(); // Alex undefined
</pre>

O valor da variável sobreNome é undefined, ou seja, ela esta sendo considerada na função mas o seu valor não.
  
E é assim que funciona o hoisting de variável. 😉

No caso de funções o hoisting ocorre de um jeito diferente. Tanto a sua declaração quanto o seu escopo é içado
  
para o topo. Olha que interessante:

<pre class="lang-javascript">nome(); // Alex
function nome(){
	var nome = "Alex";
	console.log(nome);
}
</pre>

Sim, a função foi executada antes da sua declaração por conta do hoisting. Porém, aqui vale um lembrete, uma das formas de declaramos funções em JavaScript é armazenando elas em variáveis, nesse caso a regra para hoisting em variáveis entra em cena novamente. Vamos ver o que o nosso exemplo anterior retornaria neste caso:

<pre class="lang-javascript">nome();
var nome = function(){
	var nome = "Alex";
	console.log(nome);
}
</pre>

Declarando a função desta forma o JavaScript retorna um erro dizendo que &#8220;nome&#8221; não é uma função.

## Closure

A tradução para a Closure em português seria clausura que quer dizer confinamento ou ambiente fechado. Para conseguir esse confinamento basta declarar uma função dentro de outra, a função externa confina a função interna.

O confinamento acontece por conta da regra do JavaScript referente a escopo. Sabemos que o escopo é criado por funções, isso quer dizer que a função externa cria um escopo em que a função interna fica confinada podendo ser executada somente dentro desse escopo. As variáveis e parâmetros da função externa podem ser acessados pela função interna.

Vamos a um exemplo:

<pre class="lang-javascript">// função externa
function lancamentoDeNota(nome, exercicio , nota){
	// função interna
	function fechamento(){
		var mensagem = "Avaliação do exercício : " + exercicio;
		mensagem += "\n Aluno: " + nome;
		mensagem += "\n Nota: " + nota;
		console.log(mensagem)
	}
	// executa a função interna
	fechamento();

} // fecha função externa

lancamentoDeNota("Alex", "Importando collections", "10"); // Avaliação do exercício : Importando collections Aluno: Alex Nota: 10
</pre>

Acabamos de ver um exemplo de closure em JavaScript, mas ainda temos uma diferença muito bacana na linguagem. Em JavaScript é possível escapar a função interna do seu confinamento. Vamos avaliar o código abaixo:

<pre class="lang-javascript">// função externa
function lancamentoDeNota(nome, exercicio , nota){
	// função interna
	function fechamento(){
		var mensagem = "Avaliação do exercício: " + exercicio;
		mensagem += "\n Aluno: " + nome;
		mensagem += "\n Nota: " + nota;
		console.log(mensagem)
	}
	// escapando a função interna retornando ela de forma literal para função externa. Malandragem é pouco pro JS kkkk
	return fechamento;
}
var primeiroExercicio = lancamentoDeNota("Alex", "Importando collections", "10");
var segundoExercicio = lancamentoDeNota("Alex", "Inserindo Pokemons", "10");

primeiroExercicio(); // Avaliação do exercício : Importando collections Aluno: Alex Nota: 10
segundoExercicio(); // Avaliação do exercício : Importando Pokemons Aluno: Alex Nota: 10
</pre>

O return faz com que a função interna seja retornada de forma literal podendo ser executada fora do confinamento.

## Variável Global

Variáveis globais são todas aquelas definidas fora de alguma função. Isso porque cada função gera seu próprio escopo. A variável global pode ser acessada por qualquer função. Fizemos isso segundo exemplo. 

<pre class="lang-javascript">// Escopo global
var num = 0;

// Escopo criado para a função imprimir
function imprimir(){
	num = 1; 
	console.log(num);
}

// Executar a função e o que tem no escopo
imprimir(); // 1

// Acessando a variável do escopo global
console.log(num); // 1
</pre>

Todas as variáveis que não forem declaradas com a palavra reservada &#8216;var&#8217; serão consideradas parte do escopo
  
global.

## Variável por parâmetro

Quando declaramos uma função temos a opção de indicar alguns parâmetros para elas. Tais parâmetros são considerados como variáveis que recebem um valor na hora da execução da função. Esses valores são utilizados dentro da função. Exemplo:

<pre class="lang-javascript">function sub(num1, num2){
 console.log(num1-num2)
}
sub(10, 2) // 8
</pre>

Caso esse parâmetro seja uma variável global o valor dela não se altera. Por exemplo:

<pre class="lang-javascript">var global = 12;
function sub(global, num2){
 console.log(global-num2);
}
sub(15, 2) // 13
console.log(global); // 12
</pre>

## Instanciação usando uma IIFE

IIFE é a abreviação para Imediately Invoked Function Expression, que pode ser traduzida para Expressão de Função Invocada Imediatamente. Esse tipo de função é executada no mesmo momento que esta sendo interpretada, veja a sintaxe dela:

<pre class="lang-javascript">(function(){
 // corpo da função
}())
</pre>

Os parenteses que envolvem a função fazem dela uma expressão e os parenteses no final da declaração executa a
  
função. Esse tipo de função também pode ser armazenada em uma variável. Dessa forma:

<pre class="lang-javascript">var nome = (function(){
 // corpo da função
}())
</pre>

Como toda função, a IIFE também pode receber parâmetros. Mas agora pense o seguinte, se ela é chamada imediatamente em tempo de execução, como podemos passar os parâmetros ? Vamos ver:

<pre class="lang-javascript">var nome = (function(nome){
 // corpo da função
 console.log("Artigo escrito por: " + nome); // Alex
}("Alex"))
</pre>

Bem bacana né ? A IIFE é um partner em JavaScript que evita poluição no escopo global e com ela também é possível modularizar o código e deixar tudo mais organizado.