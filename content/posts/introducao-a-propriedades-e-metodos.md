---
title: Introdução a propriedades e métodos no JS
author: Diego Eis
type: post
date: 2015-08-08
excerpt: Entendendo um pouco sobre o uso de propriedades de valores e métodos no JavaScript.
url: /introducao-a-propriedades-e-metodos/
categories:
  - Código
  - JavaScript
tags:
  - JavaScript
  - metodos
  - propriedades

---
Você descobre o tamanho de uma string ou a quantidade de valores em uma Array via JavaScript usando uma coisinha chamada `length`. O length serve para acessar uma propriedade de algum valor determinado. Existem uma série de propriedades no JS que usamos em expressões para conseguir extrair informações de uma string e outros tipos de valores. Por exemplo a função Math, que tem a propriedade `max`: `Math.max`. O max é uma propriedade do objeto `Math`, que é uma coleção de valores e funções matemáticas.

A maioria dos valores em JS tem propriedades. As exceções, quase que obviamente, são os valores `null` e o `undefined`.

<img src="http://tableless.com.br/uploads/2015/08/img1.png" alt="img1" width="461" height="72" class="alignnone size-full wp-image-50652" />

Os dois caminhos mais comuns de acessar uma propriedade no JavaScript é com o **.** (ponto) ou pelos colchetes **[]**. As duas expressões `valor.propriedade` ou `valor[propriedade]` acessam uma propriedade de valor, mas não necessariamente a mesma propriedade. A diferença está em como a propriedade é interpretada. Quando usamos a propriedade via ponto, a propriedade precisa ser um nome de variável válida, e isso nomeia diretamente o nome da propriedade. Por sua vez, quando usamos um nome dentro dos colchetes, este nome é avaliado se é mesmo uma nome de propriedade válido. Enquanto o `valor.propriedade` pega o nome da propriedade e usa o valor obtido, enquanto ao usar `valor[propriedade]` tenta avaliar a expressão e usa o resultado como o nome da propriedade. 

O nome da propriedade de um objeto pode ser uma string válida ou qualquer outra coisa que possa ser convertida em uma string. Uma string válida é qualquer coisa que não contenha hífen ou espaços e não inicie por números. E por que os nomes das propriedades podem ser qualquer string, se você quiser acessar uma propriedade cujo nome comece com um número, seja uma string com espaços ou que contenha um hífen, você precisa acessá-las através na notação de colchetes. Veja o exemplo abaixo:

<pre class="lang-javascript">(function(){

  // Pegando dados via notação de colchetes ou ponto
  var meusDados = {
    "nome" : "Diego",
    "sobrenome" : "Eis",
    "data de nascimento":  "02/12/1983"
  }

  console.log(meusDados["data de nascimento"], meuObjeto.nome)

}());
</pre>

Perceba que quando o nome da propriedade contém espaços, como é o caso de **data de nascimento**, você só consegue acessá-la usando a notação de colchetes. Da mesma forma, você consegue acessar as outras propriedades usando colchetes também. O que, nesse caso, eu prefiro. Assim mantemos um padrão de escrita. Contudo, há também a possibilidade de você padronizar os nomes das propriedade para padronizar também a forma com que você irá acessar as propriedades. 

Os elementos em uma array, são guardados em propriedades e os nomes dessas propriedades são números, que significam a posição daquela propriedade na array. Sendo assim, quando você precisa recuperar o valor de uma determinada posição da array, você utiliza a notação de colchetes. Veja abaixo:

<pre class="lang-javascript">(function(){
  // Aqui só conseguimos pegar via notação de colchetes por as posições da array são variáveis válidas, mas começando com números
  var outrosDados = ["Diego", "Eis", "02/12/1983"];

  console.log(outrosDados[2], outrosDados[0])
}());
</pre>

Geralmente também usamos a notação de colchetes quando usamos comandos como o `for`. 

<pre class="lang-javascript">(function(){
  var outrosDados = ["Diego", "Eis", "02/12/1983"];

  for (var i in meusDados) {
    console.log(i + " - " + meusDados[i]);
  }
}());
</pre>

A propriedade **length** de uma array nos diz quantos elementos essa array contém. Essa propriedade é um nome de variável válida e você já conhece esse nome antecipadamente. Por isso, quando você procura saber o tamanho de uma array, você pode usar a notação de colchetes se desejar: **nomeDaArray[&#8220;length&#8221;]**, mas por ser mais fácil de escrever geralmente todo mundo usa a notação de ponto: **nomeDaArray.length**.

Essas são coisas simples do JavaScript, mas que alguns novatos podem estranhar ou nem reparar que as duas notações de propriedades, muitas vezes misturadas numa mesma função ou em um sistema inteiro, servem para fazer as mesmas ações, claro, com algumas diferenças.

## Um pouco sobre Métodos

Tanto strings e objetos de arrays contém um numero de propriedades que se referem a valores de funções. Veja por exemplo as funções `toUpperCase` e `toLowerCase`. São funções próprias do JavaScript que transformam a string em caixa alta ou caixa baixa.

<pre class="lang-javascript">(function(){
  var texto = "Lorem Ispum Dolor"
  console.log(texto.toLowerCase(), texto.toUpperCase());
}());
</pre>

Se você logar essa linha: `console.log(typeof texto.toUpperCase);` o console retorna **function**, avisando que essa expressão é uma função e retorna um valor. Se você faz a mesma coisa, só que colocando um parênteses no final do toUpperCase, assim: `console.log(typeof texto.toUpperCase());`, o console te retorna que o resultados é uma **string**.

Toda e qualquer string tem uma propriedade `toUppercase` e `toLowerCase`. Propriedades que contém funções são o que chamamos de **métodos** dos valores que eles pertencem. `toLowerCase` é um método de uma string.

Existem uma série de outros métodos. Não vou citar todos, mas você já deve ter usado vários como o `push()`, que recebe um parâmetro que será adicionado no final de uma array. O `pop()`, que faz exatamente o contrário do push, removendo o último parâmetro de uma array:

<pre class="lang-javascript">(function(){
  var umaArray = []
  console.log(umaArray)  
  // -> []

  umaArray.push("Diego") // Adiciona "Diego" na Array
  umaArray.push("Eis") // Adiciona "Eis" na Array
  console.log(umaArray)
  // -> ["Diego", "Eis"] (2)

  umaArray.pop() // Remove o último valor da Array
  console.log(umaArray)
  // -> ["Diego"] (2)

}());
</pre>

O MDN da Mozilla tem todos os métodos listados [aqui neste link][1]. Dá uma olhada lá. Você vai achar um monte de coisa interessante para estudar.

 [1]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Methods_Index