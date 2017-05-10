---
title: CSS3 – Abas com a pseudo-classe :target
author: Diego Eis
type: post
date: 2011-03-21
excerpt: 'Fazer abas sempre foi muito chato para mim. Agora, os problemas acabaram com o :target. '
url: /css3-abas-com-a-pseudo-classe-target/
tweetbackscheck:
  - 1356419931
shorturls:
  - 'a:3:{s:9:"permalink";s:60:"http://tableless.com.br/css3-abas-com-a-pseudo-classe-target";s:7:"tinyurl";s:26:"http://tinyurl.com/42ldkf2";s:4:"isgd";s:19:"http://is.gd/5VcYQo";}'
twittercomments:
  - 'a:16:{i:49906350548975616;s:7:"retweet";i:49896396182130688;s:7:"retweet";i:49895218316705792;s:7:"retweet";i:49888254631219201;s:7:"retweet";i:49887539812765697;s:7:"retweet";i:49886879633518592;s:7:"retweet";i:49886386517585920;s:7:"retweet";i:49886032128262144;s:7:"retweet";i:124336025190412288;s:7:"retweet";i:152408786336890882;s:7:"retweet";i:156516289307873283;s:7:"retweet";i:156515825786949632;s:7:"retweet";i:156505976948789250;s:7:"retweet";i:156505366727897089;s:7:"retweet";i:153896114234458112;s:7:"retweet";i:169586416421048321;s:7:"retweet";}'
tweetcount:
  - 33
dsq_thread_id: 503040112
categories:
  - Código
  - CSS
  - CSS3
  - HTML
  - Técnicas e Práticas
tags:
  - 2011
  - aprenda
  - CSS
  - CSS3
  - Na Prática
  - tableless
  - tecnicascss
  - web standards

---
O CSS está cada vez mais facilitando as coisas. Alguns problemas que eram resolvidos apenas via Javascript já podem ser resolvidos inteiramente com CSS. Obviamente que para alguns browsers temos que usar algum script para conseguir a compatibilidade. Mesmo assim, se for já possível utilizar as novas maravilhas do CSS 3 e outras compatibilidades que estão surgindo do CSS 2.1, faça-o já. Você com certeza vai se agradecer um tempo próximo! 😉 

Um caso muito comum na produção de sites é a construção de tabs. Todo desenvolvedor já deve ter feito pelo menos uma vez na vida um script de tabs. Com a pseudo-classe :target seus problemas acabaram. 

Quando queremos relacionar um link na própria página, utilizamos o recurso de &#8220;âncora&#8221;. Quando colocamos um link com o valor assim:

[cc lang=&#8221;html&#8221;]
  
[Link][1]
  
[/cc]

Falamos para o browser que ao clicar no LINK, ele deve encontrar um ponto na página chamado, nesse exemplo, **nome-da-ancora**. Ele vai encontrar o elemento na página que tenha um ID com esse nome e navegará a barra de rolagem até a posição deste elemento. Você já deve saber disso e já deve ter visto funcionando.

Com a pseudo-classe :target isso ganha nova vida. O :target consegue relacionar isso a um objeto de forma que se você estiver criando abas (tabs), ele mostra automaticamente a aba relacionada. Vamos ao exemplo. Primeiro faça um HTML como o abaixo.

[cc lang=&#8221;html&#8221;]

<ul class="itens">
  <li>
    <a href="#aba1">Aba 1</a>
  </li>
  <li>
    <a href="#aba2">Aba 2</a>
  </li>
  <li>
    <a href="#aba3">Aba 3</a>
  </li>
</ul>

<div class="aba">
  <div id="aba1">
    Primeira Aba
  </div>
  
  <div id="aba2">
    Primeira Aba 2
  </div>
  
  <div id="aba3">
    Primeira Aba 3
  </div>
</div>

[/cc]

Note um detalhe muito importante: o valor do HREF dos links é exatamente o nome do ID dos DIVs referente ao conteúdo das abas.

Agora, para formatar e deixar bonitinho:

[cc lang=&#8221;html&#8221;]
	  
* {margin:0; padding:0;}
	  
body {
		  
font:13px verdana, arial, tahoma;
	  
}

ul { margin:20px 20px 0; list-style:none;}
	  
li {float:left;}
	  
.itens a {
		  
float:left;
		  
border:1px solid black;
		  
background:gray;
		  
padding:5px 15px;
		  
color:#FFF;
		  
text-decoration:none;
	  
}

.itens a:focus {background:red;}

.aba { padding:0 20px;width:400px; clear:both;}
	  
.aba div {
		  
background:white;
		  
border:1px solid black;
		  
padding:10px;
		  
width:100%;
		  
display:none;
	  
}

.aba div:first-child {
		  
display:block;
	  
}

[/cc]

Note que a última linha está dizendo para que os DIVs referentes às tabs fiquem escondidas e que só a primeira apareça.

A coisa toda acontece aqui, com uma linha de código:
  
[cc lang=&#8221;html&#8221;]
	  
.aba div:target {
		  
display:block;
	  
}
  
[/cc]

Essa linha entende o valor do HREF do link, capturando o ID referente ao div que o browser deve mostrar.

[Veja o exemplo completo aqui][2].

 [1]: #nome-da-ancora
 [2]: http://tableless.github.com/tableless/aba-target.html "Exemplo de pseudo-classe target"