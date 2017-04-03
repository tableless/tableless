---
title: 'Apresentando: Meteor!'
author: Leo Cavalcante
type: post
date: 2015-08-06
url: /apresentando-meteor/
categories:
  - Tecnologia e Tendências
tags:
  - meteor

---
Fiquei impressionado ao ver que não há nenhum artigo sobre o Meteor no Tableless ainda, ou a busca não tá funcionando muito bem. Por que? Porque é uma plataforma simplesmente fod@! Não conheço nada tão produtivo e simples de usar.

<a href="https://www.meteor.com/" target="_blank">Meteor</a> é uma plataforma open-source pra desenvolver aplicativos pra web e mobile.

Ela é fullstack, te entrega uma solução completa desde o banco de dados até o front-end e essa solução é toda em JavaScript. Similar ao <a href="https://en.wikipedia.org/wiki/MEAN_(software_bundle)" target="_blank">MEAN</a> (que aliás é outra plataforma bem legal que não tem artigo no Tableless) ela usa <a href="https://nodejs.org/" target="_blank">Node.js</a> e <a href="https://www.mongodb.org/" target="_blank">MongoDB</a> só que no lugar do <a href="http://expressjs.com/" target="_blank">Express</a> usa um <a href="https://www.meteor.com/webapp" target="_blank">framework próprio pra HTTP</a> e no lugar do <a href="https://angularjs.org/" target="_blank">AngularJS</a> usa uma view engine própria também chamada <a href="https://www.meteor.com/blaze" target="_blank">Blaze</a>, mas não se limita aí, se você quiser poder usar <a href="https://angularjs.org/" target="_blank">AngularJS</a> ou até mesmo <a href="http://facebook.github.io/react/" target="_blank">React</a> pra trabalhar com seus componentes.

Um dos lemas da <a href="http://docs.meteor.com/#/full/sevenprinciples" target="_blank">filosofia do Meteor</a> é _Simplicity Equals Productivity_ (Simplicidade é igual a produtividade); cara, nada de _boilerplates_ complexos, extensões sinistras, programas estranhos, arquivos de configuração&#8230; nada disso. A coisa tem que ser simples, sendo simples você se torna mais produtivo. O Meteor recebeu nada mais, nada menos que <a href="http://info.meteor.com/blog/meteors-new-112-million-development-budget" target="_blank">11,2 MILHÕES de DÓLARES em 2012</a> como aporte de uma Venture Capital que decidiu apostar na plataforma.

A parada é tão simples que você não precisa desses arquivos chatos de configuração do Gulp, Grunt, Webpack etc que você tem pro LESS, SASS, JSX, CoffeeScript&#8230; Ele se baseia na extensão do arquivo, se houve um aquivo `.less` ele compila pra CSS se tiver um arquivo `.coffee` ele compila pra JavaScript, se tiver um arquivo `.jsx` ele já compila pra JavaScript, se você tiver um arquivo `.es6.js` ele já compila pra ES5 etc; sem você precisar ficar &#8220;falando o óbvio&#8221;, é tudo automático. Até mesmo arquivos `.markdown` pra HTML.

Outra _feature_ essencial do Meteor é a <a href="http://docs.meteor.com/#/full/reactivity" target="_blank">Reatividade (Reactivity)</a>; WTF? <a href="https://en.wikipedia.org/wiki/Reactive_programming" target="_blank">Programação reativa</a> é basicamente: sobre o fluxo dos dados e a propagação da mudança de estado. Se você tiver uma variável chamada `foo` com valor `"bar"` e de qualquer lugar da Internet essa variável mudar pra `"qux"`, todas abas abertas ou aplicativos que você fez vão identificar essa alteração e <a href="http://docs.meteor.com/#/full/livehtmltemplates" target="_blank">mudar no HTML</a>, sem você precisar programar nada pra isso! O Meteor entende alterações ao no nível da camada do MongoDB fazendo essa reatividade ser até persistente. Desenvolver _chats_ ou qualquer tipo de aplicação _multi-client_ é extremamente simples.

Além de tudo isso, a plataforma Meteor ainda te da um <a href="http://docs.meteor.com/#/full/deploying" target="_blank">serviço de hospedagem grátis</a>. Seu projeto em Meteor pode rodar em qualquer servidor que rode MongoDB e Node.js, mas a gente sempre passar por aquele estágio de prototipagem da aplicação ou você fez desenvolveu uma ideia muito legal e quer mostrar pra outras pessoas; pois é, o Meteor tem um nuvem pública gratuita pra você hospedar suas aplicações de baixo tráfego e até 200 emails por dia.

Cara, na boa&#8230; Fod@!

Vou ficar de olho na popularidade desse post e se for o caso, faço um outro post mais estilo tutorial pra iniciar a galera no Meteor.

Abraço!

**EDIT
  
** Galera, tá no ar a introdução pra você começar no Meteor, confere lá:
  
[tableless.com.br/introducao-ao-meteor][1]

 [1]: http://tableless.com.br/introducao-ao-meteor/