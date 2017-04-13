---
title: Conheça o debugger.html – Depurador de JS da Mozilla
author: Diego Eis
type: post
date: 2016-09-14
url: /conheca-o-debugger-html-depurador-de-js-da-mozilla/
titulo_personalizado:
  - 'Conheça o <strong>debugger.html</strong>'
categories:
  - Destaques

---
**[debugger.html][1]** é um depurador de JavaScript moderna da Mozilla, construído como um
  
aplicação web usando React e Redux. Este projecto foi iniciado em um esforço para substituir o depurador atual dentro do Firefox Developer Tools.

O debugger.html é uma aplicação que faz uma conexão WebSocket para um alvo que será debugável. A aplicação então interpreta dados e envia comandos para o motor JS para gerenciar o ambiente de debug; por exemplo, criando um breakpoint pausando a execução do motor JS em um determinado parte do código.

![][2]

O [debugger.html][1] pode conectar-se e depurar também com Chrome e Node, ambos de forma experimental por enquanto. O depurador se conecta ao Firefox usando o Mozilla [Remote Debug Protocol][3] (RDP) e se comunica com o Node e o Chrome usando [RDP do Chrome][4].

O projeto debugger.html está hospedado em [GitHub][1] e usa frameworks modernos do mercado e toolchains, tornando-se prontamente disponível para um grande público de desenvolvedores.

### A interface

A interface é dividida em três partes: o painel que mostra o código-fonte, o painel de editor e uma barra lateral direita.

O painel do código fonte exibe uma visualização do source que está sendo depurado.

O painel do editor mostra uma árvore dos arquivos do projeto. Você também consegue abrir vários arquivos em abas para melhorar a depuração de vários arquivos de uma vez.

Já a barra da direita, mostra a listagem de breakpoints, pausando o debugger, ele mostra chamadas atuais e também o escopo das funções. Ainda nesse painel, manipular um pouco seu código, pausando, executando, pulando funções e etc.

![][5]

Lá no GitHub eles tem as instruções de como você pode usar isso HOJE. Mas eles já colocaram na versão [Nighly Build][6]. Queria ter trazido mais informações de uso, eu até clonei e rodei o `npm install`, mas está rodando até agora! 😉

<img src="http://tableless.com.br/uploads/2016/09/Screen-Shot-2016-09-14-at-2.27.50-PM.png" alt="Screen Shot 2016-09-14 at 2.27.50 PM" width="1262" height="725" class="aligncenter size-full wp-image-55942" />

 [1]: https://github.com/devtools-html/debugger.html/
 [2]: https://cloud.githubusercontent.com/assets/2134/16933811/babb4eec-4d05-11e6-8c7e-f133e54b756f.png
 [3]: https://wiki.mozilla.org/Remote_Debugging_Protocol
 [4]: https://developer.chrome.com/devtools/docs/debugger-protocol
 [5]: https://2r4s9p1yi1fa2jd7j43zph8r-wpengine.netdna-ssl.com/files/2016/09/debug.gif
 [6]: https://nightly.mozilla.org