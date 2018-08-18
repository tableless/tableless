---
title: 'Getters e Setters - Manipuladores com Javascript'
authors: Morais Junior
type: post
date: 2018-08-17
excerpt: ' Descobrindo formas elegantes de manipular valores de objetos'
image: https://pbs.twimg.com/profile_images/776813473657450497/7KHzfkD-_400x400.jpg
categories:
  - JAVASCRIPT
  - Browsers  
  - ECMAScript 5
---
Getters e setters são comuns em várias linguagens, no javascript não seria diferente, eles nos ajudam a encapsular/proteger/isolar propriedades e facilitar o trabalho com objetos. Normalmente utilizamos quando precisamos fazer validações ou tratamentos antes de salvar um dados. O mesmo acontece para recuperá-los. Sem os getters e setters poderíamos fazer desta forma:

```javascript
//definimos um valor
variavel = 123;
//resgatamos o valor para mostrar na tela
console.log( variavel.toFixed(2).replace(".",",") );
```

Porém essa não é a forma mais elegante, para melhorar essa semântica e facilitar nossa vida foram incluídos os manipuladores get e set no ECMAScript 5.

A melhor forma de fazermos isso é implementando os manipuladores para tratar os valores dentro do objeto, a utilização é bem simples basta incluir o prefixo antes da função:

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
Existem várias formas de fazer neston, com getters e setters não seria diferente além da forma literal mostrada anteriormente temos defineProperty e defineGetter/defineSetter:

### defineProperty

```javascript
var variavel = {
    valor: 0
};

Object.defineProperty(variavel, 'moeda', {
    get: function() {
        return "R$ " + this.valor.toFixed(2).replace(".",",");
    },
    set: function(i) {
        this.valor = i;
    }
});

variavel.moeda = 10;
console.log(variavel.moeda)
```

### defineGetter

```javascript
Array.prototype.__defineGetter__("sum", function sum(){
	var r = 0, a = this, i = a.length - 1;
	do {
		r += a[i];
		i -= 1;
	} while (i >= 0);
		return r;
	});
	var asdf = [1, 2, 3, 4];
asdf.sum; //returns 10
```

### defineSetter

```javascript
var o = {};
o.__defineSetter__('value', function(val) { this.anotherValue = val; });
o.value = 5;
console.log(o.value); // undefined
console.log(o.anotherValue); // 5
```

### Fazendo mágica

Podemos definir controladores mais flexíveis
```javascript
var evento_string = 'dinamico'; //string com o nome do método

var obj = {
  get [evento_string]() { return 'bar'; }
};

console.log(obj.dinamico); // "bar"
```

### Compatibilidade

Temos compatibilidades e padrões diferentes para definirmos get e set:

#### ECMAScript 5

No ES5, você normalmente usaria Obect.defineProperty para implementar:

```javascript
function pessoa() {
    this.name = "Mike";
}

Object.defineProperty(pessoa.prototype, "ola", {
    get: function() {
        return "Hi, " + this.name + "!";
    }
});

var eu = new pessoa('Alex');

console.log(eu.ola);
```

#### ECMAScript 2015

No ES2015, você também pode usar classes para obter o comportamento desejado:
```javascript
class pessoa{
    constructor(name) {
        this.name = name;
    }
    get ola() {
        return `Hi, ${this.name}!`;
    }
}

var eu = new pessoa('Bob');
console.log(eu.ola);  // Outputs 'Bob'
```

##### Herança dos manipuladores

```javascript
class pessoa {
  constructor(name) {
    this._name = name;
  }

  get name() {
    return this._name.toUpperCase();
  }

  set name(newName) {
    this._name = newName;  
  }
}
  

class programador extends pessoa {  //programador é um pessoa
  constructor(name, linguagem) {
    super(name);
    this._linguagem = linguagem;
  }
  writeCode() {
    console.log(this._name + ' programa em ' + this._linguagem + '.');
  }
}

let cory = new programador('Junior', 'JavaScript');
cory.writeCode();   // Outputs 'Junior programa em JavaScript.'
```

### Lembre-se: 
Só porque um recurso existe, ele não precisa ser usado o tempo todo. Os getters e os setters, dependendo do uso pode deixar a leitura um pouco estranha e dificultar o entendimento de outras pessoas.

### Suporte para navegador?
O IE9 e acima têm suporte completo para Object.defineProperty, juntamente com o Safari 5+, Firefox 4+, Chrome 5+ e Opera 12+.
