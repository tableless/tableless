---
title: 'Grunt: você deveria estar usando!'
author: Vagner Santana
type: post
date: 2013-04-14
excerpt: Entenda como automatizar tarefas com GruntJS.
url: /grunt-voce-deveria-estar-usando/
dsq_thread_id: 1209272560
categories:
  - Artigos
  - JavaScript
  - Técnicas e Práticas
  - Tooling
tags:
  - grunt
  - JavaScript
  - tarefas
  - tutorial

---
Todo programador é preguiçoso, e isso é fato, pois sempre estamos procurando ferramentas que automatizem o trabalho para nós. Mas isso necessariamente não é algo ruim, pelo contrário, automatizar tarefas (objetivo do Grunt) implica em ganho de produção e isso é ótimo. O que não podemos deixar acontecer é a não realização de tarefas primordiais para que uma aplicação tenha qualidade.

Minificação e concatenação de arquivos por exemplo são tarefas básicas e você não deve deixar isso de lado, mas fazer isso usando um plugin no editor (que seja o Sublime Text) ou um site, copiar o código minificado, colar em um novo arquivo renomeado com .min no final e por fim salvar, e toda vez que alterar o código ter que repetir essa operação é um saco.

E o deploy ? Se você utiliza FTP sabe o quão lento é fazer upload de arquivos, principalmente se forem muitos, e o pior de tudo, ele abre e fecha uma conexão para cada arquivo, é um sofrimento. E se você esquece de enviar um arquivo que alterou ? Melhor nem pensar&#8230;

## O que é o Grunt?

Foi pensando nessas e várias outras atividades que o Ben Alman, conhecido como <a href="https://twitter.com//cowboy" target="_blank">Cowboy</a> criou essa ferramenta incrível.
  
O Grunt é uma aplicação de linha de comando que tem como objetivo automatizar tarefas, principalmente tarefas em aplicações JavaScript. Essas tarefas são como as descritas acima. E como isso é feito? Escrevendo as tarefas em JavaScript e rodando no Node.JS.

Link oficial: <a href="http://gruntjs.com" target="_blank">http://gruntjs.com</a>

## Ok, quero usar!

Bom, agora que você já entendeu para o que ele serve, vou mostrar como é simples utilizá-lo.
  
Como eu disse, ele roda no Node.JS, então antes de tudo você precisa ter o node e o npm instalados em sua máquina. Se isso estiver ok, você pode continuar.

Se você já instalou o Grunt alguma vez, certifique-se de remove-lo para não ocorrer problemas futuros.

<pre class="lang-bash">sudo npm uninstall -g grunt</pre>

Agora para instalar:

<pre class="lang-shell">sudo npm install -g grunt-cli</pre>

Isso deixará disponível o comando _grunt_ no terminal. Perceba que instalamos o _grunt-cli_ e não o _grunt_ em si, a tarefa do grunt-cli é rodar qualquer versão do grunt, isso permite que você tenha diversas versões do grunt disponíveis em diferentes projetos e você poderá rodar (inclusive simultâneamente) em sua máquina sem ter problemas.

## Mas como ele funciona ?

Para utilizar o Grunt em um projeto, é necessário que exista dois arquivos: o _Gruntfile.js_ e o _package.json_. Eles devem estar na raiz (diretório principal, root) do projeto. Vou falar sobre esses arquivos logo mais.

Se você estiver trabalhando em um projeto que já utiliza o Grunt (isto é, exista os arquivos Gruntfile.js e package.json), para rodar é simples.

<pre class="lang-shell">// Acesse a pasta do projeto
cd project-folder

// Instale as dependências
sudo npm install

// Rode o Grunt
grunt</pre>

Simples não?
  
Mas ok, vamos fazer isso do zero agora.

## Criando um projeto com Grunt

Para iniciar um projeto com o Grunt existem algumas opções: você pode optar pelo _grunt-init_ que gera o scaffolding para alguns modelos de aplicações, como:

  * jquery: cria um projeto para um plugin jQuery
  * commonjs: cria um projeto para um módulo commonjs
  * Gruntfile: cria um arquivo Gruntfile.js básico
  * gruntplugin: cria um plugin grunt
  * node: cria um módulo Node.JS

Você também pode baixar outros templates, além dos oficiais. Para criar um projeto a partir de um dos template como os descritos acima basta usar o comando:

<pre class="lang-shell">grunt-init</pre>

Ou então iniciar o Grunt sem um template, criando os arquivos &#8220;na unha&#8221;.
  
Antes, é nescessário que você saiba para que serve aqueles dois arquivos.

**Gruntfile.js**: Esse é um arquivo JavaScript que são definidas e configuradas as tarefas a serem executadas pelo Grunt.

**package.json**: Esse arquivo é usado pelo npm para armazenar as informações da aplicação, dados como nome, autor, repositório e dependências, e é por isso que o grunt precisa dele, para instalar as dependências e os plugins do grunt que seu projeto irá utilizar. Ao rodar o comando npm install, ele procura as dependências descritas nessa arquivo, e instala na pasta do projeto as mesmas com suas respectivas versões.

Para criar um arquivo _package.json_ você pode utilizar o comando _npm init_.

Exemplo:

<pre class="lang-json">{
	"name": "meu-projeto",
	"version": "0.0.1",
	"description": "Meu íncrivel projeto",
	"homepage": "http://vagnersantana.com/meuprojeto",
	"repository": {
		"type": "git",
		"url": "http://github.com/vagnervjs/meu-projeto"
	},
	"engines": {
		"node": "0.8.x",
		"npm": "1.1.x"
	},
	"devDependencies": {
		"grunt-cli": "0.1.6",
		"grunt": "~0.4.1",
		"grunt-contrib-jshint": "~0.1.1"
	}
}</pre>

Para instalar o Grunt e os plugins dele, você pode usar o comando _npm install &#8211;save-dev_ que além de instalar localmente, adiciona a dependência e sua versão na sessão _devDependences_ do arquivo _package.json_.

O arquivo _Gruntfile.js_ é composto da função principal que engloba tudo, das configurações e tarefas da aplicação, do carregamento de grunt plugins e de tarefas personalizadas.

Exemplo:

<pre class="lang-javascript">module.exports = function(grunt) {
	'use strict';

	// configuração do projeto
	var gruntConfig = {
		pkg: grunt.file.readJSON('package.json'),
		min: {
			dist: {
				src: ['src/assets/js/main.js'],
				dest: 'src/assets/js/all.min.js'
			}
		},
		cssmin: {
			dist: {
				src: ['src/assets/css/main.css'],
				dest: 'src/assets/css/all.min.css'
			}
		},
		jshint: {
			all: ['src/assets/**/*.js']
		}
	};

	grunt.initConfig(gruntConfig);

	// carregando plugins
	grunt.loadNpmTasks('grunt-contrib-jshint');

	// tarefas
	grunt.registerTask('default', ['jshint']);
};</pre>

Bom, pra quem não entendeu direito as linhas acima, eu explico: dentro da função foram declaradas várias tarefas e suas configurações, por exemplo: _min_ é responsável por minificar os arquvios da pasta descrita na propriedade _src_ e enviar para o arquivo de destino em _desc_. Depois de definir as tarefas e configurações em _initConfig()_, é nescessário carregar os plugins grunt de terceitos, caso esteja utilizando algum.

Feito isso, basta registrar as tarefas a serem executadas, usando _registerTask()_.

## Plugins do Grunt

Talvez a melhor parte do Grunt seja essa: os plugins que estão disponíveis.
  
O Grunt vem com algumas tarefas já definidas como _min_ e _concat_, e você as chama definindo suas configurações e adicionando o parâmetro _&#8216;default&#8217;_ em _registerTask()_. Porém, a comunidade já criou e vem criando novas tarefas para o Grunt. Provavelmente tudo o que você precisa já deve existir. Confira essas tarefas em <a href="http://gruntjs.com/plugins" target="_blank">http://gruntjs.com/plugins</a>, lá tem o link para o npm, onde você tem as instruções de como instalar e qual configuração utilizar.

## E o deploy?

É, eu disse lá no início que é possível até fazer deploy com o Grunt, e sim, isso é perfeitamente possível. Agora que você já viu como ele funciona vou falar sobre esse plugin em específico.

Para deploy estou utilizando o _grunt-rsync_. Esse plugin cria uma tarefa de sincronização, tanto local como para um servidor remoto, usando o _rsync_ que já vem presente em sistemas operacionais &#8220;unix like&#8221;. O rsync é excelente pois mantém o diretório remoto sempre em sincronia com o diretório base, e só envia os arquivos que foram alterados, além de não enviar os arquivos um-a-um como faz o FTP. Outro ponto positivo é que ele utiliza SSH, portanto se você tiver uma chave publica adicionada as chaves autorizadas no servidor, você executa o deploy direto do Grunt e sem digitar senha.

Veja a configuração da tarefa:

<pre class="lang-javascript">rsync: {
	dist: {
		src: './src/',
		dest: './dist',
		recursive: true,
		syncDest: true,
		exclude: ['main.*']
	},
	deploy: {
		src: './dist/',
		dest: '/var/www',
		host: 'root@vagnersantana.com',
		recursive: true,
		syncDest: true
	}
}</pre>

Explicando: em dist eu estou fazendo uma sincronização local, preparando a aplicação para deploy, nela eu removo os arquivos que tem nome &#8220;main&#8221; pois estes foram minificados e concatenados em tarefas anteriores. Depois disso, defino a tarefa de deploy, que pega a pasta &#8216;./dist&#8217; que acabou de ser criada ou atualizada, e envio ela para meu servidor. A propriedade &#8220;dest&#8221; agora é é o diretório remoto e a propriedade &#8220;host&#8221; é o usuário e endereço do meu servidor remoto.

## Como rodar?

Mais simples impossível, depois de tudo configurado, você pode executar todas as tarefas descritas no _Gruntfile.js_ com o comando:

<pre class="lang-shell">grunt</pre>

Talvez você precise utilizar _sudo_ caso alguma tarefa necessite de privilégios.

## Grunt Boilerplate

Depois que comecei a utilizar o Grunt, percebi que sempre iria executar tarefas em comum para vários projetos, e isso me fez criar um padrão do Grunt com tudo que preciso em comum, e caso algum projeto necessitar de outras tarefas, é só ir lá e adicionar.
  
Nesse boilerplate defini (por enquanto): min, cssmin e rsync. Não adicionei o JSHint pois utilizo direto no Sublime. Dessa forma com esse boilerplate pronto, para iniciar um projeto eu apenas clono o projeto grunt-boilerplate, mudo o nome da pasta, configuro o package.json, altero os caminhos e nomes de arquivos de acordo com o projeto, e pronto, é lindo =D

Ficou com vontade de utilizar também? É só ir <a title="Github" href="https://github.com/vagnervjs/grunt-boilerplate" target="_blank">neste repositório</a> no github, clonar o projeto e alterar para suas necessidades. Basta ter o grunt-cli e o node instalados para tudo funcionar.

Se quiser realizar um fork, ou reportar um problema fique totalmente à vontade.

## Conclusão

Ferramentas como Grunt, Yeoman, Bower estão ai disponíveis e abertas para todos nós, basta sair da sua zona de conformo, perder o medo de sair do tradicional. Essas ferramentas só existem para melhorar e ajudar nosso trabalho, e se usadas de forma correta, você só irá evoluir, tanto em produção como em profissionalismo. Esperto ter ajudado um pouquinho com o Grunt nesse post. Divirtam-se!

## Referências

  *  <a title="Grunt" href="http://gruntjs.com/getting-started" target="_blank">Grunt &#8211; Getting Started</a>
  *  <a title="Meeting Grunt" href="http://net.tutsplus.com/tutorials/javascript-ajax/meeting-grunt-the-build-tool-for-javascript/" target="_blank">Meet Grunt: The Build Tool for JavaScript</a>
  *  <a title="Introducing Grunt" href="http://weblog.bocoup.com/introducing-grunt/" target="_blank">Bocoup &#8211; Introducing Grunt</a>