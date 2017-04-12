---
title: Integração Contínua com Travis CI — Parte 01
author: Jaime Neves
type: post
date: 2016-12-12
url: /integracao-continua-com-travis-ci - parte-01/
titulo_personalizado:
  - 'Integração Contínua com <strong>Travis CI </strong>'
categories:
  - Destaques
  - Técnicas e Práticas

---
O objetivo geral do artigo é mostrar como fazer uma Integração Contínua (técnica de desenvolvimento agile) com [Travi CI][1], criando um repositório no [O objetivo geral do artigo é mostrar como fazer uma Integração Contínua (técnica de desenvolvimento agile) com [Travi CI][1], criando um repositório no][2] e publicando nosso projeto em um Host utilizando o [Heroku][3].

Nesse primeiro post iremos montar toda nossa estrutura de diretórios e configuração de arquivos. Por fim iremos criar nosso repositório no GitHub e enviar o nosso projeto local.

No segundo post iremos registrar nossa aplicação no Dribbble, configurar o Travis e Heroku e finalizar nossa aplicação client-side.

**Sobre o Travis**

Travis CI é uma plataforma/serviço de <a class="markup--anchor markup--p-anchor" href="https://en.wikipedia.org/wiki/Continuous_integration" target="_blank" rel="nofollow">Integração Contínua</a>, que é free para todos os projetos open source hospedados no GitHub. Com apenas um arquivo chamado <em class="markup--em markup--p-em">.travis.yml</em> contendo algumas informações sobre o projeto, podemos produzir builds automatizados com todas as mudanças, para o branch master ou outro, e até mesmo através de <em class="markup--em markup--p-em">pull request</em>.

**Pré Requisitos**

  * Conta no GitHub
  * Conta no Heroku
  * Para o Travis você poderá usar a mesma conta do GitHub
  * Git, NodeJS e Bower instalado
  * Um editor de texto: Sublime Text, Atom ou qualquer outro de sua preferência.

**Descrição do Projeto**

Iremos implementar uma aplicação client-side que consulta uma API do site **[O objetivo geral do artigo é mostrar como fazer uma Integração Contínua (técnica de desenvolvimento agile) com [Travi CI][1], criando um repositório no [O objetivo geral do artigo é mostrar como fazer uma Integração Contínua (técnica de desenvolvimento agile) com [Travi CI][1], criando um repositório no][2] e publicando nosso projeto em um Host utilizando o [Heroku][3].

Nesse primeiro post iremos montar toda nossa estrutura de diretórios e configuração de arquivos. Por fim iremos criar nosso repositório no GitHub e enviar o nosso projeto local.

No segundo post iremos registrar nossa aplicação no Dribbble, configurar o Travis e Heroku e finalizar nossa aplicação client-side.

**Sobre o Travis**

Travis CI é uma plataforma/serviço de <a class="markup--anchor markup--p-anchor" href="https://en.wikipedia.org/wiki/Continuous_integration" target="_blank" rel="nofollow">Integração Contínua</a>, que é free para todos os projetos open source hospedados no GitHub. Com apenas um arquivo chamado <em class="markup--em markup--p-em">.travis.yml</em> contendo algumas informações sobre o projeto, podemos produzir builds automatizados com todas as mudanças, para o branch master ou outro, e até mesmo através de <em class="markup--em markup--p-em">pull request</em>.

**Pré Requisitos**

  * Conta no GitHub
  * Conta no Heroku
  * Para o Travis você poderá usar a mesma conta do GitHub
  * Git, NodeJS e Bower instalado
  * Um editor de texto: Sublime Text, Atom ou qualquer outro de sua preferência.

**Descrição do Projeto**

Iremos implementar uma aplicação client-side que consulta uma API do site **][4]** e mostre os Shots mais populares. Usaremos as seguintes tecnologias no front-end: **[Angularjs][5]** e **[Materialize.css][6]** como framework de componentes. Para gerenciar os pacotes e dependências utilizaremos o Bower. No server-side usaremos a plataforma NodeJS como nosso servidor web, e o **[Gruntjs][7]** para automatizar algumas tarefas. Para o versionamento utilizaremos o **Git**.

**Criando Nossa Estrutura de Diretórios**

<img class="aligncenter" src="https://cdn-images-1.medium.com/max/800/1*b5H0NRwfSN13Ex659Hw_Ag.png" alt="Estrutura de Diretórios" />

Os arquivos e diretórios podem ser criados da maneira que você se sentir mas a vontade. **OBS.:** Não crie o diretório “.git”, pois ele será criado através da nossa linha de comando, o restante pode ser criado manualmente.

**Detalhamento da Estrutura**

<ul class="postList">
  <li id="4172" class="graf graf--li graf-after--h4">
    <strong class="markup--strong markup--li-strong">client</strong>: diretório onde ficará todos os nossos arquivos de front-end.
  </li>
  <li id="fc63" class="graf graf--li graf-after--li">
    <strong class="markup--strong markup--li-strong">.bowerrc</strong>: arquivo de configuração do <em class="markup--em markup--li-em">Bower</em>, é nele que iremos definir onde serão instalados nossos pacotes. Se você não criá-lo as dependências serão instaladas no diretório chamado <em class="markup--em markup--li-em">bower_components</em> padrão do bower.
  </li>
  <li id="d36f" class="graf graf--li graf-after--li">
    <strong class="markup--strong markup--li-strong">.gitignore</strong>: arquivos que podem ser ignorados pelo versionamento do Git.
  </li>
  <li id="94ba" class="graf graf--li graf-after--li">
    <strong class="markup--strong markup--li-strong">.travis.yml</strong>: arquivo de configuração da nossa integração com o Travis.
  </li>
  <li id="c613" class="graf graf--li graf-after--li">
    <strong class="markup--strong markup--li-strong">Gruntfile.js</strong>: arquivo onde ficará todas as configurações de tarefas automatizadas, como por exemplo: concatenação e minificação dos arquivos.
  </li>
  <li id="2e90" class="graf graf--li graf-after--li">
    <strong class="markup--strong markup--li-strong">server.js</strong>: arquivo onde faremos a configuração de nosso servidor web.
  </li>
</ul>

deixe o diretório <strong class="markup--strong markup--p-strong">client</strong> com a seguinte estrutura:

<img class="aligncenter" src="https://cdn-images-1.medium.com/max/800/1*5ohek1gfXzLGL5OTdmrcPQ.png" alt="Diretório Client" />

código do arquivo <strong class="markup--strong markup--p-strong">.bowerrc</strong>

`{<br />
"directory" : "client/vendor"<br />
}`

código do arquivo <strong class="markup--strong markup--p-strong">.gitignore</strong>

`node_modules/`

código do arquivo .travis.yml

`language: node_js<br />
node_js:<br />
- "6.1"<br />
- "5.12.0"<br />
- "5.11.1"`

código do arquivo <strong class="markup--strong markup--p-strong">server.js</strong>

`var express = require('express');<br />
var serveStatic = require('serve-static');<br />
var app = express();<br />
var client = process.env.NODE_APP_DIRECTORY === 'production'<br />
? '/client/dist' : '/client';<br />
var port = process.env.PORT || 8081;<br />
app.use(serveStatic(__dirname + client));<br />
app.listen(port,function(){<br />
console.log('localhost:'+port);<br />
});`

Link para o código do arquivo **[server.js][8] **no GitHub**.**

código do arquivo <strong class="markup--strong markup--p-strong"><a href="https://gist.github.com/dejaneves/996644e20b2f651939c2da892dbea555#file-gruntfile-ci-agile-th-js">Gruntfile.js</a>. </strong>O código e toda sua configuração, será explicado na segunda parte do post.

#### Bower: Instalação dos Pacotes e suas dependências {#d351.graf.graf--h4.graf-after--figure}

Vá para raiz do projeto e digite o seguinte comando para instalação das dependências.

`$ bower install angular angular-resource angular-ui-router angular-sanitize<br />
angular-loading-bar bootstrap materialize`

após a execução desse comando o seu diretório <strong class="markup--strong markup--p-strong">client/vendor</strong> ficará da seguinte forma:

<img class="aligncenter" src="https://cdn-images-1.medium.com/max/800/1*0z-hRCazRdhCpIMfe3gQ1g.png" alt="Pasta Client" />

#### Nodejs: Instalação e Configuração dos Pacotes {#40e5.graf.graf--h4.graf-after--figure}

`$ npm init -y`

após a execução desse comando será criado um arquivo na raiz do seu projeto chamado <em class="markup--em markup--p-em">package.json</em>.

#### Instalação das Dependências {#bf1d.graf.graf--h4.graf-after--p}

`$ npm install express serve-static --save`

#### Iniciando o Versionamento com o GIT {#3693.graf.graf--h4.graf-after--pre}

`$ git init<br />
$ git add .<br />
$ git commit -m "primeiro commit"`

#### Executando a aplicação {#6204.graf.graf--h4.graf-after--pre}

`node server.js`

o seu sistema terá que exibir a seguinte mensagem

`client: /client<br />
environment: undefined<br />
localhost:8081`

para parar a execução do servidor pressione <strong class="markup--strong markup--p-strong">ctrl</strong> + <strong class="markup--strong markup--p-strong">c</strong>.

### Criando Repositório no GitHub {#66d0.graf.graf--h3.graf-after--p}

<p id="3970" class="graf graf--p graf-after--h3">
  Abra o site do <a class="markup--anchor markup--p-anchor" href="https://github.com/" target="_blank" rel="nofollow">GitHub</a>, crie um repositório público chamado <strong class="markup--strong markup--p-strong">ci-agile-th.</strong>
</p>

![Criando um repositório][9]

após a criação aparecerá a seguinte tela

![Repositório][10]digite os comandos que estão dentro do 2º bloco na raiz do seu projeto

`$ git remote add origin https://github.com/dejaneves/ci-agile-th.git<br />
$ git push -u origin master`

te espero no próximo post.

### Links Úteis {#8a4b.graf.graf--h3.graf-after--p}

<p id="0259" class="graf graf--p graf-after--h3">
  Instalação do NodeJS
</p>

<ul class="postList">
  <li id="67c7" class="graf graf--li graf-after--p">
    <a class="markup--anchor markup--li-anchor" href="https://udgwebdev.com/node-js-para-leigos-instalacao-e-configuracao" target="_blank" rel="nofollow">Underground WebDev</a>
  </li>
  <li id="0c62" class="graf graf--li graf-after--li">
    <a class="markup--anchor markup--li-anchor" href="http://tableless.com.br/o-que-nodejs-primeiros-passos-com-node-js" target="_blank" rel="nofollow">Tableless</a>
  </li>
  <li id="e04c" class="graf graf--li graf-after--li">
    <a class="markup--anchor markup--li-anchor" href="https://www.digitalocean.com/community/tutorials/como-instalar-o-node-js-em-um-servidor-ubuntu-14-04-pt" target="_blank" rel="nofollow">Digitalocean</a>
  </li>
</ul>

<p id="273d" class="graf graf--p graf-after--li">
  Instalação do Bower
</p>

<ul class="postList">
  <li id="caf2" class="graf graf--li graf-after--p">
    <a class="markup--anchor markup--li-anchor" href="http://tableless.com.br/bower-na-pratica" target="_blank" rel="nofollow">Tableless</a>
  </li>
  <li id="4a32" class="graf graf--li graf-after--li">
    <a class="markup--anchor markup--li-anchor" href="http://www.carvalhoweb.com/articles/bower-guia-definitivo" target="_blank" rel="nofollow">Carvalho Web</a>
  </li>
  <li id="1621" class="graf graf--li graf-after--li graf--last">
    <a class="markup--anchor markup--li-anchor" href="http://blog.thiagobelem.net/gerenciando-assets-com-o-bower" target="_blank" rel="nofollow">Thiago Belem</a>
  </li>
</ul>

 [1]: https://travis-ci.com/
 [2]: https://github.com/
 [3]: https://www.heroku.com/
 [4]: https://dribbble.com
 [5]: https://angularjs.org/
 [6]: http://materializecss.com
 [7]: http://gruntjs.com/
 [8]: https://gist.github.com/dejaneves/b983dd0cfd54d63d6bd9f4310a812289
 [9]: https://cdn-images-1.medium.com/max/800/1*h3yRLVKf2peVF_UucGQYJg.png
 [10]: https://cdn-images-1.medium.com/max/800/1*VQf-VyPNBK8dSQl3Lqmq_A.png