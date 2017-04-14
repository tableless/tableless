---
title: ReactJS 101
author: Bruno Belarmino
type: post
date: 2016-05-07
excerpt: Uma introdução a biblioteca para criação de interfaces do Facebook
url: /reactjs-101/
categories:
  - Código
  - JavaScript
  - ReactJS
  - Tecnologia e Tendências
tags:
  - bibliotecas javascript
  - JavaScript
  - js
  - react.js
  - reactjs

---
#### TL;DR

ReactJS é a biblioteca criada pelo Facebook para criação de interfaces. Pensando no mundo **MV*** qual vivenciamos hoje, este seria o **V** (view).

Através de uma api simples qual previlegia o uso do javascript e com uma performance acima da apresentada pelos seus concorrentes, o ReactJS vem ganhando cada dia mais adeptos.

#### Building Blocks

Fortemente inspirado pelo conceito de componentes, trazendo duas grandes características que o desenvolvedor deve se concentrar: _Components_ e_Elements_.

##### Components

É o template para criação de elementos. Fazendo um paralelo com a web atual, exemplos de components são _div_, _button_, _label_ entre outros.

##### Elements

_Element_ é a instância de um _component_. Por exemplo quando inserimos um _button_ em uma página HTML, este elemento é a materialização/instância de um componente no DOM.

Complicado?

Vamos ver como funciona na prática:

<pre class="lang-js">//cria elemento
var customDiv = React.createElement('div');

//renderiza elemento
ReactDOM.render(customDiv, document.getElementById('container'));
</pre>

O código acima cria um _element_ baseado no _component_ `div` e renderiza o mesmo no DOM.

Legal! Mas usar diretamente o HTML não é mais eficiente?
  
A resposta: normalmente não.

E eis que lhes apresento o _Virtual DOM_.

#### Virtual DOM

Como todos sabem a manipulação de DOM além de não ser uma das coisas mais simples no mundo web, ainda tem um grande impacto na performance de nossas aplicações.

E com isso em mente os engenheiros do facebook/instagram criaram o _virtual DOM_ que na prática é a representação do DOM em memória. Deste modo, todos os _elements_ que criamos utilizando React.createElement são criados e mantidos nesse ambiente virtual antes de serem renderizados no DOM original.

A mágica acontece de verdade nas atualizações. Imagine o seguinte cenário: numa tela HTML temos um campo de texto do tipo numeric e um botão de adicionar. Toda vez que clicamos no botão adiciona em 1 o valor do campo de texto.

Uma atividade super simples como adicionar um handler para o evento de click do botão e dentro do handler pegar o campo de texto através da api de DOM e somar 1 ao value do mesmo. Tudo lindo, mas tem alguns problemas:

  1. adicionar e manter event handlers nos _elements_ do DOM consomem bastante memória.
  2. modificar o conteúdo da página gera reflow (nova renderização do _element_modificado e seus filhos).

Agora imagine tudo isso acontecendo em uma página com centenas ou talvez milhares de _elements_ no DOM. Não é uma experiência muito boa.

Com o _virtual DOM_ esses problemas são minimizados com a técnica conhecida como &#8220;o menos é mais&#8221;, ou seja, toda vez que algo é alterado nos _elements_ que foram criados através do método React.createElement. O ReactJS renderiza esse conteúdo no _virtual DOM_ e através de um algoritmo super otimizado calcula a diferença entre o DOM atual e o DOM com as alterações e são essas diferenças que são renderizadas no DOM original. E desta forma causa o mínimo de impacto possível fazendo com que nossas páginas estejam sempre responsivas e rápidas para o usuário.

#### Conclusão

ReactJS é uma nova opção para criação de interfaces focada na simplidade de desenvolvimento e alta performance. Com baixo consumo de memória e um gerenciamento eficiente do DOM esta biblioteca vem ganhando o mundo.

Por hoje é isso!
  
Espero que tenham gostado dessa introdução e até a próxima!

##### Links de referência:

&#8211; <a href="https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Introduction" target="_blank">DOM (Document Object Model)</a>
  
&#8211; <a href="https://developers.google.com/speed/articles/reflow" target="_blank">Reflow</a>
  
&#8211; <a href="https://facebook.github.io/react/docs/getting-started.html" target="_blank">ReactJS</a>