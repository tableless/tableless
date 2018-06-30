---
title: 'Getters e Setters - Manipuladores com Javascript'
authors: Morais Junior
type: post
date: 2018-07-01
excerpt: ' Descobrindo formas elegantes de manipular valores de objetos'
categories:
  - JAVASCRIPT
  - Browsers  
  - ECMAScript 5
---
No javascript é comum ter valores para guardar em memória diferentes dos mostrados para o usuário (como no caso de moedas por exemplo), é normal implementarmos algo do tipo:

```javascript
//definimos um valor
variavel = 123;
//resgatamos o valor para mostrar na tela
console.log( variavel.toFixed(2).replace(".",",") );
```

Porém essa não é a forma mais elegante, para melhorar essa semântica e facilitar nossa vida foram incluídos os manipuladores get e set no ECMAScript 5.

A melhor forma de fazermos isso é implementando os manipuladores get/set para tratar os valores dentro do objeto, a utilização é bem simples basta incluir o prefixo antes da função:

```javascript
var variavel = {
  valor: 0,
  
  get moeda() { // define o get moeda
    return "R$ " + this.valor.toFixed(2).replace(".",",");
  },
  get int() { // define o get integer
    return this.valor;
  },  
  set int(i) {  // define o set
  	this.valor = i;
  }
}

console.log(variavel.moeda);
variavel.int = 123;
console.log(variavel.moeda);
variavel.int = 456;
console.log(variavel.int);
```

Uma outra forma de declarar esse objeto é com Object.defineProperty:

```javascript
var variavel = {
    valor: 0
};

Object.defineProperty(variavel, 'moeda', {
    get: function() {
        return "R$ " + this.valor.toFixed(2).replace(".",",");
    },
    set: function(name) {
        this.valor = i;
    }
});
```
### Lembre-se: 
Só porque um recurso existe, ele não precisa ser usado o tempo todo. Os getters e os setters, dependendo do uso pode deixar a leitura um pouco estranha e dificultar o entendimento de outras pessoas.

### Suporte para navegador?
O IE9 e acima têm suporte completo para Object.defineProperty, juntamente com o Safari 5+, Firefox 4+, Chrome 5+ e Opera 12+.
