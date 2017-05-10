---
title: 3 ferramentas para criar e gerenciar projetos web
author: Davi Ferreira
type: post
date: 2013-02-05
excerpt: 'Cada vez mais um número maior de ferramentas surge para auxiliar  e agilizar o desenvolvimento web. Conheça alguns frameworks que têm como objetivo controlar e gerenciar o uso de bibliotecas, pré-processadores e utilitários em sites e aplicações web.'
url: /3-ferramentas-para-criar-e-gerenciar-projetos-web/
dsq_thread_id: 1066395256
categories:
  - Código
  - HTML
  - JavaScript

---
Já foi o tempo que nossas aplicações web e sites eram compostos apenas por arquivos HTML e um ou outro CSS e JS. Hoje temos pré-processadores CSS, minificadores, [ferramentas de validação de JavaScript][1], grids, boilerplates, bootstraps e até mesmo JavaScript no servidor. 

Há também uma maior quantidade de arquivos e bibliotecas externas. Os arquivos CSS foram modularizados e JavaScript passou a ser (muito) mais aceita, ganhando ainda uma versão mais &#8220;amigável&#8221; na linguagem [CoffeeScript][2]. 

Neste artigo, você confere algumas opções para criar rapidamente uma aplicação inicial já com uma estrutura pré-definida e com as principais bibliotecas e ferramentas do mercado. 

## Yeoman

[yeoman.io][3]

Desenvolvido com a ajuda de popstars como Paul Irish e Addy Osmani, o framework Yeoman consiste em um conjunto de ferramentas voltadas para criar rapidamente um novo projeto web e gerenciá-lo durante o processo. Seus comandos são baseados no utilitário Grunt e executam tarefas como minificação, lint e otimização de imagens. 

Um projeto criado via Yeoman, utilizando o comando _yeoman init_, vem com algumas habilidades especiais. Você pode, por exemplo, escrever código em CoffeeScript e o Yeoman se encarrega, em background, de transformá-lo em JavaScript. O mesmo acontece para CSS escrito com Sass/Compass. 

O comando _yeoman server_ levanta um servidor local e monitora qualquer alteração nos arquivos do projeto, atualizando a página no navegador automaticamente. 

Outro comando importante é o _yeoman build_, que gera uma versão pronta para produção, com todos os scripts e estilos validados e devidamente minificados. O Yeoman também otimiza todas as imagens utilizando bibliotecas especiais. O comando build também procura por bundles JavaScript e CSS e concatena seus arquivos. 

## Roots

[roots.cx][4]

Uma boa alternativa ao Yeoman é o Roots, framework que também concentra um set de ferramentas e boas práticas para agilizar a criação e manutenção de projetos web. 

O set padrão do Roots acompanha a template engine Jade, o pré-processador de CSS Stylus e a linguagem CoffeeScript. 

Os projetos são criados através do comando _roots new_. O Roots também oferece um comando para live reload, _roots watch_, monitorando qualquer alteração e atualizando o site no navegador através de um servidor local. 

É possível também utilizar diversos plugins para diferentes bibliotecas e utilitários (Sass, ejs etc.). 

Pacotes podem ser instalados através do comando _roots install_ . Tanto o Roots como o Yeoman utilizam o gerenciador de pacotes Bower, portanto é possível instalar qualquer um dos pacotes listados no repositório [sindresorhus.com/bower-components][5]. 

## Brunch

[brunch.io][6]

As diretrizes do projeto Brunch giram em torno de dois conceitos principais: plugins e esqueletos. 

Os plugins envolvem linguagens (JavaScript, CoffeeScript, LiveScript etc.), templates (Handlebars.js, Jade, Mustache etc.), pré-processadores de CSS (Sass, Stylus, LESS), validadores (JSLint e CoffeeLint) e minificadores (uglify.js e clean-css). 

Já os esqueletos definem o framework JavaScript e o set padrão de ferramentas. O esqueleto padrão cria um projeto utilizando o HTML5 Boilerplate, Chaplin com Backbone.js, CoffeeScript, Stylus e Handlebars. Outros esqueletos incluem um set com JavaScript puro, Sass e Twitter Bootstrap; um com Backbone e CoffeeScript; e até mesmo um com [AngularJS][7]. 

Assim como o Yeoman, o Brunch também utiliza a ferramenta Grunt para gerenciar e executar suas tarefas. 

`<br />`

Essa foi uma apresentação inicial e, futuramente, pretendo escrever um artigo específico sobre cada um dos projetos listados aqui. E vocês, utilizam alguma outra alternativa? Deixem suas mensagens nos comentários!

 [1]: http://tableless.com.br/qualidade-codigo-javascript/ "http://tableless.com.br/qualidade-codigo-javascript/"
 [2]: http://tableless.com.br/javascript-com-cafe/ "http://tableless.com.br/javascript-com-cafe/"
 [3]: http://yeoman.io "http://yeoman.io"
 [4]: http://roots.cx "http://roots.cx"
 [5]: http://sindresorhus.com/bower-components/ "http://sindresorhus.com/bower-components/"
 [6]: http://brunch.io/ "http://brunch.io/"
 [7]: http://tableless.com.br/criando-uma-aplicacao-simples-com-angularjs/ "http://tableless.com.br/criando-uma-aplicacao-simples-com-angularjs/"