---
title: Sublime Text 2 – Meu novo editor
author: Diego Eis
type: post
date: 2012-04-16
excerpt: Entenda um pouco sobre o editor que está quebrando tudo.
url: /sublime-text-2-meu-novo-editor/
tweetbackscheck:
  - 1356458200
shorturls:
  - 'a:3:{s:9:"permalink";s:31:"http://tableless.com.br/?p=5924";s:7:"tinyurl";s:26:"http://tinyurl.com/dxjkter";s:4:"isgd";s:19:"http://is.gd/yzgkCt";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 651592681
categories:
  - Editores
tags:
  - desenvolvimento
  - editores
  - sublime

---
Durante muito tempo eu fui apaixonado pelo Coda e pelo Textmate. Eu os utilizava praticamente todos os dias. O Coda tem um find/replace sensacional que funciona muito bem. O Textmate é ligeiro para a criação de snippets e outras tarefinhas automatizadas. Acontece que eu conheci o Sublime Text pelo [Márcio Trindade][1], que trabalha comigo e então eu me apaixonei. Não pelo Márcio, mas pelo Sublime (falá-se sublaime). 😉

## Sem frescura

O que eu amava quando no Editplus do Windows era a interface limpa. Não quero ver iconezinhos bonitinhos, eu quero uma tela branca, pronta pra escrever. O problema é que eu não sou sadomasoquista suficiente para ficar usando o VI. O Textmate é muito parecido com o Editplus nesse quesito, assim como o Sublime. O Sublime é limpo e o code highlight padrão é muito confortável. Confesso que nunca fui fã de editores com o fundo escuro. Comecei a gostar depois do Sublime.

## Customização

A customização do Textmate é sensacional. As possibilidades são muito maiores que a do Coda. Mas o Sublime consegue superar o Textmate. Ele guarda as configurações personalizadas em um arquivo separado com a sintaxe parecida com JSON. Você pode colocar esse arquivo no seu Dropbox e criar um link simbólico para o diretório do Sublime. Assim as suas configurações ficam iguais no trabalho e em casa.

Nesse arquivo você pode configurar tudo, desde o thema que será usado até as definições de word-wrap, tabs e espaços, tamanho de fonte, algumas configurações de busca e etc. Sensacional. Nunca mais perca tempo reconfigurando seu editor quando reinstalar o sistema.

[cc lang=&#8221;javascript&#8221;]
	  
&#8220;indent\_subsequent\_lines&#8221;: true,
	  
&#8220;indent\_to\_bracket&#8221;: false,
	  
&#8220;line_numbers&#8221;: true,
	  
&#8220;line\_padding\_bottom&#8221;: 2,
	  
&#8220;line\_padding\_top&#8221;: 2,
	  
&#8220;margin&#8221;: 0,
	  
&#8220;match_brackets&#8221;: true,
	  
&#8220;match\_brackets\_angle&#8221;: false,
	  
&#8220;match\_brackets\_braces&#8221;: true,
	  
&#8220;match\_brackets\_content&#8221;: true,
	  
&#8220;match\_brackets\_square&#8221;: true,
	  
&#8220;match_selection&#8221;: true,
	  
&#8220;match_tags&#8221;: true,
	  
&#8220;move\_to\_limit\_on\_up_down&#8221;: false,
	  
&#8220;open\_files\_in\_new\_window&#8221;: true,
	  
&#8220;overlay\_scroll\_bars&#8221;: &#8220;system&#8221;,
	  
&#8220;remember\_open\_files&#8221;: false,
	  
&#8220;rulers&#8221;:
  
[/cc]

Como sou um cara solidário, coloquei [meus arquivos de configuração do Sublime no Git][2]. Assim você consegue pegar emprestado e eu não perco toda vez que eu reinstalar o sistema.

## Plugins

Os plugins são o filé do Sublime Text. Para começar instale o [Sublime Package Control][3]. Este plugin te ajuda a descobrir, instalar e gerenciar pacotes e plugins do Sublime facilmente via comando de teclado.

Outro plugin muito útil é o [SideBarEnhancements][4]. Ele insere uma série de opções no menu contextual dos arquivos da sidebar. Você pode dizer: &#8220;O meu editor faz isso sem plugin&#8221;. Aí eu digo: &#8220;Você consegue customizar se quiser?&#8221;. 

Existem outros plugins para integrar com o GIT, snippets para Bootstrap, SFTP, highlight, VI, SASS, LESS e outras coisas.

Descubra alguns [plugins disponíveis para o Sublime aqui][5].

Você pode instalar esses plugins via o Package Control, que citamos anteriormente.

## Tarefas com o Teclado

Quer encontrar uma função, classe ou id? Existe um atalho que se chama GoTo Anything. Aperte CMD+R ou CMD+P (CTRL+P), coloque um **@** e comece a digitar o nome da função. Quer ir para uma linha? Digite CTLR+G ou CMD+P, coloque **:** e diga o número da linha. 

Dá uma olhada [nesses atalhos][6] básicos e nesse [Sublime Cheet Sheet][7].

Só o GoTo Anything quebra um galho danado.

A seleção por colunas funciona como no Textmate. E pra mim, uma novidade que eu só via no VI é a seleção por similaridade. Você consegue selecionar, via teclado mesmo, várias tags ou caractéres iguais. Por exemplo, suponha que você queira selecionar em um mesmo documento todas as tags <p>. Selecione primeiro a tag e depois aperte CMD+D. 

## Find and Replace

Find and Replace é coisa linda. Eu não vivo sem e provavelmente você também não. Você consegue procurar por arquivos e palavras em todos os documentos de uma pasta determinada, em arquivos abertos ou em pastas abertas. Aperte CMD+T e você consegue filtrar os arquivos que você precisa. Claro, que você também pode procurar arquivos via o GoTo Anything que já havíamos falado anteriormente via CMD+P.

SHIT+CMD+F você procura e substitui por arquivos dentro de uma determinada pasta.
  
Com ALT(option)+CMD+F você tem o find/replace tradicional.

Nem preciso dizer do suporte a expressões regulares, né?

## Suporte

O [Sublime][8] tem versões para Windows, Linux e Mac.

### Mais para ler

  * [Eclipse Color Themes][9]
  * [Como criar snippets no Sublime Text 2][10]
  * [Sublime Text 2 Tips and Tricks][11]
  * [Sublime Text Workflow][12]
  * [Nove razões para você instalar Sublime][13]
  * [Migrando do Textmate para o Sublime][14]

 [1]: http://marciotrindade.com/
 [2]: https://github.com/tableless/Sublime/
 [3]: http://wbond.net/sublime_packages/package_control/installation
 [4]: https://github.com/titoBouzout/SideBarEnhancements
 [5]: http://wbond.net/sublime_packages/community
 [6]: https://gist.github.com/1596897
 [7]: https://docs.google.com/spreadsheet/ccc?key=0AnLDKkpwS2wCdHVoRGdlZ2h0MVhjLXlVTVJFbVFCWWc&hl=en_GB#gid=0
 [8]: http://www.sublimetext.com/2
 [9]: http://www.eclipsecolorthemes.org/?view=theme&id=66
 [10]: http://tutsmais.com.br/blog/2012/como-criar-snippets-no-sublime-text-2-rapido-pratico-util-e-sexy/
 [11]: http://net.tutsplus.com/tutorials/tools-and-tips/sublime-text-2-tips-and-tricks/
 [12]: http://tarantsov.com/blog/2012/02/sublime-text-workflow-that-beats-coda-and-espresso/
 [13]: http://1p1e1.tumblr.com/post/14262857223/9-reasons-you-must-install-sublime-text-2-code-like-a
 [14]: http://danielfilho.info/blog/migrando-do-textmate-para-o-sublime-text-2/