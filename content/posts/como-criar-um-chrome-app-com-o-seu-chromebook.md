---
title: Como criar um Chrome App com o seu Chromebook
author: Roger Albino
type: post
date: 2015-06-01
excerpt: Criando seu primeiro App para Chrome direto do seu Chromebook!
url: /como-criar-um-chrome-app-com-o-seu-chromebook/
categories:
  - Browsers
  - Editores
  - HTML
  - JavaScript
  - O Básico
tags:
  - chrome
  - chrome apps
  - chromebook
  - dart
  - js

---
## O que é um chrome app

A ideia de [chrome app][1]&nbsp;é trazer ferramentas que você usa no browser para o seu computador. Como se fosse uma extensão do browser. &nbsp;A&nbsp;instalação/desinstalação destes apps é fácil, rápida e sem dor de cabeça, além de contar com aplicativos que podem funcionar off-line.

## Por que criar um chrome APP?

A grande vantagem, é que aplicativos nativos para Chrome&nbsp;OS são feitos com tecnologias que já conhecemos como HTML, CSS e JS. Podendo também utilizar a linguagem [dart][2]&nbsp;que me parece bem interessante.

## Equipamento necessário

Encontrei vários editores de texto para o Chromebook, mas me familiarizei com o [Caret][3]. Gosto dele, pois além de informar erros, ele dá dicas de otimizações, e avisa se você esquecer de deixar callbacks para outros navegadores. Isso evita uma grande dor de cabeça. Fique à vontade para escolher o editor que mais te agrade.

## Começar pelo inicio

Para iniciar Você vai precisar de um arquivo **manifest.json** para informar detalhes sobre a aplicação como titulo, descrição e icones. E de um arquivo JavaScript para criar a tela responsável pela interação com o APP conhecido como **background.js**.

Crie um diretório para o seu projeto. Na raiz dele vamos criar um arquivo chamado **manifest.json**. A sintaxe para quem não conhece é composta por **&#8220;chave&#8221;: &#8220;valor&#8221;**. É &#8220;tipo&#8221; um objeto JavaScript (na verdade ele é). Nele informamos nome, descrição, versão da aplicação, versão do arquivo manifest, o script de background e os ícones que serão usados no APP.

<pre class="lang-js">{
  "name": "Nome do meu APP",
  "description": "Descrição do meu APP",
  "version": "0.1",
  "manifest_version": 2,
  "app": {
    "background": {
      "scripts": ["background.js"]
    }
  },
  "icons": { "16": "icone-16.png", "128": "icone-128.png" }
}

</pre>

Os icones são opcionais. Contudo, se você não tiver ícones para testar agora, tire essa linha. Na linha onde setamos &#8220;app&#8221;, setamos também o arquivo de background que é muito importante para nós.

## Criando o script de background

Após setar o script background.js, precisamos cria-lo. Aqui, por enquanto não tem segredo. Criamos o o arquivo js como o abaixo:

<pre class="lang-js">chrome.app.runtime.onLaunched.addListener(function() {
  chrome.app.window.create('index.html', {
    'bounds': {
      'width': 400,
      'height': 500
    }
  });
});</pre>

Na primeira linha, criamos um listener para ouvir nossos eventos de onLaunched, ou seja quando iniciarmos nossa aplicação. dentro dele criamos a nossa primeira tela, a função `chrome.app.window.create` cria a nossa view index.html com o tamanho de 400&#215;500.

## Criando a view

É mais simples do que vocês estão pensando. Criamos um arquivo index.html que será chamado pelo background.js quando executarmos nosso app.

<pre class="lang-html">&lt;!DOCTYPE html&gt;
&lt;html&gt;
  &lt;head&gt;
  &lt;/head&gt;
  &lt;body&gt;
    &lt;h1&gt;Minha primeira aplicação&lt;/h1&gt;
  &lt;/body&gt;
&lt;/html&gt;

</pre>

## Como testar meu Chrome App?

Acesse o endereço pelo seu chrome **chrome://flags**. Procure por &#8220;**Experimental Extension APIs**&#8220;, use &#8220;ctrl+f&#8221; ou &#8220;command+f&#8221; para acelerar o processo, e clique no link &#8220;Enable&#8221;. Caso esteja com o chrome em pt-br procure por &#8220;**APIs de extensões experimentais&#8221;** e clique no link ativar.

Após ativarmos as extensões experimentais, podemos agora finalmente carregar nossa aplicação para teste.
  
_Vá no menu do chrome>> Mais ferramentas >> Extensões&#8221;_ Ou acesse o endereço **chrome://extensions/** acho mais fácil. Verifique se o modo desenvolvedor está ativado.

Clique em &#8220;**carregar extensão expandida**&#8221;&nbsp;, escolha a pasta do seu projeto. Agora é só você procurar na sua lista de app do seu chrome, e sua aplicação está lá.

## Tornando as coisas mais simples com o&nbsp;Chrome Dev Editor

<ul class="postList">
  <li class="li">
    Primeiro vamos instalar&nbsp;o Chrome Dev Editor acessando <a class="markup--anchor markup--li-anchor" href="https://chrome.google.com/webstore/detail/chrome-dev-editor-develop/pnoffddplpippgcfjdhbmhkofpnaalpg">esse link</a>.
  </li>
  <li class="li">
    Acessamos o menu principal, e clicamos em <em class="markup--em markup--li-em">New Project</em>
  </li>
  <li class="li">
    Digitamos o nome da aplicação, e escolhemos o <em class="markup--em markup--li-em">Project Type</em>
  </li>
  <li class="li">
    Usamos o atalho <em class="markup--em markup--li-em">ctrl+r </em>para testar a aplicação
  </li>
</ul>

Nessa IDE, temos várias opções de _Project Type_, mas o que importa para nós agora são os **Chrome Apps**. Podemos iniciar um projeto usando [Dart][2], ou [JavaScript][4], também iniciar um projeto usando [Polymer][5] e todas as facilidades dele. A Facilidade, é que os arquivos que expliquei anteriormente são criados automaticamente, e a instalação e teste também são automáticos, fazemos tudo pela IDE. Tem jeito mais fácil&nbsp;?

É claro que isso é só o básico sobre criação de chrome Apps, mas já dá pra brincar um pouquinho. Abraço, e bons estudos. ☺

 [1]: https://www.google.com/chrome/webstore/apps-create.html
 [2]: http://pt.wikipedia.org/wiki/Dart_%28linguagem_de_programa%C3%A7%C3%A3o%29
 [3]: http://thomaswilburn.net/caret/
 [4]: http://pt.wikipedia.org/wiki/JavaScript
 [5]: https://www.polymer-project.org/0.5/