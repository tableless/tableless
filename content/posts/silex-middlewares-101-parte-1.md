---
title: Silex Middlewares 101 – Parte 1
author: Nando Kstro Net
type: post
date: 2016-06-26
excerpt: 'Os middlewares no Silex são utilizados para mudar o comportamento padrão do mesmo, os middlewares se mostram muito úteis quando pensamos na validação de tokens de acesso, save de logs e muitas outras tarefas. Basicamente temos dois tipos de middlewares, os de aplicação e os de rota. '
url: /silex-middlewares-101-parte-1/
categories:
  - Back-end
  - Código
  - PHP
tags:
  - Micro Frameworks PHP
  - Middlewares Silex
  - Silex

---
Fala pessoal! Tudo bem? Espero que sim! Depois de uma longa temporada retorno com mais este post sobre o micro-framework Silex! Desta vez abordarei o uso dos middlewares no mesmo.

## Middlewares

Os middlewares no Silex são utilizados para mudar o comportamento padrão do mesmo, os middlewares se mostram muito úteis quando pensamos na validação de tokens de acesso, save de logs e muitas outras tarefas. Basicamente temos dois tipos de middlewares, os de aplicação e os de rota. Mostraremos as diferenças abaixo:

## Middlewares De Aplicação

Como o próprio nome já diz, esses middlewares impactam a aplicação como um todo e são três. Vamos ver como cada um funciona logo abaixo:

### Before Method

O método `before();` é sempre executado antes de suas rotas, no escopo de aplicação ele será acionado sempre que um usuário fizer alguma requisição a mesma. Veja o código abaixo:

<pre>&lt;?php
#...
$app = new Application();

$app-&gt;before(function(){
    //Sua lógica aqui.
});

$app-&gt;get('/', function(Application $app) {
    return $app-&gt;escape('Middlewares');
});

$app-&gt;run();
</pre>

Das linhas 5 a 7 temos a definição do nosso middleware `before`, como comentado, sempre que nossa aplicação for acessada, o middleware será acionado antes da execução da rota em questão. O before se torna muito útil para validação de tokens de acesso, validação de sessão, transformação de dados, dentre outros.

### After Method

O `after();`, apesar do nome sugestivo, não quer dizer que o mesmo será executado após a chamada da rota, calma vô explicar!
  
O `after` executa antes da saída do response da rota chamada!

<pre>&lt;?php
#...
$app-&gt;after(function(){
    //Exemplo
    print 'After Middleware | ';
});

$app-&gt;get('/', function(Application $app) {
    return $app-&gt;escape('Router Content!');
});

#...
</pre>

A saida do código acima seria algo como:
  
 ``Fala pessoal! Tudo bem? Espero que sim! Depois de uma longa temporada retorno com mais este post sobre o micro-framework Silex! Desta vez abordarei o uso dos middlewares no mesmo.

## Middlewares

Os middlewares no Silex são utilizados para mudar o comportamento padrão do mesmo, os middlewares se mostram muito úteis quando pensamos na validação de tokens de acesso, save de logs e muitas outras tarefas. Basicamente temos dois tipos de middlewares, os de aplicação e os de rota. Mostraremos as diferenças abaixo:

## Middlewares De Aplicação

Como o próprio nome já diz, esses middlewares impactam a aplicação como um todo e são três. Vamos ver como cada um funciona logo abaixo:

### Before Method

O método `before();` é sempre executado antes de suas rotas, no escopo de aplicação ele será acionado sempre que um usuário fizer alguma requisição a mesma. Veja o código abaixo:

<pre>&lt;?php
#...
$app = new Application();

$app-&gt;before(function(){
    //Sua lógica aqui.
});

$app-&gt;get('/', function(Application $app) {
    return $app-&gt;escape('Middlewares');
});

$app-&gt;run();
</pre>

Das linhas 5 a 7 temos a definição do nosso middleware `before`, como comentado, sempre que nossa aplicação for acessada, o middleware será acionado antes da execução da rota em questão. O before se torna muito útil para validação de tokens de acesso, validação de sessão, transformação de dados, dentre outros.

### After Method

O `after();`, apesar do nome sugestivo, não quer dizer que o mesmo será executado após a chamada da rota, calma vô explicar!
  
O `after` executa antes da saída do response da rota chamada!

<pre>&lt;?php
#...
$app-&gt;after(function(){
    //Exemplo
    print 'After Middleware | ';
});

$app-&gt;get('/', function(Application $app) {
    return $app-&gt;escape('Router Content!');
});

#...
</pre>

A saida do código acima seria algo como:
  
`` 
  
Um caso de uso para tal, seria a transformação do response dentre outras tarefas!

### Finish Method

Existe ainda o middleware `finish();`, esse sim! É executado após a execução da rota em questão!
  
Vamos ao exemplo:

<pre>&lt;?php
#...
$app-&gt;finish(function(){
    //Exemplo
    print 'Finish middleware';
});

$app-&gt;get('/', function(Application $app) {
    return $app-&gt;escape('Router Content | ');
});
#...
</pre>

A saída do código seria:
  
 ```Fala pessoal! Tudo bem? Espero que sim! Depois de uma longa temporada retorno com mais este post sobre o micro-framework Silex! Desta vez abordarei o uso dos middlewares no mesmo.

## Middlewares

Os middlewares no Silex são utilizados para mudar o comportamento padrão do mesmo, os middlewares se mostram muito úteis quando pensamos na validação de tokens de acesso, save de logs e muitas outras tarefas. Basicamente temos dois tipos de middlewares, os de aplicação e os de rota. Mostraremos as diferenças abaixo:

## Middlewares De Aplicação

Como o próprio nome já diz, esses middlewares impactam a aplicação como um todo e são três. Vamos ver como cada um funciona logo abaixo:

### Before Method

O método `before();` é sempre executado antes de suas rotas, no escopo de aplicação ele será acionado sempre que um usuário fizer alguma requisição a mesma. Veja o código abaixo:

<pre>&lt;?php
#...
$app = new Application();

$app-&gt;before(function(){
    //Sua lógica aqui.
});

$app-&gt;get('/', function(Application $app) {
    return $app-&gt;escape('Middlewares');
});

$app-&gt;run();
</pre>

Das linhas 5 a 7 temos a definição do nosso middleware `before`, como comentado, sempre que nossa aplicação for acessada, o middleware será acionado antes da execução da rota em questão. O before se torna muito útil para validação de tokens de acesso, validação de sessão, transformação de dados, dentre outros.

### After Method

O `after();`, apesar do nome sugestivo, não quer dizer que o mesmo será executado após a chamada da rota, calma vô explicar!
  
O `after` executa antes da saída do response da rota chamada!

<pre>&lt;?php
#...
$app-&gt;after(function(){
    //Exemplo
    print 'After Middleware | ';
});

$app-&gt;get('/', function(Application $app) {
    return $app-&gt;escape('Router Content!');
});

#...
</pre>

A saida do código acima seria algo como:
  
 ``Fala pessoal! Tudo bem? Espero que sim! Depois de uma longa temporada retorno com mais este post sobre o micro-framework Silex! Desta vez abordarei o uso dos middlewares no mesmo.

## Middlewares

Os middlewares no Silex são utilizados para mudar o comportamento padrão do mesmo, os middlewares se mostram muito úteis quando pensamos na validação de tokens de acesso, save de logs e muitas outras tarefas. Basicamente temos dois tipos de middlewares, os de aplicação e os de rota. Mostraremos as diferenças abaixo:

## Middlewares De Aplicação

Como o próprio nome já diz, esses middlewares impactam a aplicação como um todo e são três. Vamos ver como cada um funciona logo abaixo:

### Before Method

O método `before();` é sempre executado antes de suas rotas, no escopo de aplicação ele será acionado sempre que um usuário fizer alguma requisição a mesma. Veja o código abaixo:

<pre>&lt;?php
#...
$app = new Application();

$app-&gt;before(function(){
    //Sua lógica aqui.
});

$app-&gt;get('/', function(Application $app) {
    return $app-&gt;escape('Middlewares');
});

$app-&gt;run();
</pre>

Das linhas 5 a 7 temos a definição do nosso middleware `before`, como comentado, sempre que nossa aplicação for acessada, o middleware será acionado antes da execução da rota em questão. O before se torna muito útil para validação de tokens de acesso, validação de sessão, transformação de dados, dentre outros.

### After Method

O `after();`, apesar do nome sugestivo, não quer dizer que o mesmo será executado após a chamada da rota, calma vô explicar!
  
O `after` executa antes da saída do response da rota chamada!

<pre>&lt;?php
#...
$app-&gt;after(function(){
    //Exemplo
    print 'After Middleware | ';
});

$app-&gt;get('/', function(Application $app) {
    return $app-&gt;escape('Router Content!');
});

#...
</pre>

A saida do código acima seria algo como:
  
`` 
  
Um caso de uso para tal, seria a transformação do response dentre outras tarefas!

### Finish Method

Existe ainda o middleware `finish();`, esse sim! É executado após a execução da rota em questão!
  
Vamos ao exemplo:

<pre>&lt;?php
#...
$app-&gt;finish(function(){
    //Exemplo
    print 'Finish middleware';
});

$app-&gt;get('/', function(Application $app) {
    return $app-&gt;escape('Router Content | ');
});
#...
</pre>

A saída do código seria:
  
``` 
  
Muito útil para save de logs dentre outras tarefas!

## Conclusão

Esses são os middlewares de aplicação do Silex Framework, percebemos que os mesmos tornam nossos trabalhos bem mais simplificados em determinados casos, só precisamos tomar um pouco de cuidado para não deixa-los um tanto quanto complexos, evitando assim dor de cabeça futura!
  
Em nosso próximo post, ainda sobre Middlewares, abordaremos os middlewares de rotas e algumas particularidades dos middlewares como um todo!
  
O código completo deste post você pode encontrar no <a href="https://goo.gl/LI4BsY" target="_blank">gist</a>. Abraços e até a próxima!