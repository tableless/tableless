---
title: 'React: JavaScript reativo'
author: Davi Ferreira
type: post
date: 2013-09-17
excerpt: Conheça a biblioteca React desenvolvida por Facebook e Instagram, que apresenta um novo paradigma para o desenvolvimento de aplicações web.
url: /react-javascript-reativo/
dsq_thread_id: 1769686962
categories:
  - JavaScript
tags:
  - JavaScript
  - react

---
Uma das palestras que chamou minha atenção na BrazilJS desse ano foi a de <a href="http://www.phpied.com/files/react/slides.html" target="_blank">Stoyan Stefanov</a>, autor do clássico <a href="http://www.amazon.com/JavaScript-Patterns-Stoyan-Stefanov/dp/0596806752" target="_blank">JavaScript Patterns</a>. Stoyan mostrou a biblioteca <a href="http://facebook.github.io/react/" target="_blank">React</a>, desenvolvida pelo pessoal do Facebook/Instagram.

Apesar de não ser um palestrante muito <a href="https://twitter.com/davitferreira/status/371051778764468224" target="_blank">carismático</a>, o código mostrado por Stoyan me deixou com a pulga atrás da orelha por possuir uma sintaxe para lá de esquisita e por fugir um pouco da abordagem mais conservadora adotada por bibliotecas e frameworks do mercado.

Depois de experimentar em algumas aplicações rápidas, fiquei bem surpreso e satisfeito com o resultado do uso da React.

## JavaScript declarativo

A React pode ser comparada com o framework AngularJS, do Google, por ser declarativo, ou seja, por fazer você, desenvolvedor, focar mais no resultado do que na forma como ele é atingido. Na prática, isso quer dizer que você vai escrever pouco código JavaScript e obter uma aplicação funcional em muito pouco tempo.

Outro grande diferencial da React é que ela trabalha com um pseudo-DOM em memória. Como vocês sabem (<a href="http://tableless.com.br/jquery-dicas-de-otimizacao-e-performance/" target="_blank">ou deveriam saber</a>), manipular o DOM é um dos principais causadores de gargalos de performance em sites e web apps e a React resolve isso de maneira brilhante trabalhando com um &#8220;DOM&#8221; próprio. 

Toda vez que um elemento precisa ser renderizado, a biblioteca identifica as atualizações comparando o elemento no DOM e na memória, modificando somente o que foi de fato alterado, sem precisar renderizar todo o elemento.

## JavaScript reativo

Outro ponto forte da biblioteca React é a criação de componentes reutilizáveis. No mesmo BrazilJS o Zeno <a href="https://speakerdeck.com/zenorocha/um-futuro-chamado-web-components" target="_blank">palestrou</a> sobre Web Components. A ideia aqui é parecida e a React faz sua própria implementação.

Todo componente React possui dois atributos principais: estado (state) e propriedades (props). Toda vez que o estado de um componente é alterado, ele é renderizado &mdash; isto é JavaScript reativo. Além disso, ao renderizar novamente um componente, a React faz uma comparação entre o estado atual e o novo estado e renderiza apenas o que foi modificado, ou seja, não renderiza novamente todos os atributos e conteúdo do elemento no DOM.

## JSX

Uma parte bem esquisita no primeiro contato com a biblioteca React é a utilização da sintaxe JSX, que transforma XML para JavaScript. Nos exemplos você verá markup HTML (sem ser string) no meio de código JavaScript.

É importante dizer que o uso de JSX é opcional. Também é importante dizer que JSX pode ser utilizado com qualquer código JavaScript, não só React.

Vejamos um exemplo simples:

<pre class="lang-javascript">// JSX:
var Site,
    tableless = &lt;Site url="http://www.tableless.com.br" nome="Tableless" /&gt;;</pre>

Tranformando em JavaScript, o resultado é o seguinte:

<pre class="lang-javascript">var tableless = Site({url:"http://www.tableless.com.br", nome:"Tableless"});</pre>

Notem que precisamos ter o objeto Site no escopo do JSX, mesmo ele não sendo utilizado. O XML é convertido para a chamada deste objeto onde os atributos da tag Site viram propriedades do objeto Site. 

O site da React oferece um compilador online de JSX caso você queira brincar e experimentar com a sintaxe: <a href="http://facebook.github.io/react/jsx-compiler.html" target="_blank">http://facebook.github.io/react/jsx-compiler.html</a>. O conceito e a implementação do JSX são tão interessantes que valeriam um artigo próprio. 

## Aplicação de exemplo

Depois de muita teoria, chegou a hora de ver a React na prática. Para nossa aplicação, vou utilizar o mesmo exemplo que mostrei no <a href="http://tableless.com.br/criando-uma-aplicacao-simples-com-angularjs/" target="_blank">artigo sobre AngularJS</a>, até mesmo para servir como um comparativo entre o código dessas duas bibliotecas.

Vamos começar com a estrutura inicial do nosso HTML:

<pre class="lang-xml">&lt;!doctype html&gt;
&lt;html&gt;
    &lt;head&gt;
        &lt;title&gt;Lista de compras com ReactJS&lt;/title&gt;
    &lt;/head&gt;
    &lt;body&gt;
        &lt;div id="container" class="container"&gt;&lt;/div&gt;
        &lt;script type="text/javascript" src="react.js"&gt;&lt;/script&gt;
        &lt;script type="text/javascript" src="JSXTransformer.js"&gt;&lt;/script&gt;
    &lt;/body&gt;
&lt;/html&gt;</pre>

Pois é, isso é tudo que vamos escrever de HTML. Na verdade, ainda vamos escrever mais HTML, mas utilizando o formato JSX dentro do nosso código React.

Vamos declarar nosso script com o tipo (&#8220;text/jsx&#8221;) e o comentário (obrigatório) que indicam que nosso código utiliza sintaxe JSX e que ele precisa ser compilado em tempo real pelo JSX Transformer.

<pre class="lang-html">&lt;script type="text/jsx"&gt;
/**
* @jsx React.DOM
*/
&lt;/script&gt;</pre>

É claro que você não deve fazer isso em produção. A react oferece um set de ferramentas como um pacote npm que inclui um compilador de linha de comando para JSX. Para instalar, digite: **npm install -g react-tools**. Feito isso, o comando **jsx** estará disponível e ele pode ser utilizado para compilar e observar modificações em arquivos jsx. No nosso exemplo, para facilitar, vamos continuar utilizando JSX inline, compilado em tempo real. Mas, não façam isso em produção!

Dando sequência, vamos criar nosso primeiro componente, o container da nossa lista de compras:

<pre class="lang-javascript">&lt;script type="text/jsx"&gt;
/**
* @jsx React.DOM
*/
var ShoppingBox = React.createClass({
    render: function () {
        return (
            &lt;div&gt;
                &lt;h1&gt;Minha Lista de Compras&lt;/h1&gt;
            &lt;/div&gt;
        );
    }
});

React.renderComponent(
    &lt;ShoppingBox /&gt;,
    document.getElementById('container')
);
&lt;/script&gt;</pre>

Estão vendo esse **document.getElementById** aí em cima? Muito provavelmente essa é a única vez que você interage com o DOM diretamente em uma app React. Precisamos definir o elemento container da nossa app. O restante das operações será feita através do DOM em memória da React.

Nosso primeiro componente não faz muita coisa, apenas adiciona o seu markup. Vamos agora adicionar dois novos componentes: a tabela que listará os produtos em nossa lista e o formulário para cadastrar um novo produto.

<pre class="lang-javascript">&lt;script type="text/jsx"&gt;
/**
* @jsx React.DOM
*/
var ShoppingBox = React.createClass({
    render: function () {
        return (
            &lt;div&gt;
                &lt;h1&gt;Minha Lista de Compras&lt;/h1&gt;
                &lt;ShoppingTable /&gt;
                &lt;ShoppingForm /&gt;
            &lt;/div&gt;
        );
    }
});

var ShoppingTable = React.createClass({
    render: function () {
        return (
            &lt;table&gt;
                &lt;thead&gt;
                    &lt;tr&gt;
                        &lt;th&gt;Comprado?&lt;/th&gt;
                        &lt;th&gt;Produto&lt;/th&gt;
                        &lt;th&gt;Quantidade&lt;/th&gt;
                    &lt;/tr&gt;
                &lt;/thead&gt;
                &lt;tbody&gt;
                &lt;/tbody&gt;
            &lt;/table&gt;
        );
    }
});

var ShoppingForm = React.createClass({
    render: function () {
        return (
            &lt;form&gt;
                &lt;input type="text" placeholder="Produto" /&gt;
                &lt;input type="number" placeholder="Quantidade" /&gt;
                &lt;button type="submit"&gt;adicionar ítem&lt;/button&gt;
            &lt;/form&gt;
        );
    }
});

React.renderComponent(
    &lt;ShoppingBox /&gt;,
    document.getElementById('container')
);
</pre>

Agora, além do container, estamos renderizando também a tabela e o form. Nosso último componente é um componente para o produto em si. Adicionem o código abaixo antes da chamada **React.renderComponent**:

<pre class="lang-javascript">...
var Product = React.createClass({
    render: function () {
        return (
            &lt;tr&gt;
                &lt;td&gt;&lt;input type="checkbox" /&gt;&lt;/td&gt;
                &lt;td&gt;Produto Teste&lt;/td&gt;
                &lt;td&gt;1&lt;/td&gt;
            &lt;/tr&gt;
        );
    }
});
...</pre>

Para o produto ser renderizado, precisamos adicionar o componente ao método render da tabela:

<pre class="lang-javascript">...
var ShoppingTable = React.createClass({
    render: function () {
        return (
            &lt;table&gt;
                &lt;thead&gt;
                    &lt;tr&gt;
                        &lt;th&gt;Comprado?&lt;/th&gt;
                        &lt;th&gt;Produto&lt;/th&gt;
                        &lt;th&gt;Quantidade&lt;/th&gt;
                    &lt;/tr&gt;
                &lt;/thead&gt;
                &lt;tbody&gt;
                	&lt;Product /&gt;
                &lt;/tbody&gt;
            &lt;/table&gt;
        );
    }
});
</pre>

Hora de explicar algumas coisas. Por enquanto temos todos os nossos componentes renderizando HTML, sem nada dinâmico além dos próprios componentes. Os componentes são criados através do método **React.createClass**, que recebe um objeto com os métodos do componente. O método **render** é obrigatório em qualquer componente React e é responsável pela interface com o usuário.

Um componente pode ser renderizado dentro do método render de um outro componente ou em um container no DOM utilizando o método **React.renderComponent**, que recebe como parâmetro os componentes e o elemento no DOM que os receberá.

Outra observação importante: um componente, para ser renderizado dentro de outro componente, precisa estar dentro de um elemento HTML válido. Por isso o nosso ShoppingBox possui um elemento <div> que contém os componentes ShoppingTable e ShoppingForm.

Agora vamos começar a tornar nossa aplicação mais dinâmica, utilizando passos pequenos. O primeiro passo é o carregamento de alguns produtos. Vejamos o código abaixo:

<pre class="lang-javascript">...
var ShoppingTable = React.createClass({
    render: function () {
        return (
            &lt;table&gt;
                &lt;thead&gt;
                    &lt;tr&gt;
                        &lt;th&gt;Comprado?&lt;/th&gt;
                        &lt;th&gt;Produto&lt;/th&gt;
                        &lt;th&gt;Quantidade&lt;/th&gt;
                    &lt;/tr&gt;
                &lt;/thead&gt;
                &lt;tbody&gt;
                    &lt;Product ammount={2} checked={false}&gt;Leite
                    &lt;Product ammount={4} checked={true}&gt;Negresco
                &lt;/tbody&gt;
            &lt;/table&gt;
        );
    }
});
...</pre>

Na criação do componente da nossa tabela de produtos estamos passando dois produtos com seus respectivos atributos. A sintaxe do JSX permite que você passe dois tipos de valores para as propriedades: uma string (entre aspas) ou um valor JavaScript utilizando chaves. No exemplo acima estamos passando a quantidade como inteiro e o checked como booleano.

Precisamos agora alterar o código do nosso componente de Produto para receber e renderizar os produtos passados no componente Tabela, retirando nosso produto de teste que estava fixo no código.

<pre class="lang-javascript">...
var Product = React.createClass({
    getInitialState: function() {
        return {checked: this.props.checked || false};
    },
    toggle: function () {
        this.setState({checked: !this.state.checked});
    },
    render: function () {
        var checked = (this.state.checked ? 'checked' : '');
        return (
            &lt;tr&gt;
                &lt;td&gt;&lt;input type="checkbox" checked={checked} onClick={this.toggle} /&gt;&lt;/td&gt;
                &lt;td&gt;{this.props.children}&lt;/td&gt;
                &lt;td&gt;{this.props.ammount}&lt;/td&gt;
            &lt;/tr&gt;
        );
    }
});
...</pre>

O método **getInitialState** é padrão para qualquer componente React. Ele deve retornar o estado inicial de um componente, seus valores default. No caso do nosso componente produto, verificamos se ele vem marcado ou não.

Implementamos também o método **toggle**, que marca e desmarca um checkbox e que, em uma implementação final, deveria atualizar essa informação no servidor. Notem que o **toggle** foi associado ao evento de clique do nosso checkbox na renderização do componente.

No método **render** acessamos aqueles dois atributos principais que citamos anteriormente: state e props. Primeiro verificamos se o produto está marcado ou não e depois definimos sua quantidade e seu nome. O atributo **children** busca qualquer nó filho do elemento JSX que utilizamos, no nosso caso um simples nó de texto com o nome do produto. Entenderam a diferença entre props e state? O primeiro é tudo passado via parâmetro no objeto do componente e o segundo é o estado do objeto, uma propriedade já definida anteriormente.

E se quiséssemos buscar nossos produtos iniciais de uma consulta ao servidor, em uma API que nos retornaria um objeto JSON com os produtos? Isso também é trivial com React. Vamos alterar nosso código:

<pre class="lang-javascript">...
var PRODUCTS = [
    {ammount: 2, checked: false, name: "Leite"},
    {ammount: 4, checked: true, name: "Negresco"}
];
...
var ShoppingBox = React.createClass({
    render: function () {
        return (
            &lt;div&gt;
                &lt;h1&gt;Minha Lista de Compras&lt;/h1&gt;
                &lt;ShoppingTable data={this.props.data} /&gt;
                &lt;ShoppingForm /&gt;
            &lt;/div&gt;
        );
    }
});
...
var ShoppingTable = React.createClass({
    render: function () {
        var productNodes = this.props.data.map(function (product) {
            return &lt;Product ammount={product.ammount} checked={product.checked}&gt;{product.name}&lt;/Product&gt;;
        });
        return (
            &lt;table&gt;
                &lt;thead&gt;
                    &lt;tr&gt;
                        &lt;th&gt;Comprado?&lt;/th&gt;
                        &lt;th&gt;Produto&lt;/th&gt;
                        &lt;th&gt;Quantidade&lt;/th&gt;
                    &lt;/tr&gt;
                &lt;/thead&gt;
                &lt;tbody&gt;
                    {productNodes}
                &lt;/tbody&gt;
            &lt;/table&gt;
        );
    }
});
...
React.renderComponent(
    &lt;ShoppingBox data={PRODUCTS} /&gt;,
    document.getElementById('container')
);
...</pre>

Nessa nova rodada de código, alteramos o componente **ShoppingBox** para receber um atributo data com o JSON dos produtos. Esse JSON é passado quando renderizamos o componente principal. Além disso, alteramos o método **render** da tabela de produtos para criar cada componente produto encontrado no objeto JSON, resultando na variável local **productNodes**.

Agora, para finalizar, vamos implementar nosso formulário.

<pre class="lang-javascript">...
var ShoppingBox = React.createClass({
    handleProductSubmit: function(product) {
        var products = this.state.data;
        products.push(product);
        this.setState({data: products});
    },
    getInitialState: function() {
        return {data: []};
    },
    render: function () {
        return (
            &lt;div&gt;
                &lt;h1&gt;Minha Lista de Compras&lt;/h1&gt;
                &lt;ShoppingTable data={this.state.data} /&gt;
                &lt;ShoppingForm onProductSubmit={this.handleProductSubmit} /&gt;
            &lt;/div&gt;
        );
    }
});
...
var ShoppingForm = React.createClass({
    handleSubmit: function() {
        var name = this.refs.name.getDOMNode().value.trim(),
            ammount = this.refs.ammount.getDOMNode().value.trim() || 1;
        if (!name) {
            return false;
        }
        this.props.onProductSubmit({name: name, ammount: ammount});
        this.refs.name.getDOMNode().value = '';
        this.refs.ammount.getDOMNode().value = '';
        return false;
    },
    render: function () {
        return (
            &lt;form class="form-inline" role="form" onSubmit={this.handleSubmit}&gt;
                &lt;div class="form-group"&gt;
                    &lt;input type="text" placeholder="Produto" ref="name" class="form-control" /&gt;
                &lt;/div&gt;
                &lt;div class="form-group"&gt;
                    &lt;input type="number" placeholder="Quantidade" ref="ammount" class="form-control" /&gt;
                &lt;/div&gt;
                &lt;button type="submit" class="btn btn-primary"&gt;adicionar ítem&lt;/button&gt;
            &lt;/form&gt;
        );
    }
});
...</pre>

O processo de envio é tratado em dois componentes diferentes. O componente do formulário trata o envio do próprio form, ativando o evento **ProductSubmit**. O tratamento deste evento, por sua vez, fica a cargo do elemento **ShoppingBox**, o container da nossa lista, responsável por atualizar seu estado e renderizar novamente nossa lista. Faz sentido, certo? Cada componente possui uma responsabilidade bem definida.

Para quem quiser conferir nosso exemplo funcionando: <a href="http://tableless.github.io/exemplos/react/" target="_blank">http://tableless.github.io/exemplos/react/</a> (código fonte: <a href="https://github.com/tableless/exemplos/tree/gh-pages/react" target="_blank">https://github.com/tableless/exemplos/tree/gh-pages/react</a>).

## Considerações finais

Apesar de ser uma biblioteca relativamente nova, a React já é utilizada em produção por Facebook e Instagram. Problemas como semântica e SEO, comuns a esse tipo de framework, continuam presentes. No entanto, se você vai desenvolver uma aplicação web, onde não temos esse tipo de preocupação, a React é uma ótima aposta como ferramenta.