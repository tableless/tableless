---
title: Condições ternárias
author: Felipe Rodrigues
type: post
date: 2015-03-04
excerpt: 'Algumas condições simples precisam de muito código para definir uma atribuição.  Podemos usar condições ternárias para tornar nosso código mais conciso.'
url: /condicoes-ternarias/
categories:
  - JavaScript

---
Algumas condições simples precisam de muito código para definir uma atribuição. 

Por exemplo:

<pre class="lang-javascript">var isIphone = false;
var os;

if (isIphone) {
  os = "iOS";
} else {
  os = "Android";
}
</pre>

O código precisa de dois blocos para definir uma única atribuição. Podemos usar condições ternárias para tornar o código mais conciso.

A condição ternária oferece um atalho mais rápido que os longos blocos de condicionais tradicionais.

Pra fazer uma condição ternária, colocamos primeiro a condição, seguida pelo operador que divide a condicional entre condição e as ações a serem tomadas.

Por exemplo:

<pre class="lang-javascript">algumaCondicional ? acaoSeVerdadeiro : acaoSeFalso;
</pre>

Uma das ações será executada de acordo com o resultado da condição.

Voltando ao primeiro código de exemplo, vamos transformá-lo numa condição ternária.

<pre class="lang-javascript">var isIphone = false;
var os;

isIphone ? "iOS" : "Android";
</pre>

Essa condição ternária já está retornando o resultado correto, mas podemos armazenar em uma variável para facilitar a utilização.

<pre class="lang-javascript">var isIphone = false;
var os = isIphone ? "iOS" : "Android";
</pre>

Uma vez que uma condição ternária sempre retorna um resultado, podemos utilizá-lo de várias formas.

Por exemplo:

<pre class="lang-javascript">var isIphone = false;
var os = isIphone ? "iOS" : "Android";

console.log("Sistema operacional atual: " + os);
</pre>

Caso você só precise utilizar o resultado apenas uma vez, podemos eliminar a atribuição.

<pre class="lang-javascript">var isIphone = false;

console.log("Sistema operacional atual: " + isIphone ? "iOS" : "Android");
</pre>

O problema é que esse código vai gerar um erro por que o operador “?” tem uma precedência menor que o operador &#8220;+&#8221;. O operador &#8220;+&#8221; vai avaliar a variável e adicioná-la a uma string antes do operador “?” checar a condição, ou seja, temos um grande problema. O resultado não é o esperado e o programa não funciona da forma que deveria.

Para resolver o problema devemos colocar nossa condição entre “()” e garantir que nossa condição será checada corretamente. Dessa forma, a condição ternária estará perfeitamente isolada.

<pre class="lang-javascript">var isIphone = false;

console.log("Sistema operacional atual: " + (isIphone ? "iOS" : "Android"));
</pre>