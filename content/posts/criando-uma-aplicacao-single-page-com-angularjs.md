---
title: Criando uma aplicação Single Page com AngularJS
author: Lucas Caprio
type: post
date: 2014-06-22
excerpt: O AngularJS oferece muitos recursos ao desenvolvedor, neste artigo vamos conhecer o de Single Page, utilizando ngView e ngRoute.
url: /criando-uma-aplicacao-single-page-com-angularjs/
dsq_thread_id: 2724224676
categories:
  - Artigos
  - JavaScript
  - Técnicas e Práticas
tags:
  - angularjs
  - ngroute
  - ngview
  - single page

---
Um dos melhores conceitos que o AngularJS oferece é o de &#8220;Single Page&#8221;, onde os recursos apropriados são dinamicamente carregados e adicionados à página, conforme necessário, geralmente em resposta a ações do usuário.

Para isto acontecer o framework oferece módulos que te possibilitam ter apenas uma página index, com outras páginas de conteúdo (views) sendo carregadas de acordo com uma específica rota (route).

Deste modo, você consegue separar bem as responsabilidades do seu projeto, e ficando de fácil manutenção e codificação dos elementos.

Vamos parar de enrolação e ver como isso funciona em um rápido exemplo&#8230;

## Estrutura de pastas

Primeiro criamos uma estrutura de pastas simples para o exemplo:

<pre>app
    controllers
        controllers.js
    views
        home.html
        sobre.html
        contato.html
    app.js
index.html
</pre>

## Configurando a aplicação

É aqui que o show acontece, no arquivo app.js, primeiro, carregamos o módulo ngRoute que é usado para **deep-linking URLs** para controllers e views. Este módulo observa qual é url ($location.url()) e tenta mapear o caminho de acordo com alguma rota pré-definida, assim ele consegue executar o controller e a view correspondente para cada url.

Para setarmos uma configuração no AngularJS, precisamos usar a função **config**, que pode receber diversas propriedades já existentes do angular.

<pre lang="javascript">var app = angular.module('app',['ngRoute']);

app.config(function($routeProvider, $locationProvider)
{
   // remove o # da url
   $locationProvider.html5Mode(true);

   $routeProvider

   // para a rota '/', carregaremos o template home.html e o controller 'HomeCtrl'
   .when('/', {
      templateUrl : 'app/views/home.html',
      controller     : 'HomeCtrl',
   })

   // para a rota '/sobre', carregaremos o template sobre.html e o controller 'SobreCtrl'
   .when('/sobre', {
      templateUrl : 'app/views/sobre.html',
      controller  : 'SobreCtrl',
   })

   // para a rota '/contato', carregaremos o template contato.html e o controller 'ContatoCtrl'
   .when('/contato', {
      templateUrl : 'app/views/contato.html',
      controller  : 'ContatoCtrl',
   })

   // caso não seja nenhum desses, redirecione para a rota '/'
   .otherwise ({ redirectTo: '/' });
});
</pre>

Neste exemplo recebemos duas propriedades, $locationProvider e $routeProvider.

O **$routeProvider** é usado para configurar as rotas, que é exatamente o que estamos fazendo, quando usamos o **.when()**, definimos a rota (url) e depois um objeto com o templateUrl (url da view) e qual nome do controller correspondente.

O **$locationProvider** é usado para configurar como a aplicação com os chamados &#8220;deep-linking&#8221; irão ser armazenados, no nosso caso nós usamos a propriedade para definir true o modo de html5 (html5Mode), isso faz com que não fique com # nas URLs.

## Definindo os controllers

Para criar um controller no angular, podemos usar a instância do módulo, que definimos anteriormente como &#8220;app&#8221;, deste modo definimos um controller mais modular (é como prefiro :]) ou de forma tradicional como sempre criamos funções no JavaScript (function HomeCtrl($rootScope, $location){ //do stuff&#8230; }).

Por ser apenas um exemplo, coloquei todos meus controllers no mesmo arquivo, mas se você quiser pode colocar em arquivos diferentes, só não esqueça de linka-los à index.

Criaremos o primeiro controller com o nome de &#8216;HomeCtrl&#8217;, igual ao que definimos nas rotas mais acima, estamos passando para ele dois parâmetros, $rootScope e $location, já definidos no Angular.

<pre lang="javascript">app.controller('HomeCtrl', function($rootScope, $location)
{
   $rootScope.activetab = $location.path();
});

app.controller('SobreCtrl', function($rootScope, $location)
{
   $rootScope.activetab = $location.path();
});

app.controller('ContatoCtrl', function($rootScope, $location)
{
   $rootScope.activetab = $location.path();
});
</pre>

Note que para cada controller, realizamos a mesma funcionalidade, para saber em qual página estou, criei uma variável no $rootScope, o que a torna global na página, podendo ser acessada de qualquer local.
  
Para a variável activetab atribuímos o caminho da localização que estamos, no caso, seria atribuído &#8216;/&#8217; logo quando acessamos o exemplo.

## Eis a Single Page!

Aqui está nossa index, ela servirá para carregar os nossos templates definidos previamente nas rotas.

Nesta página contemos algumas **diretivas** (directives) do próprio angular, mas o que é uma diretiva?
  
Basicamente, diretivas em angular são atributos de tags HTMLs que definem o comportamento do mesmo. O próprio angular já oferece muitas diretivas, mas você pode criar a sua própria se desejar.

O recomendado quando se usa AngularJS e você deseja fazer alterações no DOM, é criar uma diretiva personalizada para tal&#8230;

<pre>&lt;!doctype html&gt;
&lt;html ng-app="app"&gt;
   &lt;head&gt;
      &lt;meta http-equiv="Content-Type" content="text/html; charset=utf-8" /&gt;
      &lt;meta http-equiv="content-language" content="pt-br" /&gt;
      &lt;title&gt;AngularJS: Single Page com ngView e ngRoute&lt;/title&gt;
      &lt;link rel="stylesheet" href="//netdna.bootstrapcdn.com/bootstrap/3.0.0/css/bootstrap.min.css" /&gt;
   &lt;/head&gt;

   &lt;body&gt;
      &lt;ul class="nav nav-tabs"&gt;
         &lt;li ng-class="{active: activetab == '/'}"&gt;&lt;a href="#/home"&gt;Home&lt;/a&gt;&lt;/li&gt;
         &lt;li ng-class="{active: activetab == '/sobre'}"&gt;&lt;a href="#/sobre"&gt;Sobre&lt;/a&gt;&lt;/li&gt;
         &lt;li ng-class="{active: activetab == '/contato'}"&gt;&lt;a href="#/contato"&gt;Contato&lt;/a&gt;&lt;/li&gt;
      &lt;/ul&gt;

      &lt;div ng-view&gt;&lt;/div&gt;

      &lt;script src="//ajax.googleapis.com/ajax/libs/angularjs/1.2.8/angular.min.js"&gt;&lt;/script&gt;
      &lt;script src="//ajax.googleapis.com/ajax/libs/angularjs/1.2.0rc1/angular-route.min.js"&gt;&lt;/script&gt;

      &lt;script src="app/app.js"&gt;&lt;/script&gt;
      &lt;script src="app/controllers/controllers.js"&gt;&lt;/script&gt;
   &lt;/body&gt;
&lt;/html&gt;
</pre>

Note que a linha mais importante de código aqui é a que contém a diretiva **ng-view**, é ali que seus templates irão carregar, aquilo que você definiu previamente nas rotas, irão ser abertas dentro desta div.

Para usarmos o conceito de Single Page no angular, é necessário usarmos a diretiva ng-view. Ela é a responsável por renderizar suas devidas &#8216;views&#8217; à sua index principal.

Para cada rota, definimos uma view anteriormente, certo?
  
Àquelas views serão carregadas dentro desta div, dependendo da rota que o usuário estiver.

Mesmo não sendo o foco do artigo, coloquei uma diretiva **ng-class** para adicionar a classe active ao elemento <li> se a condição for verdadeira. Ou seja, quando o controller é ativado pelo angular, ele atribui na variável activetab a sua localização atual.

Se estivermos na rota &#8216;/&#8217; a classe active irá ser adicionada ao primeiro elemento <li>.
  
Se estivermos na rota &#8216;/sobre&#8217; a classe active irá ser adicionada ao segundo elemento <li>.
  
Se estivermos na rota &#8216;/contato&#8217; a classe active irá ser adicionada ao terceiro elemento <li>.

## Criando as views

Como é apenas um exemplo, procurei agilidade, então, os templates são praticamente iguais.

<pre>&lt;!-- home.html --&gt;
&lt;div class="page-header"&gt;
   &lt;h1&gt;Página Home!&lt;/h1&gt;
&lt;/div&gt;
</pre>

<pre>&lt;!-- sobre.html --&gt;
&lt;div class="page-header"&gt;
   &lt;h1&gt;Página Sobre!&lt;/h1&gt;
&lt;/div&gt;
</pre>

<pre>&lt;!-- contato.html --&gt;
&lt;div class="page-header"&gt;
   &lt;h1&gt;Página Contato!&lt;/h1&gt;
&lt;/div&gt;
</pre>

Finalizamos por aqui pessoal, a ideia era de passar exatamente como criamos uma aplicação Single Page com AngularJS, espero que todos consigam!