---
title: 'Yarn: A evolução do NPM'
author: Daniel Campos
type: post
date: 2016-11-03
excerpt: 'No dia 11 de outubro de 2016, o Facebook anunciou o seu novo gerenciador de pacotes para Javascript: o Yarn, que vem com a proposta de ser mais rápido, seguro e confiável que o NPM. O Yarn é open source, e nasceu com a colaboração, também, das empresas Exponent, Google, e Tilde.'
url: /yarn-evolucao-do-npm/
titulo_personalizado:
  - 'Conheça o <strong>Yarn</strong>.'
categories:
  - Código
  - Destaques
  - JavaScript
  - Tecnologia e Tendências
tags:
  - npm
  - package
  - yarn

---
<img class="aligncenter wp-image-56337" style="text-align: center" src="http://tableless.com.br/uploads/2016/10/yarn-kitten-full.png" alt="yarn-kitten-full" width="300" height="135" />

Nos primórdios do desenvolvimento web e afins, trabalhar com bibliotecas era uma tarefa árdua. Lembro que tínhamos que pesquisar pela biblioteca, escolher uma versão, baixar o zip e implementar em nosso projeto. Não parece nada de outro mundo ao se tratar de pequenos projetos, mas quando estamos falando de projetos um pouco maiores, isso se torna um transtorno.  A coisa se torna ainda mais complicada quando há a dependência entre bibliotecas.

Nesse contexto, entram os gerenciadores de pacotes, que chegaram para revolucionar a maneira como lidamos com as dependências de nosso projetos. Um dos principais gerenciadores de pacotes é o [NPM][1], que inicialmente visava abastecer apenas os desenvolvedores de NodeJS, mas acabou se tornando um hub comum de dependências Javascript em geral. O NPM hoje conta com mais de 300mil bibliotecas em seu repositório central, as quais alcançam cerca  5 bilhões de downloads por mês, e é a ferramenta de gerenciamento de pacotes mais popular do mundo.

Apesar de ser uma excelente ferramenta, o NPM nunca conseguiu agradar a todos, e são comuns as reclamações de lentidão, a falta de um instalador offline, instalações em fila, etc.

## Yarn Package Manager

No dia 11 de outubro de 2016, o Facebook [anunciou][2] o seu novo gerenciador de pacotes para Javascript: o Yarn, que vem com a proposta de ser mais rápido, seguro e confiável que o NPM. O Yarn é open source, e nasceu com a colaboração, também, das empresas Exponent, Google, e Tilde.

O Yarn funciona exatamente como o NPM e o Bower, abrangendo, inclusive, as bibliotecas que estão presentes nestes gerenciadores. Uma das coisas mais interessantes, além da rapidez, é a possibilidade de instalação de pacotes offline. Quando você instala um pacote, ele cria um cache em sua máquina que possibilita a futura instalação deste sem precisar estar conectado à internet.

## Instalando o Yarn

Para a instalação, você pode baixar no [site oficial][3], mas também pode utilizar outro gerenciador, como o NPM (confesso que parece irônico, como quando utilizávamos o Internet Explorer para baixar o Chrome).

<pre class="prettyprint">npm install -g yarn
</pre>

## Utilizando o Yarn

### Inicialização

A utilização do Yarn é bastante semelhante com a do NPM. Para inicializar basta digitar, na linha de comando:

<pre class="prettyprint">yarn init
</pre>

Este comando irá gerar um arquivo **package.json**

<pre class="prettyprint">{
"name": "Yarn",
"version": "1.0.0",
"main": "index.js",
"license": "MIT"
}
</pre>

O gerenciamento dos pacotes pode ser feito diretamente no _package.json_, ou pela linha de comando.

### Adicionando uma dependência

<pre class="prettyprint">yarn add [package]
yarn add [package]@[version]
yarn add [package]@[tag]
</pre>

### Fazendo update

<pre class="prettyprint">yarn upgrade [package]

yarn upgrade [package]@[version]
yarn upgrade [package]@[tag]
</pre>

### Desfazendo as coisas

<pre class="prettyprint">yarn remove [package]
</pre>

### Instalando as dependências

<pre class="prettyprint">yarn
</pre>

ou

<pre class="prettyprint">yarn install
</pre>

## Outras funcionalidades

### Lock file

Além do package.json, o Yarn cria, na pasta raíz do projeto, um arquivo yarn.lock, que trata de listar as bibliotecas &#8220;originais&#8221; do projeto, um sistema bem semelhante ao do composer.

### Fazendo uma limpeza

Outro recurso interessante é o mecanismo de limpeza de dependências, ao executar o comando:

<pre class="prettyprint">yarn clean
</pre>

O Yarn vasculha as dependências e verifica tudo aquilo que não está sendo utilizado e exporta para um arquivo **.yarnclean**. Caso você tenha este arquivo em sua pasta raíz, quando executar o **yarn install**, ele vai instalar as dependências de forma mais limpa.

### Self-update

Para atualizar o Yarn, basta digitar no console:

<pre class="prettyprint">yarn self-update
</pre>

ou, caso queira especificar a versão:

<pre class="prettyprint">yarn self-update 0.1.2
</pre>

## 

## Futuro

Em todos os testes realizados, o Yarn se mostrou um gerenciador de pacotes bastante robusto e completo. De fato, o Yarn é extremamente rápido. Estou utilizando-o há cerca de uma semana, e, sinceramente, não penso em voltar a utilizar o NPM.
  
A sua equipe de desenvolvimento está incentivando todos a migrarem e contribuirem na sua página do [github][4], afinal todos só temos a ganhar com esta nova e excelente ferramenta.

 [1]: https://www.npmjs.com/
 [2]: https://code.facebook.com/posts/1840075619545360
 [3]: https://yarnpkg.com/en/docs/install
 [4]: https://github.com/yarnpkg/yarn