---
title: Explorando o método bind em JavaScript
authors: Helder Burato Berto
type: post
image: https://i.imgur.com/86DGMav.png
date: 2018-07-30 00:00:00 -0300
excerpt: Conhecendo o método bind e seus benefícios.
categories:
- Javascript
publishdate: 2018-07-30 00:00:00 -0300
tags:
- bind

---
Neste artigo iremos abordar o método *bind*. Este método *é* muito importante na linguagem Javascript e de grande utilidade para o uso dos frameworks mais atuais.

## Introdução

O principal objetivo do método *bind* é alterar o contexto *this* de uma função independente de onde a mesma esteja sendo chamada.

É muito comum, ocorrer a transformação do *this* conforme são efetuadas novas chamadas de métodos, e que seja esperado um determinado valor para nosso contexto *this*, porém nos deparamos com um *this* muitas vezes inesperado ou *undefined*.

## Descobrindo o contexto this

Um dos erros mais comuns quando não temos conhecimento do método *bind* é a tentativa de executar métodos com contextos inicialmente inválidos. Confira o exemplo a seguir: 

```js
function cook() {
  console.log(this.ingredients);
}
cook(); // => undefined
```

No caso que executado acima, obtemos o valor `undefined` pelo fato que `this` não recebeu uma propriedade `ingredients`.

## Abordando o contexto correto

Como visualizamos no exemplo anterior, a função esperava um contexto *this* com a propriedade *ingredients,* porém não recebeu o contexto *undefined* ou inválido, desta forma vamos obter um resultado inválido em relação ao método `cook`. Confira a seguir a forma correta:

```js
function cook() {
  console.log(this.ingredients);
}

let dinner = {
  ingredients: 'bacon'
}
let cookBoundToDinner = cook.bind(dinner);
cookBoundToDinner(); // => "bacon"
```

Você pode perceber no exemplo anterior que criamos o objeto `dinner` onde estamos setando a propriedade `ingredients: 'bacon`, e na sequência chamamos a função `cook`  utilizando o método *bind* com o parâmetro `dinner` que será o seu novo contexto *this*.

## Conhecendo outras formas sem o uso do bind

Agora que conhecemos como trabalhar com o método *bind*, vamos efetuar a atividade anterior, porém sem a necessidade do método *bind*. Veja o exemplo a seguir:

```js
let cook = function() {
  console.log(this.ingredients);
}

let dinner = {
  cookDinner: cook,
  ingredients: 'bacon'
}
dinner.cookDinner(); // => "bacon"

let lunch = {
  cookLunch: cook,
  ingredients: 'salad'
}
lunch.cookLunch(); // => "salad"
```

Nos dois exemplos anteriores estamos utilizando o método `cook`, tanto no objeto `lunch` quanto no `dinner`. Sendo que a função esteja no mesmo contexto, ela vai utilizar a propriedade disponível que se encaixa à sua necessidade que no caso é `ingredients` na qual retornou ao executar a função.

## Atribuindo métodos em seu contexto this

Você não está limitado a atribuir apenas valores em suas propriedades, pode também utilizar métodos como propriedades. Confira a seguir:

```js
let calc = function() {
  return {
    sum: this.sum,
    mult: this.mult,
    div: this.div,
  }
}

let methods = {
  sum: function(x, y) {
    return x + y;
  },
  mult: function(x, y) {
    return x * y;
  },
  div: function(x, y) {
    return x / y;
  }
}
calcBound = calc.bind(methods);

console.log(calcBound().sum(2,2)); // => 4
console.log(calcBound().mult(2,3)); // => 6
console.log(calcBound().div(6,3)); // => 2
```

Neste exemplo foi utilizado o *higher-order function* onde são passadas funções como parâmetros para o contexto *this*, sendo estes os métodos `sum`, `mult` e `div`.

## Conclusão

Com os exemplos acima pode-se observar como o método *bind* facilita a execução das atividades ao trabalhar com contextos *this* em diferentes métodos.

Você conhece outras formas que o método *bind* pode ser aplicado? Deixe suas contribuições nos comentários e nos ajude a facilitar nosso dia a dia.

Caso tenha curtido, compartilhe com seus amigos e colegas. 💫