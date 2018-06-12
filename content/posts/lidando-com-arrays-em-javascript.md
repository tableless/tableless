---
title: Lidando com arrays em JavaScript
authors: Helder Burato Berto
type: post
image: https://i.imgur.com/Dka6iNE.jpg
date: 2018-06-12
excerpt: Métodos que vão simplificar seu trabalho com arrays em JavaScript.
categories:
  - Javascript
---

É muito comum no dia a dia do desenvolvedor utilizar <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array" target="_blank">arrays</a> ao desenvolver soluções em seus projetos.

Neste post vamos abordar alguns métodos do **JavaScript** que vão facilitar a forma que você pode trabalhar com **arrays** e escrever códigos mais elegantes.

## Vamos definir nossos arrays

```js
const beers = ['Heineken', 'San Diego', 'Coruja', 'Saint Bier'];
const ages = [20, 25, 19, 21, 42];
```

Perceba que foram definidos dois arrays, onde serão utilizados nos métodos que serão exemplificados a seguir.

## Desmistificando alguns métodos incríveis!

Agora que você já definiu os arrays necessários para trabalhar, vamos colocar a mão na massa e verificar os resultados com alguns métodos muito interessantes.

#### Array.every():

Possibilita testar todos os elementos do seu array. Caso algum dos elementos não passe pela condição definida por você, o retorno será `false`. Veja o exemplo:

```js
// ES5
function isGreaterThan(age) {
  return age >= 18;
}
const greater = ages.every(isGreaterThan);

// ES6
const isGreaterThan = (age) => age > 18;
const greater = ages.every(isGreaterThan);

console.log(greater); // true
> true
```

O retorno da variável `greater` deve ser `true`, pois todos os valores do array `ages` são maiores que `18`.

_Obs.: Caso seja informado um array vazio o retorno padrão deve ser TRUE_

#### Array.includes()

Possibilita verificar se um element existe ou não no array definido. Exemplo:

```js
console.log(beers.includes('Skol')); // false
> false

console.log(ages.includes(25)); // true
> true
```

Nos casos citados acima os retornos serão `false` para `beers.includes('Skol')` e `true` para `ages.includes(25)`.

#### Array.filter():

Este método possibilita a criação de filtros de forma rápida e fácil em seus arrays. Exemplo:

```js
// ES5
function startWithS(word) {
  return word.indexOf('S') === 0;
}

// ES6
const startWithS = (word) => word.indexOf('S') === 0;

const beersStartWithS = beers.filter(startWithS);

console.log(beersStartWithS); // [0: 'San Diego', 1: Saint Bier]
> [0: 'San Diego', 1: Saint Bier]
```

O retorno da variável `beersStartWithS` deve ser:
```
[
  0: 'San Diego',
  1: 'Saint Bier'
]
```

Sendo que todos os elementos retornados iniciam com a letra `S`.

#### Array.find():

Faça uma busca em seu array de um ou mais elementos que se encaixam no filtro definido por você. Exemplo:

```js
// ES5
function findSanDiego(element) {
  return element === 'San Diego';
}

// ES6
const findSanDiego = (element) => element === 'San Diego';

const beerSanDiego = beers.find(findSanDiego);

console.log(beerSanDiego); // 'San Diego'
> 'San Diego'
```

Criamos um filtro para buscar o elemento que se chamam `San Diego`. Como nosso array `beers` possui um elemento com este nome, vamos receber o retorno `San Diego` na variável `beerSanDiego`.

_Obs.: Caso não houvessem elementos a serem retornados, obteríamos o retorno `undefined`._

#### Array.map()

Este método percorre todos os elementos do array, executando funções para cada elemento e retornando um novo array como resultado. Exemplo:

```js
// ES5
function upAge(age) {
  return age + 1;
}

// ES6
const upAge = (age) => age + 1;

const newAges = ages.map(upAge);

console.log(newAges); // [0: 21, 1: 26, 2: 20, 3: 22, 4: 43]
> [0: 21, 1: 26, 2: 20, 3: 22, 4: 43]
```

Perceba que receberemos o seguinte retorno em `newAges`:

```js
[
  0: 21,
  1: 26,
  2: 20,
  3: 22,
  4: 43
]
```

Onde foi acrescentado `mais um` aos seus valores iniciais.

#### Array.some()

Este método verifica se ao menos um elemento satisfaz a condição definida por você. Exemplo:

```js
// ES5
function hasHeinekenOrSaint(beer) {
  return (beer === 'Saint Bier' || beer === 'Heineken');
}

// ES6
const hasHeinekenOrSaint = (beer) => (beer === 'Saint Bier' || beer === 'Heineken');

const heinekenSaint = beers.some(hasHeinekenOrSaint);

console.log(heinekenSaint); // true
> true
```

Neste caso está sendo verificado se existem ocasiões de elementos `Heineken` ou `Saint Bier`. Caso ocorrerem o resultado será `true`.

#### Array.reduce()

Você pode utilizar o método reduce para alguns casos, sendo um deles para facilitar cálculos. Exemplo:

```js
// ES5
function reducerAge(accumulator, age) {
  return accumulator + age;
}

// ES6
const reducerAge = (accumulator, age) => accumulator + age;

const sumAges = ages.reduce(reducerAge);

console.log(sumAges); // 127
> 127
```

O retorno neste caso será `127` a soma de todas as idades.

## Conclusão

Utilizar dos recursos oferecidos pela linguagem lhe da grandes poderes!

E você? Utiliza esses recursos? Compartilhe sua experiência nos comentários. ⚡️
