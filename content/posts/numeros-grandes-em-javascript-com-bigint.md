---
title: Números grandes em JavaScript com BigInt
authors: Matheus Alves
type: post
date: 2018-12-16
excerpt: Apresentação de um novo tipo de dado para números.
image: https://i.imgur.com/vMZC6sg.jpg
categories:
  - JavaScript
tags:
  - BigInt
---

Certa vez, quando comecei estudar JavaScript, decidi criar uma [ferramenta para escrever números por extenso](https://github.com/theuves/extenso.js) na língua portuguesa. Tal ferramenta deveria escrever valores altos: até 999 decilhões.

No entanto, enfrentei problemas logo quando tentei realizar os testes unitários, onde em um momento, eu passava `10000000000000001` (em `Number`) como entrada e esperava ter, portanto, `'dez quatrilhões e um'` como saída. Mas tinha algo errado e eu só recebia `'dez quatrilhões'`. Revirei todo o meu código a procura do erro, mas só após um bom tempo descobri que o "problema" estava fora dele: no próprio JavaScript.

O fato é que a linguagem armazena os seus valores numéricos em 64 bits seguindo o [padrão internacional IEEE 754](https://www.youtube.com/watch?v=PDgT0T0Yodo) cujo o maior número inteiro com uma precisão segura é 9.007.199.254.740.991 (cerca de 9 quatrilhões), onde qualquer número maior que esse pode ter valores perdidos, sendo assim, inseguros. Visto que nos meus testes eu estava passando um valor maior que esse e como um `Number` do JavaScript, eu tinha finalmente encontrado o motivo do erro.

## Resolvendo o problema com `BigInt`

Okay, então não podemos confiar em operações matemáticas com números grandes no JavaScript pois eles serão registrados de modo diferente? Sim, mas só por enquanto. Na época em que eu estava fazendo minha ferramenta, não existia nenhuma proposta de solução para isso, além de bibliotecas que deixam o sistema lento e o desenvolvimento chato. Até que [Daniel Ehrenberg](https://twitter.com/littledan) publicou sua proposta de `BigInt`, um novo tipo de dado que tem como objetivo dar a possibilidade de manipular números grandes.

A ideia é simples: representar números inteiros de qualquer tamanho utilizando um `n` no final ou dentro de *strings* envolvidas no objeto `BigInt`. Sendo assim, se antes `10000000000000001` estranhamente virava  `10000000000000000`, agora bastaria usar `10000000000000001n` e o número não teria nenhuma alteração.

##  Funcionamento

O `BigInt` tem o seu próprio tipo, onde `typeof 42n` é `'bigint'` e não `'number'`. 

Os `BigInt`s são bastante semelhantes aos `Number`s, podendo ser feita as mesmas operações matemáticas com `+`, `-`, `*`, `/`, etc. Contudo, embora eles sejam parecidos, operações entre um e outro é completamente impossível, o que significa que você jamais poderá fazer coisas como `6n * 2`, pois isso causaria um `TypeError`. Além disso, assim como o próprio nome `BigInt` sugere, o novo tipo só pode trabalhar com números inteiros, onde qualquer resultado quebrado em operações será arredondado automaticamente.

```js
console.log(5n / 2n) // Isso retorna 2n e não 2.5n.
```

Observa-se também que `2.5n` não existe, sendo um `SyntaxError`.

Outra  semelhança interessante com o `Number` é a possibilidade da manipulação de números como se fossem valores booleanos, por exemplo, `Boolean(0n)` quem é igual a `false`, enquanto qualquer outro número diferente de zero é verdadeiro.

## Já posso usá-lo em projetos?

No momento (final de 2018) a proposta do `BigInt` já está no estágio três, precisando estar no quatro para ser um novo padrão da linguagem (veja [esse post](https://medium.com/@brunovincius/processo-de-adi%C3%A7%C3%A3o-de-novas-features-do-js-5c2e086cab8f) do Bruno Vinícius sobre os estágios das futuras características do JavaScript), mas falta muito pouco para que ele chegue lá, portanto, provavelmente em 2019 ou 2020 ele já estará padronizado.

Caso você já queira testá-lo na prática, pode fazê-lo com as últimas versões do Google Chrome (que o aceita [desde maio desse ano](https://developers.google.com/web/updates/2018/05/nic67)), do Opera e do Node.js. No momento o Mozilla Firefox ainda não o suporta, mas é possível que em breve também vai aceitá-lo. [Veja aqui como anda a compatibilidade em navegadores da *internet*](https://caniuse.com/#feat=bigint).

Como ele ainda é muito pouco suportado, caso você queira trabalhar com número grandes em algum projeto, o mais recomendado seria usar algum [*polyfill*](https://pt.stackoverflow.com/questions/194857/o-que-%C3%A9-polyfill). Há muito tempo já existe bibliotecas como [*bn.js*](https://www.npmjs.com/package/bn.js) que trabalham com métodos para fazer operações com números desse tipo dentro de *strings*, porém, elas são lentas e impossibilitam o uso da notação `n` no final dos números, o que torna o desenvolvimento desagradável.

A biblioteca mais interessante no momento é a [*JSBI*](https://www.npmjs.com/package/jsbi) lançada há pouco tempo pela galera do Google Chrome Labs. Ela basicamente oferece um objeto que pode ser usado para fazer todas operações que o `BigInt` poderá fazer.

```js
import JSBI from 'jsbi'

const x = JSBI.BigInt('10000000000000000')
const y = JSBI.BigInt('1')
const result = JSBI.add(x, y)

console.log(result.toString()) // Meu '10000000000000001', finalmente!
```

O mais curioso também, é o *plugin* [*babel-plugin-transform-jsbi-to-bigint*](https://www.npmjs.com/package/babel-plugin-transform-jsbi-to-bigint) para o Babel que foi lançado junto com essa biblioteca. Esse *plugin* permite que em futuro próximo, quando `BigInt`s forem nativas do JavaScript, você possa converter o seu código que faz operações com *JSBI* para *BigInt*, ou seja, `JSBI.BigInt('10000000000000000')` seria transformado em `10000000000000000n`. Caso queira testar isso, eu deixei [esse repositório](https://github.com/theuves-demos/jsbi-to-bigint) no GitHub com um exemplo.

Se você deseja saber mais sobre o funcionamento dessa nova *feature*, eu recomendo que você veja a [proposta dela no GitHub](https://github.com/tc39/proposal-bigint) (em inglês) e assista a palestra [*Native BigInts in JavaScript: A Case Study in TC39*](https://www.youtube.com/watch?v=RiU5OzMZ7z8) (em inglês também) do próprio autor Daniel Ehrenberg na JSConf 2018.
