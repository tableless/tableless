---
title: 'Harvest: Boilerplate de Gulp para seus projetos'
author: Diego Eis
type: post
date: 2015-10-07
excerpt: Um boilerplate de Gulp com tarefas básicas de build e gerenciamento do projeto.
url: /harvest-boilerplate-de-gulp-para-seus-projetos/
categories:
  - Código
  - Técnicas e Práticas
  - Tooling
tags:
  - grunt
  - gulp
  - js
  - task runner

---
Não importa qual o Task Runner você usa. Muitos gostam de Grunt, outros de Gulp, outros usam Rake e todos tem o seu encanto e seus truques. Já usei muito Grunt, mas ultimamente tenho experimentado o Gulp. Cara&#8230; como é rápido. Por isso, tive a grande ideia de criar um boilerplate para os meus projetos, onde eu consigo rapidamente concatenar os assets, otimizar imagens, criar source maps dos arquivos SASS, subir um servidor e várias outras coisas.

Mas antes de iniciar a criação desse boilerplate, obviamente, procurei se alguém não já teve essa ideia e feito esse trabalho para mim. Foi aí que eu achei o [Harvest][1].

O Harvest é um boilerplate Gulp que te ajuda a fazer uma série tarefas rotineiras como:

  * Levantar um servidor na porta 3000
  * Live Reload usando o BrowserSync
  * Build do projeto
  * Conversão do SCSS com Source Maps
  * Concatenação e minificação do CSS e JS
  * Compressão e Otimização de imagem

A instalação é fácil:

  * Faça o download ou o clone do projeto
  * Rode `npm install` para instalar as dependencias.
  * Rode `gulp` para iniciar o servidor, o live reload e o watch dos assets.
  * Abra o browser em http://localhost:8080 para ver seu servidor local e o live reload do projeto
  * Rode `gulp deploy` para fazer o build seu projeto

Alguns dos módulos usados para fazer esse boilerplate são:

  * <a href="https://www.npmjs.com/package/gulp-autoprefixer" target="_blank">Gulp Auto Prefixer</a> insere os prefixos dos browsers no seu CSS automaticamente
  * <a href="https://www.npmjs.com/package/gulp-concat" target="_blank">Gulp Concat</a> Concatena o JS e o CSS em um arquivo.
  * <a href="https://www.npmjs.com/package/gulp-connect" target="_blank">Gulp Connect</a> Cria um servidor local para o desenvolvimento faz o reload quando você muda e salva um arquivo. 
  * <a href="https://www.npmjs.com/package/gulp-imagemin" target="_blank">Gulp ImageMin</a> Minifica as imagens.
  * <a href="https://www.npmjs.com/package/gulp-sass" target="_blank">Gulp SASS</a> Biblioteca do SASS sem a dependência do Ruby.
  * <a href="https://www.npmjs.com/package/gulp-sourcemaps" target="_blank">Gulp SourceMaps</a> Adiciona os arquivos de source maps para facilitar o debug do SASS
  * <a href="https://www.npmjs.com/package/gulp-uglify" target="_blank">Gulp Uglify</a> Uglify de JS.
  * <a href="https://www.npmjs.com/package/gulp-shell" target="_blank">Gulp Shell</a> Ajuda na criação e limpeza de diretório de build
  * <a href="https://www.npmjs.com/package/gulp-sequence" target="_blank">Gulp Sequence</a> Organiza e roda as tarefas de build em uma sequência definida. 
  * <a href="https://www.npmjs.com/package/browser-sync" target="_blank">BrowserSync</a> Sincroniza vários browsers e executa o live reload da página.
  * <a href="https://www.npmjs.com/package/gulp-minify-css" target="_blank">Gulp Minify CSS</a> Minifica o CSS.

A [documentação][2] ainda está sendo escrita, mas acho que você vai conseguir se virar bem.

 [1]: http://www.ryanbensonmedia.com/harvest
 [2]: http://www.ryanbensonmedia.com/harvest/documentation