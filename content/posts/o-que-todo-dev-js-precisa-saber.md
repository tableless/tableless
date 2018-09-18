---
title: O que TODO desenvolvedor JavaScript precisa saber
authors: Matheus Lima
type: post
date: 2017-08-06
excerpt: Nos últimos anos o JS passou por uma grande revolução, apesar disso, existe uma parte fundamental da linguagem que todos deveríamos saber.
categories:
  - Javascript
  - Na Prática
tags:
  - Javascript
  - ReactJS
  - AngularJS
image: https://i.imgur.com/duv3zng.jpg
---

Nos últimos anos o JavaScript vem passado por uma grande revolução: uma enorme
adoção por partes das empresas,
[polêmicas](https://medium.com/@wob/the-sad-state-of-web-development-1603a861d29f#.98fanzhk9)
e algumas rivalidades:

* ES6/ES7 x TypeScript
* Angular x React
* Gulp x Grunt
* Functional Programming x OOP

Apesar disso, existe uma parte fundamental da linguagem que todos deveríamos
saber.

## 1) Call x Apply

As funções **call** e **apply** nos deixam invocar métodos como se estivéssemos
no contexto de um outro objeto:

<script src="https://gist.github.com/matheusml/060746fcebfe791c3d78.js"></script>

O primeiro parâmetro tanto de **call** quanto de **apply** é o próprio contexto,
ou seja: o valor de **this** será exatamente o que você passar como parâmetro.
<br> Então qual a diferença entre eles? O segundo parâmetro.

Enquanto **apply** aceita um array, **call** requer parâmetros divididos por
vírgulas:

<script src="https://gist.github.com/matheusml/688081b5de307bd83ae4.js"></script>

### Qual a importância?

A importância desses dois métodos e o porquê deles serem tão usados
(principalmente em
[libs](https://github.com/angular/angular.js/blob/master/src/Angular.js#L1138))
é bem simples: **apply** e **call** nos permitem pegar métodos emprestados
reduzindo assim a quantidade total de código gerada e seguindo o
[DRY](https://c2.com/cgi/wiki?DontRepeatYourself).

## 2) Closures

A combinação de uma função e a referência ao seu estado externo é uma
**closure**. Uma aplicação comum de **closures** são os
[IIFEs](https://blog.concretesolutions.com.br/2014/12/funcoes-imediatas-javascript-iife/):

<script src="https://gist.github.com/matheusml/a8b543babdfdff07be83.js"></script>

A variável **a** é privada por ficar em uma **closure**. Já a **b**, é uma
variável global.

Uma outra abordagem para a criação de uma **closure**, é basicamente criar uma
função dentro de outra, dessa forma:

<script src="https://gist.github.com/matheusml/31efe0133e886ff32413.js"></script>

A função de dentro (**hello**) tem acesso ao escopo externo dela (**init**).
Porém, ao sairmos de **init**, perdemos a visibilidade da função **hello**.

### Qual a importância?

A capacidade de esconder informações também conhecida como: *data privacy*. Isso
é essencial para que possamos esconder informações que deveriam ser privadas e
[programar para uma interface e não para uma
implementação](https://www.fatagnus.com/program-to-an-interface-not-an-implementation/).

## 3) This

A palavra-chave **this** no JavaScript funciona de uma maneira um pouco
diferente das outras linguagens. Em [linguagens
OO](https://searchsoa.techtarget.com/definition/object-oriented-programming)
comuns o **this** se refere a instância da classe corrente. Porém, no JavaScript
o valor de **this** é determinado pelo contexto de invocação da função e onde
elas foram chamadas.

### Escopo Global

No escopo global (em um *browser*) o **this** se refere ao objeto
[window](https://developer.mozilla.org/en-US/docs/Web/API/Window), tanto dentro
quanto fora de uma função:

<script src="https://gist.github.com/matheusml/015de3b343c79f4d825a.js"></script>

### Método de objeto

Quando usado dentro de um método de um objeto, o **this** se refere ao próprio
objeto:

<script src="https://gist.github.com/matheusml/5fae41113eb41894c897.js"></script>

E no caso de objetos aninhados, o **this** vai se referir ao objeto pai mais
próximo:

<script src="https://gist.github.com/matheusml/c818f5592608844f79ed.js"></script>

É bem comum esquecermos a regra acima, principalmente no uso de *loops*:

<script src="https://gist.github.com/matheusml/c72ad74787cc99fa0221.js"></script>

Uma forma fácil de corrigir esse problema é simplesmente guardar o valor do
**this** em uma variável e ao invés de chamar o **this**, chamar essa variável:

<script src="https://gist.github.com/matheusml/9bf5029da4ed5a9bac42.js"></script>

### Função sem contexto

Quando usamos o **this **numa função invocada sem contexto então o *bind* é
feito no contexto global, mesmo se a função for definida dentro de um objeto:

<script src="https://gist.github.com/matheusml/69d14063d386422a350c.js"></script>

### Função na Prototype Chain

Quando um método está na [prototype
chain](https://developer.mozilla.org/en/docs/Web/JavaScript/Inheritance_and_the_prototype_chain)
de um objeto, o **this** desse método vai se referir ao objeto que o está
chamando, mesmo se o método não estiver definido nesse objeto:

<script src="https://gist.github.com/matheusml/07faf7ed32fd8fd68a1d.js"></script>

### Qual a importância?

O **this** é um dos maiores responsáveis por erros para quem está iniciando com
o JavaScript. Portanto entender como ele funciona é de extrema importância para
quem quer dominar a linguagem e gerar menos *bugs*.

## 4) Bind

Agora que já entendemos o **this** em JavaScript e os métodos **call** e
**apply**, podemos estudar o método **bind**.

O **bind** é muito semelhante ao **call** e **apply**: serve para passarmos um
contexto para uma função, que não é dela, e podermos executá-la. A diferença é
que **call** e **apply** invocam a função imediatamente:

<script src="https://gist.github.com/matheusml/e45a44cd1ea340264912.js"></script>

Enquanto **bind** retorna uma nova função que quando for executada terá o
contexto que passamos.

<script src="https://gist.github.com/matheusml/c905cfc649b095401b38.js"></script>

É comum usarmos o **bind** para o disparo de eventos:

<script src="https://gist.github.com/matheusml/a93496610a8dee6aade4.js"></script>

E também no mundo [React](https://facebook.github.io/react/):

<script src="https://gist.github.com/matheusml/e2e97b8c8a43b3c7544e.js"></script>

### Qual a importância?

Basicamente a mesma de **apply** e **call**.

## 5) Map, Filter e Reduce

Você provavelmente já passou por alguma situação em que era necessário por
exemplo iterar sobre um *array*, ou então verificar se existe alguma propriedade
nele ou mesmo simplesmente gerar um novo *array* com base no primeiro. Os
métodos **map**, **filter** e **reduce** nos ajudam nessas situações além de
começarmos a pensar mais em termos de [programação
funcional](https://www.smashingmagazine.com/2014/07/dont-be-scared-of-functional-programming/).

**Map:**Dado um *array* qualquer, como podemos fazer para transformá-lo, ou
**mapeá-lo**, em um outro *array*? <br> Existe a forma difícil (sem **map**):

<script src="https://gist.github.com/matheusml/ecb414a87416d65bc337.js"></script>

E existe a forma fácil (com **map**):

<script src="https://gist.github.com/matheusml/860de591a3acf1db5393.js"></script>

**Filter:**Dado o mesmo *array*, como podemos gerar um novo **filtrando** apenas
os 6 primeiros meses do ano?

Com o **filter** é bem fácil fazer isso:

<script src="https://gist.github.com/matheusml/8ffffb079dd613183414.js"></script>

**Reduce**:<br> Dado o *array* de meses que temos trabalhado até então, como
podemos fazer para gerar uma acumulação de valores, ou **reduzi-lo**, em algum
valor específico?

Com o **reduce** seria mais ou menos assim:

<script src="https://gist.github.com/matheusml/3880ac0df6e0ffe822b1.js"></script>

Pra quem conhece o [Redux](https://github.com/rackt/redux) (um *state container*
muito comum em aplicações que usam o React), uma curiosidade é que a ideia dele
está basicamente resumida na ideia de uma função **reduce**: a [Reducer
Function](https://egghead.io/lessons/javascript-redux-the-reducer-function).

### Qual a importância?

Os métodos **map**, **filter** e **reduce** são a base da [programação
funcional](https://medium.com/@jugoncalves/functional-programming-should-be-your-1-priority-for-2015-47dd4641d6b9#.ly6e3wvpv)
não só em JavaScript, mas em diversas outras linguagens. E sem saber programação
funcional não há como tirar 100% de proveito de JavaScript e do seu ecossistema.

## 6) Prototype

A herança em JavaScript é feita através dos **prototypes**. Ela funciona de uma
maneira um pouco diferente da [herança
clássica](https://en.wikipedia.org/wiki/Inheritance_(object-oriented_programming)),
o que pode gerar um pouco de confusão mesmo para os mais desenvolvedores mais
experientes em JavaScript.

Podemos pensar em objetos em JavaScript como agregadores de propriedades
dinâmicas. E quando um objeto tenta acessar qualquer propriedade sua e não a
encontrar, ela procurará no seu **prototype**. E se não estiver lá, no
**prototype** de seu **prototype** até que a propriedade seja encontrada ou
então essa corrente, chamada de [Prototype
Chain](https://stackoverflow.com/questions/11288660/prototype-chain-in-javascript),
se acabe:

<script src="https://gist.github.com/matheusml/4dab8510c921a6ca7dc3.js"></script>

*Animal* consegue invocar o método *walk* porque o mesmo pertence a ele. *Dog*
também consegue invocar porque apesar do mesmo não pertencer a ele pertence a
seu **prototype**. No caso de *Airplane* porém, nem ele e nenhum **prototype**
seu encontrou o método walk até o fim da *Prototype Chain*.

### Qual a importância?

Um dos conceitos mais usados em qualquer linguagem de programação é a Herança e
com JavaScript ela é feita através do **Prototype**. Entender bem não apenas o
**Prototype** como também o *Prototype Chain* é fundamental para dominar o
JavaScript.

## 7) Hoisting

A tradução de *hoist* é içar, levantar ou suspender. E é isso que acontece em
JavaScript quando declaramos uma variável: ela é **levantada** até o topo do
escopo.

Qual o retorno da função abaixo?

<script src="https://gist.github.com/matheusml/68b8030a4f5369e7d714.js"></script>

As respostas mais comuns são 1 ou 2, mas a resposta correta é **undefined**. A
declaração de variáveis em JavaScript é *hoisted* (ou elevada), mas não sua
inicialização. Portanto o código acima é equivalente a esse:

<script src="https://gist.github.com/matheusml/30a433dadcbab3b0123a.js"></script>

Para evitar problemas inesperados, tente sempre declarar todas a variáveis no
topo do escopo, mesmo que você não as tenha inicializado ainda.<br> Ou então
atualize para o [ES6](https://es6-features.org/) e passe a usar as *keywords*
**let** e **const**. Elas funcionam da maneira esperada:

<script src="https://gist.github.com/matheusml/86568b95044477d25296.js"></script>

### Qual a importância?

Evitar futuros *bugs* ao entender uma das partes mais problemáticas da
linguagem.

## Para aprender mais

É difícil encontrar conteúdo bom e atualizado em português. Com isso em mente
criamos o [JSCasts](https://jscasts.teachable.com/), onde você vai se manter em
dia com o JavaScript e todo o seu ecossistema de forma fácil e interativa.

#### Cursos:

* [Começando com
React.js](https://jscasts.teachable.com/courses/comecando-com-react-js)
* [React.js com ES6](https://jscasts.teachable.com/courses/react-js-com-es6)


---

Esse artigo foi escrito originalmente no [canal do Tableless no Medium](https://medium.com/tableless)!