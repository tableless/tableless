---
title: Criando sua aplicação React em 2 minutos
author: DiegoPinho
type: post
date: 2016-08-05
excerpt: Configurar aplicações que utilizam React pode ser uma tarefa árdua e complexa... Babel, Webpack, ESLint, Autoprefixer... Mas agora não mais! Com o Create React App, é possível configurar o projeto em menos de 2 minutos!
url: /criando-sua-aplicacao-react-em-2-minutos/
categories:
  - JavaScript
  - ReactJS
tags:
  - JavaScript
  - ReactJS

---
Para facilitar a criação de aplicações utilizando React, o Facebook lançou uma ferramenta que promete reduzir toda complexidade envolvida em configurar um novo projeto que utilize a tecnologia.

O projeto chamado de “ Create React App”, divulgado por Dan Abramov no <a href="https://facebook.github.io/react/blog/2016/07/22/create-apps-with-no-configuration.html" rel="nofollow">blog oficial do React</a>, permite que os desenvolvedores criem suas aplicações React com apenas um comando. Não é criado somente a estrutura básica de pastas, mas também toda a configuração de build e dependências necessárias, ou seja, comandos complexos do <a href="https://babeljs.io/" rel="nofollow">Babel </a>e <a href="https://webpack.github.io/" rel="nofollow">Webpack</a>, usado na maior parte dos projetos, são abstraídos, permitindo ao desenvolvedor se concentrar no que realmente interessa: a sua aplicação.

No blog, Abramov diz que a motivação para a criação deste projeto é a associação que os desenvolvedores fazem do ecossistema de desenvolvimento do React com uma grande quantidade de ferramentas, principalmente Babel e Webpack, o que torna o processo de desenvolvimento lento e curva de aprendizado mais longa, principalmente quando se trata de aplicações que vão à produção.

Abramov reforça que quem já tem um processo de build que já funciona, deve mantê-lo. A ideia é que a ferramenta auxilie principalmente quem ainda não tem experiência com React.

Para o futuro há planos de adicionar mais funcionalidades, como adicionar testes. Abramov comentou que as atualizações serão feitas de forma gradual para deixar as configurações padrões mais flexíveis para cobrir mais casos de uso.

Para utilizá-lo, é bem simples. Inicialmente, precisamos utilizar o <a href="https://www.npmjs.com/" rel="nofollow">npm</a> para instalar a ferramenta globalmente na nossa máquina com o comando:

<pre class="lang-bash">npm install -g create-react-app</pre>

Feito isso, você já terá o Create React App instalado na sua máquina. Agora podemos criar um projeto utilizando o comando <em class="markup--em markup--p-em">create-react-app</em> seguido do nome do nosso projeto:

<pre class="lang-bash">create-react-app hello-world</pre>

Agora, se verificamos o projeto criado, podemos ver sua estrutura:

<pre class="lang-html">node_modules/
src/
.gitignore
README.md
favicon.ico
index.html
package.json
</pre>

Ao abrirmos o package.json, iremos notar que há somente uma dependência de desenvolvimento chamada **react-scripts** e três scripts:

<ul class="postList">
  <li id="147a">
    <strong>start:</strong> react-scripts start
  </li>
  <li id="a8df">
    <strong>build:</strong> react-scripts build
  </li>
  <li id="e01c">
    <strong>eject:</strong> react-scripts eject
  </li>
</ul>

<p class="graf--p graf-after--li">
  O script <em class="markup--em markup--p-em">start </em>iniciará nossa aplicação com base nos componentes que estão no diretório <em class="markup--em markup--p-em">src/</em>. Na criação, ele irá conter os seguintes arquivos:
</p>

<pre class="lang-html">App.css
App.js
index.css
index.js
logo.svg
</pre>

E terá a seguinte cara:

<img class="alignnone wp-image-55617 size-full" src="http://tableless.com.br/uploads/2016/08/1-pd5QJ5nHm0h9x4Fa9ey0AQ.png" alt="1-pd5QJ5nHm0h9x4Fa9ey0AQ" width="800" height="489" />

Ao alterar qualquer um dos arquivos e salvar, eles serão recompilados automaticamente e o browser também será atualizado. Se erros forem encontrados, eles são exibidos no console.

Uma vez que o projeto está pronto para ir para produção, podemos utilizar o script <em class="markup--em markup--p-em">build. </em>Ele será responsável por criar o diretório <em class="markup--em markup--p-em">build/, </em>onde o código estará pronto para produção.

No entanto, se em algum momento você não quiser mais depender da ferramenta para o desenvolvimento da sua aplicação, você pode executar o comando <em class="markup--em markup--p-em">eject</em>. Ele irá remover permanentemente a configuração padrão do Create React App e criará um diretório <em class="markup--em markup--p-em">config/ </em>com todas as “configurações cruas” que ele utiliza por padrão. Isso significa que o seu <em class="markup--em markup--p-em">package.json</em> será modificado para obter as dependências do Babel, Webpack e afins.

A <a href="https://github.com/facebookincubator/create-react-app" rel="nofollow">página oficial do projeto</a> no GitHub possui mais informações sobre a ferramenta.