---
title: Hierarquia de arquivos do WordPress
author: Diego Eis
type: post
date: 2009-04-08
excerpt: O Wordpress utiliza uma hierarquia de arquivos para a criação de themes. Para criar bons sites e blogs baseados em Wordpress, é importante que você entenda essa hierarquia.
url: /hierarquia-de-arquivos-do-wordpress/
aktt_notify_twitter:
  - no
tweetbackscheck:
  - 1356425990
shorturls:
  - 'a:3:{s:9:"permalink";s:59:"http://tableless.com.br/hierarquia-de-arquivos-do-wordpress";s:7:"tinyurl";s:26:"http://tinyurl.com/3j7m5qr";s:4:"isgd";s:19:"http://is.gd/0tzn55";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 503039009
categories:
  - Técnicas e Práticas
  - Wordpress
tags:
  - CSS
  - html
  - Na Prática
  - Wordpress

---
Para criar um bom theme para WordPress, você precisa conhecer bem a estrutura de arquivos que são utilizados no construir estes themes. São usados vários arquivos que setorizam as várias funcionalidades do blog ou site. Veja abaixo arquivos que são normalmente utilizados:

  * Página de Erro 404 &#8211; **404.php**
  * Histórico e Arquivo &#8211; **archive.php**
  * Index de Histórico e Arquivo &#8211; **archives.php**
  * Página de uma Categoria &#8211; **category.php**
  * Comentários &#8211; **comments.php**
  * Rodapé &#8211; **footer.php**
  * Cabeçalho &#8211; **header.php**
  * Links &#8211; **links.php**
  * Home e Principal &#8211; **index.php**
  * Páginas &#8211; **page.php**
  * Post &#8211; **single.php**
  * Formulário de busca &#8211; **searchform.php**
  * Resultados de busca &#8211; **search.php**
  * Sidebar &#8211; **sidebar.php**
  * Stylesheet &#8211; **style.css** 

O WordPress usa as [Query String][1] de cada link do seu site para saber qual arquivo ele deve mostrar na página. Ele decide qual tipo de página será requisitada &#8211; uma página de busca, categoria, a home etc.
  
Ele procura esses arquivo dentro do diretório do seu template. Caso o WP não encontre o arquivo requisitado, ele escolhe o template padrão do index.php para ser usado. Há uma hierarquia de arquivos de template que o WordPress irá requisitar caso ele não encontre o correto.

Por exemplo: imagine que seu visitante clique em um link de seu site que o leve para dentro de uma categoria. O WordPress irá procurar o arquivo referente a categoria personalizada. Suponha que o ID da categoria seja 40, ele procuraria o arquivo _category-40.php_, que é o arquivo que personaliza a página desta categoria. Caso ele não o encontre, o WordPress procura pelo arquivo genérico que gera as páginas de categorias, no caso o _category.php_. Contudo, se ele não encontrá-lo também, ele procurará o _archive.php_ que é o documento que gera as páginas de históricos e arquivos. Caso ele também não o encontre, ele irá utilizar o arquivo principal _index.php_
  
Assim, seu sistema/blog/site não fica com erros por não encontrar um determinado documento.

Abaixo segue a hierarquia de alguns arquivos. Você pode ver muito mais [detalhes aqui][2].

##### Home Page

  1. home.php
  2. index.php 

##### Visualizando o post

  1. single.php
  2. index.php

##### Páginas 

  1. nomedapagina.php &#8211; Seria um arquivo para uma página especifica personalizada
  2. page.php
  3. index.php 

##### Category display

  1. category-id.php &#8211; Categoria específica, onde o ID é o número de identificação da categoria
  2. category.php
  3. archive.php
  4. index.php 

##### Histórico

  1. date.php
  2. archive.php
  3. index.php 

##### Tag

  1. tagslug.php &#8211; Arquivo personalizado para uma tag específica
  2. tag.php
  3. archive.php
  4. index.php 

##### 404

  1. 404.php
  2. index.phpc

Na documentação do WordPress há [um diagrama muito esclarecedor][3]:
  
[<img src="http://tableless.com.br/uploads/2009/04/template_hierarchy-300x238.png" alt="template_hierarchy" title="template_hierarchy" width="300" height="238" class="alignnone size-medium wp-image-1311" srcset="uploads/2009/04/template_hierarchy-300x238.png 300w, uploads/2009/04/template_hierarchy.png 880w" sizes="(max-width: 300px) 100vw, 300px" />][4]

Muitos desenvolvedores por aí, aconselham que você comece seu theme a partir de um já pronto. Eu já vou além e sugiro que você comece fazendo os arquivos à medida em que for precisando dos arquivos. Assim você **evita grandes quantidade de documentos inúteis** na pasta do seu template. Isso é muito importante caso você esteja fazendo um site, por exemplo. Quanto mais organizado e menor a quantidade de arquivos, melhor. Mesmo assim, não atole todas as funções no _index.php_. Divida cuidadosamente as seções do site para não haver confusão em apenas um arquivo.

É possível saber quais os arquivos você precisará utilizar em seu template logo quando recebemos os documentos em HTML. Você pode utilizá-los como base para a criação dos arquivos dos templates. É a melhor maneira de começar criando um theme do zero. 

No site do [WordPress][5] há outras muitas [informações importantes sobre a Hierearquia dos Arquivos][6].

 [1]: http://codex.wordpress.org/Glossary#Query_string
 [2]: http://codex.wordpress.org/Template_Hierarchy "Hierarquia de arquivo do WordPress - Em inglês"
 [3]: http://codex.wordpress.org/images/1/18/Template_Hierarchy.png
 [4]: http://tableless.com.br/uploads/2009/04/template_hierarchy.png
 [5]: http://tableless.com.br/categoria/wordpress "Artigos sobre WordPress"
 [6]: http://codex.wordpress.org/Template_Hierarchy