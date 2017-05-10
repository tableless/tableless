---
title: JavaScript de forma assíncrona e legível
author: Igor Ribeiro Lima
type: post
date: 2013-12-30
url: /javascript-de-forma-assincrona-e-legivel/
dsq_thread_id: 2082284439
categories:
  - Geral
  - JavaScript
tags:
  - callback hell
  - JavaScript
  - JavaScript legível

---
A programação assíncrona possui a vantagem de gerar códigos perfomáticos. Em certos casos, a implementação de diversas funções assíncronas encadeadas através de funções _callback_ pode prejudicar a leitura e a manutenção do código. Para demonstrar esse encadeamento, vamos utilizar um trecho de código que utiliza a [API do Selenium 2][1]. Baseado em um [exemplo do site do SauceLabs][2].

A API do Selenium WebDriver pode ser utilizada por diversas linguagem de programação, porém, em nosso exemplo, iremos utilizar o NodeJS (JavaScript) e o gerenciador de pacotes NPM, que podem ser baixados no [site oficial][3]. O NPM é necessário para instalar o [PhantomJS][4] e o [WD][5], utilizando o seguinte _script_:

<pre class="lang-ssh">npm install -g phantomjs</pre>

<pre class="lang-ssh">npm install wd</pre>

O NodeJS possui dois tipos de dependências: global ou local. Quando uma dependência é global, o pacote passa a ser executável, tornando possível a utilização da dependência através da linha de comando. Já as dependências locais são instaladas no diretório corrente, dentro de _node_modules_.

O primeiro _script_, utilizando o parâmetro **-g**, instala o [PhantomJS][4] como dependência global, que é um WebKit headless totalmente em JavaScript e possui suporte rápido e nativo para vários padrões web como manipulação de DOM, seletores CSS, JSON, Canvas e SVG.

Já o segundo _script_, instala como dependência local o [WD][5], que é um cliente NodeJS para facilitar o acesso à API do Selenium 2 e suporta [métodos][6] como: fazer requisições GET e POST, clicar no botão VOLTAR do navegador, fazer refresh no navegador, pegar um _printscreen_ da tela atual, redimensionar e mover a janela do navegador, submeter formulário, digitar texto, usar _cookies_, selecionar um elemento DOM, clicar e mover um elemento, etc.

Após a instalação das dependências, vamos criar um arquivo com [vários _callbacks_ encadeados][7]. Esse código possui seis passos: _(i)_ abrir o navegador, _(ii)_ acessar uma página de teste, _(iii)_ verificar o título da página, _(iv) _submeter um formulário, _(v)_ verificar a url da página após enviar o formulário e _(vi)_ fechar o navegador. Algo bem simples. Suficiente para ressaltar a quantidade de _callbacks_ encadeados.

**um-exemplo-COM-varios-callbacks-encadeados.js**

<pre class="lang-js">var webdriver = require('wd'),
    assert    = require('assert'),
    browser   = webdriver.remote({
      hostname: "localhost",
      port: 8910
    });

browser.init({}, function(erro, id_da_sessao, recursos_webdriver) {
  console.log('navegador aberto');
  browser.get("http://saucelabs.com/test/guinea-pig", function(erro) {
    console.log('pagina de teste aberta');
    browser.title(function(erro, title) {
      console.log('verificando titulo da pagina...');
      assert.ok( title.indexOf('I am a page title - Sauce Labs')===0, 'titulo NAO esta correto');
      browser.elementById('submit', function(erro, elemento) {
        console.log('botao enviar encontrado');
        browser.clickElement(elemento, function(erro) {
          console.log('botao clicado');
          browser.eval("window.location.href", function(erro, href) {
            console.log('verificando url da pagina...');
            assert.ok(href.indexOf('guinea')&gt;0, 'pagina NAO esta correta');
            browser.quit(function(erro){
              console.log('navegador fechado');
            });
          });
        });
      });
    });
  });
});</pre>

Um detalhe importante sobre assincronismo é que, na maioria dos casos, os _callbacks_ possuem como parâmetro uma variável de erro, que serve para impedir a execução dos _callbacks_ subsequentes, caso haja algum problema.

Criado o arquivo exemplo, é preciso, em um outro terminal, rodar o PhantomJS em modo WebDriver, digitando o seguinte comando:

<pre class="lang-ssh">phantomjs --webdriver=localhost:8910</pre>

Com o PhantomJS rodando em segundo plano, execute o exemplo usando o _node_. Segue o comando e uma ilustração do resultado obtido:

<pre class="lang-ssh">node um-exemplo-COM-varios-callbacks-encadeados.js</pre>

![ilustração do resultado obtido após executar o exemplo COM vários callbacks encadeados][8]

Para evitar tantos _callbacks_ encadeados, vamos utilizar a biblioteca [Async][9] que prover várias funções que facilitam a programação assíncrona em JavaScript. Nesse exemplo, usaremos a função [**waterfall**][10]. Uma alternativa mais leve para código Front-End é a biblioteca [Underscore][11]. Para instalar o Async, utilize o seguinte _script_:

<pre class="lang-ssh">npm install async</pre>

Agora vamos criar um outro arquivo sem tantos encadeamentos.

**um-exemplo-SEM-varios-callbacks-encadeados.js**

<pre class="lang-js">var webdriver = require('wd'),
    async     = require('async'),
    assert    = require('assert'),
    browser   = webdriver.remote({
      hostname: "localhost",
      port: 8910
    });

async.waterfall([
  function(callback_navegador_aberto) {
    browser.init({}, callback_navegador_aberto);
  },
  function(id_da_sessao, recursos_webdriver, callback_pagina_aberta) {
    console.log('navegador aberto');
    browser.get("http://saucelabs.com/test/guinea-pig", callback_pagina_aberta);
  },
  function(callback_titulo) {
    console.log('pagina de teste aberta');
    browser.title(callback_titulo);
  },
  function(title, callback_elemento_encontrado) {
    console.log('verificando titulo da pagina...');
    assert.ok( title.indexOf('I am a page title - Sauce Labs')===0, 'titulo NAO esta correto');
    browser.elementById('submit', callback_elemento_encontrado);
  },
  function(elemento, callback_botao_clicado) {
    console.log('botao enviar encontrado');
    browser.clickElement(elemento, callback_botao_clicado);
  },
  function(callback_verificar_url) {
    console.log('botao clicado');
    browser.eval("window.location.href", callback_verificar_url);
  },
  function(href, callback_navegador_fechado) {
    console.log('verificando url da pagina...');
    assert.ok(href.indexOf('guinea')&gt;0, 'pagina NAO esta correta');
    browser.quit(callback_navegador_fechado);
  },
  function(callback_final) {
    console.log('navegador fechado');
    callback_final();
  }
], function(erro){
  erro && console.log('algum erro ocorreu', erro);
});</pre>

Lembre-se que o PhantomJS ainda deve estar rodando em segundo plano para executar o segundo código de exemplo. Segue o comando e uma ilustração do resultado obtido:

<pre class="lang-ssh">node um-exemplo-SEM-varios-callbacks-encadeados.js</pre>

![ilustração do resultado obtido após executar o exemplo SEM vários callbacks encadeados][12]

Esse trecho de código exemplifica como vários _callbacks_ encadeados podem ser evitados com o uso de uma estrutura de controle. Para quem se interessar, todo código está disponível em um [gist][13]. Muito obrigado.

 [1]: http://tableless.com.br/introducao-ao-selenium-2/ "Introdução ao Selenium 2"
 [2]: https://saucelabs.com/docs/ondemand/getting-started/env/js/se2/linux "Exemplo oficial do SauceLabs de como utilizar o Selenium 2 com o NodeJS"
 [3]: http://nodejs.org/download/ "Site oficial do NodeJS"
 [4]: http://phantomjs.org/ "Site oficial do PhantomJS"
 [5]: https://github.com/admc/wd "Repositório GitHub do WD"
 [6]: https://github.com/admc/wd/blob/master/doc/api.md "Documentação da API do WD"
 [7]: http://callbackhell.com/ "Introdução sobre callback hell - vários callbacks encadeados"
 [8]: https://a248.e.akamai.net/camo.github.com/4e876b931ca0cd673f3707ebdc8bd60407ae1b9d/687474703a2f2f69313336382e70686f746f6275636b65742e636f6d2f616c62756d732f61673138322f69676f727269626569726f6c696d612f756d2d6578656d706c6f2d434f4d2d766172696f732d63616c6c6261636b732d656e6361646561646f735f7a707362636262323735642e706e67
 [9]: https://github.com/caolan/async "Repositório GitHub da biblioteca Async"
 [10]: https://github.com/caolan/async#waterfall "âncora para as especificações da função waterfall da biblioteca Async"
 [11]: http://underscorejs.org/ "Site oficial da biblioteca Underscore"
 [12]: http://i1368.photobucket.com/albums/ag182/igorribeirolima/um-exemplo-SEM-varios-callbacks-encadeados_zps1a8a9ad0.png
 [13]: https://gist.github.com/igorlima/7930016 "Gist - JavaScript de forma assíncrona e elegível"