---
title: Entendendo o DOM (Document Object Model)
authors: Leonardo Maldonado
type: post
image: https://i.imgur.com/y05YIAB.jpg
date: 2018-02-08
excerpt: O DOM explicado de uma maneira fácil.
categories:
  - Javascript
  - HTML
---


## Entendendo o DOM (Document Object Model)

Você estudou bastante HTML, criou suas primeiras tags, aprendeu CSS, fez formulários bonitos, botões incríveis, páginas responsivas e começou mostrar para todo mundo como aquilo é incrível, mas chega uma hora que você deseja dar um passo a mais no seu aprendizado e se pergunta: ”Mas como eu posso dar movimento a minha página? Queria tanto que aquele botão por exemplo mudasse algo nela!”. É aí que entra o DOM, algo que constantemente você ouve falar por aí, mas não sabe explicar ao certo o que é.

Sabe aquelas animações legais que você vê por aí e você fala “Uau, queria tanto fazer algo assim, mas como?”, elas são feitas manipulando o DOM (Document Object Model), e esse artigo vai te explicar do zero o que ele é e como manipulá-lo.

### Então, o que é o DOM?

O DOM (Document Object Model) é uma interface que representa como os documentos HTML e XML são lidos pelo seu browser. Após o browser ler seu documento HTML, ele cria um objeto que faz uma representação estruturada do seu documento e define meios de como essa estrutura pode ser acessada. Nós podemos acessar e manipular o DOM com JavaScript, é a forma mais fácil e usada.

### Quais as vantagens do DOM?

Com ele você tem infinitas possibilidades, você pode criar aplicações que atualizam os dados da página sem que seja necessário uma atualização. Pode também criar aplicações que são customizáveis pelo usuário, mudar o layout da página sem que seja necessário atualização. Arrastar, mover, excluir elementos. Ou seja, você tem infinitas possibilidades, milhares de coisas que você pode fazer manipulando o DOM, basta você usar sua criatividade.

### Como ele é representado pelo browser:

![](https://i.imgur.com/lu4PMfw.jpg)

A estrutura que o DOM constrói a partir da leitura do seu documento HTML.

Nessa imagem vemos a estrutura do DOM, suas marcações e como ele é montado pelo browser. Nessa base, temos 4 pontos importantes que você vai ver bastante daqui pra frente:

1. **Document: **que como o nome diz, cuida de documentos HTML.
2. **Elements: **são todas as tags que estão em arquivos HTML ou XML se transformam em elementos da árvore DOM.
3. **Texts**: É o texto que vai entre os elementos. Todo o conteúdo das tags.
4. **Attributes**: É a junção de todos atributos para um nó específico. No caso, o attribute _class=”hero”_ está apontando para o elemento ```<p>```.

### Manipulando o DOM

Agora vamos a parte mais legal de todas: manipular o DOM. Primeiramente, vamos criar um HTML como exemplo para mostrar como os métodos e os eventos funcionam.

O HTML:

```
  <!DOCTYPE html>
  <html lang="pt-br">
  <head>
      <meta charset="UTF-8">
      <meta name="viewport" content="width=device-width, initial-scale=1.0">
      <meta http-equiv="X-UA-Compatible" content="ie=edge">
      <title>Entendo o DOM (Document Object Model)</title>
  </head>
  <body>
      <div class="container">
          <h1><time>00:00:00</time></h1>
          <button id="start">Start</button>
          <button id="stop">Stop</button>
          <button id="reset">Reset</button>
      </div>
  </body>
  </html>
```

Bem simples, agora vamos aprender um pouco sobre os métodos do DOM, é com eles que vamos pegar nossos elementos e criar interatividade.

### Métodos

O DOM possui muitos métodos, são eles que fazem a ligação entre os nodes (elementos) e os eventos, algo que vou falar mais abaixo. Vou mostrar os métodos mais usados e pra quê eles servem também. Lembrando que existem vários, para todos os tipos e você pode ver todos [aqui](https://developer.mozilla.org/en-US/docs/Web/API/Document).

### getElementById()

Esse método retorna o elemento que estiver contendo o nome do ID passado. Como os IDs devem ser únicos, é um método muito útil para pegar apenas o elemento desejado.

```
  var myStart = document.getElementsById('start');
```

**myStart**: elemento específico que se equipara com o seletor passado.

**start**: seletor passado, caso não houvesse nenhum ele retornaria _null_.

### getElementsByClassName()

Esse método retorna um _HTMLCollection_ de todos elementos que estiverem contendo o nome da classe passada.

```
  var myContainer = document.getElementsByClassName('container');
```

**myContainer**: elemento específico que se equipara com o seletor passado.

**.container**: seletor passado, caso não houvesse nenhum ele retornaria _null_.

### getElementsByTagName()

Na mesma maneira do método acima, ele também retorna uma _HTMLCollection_ mas com uma diferença: esse método retorna todos elementos contendo a tag name passada.

```
  var buttons = document.getElementsByTagName('button');
```

**buttons**: elemento específico que se equipara com o seletor passado.

**button**: tag name passada.

### querySelector()

Retorna o primeiro elemento que se equipara ao seletor CSS passado. Lembrando que o seletor deve seguir a sintaxe CSS. Caso não tenha nenhum seletor, ele retornará _null. _

```
  var resetButton = document.querySelector('#reset');
```

**resetButton**: primeiro elemento que se equipara com o seletor passado. 

**#reset**: seletor passado, caso não houvesse nenhum ele retornaria _null_.

### querySelectorAll()

Muito igual ao querySelector(), mas ele tem apenas uma diferença: retorna todos elementos que se equiparam ao seletor CSS passado. O seletor também deve seguir a sintaxe CSS, caso não haja nenhum ele retornará _null_.

```
  var myButtons = document.querySelector('#buttons');
```

**myButtons**: elementos que se equiparam com o seletor passado.

**#buttons**: seletor passado, como nesse caso não há nenhum seletor com esse nome, ele retorna _null_.

Esses são apenas 3 métodos do DOM, existem vários e alguns são bastante usados, por exemplo o _createElement()_ que cria um novo elemento HTML usando o nome da da tag a ser criada, o setAttribute() que você pode setar novos atributos para elementos HTML e muitos outros.

Você pode encontrar todos [AQUI](https://developer.mozilla.org/en-US/docs/Web/API/Element) indo no canto esquerdo em _Methods_ . Recomendo fortemente que você veja alguns, porque há muitos métodos interessantes sem que nós nem saibamos da existência e que talvez um dia você precise usar.

Agora vamos falar um pouco sobre eventos, afinal sem eles não conseguimos criar interatividade nas nossas páginas.

### Events

Os elementos DOM além de possuirem métodos também possuem eventos. São eles que fazem a interatividades dos elementos no documento, mas não se engane: eventos também são métodos.

### click

Um dos mais usados é o click, quando o usuário clicar no elemento, ele realizará alguma ação.

```
  myStart.addEventListener('click', function(event) {

    // Faça algo aqui.

  }, false);
```

Os parâmetros do **addEventListener()** são:

1. O tipo de evento que você deseja (nesse exemplo eu usei o _‘click’_).
2. A função de callback
3. O _useCapture_ faz o evento se atrelar ao pai até chegar ao filho. Ele por padrão é _false_, mas caso você coloque-o como _true_, ele vai fazer o caminho contrário atrelando o elemento. Você quase sempre vai usá-lo como _false_.

### select

Esse evento serve para quando você quiser disparar algo quando o elemento for selecionado. Nesse caso apenas disparamos um simples _alert_.

```
  myStart.addEventListener('select', function(event) {

     alert('Elemento selecionado!');

  }, false);
```

Esses são uns dos mais usados, temos outros vários eventos que você pode usar, por exemplo, eventos de _drag & drop_, quando o usuário começar a arrastar um elemento você pode realizar uma ação, e quando ele soltá-lo você pode realizar outra.

### Percorrer elementos

Você consegue percorrer elementos pelo DOM, usando algumas propriedades que vamos ver agora. É possível retornar com elas: elementos, comentários, textos.

### .childNodes

Essa propriedade retorna uma _nodeList_ de filhos do elemento passado. Ela vai retornar textos, comentários e quebras de linhas também. Portanto muito cuidado ao usá-la

```
  var container = document.querySelector('.container');

  var getContainerChilds = container.childNodes;
```

### .firstChild

Essa propriedade retorna o primeiro filho do elemento passado.

```
  var container = document.querySelector('.container');

  var getFirstChild = container.firstChild;
```

### .nodeName

Essa propriedade retorna o name do elemento passado. Como no caso passamos uma div, ele irá nos retornar “_div_”.

```
  var container = document.querySelector('.container');

  var getName = container.nodeName;
```

### .nodeValue

Específico para textos e comentários, ele retorna o conteúdo do nó de texto ou comentário. Como passamos ele para uma _div_, ele irá nos retornar _null_.

```
  var container = document.querySelector('.container')

  var getValue = container.nodeValue;
```

### .nodeType

Essa propriedade nos retorna o tipo do elemento passado. Nesse caso ele retornaria ‘_1_'.

```
  var container = document.querySelector('.container')

  var getValue = container.nodeType;
```

Mas o que significa esse ‘_1_’? Ele simplesmente é o _nodeType_ do elemento, no caso ele é um _ELEMENT_NODE _e retorna null, caso fosse um atributo por exemplo ele era um nodeType ‘2’ e retornaria o valor do atributo.

![](https://i.imgur.com/HH2XHS5.png)

Tabela que mostra os nodeTypes, os names que eles retornam e seus valores.

Você pode ler mais sobre nodeTypes [aqui](https://www.w3schools.com/jsref/prop_node_nodetype.asp). 

### Elements

Essas propriedades, ao contrários das outras acima retornam somente elementos. São mais recomendadas pois podem causar menos confusão e são mais simples de serem entendidas.

### .parentNode

Essa propriedade retorna o parente do nó passado.

```
  var container = document.querySelector('.container')

  var getParent = container.parentNode;
```

### .firstElementChild

Essa propriedade retorna o primeiro elemento-filho do elemento especificado.

```
  var container = document.querySelector('.container')

  var getValue = container.firstElementChild;
```

### .lastElementChild

Semelhante a propriedade anterior, mas essa retorna o último elemento-filho do elemento especificado.

```
  var container = document.querySelector('.container')

  var getValue = container.lastElementChild;
```

Essas são apenas alguma das propriedades do DOM, existem várias outras. É muito importante você entender ao menos o básico de como o DOM funciona, seus métodos e propriedades pois cada aplicação pede algo diferente e, nunca se sabe quando você vai usar aquele método ou propriedade.

### Conclusão

O DOM nos proporciona várias API’s importantes para a criação de aplicações fantásticas e cada vez mais inovadoras, entendendo o básico dele você já consegue fazer coisas incríveis. Caso você queira ler mais sobre eventos e saber quais existem, você pode clicar [aqui](https://developer.mozilla.org/en-US/docs/Web/Events) e ler toda referência da MDN.

### Você se interessou por DOM e quer ler mais?

[Understanding DOM: A Fool’s Guide](https://www.guru99.com/understanding-dom-fool-guide.html) (Artigo)

[DOM Enlightment](https://shop.oreilly.com/product/0636920027690.do) (Book by Cody Lindley)

Gostou? Como esse é meu primeiro artigo, deixa seu like, me segue no [**Twitter**](https://twitter.com/leonardomso) e deixa um comentário como feedback que isso é muito importante! ✌
