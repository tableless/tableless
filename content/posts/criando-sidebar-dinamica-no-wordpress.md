---
title: Criando Sidebar Dinâmica no WordPress
author: Paulo Rodrigues
type: post
date: 2011-01-18
excerpt: Aprenda a adicionar sidebars e adicione os widgets disponíveis dentro do painel de administração.
url: /criando-sidebar-dinamica-no-wordpress/
tweetbackscheck:
  - 1356425161
shorturls:
  - 'a:3:{s:9:"permalink";s:61:"http://tableless.com.br/criando-sidebar-dinamica-no-wordpress";s:7:"tinyurl";s:26:"http://tinyurl.com/3nureyb";s:4:"isgd";s:19:"http://is.gd/E4jXWS";}'
twittercomments:
  - 'a:12:{i:36967906554294273;s:7:"retweet";i:36957508065042432;s:7:"retweet";i:156425917344907265;s:7:"retweet";i:156370509796347904;s:7:"retweet";i:156345151780945920;s:7:"retweet";i:156322783184433152;s:7:"retweet";i:159577988613160961;s:7:"retweet";i:159450100849053699;s:7:"retweet";i:159445987721617408;s:7:"retweet";i:159440797467557888;s:7:"retweet";i:159435779637116928;s:7:"retweet";i:159433088785580034;s:7:"retweet";}'
tweetcount:
  - 29
dsq_thread_id: 503039956
categories:
  - Wordpress
tags:
  - 2011
  - Na Prática
  - sidebar
  - sidebar dinamica
  - widgets
  - Wordpress

---
O WordPress disponibiliza uma função para criar sidebars de forma dinâmica, onde no painel de administração podemos gerenciar todos os Widgets disponíveis ou Widgets instalados.

Essa função, mais uma vez, sai na frente e contribui para o WordPress ser esse CMS tão poderoso para os desenvolvedores e os usuários que o utilizam.

De início iremos registrar a sidebar. Para isso coloque esse código em functions.php: 

[cc lang=&#8221;php&#8221;]
	  
/\* Registando a primeira sidebar\*/
	  
register_sidebar( array(
		  
&#8216;name&#8217; => &#8216;Minha Primeira Sidebar&#8217;,
		  
&#8216;id&#8217; => &#8216;minha-primeira-sidebar&#8217;,
		  
&#8216;description&#8217; => &#8216;Esta é a primeira sidebar do meu site&#8217;,
		  
&#8216;before_widget&#8217; => &#8216;

<li class="widget-sidebar">
  &#8216;, /* Antes da Widget */<br /> &#8216;after_widget&#8217; => &#8216;
</li>
&#8216;, /\* Depois da Widget \*/
		  
&#8216;before_title&#8217; => &#8216;

### &#8216;, /\* Antes do título \*/
		  
&#8216;after_title&#8217; => &#8216;

&#8216;, /\* Depois do título \*/
	  
) );

/\* Registando a segunda sidebar\*/
	  
register_sidebar( array(
		  
&#8216;name&#8217; => &#8216;Minha Segunda Sidebar&#8217;,
		  
&#8216;id&#8217; => &#8216;minha-segunda-sidebar&#8217;,
		  
&#8216;description&#8217; => &#8216;Esta é a segunda sidebar do meu site&#8217;,
		  
&#8216;before_widget&#8217; => &#8216;

<li class="widget-sidebar">
  &#8216;, /* Antes da Widget */<br /> &#8216;after_widget&#8217; => &#8216;
</li>
&#8216;, /\* Depois da Widget \*/
		  
&#8216;before_title&#8217; => &#8216;

#### &#8216;, /\* Antes do título \*/
		  
&#8216;after_title&#8217; => &#8216;

&#8216;, /\* Depois do título \*/
	  
) );
  
[/cc]

Neste código, registramos nossa sidebar, ou seja, aplicamos os parâmetros que estarão agregados a ela. Os três primeiros parâmetros estão subentendidos, mas você pode definir o valor que quiser. O restante dos parâmetros agregará o que vai está antes e depois do Widget e do Título. Você pode personalizar como quiser, com uma LI ou DIV ou até outra tag que queria retornar.

### Retornando a sidebar

Adicione o seguinte código aonde queria que retornasse a sua sidebar: 

[cc lang=&#8221;php&#8221;]
  
<?php dynamic_sidebar('Minha Primeira Sidebar'); ?>


  
[/cc]

A função vai agregar o nome da sidebar ou o ID da sidebar de forma muito simples. Para deixar mais completo, vamos adicionar uma condição, só para verificar se a sidebar está ativa. A função is\_active\_sidebar vai agregar também o nome da sidebar ou o ID dela.

[cc lang=&#8221;php&#8221;]
  
<?php 
	/* Retornando minha primeira sidebar */
       if ( is_active_sidebar('minha-primeira-sidebar') ) {
	      dynamic_sidebar('minha-primeira-sidebar');
       }

	/* Retornando minha segunda sidebar */
        if ( is_active_sidebar('minha-segunda-sidebar') ) {
	       dynamic_sidebar('minha-segunda-sidebar');
        }
 ?>


  
[/cc]

Caso tenham dúvidas, verifiquem em [http://codex.wordpress.org/Widgets_API][1]

 [1]: http://codex.wordpress.org/Widgets_API "Widgets WordPress"