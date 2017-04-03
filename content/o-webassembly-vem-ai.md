---
title: WebAssembly – a web compilada
author: Marco Antônio
type: post
date: 2015-06-24
excerpt: Um novo formato binário para compilar aplicações para web.
url: /o-webassembly-vem-ai/
categories:
  - Browsers
  - Geral
  - Tecnologia e Tendências
tags:
  - WebAssembly

---
Como não esperar algo bom vindo de uma parceria entre <a href="https://twitter.com/jfbastien/status/611201861245399041" target="_blank">Google</a>, <a href="http://blogs.msdn.com/b/mikeholman/archive/2015/06/17/working-on-the-future-of-compile-to-web-applications.aspx" target="_blank">Microsoft</a>, <a href="https://blog.mozilla.org/luke/2015/06/17/webassembly/" target="_blank">Mozilla</a> e <a href="https://bugs.webkit.org/show_bug.cgi?id=146064" target="_blank">WebKit Project</a>?

A novidade dessa vez é o <a href="https://github.com/WebAssembly" target="_blank">WebAssembly</a>, um novo formato binário para compilar aplicações para a Web.

Por bem ou por mal, o JavaScript se tornou um padrão para a aplicações web. Nos últimos anos temos visto mais e mais esforços para que o desenvolvedor crie seu código em uma outra linguagem e &#8220;compile&#8221; para arquivos JavaScript. Outros projetos buscar resolver as limitações do JavaScript, adicionar novas funcionalidades ou mesmo aumentar sua velocidade. Agora, alguns desses projetos serão juntados para criar o pretensioso WebAssembly, que visa se tornar o novo padrão nativo para web.

### O que é esse tal de WebAssembly?

Basicamente, é um novo formato vai permitir que os desenvolvedores compilem seus códigos para a web. Atualmente o projeto está focado em C/C++, mas pretende abranger outras linguagens.

O time do WebAssembly optou por usar formato binário porque, desta forma, a aplicação pode ser comprimidas ainda mais que os arquivos de texto em JavaScript e também porque é muito mais rápido para a engine do browser decodificar os arquivos binários do que analisar/executar códigos JavaScript-based (23x mais rápido no protótipo atual comparado ao <a href="http://asmjs.org/" target="_blank">asm.js</a> da Mozilla).

Como uma primeira etapa do projeto, o WebAssembly vai ofertar as mesmas funcionalidades do asm.js. O WebAssembly Team pretende também lançar também o então chamado <a href="https://remysharp.com/2010/10/08/what-is-a-polyfill" target="_blank">polyfill library</a> que irá converter os códigos WebAssembly em arquivos JavaScript para que possa ser executado em qualquer browser, mesmo que não haja suporte nativo ao novo formato. Com o decorrer do projeto, serão adicionadas novas funcionalidades, ferramentas e suporte a outras linguagens, além de um suporte nativo a WebAssembly nas futuras versões dos principais navegadores do mundo.

A equipe afirma que o objetivo não é substituir o JavaScript, mas permitir que mais linguagens sejam compiladas para web. De fato, há a possibilidade de usar essas duas linguagens lado a lado, partes das aplicações podem ser feitas com módulos do WebAssemply (Animações, visualizações, compressões, etc) enquanto a interface é programada em JavaScript, por exemplo.

Esse novo formato poderá abrir uma nova gama de possibilidades, permitindo criar aplicações mais rápidas e leves, portanto é um projeto que definitivamente vale a pena acompanhar nos meses e anos seguintes.

Fonte: [Techcrunch][1]

 [1]: http://techcrunch.com/2015/06/17/google-microsoft-mozilla-and-others-team-up-to-launch-webassembly-a-new-binary-format-for-the-web/