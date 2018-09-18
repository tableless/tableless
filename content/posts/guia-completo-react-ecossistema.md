---
title: O Guia Completo do React e o seu Ecossistema
authors: Matheus Lima
type: post
date: 2017-07-18
excerpt: Você ouve falar frequentemente sobre o React mas sabe pouco sobre ele?
categories:
  - javascript
tags:
  - reactjs
  - nodejs
image: https://i.imgur.com/FBXy8M5.png
---

Você já até estudou um pouco sobre a biblioteca desenvolvida pelo Facebook mas
quer consolidar os seus conhecimentos?

Então esse *post* é pra você. Continue lendo para aprender:

* O porquê do React
* Como começar uma aplicação com React
* Pra quê serve o JSX
* O que é Virtual DOM
* Como funciona o *lifecycle* dos componentes React
* A Era da Componentização
* *One-way data binding*
* Flux, Redux ou MobX
* O que usar para criar testes unitários com React

*****

## Introdução

Para começar precisamos saber o que é o React. Para isso, nada melhor do que
utilizar a definição de quem o criou, o próprio Facebook, que o define assim:

> Uma biblioteca JavaScript declarativa, eficiente e flexível para criar
> interfaces visuais

Com isso, temos que:

1.  O React não é um *framework*, mas uma biblioteca (*library*).
1.  O React serve para criar interfaces visuais
([UI](https://en.wikipedia.org/wiki/User_interface)).

Essas duas informações juntas criam a primeira grande confusão para quem está
começando: se o React é apenas uma biblioteca e só serve para criar UI, como
posso criar aplicações completas com ele?

E para resolver essa questão precisamos entender que quando a comunidade se
refere ao React, o que na verdade ela está querendo dizer é o **React e o seu
ecossistema.** <br> E esse ecossistema é formado por:

* React
* JSX
* ES2015
* Webpack
* Flux/Redux
* axios/fetch
* Jest/Mocha

E com todos esses itens, que fazem parte do ecossistema do React, conseguimos
afirmar que é possível sim criar aplicações completas usando o React.

## JSX

Explicando de forma rápida, o JSX é uma extensão de sintaxe do JavaScript (daí o
nome, **J**avaScript **S**yntax e**X**tension) que nos permite escrever HTML
dentro do JavaScript.

Nos primórdios, o JSX era um dos grandes motivos das críticas e piadas em
relação ao React. Em teoria estávamos voltamos no tempo ao misturar HTML com
JavaScript.

Os críticos mais ferrenhos afirmavam que o JSX quebra um dos princípios básicos
do desenvolvimento de software, que é o [Separation of
Concerns](https://deviq.com/separation-of-concerns/).<br> Na minha opinião, essa
visão é errada por dois motivos:

1.  O React em si, a biblioteca e não o ecossistema, como já falei anteriormente,
representa apenas a parte da *view* da sua aplicação. Portanto, por definição,
ele tem apenas um *concern*: renderizar a UI. Então quais *concerns* estão sendo
violados?
1.  E mesmo que o JSX violasse esse princípio, a área de tecnologia evolui (e muito)
com o tempo. **Se um dos princípios que nós sempre demos como verdade não fizer
mais sentido para um determinado cenário, deveremos nos forçar a seguir esse
princípio mesmo assim?**

Independente das minhas opiniões pessoais, com o tempo a comunidade percebeu que
o [JSX foi uma decisão
acertada](https://facebook.github.io/react/docs/introducing-jsx.html) e que
acabou se tornando um dos grandes alicerces do sucesso do React.

## Componentes

Como foi dito anteriormente, o React tem como função principal auxiliar na
criação da UI. Só deixei um detalhe importante de fora: o React usa
[componentes](https://facebook.github.io/react/docs/react-component.html), e
apenas componentes, para que que seja possível aumentar o máximo do reuso na sua
aplicação.

Para exemplificar, vamos ver um pouco de código para entender como é um
componente React:

<script src="https://gist.github.com/matheusml/52be228500e15b50dff0cadea2cbd003.js"></script>

A função acima (sim, componentes React podem ser simplesmente funções em
JavaScript) gera um botão que mostra um *alert* para o usuário ao ser clicado.

Se precisarmos de outro botão como esse, basta reaproveitá-lo sem a necessidade
de adicionar mais código na aplicação. **Lembrando que mais código é sinônimo de
mais trabalho, mais testes unitários e mais potenciais bugs inseridos.**

E se a necessidade for um botão parecido com esse, basta editarmos passando
alguns parâmetros (vamos falar mais sobre eles na próxima seção) e transformá-lo
no que precisamos.

Se houver algum *bug* no comportamento, ou mesmo no layout do botão, sabemos
exatamente onde devemos mexer no código para fazer o conserto rápido.

Em resumo, [os componentes em React nos deixam mais
produtivos](https://medium.com/tableless/organizando-uma-aplicaÃ§Ã£o-com-react-5b8ea9075596#.301wpiqdz).
Com eles temos um **reaproveitamento de código maior** e uma **menor
probabilidade de novos bugs serem introduzidos na aplicação**.

## Props

Em todos os tipos de paradigmas no desenvolvimento de *software*, passar
parâmetros é extremamente comum. Com os componentes do React isso não poderia
ser diferente. A diferença é que no React, usamos os
[props](https://facebook.github.io/react/docs/components-and-props.html)
(abreviação para *properties*).

A ideia é simples.

O componente abaixo, mostra para o usuário um Hello World:

<script src="https://gist.github.com/matheusml/6f6fdbd9b74135890a983be0c5cded6c.js"></script>

Imaginando que precisamos mudar a mensagem ‘World’ para alguma outra que for
enviada dinamicamente, podemos reescrever esse componente usando as *props*
dessa forma:

<script src="https://gist.github.com/matheusml/22bcb152e0d2a1b485a426f76617df16.js"></script>

E com isso feito, podemos chamar esse componente dentro de outros assim:

<script src="https://gist.github.com/matheusml/acd5f80e2c61e8b69c29c657df623e90.js"></script>

Além disso, podemos fazer uma validação das *props* que são passadas no
componente para evitar *bugs* desnecessários e facilitar no desenvolvimento da
aplicação usando os [PropTypes](https://www.npmjs.com/package/prop-types):

<script src="https://gist.github.com/matheusml/3caa03e8db5cb9f57e58043cda500141.js"></script>

Agora, informamos explicitamente ao React para apenas aceitar a *prop* quando
ela for uma *string*. Se qualquer outra coisa for passada para esse componente,
a aplicação irá falhar e receberemos uma mensagem de erro nos avisando o porquê.

Para ler mais sobre os PropTypes, entre na [documentação completa na própria
página do
React](https://facebook.github.io/react/docs/typechecking-with-proptypes.html).

Outras possibilidades para lidar com os PropTypes são: o
[Flow](https://flow.org/) e o [TypeScript](https://www.typescriptlang.org/).

## State

O estado (ou *state*) da sua aplicação, pode ser definido como: o lugar onde os
dados vem e se transformam ao longo do tempo.

Dito isso, os componentes React podem ser divididos em duas categorias:
[Presentational e
Container](https://medium.com/@dan_abramov/smart-and-dumb-components-7ca2f9a7c7d0).
Outra nomenclatura usada na comunidade para esses dois é: Stateless (sem estado)
e Stateful (com estado).

Os componentes do tipo Presentational, se importam somente com a apresentação
dos dados, portanto não tem estado (*stateless*).<br> Eles podem ser escritos
como uma simples função:

<script src="https://gist.github.com/matheusml/c46d1f293ba33bd84e140e54d7fb5c7f.js"></script>

O ideal é escrever o máximo possível de componentes dessa categoria. Eles são
mais fáceis de desenvolver, manter e testar.

Já os componentes do tipo Container, além da apresentação dos dados, tem que
lidar também com algum tipo de lógica, ou transformação de dados. Por isso
necessitam de estado (*stateful*). <br> Esses componentes não podem ser escritos
como uma função, eles obrigatoriamente devem ser uma classe:

<script src="https://gist.github.com/matheusml/2930942224cbd4723798d33dfffe800a.js"></script>

Os dois exemplos mostrados acima tem exatamente o mesmo resultado final. A única
diferença é que o primeiro deles não usa o [state do
React](https://facebook.github.io/react/docs/state-and-lifecycle.html), enquanto
que o segundo usa.

Podemos ainda complicar um pouco mais o segundo exemplo, para demonstrar como é
possível alterar o estado do seu componente React:

<script src="https://gist.github.com/matheusml/ad61ee3a0c8631f7f6e11484b99c3ecb.js"></script>

Em cada mudança que ocorrer no *input* (linha 16), um evento é disparado na
função *change*. A função *change* por sua vez altera o estado do componente,
usando a função
[setState](https://facebook.github.io/react/docs/state-and-lifecycle.html), que
é nativa do React.

Toda vez que o estado for alterado, o React automaticamente invoca de novo a
função *render*, que irá renderizar a UI com os novos dados *inputados* pelo
usuário.

## One-way data binding

É bem mais fácil falar dos benefícios do [one-way data
binding](https://facebook.github.io/react/docs/thinking-in-react.html) (ou
*one-way data flow*), demonstrando o fracasso do seu “concorrente”, o *two-way
data binding*.

O [Angular.js](https://angularjs.org/) ganhou bastantes usuários, principalmente
entre 2012 e 2015, e um dos principais motivos para isso, era justamente o
*two-way data binding*.

![https://docs.angularjs.org/guide/databinding](https://cdn-images-1.medium.com/max/800/1*hR_vXH3eYzS093z33CO0RQ.png)

O *two-way data binding *funciona assim: se uma mudança acontece na *view*, ela
é refletida automaticamente no *model*, e vice-versa.

No começo, o *two-way data binding* parecia uma excelente ideia. Com o tempo,
após inúmeros projetos construídos usando essa tecnologia, ela se mostrou
extremamente nociva principalmente por dois motivos:

1.  [Performance](https://stackoverflow.com/questions/35379515/why-is-two-way-databinding-in-angularjs-an-antipattern)
1.  [Manter aplicações grandes se mostrou extremamente
difícil](https://www.quora.com/Why-is-the-two-way-data-binding-being-dropped-in-Angular-2)

A própria equipe do Angular resolveu limitar essa funcionalidade nas novas
versões do* framework*.

O React porém, percebeu essa falha desde o início e estimula apenas o uso do
*one-way data binding*.

Não existe um mecanismo no React que permita com que o HTML altere os dados do
componente. E nem vice-versa. Essa mudança é sempre feita de forma explícita
pelo desenvolvedor. **Lembrando que explícito é muito melhor, em termos de
desenvolvimento, manutenção e testes, do que implícito.**

Um exemplo simples de *one-way data binding* em ação no React pode ser visto no
componente abaixo:

<script src="https://gist.github.com/matheusml/8a4a053697f7147e71e40b365434e1a3.js"></script>

Se estivéssemos no mundo *two-way data binding* do Angular.js, o *model* e a
*view* estariam conectados **implicitamente** e ambos mudariam juntos.

Porém, com o *one-way data binding* do React, precisamos **explicitamente**
invocar a função *setState* para que o estado seja alterado. Dessa forma temos
muito mais previsibilidade e segurança da nossa aplicação.<br> Isso fica muito
evidente conforme a aplicação cresce.

## Lifecycle

Para que seja possível o desenvolvimento de componentes mais complexos, alguns
métodos foram adicionados na API dos componentes React.<br> Eles fazem parte do
[Component
Lifecycle](https://facebook.github.io/react/docs/react-component.html) (ciclo de
vida dos componentes).

Com esses métodos, os desenvolvedores podem saber, por exemplo, quando um
componente vai ser criado, destruído, atualizado, etc.

![](https://cdn-images-1.medium.com/max/800/1*smGro1UuhyqopVT4aEsIrA.png)

São esses os métodos de *lifecycle* dos componentes:

* [componentWillMount](https://facebook.github.io/react/docs/react-component.html#componentwillmount),
executado logo antes do primeiro *render*. Não é muito usado, geralmente faz
mais sentido simplesmente usar o próprio construtor da classe.
* [componentDidMount](https://facebook.github.io/react/docs/react-component.html#componentdidmount),
executado logo após o primeiro render. É provavelmente o método mais usado.
Alguns exemplos de casos de uso são: chamadas AJAX, manipulação do DOM, início
de *setTimeouts* e *setIntervals*, etc.
* [componentWillReceiveProps](https://facebook.github.io/react/docs/react-component.html#componentwillreceiveprops),
executado quando as *props* que o componente recebe são atualizadas. Geralmente
é usado quando os componentes precisam reagir aos eventos externos.
* [componentWillUpdate](https://facebook.github.io/react/docs/react-component.html#componentwillupdate),
é igual ao *componentWillMount*, só que ele executa logo antes da atualização de
um componente.
* [componentDidUpdate](https://facebook.github.io/react/docs/react-component.html#componentdidupdate),
é igual ao *componentDidMount*, só que ele executa logo depois da atualização de
um componente.
* [componentWillUnmount](https://facebook.github.io/react/docs/react-component.html#componentwillunmount),
executado quando o ciclo de vida de um componente termina e ele vai ser removido
do DOM. É muito usado para remover *setTimeouts* e *setIntervals* que foram
adicionados.
* [shouldComponentUpdate](https://facebook.github.io/react/docs/react-component.html#shouldcomponentupdate),
deve retornar *true/false*. Esse valor vai dizer que se o componente deve ser
atualizado ou não, com base em certos parâmetros. Geralmente é usado para
resolver questões de performance.

Um exemplo simples de uso dos métodos de *lifecycle*, seria o contador de
segundos abaixo:

<script src="https://gist.github.com/matheusml/cade81d8762f98cff962c1eeb0a9acce.js"></script>

Assim que o componente é montado (*componentDidMount*), nós iniciamos o
*setInterval* que a cada 1000ms invoca a função *tick*. E quando o componente
for destruído (*componentWillUnmount*) removemos o *setInterval* para que a
função *tick* não continue sendo chamada desnecessariamente.

## Virtual DOM

A manipulação do
[DOM](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Introduction)
está no centro do desenvolvimento *front-end* moderno. Fazemos isso basicamente
todos os dias.<br> Só tem dois problemas com isso:

1.  Essa manipulação direta do DOM é mais lenta do que a maioria das operações
feitas pelo JavaScript
1.  A maioria dos *frameworks* JavaScript alteram muito mais o DOM do que deveriam

Sabendo disso, o Facebook criou o [Virtual
DOM](https://facebook.github.io/react/docs/reconciliation.html).<br> Ele
funciona da seguinte forma: no React, uma cópia de todos os *nodes* do DOM são
replicados em código JavaScript. Ao invés de fazer alterações diretamente no DOM
(que são lentas) elas são feitas no Virtual DOM (rápidas). E somente quando
realmente necessário, essas alterações são repassadas para o DOM original.

Esse é um dos principais motivos para os *benchmarks* de performance excelentes
que o React tem.

![](https://cdn-images-1.medium.com/max/800/1*FRj5ljLvQ-p7vu0gol4PmA.jpeg)

Agora que já entendemos as partes fundamentais do React, precisamos entender
também o seu ecossistema.

*****

## create-react-app

Nos primeiros anos do React, uma das principais críticas era de que iniciar uma
aplicação era muito mais complicado do que deveria ser, o que acabava excluindo
diversos iniciantes.

Antes de sequer começar a primeira linha de código em React, os desenvolvedores
precisavam aprender no mínimo: Webpack e ES2015.

Hoje isso não é mais um problema, a equipe do Facebook vem trabalhando
diariamente no projeto
[create-react-app](https://github.com/facebookincubator/create-react-app).

Agora, com apenas 4 simples comandos, sem ter que criar e editar nenhuma
configuração, temos um arcabouço completo para começar a desenvolver aplicações
em React:

    npm install -g create-react-app
    create-react-app my-app
    cd my-app/
    npm start

## CSS-in-JS

Todas as boas práticas ao se escrever CSS apontavam para um mesmo caminho por
anos: escrever CSS o mais desacoplado possível do JavaScript e do HTML, usando
nomes bem descritivos para as classes.

**O problema dessa abordagem é que ela não resolve o maior defeito do CSS: tudo
o que você cria é global.** Cada vez que você cria uma nova classe CSS ela é,
por definição, global. Isso gera diversos problemas na manutenção,
principalmente em aplicações maiores.

Com o grande sucesso da componentização no React, a forma de se escrever CSS vem
mudando drasticamente.

A primeira revolução veio com o [CSS Modules](https://github.com/css-modules).

<script src="https://gist.github.com/matheusml/ea2e23524d8bcc5bcdca8c9518c19697.js"></script>

A ideia é simples: escrever o mesmo CSS de sempre, só com uma diferença: esse
CSS só vai valer para aquele componente. Ou seja, será um módulo (daí o nome,
CSS Modules).

Um exemplo simples de uso do CSS Modules:

<script src="https://gist.github.com/matheusml/47059d2fea8f3bcdf3dace41d3016364.js"></script>

E o arquivo de estilos que só valerá para o componente acima:

A segunda revolução veio com o
[styled-components](https://github.com/styled-components/styled-components).

Nesse, o próprio componente já teria seus estilos escritos em JavaScript, sem
que nenhum arquivo CSS seja sequer criado.

Uma das vantagens do *styled-components*, é que o *code-splitting* fica muito
mais fácil de ser feito, e assim como o CSS Modules, não existe CSS global. A
desvantagem é que você não escreve o CSS padrão que muitos já estão acostumados,
o que pode não ser muito intuitivo.

Um exemplo simples:

<script src="https://gist.github.com/matheusml/080d054bc5ab29c6ffec80959af5a453.js"></script>

## Bundlers

Resolver dependências no *front-end*, apesar de ser uma questão comum, sempre
foi extremamente problemático.<br>  <br> Na maioria dos projetos temos que
lidar, no mínimo, com essas questões:

* A concatenação e minificação do JavaScript (ou TypeScript, ES2015, CoffeScript,
etc) e do CSS (ou Sass, Less, Stylus, etc)
* Inclusão de Imagens
* Adição de Fontes

Dessa necessidade frequente das aplicações* front-end*, surgiram os *module
bundlers*. E no mundo React, o *bundler* mais usado pela comunidade é o
[Webpack](https://webpack.js.org/guides/).

![](https://cdn-images-1.medium.com/max/800/1*BxSBCuP7IRFz4pZCSVBxlQ.png)

Além de resolver todos os problemas acima (imagens, fontes e a
minificação/concatenação de JavaScript e CSS), o Webpack também consegue prover:

* [Caching](https://webpack.js.org/guides/caching/)
* [Code Splitting](https://webpack.js.org/guides/code-splitting/) (entrar código
sob demanda)
* [Tree Shaking](https://webpack.js.org/guides/tree-shaking/) (eliminação de
código não usado)
* [Hot Module Replacement](https://webpack.js.org/guides/hot-module-replacement/)
(após salvar o código novo, ele já aparece no *browser* em ambiente de
desenvolvimento sem a necessidade de *refresh*)

Além de outras *features* também muito interessantes.

## State containers

Para aplicações mais complexas usar apenas o *setState* nativo do React pode não
ser o suficiente para controlar toda a lógica da aplicação.

Existem diversos gerenciadores de estado feitos exclusivamente para lidar com
esse problema, dentre eles: [Flux](https://facebook.github.io/flux/),
[MobX](https://github.com/mobxjs/mobx),
[Reflux](https://github.com/reflux/refluxjs) e o mais famoso deles, o
[Redux](https://redux.js.org/).

![](https://cdn-images-1.medium.com/max/800/1*tOI6UC5EaS2fPItCesI-AQ.png)

Dito isso, **toda vez que tivermos que tomar uma decisão de se adicionar uma
nova biblioteca no projeto, temos que pesar o custo/benefício dessa decisão. **E
para a grande maioria das aplicações, que não são complexas o bastante, nenhuma
das opções acima (inclusive o Redux) são necessárias.

Me preocupa ver na comunidade, diversos iniciantes começando a aprender o Redux
antes mesmo de entender bem o próprio React. Ou mesmo criando projetos já com o
Redux, sem antes ter visto se há de fato uma necessidade.

O próprio criador do Redux já falou sobre isso:

<blockquote class="twitter-tweet" data-lang="en"><p lang="en" dir="ltr">Good thread. Don’t use Redux unless you *tried* local component state and were dissatisfied. <a href="https://t.co/MR3XWsdhd1">https://t.co/MR3XWsdhd1</a></p>&mdash; Dan Abramov (@dan_abramov) <a href="https://twitter.com/dan_abramov/status/725089243836588032">April 26, 2016</a></blockquote> <script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>


## Testes

Outro ponto crucial para o desenvolvimento de aplicações *web* é o uso de testes
unitários. As garantias de que os testes nos dão são consideráveis. Podemos
refatorar, encontrar e evitar novos *bugs*, e até mesmo para escrever código a
partir dos testes (TDD).

No mundo React, a principal ferramenta para escrever testes unitários é o
[Jest](https://facebook.github.io/jest/), que é mais um *open source* do
Facebook.

![](https://cdn-images-1.medium.com/max/800/1*Q26gw-kNzOXUqZKRr04T-g.png)

O Jest tem três vantagens principais em relação aos concorrentes:

1.  É extremamente [fácil de
configurar](https://facebook.github.io/jest/docs/en/getting-started.html)
1.  Ele vem com tudo o que você precisa para testar: o *runner*, as *assertions*, o
*report* de *coverage*, etc. Não é mais necessário instalar diversas bibliotecas
diferentes para poder escrever testes unitários.
1.  [Snapshots](https://facebook.github.io/jest/docs/en/snapshot-testing.html#content)

Esse último é tão interessante que vale a pena se aprofundar um pouco mais.<br>
A ideia das Snapshots é simples: o Jest tira uma “foto” do seu componente, e se
algo mudar o seu teste vai quebrar e te avisar dessa mudança, mostrando
exatamente como o componente era e como ele ficou.

E isso tudo com pouquíssimas linhas de código:

<script src="https://gist.github.com/matheusml/532341e28eb603ccfed64515f830fb6d.js"></script>

*****

## Conclusão

E pra recapitular, nesse *post* aprendemos as partes mais centrais do React
como: JSX, Virtual DOM, *Lifecycle*, Componentização, *One-way data binding*,
etc.

E além disso, conhecemos também os principais atores que fazem parte do
ecossistema do React, dentre eles: Webpack, create-react-app, Jest, CSS Modules,
etc.

Mas se mesmo assim ficou alguma dúvida, basta adicionar a pergunta nos
comentários abaixo :)

*****

**Se você gostou do post não se esqueça de dar um ❤ aqui embaixo!E se quiser
receber de antemão mais posts como esse, **[assine nossa newsletter](https://eepurl.com/bHZHC1)**.**

*Seja um apoiador, doe BitCoins: 1BGVKwjwQxkr3w1Md2X8WHAsyRjDjyJiPZ*

![](https://cdn-images-1.medium.com/max/800/1*zdKxCoB-FLTRpfYqjdNcqA.png)

### JSCasts

É difícil encontrar conteúdo bom e atualizado em português. Com isso em mente
criamos o [JSCasts](https://jscasts.teachable.com/), onde você vai se manter em
dia com o JavaScript e todo o seu ecossistema de forma fácil e interativa.

![](https://cdn-images-1.medium.com/max/800/1*hUoaRpFtnMdWTE8Vo-5lIA.png)

### Cursos:

- [Começando com React.js](https://jscasts.teachable.com/courses/comecando-com-react-js)
- [React.js com ES6](https://jscasts.teachable.com/courses/react-js-com-es6)

*Obrigado por ler! ❤*