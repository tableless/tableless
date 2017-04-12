---
title: 'Flux: Entenda como funciona a arquitetura Flux com React'
author: Macgyver
type: post
date: 2015-05-24
excerpt: Arquitetura de aplicações para construir interfaces de usuário feita pelo Facebook.
url: /flux-entenda-como-funciona-arquitetura-flux-com-react/
categories:
  - Geral
  - JavaScript
  - Tecnologia e Tendências

---
### **O que é Flux**

Se você já viu algo sobre React, já brincou ou pelo menos acessou a [sua documentação][1], deve ter se deparado com um cara chamado [**Flux**][2]. E se você, assim como eu, ficou um pouco confuso com a ideia, esse post vai descomplicar as coisas para você.

O Flux (prefiro chamar assim) é uma arquitetura usada pelo Facebook, que junto com o framework React é usado para construir aplicações web no client-side que trabalhem de forma reativa. Basicamente uma forma de fluxo unidirecional de dados entre eventos e ouvintes.

Caso você ainda não tenha noção do que é ou de como desenvolver com React, eu indico ler essa sequência de posts:

  * Introdução sobre React: http://bit.ly/guia-react
  * O que é React e como trabalhar com JSX: http://bit.ly/guia-react-pt1
  * Virtual DOM e Criação de Componentes: http://bit.ly/guia-react-pt2
  * Estados e propriedades de um Componente: http://bit.ly/guia-react-pt3

O conteúdo é ótimo e em português.

Continuando&#8230;

&nbsp;

**Por que parece complicado?**

O nome **Flux** por si já é algo complicado. Ele faz parecer que Flux é como um framework que você precisa carregar pra começar a usar. Porém, Flux não é nada disso. Na verdade o que o Facebook fez foi: pegar uma coisa chamada _fluxo de dados unidirecional_, separar em partes, adicionar um cara chamado **Dispatcher** e chamar isso tudo de Flux.

Então você não precisa se preocupar muito quanto a isso. **Flux é um modelo e não uma coisa**.

Outra coisa que ajuda a dar uma travada, é que no primeiro contato com Flux nosso cérebro não entende o seu conceito e funcionamento, pois queremos compará-lo a outros modelos que já conhecemos como MVC, MVM e etc. Mas acredite, essa não é a melhor maneira. A primeira &#8220;regra&#8221; aqui é não comparar. Não tente fazer analogias ou algo do tipo agora, isso só vai tornar as coisas mais complicadas.

Então vamos ter a mente aberta e entender como o Flux funciona.

_Obs: Precisei colocar as imagens dos scripts no meu post, pois o WordPress estava interpretando minhas tag como html. Desculpem&#8230;_

### **1. O Dispatcher**

Flux é inicialmente dividido em 3 partes:

  * Dispatcher
  * View
  * Store

O **Dispatcher** é como uma central da sua aplicação. Uma central responsável por registrar callbacks e emitir eventos. Por ser uma central, fica claro que **deve haver apenas um único Dispatcher para toda sua aplicação**. Para instanciá-lo você vai precisar usar a lib [Dispatcher.js][3] do Facebook.

Esse é o único código de terceiro que você irá precisar pra rodar sua aplicação Flux.
  
Mas lembre-se: **isso é somente uma lib para fazer Dispatchers**, e não o Flux. Como dito antes, não existe algo como uma biblioteca Flux, pois Flux é só uma arquitetura de fluxo.

Para instanciar o Dispatcher é simples:

<pre class="lang-javascript">var AppDispatcher = new Dispatcher();
</pre>

### **2. Nossa view faz um Dispatch**

A view nada mais é do que um componente React.

Vamos imaginar que nosso app é uma clássica ToDo List.
  
Nela nosso usuário digita a tarefa e clica em salvar.
  
Nossa view seria assim:

<pre class="lang-javascript">var MyApp = React.createClass({  
  render: function() {
    return (
        &lt;div&gt;
          &lt;input type="text" ref="taskName"/&gt;
          &lt;button onCLick={this.handleSave}&gt;Salvar&lt;/button&gt;
        &lt;/div&gt;
    );
  }
});
</pre>

Quando o usuário clicar em _Salvar_, nossa view faz o dispatch de um evento específico, através do método **AppDispatcher.dispatch:**

<pre class="lang-javascript">handleSave: function() {  
    var titulo = this.refs.taskName.getDOMNode().value;

    AppDispatcher.dispatch({
      type: 'novo-item',
      data: { titulo: titulo }
    });
}
</pre>

O método dispatch recebe um objeto como argumento. Nele nós temos os parametros type e data.
  
Nosso dispatch deve indicar qual evento estamos emitindo, e fazemos isso através do **type**. Também passamos a informação que queremos salvar através do **data**.

### **3. A Store responde o evento do dispatch**

Store é o nome que o Facebook decidiu dar para um objeto JavaScript específico, responsável por saber quais são os dados que sua view precisa consumir; e quando e como atualizar a mesma.

No nosso exemplo precisamos de uma lista para salvar nossas tarefas e deletar as mesmas quando nossa view pedir. Vamos chamá-la de _TaskStore_.

<pre class="lang-javascript">var _tasks = [];

var TaskStore = {  
    getAll: function(){
        return {
          tasks: _tasks
        };
    },
};
</pre>

**_NOTA:_** _Como você deve ter notado, temos uma variável chamada _tasks fora da nossa TaskStore. Essa é somente uma forma de deixar a variável que contém nossas tasks, privada, de forma que a view precise chamar TaskStore.getAll() para ter a lista de tasks._

Na TaskStore o dispatcher precisa registrar um callback para cada evento específico. No Flux isso acontece através do método _register_ da biblioteca Dispatcher:

<pre class="lang-javascript">AppDispatcher.register()  
</pre>

Normalmente você encontrará esse registro sendo executado dentro de um método da store. Por exemplo:

<pre class="lang-javascript">var TaskStore = {  
     dispatcherIndex: AppDispatcher.register(function(payload) {
        switch(payload.type) {
          case 'novo-item':
            _tasks.push(payload.data);
            break;
          case 'delete-item':
            //lógica para deletar
            break;
        }
    })
};
</pre>

Essa é a forma como Flux faz o dispatch de callbacks. Cada **payload** contém um evento com seu tipo e dados, no nosso caso _type_ e _data_.
  
Uma estrutura de switch decide o que fazer com essa ação de acordo com o type.
  
Aqui mudamos nosso array inicial, adicionando a ele uma tarefa.

### **4. A Store emite um evento quando finaliza a mudança**

Como dito, nossa Store é a única responsável por saber quando e como atualizar a nossa View. Sendo assim ela deve avisar quando concluir a ação da nossa View.

Você pode usar a lib que achar melhor para emitir eventos. Uma bem simples é a [MicroEvent.js][4].
  
Para nosso exemplo eu prefiro usar a [**EventEmitter**][5] do Nodejs, pois com certeza vai se deparar com ela em quase todos os códigos de Flux open source por aí.
  
Pra instanciá-la é bem fácil:

<pre class="lang-javascript">var EventEmitter = require('events').EventEmitter;  
</pre>

Você pode ler mais sobre ela [aqui][5].

Além disso precisamos usar o [_Object.assign()_][6] do JavaScript para copiar as propriedades do EventEmitter para nossa TaskStore.
  
Como ele só esta presente no ES6, vamos usar um polyfill maroto aqui pra fazer a coisa funcionar bonitinha. Se chama **object-assign** e você aprende mais sobre ele [aqui][7].

<pre class="lang-javascript">var assign = require('object-assign');  
</pre>

Agora com nossa lib de EventEmitter em mãos vamos adicionar à nossa TaskStore os métodos responsáveis por adicionar ouvintes, remover ouvintes e é claro emitir eventos.

<pre class="lang-javascript">var TaskStore = assign({}, EventEmitter.prototype, {  
  //Adiciona um Listener(ouvinte)
  addChangeListener: function(callback) {
    this.on('change', callback);
  },

  //Remove um Listener(ouvinte)
  removeChangeListener: function(callback) {
    this.removeListener('change', callback);
  },

  //Emit mudanças
  emitChange: function() {
    this.emit('change');
  },

  dispatcherIndex: ...;

};
</pre>

Lembra de quando registramos uma ação de adicionar item para o dispatch &#8216;novo-item&#8217;? Então, nossa Store precisa emitir um evento dizendo que essa ação acabou e que nossa View deve se atualizar

<pre class="lang-javascript">dispatcherIndex: AppDispatcher.register(function(payload) {
   switch(payload.type) {
     case 'novo-item':
       _tasks.push(payload.data);
       this.emitChange(); // Avisa que a ação foi concluída
       break;
     case 'delete-item':
       //lógica para deletar
       break;
   }
})
</pre>

_**NOTA**: Somente sua Store faz os registros de callbacks do dispatcher. Sua View nunca deve realiza um AppDispatcher._

**Sobre Stores e sua finalidade**

Deve haver uma Store para cada propósito de uma parte da sua aplicação.
  
Isso é um pouco complicado, então vou tentar ser mais claro: Se em sua aplicação você tem um cadastro de funcionários e um cadastro de clientes, você precisa ter uma store para funcionários e uma para os clientes. Ok?

### **5. A View escuta o evento da Store e atualiza**

Nossa View agora precisa escutar o evento da TaskStore para saber que é hora de se atualizar alterando seu estado.
  
Fazemos isso ouvindo a TaskStore quando o componente for &#8220;montado&#8221;.

<pre class="lang-javascript">var MyApp = React.createClass({ 
  getInitialState: function(){
    return {
      tasks: []
    }
  },
 
  componentDidMount: function() {
    TaskStore.addChangeListener(this._onChange);
  },

  _onChange: function() {
    this.setState(TaskStore.getAll());
  },

  render: ...;
});
</pre>

Para que nossa View se atualize devemos utilizar o estado (_this.state_) do nosso componente, dentro do nosso método render. Dessa forma todas as vezes em que o estado do nosso componente for alterado, nossa view fará um **re-render**.
  
No nosso exemplo, pra listar as tasks ficaria assim:

<pre class="lang-xml">var MyApp = React.createClass({  
  render: function() {

    var listHtml = this.state.tasks.map( function(item, index) { 
       return &lt;li key={ index }&gt; 
                { item.titulo } 
              &lt;/li&gt;; 
    };

    return (
        &lt;div&gt;

          &lt;ul&gt;
            {listHtml}
          &lt;/ul&gt;

          &lt;input type="text" ref="taskName"/&gt;
          &lt;button onCLick={this.handleSave}&gt;Salvar&lt;/button&gt;
        &lt;/div&gt;
    );
  }
});
</pre>

E então por último remova o ouvinte quando nosso componente for &#8220;desmontado&#8221;

<pre class="lang-javascript">var MyApp = React.createClass({  
  ...

  componentWillUnmount: function() {
    TaskStore.removeChangeListener(this._onChange);
  },

  render: ...;
});
</pre>

_**NOTA:** Nunca se esqueça de remover todos os ouvintes da sua view/componente quando ela for desmontada_

Se você não sabe como funciona o lifecycle de um componente, recomendo dar uma lida na [documentação do React][8].

### **E Pronto!**

Isso é o básico de como funciona o Flux. Claro que esse não foi nenhum tutorial, somente uma explicação de como é o funcionamento. Mas espero ter ajudado um pouco.

Aqui está um exemplo de [aplicação com Flux e React][9] desenvolvida pelo Facebook.

Qualquer dúvida, críticas, sugestões ou agradecimentos coloquem aí nos comentários.

Valeu gente!!!

_Esse post foi originalmente publicado em [macgyvermartins.com.br][10]_

 [1]: http://facebook.github.io/react/docs/getting-started.html
 [2]: http://facebook.github.io/flux/docs/overview.html
 [3]: https://github.com/facebook/flux/blob/master/src/Dispatcher.js
 [4]: http://notes.jetienne.com/2011/03/22/microeventjs.html
 [5]: https://nodejs.org/api/events.html
 [6]: https://people.mozilla.org/~jorendorff/es6-draft.html#sec-object.assign
 [7]: https://github.com/sindresorhus/object-assign
 [8]: https://facebook.github.io/react/docs/component-specs.html
 [9]: https://github.com/facebook/flux/tree/master/examples/flux-todomvc
 [10]: http://macgyvermartins.com.br/como-funciona-a-arquitetura-flux-com-react/