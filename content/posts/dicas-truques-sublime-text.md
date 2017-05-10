---
title: Dicas e truques de Sublime Text
author: Diego Eis
type: post
date: 2012-09-04
excerpt: Conheça algumas dicas e truques do Sublime Text.
url: /dicas-truques-sublime-text/
tweetbackscheck:
  - 1356386541
shorturls:
  - 'a:3:{s:9:"permalink";s:56:"http://tableless.com.br/dicas-e-truques-de-sublime-text/";s:7:"tinyurl";s:26:"http://tinyurl.com/8s5l6sp";s:4:"isgd";s:19:"http://is.gd/RBWXfm";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 830376124
categories:
  - Editores
  - O Básico
tags:
  - 2012
  - editores
  - produtividade
  - sublime

---
Sublime Text tem sido o meu editor predileto da vez. Ele é simples, limpo, leve e muito, mas muito customizável. Como um bocado de gente tem me pedido dicas resolvi fazer esse post, curtinho, com dicas básicas de Sublime. 

### Suas preferências

Uma das primeiras coisas que você precisa saber é que o Sublime guarda suas preferências em um arquivo em formato JSon, por isso é bem fácil de entender.
  
Os dois arquivos que você precisa saber: Um para seus atalhos de teclado, que fica aqui **Sublime Text 2 > Preferences > Key Bindings &#8211; User** e outro para as definições gerais, **Sublime Text 2 > Preferences > Settings &#8211; User** ou _CMD + ,_.

Nestes dois arquivos você muda o que quiser. Coisa linda. Se você tiver que mudar qualquer coisa, lembre-se de mudar sempre no arquivo de USER, que é o seu arquivo. Assim você mantém as definições default intactas. 

Uma sacada é colocar estes arquivos dentro da sua pasta de Dropbox, no GIT ou qualquer outro lugar de forma que você consiga recuperá-los quando formatar a máquina ou quando quiser configurar o Sublime em outro computador. Eu fiz coloquei os meus dentro de uma pasta no Dropbox e fiz um link simbólico para o Sublime.

Se você quiser descobrir o nome de um determinado atalho referente a um comando de teclado, basta abrir o console do Sublime com o atalho _CMD+\`_ e a cada comando de teclado que você executar, você verá o nome do comando referente a este atalho.

### Lista de comandos

Sublime tem muitos comandos escondidos que podem não estar listados nos menus. Você pode acioná-los pelo teclado acionando os comandos pelo controle de acesso CMD+SHIFT+P. Lindo, não?

### Package Control

Como qualquer outro editor o Sublime tem uma série de plugins que salvam a sua vida e turbinam sua produtividade. Acontece que é muito, mas muito chato você instalar todos estes plugins, é por isso que antes de qualquer outro plugin, instale o [Sublime Packaget Control][1]. 

O Sublime Package Control é um plugin que gerencia outros plugins. Você consegue procurar, instalar e desinstalar plugins do seu Sublime de uma maneira simples. Para acioná-lo use o atalho CMD+SHIFT+P. Com esse atalho você consegue executar uma série de comandos do Sublime, para usar o Package Control, inicie escrevendo &#8220;Package Control:&#8221;. Aparecerá uma lista de comandos que você poderá utilizar. 

A opção INSTALL PACKAGE mostra uma lista de pacotes que você poderá instalar. Se quiser ver uma lista do site deles, [vá direto nesse link][2].

Uma [lista completa de comandos pode ser vista aqui][3].

### Configurando um atalho de linha de comando

Esse [link dispensa explicações][4]. Ele ensina a instalar o comando **subl** no seu terminal para facilitar a abertura de projetos no Sublime via terminal.

### Múltiplas seleções

Quer selecionar vários lugares ao mesmo tempo? Fácil, segure o CMD ou o CTRL e use o mouse para selecionar diversas partes do seu código.

### Selecionar pedaços iguais de código

Imagine que você tem o código abaixo:

<pre class="lang-html">&lt;ul&gt;
	&lt;li&gt;Op&ccedil;&atilde;o 1&lt;/li&gt;
	&lt;li&gt;Op&ccedil;&atilde;o 2&lt;/li&gt;
	&lt;li&gt;Op&ccedil;&atilde;o 3&lt;/li&gt;
	&lt;li&gt;Op&ccedil;&atilde;o 4&lt;/li&gt;
	&lt;li&gt;Op&ccedil;&atilde;o 5&lt;/li&gt;
&lt;/ul&gt;
</pre>

Você quer colocar agora a mesma classe em todos os li desse bloco. Selecione a primeira tag <li> e em seguida aperte CMD+D para selecionar outros blocos de código iguais a este que você selecionou inicialmente, nesse caso os LIs.

### Procurar arquivos

Quer encontrar arquivos no seu projeto sem ter que ficar perdendo tempo nas pastas? Use o atalho CMD+T e pronto, digite o nome do seu arquivos e edite-o.

### Goto Anything

Quer encontrar funções, classes ou IDs dentro do seus arquivos? Use o atalho CMD+P. Esse comando abre o search geral do Sublime. Nesse search você pode procurar arquivos, como no exemplo anterior ou se você iniciar a busca com um **@**, vai possibilitar a procura de funções, classes, IDs e etc no arquivo aberto.

Se você quiser ir para uma linha específica, você pode começar a busca com **:** (dois pontos) e aí você coloca o número da linha ou use o atalho CTRL+G e número da linha.

### Esconder a Sidebar

Se você trabalha em um notebook com tela pequena você vai querer isso. Basta apertar CMD+K e seguidamente CMD+B. Isso faz com que a Sidebar apareça ou desapareça.

### Apagar linha inteira

Para apagar a linha inteira: CMD+K+K.

### Clonar a linha

Para copiar uma linha inteira e duplicá-la: CMD+SHIFT+D.

### Seleção em bloco

Segure CTLR+SHIFT aperte a seta do teclado para baixo. Você verá o cursor selecionando as linhas. Depois segure o SHIFT e aperte a tecla para direita. Pronto… Seleção bloco.

### Atalhos de seleção

A tecla SUPER é **CMD no Mac** e a **tecla WINDOWS no Windows**.

| Ação                                      | Atalho                |
| ----------------------------------------- | --------------------- |
| Selecionar conteúdo entre tags            | SUPER + SHIFT + A     |
| Expadir seleção para linha                | SUPER + L             |
| Expandir seleção para ocorrência idêntica | SUPER + D             |
| Expandir seleção para escopo              | SUPER + SHIFT + SPACE |
| Expandir seleção para colchetes           | CTRL + SHIFT + M      |
| Mover a linha para cima                   | CTRL + SUPER + UP     |
| Mover a liha para baixo                   | CTRL + SUPER + DOWN   |
| Duplicar linha                            | SUPER + SHIFT + D     |
| Juntar linhas                             | SUPER + J             |

Segue alguns links de referência:

  * [Sublime Text 2 &#8211; Meu novo editor][5]
  * [Sublime Text Cheat Sheet][6]
  * [Sublime Text Tips and Tricks][7]
  * [Sublime Text 2 Tips and Shortcuts][8]
  * [OS X Command Line &#8211; Sublime][4]
  * [Customizing Sublime Text][9]

 [1]: http://wbond.net/sublime_packages/package_control
 [2]: http://wbond.net/sublime_packages/community
 [3]: http://wbond.net/sublime_packages/package_control/usage
 [4]: http://www.sublimetext.com/docs/2/osx_command_line.html
 [5]: http://tableless.com.br/sublime-text-2-meu-novo-editor/
 [6]: https://docs.google.com/spreadsheet/ccc?key=0AnLDKkpwS2wCdHVoRGdlZ2h0MVhjLXlVTVJFbVFCWWc&hl=en_GB#gid=0
 [7]: http://net.tutsplus.com/tutorials/tools-and-tips/sublime-text-2-tips-and-tricks/
 [8]: http://robdodson.me/blog/2012/06/23/sublime-text-2-tips-and-shortcuts/
 [9]: http://docs.sublimetext.info/en/latest/customization/settings.html