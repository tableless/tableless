---
title: Visualizando páginas responsivas em diversos navegadores
author: Igor Ribeiro Lima
type: post
date: 2014-04-25
excerpt: Teste como sua página se comporta em diversos dispositivos e navegadores.
url: /visualizando-pagina-responsiva-em-diversos-navegadores/
dsq_thread_id: 2634576908
categories:
  - Responsive Web Design (RWD)
  - Tecnologia e Tendências
tags:
  - BrowserStack
  - JavaScript
  - NodeJS
  - página responsiva
  - responsive design
  - SauceLabs
  - Selenium 2

---
Nesse artigo vou mostrar rapidamente como tirar um Print Screen da página inicial de seu site utilizando diversos dispositivos. Algo que pode facilitar e muito a vida caso esteja desenvolvendo uma página responsiva.

Nesse exemplo vamos utilizar o <a href="http://nodejs.org/" rel="noreferrer">NodeJS</a> e o <a href="http://tableless.com.br/introducao-ao-selenium-2/" rel="noreferrer">Selenium 2</a>. As outras dependências necessárias estão especificadas no arquivo <a href="http://docs.nodejitsu.com/articles/getting-started/npm/what-is-the-file-package-json" rel="noreferrer">package.json</a>. Arquivo que é usado para fornecer ao gerenciador de pacotes NPM, informações de como lidar com as dependências do projeto, a descrição do projeto, a licença utilizada, <a href="http://package.json.nodejitsu.com/" rel="noreferrer">dentre outras</a>.

Para facilitar nossa vida, utilizaremos um serviço de Cloud do <a href="https://saucelabs.com/" rel="noreferrer">SauceLabs</a>. Esse serviço permite utilizar diversos tipos de navegadores. Logo, logo estarei escrevendo outros artigos, mostrando outros tipos de serviços parecidos, como por exemplo o <a href="http://www.browserstack.com/" rel="noreferrer">BrowserStack</a>. Todos esses serviços de Cloud fornecem uma **chave de acesso**. Para criar uma conta, basta acessar a <a href="https://saucelabs.com/signup" rel="noreferrer">página de cadastro</a> e preencher o formulário. Posso te assegurar que o cadastro é simples e rápido.

Tendo a chave de acesso em mãos, vamos executar <a href="https://gist.github.com/igorlima/9875745" rel="noreferrer">o seguinte script</a>. Magicamente teremos um printscreen da página inicial do site do Tableless:

<pre class="lang-ssh">git clone https://gist.github.com/9875745.git visualizao-pagina-web
npm install
node script.js -u $SAUCE_USERNAME -k $SAUCE_ACCESS_KEY --url 'http://tableless.com.br/' --screenshot 'printscreen-da-pagina-do-tableless.png'</pre>

Esse script utiliza como padrão a última versão do navegador Chrome. Para utilizar outros navegadores, especificaremos via parâmetros direto no Terminal. Os detalhes de cada parâmetro são obtidos utilizando _&#8211;help_. Existe uma lista com centenas de navegadores e dispositivos, os quais podem ser vistos no seguinte <a href="https://saucelabs.com/platforms" rel="noreferrer">link</a>. Segue abaixo dois exemplos de como visualizar o site do Tableless em um tablet com Android e em um iPhone:

<pre class="lang-ssh">node script.js -u $SAUCE_USERNAME -k $SAUCE_ACCESS_KEY --url 'http://tableless.com.br/' --screenshot 'printscreen-tableless-android.png' -b 'android' -p 'Linux' -v '4.0' --deviceType tablet --deviceOrientation landscape
node script.js -u $SAUCE_USERNAME -k $SAUCE_ACCESS_KEY --url 'http://tableless.com.br/' --screenshot 'printscreen-tableless-iphone.png' -b 'iphone' -p 'OS X 10.9' -v '7.0'</pre>

O resultado é ilustrado na imagem abaixo.

<img class="alignnone" alt="PrintScreen da página do Tableless em diversos dispositivos" src="https://camo.githubusercontent.com/0ba7d9a87cde934188995961c780401e73d19350/68747470733a2f2f63616d6f2e67697468756275736572636f6e74656e742e636f6d2f323936383265353030646663643562303032656230653766383832666332346231636266653261622f3638373437343730336132663266363933313333333633383265373036383666373436663632373536333662363537343265363336663664326636313663363237353664373332663631363733313338333232663639363736663732373236393632363536393732366636633639366436313266373436313632366336353663363537333733326436313732373436393633366336353264363936643631363736353566376137303733333933313335333536333634333636313265366137303637" width="836" height="695" />

Caso se interessem e queiram modificar o script utilizado acima, fiquem a vontade. Para um melhor entendimento do script, deem uma lida nos seguintes artigos: **(i)** <a href="http://tableless.com.br/introducao-de-como-executar-testes-unitarios-em-diferentes-tipos-de-navegadores/" rel="noreferrer">Introdução de como executar testes unitários em diferentes tipos de navegadores</a> e **(ii)** <a href="http://tableless.com.br/javascript-de-forma-assincrona-e-legivel/" rel="noreferrer">JavaScript de forma assíncrona e legível</a>. Espero que tenham gostado. Até a próxima.