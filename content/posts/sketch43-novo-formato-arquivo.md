---
categories:
  - Artigos
  - Design
excerpt: Algumas informações sobre o novo formato de arquivo do Sketch 43
image: http://i.imgur.com/oU9aar0.jpg
type: post
author: Diego Eis
date: 2017-04-16T09:23:34-03:00
title: O novo formato de arquivo do Sketch 43
---

Depois de toda a polêmica causada pelo [último artigo](https://tableless.com.br/carreira-de-front-end-vai-morrer/), decidi fazer um acompanhamento dos fatos sempre que uma novidade aparecer, que nos aproxime ou nos distancie da extinção do trabalho do front-end como conhecemos hoje.

Esse não é um artigo técnico nem nada do tipo, só um apanhado de informações na interno sobre o novo formato de arquivo do Sketch, nada de outro mundo. Mas estou preparando um novo artigo para abordar o que estamos chamando por aí afora de CaaS: Code as a Service. Fica para um próximo artigo.

Mas como era esperado, saiu a versão 43 do Sketch. A principal mudança nessa versão é o novo formato de arquivo, baseado em JSON. Esse novo formato é um marco importante. Por causa desse novo formato, a galera tem ficado animada por conta das possibilidades de automatizações tanto pelo lado do código quanto pelo design.

No Sketch 42, os arquivos eram baseados em formato binário. Formato binário não são legíveis para seres humanos. O código é fechado. Isso mudou no Sketch 43, que introduziu um novo formato de arquivo baseado em JSON. Como você está cansado de saber, JSON é um formato muito simples de texto para estruturação de dados, fácil de ler e entender por seres humanos e para as máquinas é muito simples de interpretar e gerar. Como ser humano, você consegue escrever facilmente a estrutura de dados manualmente usando JSON por causa do seu formato baseado nos objetos literais do JavaScript e tem uma sintaxe muito enxuta formada por duas partes principais: chave e valor.

O que isso significa para os designers? Nada. Eles não vão criar seus designs escrevendo JSON, o que seria muita estupidez. Mas o fato de que todo o design feito no Sketch é traduzido automaticamente para um formato aberto, com todos os detalhes daquele layout é incrível. Arquivos são abstrações, mas nem por isso os designers mudarão a forma com que interagem com o Sketch.

<blockquote class="twitter-tweet" data-lang="en"><p lang="en" dir="ltr">Check it out. Now (9.1 or 9.2) <a href="https://twitter.com/gitlab">@gitlab</a> will be rendering <a href="https://twitter.com/sketchapp">@sketchapp</a> 43 files. <a href="https://twitter.com/rboudinot">@rboudinot</a>, <a href="https://twitter.com/iamphill">@iamphill</a> and I. More advance features to come. <a href="https://t.co/ZzOHVzIiHd">pic.twitter.com/ZzOHVzIiHd</a></p>&mdash; Jacob Schatz (@jakecodes) <a href="https://twitter.com/jakecodes/status/847536958750556161">March 30, 2017</a></blockquote>
<script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

Mas o formato aberto do Sketch só deixa a tarefa de automatizar os layouts feitos Sketch para HTML/CSS/JS mais perto. Uma das grandes qualidades do Sketch, é que ele valoriza os plugins. Eles sabem que existem pessoas inteligentes nesse mundão afora que podem melhorar ainda mais seu produto fazendo plugins que facilitam algumas tarefas do dia a dia dos designers. Muito por isso eles tem uma [documentação bem legal para desenvolvedores](http://developer.sketchapp.com/reference/api/) que querem entender como é possível interagir com o programa. A [API JavaScript para trabalhar com Sketch está no GitHub](https://github.com/BohemianCoding/SketchAPI).

![Estrutura de arquivos do Sketch](http://i.imgur.com/p3ostqh.png)

Os novos formatos de arquivos do Sketch são basicamente um arquivo ZIP que guardam todos os assets necessários para que o arquivo funcione.

![API JavaScript para construir plugins do Sketch](http://i.imgur.com/CHzCjA8.png)

Faça o teste aí com qualquer arquivo do Sketch 43: renomeie para **.zip** e descompacte o arquivo.

Mesmo assim, ainda não vai ser possível versionar decentemente arquivos Sketch. Embora tudo aí seja human-readable, você não vai versionar o conteúdo dos arquivos Sketch, mas o arquivo fechado **.sketch**.

> Translating a visual design to CSS/HTML is now a mundane task of the past. [Andree @blended.io](https://uxdesign.cc/design-is-code-code-is-design-b941c14f3fd8)

Alguns mitos que a galera tem falado por aí e várias pessoas já desmentiram:

1. Designers não serão obrigados a aprenderem GIT, apenas se quiserem... Mesmo porque já há programas com o [Abstract](https://www.abstractapp.com) que já os ajudam nesse trabalho de versionamento;
2. Designers não precisarão aprender a codificar HTML/CSS/JS para fazer seus layouts. Longe disso. Embora os layouts sejam baseados em JSON, ninguém vai ficar fazendo layout escrevendo JSON em vez de usar a interface do Sketch;
3. Os plugins que são usados para exportar designs ficarão obsoletos, como o Zeplin, por exemplo. Pelo contrário: com uma API muito bem documentada, pode ser que várias outras ferramentas dessas surjam;

Já existem algumas ferramentas surgindo por aí, como é o caso do [Sketch Web Viewer](https://github.com/AnimaApp/sketch-web-viewer).

Existem várias pessoas apostando que um monte de plugins e outras ferramentas de automatizações surjam do nada por causa desse novo formato do Sketch. Os caras estão realmente animados com todas essas possibilidades:

**However, we expect in influx of tools that supercharge designers workflow and automate mundane, error-prone, human annoyable, tasks.**
**It might take some time, but automation is revolutionizing the world and since the new Sketch file format is digestible by all, the potential for the integrations with all sorts of automation software is limitless.**

Além disso, designers estão aprendendo algumas coisas com os desenvolvedores, por exemplo, [lidar bem com componentes em seus Designs](https://medium.com/goabstract/a-component-based-workflow-for-sketch-6d3556b18d4c).


### Para ler mais:

- [With Sketch 43, Design IS Code & Code IS Design](https://uxdesign.cc/design-is-code-code-is-design-b941c14f3fd8)
- [View and inspect Sketch 43 files in browser](https://github.com/AnimaApp/sketch-web-viewer)
- [Abstract](https://www.abstractapp.com/)
- [Sketch 43 is coming to town with a new game. An open file format!](https://medium.com/sketch-app-sources/sketch-43-is-coming-to-town-with-a-new-game-an-open-file-format-ae62e7e7c223)
- [Sketch API](http://developer.sketchapp.com/reference/api/)
- [Sketch 43: A brief tour of fact vs folklore](https://blog.prototypr.io/sketch-43-a-brief-tour-of-fact-and-folklore-7772ca7f6e61)
- [New file format in Sketch 43](http://sketchplugins.com/d/87-new-file-format-in-sketch-43)
