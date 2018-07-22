---
title: Congelando seus objetos no JavaScript
authors: Breno Panzolini
type: post
publishdate: 2018-03-22
date: 2018-03-19
excerpt: Como utilizar o método Object.freeze() para congelar seus objetos no JavaScript.
categories:
  - Javascript
  - NodeJS
tags:
  - Javascript
  - NodeJS
image: https://i.imgur.com/mVJXrK1.jpg
---

Nesse post vou apresentar a funcionalidade do método **Object.freeze()** e como podemos utilizá-lo para congelar nossos objetos e assim deixar nosso código JavaScript um pouco mais elegante.

## O problema

Quem conhece ou trabalha com programação orientada à objetos já está acostumado a naturalmente agrupar funções e comportamentos semelhantes dentro de `classes`, como por exemplo:

```
// Quadrado.js

export default class Quadrado {
  constructor (lado) {
    this.lado = lado
  }

  function area () {
    return this.lado * this.lado
  }
}

// Index.js

const quadrado = new Quadrado(5)
const resultado = quadrado.area()
```

Apesar de não haver nenhum erro na implementação acima, as classes e objetos no JavaScript apresentam um comportamento que podem ocasionar certa "dor de cabeça" se não tomarmos o devido cuidado e atenção.

Por exemplo, os objetos instanciados através da palavra `new` são **mutáveis**, ou seja, conseguimos mudar o comportamento padrão de objeto. Voltando para o exemplo da classe `Quadrado` apresentada acima, poderíamos fazer:

```
const quadrado = new Quadrado(2)
quadrado.area = () => console.log('outro comportamento')

const resultado = quadrado.area()
// Mudamos o comportamento da função area() e teremos um resultado completamente diferente do esperado
```

## A solução

Para nos "proteger" do cenário apresentado acima, podemos utilizar o método **Object.freeze()** para congelar nossas classes e objetos:

```
// Quadrado.js

export default function newQuadrado (lado) {
  return Object.freeze({
    area
  })

  function area () {
    return lado * lado
  }
}

// Index.js

const quadrado = newQuadrado(5)
const resultado = quadrado.area()
```

Com a nossa implementação acima não precisamos mais:
* Da palavra reservada `new`
* Da palavra reservada `this`
* E o principal é que agora o nosso objeto está **imutável**

Quando utilizamos o método **Object.freeze()** nós literalmente congelamos o objeto, impedindo que novas propriedades sejam adicionadas e removidas. Além disso os _prototypes_ também não podem ser alterados.

## Vá com calma

Apesar de ser uma técnica muito boa para evitar a mutabilidade dos nossos objetos, criar as classes com o **Object.freeze()** é mais lento e consome mais memória do que a forma tradicional.

Não existe nada perfeito e tudo é uma questão de escolha, ou seja, vai depender especificamente de cada cenário e situação. Em determinados momentos podemos utilizar a forma apresentada acima e em outros a forma tradicional de criação de classes do JavaScript.

## Conclusão

Esse post foi para apresentar a funcionalidade do método **Object.freeze()** e mostrar uma das formas de como criar classes e objetos imutáveis no JavaScript.

O post foi baseado no artigo [Elegant Patterns in Modern JavaScript - Ice Factory](https://medium.freecodecamp.org/elegant-patterns-in-modern-javascript-ice-factory-4161859a0eee) onde o autor apresenta mais a fundo o padrão *Ice Factory* e os benefícios dessa técnica.

Quem quiser conhecer mais sobre o **Object.freeze()** pode também consultar a [documentação oficial](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Object/freeze).
