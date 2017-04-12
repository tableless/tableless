---
title: ES2015 – Babel 6 com Browserify e Babelify
author: Renato Augusto Gama dos Santos
type: post
date: 2015-11-23
excerpt: O Babel 6 trouxe muitas mudanças na maneira que convertemos arquivos ES2015 para ES5.
url: /es2015-babel-6-com-browserify-e-babelify/
categories:
  - JavaScript
tags:
  - babel
  - babelify
  - browserify
  - es2015
  - grunt
  - JavaScript
  - tutorial

---
Vivemos um momento de transição no mundo Javascript com a aprovação do ES2015 ou ES6, porém, este novo padrão ainda não é suportado totalmente por todos os navegadores, para administrar este problema foi criado o Babel, um compiler Javascript, que além de suas muitas funções, nesta versão 6, pode transformar ES2015 em ES5.

## Instalando

Para este tutorial, iremos utilizar o <a href="https://github.com/babel/babelify" target="_blank">Babelify</a>, um módulo <a href="https://www.npmjs.com/" target="_blank">npm</a> feito para funcionar juntamente com o <a href="http://browserify.org/" target="_blank">Browserify</a>, outro módulo que empacota todos os seus requires para serem usados no browser.

Para instalar ambos, é necessário ter instalado em seu computador o <a href="https://nodejs.org/" target="_blank">Node.js</a>, que juntamente instala o npm (Node Package Manager) ou Gerenciador de Pacotes Node.

Navegue via terminal até a raiz do seu projeto e digite o comando abaixo:

<pre class="lang-bsh">npm install --save-dev browserify babelify babel-preset-es2015
</pre>

O comando irá instalar o Browserify, Babelify e o plugin es2015 do Babel, responsável por cuidar da conversão de ES2015 para ES5, além de salvá-los na lista de devDependencies do seu <a href="https://docs.npmjs.com/files/package.json" target="_blank">package.json</a>. Nesta versão do Babel (6) nenhum plugin é instalado por padrão, por isso precisamos instalar ele à parte, você pode encontrar a lista completa de plugins <a href="http://babeljs.io/docs/plugins/" target="_blank">aqui</a>.

## Configurando

### Script

Para configurarmos via script, abra o seu arquivo <a href="https://docs.npmjs.com/files/package.json" target="_blank">package.json</a>, crie a sessão <a href="https://docs.npmjs.com/misc/scripts" target="_blank">scripts</a> e nela vamos adicionar o código que irá transformar seu código ES2015 para ES5:

<pre class="lang-js">"build-browserify": "browserify ./src/meuarquivo.js -t [ babelify --presets [ es2015 ] ] -o ./dist/meunovoarquivo.js"
</pre>

Explicando um pouco mais sobre o código acima:

./src/meuarquivo.js &#8211; Este é o local do seu arquivo JS escrito nos padrões ES2015.

-t [ babelify &#8211;presets [ es2015 ] ] &#8211; A option -t se refere à transform, que utiliza de módulos de transformação terceiros, neste caso o <a href="https://github.com/babel/babelify" target="_blank">Babelify</a>. Passamos o módulo que iremos utilizar e passamos uma option para o módulo (&#8211;presets), nesta option listamos os <a href="http://babeljs.io/docs/plugins/" target="_blank">plugins</a> que iremos utilizar do Babel, que será o es2015.

-o ./dist/meunovoarquivo.js &#8211; A option -o se refere à output, aqui passamos o destino do nosso arquivo, que será gerado após a transformação.

### Grunt

Podemos utilizar também o <a href="http://gruntjs.com/" target="_blank">Grunt</a>, um Task Runner de Javascript, para realizarmos a transformação do arquivo. Para isso é necessário instalarmos mais um módulo npm, o <a href="https://www.npmjs.com/package/grunt-browserify" target="_blank">grunt-browserify</a> (contando que você já tenha instalado em seu projeto os módulos <a href="https://www.npmjs.com/package/grunt" target="_blank">grunt</a> e <a href="https://www.npmjs.com/package/grunt-cli" target="_blank">grunt-cli</a>).

Novamente na raiz do seu projeto via terminal, digite o comando abaixo:

<pre class="lang-bsh">npm install --save-dev grunt-browserify
</pre>

Após a instalação, vá em seu arquivo <a href="http://gruntjs.com/sample-gruntfile" target="_blank">Gruntfile.js</a> e adicione no config:

<pre class="lang-js">browserify: {
    dist: {
        options: {
            "transform": [ ["babelify", { "presets": ["es2015"] }] ]
        },
        files: {
            './dist/meunovoarquivo.js': ['./src/meuarquivo.js']
        }
    }
}
</pre>

Depois, carregue o módulo e registre uma task:

<pre class="lang-js">grunt.loadNpmTasks('grunt-browserify');
grunt.registerTask('default', ['browserify']);
</pre>

## Conclusão

Ainda estamos iniciando essa nova fase de ES2015, porém já podemos perceber que o futuro espera muitas novidades e um crescimento maravilhoso do Javascript.