---
title: Front-end concluído, como começar no WordPress? Parte I
author: Paulo Rodrigues
type: post
date: 2012-01-05
excerpt: A primeira parte do artigo abordará o inicio com desenvolvimento com Wordpress, desde da conclusão do front-end, até de criação da página inicial e sua personalização através de sidebar, menu, loop dos posts, ect.
url: /front-end-concluido-como-comecar-wordpress-parte-i/
tweetbackscheck:
  - 1356437477
shorturls:
  - 'a:3:{s:9:"permalink";s:31:"http://tableless.com.br/?p=4835";s:7:"tinyurl";s:26:"http://tinyurl.com/bsv6v2r";s:4:"isgd";s:19:"http://is.gd/OBr5q1";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 527485010
categories:
  - Wordpress
tags:
  - 2012
  - Wordpress

---
Andando pelo <a href="http://tableless.com.br/forum/" title="Fórum" target="_blank">fórum do Tableless</a>, me deparei com [esta postagem][1], e pelo que eu vi, essa é uma grande dúvida para todos que estão iniciando no desenvolvimento com WordPress. 

O usuário [Angelo Lucas][2] do nosso fórum postou a seguinte resposta:

>   1. Desenvolva o Front-End do tema (HTML, CSS e Javascript)
>   2. Instale o PHP, Mysql na sua máquina. Baixe o WordPress e instale-o, ele vem com alguns temas incluso
>   3. Duplique um tema do wordpress e começe a implementar seu HTML na programação já existente, não é difícil, não é chato.

Gostei bastante da resposta, mas o assunto é tão empolgante que merecia um conteúdo mais detalhado. E para melhorar o aprendizado e nos guiar, <a href="http://tableless.com.br/uploads/2011/12/layout-para-desenvolvimento-wordpress.jpg" target="_blank">desenhei um layout bem simples</a>. **Não reparem, sou péssimo design.**

### Iniciando o desenvolvimento

Com o front-end concluído, duplique o tema padrão do WordPress e altere o nome da pasta duplicada para o nome do seu tema. Acho melhor duplicar, pois se perde um tempo criando os arquivos do zero. Se o seu WordPress for a partir da versão 3.2, terás dois temas padrões: o Twenty Ten e o Twenty Eleven. A diferença é que o Twenty Eleven vem programado nas tags do HTML5.

Depois disso, é importante entender a <a href="http://tableless.com.br/hierarquia-de-arquivos-do-wordpress/" target="_blank">hierarquia de arquivos do WordPress</a> e saber que **sem os arquivos index.php e style.css o tema não funciona**.

O arquivo style.css, além do estilo do tema, pode-se preencher informações do tema. Adicione no inicio do style.css esses comentários:

<pre class="lang-css">/*
Theme Name: Nome do meu Tema
Theme URI: http://meusite.com.br
Description: Descrição do meu tema
Author: Paulo Rodrigues
Author URI: http://meusite.com.br
Version: 1.0
Tags: branco, vermelho, preto, header, menu, colunas, rodape
*/
</pre>

Personalize a partir das suas informações, mas não é necessário preencher todas elas, colocar o nome do tema e o nome do autor está ótimo.

Dois arquivos do tema possuem importância e servem para aumentar a nossa produtividade, que são: header.php e footer.php e essas páginas são incluidas nas páginas através das funções get\_header() e get\_footer(), respectivamente. 

Vou mostrar um exemplo de meus arquivos header.php e footer.php para vocês terem noção.

[<img src="http://tableless.com.br/uploads/2011/12/header-para-desenvolvimento-wordpress.jpg" alt="Header para desenvolvimento WordPress" width="600" height="63" class="alignnone size-medium wp-image-4843" />][3]

**header.php**

<pre class="lang-html">&lt;!DOCTYPE html&gt;
&lt;html xmlns="http://www.w3.org/1999/xhtml" dir="ltr" lang="pt-BR"&gt;
&lt;head profile="http://gmpg.org/xfn/11"&gt;
&lt;meta charset="&lt;?php bloginfo( 'charset' ); ?&gt;" /&gt;
&lt;title&gt;&lt;?php bloginfo('name'); ?&gt;&lt;?php wp_title('|'); ?&gt;&lt;/title&gt;
&lt;link rel="stylesheet" type="text/css" href="&lt;?php bloginfo( 'stylesheet_url' ); ?&gt;" /&gt; 
&lt;link rel="pingback" href="&lt;?php bloginfo( 'pingback_url' ); ?&gt;" /&gt; 
&lt;link rel="alternate" type="application/rss+xml" title="&lt;?php bloginfo('title');?&gt; RSS Feed" href="&lt;?php bloginfo('rss2_url'); ?&gt;" /&gt;
&lt;!-- Se voc&ecirc; for usar coment&aacute;rio no seu tema, deixe isso! --&gt;
&lt;?php if ( is_singular() && get_option( 'thread_comments' ) ) wp_enqueue_script( 'comment-reply' );?&gt;
&lt;!-- Se voc&ecirc; for usar coment&aacute;rio no seu tema, deixe isso! --&gt;
&lt;?php
//Sempre deixa essa fun&ccedil;&atilde;o wp_head(); pois alguns plugins utilizam dela para retornar informa&ccedil;&atilde;o 
wp_head(); 
?&gt; 
&lt;/head&gt;
&lt;body &lt;?php body_class(); ?&gt;&gt;
&lt;div id="main"&gt;
&lt;header&gt;
&lt;section id="logo"&gt;
&lt;h2&gt;&lt;a href="&lt;?php bloginfo('url'); ?&gt;" title="&lt;?php bloginfo('title'); ?&gt;"&gt;&lt;span&gt;&lt;/span&gt;&lt;?php bloginfo('title'); ?&gt; - &lt;?php bloginfo('description'); ?&gt;&lt;/a&gt;&lt;/h2&gt;
&lt;/section&gt;
&lt;?php 
//Fun&ccedil;&atilde;o para retornar o menu
wp_nav_menu(array(
'menu' =&gt; 'menu_principal',
'theme_location' =&gt; 'menu_principal',
'echo' =&gt; true,
'container' =&gt; 'nav',
'container_id' =&gt; 'menu' 
));
?&gt;
&lt;/header&gt; 
&lt;div id="container"&gt;
</pre>

Estudem essas funções: [bloginfo()][4], [wp_title()][5], [wp_head()][6] e [wp_footer()][7].

**wp\_nav\_menu,** WTF??? O que é isso, Paulo? Calma, é uma função para retornar menus, confira esse artigo de [criação de menus no WordPress][8], que aí tenho certeza que vai entender tudo.

Personalize essas páginas através do seu front-end, tente explorar o máximo dessas páginas para não perder tempo nas páginas internas.

Finalizando esse inicio, o esqueleto do seu tema está pronto!

### Trabalhando com a página inicial e páginas internas

Beleza, concluímos nosso “esqueleto”, e a partir daí vamos criar as páginas do tema. A página índex.php é a página inicial do tema, ela só não é a página inicial, quando adicionamos ao nosso tema a pagina home.php. Mas de inicio, vamos trabalhar com a página índex.php.

Já ouviram falar no **Loop do WordPress**? Confiram esse [artigo][9] pois vão entender para o que ela serve.

Vamos ao exemplo da página inicial:

<img src="http://tableless.com.br/uploads/2011/12/conteudo.jpg" alt="Conteudo para tema no WordPress" width="600" height="578" class="alignnone size-full wp-image-5034" srcset="uploads/2011/12/conteudo.jpg 1000w, uploads/2011/12/conteudo-300x289.jpg 300w" sizes="(max-width: 600px) 100vw, 600px" />

<pre class="lang-php">&lt;?php get_header(); ?&gt;
&lt;div id="blog"&gt;
&lt;?php while (have_posts()) : the_post(); ?&gt; 
&lt;section class="post"&gt; 
&lt;h1 class="title-post"&gt;&lt;a href="&lt;?php the_permalink(); ?&gt;" title="&lt;?php the_title(); ?&gt;"&gt;&lt;?php the_title(); ?&gt;&lt;/a&gt;&lt;/h1&gt;
&lt;p&gt;Postado: &lt;?php the_time('F j, Y'); ?&gt; at &lt;?php the_time('g:i a'); ?&gt;&lt;/p&gt;
&lt;?php the_post_thumbnail(); ?&gt;
&lt;?php the_content(); ?&gt; 
&lt;/section&gt;
&lt;?php endwhile; ?&gt;
&lt;/div&gt;
&lt;?php get_sidebar(); ?&gt;
&lt;?php get_footer(); ?&gt;</pre>

Estude a função [the_time()][10] e a forma de [customizar data e hora dessa função][11].

A função **the\_post\_thumbnail** serve para retornar os [Posts Thumbnails][12], Caso não tenha interesse, pode remover a função, mas se tiver interesse, aprenda através [desse artigo][13].

A função get_sidebar() serve para retornar o que está no arquivo sidebar.php, e esclareça suas dúvidas [nesse artigo][14] para criação de sidebars

Arquivo **sidebar.php**

<pre class="lang-html">&lt;div id="sidebar"&gt;
&lt;ul class="sidebar"&gt;
&lt;?php if(!function_exists('dynamic_sidebar') || !dynamic_sidebar("Blog Sidebar")); ?&gt;
&lt;/ul&gt;
&lt;/div&gt;</pre>

Não se limite a esse artigo, aprofunde seu conhecimento através da [documentação disponibilizada pelo WordPress][15]. **“Futuque”** novas funções, pois é assim que se aprende, é quebrando a cara e arriscando. Basta somente ter interesse!

Esperem pelas próximas partes deste artigo, pois vou aprofundar mais esse assunto e pensar no WordPress como um poderoso CMS.

Quero deixar o espaço sempre aberto para quem tiver dúvidas, dar sugestões, criticas construtivas, ect. Podem comentar, enviar email e encher o fórum do Tableless, pois de lá nasceu a idéia para esse artigo e tenho certeza que nascerá os próximos também.

 [1]: http://tableless.com.br/forum/discussion/55/customizacao-tema-wordpress
 [2]: http://tableless.com.br/forum/profile/375/angelolucas
 [3]: http://tableless.com.br/uploads/2011/12/header-para-desenvolvimento-wordpress.jpg
 [4]: http://codex.wordpress.org/pt-br:Template_Tags/bloginfo
 [5]: http://codex.wordpress.org/Function_Reference/wp_title
 [6]: http://codex.wordpress.org/Function_Reference/wp_head
 [7]: http://codex.wordpress.org/Function_Reference/wp_footer
 [8]: http://tableless.com.br/criando-menus-no-wordpress/
 [9]: http://tableless.com.br/o-loop-do-wordpress/
 [10]: http://codex.wordpress.org/Function_Reference/the_time
 [11]: http://codex.wordpress.org/pt-br:Formatando_Data_e_Hora
 [12]: http://codex.wordpress.org/Post_Thumbnails
 [13]: http://tableless.com.br/adicionando-post-thumbnail/
 [14]: http://tableless.com.br/criando-sidebar-dinamica-no-wordpress/
 [15]: http://codex.wordpress.org/Template_Tags