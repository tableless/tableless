---
title: Entendendo as diretivas e fazendo abas com AngularJS
author: Diego Eis
type: post
date: 2014-09-08
excerpt: As diretivas do AngularJS estendem o código HTML, atribuindo funcionalidades aos componentes. Entenda como as diretivas funcionam fazendo uma funcionalidade básica de abas (tabs).
url: /diretivas-angularjs-abas/
categories:
  - AngularJS
  - JavaScript
tags:
  - angularjs
  - JavaScript
  - js

---
O AngularJS é um framework em JavaScript para a criação de web apps. Uma das suas principais características é levar parte da lógica das funcionalidades dos componentes direto para o HTML a partir das diretivas.

O [Rodrigo Branas][1] define as diretivas assim:

<blockquote cite="rodrigo branas">
  <p>
    Diretivas são extensões da linguagem HTML que permitem a implementação de novos comportamentos de forma declarativa.
  </p>
</blockquote>

Isso quer dizer que você não vai precisar escrever um monte de JavaScripts para executar funções que deveriam ser simples, como abas, por exemplo. Vamos fazer agora a funcionalidade de abas, que é bastante conhecida de todo mundo. Isso vai fazer você entender melhor como a lógica das diretivas do AngularJS funciona.

## Iniciando as abas

Este é um HTML simples, com o código HTML básico que precisamos para formatar o visual e acomodar o conteúdo das abas. 



Ainda não há nenhuma funcionalidade, só estilo CSS. Vamos inserir as diretivas a partir de agora. se você for acompanhar por aí, basta chamar o AngularJS no seu exemplo:

<pre class="lang-html">&lt;script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.3.0-beta.19/angular.js"&gt;&lt;/script&gt;
</pre>

## Inserindo as diretivas

A primeira diretiva que precisamos inserir é a `ng-app` que vai iniciar o AngularJS, avisando que aquele pedaço de HTML é a minha aplicação e que ele vai apenas funcionar naquele escopo. Nesse meu exemplo, eu inseri `ng-app` no meu div `.container` que é o div que engloba tudo, mas geralmente esse `ng-app` é colocado na tag `html`.

<pre class="lang-html">&lt;div class="container" ng-app&gt;
</pre>

Se você quiser ler uma introdução básica sobre AngularJS, leia o artigo do Davi Ferreira, aqui mesmo no Tableless, explicando sobre [como iniciar uma aplicação simples com AngularJS][2].

Feito isso, vamos inserir algumas diretivas no HTML que fazemd as abas. Serão duas diretivas: `ng-click` e `ng-class`. 

<pre class="lang-html">&lt;ul class="tabs-nav"&gt;
  &lt;li&gt;&lt;a ng-click="tab=1" ng-class="{'active' : tab==1}"&gt;Aba 1&lt;/a&gt;&lt;/li&gt;
  &lt;li&gt;&lt;a ng-click="tab=2" ng-class="{'active' : tab==2}"&gt;Aba 2&lt;/a&gt;&lt;/li&gt;
  &lt;li&gt;&lt;a ng-click="tab=3" ng-class="{'active' : tab==3}"&gt;Aba 2&lt;/a&gt;&lt;/li&gt;
&lt;/ul&gt;
</pre>

A [diretiva ng-click][3] detecta o click no elemento e executa algum comportamento. Nesse caso ele vai definir uma variável contextual chamada `tab` atribuindo o valor **1, 2 ou 3** para essa variável, dependendo da aba clicada.

A [diretiva ng-class][4] permite adicionar uma classe dinamicamente no elemento por meio de uma expressão. O valor que adicionamos ali é uma condicional: `{'active' : tab==1}`. Adicione a classe **active** se a variável **tab** for igual a **1**. Colocamos essa condição em todas as nossas tabs.

Agora, para fecharmos, vamos adicionar mais uma diretiva chamada `ng-show` nos conteúdos das respectivas tabs. A [diretiva ng-show][5] mostra ou esconde o elemento baseado em alguma expressão ou condicional. Nesse nosso caso a condicional é simples: `tab == 1`. Se a variável **tab** for igual a **1**, mostra aquele elemento. Fazemos isso em todos os conteúdo das abas.

<pre class="lang-html">&lt;div class="tabs-container"&gt;
	&lt;div class="tab-content" ng-show="tab == 1"&gt;
		&lt;h3&gt;Primeira aba&lt;/h3&gt;
		&lt;p&gt;Lorem ipsum...&lt;/p&gt;
	&lt;/div&gt;

	&lt;div class="tab-content" ng-show="tab == 2"&gt;
		&lt;h3&gt;Segunda aba&lt;/h3&gt;
		&lt;p&gt;Lorem ...&lt;/p&gt;
	&lt;/div&gt;

	&lt;div class="tab-content" ng-show="tab == 3"&gt;
		&lt;h3&gt;Terceira aba&lt;/h3&gt;
		&lt;p&gt;Lorem ...&lt;/p&gt;
	&lt;/div&gt;
&lt;/div&gt;
</pre>

Perceba que o AngularJS já começa a fazer a mágica aqui. O `ng-click` cria a variável `tab` e já atribui um valor. O `ng-class` verifica essa variável, se for igual ao valor determinado, ele adiciona a classe. O `ng-show` já faz o trabalho de mostrar ou não os conteúdos de acordo com a aba clicada, verificando o valor atual da variável `tab`. Sem JavaScript, baby! Veja o exemplo completo abaixo:



Agora sua cabeça começa a fundir, porque as abas funcionam, perfeitamente e toda a lógica disso está no HTML. Isso é bom? Poxa, talvez sim, talvez não.

Opa! Faltou uma diretiva&#8230; Essa se chama `ng-init`. A [diretiva ng-init][6] permite avaliar e modificar uma expressão dentro de um determinado escopo. O escopo, no caso desse exemplo, é tudo que está no `ng-app`. Vamos colocar esse atributo junto com o ng-app: `ng-init="tab=1"`. Isso define o valor inicial de 1 para a variável **tab**. Isso faz com que nossa primeira tab seja iniciada logo no load do documento.</p> 

A primeira vez que mexi com AngularJS e fiz algo bem básico, logo pensei: essa coisa é mágica. E muitas vezes é. As diretivas são parte dos princípios do AngularJS. São elas que farão boa parte das mágicas. Mas preciso avisar: é a parte mais difícil de engolir do AngularJS. Ainda é muito difícil para mim assimilar que parte das funcionalidades não são tratadas no JavaScript como fazemos todos os dias, mas no HTML. Isso pode parecer bastante estranho logo no início por que a lógica das funcionalidades pode ficar bastante espalhada entre JS e HTML, mas vou voltar a falar sobre isso em outros artigos.

O exemplo das tabs e uma aplicação básica de ToDo que fiz com AngualrJS pode ser visto direto [aqui no meu GitHub][7].

 [1]: http://twitter.com/rodrigobranas
 [2]: http://tableless.com.br/criando-uma-aplicacao-simples-com-angularjs/ "Criando uma aplicação simples com AngularJS"
 [3]: https://docs.angularjs.org/api/ng/directive/ngClick
 [4]: https://docs.angularjs.org/api/ng/directive/ngClass
 [5]: https://docs.angularjs.org/api/ng/directive/ngShow
 [6]: https://docs.angularjs.org/api/ng/directive/ngInit
 [7]: https://github.com/diegoeis/angular-tests