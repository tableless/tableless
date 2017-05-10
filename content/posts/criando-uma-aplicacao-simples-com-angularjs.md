---
title: Criando uma aplicação simples com AngularJS
author: Davi Ferreira
type: post
date: 2012-07-26
excerpt: Com a missão de enriquecer o vocabulário HTML o framework AngularJS chega com a marca Google de simplicidade e promete um workflow diferente para os desenvolvedores.
url: /criando-uma-aplicacao-simples-com-angularjs/
tweetbackscheck:
  - 1356422885
shorturls:
  - 'a:3:{s:9:"permalink";s:31:"http://tableless.com.br/?p=6496";s:7:"tinyurl";s:26:"http://tinyurl.com/bu5nx7l";s:4:"isgd";s:19:"http://is.gd/VvUXaS";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 780697075
categories:
  - JavaScript
tags:
  - angularjs
  - JavaScript
  - mvc

---
AngularJS é o mais novo lançamento do time de desenvolvedores do Google. Diferentemente de outros frameworks JavaScript, ele adota uma abordagem mais ligada à sintaxe HTML, funcionando como uma espécie de extensão da linguagem.

Neste artigo, vamos criar uma aplicação simples de lista de compras e aprender os conceitos básicos do framework no que diz respeito à associação, manipulação e exibição de dados.

## Estrutura inicial

Assim como qualquer aplicação web, nosso ponta-pé inicial acontece com a criação de um página básica. A diferença aqui é que vamos informar um nova propriedade na tag do nosso arquivo: **ng-app**.

<pre class="lang-html">&lt;html ng-app&gt;
    &lt;head&gt;
        &lt;title&gt;Lista de compras&lt;/title&gt;
        &lt;script src="http://code.angularjs.org/1.0.1/angular-1.0.1.min.js"&gt;&lt;/script&gt;
    &lt;/head&gt;
    &lt;body&gt;
    &lt;/body&gt;
&lt;/html&gt;</pre>

Essa é a grande sacada do AngularJS. Ao declarar a propriedade ng-app, estamos inicializando a nossa aplicação. É a primeira de algumas novas propriedades que iremos utilizar. Todo o funcionamento do framework gira em torno dessas novas declarações.

O atributo ng-app na tag informa que o nosso DOM, além de HTML, é também um documento AngularJS. Esta propriedade pode ser utilizada em qualquer elemento do DOM &mdash; em alguns casos, apenas uma parte do seu HTML será uma aplicação Angular. Por baixo dos panos, o framework define o elemento com o atributo ng-app como a raiz da aplicação.

## Olá, Tableless!

Para provar que o foco do Angular está no HTML e não no JavaScript, vamos implementar um exemplo simples em nossa estrutura:

<pre class="lang-html">&lt;html ng-app&gt;
    &lt;head&gt;
        &lt;title&gt;AngularJS - Tableless&lt;/title&gt;
        &lt;script src="http://code.angularjs.org/1.0.1/angular-1.0.1.min.js"&gt;&lt;/script&gt;
    &lt;/head&gt;
    &lt;body&gt;
        &lt;input type="text" ng-model="nome"&gt;
        &lt;p&gt;Olá, Tableless! Meu nome é: {{ nome }}&lt;/p&gt;
    &lt;/body&gt;
&lt;/html&gt;</pre>

Ao carregarmos esse HTML no navegador e digitarmos qualquer coisa no input, o parágrafo é atualizado automagicamente. Perceberam que até agora não escrevemos nenhum código JavaScript?

A propriedade _ng-model_ funciona como um canal entre a nossa view e o form. Ela pode ser utilizada em inputs do tipo texto, selects, textareas, checkboxes e radio buttons. 

O model, seus dados e suas validações ficam automaticamente disponíveis no escopo da nossa aplicação, como veremos a seguir.

A associação de dados é feita através do famoso &#8220;bigode-bigode&#8221; ({{ }}), passando nomes presentes no escopo (no exemplo acima, o model **nome**).

## Enfim, JavaScript!

Chegou a hora de escrevermos nosso primeiro trecho de código JavaScript. Vamos criar um controller para nossa aplicação que carrega uma lista inicial de ítens. Os ítens são armazenados no escopo da aplicação ($scope).

<pre class="lang-javascript">function ListaComprasController($scope) {
    $scope.itens = [
        {produto: 'Leite', quantidade: 2, comprado: false},
        {produto: 'Cerveja', quantidade: 12, comprado: false}
    ];
}</pre>

E é só isso por enquanto!

## Exibindo nossos ítens

Vamos agora adicionar um novo bloco HTML com a tabela de listagem dos produtos:

<pre class="lang-html">&lt;div ng-controller="ListaComprasController"&gt;
    &lt;table&gt;
      &lt;thead&gt;
        &lt;tr&gt;
          &lt;th&gt;Produto&lt;/th&gt;
          &lt;th&gt;Quantidade&lt;/th&gt;
        &lt;/tr&gt;
      &lt;/thead&gt;
      &lt;tbody&gt;
        &lt;tr ng-repeat="item in itens"&gt;
          &lt;td&gt;&lt;strong&gt;{{ item.produto }}&lt;/strong&gt;&lt;/td&gt;
          &lt;td&gt;{{ item.quantidade }}&lt;/td&gt;
        &lt;/tr&gt;
      &lt;/tbody&gt;
    &lt;/table&gt;
&lt;/div&gt;</pre>

Duas novidades foram apresentadas no HTML acima:

  * o atributo **ng-controller** informa o nome do controller JavaScript responsável pelo bloco contido no elemento, no nosso caso o controller _ListaComprasController_ definido anteriormente. 
  * o atributo **ng-repeat** executa um _loop_ na variável **itens** declarada no escopo da aplicação, retornando cada ítem e imprimindo o produto e a quantidade em uma linha da nossa tabela. O formato é: <retorno> in <coleção>. 

## Adicionando produtos

Para não ficarmos apenas com 4 linhas de JavaScript, vamos adicionar uma funcionalidade que inclui ítens em nossa lista de compras.

O primeiro passo é criar um formulário que será responsável pela ação:

<pre class="lang-html">&lt;form class="form-inline" name="formItem"&gt;
  &lt;input type="text" ng-model="item.produto"&gt;
  &lt;input type="number" ng-model="item.quantidade"&gt;
  &lt;button ng-click="adicionaItem()"&gt;adicionar ítem&lt;/button&gt;
&lt;/form&gt;</pre>

Estamos utilizando de novo o atributo **ng-model** para definir um model para os nossos inputs. O controller passa a receber diretamente informações sobre esses campos.

A novidade dessa vez fica por conta do atributo **ng-click**, que recebe uma função que precisamos declarar no controller:

<pre class="lang-javascript">function ListaComprasController($scope) {
    $scope.itens = [
        {produto: 'Leite', quantidade: 2, comprado: false},
        {produto: 'Cerveja', quantidade: 12, comprado: false}
    ];

    $scope.adicionaItem = function () {
        $scope.itens.push({produto: $scope.item.produto,
                           quantidade: $scope.item.quantidade,
                           comprado: false});
        $scope.item.produto = $scope.item.quantidade = '';
    };
}</pre>

Ao clicarmos no botão, o produto é adicionado à tabela. Aqui o model poderia estar realizando diversas validações disponíveis na API do framework entre outras coisas. Porém, no nosso exemplo, apenas adicionamos um novo ítem à lista de produtos e em seguida limpamos os models (os campos do formulário).

## Testes

Por ser um framework que demanda um código JavaScript mais estruturado, fica bem simples testar sua aplicação. Utilizando <a href="http://tableless.com.br/testando-seu-codigo-jquery-com-jasmine-parte-1/" target="_blank">Jasmine</a>, por exemplo, poderíamos facilmente testar o controller dessa forma:

<pre class="lang-javascript">describe('Lista Compras Unitário', function () {
    describe('ListaComprasController', function () {
        beforeEach(function () {
            this.$scope = {};
            this.controller = new ListaComprasController(this.$scope);
        });

        it('deve criar "itens" com 2 ítens', function () {
            expect(this.$scope.itens.length).toBe(2);
        });

        describe('adicionaItem', function () {
            it('deve adicionar um novo ítem à lista com dados do escopo', function () {
                this.$scope.item = {};
                this.$scope.item.produto = 'Carne';
                this.$scope.item.quantidade = 5;
                this.$scope.adicionaItem();
                expect(this.$scope.itens.length).toBe(3);
                expect(this.$scope.itens[2].produto).toBe('Carne');
                expect(this.$scope.itens[2].quantidade).toBe(5);
                expect(this.$scope.itens[2].comprado).toBeFalse;
            });
        });
    });
});</pre>

## AngularJS é muito mais do que isso!

Deixei muitos tópicos de fora por enquanto. O objetivo aqui era mostrar o potencial do framework AngularJS. Seus recursos ainda incluem rotas, múltiplas views, AJAX e serviços REST e a criação de componentes personalizados. O que vocês viram foi o básico do básico, uma introdução.

No <a href="http://angularjs.org/" target="_blank">site do framework</a> há uma documentação bem completa, com diversos tutoriais.

O código fonte do nosso exemplo vocês encontram no <a href="https://github.com/tableless/exemplos/tree/gh-pages/angularjs/lista-compras/" target="_blank">Github do Tableless</a>. E <a href="http://tableless.github.com/exemplos/angularjs/lista-compras/" target="_blank">nesse link</a> vocês conseguem visualizar nossa lista de compras em ação.

Finalizando, nosso camarada Vedovelli gravou um <a href="http://blog.vedovelli.com.br/?p=1946" target="_blank">screencast</a> bem completo sobre o AngularJS, recomendo!