---
title: WordPress Include Tags
author: Diego Eis
type: post
date: 2008-07-06
url: /wordpress-include-tags/
tweetbackscheck:
  - 1356393097
shorturls:
  - 'a:3:{s:9:"permalink";s:46:"http://tableless.com.br/wordpress-include-tags";s:7:"tinyurl";s:26:"http://tinyurl.com/3blm938";s:4:"isgd";s:19:"http://is.gd/KilJqu";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 503038324
categories:
  - Técnicas e Práticas
  - Wordpress
tags:
  - CSS
  - desenvolvimento
  - Na Prática
  - php
  - template
  - themes
  - Wordpress
  - xhtml

---
O [WordPress][1] tem 3 TemplatesTags para incluir elementos básicos de Cabeçalho, Coluna lateral (sidebar) e Rodapé, são eles: get\_header(), get\_sidebar() e get_footer(). Essas TemplateTags não aceitam qualquer tipo de parâmetro, portanto são simples de se aplicar. Em todos os themes do WordPress, essas 3 TemplateTags estão sempre presentes, mesmo assim, você pode modificar isso incluindo outro arquivo que não seja o padrão que o WP estabeleceu.
  
<!--more-->

### get_header()

O **<?php get_header(); ?>**inclui em seu template o arquivo header.php, que é onde vai o cabeçalho do seu site. É lá onde vai o começo da estrutura básica do HTML &#8211; Doctype, html, head, title, metatags e body.

### get_sidebar()

O **<?php get_sidebar(); ?>** é a função que incluirá em seu template a sua coluna lateral. Menu lateral, banners, informações e tudo o que normalmente vai em um sidebar.

### get_footer()

O **<?php get_footer(); ?>** inclui em seu template o arquivo footer.php. É lá onde você normalmente termina seu . É neste arquivo que você terá o código do rodapé e de elementos que sempre seguirão o final da página.

Se o WordPress não encontrar, por exemplo o arquivo footer.php, ele irá incluir o arquivo relacionado do theme default: wp-content/themes/default/footer.php. O mesmo acontece para o sidebar.php, o header.php e o comments_template().

### Incluindo qualquer arquivo

Claro que você vai querer incluir outros arquivos. Por exemplo, caso seu site tiver duas colunas, ou o seu cabeçalho for muito grande e você quiser inserir os elementos em arquivos separados. Nestes casos você pode utilizar esse código:

`<?php include (TEMPLATEPATH . '/header2.php'); ?>`

O WordPress vai inserir o arquivo pedido como um include PHP normal.

Quer saber mais sobre WordPress? [Fique antenado aqui][2]!

 [1]: http://wordpress.org/
 [2]: http://tableless.com.br/wordpress