---
title: História de usuário e teste de aceitação em JavaScript
author: Igor Ribeiro Lima
type: post
date: 2014-01-22
excerpt: 'História de usuário é uma descrição resumida de alguma funcionalidade do sistema sob o ponto de vista do usuário. '
url: /historia-de-usuario-e-teste-de-aceitacao-em-javascript/
dsq_thread_id: 2104572243
categories:
  - JavaScript
tags:
  - CucumbeJS
  - história de usuário
  - JavaScript
  - NodeJS
  - PhantomJS
  - Selenium 2
  - teste de aceitação
  - webdriver

---
Cada história deve ter valor de negócio na visão do cliente e é uma pequena parte da funcionalidade, não necessariamente uma especificação completa, o que minimiza a necessidade de uma extensa documentação.

A história de usuário é escrita pelo próprio cliente e, também, serve para conduzir a criação de teste de aceitação, o qual tem o propósito de avaliar a qualidade externa do produto e, na medida do possível, a qualidade de uso e experiência do usuário. A automatização dos testes de aceitação é criada para certificar de que a história foi implementada corretamente.

Nesse exemplo é preciso a instalação do NodeJS e do Node Package Manager (NPM), que podem ser baixados no [site oficial][1]. O NPM é necessário para instalar o [CucumberJS][2], o [PhantomJS][3] e o [WD][4], digitando o seguinte _script_ no terminal:

<pre class="lang-ssh">npm install -g cucumber phantomjs</pre>

<pre class="lang-ssh">npm install wd</pre>

O NodeJS possui dois tipos de dependências: global e local. Quando é global, a dependência passa ser executável, tornando possível a utilização da dependência através da linha de comando. Já as dependências locais são instaladas no diretório corrente, dentro de um diretório chamado _node_modules_.

O primeiro _script_, que utiliza o parâmetro **-g**, instala o [CucumberJS][2] e o [PhantomJS][3] como dependências globais. O CucumberJS é uma implementação JavaScript para interpretar uma linguagem chamada [Gherkin][5], a qual permite escrever funcionalidades e especificações em texto simples. Já o PhantomJS é um WebKit headless totalmente em JavaScript e possui suporte rápido e nativo para vários padrões web como manipulação de DOM, seletores CSS, JSON, Canvas e SVG.

O segundo _script_ instala o [WD][4] como dependência local, um cliente NodeJS para facilitar o acesso à API do [Selenium 2][6], o qual suporta [métodos][7] como: fazer requisições GET e POST, clicar no botão VOLTAR do navegador, redimensionar e mover a janela do navegador, submeter formulário, digitar texto, selecionar um elemento DOM, clicar e mover um elemento DOM selecionado, etc.

Após a instalação das dependências, vamos criar o arquivo [**apenas-um-exemplo.feature**][8] com a especificação da história de usuário e o teste de aceitação. Algo bem simples. Suficiente para exemplificar a implementação desse tipo de teste utilizando JavaScript.

**apenas-um-exemplo.feature**

<pre class="lang-js">Feature: Apenas Um Exemplo
  Como um usuario do CucumberJS
  Eu quero acessar um formulario de teste
  Para que eu possa submeter novas informacoes

  Scenario: Submetendo um formulario de teste
    Given o navegador aberto
      And acessar o formulario de teste
      And certificar que o titulo da pagina contem "Sauce Labs"
      And certificar que o titulo da pagina contem "page title"
      And certificar que o titulo da pagina contem "I am a"
    When clicar no botao de submeter formulario
    Then a url do navegador DEVE conter "guinea-pig"
    And o navegador pode ser fechado</pre>

Ao criar o arquivo de especificação, vamos criar mais dois arquivos: [**configuracao-webdriver-usando-phantom.js**][9] com as configurações do WebDriver e o arquivo [**step-definitions.js**][10] com as definições de cada passo do teste de aceitação. Em seguida, é preciso, em um outro terminal, rodar o PhantomJS em modo WebDriver, digitando o seguinte comando:

<pre class="lang-ssh">phantomjs --webdriver=localhost:8910</pre>

Com o PhantomJS rodando em segundo plano, basta rodar o CucumberJS passando como argumento o arquivo com a história de usuário e o teste de aceitação. O parâmetro **&#8211;require** serve para especificar o arquivo com as definições de cada passo do teste de aceitação. E o parâmetro **&#8211;format** é para alterar a formatação do resultado dos testes. Abaixo, o _script_ e uma ilustração do resultado obtido:

<pre class="lang-ssh">cucumber.js apenas-um-exemplo.feature --require step-definitions.js --format pretty</pre>

<img alt="Ilustração do resultado de exemplo de como escrever história de usuário e teste de aceitação com JavaScript" src="http://i1368.photobucket.com/albums/ag182/igorribeirolima/resultado-obtido_zps867ddb6d.png" width="1020" height="468" />

Esse exemplo contempla de forma bem simples a implementação de teste de aceitação utilizando JavaScript. Essa abordagem também pode utilizar [diferentes tipos de navegadores][11], mas isso ficará para uma próxima discussão. Para quem tiver interesse, todo código está disponível em um [gist][12].

 [1]: http://nodejs.org/download/
 [2]: https://github.com/cucumber/cucumber-js
 [3]: http://phantomjs.org/
 [4]: https://github.com/admc/wd
 [5]: https://github.com/cucumber/gherkin
 [6]: http://tableless.com.br/introducao-ao-selenium-2/
 [7]: https://github.com/admc/wd/blob/master/doc/api.md
 [8]: https://gist.github.com/igorlima/8024944#file-apenas-um-exemplo-feature
 [9]: https://gist.github.com/igorlima/8024944#file-configuracao-webdriver-usando-phantom-js
 [10]: https://gist.github.com/igorlima/8024944#file-step-definitions-js
 [11]: http://tableless.com.br/introducao-de-como-executar-testes-unitarios-em-diferentes-tipos-de-navegadores/
 [12]: https://gist.github.com/igorlima/8024944 "Gist - Exemplo de como escrever história de usuário e teste de aceitação com JavaScript"