---
title: Em um relacionamento sério com generators front-end – Parte 3
author: Beto Muniz
type: post
date: 2015-02-06
excerpt: Nesta terceira parte da série, iremos abordar o Slush Generator, que é um Scaffolding Generator baseado em NodeJS e que tem uma forma diferenciada para criação de seus scaffolds.
url: /em-um-relacionamento-serio-com-generators-front-end-parte-3/
categories:
  - Código
  - CSS
  - Geral
  - HTML
  - HTML5
  - JavaScript
  - Técnicas e Práticas
  - Tecnologia e Tendências
tags:
  - generators
  - gulp
  - Node
  - slush

---
<h2 style="text-align: center">
  <img class="aligncenter size-full wp-image-46781" src="http://tableless.com.br/uploads/2015/02/pngbase643ef91c517603490c.png" alt="png;base643ef91c517603490c" width="281" height="408" srcset="uploads/2015/02/pngbase643ef91c517603490c.png 281w, uploads/2015/02/pngbase643ef91c517603490c-96x139.png 96w" sizes="(max-width: 281px) 100vw, 281px" />
</h2>

## TL;DR

Antes de iniciarmos o post, vale lembrar que em momento nenhum eu e o <a href="https://twitter.com/PedroPolisenso" target="_blank">Pedro Polisenso</a> estamos elegendo o melhor ou pior generator, visto que o output desse tipo de ferramenta é geralmente o mesmo dependendo da comparação, sendo assim, cabe a você analisar prós e contras de cada um e realizar uma escolha satisfatória pra sua necessidade.

**Mas vamos parar de mimimi e vamos ao que importa.**

## Slush, um gerador baseado em streamings (e no gulp).

Nossa! Entramos no assunto principal e de cara deixando explícito que o <a href="http://slushjs.github.io/" target="_blank">Slush</a> utiliza Streamings e o Gulp, e se usa eles, já que todo mundo fala de Streamings e Gulp, é porque é bom, não é? Mas o que são Streamings e porque isso pode fazer a diferença na escolha do Slush como gerador? E que raios é esse tal de Gulp?

### Stream

Sendo bem objetivo, <a href="http://pt.wikipedia.org/wiki/Stream" target="_blank">Stream</a> é um processo computacional para lidar com informações. Ok, mas o que isso quer dizer para nós? Quer dizer que&#8230;

_**Streams está para o Slush, Como a cereja está para o bolo.**_

Isso mesmo! E quando digo isso, é porque, ao utilizar Streamings ganhamos agilidade para trabalhar com dados provenientes de arquivos ou seja lá qual for a origem, pois esta forma de processo, armazena toda a informação em memória, o que não nos obriga por exemplo, abrir(_ler_) e fechar(_escrever_) arquivos e/ou conexões o todo tempo para manipular essa informação, além de outros benefícios, que não vou abordar neste post, visto que o foco dele é o Slush, certo? 😀

### Gulp

O <a href="http://gulpjs.com/" target="_blank">Gulp</a> é um Task Runner baseado em Streamings, e ao ler isso, normalmente a pessoa faz uma cara de espertinho, sabendo de cara que esse é o motivo do Slush ser um Scaffolding Generator baseado em Streamings (_dã_). Ok! Mas ao chegar nessa conclusão, o que digo a vocês é que estão **CERTÍSSIMOS** 😉

Mas não é só isso, Gulp é de fácil uso, alta eficiência e qualidade de código, e além de tudo, fácil de aprender e isso o Slush herda por default ao utilizar ele.

Tá! Mas não da pra falar do Gulp sem falar do Grunt (_mimimi4ever_), porém, não quero gerar nenhum flame, o principal tópico que tenho a dizer sobre isso, é que no final, ambos tem a mesma finalidade, mas a forma de execução e as vezes de processamento, é que pode variar… oO&#8230;mas vamos deixar esses breves conceitos embutidos pra lá e voltar ao assunto principal&#8230;

## Tudo bem, mas&#8230; é só isso que o Slush tem de bom?

Se fosse só o uso do Gulp e Streamings já seria bastante coisa, mas a boa notícia é que o Slush tem muito mais a oferecer, e para ilustrar, fiz uma pequena lista de benefícios trazidos por ele:

  * <a href="http://slushjs.github.io/generators/#/" target="_blank">Repositório de Generators oficial</a>;
  * É extremamente flexível para criação e distribuição de Generators;
  * Faz tudo que o Grunt faz, e muita das vezes de forma bem mais simples;
  * Utiliza o Gulp em sua base e que por sua vez aplica outros inúmeros benefícios e comodidades;
  * É totalmente testavél.

## Entendi e gostei, como faço para começar a utilizar?

#### Instalação

Para instalar o Slush, basta você ter o <a href="http://nodejs.org/" target="_blank">NodeJS</a> no seu computador e executar o seguinte comando no terminal:

     $ npm install -g slush

Para testar a instalação, basta executar o comando:

     $ slush -v

Se ele retonar a versão do mesmo, é porque ocorreu tudo supimpa (_rs&#8230;_).

#### Utilizando Generators de terceiros

Para utilizar Generators de terceiros ou até mesmo distribuir e utilizar os que você criar em qualquer lugar daqui pra frente, vamos recorrer ao repositório disponibilizado pelo <a href="http://joakim.beng.se/" target="_blank">criador do Slush</a>, que você pode conferir <a href="http://slushjs.github.io/generators/#/" target="_blank">aqui</a>. Nele existem centenas de Generators dos mais variados tipos e finalidades, e para exemplificar o uso de Generators de terceiros, irei utilizar um que eu mesmo criei: O <a href="https://github.com/webcomponents/slush-element/" target="_blank"><strong>slush-element</strong></a>, que basicamente serve pra criar Web Components, utilizando-se do padrão do Polymer, X-Tags ou Nativo (VannilaJS).

Para iniciarmos o uso do generator **element**, precisamos instalar o mesmo e para isso, basta executar o seguinte comando no terminal:

     $ npm install -g <strong>slush-element</strong>

Após concluir a instalação, você poderá executar esse generator em sua forma _default_ ou através de tarefas disponibilizadas, e a forma de se fazer isso, eu exemplifico logo abaixo:

     # Executando tarefa <em>'default'</em> do generator <strong>element</strong>
     $ slush element

Ou então, se desejar e caso exista alguma tarefa específica, faça o seguinte:

     # Executando tarefa <em>'repo'</em> do generator <strong>element</strong>
     $ slush element:<strong>repo</strong>

Mas claro, existem múltiplas opções de saída dentro deste exemplo, porém, vai lá, instala o generator, teste-o e divirta-se, e principalmente se você curtir o assunto Web Components como eu, este gerador será uma super mão na roda pra você. Mas para saber mais sobre ele, acesse este [link][1].

## Bacana, mas e seu eu quiser fazer um? #comofaz

Bom, não irei aprofundar muito nos detalhes de criação, pois dá pra fazer uma série só sobre esses detalhes, mas irei demonstrar os arquivos necessários para desenvolvermos um Generator para o Slush e também colocarei o conteúdo que cada um deles necessita com comentários explicativos, mas qualquer dúvida a mais que você tiver, é só deixar nos comentários! Vou ter um prazer enorme em responder. E lá vamos nós 😀

<pre>slush-boilerplate/
   node_modules/         # Diretório de instalação local das dependências obrigatórias do Slush e do seu generator, se ele tiver alguma.
   templates/            # Local que armazenamos os templates do generator.
   templates/index.html  # Arquivo* de template [<em>*poderia ser qualquer arquivo</em>].
   package.json          # Arquivo de configuração do NodeJS e onde ficam declaradas as dependências do Slush   Generator.
   slushfile.js          # Arquivo de configuração que o Slush busca para execução do generator.</pre>

### Arquivo package.json

Em primeiro lugar, vou falar do _package.json,_ que além de declarar as dependências necessárias para que o Slush e o Generator possa trabalhar, possui uma keyword chamada **slushgenerator**, que é obrigatória para indexação no repositório oficial de Generators do Slush, mas não se preocupe em colocar outras além dessa, pois isso também ajudará na hora de buscar pelo seu Generator. Segue o modelo do package.json do nosso Generator abaixo:

    {
      "name": "slush-boilerplate",
      "description": "A slush generator boilerplate",
      "version": "1.0.0",
      "homepage": "https://github.com/obetomuniz/slush-boilerplate",
      "author": {
        "name": "Beto Muniz",
        "email": "contato@betomuniz.com"
      },
      "repository": {
        "type": "git",
        "url": "git://github.com/obetomuniz/slush-boilerplate.git"
      },
      "bugs": {
        "url": "https://github.com/obetomuniz/slush-boilerplate/issues"
      },
      "licenses": [{
        "type": "MIT",
        "url": "https://github.com/obetomuniz/slush-boilerplate/blob/master/LICENSE"
      }],
      "main": "slushfile.js",
      "dependencies": {
    <strong>    "gulp": "^3.8.7",
        "gulp-conflict": "^0.3.0",
        "gulp-install": "^0.2.0",
        "gulp-template": "^2.0.0",
        "inquirer": "^0.8.0"</strong>
      },
      "keywords": [
        "<strong>slushgenerator</strong>"
      ]
    }

#### Arquivo slushfile.js

Em segundo lugar e não menos importante, iremos criar o _slushfile.js_, mas para entender melhor como funciona cada parte, leia os comentários no conteúdo logo abaixo:

    'use strict';
    
    // Requisição das dependências do Slush
    var gulp = require('gulp'),
        install = require('gulp-install'),
        conflict = require('gulp-conflict'),
        template = require('gulp-template'),
        inquirer = require('inquirer');
    
    // Aqui está nossa tarefa default, ou seja, ao executarmos o comando `<em>slush boilerplate</em>`, esta tarefa é a que será chamada.
    gulp.task('default', function(done) {
    
      // Está é a lista de perguntas. Podemos aplicar uma ou mais perguntas, e de diferentes tipos como: lista, checklist, boleano, texto, etc.
      var prompts = [{
        name: 'seuNome',
        message: "Qual seu nome?",
        default: "Fulano de Tal"
      }];
    
      inquirer.prompt(prompts, function(answers) {
    
        // Aqui os templates são declarados para serem encontrados no diretório `<em>templates</em>`
        var files = [];
        files.push(__dirname + '/templates/**');
    
        // Executando e processando nossos arquivos a serem gerados.
        gulp.src(files)
          .pipe(template(answers))
          .pipe(conflict('./'))
          .pipe(gulp.dest('./'))
          .pipe(install())
          .on('end', function() {
            done();
          });
      });
    });

#### Diretório \`_templates_\`

Neste diretório serão armazenado os arquivos que serão entregues ao se utilizar o Generator. No nosso caso, iremos entregar dentro do diretório apenas um arquivo _index.html_, mas nada impede você de colocar imagens, vídeos, sub-diretórios, arquivos de JavaScript, folhas de estilo, Markdown, ou seja, qualquer tipo de arquivo pode ser um “template” aqui dentro.

#### Arquivo \`_index.html_\` dentro do diretório \`_templates_\`

<pre class="prettyprint lang-html"><code>&lt;!DOCTYPE html&gt;
&lt;html&gt;
&lt;head&gt;
  &lt;meta charset="UTF-8"&gt;
  &lt;title&gt;Slush - Simple Bootstrap&lt;/title&gt;
&lt;/head&gt;
&lt;body&gt;
  &lt;h1&gt;Olá, &lt;%= seuNome %&gt;.&lt;/h1&gt; &lt;!-- Repare que coloco a mesma declaração de variável que eu crio na resposta da pergunta do slushfile.js. --&gt;
&lt;/body&gt;
&lt;/html&gt;</code></pre>

E basicamente serão estes 3 arquivos + um sub-diretório que iremos precisar.

Para testar localmente, além de ter o Slush instalado e ter rodado o comando `npm install` no diretório do nosso Generator, será preciso executar no seu terminal o comando `npm link .` dentro do diretório do nosso Generator, e assim, o mesmo será adicionado a lista de módulos do NPM do seu computador para uso normal.

Em no nosso caso após executar o comando `npm link .` iremos executar o comando abaixo dentro de uma pasta qualquer:

     $ slush boilerplate

Ao fazer isso, será perguntado a você o seu nome, e em seguida, um arquivo _index.html_ será criado  neste diretório. Sim, é só isso mesmo 🙂

E por fim, para distribuir seu generator, será necessário uma conta no <a href="https://www.npmjs.com/" target="_blank">NPMJS.ORG</a> e a execução do comando `npm publish` dentro do diretório do seu Generator. Caso você não esteja logado localmente no NPM, ao executar o comando, será solicitado seu **username, senha e email** cadastrados no _NPMJS.ORG_, para prosseguir, basta oferecer tais dados e executar novamente o comando `npm publish`. E por fim, pra conferir a publicação, basta acessar sua conta no _NPMJS.ORG_.

**OBS:** Se seu Generator tiver a keyword **slushgenerator**, em pouco tempo ele será adicionado automaticamente no Repositório oficial de Generators do Slush.

## E isso é tudo pessoal&#8230; o/

Mas antes de fechar o post, primeiramente espero que tenham gostado do tema e agradeço imensamente a leitura, mas deixo a dica para que não se prendam apenas nesse post, sempre busquem outras fontes de conhecimento, pois só assim, o seu senso crítico irá evoluir. Ah! E não deixem pra lá outros tópicos abordados aqui, como Streamings, Gulp, Grunt e bolos (sim, bolos).

Mas é isso&#8230;Um abração!!! E até o próximo post.

## Referências

  * <a href="https://github.com/slushjs/mock-gulp-dest" target="_blank">Ferramenta de Testes para Slush</a>
  * <a href="http://en.wikipedia.org/wiki/Stream_%28computing%29" target="_blank">Stream</a>
  * <a href="http://gulpjs.com/" target="_blank">GulpJS</a>
  * <a href="http://slushjs.github.io/#/" target="_blank">Slush</a>
  * <a href="http://slushjs.github.io/generators/#/" target="_blank">Slush Generators</a>
  * <a href="http://nodejs.org/" target="_blank">NodeJS</a>
  * <a href="https://www.npmjs.com/" target="_blank">NPMJS.ORG</a>
  * <a href="https://github.com/obetomuniz/slush-boilerplate" target="_blank">Slush Generator Boilerplate</a>
  * <a href="https://github.com/webcomponents/slush-element" target="_blank">Slush Element</a>

&nbsp;

<img class="alignleft size-medium wp-image-46783" src="http://tableless.com.br/uploads/2015/02/elvis-thanks.gif" alt="elvis-thanks" width="247" height="139" />

 [1]: https://github.com/webcomponents/slush-element