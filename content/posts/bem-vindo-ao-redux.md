---
title: Introdução ao Redux
author: Henrique Sosa
type: post
date: 2016-04-04
excerpt: 'Uma breve explicação sobre a arquitetura Redux e suas principais características '
url: /bem-vindo-ao-redux/
titulo_personalizado:
  - 'Redux: um container de estados para <strong>aplicações JavaScript</strong>'
categories:
  - Código
  - Destaques
  - JavaScript
  - ReactJS
  - Técnicas e Práticas
tags:
  - arquitetura
  - elm
  - flux
  - JavaScript
  - react
  - redux

---
## Introdução

**[Redux][1]** é uma maneira de pensar o desenvolvimento de aplicações criada pelo <a href="https://twitter.com/dan_abramov" target="_blank">@dan_abramov</a> que teve como principio optimizar a ideia do <a href="https://facebook.github.io/flux/" target="_blank">Flux</a>. Ela foi criada para tentar optimizar alguns obstáculos que o Flux começou a enfrentar, e também veio para simplificar a implementação do mesmo. Inspirada em conceitos da linguagem funcional <a href="http://elm-lang.org/" target="_blank">Elm</a>, e de algumas bibliotecas JS como o <a href="https://facebook.github.io/immutable-js/" target="_blank">Immutable.js</a>,  o <a href="https://github.com/Yomguithereal/baobab" target="_blank">Baobab</a>, o  <a href="https://github.com/Reactive-Extensions/RxJS" target="_blank">RxJs</a> e o próprio Flux, o Redux veio com alguns paradigmas interessantes e um pouco diferenciados do Flux.

## Triforce do Redux

O Redux é composto de três princípios que formam e definem o seu conceito. Eles são:

  1. **Um único ponto de verdade** &#8211; Todo o estado da aplicação é mantido em apenas um único objeto chamado de Store.
  2. **O estado é imutável** &#8211; O estado da aplicação é inalterável, a unica maneira de afeta-lo é emitindo uma Action com a mudança.
  3. **Mudanças são feitas apenas por funções puras** &#8211; Reducers recebem as Actions emitidas e aplicam-nas ao estado. Sempre retornando um novo estado.

Agora com os princípios estabelecidos, vamos entender o que significa cada uma dessas parte da arquitetura.

## O que é Estado

Quando se trata de aplicações reativas, ouvimos muito falar do tal estado (ou **state** em inglês), mas nem todo mundo consegue assimilar de fato o que ele representa na aplicação.

**Estado** é ser considerado _o conjunto de dados mantidos no momento em que sua aplicação está rodando no lado do cliente_. Qualquer atualização que envolva alteração desses dados, automaticamente essa mudança irá alterar o estado.

## Views

Views são os arquivos finais mostrados para o usuário, na maior parte dos frameworks views são todos os arquivos HTML renderizados pelo Browser, no caso do React em especifico,  as views são consideradas componentes React, onde o contexto é renderizado através da função `render()`.

## Actions

Actions (ou ações) são objetos que servem para transmitir o que será enviado de sua view para sua store.

Actions possuem obrigatoriamente uma propriedade **type** que indica o tipo de ação que será executada,  e que por sua vez devem ser escritas sempre como constantes.

<pre class="lang-javascript">{
 type: 'ENVIAR_MENSAGEM',
 text: 'Olá Redux'
}
</pre>

Neste caso estou criando uma action que será do tipo `ENVIAR_MENSAGEM e `a propriedade **text** é apenas um parâmetro que ela irá transmitir para a store.

## Reducers

Actions descrevem de fato que algo aconteceu e o papel dos Reducers é transmitir o que aconteceu para alterar devidamente sua store

<pre class="lang-javascript">let initialState = {
  mensagem: 'Olá Mundo'
}

function olaMundo(state = initialState, action) {
  switch (action.type) {
    case ENVIAR_MENSAGEM:
      return Object.assign({}, state, {
        mensagem: action.text
      })
    
    case APAGAR_MENSAGEM:
      return Object.assign({}, state, {
        mensagem: ''
      })
    
    default:
      return state
  }
}
</pre>

Vamos analisar o código acima:

Primeiro gostaria de avisar que estou implementando usando ES2015, então sugiro para quem ainda não experimentou, de uma olhada <a href="https://babeljs.io/docs/learn-es2015/" target="_blank">neste link</a> que é uma referência bem bacana sobre o que mudou.

Em primeiro lugar eu declarei o estado inicial da aplicação com uma propriedade `mensagem` e disse que seu valor é **Olá Mundo**

Criei uma função chamada de **olaMundo** com dois parâmetros (state que já declarado como meu estado inicial e a action que foi emitida para acionar este reducer) e nela que está a mágica. Note que ela possui um `switch` com duas condições, explicarei apenas a primeira, pois as duas basicamente tem o mesmo resultado.

Quando a Ação `ENVIAR_MENSAGEM` é emitida para este reducer, ele irá atribuir o valor que a action transmiti ao estado e a função `Object.Assign()` será responsável por criar a cópia do estado e envia-lo à store.

## Store

Além de manter o estado da aplicação como já falado antes. A Store também tem algumas outras responsabilidades, são Elas:

  * Permitir a leitura do estado através do método `getState()`;
  * Permitir que o estado seja alterado pelos **Reducers**;
  * Registrar **Listeners** para escutar o estado à partir do método `subscribe(listener)`;
  * Manipular os **Listeners** registrados.

## 

## Migrando Para o Redux

Como é dito na própria documentação oficial do Redux, ele nao é algo que te deixará preso e impossibilitado de mudar, mas claro, caso queira adota-lo, algumas tomadas de decisões terão de ser feitas.

> Redux is not a monolithic framework

O Redux também é uma maneira de se pensar, note que todos os passos que eu mostrei não são exclusivos do React, ou do Angular por exemplo, a biblioteca em si foi documentada usando o React, mas nada te impede de implementar a ideia em qualquer outro Framework como o Angular.

E para quem usa o Backbone também existe uma lib citada pelo próprio Redux para você que queira fazer a migração.

## Conclusão

Lembrando que o Redux não é de forma alguma um concorrente do Flux, ou das outras implementações do mesmo. E que esse post é apenas uma breve introdução ao assunto. Deixei alguns links interessantes nas referencias para quem possam começar ou continuar a estudar Redux.

### Para ler mais

Um ótimo exemplo para entender mais sobre o que eu escrevi acima pode ser encontrado em <a href="https://github.com/reactjs/redux/tree/master/examples/todomvc" target="_blank">aqui</a>;

A documentação completa pode ser vista através <a href="http://redux.js.org/" target="_blank">deste link</a>;

E caso tenha lido o post sobre <a href="http://tableless.com.br/introducao-ao-electron/" target="_blank">Electron.js</a> e queira iniciar o desenvolvimento de aplicações Desktop usando React + Redux aqui esta o <a href="https://github.com/henriquesosa/electron-intro" target="_blank">repositório</a> que criei com uma breve introdução ao assunto.

<a href="https://github.com/redbooth/backbone-redux" target="_blank">Migração do Backbone.</a>

<a href="https://github.com/wbuchwalter/ng-redux" target="_blank">Migrando o Angular.js para Redux.</a>

 [1]: http://redux.js.org/docs/introduction/index.html