---
title: Introdução ao webpack
author: Leo Cavalcante
type: post
date: 2015-02-23
excerpt: 'Conheça o webpack: um bundler que permite dividir seu código em múltiplos módulos para serem lidos sob demanda.'
url: /introducao-ao-webpack/
categories:
  - JavaScript
  - ReactJS
  - Técnicas e Práticas
tags:
  - jsx
  - react
  - webpack

---
## O que é? (Onde vivem? O que comem?)

webpack (com &#8220;w&#8221; minúsculo, respeitando a grafia do site oficial) é um empacotador de código para projetos web, como o [browserify][1]. O que ele se propõe a fazer de diferente é focar em módulos da sua aplicação. Nem sempre ter todo e qualquer JavaScript/CSS do seu projeto num único arquivo é bom, por isso o webpack tem a ideia de [code splitting][2], onde você modulariza partes reaproveitáveis do seu projeto, facilitando o desenvolvimento independente, por exemplo, ter uma equipe trabalhando em um módulo X e outra num módulo Y, mas ambos de um mesmo projeto.

Não é sempre que a gente faz um projeto tão grande assim, a ponto de precisar separar equipes em diferentes módulos, mas o webpack também pode ser ideal para pequenos projetos. 

## Instalando.

É bem simples. Você tem o webpack como pacote do [NodeJS][3]. Se você não sabe o que é NodeJS, [pare agora e leia esse artigo][4]. Sugiro dar uma pesquisada sobre [NPM][5] antes. Se você entendeu tudo até aqui, pode escolher entre tê-lo globalmente ou somente num projeto:

<pre class="lang-bash">&gt; npm install&lt;/span> webpack -g
&gt; npm install webpack --<span class="hljs-built_in">save</span>-<span class="hljs-built_in">dev</span>
</pre>

## Usando {#usando}

É bem simples, também. O comando espera dois argumentos, um arquivo de entrada e um arquivo de saída que se não existir vai ser criado e se já existir será substituído.

<pre class="lang-bash">$ webpack <span class="hljs-tag">&lt;<span class="hljs-title">entry</span>&gt;</span> <span class="hljs-tag">&lt;<span class="hljs-title">output</span>&gt;</span></pre>

Você pode definir um arquivo de configuração pro comando com a opção `--config example.config.js` se nada for passado o webpack vai procurar um arquivo chamado `webpack.config.js` onde ele está sendo executado (normalmente raiz do projeto) se não achar, vai usar as configurações padrão, o famoso default.

## Loaders e preloaders {#loaders-e-preloaders}

O webpack pode executar transformações nos arquivos durante o processo de empacotamento, essas transformações são, por exemplo, nossos famosos pré-processadores, React (JSX), Coffee, 6to5, SweetJS, TypeScript&#8230; a lista de _loaders_ já prontos é muito boa e claro, você pode construir os seus se sentir falta de algum. Também tem Less, Sass, Stylus, Jade, Ejs, Mustache, Handlebars, Markdown&#8230; não é só pra JavaScript. Em adição aos _loaders_, você pode ter plugins, que executam processos mais complexos que as transformações, por exemplo, **UglifyJsPlugin!** Yay!

## Bora ver na prática {#bora-ver-na-pr-tica}

Vamos criar um módulo super útil que nunca vi por aí que serve pra deixar as letras de um texto em caixa alta.

<pre class="lang-javascript">// upper.js
module.exports = function(str) {
	return str.toUpperCase();
};
</pre>

Agora a gente chama esse modulo no nosso arquivo de entrada, que não é necessariamente o principal, por isso a gente não vai chamar de _main.js_ ou _app.js._

<pre class="lang-javascript">// entry.js
var upper = require('./upper.js');
console.log(upper('test'));
</pre>

Sim! Como puderam perceber, podemos usar o padrão CommonJS pra criar nossos módulos, que é o mesmo padrão usado pelo NodeJS, então a gente pode usar alguns pacotes do NPM também, mesmo num build com target pro browser (módulo focado para o navegador). Vamos ver o que vai dar isso até agora.

<pre class="lang-bash">&gt; webpack entry.js bundle.js</pre>

O comando gera um _report_ simples no console mesmo, aqui ficou:

<pre class="lang-bash">Hash: 0b87391ad5027f171afe
Version: webpack 1.5.3
Time: 310ms
Asset Size Chunks Chunk Names
bundle.js 1706 0 [emitted] main
[0] ./entry.js 63 {0} [built]
[1] ./upper.js 67 {0} [built]
</pre>

Se você estiver acompanhando na prática, pode abrir o _bundle.js_ (se já não fez isso seguindo o instinto curioso de qualquer dev) e ver como fica o _build_. Você vai notar que o **webpack** tem um _boilerplate_ até considerável, mas é útil, ele tem um sistema de cache que performa os _builds_, ele vai saber qual módulo mudou de verdade ao invés de pegar tudo e _buildar_ tudo de novo.

<pre class="lang-bash">&gt; node bundle.js
TEST
</pre>

## React tá na moda, vamos usar. {#react-t-na-moda-vamos-usar-}

Vamos usar um arquivo de configuração pra vincular os arquivos _.jsx_ ao Loader certo, o webpack usa RegExp pra testar sobre o nome dos arquivos e vincular a um _loader_ e o arquivo de configuração é um módulo CommonJS. Já que estamos usando um arquivo para a configuração, vamos por nele qual é nosso _entry_ e qual é nosso _output_. Mas antes, como usaremos módulos do NPM, vamos inicia-lo em nosso projeto e ter um arquivo declarando essas dependências, o _packages.json_.

<pre class="lang-bash">&gt; npm init
&gt; npm install react --save
&gt; npm install jsx-loader --save-dev
</pre>

Nosso arquivo de configuração vai ficar assim:

<pre>// webpack.config.js
module.exports = {
	entry: "./entry.jsx",
	output: {
		filename: "bundle.js"
	},
	module: {
		loaders: [
			{test: /\.jsx/, loader: 'jsx-loader'}
		]
	}
};
</pre>

Agora é só rodar o webpack, sem passar nada, ele já vai ler nas configurações.

<pre>&gt; webpack</pre>

Tá lá! Você tem um _bundle_ com React pronto pra web.

## Concluindo {#concluindo}

Essa foi só uma introdução e vale ressaltar que o webpack não é uma alternativa aos _tasks managers_ como Gulp e Grunt (caso alguém tenha entendido isso), mas só com o webpack você tem um _watcher_ pro _build_ acontecer logo que ele detecta uma alteração em um arquivo e o plugin do UglifyJS pra _minificar_ seu _build_.

Isso aí, se ficou alguma dúvida, só chamar 😉

 [1]: http://browserify.org/
 [2]: http://webpack.github.io/docs/code-splitting.html
 [3]: http://nodejs.org/
 [4]: http://tableless.com.br/o-que-nodejs-primeiros-passos-com-node-js/
 [5]: https://www.npmjs.com/