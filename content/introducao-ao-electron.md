---
title: Introdução ao Electron
author: Henrique Sosa
type: post
date: 2015-11-09
excerpt: Desenvolvedor web também pode construir aplicações desktop. Com o Electron, você usa HTML, CSS e JavaScript.
url: /introducao-ao-electron/
categories:
  - Código
  - JavaScript
  - Técnicas e Práticas
tags:
  - app
  - atom shell
  - CSS
  - electron
  - github
  - gulp
  - html
  - JavaScript
  - NodeJS
  - slack
  - visual studio code

---
## O que é o Electron

O Electron foi desenvolvido para permitir que o desenvolvimento de aplicações _desktop_ usando JavaScript, HTML e CSS fosse muito mais fácil. Criado pela equipe do <a href="https://github.com/" target="_blank">Github</a>, ficou conhecido no começo como Atom Shell. O Electron foi criado usando tecnologias como o <a href="https://nodejs.org" target="_blank">Node.js</a> e o Chromium, e atualmente roda em ambiente de produção de vários projetos, como o próprio <a href="https://code.visualstudio.com/" target="_blank">Atom editor</a> e outros, como o <a href="https://slack.com/" target="_blank">Slack</a> e o <a href="https://code.visualstudio.com/" target="_blank">Visual Studio Code</a>. Ele é um _framework_ bem simples de trabalhar e de rápida configuração, para construção de pequenas e grandes aplicações _desktop_.

Para todos que queiram se aventurar mais, ou já conhecem o Electron, a documentação completa é traduzida para vários idiomas, inclusive o português. Para acessá-la é só <a href="https://github.com/atom/electron/tree/master/docs-translations/pt-BR" target="_blank">clicar aqui</a>.

## Mãos à obra

Nesta Introdução iremos abordar os primeiros passos para começar a trabalhar com o Electron e desenvolver aplicações _desktop_.

Além do <a href="https://nodejs.org" target="_blank">Node.js</a> presente em sua máquina, é necessário que você também instale globalmente o pacote `electron-prebuilt`. Para isto, basta digitar o seguinte comando:

<pre class="language-bash">npm install -g electron-prebuilt</pre>

### Entendendo a estrutura

A estrutura básica de arquivos que usaremos aqui é a seguinte:

<pre class="language-text">electron-app/
├── app 
    ├── assets
        └── css
            └── main.css
    ├── main.js
    ├── index.html
    └── package.json
├── Gulpfile.js
└── package.json
</pre>

Vamos falar um pouco de cada arquivo e pasta inseridos no exemplo acima:

#### app

É  a pasta onde todos os arquivos referentes à aplicação são inseridos.

#### main.js

É o arquivo de inicialização da aplicação. Nele vão as configurações do tipo: tamanho da tela, posicionamento, manipular eventos do sistema, etc&#8230;

#### index.html

É a pagina HTML que será nossa _view_ inicial para essa introdução.

#### app/package.json

O arquivo `package.json` que vai dentro da pasta _app_ é o arquivo que leva todos as dependências que sua aplicação precisará para rodar. Sendo assim, qualquer pacote _npm_ a ser usado diretamente por sua aplicação deverá ser instalado nesse _package_.

#### Gulpfile.js

Optei usar <a href="http://gulpjs.com/" target="_blank">Gulp</a> por escolha própria mesmo, mas fiquem livres para escolher seu _&#8220;task runner&#8221;_ favorito.

#### package.json

O `package.json` que fica na raiz do seu projeto é responsável pelas configurações, dependências para seu ambiente de desenvolvimento. Tudo que for incluso neste arquivo não estará presente na _build_ de produção da sua _app_.

### Declarando as dependências

Após criar a estrutura de pastas que foi citada no tópico anterior. Iremos atribuir os mesmos valores para os atributos de ambos `package.json` presentes no projeto. Levando em consideração que `"your-app"` será o nome da sua aplicação.

<pre class="language-json">{
  "name"    : "olamundo",
  "version" : "0.1.0",
  "main"    : "main.js"
}
</pre>

**Nota**: Caso o campo main não tenha sido preenchido, o Electron automaticamente procurará pelo arquivo `index.js`. É importante que preencha este campo com o arquivo que usará na inicialização da aplicação.

Após feito isso, instale as dependências que utilizaremos nesta introdução, no arquivo `package.json` que se encontra diretamente na raiz do seu projeto.

<pre class=" language-bash">npm install --save-dev electron-prebuilt fs-jetpack asar rcedit Q
</pre>

### Criando seu arquivo de inicialização

Depois de configurar as pastas e instalar as dependências da nossa aplicação, vamos abrir o nosso arquivo `main.js` . Nele vamos incluir todo o código de configuração:

<pre class="language-javascript">var app = require('app');
var BrowserWindow = require('browser-window');

require('crash-reporter').start();

var mainWindow = null;

app.on('window-all-closed', function() {
  
  if (process.platform != 'darwin') {
    app.quit();
  }

});

app.on('ready', function() {
  
  mainWindow = new BrowserWindow({width: 800, height: 600});
  
  mainWindow.loadUrl('file://' + __dirname + '/index.html');
  
  mainWindow.openDevTools();
  
  mainWindow.on('closed', function() {
    
    mainWindow = null;
  });
}); 
</pre>

**Nota**: a Função _mainWindow.openDevTools_ é chamada apenas para iniciar o _Inspetor de Elementos_ junto com a aplicação. Caso não precisem, fiquem à vontade para removê-la do seu projeto.

### Primeira _view_

Finalmente a parte mais fácil. Note que em nosso arquivo `main.js` existe a seguinte função:

<pre class="language-javascript">mainWindow.loadUrl('file://' + __dirname + '/index.html'); 
</pre>

Ela será responsável por carregar o arquivo `index.html`. No exemplo a seguir, criei um exemplo bem simples de um arquivo HTML. Esta página que foi criada, tem os mesmos aspectos de uma janela aberta de um navegador. Ou seja, podemos carregar todos os arquivos CSS e JavaScript que utilizaremos normalmente. Veja:

<div class="highlight">
  <pre class="language-html">&lt;!DOCTYPE html&gt;
&lt;html&gt;
  &lt;head&gt;
      &lt;meta charset="utf-8" /&gt;
      &lt;title&gt;Olá Mundo&lt;/title&gt;
      &lt;link href="assets/css/main.css" rel="stylesheet" type="text/css" /&gt;
    &lt;/head&gt;
    &lt;body&gt;
      &lt;h1&gt;Olá Mundo&lt;/h1&gt;
      
      &lt;p&gt;Bem vindos à nossa introdução ao Electron&lt;/p&gt;
    &lt;/body&gt;
&lt;/html&gt;
</pre>
  
  <h2 id="run-your-app">
    Rodando sua aplicação
  </h2>
  
  <h3>
    electron-prebuilt
  </h3>
  
  <p>
    Se você instalou o <code>electron-prebuilt</code> global, Acesse a pasta <strong>app</strong> e rode o seguinte comando:
  </p>
  
  <pre class="language-bash">electron app</pre>
  
  <p>
    Caso tenha instalado apenas localmente, então, na pasta <strong>app</strong> de seu projeto, digite o seguinte comando:
  </p>
  
  <pre class="language-bash">"../node_modules/.bin/electron" "./app"</pre>
  
  <h3>
    Automatizando
  </h3>
  
  <p>
    Como citei anteriormente, usaremos o <em>Gulp</em> para automatizar o <em>run</em> da nossa aplicação, facilitando assim a criação de testes e o próprio desenvolvimento da aplicação. Para isso, deixaremos nosso <code>Gulpfile.js</code> da seguinte maneira:
  </p>
  
  <pre class="language-javascript">var gulp = require('gulp'),
  childProcess = require('child_process'),
  electron = require('electron-prebuilt');
  
gulp.task('run', function () {
  childProcess.spawn(electron, ['./app'], { stdio: 'inherit' });
});
</pre>
  
  <p>
    Feito isso basta rodar o seguinte comando em seu terminal:
  </p>
  
  <pre class="language-bash">gulp run</pre>
  
  <h2>
    Criando uma distribuição
  </h2>
  
  <p>
    Depois de terminado todo o processo de desenvolvimento, você pode criar uma distribuição do seu <em>app</em> seguindo as instruções do <a href="http://electron.atom.io/docs/v0.33.0/tutorial/application-distribution" target="_blank">Application Distribution guide</a>.
  </p>
  
  <p>
    Pronto! Você está pronto(a) para desenvolver aplicações Desktop com o Electron.
  </p>
  
  <p>
    E caso queiram, o projeto está disponível no <a href="https://github.com/henriquesosa/electron-intro" target="_blank">Github</a>.
  </p>
</div>