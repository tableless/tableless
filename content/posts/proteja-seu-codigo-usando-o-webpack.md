---
title: Proteja seu código usando o Webpack
author: Jscrambler
type: post
date: 2016-11-28
url: /proteja-seu-codigo-usando-o-webpack/
titulo_personalizado:
  - 'Proteja seu código usando o <strong>Webpack</strong>'
categories:
  - Código
  - Destaques
  - JavaScript
  - Técnicas e Práticas
tags:
  - desenvolvimento
  - integração
  - JavaScript
  - segurança
  - Segurança Web
  - webpack

---
Não é um eufemismo dizer que que as ferramentas de front-end avançam rapidamente. Por um tempo, <a href="http://gruntjs.com/" target="_blank">Grunt</a> foi o principal automatizador. E desde então a comunidade adotou o <a href="http://gulpjs.com/" target="_blank">Gulp</a>, uma alternativa de streaming. Embora essas ferramentas sejam ótimas, você ainda precisará trabalhar dura para manter o seu sistema. E é aí que entram os empacotadores como o <a href="http://browserify.org/" target="_blank">Browserify</a> e <a href="https://webpack.github.io/" target="_blank">Webpack</a>.

## Como usar um empacotador

Os empacotadores resolvem o problema fundamental no desenvolvimento front-end. Eles permitem que você transforme assets arbitrários em algo que possa ser consumido por um navegador. Se você está usando NPM, e deveria, você pode empacotar todos esses pacotes que está utilizando em seu aplicativo para poder usá-los no navegador. Mas há a possibilidade de você querer fazer muitas outras coisas além de empacotar, então você vai entrelaçar isso com alguma ferramenta de automação como o Grunt ou Gulp. Você pode até ignorar um task runner e implementar suas tarefas por meio da seção de **scripts** `package.json` (se estiver usando NPM) para configurar as transformações do Browserify.

## Conhecendo o Webpack

Você pode alcançar resultados similares tanto com o Browserify quanto o Webpack. O Browserify está mais próximo da filosofia Unix. Ao usá-lo você está literalmente colando pequenos utilitários juntos. Como resultado, o Browserify é fácil de conseguir. Mas se você tem uma lista longa de transformações que deseja aplicar em seu código é melhor utilizar um task runner como Grunt ou Gulp para automatizar esse processo.

Por outro lado, se você usa Webpack pode nem precisar do Grunt ou Gulp. O Webpack presume que existem certas tarefas que você sempre deseja executar. É claro que você deseja mover os arquivos de uma pasta de origem para um diretório de compilação. Claro que você vai querer completar seu código fonte usando uma (geralmente longa) lista de transformações (aliás, elas são chamadas de **loaders**, ou carregadores, no Webpack). É claro que você quer usar bibliotecas em diferentes formatos de módulo como CoomonJS, RequireJS ou os novos módulos ES6 se desejar.

Você pode até desejar lidar com diferentes formatos de arquivos. Para lhe dar um exemplo melhor do que isso significa na prática, considere os códigos abaixo:

**style.css**

<pre class="lang-css">body {
    font-family: sans-serif;
}
</pre>

**index.js**

<pre class="lang-javascript">// load style to the resulting bundle
require('./style.css');

// just print hello, normally we would do
// something more involved and start the
// application here
console.log('hello world');</pre>

**webpack.config.js**

<pre class="lang-javascript">var webpack = require('webpack');

    module.exports = {
    // this is the top level file or set of files
    entry: './index.js',
    // it will bundle everything inside this output path
    output: {
    path: __dirname,
    filename: 'bundle.js'
},
module: {
loaders: [
{
    // 1. resolve @import and url() through css-loader
    // 2. load the result to bundle using style-loader
    // note that loaders are interpreted from right to left
    test: /.css$/, // A regexp to test the require path
    loaders: ['style', 'css']
}
]
},
plugins: [
    // minify output
    new webpack.optimize.UglifyJsPlugin()
]
};</pre>

O Webpack permite que você carregue o CSS da mesma forma que carrega outros códigos com <a href="https://github.com/webpack/css-loader" target="_blank">css-loader</a> e <a href="https://github.com/webpack/style-loader" target="_blank">style-loader</a>.

Por que você iria querer usar o require para o seu CSS em vez da mesma velha maneira que temos utilizado CSS? Bem, porque o Webpack é inteligente o suficiente para concatenar seu CSS quando ele é pequeno o bastante, caso contrário ele irá minificar o arquivo e dar a ele um nome único para fins de cache. O mesmo pode ser feito com imagens utilizando o <a href="https://github.com/webpack/url-loader" target="_blank">url-loader</a>.

Se você executou o Webpack contra essa configuração, você irá acabar com um `bundle.js` minificado que contém CSS inline. Pode parecer muito esforço para alcançar um simples resultado como esse. Isso está além do ponto. Considere o seguinte:

  * E se você quisesse usar os novos recursos do Javascript em seu projeto? Você teria que configurar o <a href="https://www.npmjs.com/package/babel-loader" target="_blank">babel-loader</a>.
  * E se você quisesse usar CSS compilado? Você precisaria configurar o <a href="https://github.com/webpack/less-loader" target="_blank">less-loader</a> ou o <a href="https://github.com/jtangelder/sass-loader" target="_blank">sass-loader</a>.
  * E se você quisesse sourcemaps? Você teria que configurar a opção <a href="https://webpack.github.io/docs/configuration.html#devtool" target="_blank">devtool</a>.
  * E se você quisesse uma saída UMD para sua biblioteca? É preciso configurar o <a href="https://webpack.github.io/docs/configuration.html#output-librarytarget" target="_blank">output.libraryTarget</a>.
  * E se você quisesse um servidor de desenvolvimento _hot loading_? Você precisaria configurar o <a href="https://webpack.github.io/docs/webpack-dev-server.html" target="_blank">webpack-dev-server</a> ou construir um sozinho baseado no Express, como mostrado no <a href="https://github.com/gaearon/react-transform-boilerplate" target="_blank">react-transform-boilerplate</a>. O recurso de _hot loading_ separa Webpack conforme atualiza seu navegador automaticamente enquanto mantém o estado do aplicativo.
  * E se você quisesse múltiplas metas (desenvolvimento, produção, teste)? Poderia usar uma solução como a <a href="https://www.npmjs.com/package/webpack-merge" target="_blank">webpack-merge</a> e conectar seu automatizador de tarefas com ela.
  * E se você quisesse carregar algumas dependências lentamente? Você precisaria configurar o <a href="https://webpack.github.io/docs/code-splitting.html#require-ensure" target="_blank">require.ensure</a>. O Webpack irá gerar pacotes separados para dividir os pontos e carregá-los sob demanda.

Basicamente, você pode desenvolver as configurações para várias direções baseado em suas necessidades. Há definitivamente uma curva de aprendizado e leva um tempo para entender todas as opções. Dito isso, a abordagem é poderosa uma vez que você entende.

## Conectando o Webpack com Jscrambler

Se você quiser adicionar o Jscrambler para o seu processo de desenvolvimento e estiver usando o Webpack, nós temos uma boa notícia para você! O <a href="https://github.com/jscrambler/jscrambler-loader" target="_blank">jscrambler-loader</a> está disponível e é realmente fácil de configurar assim como a maioria dos loaders do Webpack.

Nós vamos lhe mostrar o quanto essa configuração é fácil utilizando o exemplo abaixo e adicionando o <a href="https://github.com/jscrambler/jscrambler-loader" target="_blank">jscrambler-loader</a> em nosso processo. Também vamos remover o **UglifyJsPlugin**, já que o **Jscrambler** pode desempenhar essa mesma função.

**webpack.config.js**

<pre class="lang-javascript">var webpack = require('webpack');

    module.exports = {
    // this is the top level file or set of files
    entry: './index.js',
    // it will bundle everything inside this output path
    output: {
    path: __dirname,
    filename: 'bundle.js'
},
module: {
loaders: [
{
    // 1. resolve @import and url() through css-loader
    // 2. load the result to bundle using style-loader
    // note that loaders are interpreted from right to left
    test: /.css$/, // A regexp to test the require path
    loaders: ['style', 'css']
},
{
    test: /.js$/,
    exclude: /node_modules/,
    loader: 'jscrambler-loader'
}
]
}
};</pre>

Você também irá precisar criar um arquivo chamado **.jscramblerrc** com suas credenciais da API.
  
Você irá encontrar elas no painel de controlo da sua conta Jscrambler.

**.jscramblerrc**

<pre class="lang-javascript">{
    "keys": {
    "accessKey": "XXXXXX",
    "secretKey": "XXXXXX"
},
"params": {
    "self_defending": "%DEFAULT%"
    // there is a big set of transformations that you can use
    // check https://jscrambler.com/en/help/javascript_obfuscation
}
}</pre>

Pronto! Você está pronto para depurar o seu código protegido!

Há várias outras formas de conectar o Jscrambler com o seu sistema. Isso depende do seu task runner. Eu reuni as possíveis abordagens abaixo:

  1. Grunt &#8211; <a href="https://www.npmjs.com/package/grunt-jscrambler" target="_blank">grunt-jscrambler</a>
  2. Gulp &#8211; <a href="https://www.npmjs.com/package/gulp-jscrambler" target="_blank">gulp-jscrambler</a>
  3. _package.json_ &#8211; <a href="https://www.npmjs.com/package/jscrambler" target="_blank">Jscrambler CLI tool</a>. Para isso funcionar, crie um _script_ separado e depois passe sua versão minificada do Webpack através dele. É preferível manter uma versão local da ferramenta Jscrambler CLI (`npm i jscrambler --save-dev`) dentro de seu projeto para que tudo funcione independentemente do ambiente.

O Jscrambler tem um conjunto de ferramentas para proteger seu código (ofuscação + armadilhas no código + serviço de autoproteção de aplicativo, ou RASP em inglês), fazendo com que a engenharia reversa fique significantemente difícil, mas também tem alguns recursos de otimização de código para você tirar vantagem. Você pode até usá-lo para minificação ou compressão.

Saiba mais sobre o Jscrambler em <a href="https://jscrambler.com?utm_medium=social&utm_source=tableless" target="_blank">jscrambler.com</a>.

## Conclusão

Ainda que o Webpack não seja a ferramenta mais fácil de aprender, eu recomendo que você dê uma olhada nela. O livro <a href="http://survivejs.com/" target="_blank">SurviveJS &#8211; Webpack and React</a>, que está em inglês, fala sobre essa ferramenta com mais detalhes. A maioria dos conteúdos está disponível gratuitamente e irá lhe ajudar a entender o Webpack e React a um nível mais profundo.