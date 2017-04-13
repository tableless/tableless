---
title: Introdução ao Meteor
author: Leo Cavalcante
type: post
date: 2015-08-13
excerpt: Uma introdução ao Meteor.
url: /introducao-ao-meteor/
categories:
  - JavaScript
  - Meteor
  - O Básico
tags:
  - meteor
---

Primeiro, se você ainda não conhece o Meteor, <a href="http://tableless.com.br/apresentando-meteor/" target="_blank">da uma lida aqui</a>.

Não sou tão bom em fazer tutorial quanto em propaganda, deve ser por isso que trabalho numa agência de publicidade e não numa escola, mas vamos ao que interessa, vamos brincar um pouco com Meteor.

Antes de mais nada, obviamente, você precisa instalar em sua máquina. Tem pra Windows, Linux e Mac, não tem erro:
  
&#8211; <a href="https://www.meteor.com/install" target="_blank">https://www.meteor.com/install</a>

Depois de instalado (poderá ser necessário reiniciar o computador em alguns casos), você vai estar apto pra executar os comandos do <a href="https://www.meteor.com/tool" target="_blank">Meteor Tool</a>. O que é isso? É uma CLI (Command Line Interface) pra você criar, rodar, instalar pacotes e tudo o mais necessário pra desenvolver aplicações com a plataforma.

Para testar, rode o comando `meteor --version`; o output é como se espera: a versão instalada do Meteor:

[<img class="alignnone size-full wp-image-50696" src="http://tableless.com.br/uploads/2015/08/meter-version.jpg" alt="meter--version" width="805" height="373" />][1]

Falando nisso, tenho que atualizar o meu. Pra quem acabou de instalar a versão vai ser a 1.1.0.3.

Então bora criar o primeiro app; e você faz isso simplesmente executado o comando `create` e passando o nome da pasta que você vai dar pro projeto.

<pre class="lang-bash">meteor create hello-meteor</pre>

O Meteor vai então criar essa pasta `hello-meteor` e vai deixa lá alguns arquivos iniciais. Aí você pensa: &#8220;lá vem uns arquivos sinistros que nunca vi na vida; coisa a mais pra aprender&#8221;, mas calma jovem, não são nada mais nada menos que um `.html`, um `.css` e um `.js`; exatamente isso, esse trio que você já conhece e tem a maior admiração e eles só estão lá pra ilustrar como o Meteor funciona, só pra te falar: &#8220;olha, é por aqui que você começa&#8221;; quem manja &#8220;dos Meteor&#8221; já sai apagando esses arquivos.

Como a gente não manja ainda, vamos usa-los pra entender como ele funciona!

[<img class="alignnone size-full wp-image-50701" src="http://tableless.com.br/uploads/2015/08/hellometeor.jpg" alt="hellometeor" width="805" height="373" />][2]

O `hello-meteor.css` não tem nada, é isso, tá lá só pra ilustrar, como falei antes, mas é lá que vai seu CSS.

O `hello-meteor.html` já tem alguma coisa, mas não é um HTML qualquer. Ele não tem a tag `<html>` e tem essa tal de `template` mais essas chaves `{{ }}`.  Primeiro é bom lembrar que a `template` não é coisa que o Meteor inventou é HTML5 e já é [recomendação da W3C](http://www.w3.org/TR/html5/scripting-1.html#the-template-element). As chaves também não são coisa nova do Meteor, quem usa [Handlebars.js](http://handlebarsjs.com/) já conhece muito bem e vai estar muito familiarizado já que o [Spacebars](https://atmospherejs.com/meteor/spacebars), a engine do Meteor, é baseada no Handlebars. &#8220;Por que eles fizeram outra template engine?&#8221; você deve estar se perguntando e isso pra ter a [reatividade no HTML](http://docs.meteor.com/#/full/livehtmltemplates) que a gente viu no post anterior.

Mas o HTML é simples, uma olhada cautelosa e você já entende o que tá acontecendo, tem a `head` com um `title`, ok; tem a `body` com um `h1`, normal e tem esse `{{> hello}}` (se você usou o mesmo nome pra pasta), isso faz exatamente o que você tá imaginando, imprime o `template name="hello"`, declarado logo abaixo, naquele espaço da `body`. Se você já tem noção de template engine isso já entrou na sua cabeça, nada diferente de Angular e Ember até aqui.

## O hello-meteor.js

Agora sim, o JavaScript, ele que faz acontecer.

A primeira coisa que a gente tem que falar no JS quando se trata do Meteor, são as Booleans: `Meteor.isClient` e `Meteor.isServer`; sim, tenho certeza que você imaginou e é pra isso mesmo pra isso que elas servem. Os arquivos `.js` no Meteor tem por natureza rodar tanto no ambiente cliente quanto no servidor, <a href="http://docs.meteor.com/#/full/structuringyourapp" target="_blank">salvo quando localizados em pastas específicas</a>, que é a parte sobre como organizar seu app em Meteor que a gente pode deixar pra outro post. Sendo assim o Meteor te da essas duas <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean" target="_blank">Booleans</a> pra você saber quando tá em um ambiente ou em outro. No `hello-meteor.js` o `if (Meteor.isClient) {` e o `if (Meteor.isServer) {` estão claros.

No `isServer` não temos muita ação, mas no `isClient` a gente nota essa global `Template`; pra cada `template` que você definir nos seus `.html`, a `Template` terá uma propriedade com o nome que você deu, no caso `hello`. E o que você pode fazer com isso? Adicionar helpers e eventos. Helpers, quem trabalha com templates já sabe, são pequenas funções que te ajudam a mover alguma lógica de apresentação que estaria no HTML pro JS, o que faz muito mais sentido e eventos são, bom, eventos, você já conhece eles, são exatamente os eventos do DOM: click, mouseover, submit etc.

O <a href="http://docs.meteor.com/#/full/eventmaps" target="_blank">padrão pra selecionar os eventos</a> é: `eventtype selector` e eles pode ser separados por vírgula. No nosso hello-meteor.js temos lá como exemplo: `'click button'` no lugar de `click` poderia ser `submit` e no lugar de `button` poderia ser qualquer seletor CSS como é na jQuery, aliás, já comentei que o Meteor vem a com jQuery por padrão e você pode executar `template.$` e retornar um jQuery Object? 😉 Pois é&#8230;

Ainda no JavaScript temos a global `Session` e é justamente pra trabalhar com sessões mesmo; no exemplo temos a chave `counter` na nossa `Session` e a cada clique do botão o handle incrementa essa chave direto na `Session`; temos uma helper de mesmo nome (`counter`) que simplesmente retorna o valor da chave na sessão e no `.html` a gente invoca essa helper com `{{counter}}`; simples, um template em HTML imprimindo o valor de uma variável do JavaScript. O que tem de super cool aí é como dissemos a reatividade, a mudança de estado ser propagada sem esforço algum, você pode ver que não tem nenhum código pra ouvir quando a `counter` é alterada e alterar no HTML, o Meteor te da isso out-of-the-box.

Toda chave na `Session` é uma <a href="http://docs.meteor.com/#/full/reactivevar" target="_blank">ReactiveVar</a> e vai ser pro-ativa o suficiente pra ouvir alterações em si e propaga-las até a View/HTML/Blaze/Spacebars.

Quer ver isso tudo funcionando? Só executar `meteor` dentro da pasta do seu app.

[<img class="alignnone size-full wp-image-50707" src="http://tableless.com.br/uploads/2015/08/runnnign.jpg" alt="running" width="805" height="373" />][3]

Pronto, app rodando, só entrar em http://localhost:3000/ no seu navegador preferido e clicar à vontade.

Quer saber onde entra o MongoDB nessa história? Que ver o Meteor com Angular ou React? Comenta aí&#8230;

Abs!

 [1]: http://tableless.com.br/uploads/2015/08/meter-version.jpg
 [2]: http://tableless.com.br/uploads/2015/08/hellometeor.jpg
 [3]: http://tableless.com.br/uploads/2015/08/runnnign.jpg