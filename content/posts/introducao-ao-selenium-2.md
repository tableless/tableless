---
title: Introdução ao Selenium 2
author: Igor Ribeiro Lima
type: post
date: 2013-12-18
excerpt: Entenda mais sobre Selenium e entenda como ele pode ajudar em aplicações web.
url: /introducao-ao-selenium-2/
dsq_thread_id: 2039029598
categories:
  - JavaScript
  - Técnicas e Práticas
tags:
  - bdd
  - JavaScript
  - Selenium
  - tdd
  - webdriver

---
[Selenium][1] é uma ferramenta de apoio às necessidades de testes em aplicações web. Altamente flexível, permite muitas opções para a localização de elementos de interface no navegador e simular comportamentos reais de um usuário. A [versão 2.0][2] tem como funcionalidade primária a integração da API WebDriver. Projetado para fornecer uma interface ainda mais simples, concisa e orientada a objeto, o que melhora de forma significativa o suporte aos problemas complexos que são enfrentados ao testar uma aplicação web.

Essa API pode ser chamada através de diversas linguagem de programação, porém, em nosso exemplo, iremos utilizar o NodeJS (JavaScript), que pode ser baixado no [site oficial][3] e que possui um gerenciador de pacotes (Node Package Manager – NPM), o qual permite a interação com um repositório online via linha de comando, facilitando a instalação de várias outras ferramentas.

Nesse exemplo, será utilizado uma ferramenta chamada [Vows][4], gerenciada e instalada pelo NPM, que ajuda no desenvolvimento orientado a comportamento assíncrono. Usar testes assíncronos no NodeJS tem dois motivos. Primeiro (e talvez óbvio), é que o NodeJS é assíncrono e por isso os testes também deveriam ser. Segundo, é fazer com que os testes, os quais lidam com entrada e saída de dados, rodem mais rápido.

Breve resumo dos conceitos do Vows. **Suite**: um objeto que contêm um ou mais batches, e pode ser executado ou exportado. **Batch**: uma estrutura de contextos. **Context**: um objeto que pode conter um _topic_(opcional), nenhum ou mais _vows_, nenhum ou mais _sub-contexts_. **Topic**: pode ser tanto um valor ou uma função de código assíncrono. **Vow**: é uma função que recebe o _topic_ como um argumento e roda assertivas no _topic_.

O teste que será feito possui quatro passos: _(i)_ abrir o navegador, _(ii)_ acessar uma [página de teste][5], _(iii)_ verificar o título da página e _(iv)_ fechar o navegador. Algo bem simples. Suficiente para experimentar a versão 2.0 do Selenium.

As dependências necessárias podem ser instaladas usando o NPM, digitando o seguinte _script_ no terminal:

<pre class="lang-ssh">npm install -g phantomjs vows </pre>

<pre class="lang-ssh"> npm install chai wd vows </pre>

Há duas maneiras de instalar [dependências no NodeJS][6]: globalmente ou localmente. Quando uma dependência é global, os arquivos são executáveis, tornando possível a utilização de uma dependência através da linha de comando. Quanto às dependências locais, estas são instaladas no diretório corrente, dentro de um diretório chamado _node_modules_.

O primeiro _script_, utilizando o parâmetro **-g**, instala duas dependências globais: phantomjs e vows.[PhantomsJS é um headless WebKit][7], feito totalmente em javascript e possui suporte rápido e nativo para vários padrões web como manipulação de DOM, seletores CSS, JSON, Canvas e SVG.

Já o segundo _script_, instala três dependências locais: chai, wd e vows. [Chai][8] é uma biblioteca de assertivas BDD/TDD para NodeJS e navegadores, a qual pode ser &#8216;graciosamente&#8217; utilizada com qualquer framework de teste JS. [WD][9] é um cliente em NodeJS para facilitar o acesso à API do Selenium 2, a qual suporta métodos como: fazer requisições GET e POST, clicar no botão VOLTAR do navegador, fazer refresh no navegador, pegar um printscreen da tela corrente, redimensionar e mover a janela do navegador, submeter formulário, digitar texto, usar cookies, selecionar um elemento DOM, clicar e mover um elemento DOM selecionado, etc.

Após a instalação de todas as dependências necessárias, vamos criar dois arquivos: _**configuracao-webdriver-usando-phantom.js**_ com as informações de configurações do webdriver e _**apenas-um-exemplo.js**_ com os passos-a-passos simulando o comportamento real de um usuário.

**configuracao-webdriver-usando-phantom.js**

<pre class="lang-js">var exports   = module.exports = {},
    webdriver = require('wd'),
    browser   = exports.browser = webdriver.remote({
      hostname: "localhost",
      port: 8910
    });
 
/**
Vows Errored » callback not fired
http://birkett.no/blog/2013/05/01/vows-errored-callback-not-fired/
*/
process.on( 'uncaughtException', function(err) {
  console.error('Caught exception: ' + err.stack );
});
</pre>

**apenas-um-exemplo.js**

<pre class="lang-js">var vows    = require('vows'),
    expect  = require('chai').expect,
    browser = require('./configuracao-webdriver-usando-phantom.js').browser;
 
vows.describe('Apenas um exemplo')
.addBatch({
  'Criando uma nova sessão no WebDriver': {
    topic: function() {
      var callback = this.callback;
      browser.init( {}, function(err, sessionID, capabilities) {
        callback( err );
      });
    },
    'Sessão criada': function() { /**...*/ }
  }
})
.addBatch({
  'Acessando a página de teste do SauceLabs': {
    topic: function() {
      var callback = this.callback;
      browser.get( 'http://saucelabs.com/test/guinea-pig', function(err) {
        callback( err );
      });
    },
    'Página de teste aberta': function() { /**...*/ }
  }
})
.addBatch({
  'Verificando o título da página': {
    topic: function() {
      var callback = this.callback;
      browser.title( function(err, title) {
        callback( err, title );
      });
    },
    "O título da página deve conter 'Sauce Labs'": function(title) {
      expect(title).to.contain('Sauce Labs');
    },
    "O título da página deve conter 'page title'": function(title) {
      expect(title).to.contain('page title');
    },
    "O título da página deve conter 'I am a'": function(title) {
      expect(title).to.contain('I am a');
    }
  }
})
.addBatch({
  'Fechando o navegador': {
    topic: function() {
      var callback = this.callback;
      browser.quit( function(err){
        callback( err );
      });
    },
    'Fim': function() { /**...*/ }
  }
}).export(module);
</pre>

Criado esses dois arquivos, é preciso, em um outro terminal, rodar o PhantomJS em modo WebDriver, digitando o seguinte comando:

<pre class="lanh-ssh">phantomjs --webdriver=localhost:8910 </pre>

Uma vez o PhantomJS rodando em segundo plano, basta rodar o _vows_, o parâmetro **&#8211;spec** serve apenas para ter um diferente tipo de &#8216;reporter&#8217;, segue o comando e uma ilustração do resultado obtido:

<pre class="lang-ssh">vows apenas-um-exemplo.js --spec </pre>

<img class="aligncenter" alt="Resultado obtido" src="https://camo.githubusercontent.com/67da73c5f31ecbfaee938cf04056d96c4f2ada41/687474703a2f2f69313336382e70686f746f6275636b65742e636f6d2f616c62756d732f61673138322f69676f727269626569726f6c696d612f315f626173685f616e645f556d615f696e74726f647563636564696c6174696c64656f5f616f5f53656c656e69756d5f325f616e645f6170656e61732d756d2d6578656d706c6f6a735f6d646173685f696e74726f647563616f2d73656c656e69756d2d74776f2d31335f7a707334333166383131372e706e67" width="897" height="445" />

Esse exemplo contempla de forma bem simples a utilização da API do WebDriver/Selenium 2. Essa abordagem também pode ser feita em [diferentes tipos de navegadores][10]. Como é sempre melhor começarmos aos poucos, aplicando pequenos passos de cada vez, isso ficará para uma próxima discussão. Para quem se interessar, todo código está disponível em um [gist][11]. Muito obrigado.

 [1]: http://www.seleniumhq.org/docs/01_introducing_selenium.jsp "introdução ao selenium no site oficial"
 [2]: http://www.seleniumhq.org/docs/03_webdriver.jsp "introdução ao selenium webdriver no site oficial"
 [3]: http://nodejs.org/download/ "site oficial do NodeJS"
 [4]: http://vowsjs.org/ "site oficial do vows"
 [5]: https://saucelabs.com/test/guinea-pig "página oficial de teste do SauceLabs"
 [6]: http://blog.nodejs.org/2011/03/23/npm-1-0-global-vs-local-installation/ "artigo do blog oficial do NodeJS sobre os tipos de dependências"
 [7]: http://phantomjs.org/ "site oficial do PhantomJS"
 [8]: http://chaijs.com/ "site oficial do Chai"
 [9]: https://github.com/admc/wd "repositorio oficial do WebDriver no github"
 [10]: http://tableless.com.br/introducao-de-como-executar-testes-unitarios-em-diferentes-tipos-de-navegadores "introdução de como executar testes unitários em diferentes tipos de navegadores"
 [11]: https://gist.github.com/igorlima/7826752 "gist introduzindo o Selenium 2"