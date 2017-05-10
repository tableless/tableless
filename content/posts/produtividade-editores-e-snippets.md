---
title: 'Produtividade: editores e snippets'
author: Diego Eis
type: post
date: 2010-02-18
excerpt: Se você é um desenvolvedor de verdade, você deve conhecer seu editor de códigos. Não importa qual ele seja, contanto que você o conheça do começo ao fim, saiba suas limitações e saiba utilizar suas vantagens para minimizar o tempo de produção.
url: /produtividade-editores-e-snippets/
aktt_notify_twitter:
  - no
tweetbackscheck:
  - 1356384255
shorturls:
  - 'a:3:{s:9:"permalink";s:57:"http://tableless.com.br/produtividade-editores-e-snippets";s:7:"tinyurl";s:26:"http://tinyurl.com/3jsphd4";s:4:"isgd";s:19:"http://is.gd/jBpidD";}'
twittercomments:
  - 'a:3:{i:154578867951124480;s:7:"retweet";i:154258868367654913;s:7:"retweet";i:154257360477634561;s:7:"retweet";}'
tweetcount:
  - 5
dsq_thread_id: 503039354
categories:
  - Artigos
  - Código
  - Editores
  - Técnicas e Práticas
tags:
  - 2010
  - CSS
  - desenvolvimento web
  - editores
  - html
  - Na Prática
  - sparkup
  - tableless
  - Vídeos Tutoriais
  - zen coding

---
Não é muito difícil ser produtivo. Em muitas palestras e aulas, me perguntam como o desenvolvedor client-side (ou qualquer outro) pode melhorar sua performance e desenvolver melhor, mais rápido e com qualidade. Além de muito treino, existem outros pontos que se utilizados da maneira correta, podem agilizar seu trabalho. Um destes pontos é o seu editor de código.
  
Você já parou para conhecer seu editor? Muitos desenvolvedores simplesmente ignoram a existência das features que seu editor carrega. Simplesmente instalam e digitam código. Desenvolvedor que é desenvolvedor, gasta tempo aprendendo seu editor.

Quando eu utilizava Windows, experimentei dezenas de editores. Foram muitos mesmo. Comecei pelo Notepad, passei pelo [Homesite][1] e [CoffeeCup][2]. Antes de migrar para Mac, eu estava utilizando [EditPlus][3], mas estava tendo uma quedinha pelo [NotePad++][4]. Os dois são muito bons, embora faça um pouco de tempo que o EditPlus não tenha uma atualização.
  
Quando migrei para Mac, comecei utilizando o [BlueFish][5]. Gostei, mas não fui com a cara. A mesma coisa aconteceu com o [BBEdit][6]. Foi aí que encontrei o [Textmate][7] e depois o [Coda][8]. Gostei dos dois. Utilizei durante muito tempo o Coda por conta do seu FTP. Embora o Coda seja completíssimo, o TextMate me ganhou.

Toda essa migração de editores não foi da noite para o dia. Quando eu realmente gostava de um editor, eu o utilizava por muito tempo. Alguns desenvolvedores trocam de editor como trocam de roupa. Não é saudável. Você acaba não conhecendo suas especialidades e limitações. Você não tem tempo para se acostumar com a interface. E isso tudo prejudica sua produtividade. Eu recomendo que você tenha um editor predileto e fique apenas com ele.

### Snippets

Eu gostava do Editplus por que ele era um dos únicos editores para Windows que tinham um configurador de Snippets decente (e olha que nem era muito bom). O Textmate tem um gerenciador de snippets invejável e foi por isso que fiquei com ele e não com o Coda.

Na maioria dos editores, os snippets te ajudam com código repetitivo. Eles autocompletam e inserem códigos que são repetitivos para que você não perca tempo redigindo. Mas pára por aí. Você sempre tem que digitar um bocado de código mesmo quando o snippet te ajuda no trabalho pesado. Claro que você tem a possibilidade de configurar e personalizar os seus snippets. Mas muitos dos desenvolvedores não querem parar para criar uma biblioteca de snippets que os ajudem realmente no trabalho pesado do código. É aí que entra o Zen Coding, uma biblioteca completa que lhe permite escrever pouco código e obter o máximo de resultado.

A sintaxe do Zen Coding é baseado em CSS. Você escreve &#8220;seletores&#8221; de CSS para obter código HTML.
  
O [Zen Coding][9] foi feito pelo [Sergey Chikuyonok][10] (em russo). Veja abaixo um vídeo demo de como funciona:



Pra quem não quiser ver o vídeo: a idéia é que uma linha como essa:
  
[cc lang=&#8221;CSS&#8221;]div#header > h1.logo > a {logo do site} < ul.menu > li.item-$*5 > a[/cc]
  
Retorne este código:
  
[cc lang=&#8221;html&#8221;]

<div id="header">
  <h1 class="logo">
    <a></a>
  </h1>
  
  <ul class="menu">
    <li class="item-1">
      <a></a>
    </li>
    <li class="item-2">
      <a></a>
    </li>
    <li class="item-3">
      <a></a>
    </li>
    <li class="item-4">
      <a></a>
    </li>
    <li class="item-5">
      <a></a>
    </li>
  </ul>
</div>

[/cc]
  
Os programadores da [Visie][11] me mostraram estes dias um outro projeto criado pelo [Rico Sta. Cruz][12] chamado [SparkUp][13]. O Sparkup foi inspirado no Zen Coding. Mas tem uma coisa ou outra diferente. Abaixo veja um vídeo introdutório:



Se você é iniciante, entenda que você precisa aprender HTML primeiro. É interessante que você saiba o que cada tag faz, qual sua função e suas características. Aconselho o uso destes snippets apenas para desenvolvedores que já são fluentes em HTML. Não adianta você escrever em Sparkup, mas não saber do que se trata cada tag que foi jogada ali. Isso pode te transformar em um [desenvolvedor analfabeto][14].

O Sparkup tem apenas suporte para Textmate e VIM, por enquanto. Já o Zen Coding tem suporte completo para [Aptana][15], [Coda][8], [Espresso][16], [Textmate][7], [editArea][17], [Visual Studio][18], [Komodo Edit/IDE][19]. Sem contar com suporte parcial para os editores [TopStyle][20], [Sublime Text][21], [GEdit][22], [Dreamweaver CS4][23], [UltraEdit][24], [BBEdit][6] e [Emacs][25].

[Para baixar o Sparkup visite seu projeto no GitHug][13].
  
[Para baixar o Zen Coding, visite seu projeto no Google Code][9].

 [1]: http://www.adobe.com/products/homesite/
 [2]: http://www.coffeecup.com/html-editor/
 [3]: http://editplus.com/
 [4]: http://notepad-plus.sourceforge.net/uk/site.htm
 [5]: http://bluefish.openoffice.nl/
 [6]: http://www.barebones.com/products/bbedit/
 [7]: http://macromates.com/
 [8]: http://www.panic.com/coda/
 [9]: http://code.google.com/p/zen-coding/
 [10]: http://chikuyonok.ru/
 [11]: http://visie.com.br/
 [12]: http://github.com/rstacruz
 [13]: http://github.com/rstacruz/sparkup
 [14]: http://tableless.com.br/desenvolvedor-analfabeto
 [15]: http://www.aptana.com/
 [16]: http://macrabbit.com/espresso/
 [17]: http://www.cdolivet.com/index.php?page=editArea
 [18]: http://www.microsoft.com/visualstudio/
 [19]: http://www.activestate.com/komodo/
 [20]: http://www.topstyle4.com/
 [21]: http://www.sublimetext.com/
 [22]: http://www.gnome.org/projects/gedit/
 [23]: http://www.adobe.com/products/dreamweaver/
 [24]: http://www.ultraedit.com/
 [25]: http://www.gnu.org/software/emacs/