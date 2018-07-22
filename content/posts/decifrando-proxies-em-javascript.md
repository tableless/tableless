---
title: Decifrando Proxies em JavaScript
authors: Helder Burato Berto
type: post
image: https://i.imgur.com/3St5FYf.jpg
date: 2018-07-06
excerpt: Intercepte seus objetos utilizando Proxies.
categories:
  - Javascript
tags:
  - ECMAScript 6
---

Neste post vamos abordar o objeto **_Proxy_** incluído na versão ECMAScript 6, criando a possibilidade de interceptação de operações e viabilizando a criação de métodos customizados.

## Desvendando o objeto _Proxy_

O objeto **_Proxy_** é utilizado para criar comportamentos customizados, tem como padrão alguns parâmetros que podemos ver a seguir:

* **target**: Objeto que está sendo virtualizado pelo _Proxy_;
* **handler**: Objeto que contém as armadilhas (_traps_);
* **traps**: São métodos utilizados para interceptar operações nas propriedades de um objeto.

## Criando nosso primeiro _Proxy_

Nesta primeira etapa, criaremos um _Proxy_ simples com o objetivo de utilizarmos o objeto _handler_, onde incluiremos uma armadilha (_trap_) para que uma das propriedades do objeto tenha um valor padrão caso a propriedade não seja definida. Vamos lá?

```js
const handler = {
  get: function(obj, prop) {
    return prop in obj ? obj[prop] : 1;
  }
};

const target = {};
const proxy = new Proxy(target, handler);
proxy.age = 20;

console.log(proxy.age, proxy.active); // => 20 1
> 20 1
```

## Elaborando uma validação

Vamos utilizar o exemplo anterior e criar uma nova armadilha no objeto _handler_, aplicando o método _set_. Confira a seguir:

```js
const handler = {
  get: function(obj, prop) {
    return prop in obj ? obj[prop] : 1;
  },
  set: function(target, prop, value, receiver) {
    if (prop === 'age') {
      if (!Number.isInteger(value)) {
        throw new TypeError(`The property age isn't a number.`);
      }
    }

    // For default the value will be add to the property in the object
    target[prop] = value;

    // Indicate the success
    return true;
  }
};

const target = {};
const proxyOne = new Proxy(target, handler);
proxyOne.age = 20;

console.log(proxyOne.age, proxyOne.active); // => 20 1
> 20 1

const proxyTwo = new Proxy(target, handler);
proxyTwo.age = 'Hello World';

console.log(proxyTwo.age); // => "TypeError: The property age isn't a number."
> "TypeError: The property age isnt a number."
```

## Cancelando armadilhas (_traps_)

Vamos utilizar o método **Proxy.revocable()** para cancelar as armadilhas de um _proxy_. Confira a seguir:

```js
const handler = {
  get: function(obj, prop) {
    return prop in obj ? obj[prop] : 1;
  },
  set: function(target, prop, value, receiver) {
    // For default the value will be add to the property in the object
    target[prop] = value;

    // Indicate the success
    return true;
  }
};

const target = {
  firstName: "Helder",
  lastName: "Burato Berto"
};

const { proxy, revoke } = Proxy.revocable(target, handler);

console.log(`${proxy.firstName} ${proxy.lastName}`); // => "Helder Burato Berto"
> "Helder Burato Berto"

revoke(); // Revoke access to the proxy

console.log(`${proxy.firstName} ${proxy.lastName}`); // => "TypeError: Cannot perform 'get' on a proxy that has been revoked"
> "TypeError: Cannot perform 'get' on a proxy that has been revoked"
```

Depois que você fizer a chamada `revoke()` todas as operações relacionadas ao objeto **Proxy** vão causar um `TypeError`, desta forma você consegue prevenir que 
ocorram ações em objetos indevidos.

## Conclusão

Com os exemplos acima, podemos ilustrar como o objeto _Proxy_ pode nos ajudar em nosso dia a dia. Outros exemplos de uso e métodos de armadilhas (_traps_) você pode encontrar em:

* [MDN Proxy](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Proxy);
