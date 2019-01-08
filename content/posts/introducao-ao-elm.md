---
title: Introdução ao Elm - diga adeus aos runtime errors
authors: Breno Panzolini
type: post
date: 2017-08-23
excerpt: Uma introdução básica à linguagem Elm.
categories:
  - Javascript
  - Tecnologia e Tendências
tags:
  - elm
image:  https://cdn-images-1.medium.com/max/720/1*I-3kbXzEIAPAPEGiMcAs0A.png
---

Nos últimos anos o JavaScript vem cada vez mais ganhando espaço no mundo da programação, seja no front-end quanto no back-end ele já se provou capaz de atender todas as demandas e necessidades de qualquer tipo de projeto.

Eu sempre utilizei JavaScript, desde o tempo onde ele servia "apenas" para fazer uma simples validação no client-side. Algo que sempre me chamou muita atenção na linguagem (e por isso acredito que se tornou tão popular) é a liberdade que ela nos fornece. Porém, ao mesmo tempo que isso é vantajoso por um lado pode se tornar um pesadelo em projetos maiores.

## O que é esse tal de Elm?

O Elm é uma linguagem de programação funcional, fortemente tipada e que compila para JavaScript, HTML e CSS. Ele surgiu com o propósito de eliminar **todas** as exceções de runtime (além de uma série de outras vantagens).

No começo achei que o Elm seria mais um *transpiler* para JS (assim como o [TypeScript][4]), porém na verdade o Elm é uma linguagem de programação e que no fim compila para JavaScript.

Um dos grandes pontos positivos é que a linguagem te obriga a desenvolver do jeito certo e reforça todas as boas práticas de programação que encontramos em diversos guias pelo GitHub.

Você pode encontrar mais informações no [site oficial][1] da linguagem, com vários exemplos, documentação e até mesmo um editor para testar o Elm online.

## Mas quais são as vantagens que o Elm proporciona?

Um dos pontos que mais chamam atenção é que no Elm não existe *runtime exceptions*, ou seja, se o seu código compilar você pode ter certeza de que não irá ter erros em tempo de execução.

Você nunca mais verá aqueles erros de *"Uncaught TypeError"*, isso porque além da forte tipagem da linguagem, não existe *Null* e *Undefined*.

O [Richard Feldman][2] [publicou em seu twitter][3] que tem uma aplicação em Elm (em produção) que desde 2015 nunca teve um erro de runtime.

Outra grande vantagem da linguagem é seu **compilador extremamente poderoso**, acho que nunca vi algo parecido em nenhuma outra linguagem.

![Compilador do Elm](https://i.imgur.com/5O0lwHl.png)

Repare que no exemplo acima cometemos um erro de digitação e o compilador não apenas sublinhou o erro como fez sugestões de correção.

## Conclusão

Apesar da linguagem ser relativamente nova e de ainda não ter ganhado a devida popularidade na comunidade, eu vejo o Elm como uma das linguagens para se ficar de olho, pois ela traz e resolve muito dos problemas atuais que encontramos no JavaScript.

Esse primeiro artigo foi apenas uma introdução básica para despertar sua curiosidade sobre o Elm. Mais artigos virão e entrarei em detalhes mais aprofundados da linguagem propriamente dita. 

[1]: https://elm-lang.org/
[2]: https://twitter.com/rtfeldman
[3]: https://twitter.com/rtfeldman/status/773185722643734528
[4]: https://www.typescriptlang.org/
