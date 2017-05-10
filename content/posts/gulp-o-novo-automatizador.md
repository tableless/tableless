---
title: 'Gulp: O novo automatizador'
author: Guilherme Kalani
type: post
date: 2014-01-20
excerpt: Automatize suas tarefas repetitivas de forma simples e rápida.
url: /gulp-o-novo-automatizador/
dsq_thread_id: 2130313189
categories:
  - JavaScript
tags:
  - gulp
  - JavaScript
  - plugin

---
Se você não esteve morando em baixo de uma rocha pelos últimos meses, provavelmente conhece o automatizador de tarefas [Grunt][1], que já dominava a área há algum tempo. Mas agora, chegou um novo automatizador chamado [Gulp][2] que promete realizar suas tarefas de forma mais rápida e simples do que seu concorrente.

Caso você não saiba, automatizadores de tarefa são ferramentas que ajudam programadores <del>preguiçosos</del> a realizarem tarefas repetitivas mas essenciais para o desenvolvimento como: concatenação de arquivos, minificação, testes e muitas outras coisas necessárias para a criação de um código rápido e eficiente.

### Por que Gulp?

Se você já utiliza o Grunt em seus projetos, deve estar se perguntando por que mudar de automatizador. A resposta é simples: O Gulp é muito mais rápido que o Grunt, já que faz uso das streams do nodejs para escrever arquivos diretamente para o disco, dispensando intermediários. Sem falar na simplicidade do Gulpfile(equivalente ao Gruntfile), que utiliza uma sintaxe de código semelhante ao código comum do nodejs.

Espero que até o final do texto você fique impressionado com a simplicidade do Gulp, e pense duas vezes antes de escolher o automatizador de tarefas para o seu próximo projeto.

### Instalação

Lembrando que o Gulp roda no [nodejs][3] então é preciso que você o tenha instalado no seu computador, caso esteja tudo ok, basta rodar o comando abaixo na sua linha de comando para instalar o CLI:

<pre class="lang-javascript">npm install -g gulp
</pre>

Caso você esteja em um sistema baseado em Unix, talvez seja preciso rodar \`sudo\` antes do comando acima. Agora você vai poder rodar o Gulp na sua linha de comando. Para ver a versão instalada, execute:

<pre class="lang-javascript">gulp -v
</pre>

Se o comando acima retornar a versão do Gulp instalada, a instalação foi um sucesso.

### Iniciando com o Gulp

Agora vamos ao que interessa, a automatização! O Gulp faz uso do Gulpfile para configuração das tarefas que ele vai rodar, que é o único arquivo necessário.

Para nossos testes, criei uma estrutura desta forma:

<pre class="lang-html">|projeto/
|--dist/
|--src/
|----source.js
|--Gulpfile.js
</pre>

Vou rodar três testes diferentes: Concatenação, minificação e teste de código com o jshint. O Gulp faz uso de [plugins][4] para facilitar a criação de tarefas, então vou instalar alguns para nós rodarmos nossos testes.

<pre class="lang-javascript">npm install gulp gulp-jshint gulp-uglify gulp-concat gulp-rename --save-dev
</pre>

Note que eu instalei o próprio Gulp DE NOVO e alguns plugins. Isto é porque o Gulp instalado anteriormente foi o CLI, responsável por rodar o comando \`gulp\` na linha de comando e o instalado desta vez é o local que é usado para rodar os testes no projeto. Agora podemos criar nosso Gulpfile:

<pre class="lang-javascript">// Aqui nós carregamos o gulp e os plugins através da função `require` do nodejs
var gulp = require('gulp');
var jshint = require('gulp-jshint');
var uglify = require('gulp-uglify');
var concat = require('gulp-concat');
var rename = require('gulp-rename');

// Definimos o diretorio dos arquivos para evitar repetição futuramente
var files = "./src/*.js";

//Aqui criamos uma nova tarefa através do ´gulp.task´ e damos a ela o nome 'lint'
gulp.task('lint', function() {

// Aqui carregamos os arquivos que a gente quer rodar as tarefas com o `gulp.src`
// E logo depois usamos o `pipe` para rodar a tarefa `jshint`
gulp.src(files)
.pipe(jshint())
.pipe(jshint.reporter('default'));
});

//Criamos outra tarefa com o nome 'dist'
gulp.task('dist', function() {

// Carregamos os arquivos novamente
// E rodamos uma tarefa para concatenação
// Renomeamos o arquivo que sera minificado e logo depois o minificamos com o `uglify`
// E pra terminar usamos o `gulp.dest` para colocar os arquivos concatenados e minificados na pasta build/
gulp.src(files)
.pipe(concat('./dist'))
.pipe(rename('dist.min.js'))
.pipe(uglify())
.pipe(gulp.dest('./dist'));
});

//Criamos uma tarefa 'default' que vai rodar quando rodamos `gulp` no projeto
gulp.task('default', function() {

// Usamos o `gulp.run` para rodar as tarefas
// E usamos o `gulp.watch` para o Gulp esperar mudanças nos arquivos para rodar novamente
gulp.run('lint', 'dist');
gulp.watch(files, function(evt) {
gulp.run('lint', 'dist');
});
});
</pre>

O código acima está muito bem comentado e dispensa mais explicações. Caso você tenha usado o Grunt anteriormente, percebeu como a criação de tarefas com o Gulpfile é muito mais simples. Para rodar as tarefas, rode o comando:

<pre class="lang-javascript">gulp
</pre>

Perceba que ele executa a rotina de tarefas que você definiu e fica esperando mudanças no seu código para rodar novamente(lembra do watch?), mas se você quiser rodar apenas um tarefa específica, basta adicionar o nome da tarefa após o comando:

<pre class="lang-javascript">gulp lint
</pre>

No exemplo acima rodamos o teste de código usando o nome da task que definimos anteriormente.

### Conclusão

Enfim, neste texto vimos como usar o Gulp para automatizar as tarefas do seu próximo projeto de forma simples e eficiente. O Gulp é um projeto novo e que ainda deve amadurecer muito nas próximas semanas. Caso você queira contribuir de alguma maneira, acesse o projeto no [github][5] e veja como ajudar.

 [1]: http://tableless.com.br/grunt-voce-deveria-estar-usando/
 [2]: http://gulpjs.com
 [3]: http://nodejs.org/
 [4]: http://gratimax.github.io/search-gulp-plugins/
 [5]: https://github.com/gulpjs/gulp