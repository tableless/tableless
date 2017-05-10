---
title: Convertido – Menu (Livraria Cultura)
author: Diego Eis
type: post
date: 2010-01-12
excerpt: Reconstruindo o menu da Livraria Cultura.
url: /convertido-menu-livraria-cultura/
aktt_notify_twitter:
  - no
aktt_tweeted:
  - 1
tweetbackscheck:
  - 1356380431
shorturls:
  - 'a:3:{s:9:"permalink";s:56:"http://tableless.com.br/convertido-menu-livraria-cultura";s:7:"tinyurl";s:26:"http://tinyurl.com/3kaoclj";s:4:"isgd";s:19:"http://is.gd/yGTags";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 503016648
categories:
  - Código
  - Convertidos
tags:
  - Convertidos
  - CSS
  - estudo
  - html
  - livraria cultura
  - Na Prática
  - xhtml

---
Fazer menus com CSS é relativamente simples. Não precisamos de muitas linhas de código para fazer um menu totalmente personalizado. O Menu da [Livraria Cultura][1] é feito com Tabela. Na verdade, todo o site deles é feito com Tabelas, mas esse é outro assunto.

Você pode ver o [menu deles aqui][2].

O Código HTML do menu deles é:

<pre lang="html" line="1"><table border="0" cellpadding="0" cellspacing="0" width="100%">
  <tr>
    <td>
      <ul id="jsddm">
        <li id="mainmenu-livro" style="height: 22px; width: 79px;">
          <a href="/scripts/cultura/index.asp?sid=89120138612112390515516911&k5=2FEC93B&uid="><img src="imagem/_topo/abas/novo_livros.gif" alt="Livros" border="0" /></a>
          			<ul id="mainmenu-livro-sub" style="padding: 5px; background: rgb(11, 161, 176) none repeat scroll 0% 0%; -moz-background-clip: border; -moz-background-origin: padding; -moz-background-inline-policy: continuous; position: absolute; width: 69px; z-index: 350; margin-top: -2px; list-style-type: inherit; list-style-image: inherit; list-style-position: inherit; visibility: hidden;">
            <li>
              <a style="color: rgb(255, 255, 255);" href="/scripts/cultura/index.asp?lingua=POR&sid=89120138612112390515516911&k5=2FEC93B&uid=">Português</a>
              <a style="color: rgb(255, 255, 255);" href="/scripts/cultura/index.asp?lingua=ING&sid=89120138612112390515516911&k5=2FEC93B&uid=">Inglês</a>
              <a style="color: rgb(255, 255, 255);" href="/scripts/cultura/index.asp?lingua=ESP&sid=89120138612112390515516911&k5=2FEC93B&uid=">Espanhol</a>
            </li>
            <li>
              <a style="color: rgb(255, 255, 255);" href="/scripts/cultura/index.asp?lingua=FRA&sid=89120138612112390515516911&k5=2FEC93B&uid=">Francês</a>
            </li>
            <li>
              <a style="color: rgb(255, 255, 255);" href="/scripts/cultura/index.asp?lingua=ITA&sid=89120138612112390515516911&k5=2FEC93B&uid=">Italiano</a>
            </li>
            <li>
              <a style="color: rgb(255, 255, 255);" href="/scripts/cultura/index.asp?lingua=ALE&sid=89120138612112390515516911&k5=2FEC93B&uid=">Alemão</a>
              
              
            </li>
            			
          </ul>
          		
        </li>
        	
      </ul>
      		
    </td>
    	
    
    <td>
      <a href="/scripts/videos/index.asp?sid=89120138612112390515516911&k5=2FEC93B&uid="><img src="imagem/_topo/abas/b_dvds2.gif" alt="DVDs" border="0" /></a>
    </td>
    	
    
    <td>
      <a href="/scripts/musica/index.asp?sid=89120138612112390515516911&k5=2FEC93B&uid="><img src="imagem/_topo/abas/b_cds2.gif" alt="CDs" border="0" /></a>
    </td>
    	
    
    <td>
      <a href="/scripts/games/index.asp?sid=89120138612112390515516911&k5=2FEC93B&uid="><img src="imagem/_topo/abas/b_games2.gif" alt="Games" border="0" /></a>
    </td>
                                   
    
    <td>
      <a href="/scripts/hotsites/index.asp?sid=89120138612112390515516911&k5=2FEC93B&uid="><img src="imagem/_topo/abas/novo_sitesesp.gif" alt="Hotsites" border="0" /></a>
    </td>
    
    	
    
    <td>
      <a href="/scripts/eventos/index.asp?sid=89120138612112390515516911&k5=2FEC93B&uid="><img src="imagem/_topo/abas/novo_eventos.gif" alt="Eventos" border="0" /></a>
    </td>
    	
    
    <td width="100%">
      
    </td>
    
  </tr>
  
</table>
</pre>

Eu não encontrei qual seria o pedaço do CSS referente ao menu, por isso eu não vou colar aqui.

O problema da versão do menu deles é que é todo feito com imagens e usa muita tabela. Há também código CSS inline. Isso prejudica leitores de tela, prejudica Google, e manutenção.
  
A versão que sugerimos é feita utilizando a técnica [Image-Replacement][3]. Segue abaixo o código HTML:

<pre lang="html" line="1"><div class="nav">
  <ul>
    <li class="navlivros">
      <a href="#">Livros</a>
      			<ul>
        <li>
          <a href="#">Português</a>
        </li>
        				
        
        <li>
          <a href="#">Inglês</a>
        </li>
        				
        
        <li>
          <a href="#">Espanhol</a>
        </li>
        				
        
        <li>
          <a href="#">Francês</a>
        </li>
        				
        
        <li>
          <a href="#">Italiano</a>
        </li>
        				
        
        <li>
          <a href="#">Alemão</a>
        </li>
        			
      </ul>
      		
    </li>
    		
    
    <li class="navdvd">
      <a href="#">DVDs</a>
    </li>
    		
    
    <li class="navcd">
      <a href="#">CDs</a>
    </li>
    		
    
    <li class="navgames">
      <a href="#">Games</a>
    </li>
    		
    
    <li class="navsitesesp">
      <a href="#">Sites especiais</a>
    </li>
    		
    
    <li class="naveventos">
      <a href="#">Eventos</a>
    </li>
    	
  </ul>
  
</div>
</pre>

Abaixo o Código CSS:

<pre lang="CSS" line="1">* {
	margin:0;
	padding:0;
	list-style:none;
}

.nav {padding:10px;}

.nav ul li {float:left; position:relative;}

/* Define que todos os submenus aparecem quando passarmos o mouse no LI "pai" */
.nav ul li:hover ul {display:block;}

/* Define o estilo dos links */
.nav ul li a {
	float:left;
	height:22px;
	text-indent:-9999px;
	overflow:hidden;
	background-position:center center;
	background-repeat:no-repeat;
}

/* Adiciona o background e a largura nos elementos do menu */
.nav ul li.navlivros a {width:79px; background-image:url(imagem/_topo/abas/novo_livros.gif);}
.nav ul li.navdvd a {width:79px; background-image:url(imagem/_topo/abas/b_dvds2.gif);}
.nav ul li.navcd a {width:79px; background-image:url(imagem/_topo/abas/b_cds2.gif);}
.nav ul li.navgames a {width:79px; background-image:url(imagem/_topo/abas/b_games2.gif);}
.nav ul li.navsitesesp a {width:149px; background-image:url(imagem/_topo/abas/novo_sitesesp.gif);}
.nav ul li.naveventos a {width:109px; background-image:url(imagem/_topo/abas/novo_eventos.gif);}

/** Define que a UL do submenu está escondida por default. E define o visual do submenu */
.nav ul li ul {
	display:none;
	background:#00A2B0;
	width:70px;
	position:absolute; top:22px; left:0px;
	padding:4px;
}

/* Resetamos todo o estilo dos links do submenu. Isso poderia ser evitado se o IE7 conhecesse seletores complexos ou com JQuery */
.nav ul li ul li a {
	font:13px verdana, arial, tahoma, sans-serif;
	background-image:none !important;
	text-indent:0;
	float:none;
	color:white;
}

.nav ul li ul li a:hover {text-decoration:none;}
</pre>

Veja o resultado do [menu reconstruído aqui][4].

O Submenu na versão original, eu fiz utilizando apenas CSS. Testei em Firefox e IE7/8. Funciona que é uma beleza. Sem Javascript, sem JQuery, nem nada.
  
Se o IE7 já conhecesse seletores complexos, não precisaríamos resetar todos os links dos submenus como fizemos na linha 35.
  
O Código CSS, embora pareça longo, ele está organizado para ser fácil de adicionar outros elementos. 

Sempre que escrever um CSS, pense sempre no futuro. Um CSS para resolver um problema imediato, normalmente tem menos código. Mas ele resolve apenas aquele problema específico. Se você fizer um CSS abrangente e pensando no futuro, seu código fatalmente vai ficar maior. Mas você terá menos retrabalho ao fazer as alterações futuras. Eu prefiro.

Pegue aqui os dois códigos para estudar: [Reconstrução Menu Livraria Cultura][5]

 [1]: http://www.livrariacultura.com.br/
 [2]: http://tableless.com.br/convertidos/livraria-cultura/menu/original/
 [3]: http://tableless.com.br/image-replacement-x-imagens
 [4]: http://tableless.com.br/convertidos/livraria-cultura/menu/correto/
 [5]: http://tableless.com.br/uploads/2010/01/livraria-cultura.zip