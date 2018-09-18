---
title: WordPress Include Tags
authors: Diego Eis
type: post
date: 2008-07-06
url: /wordpress-include-tags/
categories:
  - cms
  - php
tags:
  - Wordpress
  - php
  - CSS
  - template
  - themes
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

 [1]: https://wordpress.org/
 [2]: https://tableless.com.br/wordpress