---
title: Funções do JavaScript na versão ES 6 – Parte 1
author: caioincau
type: post
date: 2015-03-25
excerpt: Entendendo algumas novidades em funções do JavaScript na versão ES6.
url: /funcoes-javascript-na-versao-es-6-parte-1/
categories:
  - Código
  - JavaScript
tags:
  - ES6
  - JavaScript
  - js

---
Ao longo dos anos as funções em JavaScript não tem mudado muito, mas agora com a nova especificação de ECMAScript 6 teremos algum avanço. Confira abaixo o que tem mudado na nova versão do JavaScript.

## Parâmetros Default:

Algo muito comum ao desenvolvermos é verificar a presença de uma váriavel e caso ela não exista, inicializamos com um valor, assim como no código abaixo:

<pre class="lang-js">function hello(nome,cidade){

  nome = nome || "Caio";
  cidade = cidade || "São Paulo";

  console.log("Sou "+nome+ " e moro em "+cidade);

}

hello(); // Sou Caio e moro em São Paulo
</pre>

Agora, com a novidade de **default parameters**, nós podemos declarar valores padrões de uma forma bem mais elegante:

<pre class="lang-js">function hello(nome="Caio", cidade="São Paulo"){

  console.log("Sou "+nome+ " e moro em "+cidade);

}

hello(); // Sou Caio e moro em São Paulo

hello("Pedro","Belo Horizonte") // Sou Pedro e moro em Belo Horizonte

</pre>

Veja que reduzimos muito nosso código, além de ficar mais fácil para um novo desenvolvedor compreender o que está ocorrendo.

## Rest Parameters:

Em JavaScript sempre pudemos passar quantos parâmetros quiséssemos para uma função por meio de argumentos:

<pre class="lang-js">function somaContaDoCliente(cliente, moeda, valores){
  var i = 2;
  var tamanho = arguments.length;
  var resultado = 0;

  while (i &lt; tamanho) {
   resultado += arguments[i];
   i++;
  }

console.log("A conta do cliente "+cliente+ " totalizou "+moeda+ resultado);

}

somaContaDoCliente("Caio","R$",1,2,3,4,5); // A conta do cliente Caio totalizou R$15
</pre>

Repare que no código acima precisamos lembrar da posição que começa nosso valores, mas e se adicionarmos mais um parâmetro no futuro? Precisaríamos lembrar de alterar o índice que usamos, mas será que só pelo nome da variável, lembraríamos que ali pode estar uma quantidade indefinida de valores?

Pensando nisto, foi criado o **Rest Parameters**, onde nós podemos realizar isso de um modo mais interessante, pois não precisamos mais acessar o array arguments e verificar as posições dele, o parâmetro que pode receber vários valores é precedido por três pontos(&#8230;) e precisa ser sempre o último parâmetro da função:

<pre class="lang-js">function somaContaDoCliente(cliente, moeda, ...valores){

  var resultado = 0;
  var i = 0;

  while (i &lt; valores.length) {

    resultado += valores[i];

    i++;

  }

console.log("A conta do cliente "+cliente+ " totalizou "+moeda+ resultado);

}

somaContaDoCliente("Caio","R$",1,2,3,4,5); //A conta do cliente Caio totalizou R$15
</pre>

Repare que ficou mais simples, não nos preocupamos com o índice e ainda está bem claro que o valores é um parâmetro especial que recebe um ou mais números.

## Destructured Parameters:

É muito comum em bibliotecas e afins, precisarmos extrair os paramêtros passados como opção, por exemplo:

<pre class="lang-js">function auth(name, password, options) {

  options = options || {};

  var https = options.https,
  provider = options.provider,
  callback = options.callback;


//Autentica baseado no provider, verifica se usa https e executa um callback caso necessário.

}

auth("caio", "minhasenha", {

  https: true,

  provider: "git"

});
</pre>

Com destructured parameters nós podemos simplesmente passar o array de elementos, sem precisar extrair cada um manualmente, deixando nossa função mais enxuta.

<pre class="lang-js">function auth(name, password, {https,provider,callback}) {

  //Autentica baseado no provider, verifica se usa https e executa um callback caso necessário.

}

auth("caio", "minhasenha", {

  https: true,

  provider: "git"

});

</pre>

Interessante não? O problema nesta abordagem é que caso o último parâmetro não seja passado, receberemos um erro, mas temos um meio de lidar com isso, usando os default parameters abordados no começo do texto, deixando nossa função da seguinte maneira:

<pre class="lang-js">function auth(name, password, {https,provider,callback} = {}) {

  //Autentica baseado no provider, verifica se usa https e executa um callback caso necessário.
}
</pre>

Ainda existem outras mudanças e incrementações nas funções em ECMAScript 6, essas irão ficar para o segundo post da série, espero que tenham gostado.