---
title: Entendendo Programação Funcional em JavaScript de uma vez
authors: Matheus Lima
type: post
date: 2017-09-14
excerpt: Você já percebeu que cada vez mais o termo Programação Funcional vem sendo usado pela comunidade?
categories:
  - Javascript
  - Na Prática
  - es6
  - es5
tags:
  - Javascript
  - ReactJS
  - AngularJS
  - es6
  - es5
image: https://cdn-images-1.medium.com/max/800/1*2paLPOKgTuxCqGADIY2CKg.png
---

No meu último *post*, por exemplo: [O que TODO desenvolvedor JavaScript precisa
saber](https://tableless.com.br/o-que-todo-dev-js-precisa-saber/),
um dos pontos que gerou mais dúvida foi justamente o da Programação Funcional.

Continue lendo esse artigo para aprender:

1. Quais as vantagens de usar a Programação Funcional;
2. Como usá-la tanto em ES5 quanto em ES6;
3. O que são *Pure Functions* e *Higher-Order Functions*;
4. Qual a diferença entre *Map*, *Filter *e *Reduce*;
5. O que é *Currying*;
6. Como compor funções de maneira eficaz;

Para entender as verdadeiras motivações, temos obrigatoriamente que voltar aos
conceitos básicos.

A função abaixo possui *inputs* e *outputs* bem definidos:

<script src="https://gist.github.com/matheusml/e492bcb9c9f3d4898035.js"></script>

Ela recebe como parâmetro uma variável **x** e retorna um *int* que é a
multiplicação de **x** com ele mesmo.

A função abaixo porém, não possui *inputs* e *outputs* tão bem definidos:

<script src="https://gist.github.com/matheusml/3e32f89a220b295a5732.js"></script>

Ela não recebe nada como parâmetro e retorna o que parece ser uma data
processada mas não temos como ter certeza.

Um ponto que vale ser reforçado: só porque não declaramos explicitamente os
*inputs* e *outputs* dessa função não quer dizer que a mesma não os tenha. Eles
apenas estão ocultos. E isso pode gerar um dos piores problemas nas aplicações
modernas: os [Efeitos Colaterais
(side-effects)](https://www.quora.com/What-is-a-side-effect-in-programming).

Funções como as de cima que possuem *inputs* e *outputs* ocultos e podem gerar
*side-effects* são chamadas de [Funções Impuras (impure
functions)](https://egghead.io/lessons/javascript-redux-pure-and-impure-functions).
Outra característica importante delas é que se invocarmos uma função impura
diversas vezes, o retorno dela nem sempre será o mesmo. O que dificulta a
manutenção e os testes na sua aplicação.

[Funções Puras (pure
functions)](https://stackoverflow.com/questions/22395311/difference-between-pure-and-impure-function)
por outro lado, como o primeiro exemplo desse *post*, tem *inputs* e *outputs*
declarados e não geram *side-effects*. Além disso, o retorno de uma função pura
dado um parâmetro será sempre o mesmo. Obviamente os seus testes serão mais
fáceis de desenvolver, assim como a manutenção da sua aplicação.

<div style="text-align: center;">
	<img style="width: auto;" src="https://cdn-images-1.medium.com/max/800/1*RBr2QH3f_Wm2_tKtsFkQsw.png">
</div>

E por que estamos falando sobre isso?

Porque escrever funções puras e remover *side-effects* é a base da Programação
Funcional.

*****

Agora que temos uma ideia melhor da motivação de se usar Programação Funcional,
podemos começar a ver os casos reais e aprender na prática como usá-la.

### 1) Higher-Order Functions

Matematicamente falando, funções que operam sobre outras funções ou as recebendo
como parâmetro ou as retornando são chamadas de [Higher-Order
Functions](https://github.com/js-functional/js-funcional#higher-order-functions).

Essas funções nos permitem fazer abstrações não apenas de valores mas também de
ações, como no exemplo abaixo:

<script src="https://gist.github.com/matheusml/0bda9801dee4cbca2f61.js"></script>

A função **calculate** recebe três parâmetros. O primeiro é uma função qualquer
que será invocada passando como parâmetro **x** e **y**.

Pensando em um cenário em que precisamos tanto de uma soma quanto de uma
multiplicação, podemos pensar na solução dessa forma em ES5:

<script src="https://gist.github.com/matheusml/f0337b46ce139174ffb6.js"></script>

Ou dessa, bem mais curta, em ES6:

<script src="https://gist.github.com/matheusml/4a40ce82b5e28248aa4b.js"></script>

*Higher-order functions* estão em todos os lugares no ecossistema do JavaScript.
Se você já usou testes unitários com [Jasmine](https://jasmine.github.io/) ou
[Mocha](https://mochajs.org/), então o trecho abaixo deve ser familiar:

<script src="https://gist.github.com/matheusml/0dda8c064b756e5ec077.js"></script>

Percebemos que o segundo parâmetro tanto de **describe** quanto de **it** são
funções. Por definição ambas são *higher-order functions*.

Outro exemplo também é o bom e velho [jQuery](https://jquery.com/). Podemos
perceber que praticamente todo o código gerado por ele era composto de
*higher-order functions*, como o exemplo abaixo:

<script src="https://gist.github.com/matheusml/d2e53527b51a72e0097f.js"></script>

Em aplicações desenvolvidas com [AngularJS](https://angularjs.org/) também não é
diferente, observe atentamente a definição de um *controller*:

<script src="https://gist.github.com/matheusml/e63cd4138422e98433f6.js"></script>

Agora que já temos conhecimento dos fundamentos: *pure functions* e
*higher-order functions* podemos nos aprofundar um pouco mais…

### 2) Map

A função **map** invoca um *callback* e retorna um novo *array* com o resultado
desse *callback* aplicado em cada item do *array* inicial.

Imaginando um cenário em que temos um *array* de inteiros e precisamos do
quadrado de cada valor desse *array*, podemos fazer dessa forma bem simples
usando a função **map** em ES5:

<script src="https://gist.github.com/matheusml/1b32cf1f9dc86cc432c8.js"></script>

Ou assim em ES6:

<script src="https://gist.github.com/matheusml/2cf56c706e6a0244fe97.js"></script>

Nesse outro cenário abaixo, percebemos o reaproveitamento de código que podemos
conseguir ao usar o **map**.

Possuímos dois *arrays* de objetos diferentes, porém ambos tem o campo *name*, e
precisamos de uma função que retorne um novo *array* apenas com os *names* dos
objetos:

<script src="https://gist.github.com/matheusml/6cc1220e4eb4b5c1c89c.js"></script>

Em ES6:

<script src="https://gist.github.com/matheusml/8afaa0e25a8b3fe498d6.js"></script>

Podemos melhorar ainda mais esse trecho de código alterando as funções *byName*
e *byNames* para que o atributo *name* não esteja mais tão acoplado. Podemos
simplesmente receber como parâmetro qualquer atributo e aplicá-lo a função. Fica
como exercício :)

### 3) Filter

A função **filter** é bem semelhante ao *map*: ela também recebe um *callback*
como parâmetro e também retorna um novo *array*, a única diferença é que
**filter**, como o próprio nome diz, retorna um filtro dos elementos do *array*
inicial baseado na função de *callback*.

Imaginando que temos um *array* de inteiros e desejamos retornar apenas aqueles
que são maiores do que 4. Podemos resolver assim usando o **filter** com ES5:

<script src="https://gist.github.com/matheusml/5f4594ed91ba8de6f9a9.js"></script>

Ou com ES6:

<script src="https://gist.github.com/matheusml/02eeb2beb95cdc22029b.js"></script>

Outro exercício é uma melhoria na função **isBiggerThanFour**, deveríamos
alterá-la para receber como parâmetro qualquer inteiro que desejamos fazer a
comparação.

### 4) Reduce

Uma das funções que mais gera dúvidas é o **reduce**. Ele recebe como parâmetro
um *callback* e um valor inicial, com o objetivo de reduzir o array a um único
valor. O cenário mais comum para explicar o **reduce** é uma soma:

<script src="https://gist.github.com/matheusml/56910066541946825b47.js"></script>

Com ES6 seria assim:

<script src="https://gist.github.com/matheusml/53e7ad603bd6b2e5c15e.js"></script>

O primeiro parâmetro é a função que será aplicada, no caso uma soma. E o segundo
parâmetro é o valor inicial. Se por algum motivo precisássemos começar a soma
com 10, faríamos dessa forma:

<script src="https://gist.github.com/matheusml/4a64111b317ae24f8913.js"></script>

Mas o **reduce** não serve apenas para somas, podemos também trabalhar com
*strings*. Imaginando que nós temos um *array* de meses e precisamos retornar o
meses dessa forma: **JAN/FEV/MAR … / DEZ**. <br> Podemos fazer assim:

<script src="https://gist.github.com/matheusml/9b0dd9da7ac2dd3ffc76.js"></script>

Não era bem o que a gente queria inicialmente. <br> Nós queríamos isso:
**JAN/FEV/MAR … / DEZ**Mas obtivemos isso:** /JAN/FEV/MAR … / DEZ**

Devemos alterar nossa função *monthsShortener* para adicionar uma condição que
faça a prevenção desse erro:

<script src="https://gist.github.com/matheusml/8d23be9d2cc1ea36545d.js"></script>

Feito! E também na versão em ES6:

<script src="https://gist.github.com/matheusml/bef91d9e3e5ef8851834.js"></script>

### 5) Currying

A técnica de transformar uma função com múltiplos parâmetros em uma sequência de
funções que aceitam apenas um parâmetro é chamada de
[Currying](https://en.wikipedia.org/wiki/Currying).

Se na teoria ficou confuso, na prática seria transformar isso:

<script src="https://gist.github.com/matheusml/0a74712997cae05d35fd.js"></script>

Nisso:

<script src="https://gist.github.com/matheusml/d609db4920fa312aaee7.js"></script>

A princípio parece que estamos apenas adicionando mais dificuldade sem nenhum
ganho. Porém temos uma grande vantagem: transformar 0 código em pequenos pedaços
mais expressivos e com maior reuso.

Pensando em uma aplicação que possui diversos trechos do código uma soma com 5 e
outra com 10, podemos usar a segunda versão da função *add* dessa forma:

<script src="https://gist.github.com/matheusml/ac345d524f937f121c05.js"></script>

Mais um exemplo seria um *Hello World* simples com uma *curried function*.
Podemos implementá-lo desse jeito com ES5:

<script src="https://gist.github.com/matheusml/b9bc4fedb1225b654213.js"></script>

Ou com ES6:

<script src="https://gist.github.com/matheusml/219a6454c79a39afde47.js"></script>

### 6) Compose

Podemos compor funções pequenas para gerar outras mais complexas de forma bem
fácil em JavaScript. A vantagem é o poder de usar essas funções mais complexas,
de forma simples, em toda aplicação. Ou seja, aumentamos o reuso.

Por exemplo, em uma aplicação em que necessitamos de uma função para transformar
uma *string* passada pelo usuário em um grito: mudar para caracteres maiúsculos
e adicionar uma exclamação no final. Podemos fazer assim em ES5:

<script src="https://gist.github.com/matheusml/bb206f46799a2a89bb81.js"></script>

Ou em ES6:

<script src="https://gist.github.com/matheusml/fc945c5719bc6d5514d8.js"></script>

---

Esse artigo foi escrito originalmente no [canal do Tableless no Medium](https://medium.com/tableless)!