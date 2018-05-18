---
title: O que são funções puras
authors: Helder Burato Berto
type: post
image: https://i.imgur.com/EkjmCK8.jpg
date: 2018-05-18
excerpt: Compreenda o que são funções puras e como podem beneficiar na construção de suas aplicações.
categories:
  - Javascript
---

## Introdução

Sempre que lhe falarem sobre funções puras tenha em mente o seguinte.

> Funções puras são funções que dado um parâmetro _input_ sempre vão retornar o mesmo _output_ sem causar efeitos colaterais _side effects_.

## _Side effects_ quando ocorrem?

_Side effects_ (efeitos colaterais) ocorrem quando uma função ao ser executada causa mudanças no estado da aplicação, o que são chamadas de **funções impuras**.

## Por que usar funções puras?

Vou citar alguns tópicos que tornam tão interessante o uso desse tipo de função. Veja a seguir:

### Refatoração

Refatore seu código sempre que possível, funções puras te proporcionam a facilidade de mudança para que você possa observar melhorias e aplica-las sem afetar o restante de sua aplicação.

### Testabilidade
 
Pelo simples motivo de funções puras terem seus valores de entrada e saída determinados, isso vai facilitar muito a escrita de seus códigos unitários.

### _DRY (Don't Repeat Yourself)_

Reutilize suas funções! _DRY_ (Não repita a si mesmo).

## Devo usar apenas funções puras?

Não! É importante perceber que funções puras mesmo oferecendo diversos benefícios, não são utilizadas em todo o projeto. Afinal de contas, se todas as funções de seu projeto fossem funções puras, não haveriam efeitos colaterais _side effects_ onde são visíveis ao mundo externo. Certifique-se de utilizar funções puras quando necessário, crie testes unitários e sem dúvidas quando houverem bugs, será mais fácil para você desvendá-los e efetuar sua correção.

## Vamos praticar!

Vamos criar duas funções uma função **pura** e outra **impura**. Confira:

### Função Pura:

```javascript
## ES6 ##
const sum = (x, y) => x+y;

## ES5 ##
var sum = function (x, y) {
  return x + y;
}
```

### Função Impura:

```javascript
## ES6 ##
const x = 20;
const sum = (y) => x+y;

## ES5 ##
var x = 20;
var sum = function (y) {
  return x+y;
}
```

Repare que a variável `x` está sendo definida no estado global da aplicação, sendo assim o _output_ da função `sum` sempre dependerá da mudança de estado global e não pelo _input_ passado como parâmetro, o que torna a função dependente de fatores externos.

## Conclusão

É isso aí galera, espero que esse post ajude vocês no desenvolvimento de belas funções, gerando maior produtividade para você e sua equipe.

Ah, se você tem alguma dúvida ou sugestão, faça nos comentários, estou sempre atento!
