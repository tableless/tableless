---
title: Aplicativos Desktop com NW.js – Node Webkit – Introdução
author: João A. Zonta
type: post
date: 2016-07-14
excerpt: Este é o primeiro artigo de uma série sobre aplicações desktop usando tecnologias web. (HTML, CSS, Javascript e WebGL)
url: /aplicativos-desktop-com-nw-js-node-webkit-introducao/
categories:
  - Código
  - CSS
  - HTML
  - JavaScript
tags:
  - app
  - CSS
  - html5
  - JavaScript
  - NodeJS
  - nwjs
  - webgl

---
# _**Este é o primeiro artigo de uma série que vou escrever sobre aplicações desktop usando tecnologias web. (HTML, CSS, Javascript e WebGL)**_

O **NW.js** é uma aplicação em tempo de execução baseado em Chromium e Node.js, com ele é possível desenvolver aplicativos nativos para Windows, Linux e Mac, usando tecnologias web e usufruindo dos pacotes do Node.js.

Para ter uma ideia do que é possível fazer, visite este link e veja alguns aplicativos desenvolvidos com NW.js -> <a href="http://tangiblejs.com/posts/nw-js-and-electron-compared-2016-edition" target="_blank">http://tangiblejs.com/posts/nw-js-and-electron-compared-2016-edition</a>

O **NW.js** é um projeto criado pela Intel. Outro projeto muito bom e conhecido para desenvolver aplicativos desktop usando tecnologias web é o **Electron**, criado pelo GitHub. Segue um link comparativo entre os dois -> <a href="http://tangiblejs.com/posts/nw-js-and-electron-compared-2016-edition" target="_blank">http://tangiblejs.com/posts/nw-js-and-electron-compared-2016-edition</a>

Nessa série de artigos, vou explicar como criar um aplicativo desktop, com ícone personalizado e empacotado em um único executável. No último artigo, vou explicar como fazer uma integração com base de dados local, em tempo real e sem a necessidade de abrir portas ou fazer configurações de _firewall_.

A versão mais atual do NW.js no momento em que eu escrevo este artigo é a **_nwjs-v0.15.3_**, é esta que estou usando. Além disso, estou usando Windows como sistema operacional.

Vamos começar com um &#8220;Olá Mundo&#8221;, porém, vou explicar alguns recursos de &#8220;Window&#8221; e as configurações para iniciar o projeto.

Primeiro faça o download do NW.js no site <http://nwjs.io/> &#8211; Para desenvolvimento, baixe a versão SDK &#8211; descompacte os arquivos em uma pasta que seja fácil para acessar pelo _prompt_ de comando &#8211; eu costumo descompactar na pasta _c:\nwjs\_

Para uma aplicação básica funcionar, precisamos apenas de dois arquivos, o _package.json_, que contém as configurações da nossa aplicação e o _index.html_, que contém o código da nossa aplicação. Depois vamos adicionar arquivos .js e .css. Neste primeiro artigo, vamos brincar um pouco com o package.json.

Crie um novo arquivo index.html &#8211; vamos adicionar uma estrutura básica de HTML:

<pre class="lang-html">&lt;!DOCTYPE html&gt;
&lt;html lang="pt-br"&gt;
&lt;head&gt;
&lt;meta charset="utf-8"/&gt;
&lt;title&gt;Meu Primeiro Projeto&lt;/title&gt;
&lt;/head&gt;
&lt;body&gt;
&lt;h1&gt;Olá Mundo.&lt;/h1&gt;
&lt;/body&gt;
&lt;/html&gt;
</pre>

Crie um novo arquivo package.json, com o código abaixo e salve na mesma pasta do HTML:

<pre>{
 "name": "ola-mundo",
 "main": "index.html"
}</pre>

Somente com essas informações no package.json você já pode testar seu &#8220;Olá Mundo&#8221;. &#8220;_name_&#8221; é o nome do projeto, e &#8220;_main_&#8221; é o arquivo inicial da aplicação, sua &#8220;página inicial&#8221;.

Para executar nosso aplicativo, abra o _prompt_ de comando e vá até a pasta do seu projeto, no meu caso &#8220;c:\projetos\olamundo&#8221;, depois vamos executar o comando para o NW.js executar nosso projeto. Como estou usando o Windows, vou apontar para o nw.exe. No Linux ou no Mac é diferente, você pode olhar na documentação. Então nosso comando ficaria assim:

<pre>cd /path/to/your/app
/path/to/nw .</pre>

No meu caso:

<pre>cd c:\projetos\olamundo
c:\nwjs\nw.exe .</pre>

<img class="alignnone wp-image-54795 size-full" src="http://tableless.com.br/uploads/2016/06/olamundo01.png" alt="Tela Olá Mundo NW.js" width="966" height="535" />

## Mais sobre o package.json

O nosso package.json está muito simples, tem apenas um nome e o caminho do arquivo index. Vou explicar um pouco sobre as configurações &#8220;window&#8221;, que servem para controlar os botões de fechar, minimizar, informar os tamanhos mínimos e máximos, se a janela pode ser dimensionada e outras configurações.

Abra o seu arquivo package.json e deixe ele como o exemplo abaixo:

<pre>{
 "name": "ola-mundo",
 "main": "index.html",
 "version": "1.0",
 "description": "Olá Mundo",
 "window": {
 "width": 400,
 "height": 300,
 "resizable": false,
 "frame": true,
 "title": "Olá Mundo",
 "show": true,
 "fullscreen": false,
 "kiosk": false,
 "icon": "icon.png"
 }
}
</pre>

Execute novamente o aplicativo e veja como ficou. Abaixo, explico cada uma das configurações usadas.

<pre>name -&gt; Nome do projeto
main -&gt; Arquivo inicial
version -&gt; Versão
description -&gt; Descrição do projeto
window:
 width -&gt; Largura da janela
 height -&gt; Altura da janela
 resizable -&gt; Se o tamanho da janela pode ser alterado ou não
 frame -&gt; Quadro que envolve a aplicação com o título, ícone, botões de fechar, minimizar e maximizar
 title -&gt; Título da janela
 show -&gt; Se estiver como false você executa o aplicativo e ele fica em modo silencioso, 
  está rodando, mas não aparece. Fica apenas como um processo no Windows.
 fullscreen -&gt; executa em tela cheia
 kiosk -&gt; Executa em tela cheia e dificulta a saída da aplicação, normalmente é usado para exposições.
 icon -&gt; Caminho para o ícone (deve estar na mesma pasta do projeto)</pre>

Você pode ver mais opções e detalhes na documentação: <a href="http://docs.nwjs.io/en/latest/References/Manifest%20Format/#window-subfields" target="_blank">http://docs.nwjs.io/en/latest/References/Manifest%20Format/#window-subfields</a>

Repositório com os fontes do primeiro artigo: <a href="https://bitbucket.org/jzonta/artigos_nwjs" target="_blank">https://bitbucket.org/jzonta/artigos_nwjs</a>

## Próximos artigos &#8211; Aplicativos Desktop com NW.js &#8211; Node Webkit

<del><strong>1º &#8211; Introdução</strong></del>
  
_Uma breve introdução, fazer um &#8220;Olá Mundo&#8221; e aprender um pouco sobre as configurações iniciais._

**2º &#8211; Menus**
  
_Fazer um menu nativo da aplicação e um menu HTML, capturar as ações do botão de minimizar e alterar para minimizar o aplicativo para o System Try (Aqueles ícones pequenos ao lado do relógio) e vamos adicionar menu de opções no System Try._

**3º &#8211; Pacotes Node e Persistência de dados**
  
_Vamos aprender como usar os pacotes do Node.js, vamos instalar um pacote para persistir informações em um banco de dados MySql e também em um arquivo local._

**4º &#8211; Preparando para produção**
  
_Como empacotar sua aplicação em um executável e adicionar um ícone para o Windows._

**5º &#8211; Integração web com base de dados local**
  
Como fazer uma integração de uma aplicação web com um banco de dados local, através de uma api REST, sem a necessidade de abertura de portas ou configurações de _firewall_.

Poste suas dúvidas e sugestões nos comentários!