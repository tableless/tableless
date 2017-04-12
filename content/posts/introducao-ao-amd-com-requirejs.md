---
title: Introdução ao AMD com Require.js
author: Lucas Caprio
type: post
date: 2015-08-14
excerpt: Aprenda agora em 4 passos simples a modularizar seu código JavaScript utilizando a especificação AMD com RequireJS.
url: /introducao-ao-amd-com-requirejs/
categories:
  - Código
  - JavaScript
tags:
  - amd
  - JavaScript
  - require.js

---
Antes de entrarmos no foco do artigo, é importantíssimo tocar no assunto **_modularização_**.

A modularização é um conceito muito antigo em termos computacionais, em poucas palavras, é a **separação de funcionalidades**, **redução de complexidade** e principalmente, o **reuso de código**.

O <a href="http://jcemer.com/" target="_blank">Jean Carlo Emer</a> postou um um artigo aqui mesmo muito bom sobre _Modularização em JavaScript._ Recomendo fortemente ler o <a href="http://tableless.com.br/modularizacao-em-javascript/" target="_blank">artigo na íntegra</a>. Nele, o autor também dá um exemplo com AMD e fala dos pontos fracos e fortes do uso.

### AMD

Buscando a modularização do código JavaScript, um dos padrões mais falados ultimamente é o Asyncronous Module Definition (AMD), consiste basicamente de que nossos módulos escritos podem ser requisitados assincronamente quando necessários.

### Require.js

O _script loader_ mais famoso da internet, o RequireJS é o cara responsável por carregar os nossos scripts assincronamente. A <a href="http://requirejs.org/" target="_blank">página do projeto</a> dá muito mais informações sobre compatibilidade e benefícios de seu uso.

## Exemplificando

Para exemplificar o AMD com RequireJS, vamos criar uma aplicação simples que usa o jQuery para pegar os números de dois inputs da tela, passa para outro módulo que faz apenas a soma desses números, e devolve para a aplicação principal.

Sim, apenas isso&#8230;

A intenção deste artigo é introduzir à estruturação, e como aplicar o AMD utilizando o RequireJS.

### 1º Passo: Adicione o require.js ao seu projeto

Faça o download no <a href="http://requirejs.org/docs/download.html" target="_blank">site oficial</a> (ou use CDN), e incorpore-o na aplicação:

<pre class="lang-html">&lt;script data-main="js/app" src="//cdnjs.cloudflare.com/ajax/libs/require.js/2.1.20/require.min.js"&gt;
    &lt;/script&gt;
&lt;/body&gt;
&lt;/html&gt;
</pre>

O atributo `data-main` diz ao RequireJS carregar o arquivo app.js, logo após que carregar o require.js.

### 2º Passo: Configuração

Dentro do arquivo _app.js_, vamos configurar da seguinte forma:

<pre class="lang-javascript">requirejs.config({
    "baseUrl": "js/modules",
    "paths": {
        "jquery": "//code.jquery.com/jquery-2.1.1.min",
        "main": "../main"
    }
});

// Chamando módulo principal para iniciar a aplicação
requirejs(["main"]);
</pre>

A propriedade `baseUrl` diz de onde os módulos serão carregados, exceto os que passamos em `paths`. Onde que o _main_ está em um diretório anterior de acordo com o diretório configurado no _baseUrl_. E o jQuery que vem por CDN.

Mais abaixo, chamamos o nosso módulo _main_, que será o módulo principal da aplicação.

### 3º Passo: Criando nosso módulo

No arquivo _modules/myModule.js_ criamos nosso simples módulo.

<pre class="lang-javascript">// Ou podemos declarar o nome explicitamente...
// define('myModule', function () {
define(function () {
    return {
        sum: function (a, b) {
            return (+a) + (+b);
        }
    }
});
</pre>

O grande <a href="http://addyosmani.com/" target="_blank">Addy Osmani</a>, publicou um <a href="http://addyosmani.com/writing-modular-js/" target="_blank">artigo muito bom</a> sobre JavaScript Modular, onde demonstra outras formas de declarar módulos AMD.

### 4º Passo: Criando o main.js

Neste arquivo é onde controlamos nossa aplicação, tendo como **dependência** dois módulos, _jquery_ e _myModule_. Ou seja, para iniciar o módulo main, temos que primeiro carregar suas dependências.

<pre class="lang-javascript">define(
    ["jquery", "myModule"],
    function ( $, myModule ) {
        $(function () {
            $('.btn').on('click', function () {
                var number1 = $('#number1').val();
                var number2 = $('#number2').val();
                alert(myModule.sum(number1, number2));
            });
        });
    }
);
</pre>

## Concluindo

Finalizamos por aqui pessoal, apesar do exemplo ser tão simples, acho que consegui introduzir o conceito necessário.

Disponibilizei o código do exemplo no <a href="http://plnkr.co/edit/OdLRwo62uV4KJPKSL4zh" target="_blank">Plunker</a>, dá uma olhada lá caso precise 😉

Abraço!