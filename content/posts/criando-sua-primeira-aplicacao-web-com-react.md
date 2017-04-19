---
title: Criando a sua primeira aplicação web com React
author: Lucas Daltro
type: post
date: 2017-02-17
excerpt: Um exemplo prático de como criar seu primeiro código com o Create React App.
aliases: 
  - /?p=56997
  - /criando-sua-primeira-aplicacao-web-com-react/
categories:
  - JavaScript
tags:
  - ES6
  - JavaScript
  - react

---
Você já deve ter ouvido falar do React, a biblioteca JS mais popular da atualidade, usado por várias empresas grandes como Facebook, Airbnb e Twitter. A ideia desse artigo é demonstrar a criação de uma aplicação simples, que use as principais partes do React. Neste tutorial nós iremos ver:

  * Componentes
  * Componentes puros/funcionais
  * O uso do _state_ vs _props_

Todos os exemplos deste tutorial serão escritos em ES6. Se você não sabe ES6 [leia esse artigo antes][1]. Se você é impaciente demais para isso considere que:

ES6:

<pre class="lang-javascript">const foo = 42; // const declara uma constante
let bar = 5; // let declara uma variável
</pre>

<pre class="lang-javascript">const soma = (a, b) =&gt; a + b;
ou 
const soma = (a, b) =&gt; { return a + b; };
</pre>

ES5:

<pre class="lang-javascript">var soma = function (a, b) {
  return a + b;
};
</pre>

ES6:

<pre class="lang-javascript">import React from 'react';
</pre>

ES5:

<pre class="lang-javascript">var React = require('react');
</pre>

ES6:

<pre class="lang-javascript">class MeuComponente extends React.Component {
  render() {
    return ();
  }
} 
</pre>

ES5:

<pre class="lang-javascript">var MeuComponente = React.createClass({
  render: function(){
    return ();
  }
});</pre>

Outro pré-requisito para o tutorial é ter o [Node.js][2] instalado na sua máquina. Se você ainda não fez isso, clique [aqui][3] e siga as instruções, dependendo do seu sistema operacional.

## Afinal, o que é React?

**React** é uma biblioteca criada pelo Facebook em 2013 com o objetivo de tornar o desenvolvimento de _Single Page Applications_ (SPAs) mais fácil. A biblioteca se baseia em alguns conceitos como:

### Componentes

Uma aplicação React é dividida em componentes, ou seja, pequenos pedaços de código responsáveis por alguma parte da UI. Um componente ideal é independente e reutilizável, capaz de retornar a resposta esperada usando apenas dados genéricos enviados por outras partes da aplicação.

Um exemplo de componente React interessante pode ser visto [nessa biblioteca de mapas][4]:

<pre>&lt;<span class="pl-ent"><span class="pl-c1">GoogleMap</span></span>
    <span class="pl-e">ref</span><span class="pl-k">=</span><span class="pl-pse">{</span><span class="pl-s1"><span class="pl-smi">props</span><span class="pl-k">.</span><span class="pl-smi">onMapLoad</span></span><span class="pl-pse">}</span>
    <span class="pl-e">defaultZoom</span><span class="pl-k">=</span><span class="pl-pse">{</span><span class="pl-s1"><span class="pl-c1">3</span></span><span class="pl-pse">}</span>
    <span class="pl-e">defaultCenter</span><span class="pl-k">=</span><span class="pl-pse">{</span><span class="pl-s1">{<span class="pl-c1"> <span class="pl-s">lat</span>:</span> <span class="pl-c1">-25.363882</span>,<span class="pl-c1"> <span class="pl-s">lng</span>:</span> <span class="pl-c1">131.044922</span> }</span><span class="pl-pse">}</span>
    <span class="pl-e">onClick</span><span class="pl-k">=</span><span class="pl-pse">{</span><span class="pl-s1"><span class="pl-smi">props</span><span class="pl-k">.</span><span class="pl-smi">onMapClick</span></span><span class="pl-pse">}</span>
  &gt;
&lt;/<span class="pl-ent"><span class="pl-c1">GoogleMap</span></span>&gt;
</pre>

Graças ao componentes do React, podemos importar um mapa do Google Maps e usá-lo como se fosse uma tag nativa de HTML, passando apenas as propriedades que nós queremos no componente, como _defaultZoom_ e _defaultCenter_.

### JSX

Em React nós não usamos HTML, toda a marcação é feita no JavaScript, com uma sintaxe baseada em XML chamada JSX. A ideia pode parecer bem maluca no começo mas vai fazer sentido assim que você começar a escrever os seus próprios componentes. JSX parece bastante com HTML mas existem algumas diferenças como:

  * Todas as tags devem ser fechadas
  * Podemos colocar expressões JavaScript dentro do JSX usando {}. Ex.: <pre class="lang-javascript">function ola() {
 return "ola";
}
 &lt;p&gt;{2 + 2}&lt;/p&gt;
 &lt;p&gt;{ola()}&lt;/p&gt;</pre>

  * Como o JSX fica dentro de arquivos &#8216;.js&#8217; a palavra _class_ não pode ser usada. Em seu lugar, devemos usar _className_. Ex.: <pre class="lang-javascript">&lt;h1 className="titulo"&gt;Olá!&lt;/h1&gt;
</pre>

Por debaixo dos panos, usamos o **Babel** para converter o JSX em funções comuns de JavaScript, logo, esse código:

<pre>&lt;div&gt;Olá mundo&lt;/div&gt;
</pre>

Fica assim:

<pre><span class="nx">React</span><span class="p">.</span><span class="nx">createElement</span><span class="p">(</span><span class="s1">'div'</span><span class="p">,</span> <span class="kc">null</span><span class="p">,</span> "Olá mundo"<span class="p">);
</span></pre>

Leia mais sobre JSX [aqui][5].

### Virtual DOM

Para evitar updates custosos e desnecessários, o React não escreve as alterações diretamente na DOM. Ao invés disso, a biblioteca cria uma cópia da árvore de componentes em memória e esta cópia (Virtual DOM) é quem recebe os updates primeiro. Depois que a Virtual DOM é atualizada o React calcula a maneira mais eficiente de atualizar a árvore DOM real usando um algoritmo de _diffing._

## Pondo a mão na massa

Ok, chega de tanta teoria, vamos por a mão na massa! Abra o seu terminal e vamos instalar um pacote que vai nos ajudar a criar nossas aplicações o **[create-react-app][6]:**

<pre>npm install create-react-app</pre>

Montar um ambiente de desenvolvimento capaz de suportar React costumava ser uma tarefa complicada ([esse tutorial do Diego Eis explica muito bem a criação de um ambiente &#8220;na mão&#8221;][7]). Por causa disso, o Facebook inventou um pacote chamado _create-react-app_, que cria um ambiente com tudo o que nós precisamos para começar o nosso projeto (React, ES6 e webpack).

Depois de instalar o pacote, vamos criar um novo projeto. No terminal digite:

<pre class="p1"><span class="s1">create-react-app vamos-aprender-react</span></pre>

Depois de alguns minutos todas as dependências estão instaladas e _voilà!_ Temos um projeto pronto para ser criado.
  
Com o terminal do diretório do seu projeto digite:

<pre>npm start</pre>

Se tudo deu certo, o seu browser em _http://localhost:3000/_ deve estar assim:
  
<img class="alignnone wp-image-57013 size-full" src="uploads/2017/01/Captura-de-Tela-2017-01-22-às-19.29.35.png" alt="Imagem ilustrativa do create-react-app" width="1438" height="748" />

Parabéns! Você acabou de criar a sua primeira aplicação com React! Vamos dar uma olhada no que foi gerado:

<img class="alignnone wp-image-57015 size-full" src="uploads/2017/01/Captura-de-Tela-2017-01-22-às-19.34.30.png" alt="Estrutura de pastas do create-react-app" width="232" height="415" />

Como podemos ver, a pastar _src_ contém todos os nosso componentes React. Dentro de _src_ abra o arquivo _index.js_, ele deve conter algo desse tipo:

<pre>import React from 'react';
import ReactDOM from 'react-dom';
import App from './App';
import './index.css';

ReactDOM.render(
 &lt;App /&gt;,
 document.getElementById('root')
);
</pre>

O index.js é o arquivo principal da nossa aplicação, ele é responsável por colocar o nosso componente principal (App) no elemento _root_ da nossa página. _Root_ é uma div que está dentro do único arquivo .html do projeto (public/index.html). Toda a nossa aplicação vai ser escrita dentro dessa div root.

### Criando nosso primeiro componente

Abra o arquivo _App.js_, ele é o primeiro componente da nossa árvore. Dentro dele podemos ver o JSX usado para renderizar a tela de boas vindas do _create-react-app_:

<pre>&lt;div className="App"&gt;
 &lt;div className="App-header"&gt;
 &lt;img src={logo} className="App-logo" alt="logo" /&gt;
 &lt;h2&gt;Welcome to React&lt;/h2&gt;
 &lt;/div&gt;
 &lt;p className="App-intro"&gt;
 To get started, edit &lt;code&gt;src/App.js&lt;/code&gt; and save to reload.
 &lt;/p&gt;
 &lt;/div&gt;
</pre>

Note que todo esse código está dentro de um método chamado _render_ na classe _App_ que é filha da classe de _React.Component_. _Render_ é responsável por dizer ao React o que deve ser renderizado, todo componente precisa de um método _render_ para exibir alguma coisa.

Substitua o método _render_ por:

<pre>render() {
 return &lt;HelloWorld/&gt;;
 }</pre>

Se tentarmos rodar o projeto, veremos o seguinte erro:

<pre>7:13 error 'HelloWorld' is not defined react/jsx-no-undef 
</pre>

Isso acontece porque estamos tentando usar um component (HelloWorld) que ainda não foi definido. Vamos resolver isso criando um arquivo chamado HelloWorld.js dentro da pastar _src_. Dentro de HelloWorld coloque:

<pre>import React from 'react';

export default class HelloWorld extends React.Component {
 render() {
 return &lt;p&gt;Olá mundo!&lt;/p&gt;;
 }
}</pre>

Esse código cria um componente React chamado HelloWorld e implementa o método _render_ que retorna um parágrafo com **olá mundo**. Depois disso vamos importar nosso novo componente em App.js:

<pre>import React, { Component } from 'react';
import logo from './logo.svg';
import './App.css';

import HelloWorld from './HelloWorld';// nosso primeiro componente React!

class App extends Component {
 render() {
 return &lt;HelloWorld/&gt;;
 }
}

export default App;</pre>

Agora abrindo o browser em _http://localhost:3000/_ vemos:

<img class="alignnone wp-image-57018 size-full" src="uploads/2017/01/Captura-de-Tela-2017-01-22-às-20.00.26.png" alt="Exemplo de Hello World" width="1439" height="723" />

Ótimo! Nós acabamos de criar nosso primeiro React Component \o/. Mas ele não faz lá muita coisa não é mesmo? Vamos tentar fazer esse componente ser mais customizável.

## Criando componentes genéricos com Props

E se nós quiséssemos exibir o nome de uma pessoa na mensagem do nosso HelloWorld? Obviamente poderíamos fazer algo do tipo:

<pre>import React from 'react';

export default class HelloWorld extends React.Component {
 render() {
 return &lt;p&gt;Olá Lucas!&lt;/p&gt;;
 }
}</pre>

Mas e se for necessário escrever novos nomes? Criar um componente novo para cada pessoa não parece uma ideia muito inteligente&#8230; lembra do exemplo do Google Maps mostrado na introdução? No exemplo, nós passávamos dados para um componente como se fosse uma tag HTML. Vamos fazer a mesma coisa para o nosso HelloWorld! Mude App.js para:

<pre>import React, { Component } from 'react';
import logo from './logo.svg';
import './App.css';

import HelloWorld from './HelloWorld';// nosso primeiro componente React!

class App extends Component {
 render() {
 return &lt;div&gt;
 &lt;HelloWorld nome="Lucas"/&gt;
 &lt;HelloWorld nome="Tableless"/&gt;
 &lt;HelloWorld nome="Leitor"/&gt;
 &lt;/div&gt;;
 }
}

export default App;</pre>

Veja que dessa vez nós tivemos que colocar o HelloWorld dentro de uma div, isso acontece porque o método _render_ deve sempre retornar apenas um elemento, **sempre que tiver que renderizar mais de um elemento no seu componente, coloque tudo dentro de uma div**.

Agora nós temos que fazer com que o componente HelloWorld leia o valor dado em nome. Isso pode ser feito facilmente usando o objeto **props** presente em todo componente React. Veja como HelloWorld.js vai ficar agora:

<pre>import React from 'react';

export default class HelloWorld extends React.Component {
 render() {
 return &lt;p&gt;Olá {this.props.nome}!&lt;/p&gt;;
 }
}

HelloWorld.propTypes = {
 nome: React.PropTypes.string.isRequired
}</pre>

Tudo que for passado de um componente para outro é adicionado ao objeto _props_, podendo ser acessado dentro do componente. Nós também usamos a propriedade _propTypes_ para informar ao React que a _prop_ &#8216;nome&#8217; é uma _string_ e que essa _string_ é obrigatória para o funcionamento do componente (_isRequired_). Você não é obrigado a usar _propTypes_ nos seus componentes, mas é interessante fazer isso, já que elas facilitam a documentação do seu código e podem reduzir erros.

Agora nós temos um componente muito mais genérico:

<img class="alignnone wp-image-57023 size-full" src="uploads/2017/01/Captura-de-Tela-2017-01-22-às-20.18.28.png" alt="Exemplo de Componente React" width="181" height="193" />

_Props_ são algo crucial para os componentes React, já que com elas nós podemos fazer com que o nosso componente seja reutilizado até mesmo em outra aplicação. Mas devemos sempre ter em mente que _props_ são imutáveis, uma vez definida a _prop_ &#8216;nome&#8217;, uma instância de HelloWorld não pode mais ser alterada. Ex.:

<pre>import React from 'react';

export default class HelloWorld extends React.Component {
 render() {
 this.props.nome = "Fulano"; // ERRO Cannot assign to read only property 'nome' of object '#&lt;Object&gt;'
 return &lt;p&gt;Olá {this.props.nome}!&lt;/p&gt;;
 }
}

HelloWorld.propTypes = {
 nome: React.PropTypes.string.isRequired
}</pre>

### Componente &#8220;puro&#8221; ou _stateless_

Nosso componente HelloWorld é bastante simples e utiliza apenas _props_, por causa disso ele pode ser escrito de uma forma melhor, utilizando uma [função pura][8]. Veja como fica o nosso componente em forma de função:

<pre>import React from 'react'; const HelloWorld = (props) =&gt; &lt;p&gt;Olá {props.nome}!&lt;/p&gt;;</pre>

<pre>HelloWorld.propTypes = { nome: React.PropTypes.string.isRequired } export default HelloWorld;</pre>

Veja que dessa vez o componente é basicamente escrito em apenas uma linha (**const HelloWorld = (props) => <p>Olá {props.nome}!</p>;**). Esse é o React Component ideal! Simples, reutilizável e escrito em apenas uma função! Tente criar seus componentes dessa maneira, ao invés de ter um componente complexo e grande, crie vários componentes menores e simples, isso vai melhorar bastante a qualidade do seu projeto.

Para comprovar que o nosso componente é realmente reutilizável vamos usá-lo em uma lista de nomes. Volte para App.js e digite:

<pre>import React, { Component } from 'react';
import logo from './logo.svg';
import './App.css';

import HelloWorld from './HelloWorld';// nosso primeiro componente React!

class App extends Component {
 render() {
 const nomes = ["Lucas", "Tableless", "Leitor", "Maria", "João", "Ana"];
 return &lt;div&gt;
 {nomes.map((n, i) =&gt; &lt;HelloWorld nome={n} key={i}/&gt;)}
 &lt;/div&gt;;
 }
}

export default App;
</pre>

Perceba que nós temos uma mudança aqui, para exibir nomes do nosso _array_ nós usamos a [função map][9], já que ela retorna uma expressão JavaScript (além de ter uma sintaxe mais legal que a do o laço for :P) e passamos uma nova _prop_ chamada _**key**_ para o nosso componente. _Keys_ ajudam o React a identificar qual elemento foi adicionado/removido de uma lista/array ([mais informações sobre o assunto aqui][10]). Uma _Key_ deve sempre ser um valor **único** ou poderemos ter problemas de performance. Evite usar o índice do seu _loop_ como _key_ em aplicações reais (como fizemos no exemplo acima), tente usar números realmente únicos como um ID vindo de um backend. Leia mais sobre isso [aqui][11].

## Componentes interativos com state

Como visto anteriormente _props_ são imutáveis, componentes feitos apenas com _props_ não podem por exemplo, ser atualizados baseados em uma ordem do usuário. Para representar o estado mutável do seu componente usamos a propriedade **_state_.**

Para ilustrar o uso de _state_ no nosso elemento vamos fazer um novo componente e chamá-lo de **ContaClick.js**:

<pre>import React from 'react';

export default class ContaClick extends React.Component {
 constructor() {
 super();
 this.state = {
 clicks: 0
 }
 }

 render() {
 return &lt;div&gt;&lt;p&gt;{this.state.clicks}&lt;/p&gt;&lt;/div&gt;
 }
}

</pre>

No construtor da classe ContaClick nós definimos o estado inicial do nosso componente: um contador de clicks que começa em 0. Vamos adicionar um botão para atualizar o contador:

<pre>import React from 'react';

export default class ContaClick extends React.Component {
 constructor() {
 super();
 this.state = {
 clicks: 0
 }
 }

 clicou = () =&gt; this.setState({clicks: this.state.clicks + 1});
 
 render() {
 return &lt;div&gt;
 &lt;p&gt;{this.state.clicks}&lt;/p&gt;
 &lt;button onClick={this.clicou}&gt;Clica aqui!&lt;/button&gt;
 &lt;/div&gt;
 }
}
</pre>

No código acima nós criamos um botão embaixo do exibidor de cliques que chama o método _**clicou**_ sempre que o evento onClick é disparado. O método _**clicou**_ substitui o objeto _state_ do componente ContaClick por um objeto novo com clicks incrementados em uma unidade. Veja que nós atualizamos o _state_ usando a função _setState_. **NUNCA atualize o objeto _state_ manualmente**.

Agora vamos colocar o nosso componente _ContaClick_ em _app_:

<pre>import React, { Component } from 'react';
import logo from './logo.svg';
import './App.css';

import HelloWorld from './HelloWorld';// nosso primeiro componente React!
import ContaClick from './ContaClick';

class App extends Component {
 render() {
 const nomes = ["Lucas", "Tableless", "Leitor", "Maria", "João", "Ana"];
 return &lt;div&gt;
 {nomes.map((n, i) =&gt; &lt;HelloWorld nome={n} key={i}/&gt;)}
 &lt;ContaClick /&gt;
 &lt;/div&gt;;
 }
}

export default App;
</pre>

Pronto! Rodando a aplicação podemos usar o contador e ver que ele é atualizado a cada clique!

Até a próxima!

 [1]: https://github.com/ldaltro/guia-basico-ES6
 [2]: https://nodejs.org/en/
 [3]: https://nodejs.org/en/download/
 [4]: https://github.com/tomchentw/react-google-maps
 [5]: https://facebook.github.io/react/docs/introducing-jsx.html
 [6]: https://github.com/facebookincubator/create-react-app
 [7]: https://tableless.com.br/hello-world-com-react-do-rascunho-ate-o-primeiro-componente/
 [8]: https://en.wikipedia.org/wiki/Pure_function
 [9]: https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/Array/map
 [10]: https://facebook.github.io/react/docs/lists-and-keys.html
 [11]: https://medium.com/@robinpokorny/index-as-a-key-is-an-anti-pattern-e0349aece318#.4nmajnqsa