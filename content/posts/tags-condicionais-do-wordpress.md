---
title: Tags Condicionais do WordPress
authors: Paulo Rodrigues
type: post
date: 2011-04-12
excerpt: As Tags Condicionais são usadas para manipular o conteúdo exibido ou especificar informações na página
url: /tags-condicionais-do-wordpress/
categories:
  - cms
tags:
  - 2011
  - Wordpress

---
As Tags Condicionais são funções próprias do WordPress capazes de manipular todo o conteúdo de sua página. Com elas, você ganha aquele tempo que iria perder criando aquelas condições para retornar seus valores de maneira personalizada. Geralmente retornam o valor em Booleano, ou seja, TRUE (verdadeiro) ou FALSE (falso).

### Como usar?

[cce lang=&#8221;php&#8221;]
  
<?php
	if(tag_condicional()){
		//se verdadeiro, retorne isso
	}else{
		//se falso, retorne isso
	}
?>


  
[/cce]

Tags que podem receber parâmetros dentro de sua função, ex:

[cce lang=&#8221;php&#8221;]
  
<?php
	if(tag_condicional(‘valor’)){
		//se verdadeiro, retorne isso
	}else{
		//se falso, retorne isso
	}
?>


  
[/cce]

A tabela abaixo que encontrei no livro WordPress 3, é basicamente um mini-guia das tags que precisam de parâmetros e das que não precisam.

<table summary="Guia básico de Tags Condicionais" style="width: 90%;text-align: center">
  <tr>
    <th>
      Condicional
    </th>
    
    <th>
      ID
    </th>
    
    <th>
      Slug
    </th>
    
    <th>
      Título
    </th>
    
    <th>
      Array
    </th>
    
    <th>
      Outro
    </th>
  </tr>
  
  <tr>
    <td style="font-weight: bold">
      is_single
    </td>
    
    <td>
      X
    </td>
    
    <td>
      X
    </td>
    
    <td>
      X
    </td>
    
    <td>
      X
    </td>
    
    <td>
    </td>
  </tr>
  
  <tr>
    <td style="font-weight: bold">
      is_sticky
    </td>
    
    <td>
      X
    </td>
    
    <td>
    </td>
    
    <td>
    </td>
    
    <td>
    </td>
    
    <td>
    </td>
  </tr>
  
  <tr>
    <td style="font-weight: bold">
      is_page
    </td>
    
    <td>
      X
    </td>
    
    <td>
      X
    </td>
    
    <td>
    </td>
    
    <td>
    </td>
    
    <td>
    </td>
  </tr>
  
  <tr>
    <td style="font-weight: bold">
      is_page_template
    </td>
    
    <td>
    </td>
    
    <td>
    </td>
    
    <td>
    </td>
    
    <td>
    </td>
    
    <td>
      Nome do arquivo
    </td>
  </tr>
  
  <tr>
    <td style="font-weight: bold">
      is_category
    </td>
    
    <td>
      X
    </td>
    
    <td>
      X
    </td>
    
    <td>
      X
    </td>
    
    <td>
      X
    </td>
    
    <td>
    </td>
  </tr>
  
  <tr>
    <td style="font-weight: bold">
      in_category
    </td>
    
    <td>
      X
    </td>
    
    <td>
      X
    </td>
    
    <td>
      X
    </td>
    
    <td>
      X
    </td>
    
    <td>
    </td>
  </tr>
  
  <tr>
    <td style="font-weight: bold">
      is_tag
    </td>
    
    <td>
    </td>
    
    <td>
      X
    </td>
    
    <td>
      X
    </td>
    
    <td>
      X
    </td>
    
    <td>
    </td>
  </tr>
  
  <tr>
    <td style="font-weight: bold">
      has_tag
    </td>
    
    <td>
    </td>
    
    <td>
      X
    </td>
    
    <td>
      X
    </td>
    
    <td>
      X
    </td>
    
    <td>
    </td>
  </tr>
  
  <tr>
    <td style="font-weight: bold">
      is_tax
    </td>
    
    <td>
    </td>
    
    <td>
      X
    </td>
    
    <td>
      X
    </td>
    
    <td>
      X
    </td>
    
    <td>
    </td>
  </tr>
  
  <tr>
    <td style="font-weight: bold">
      is_author
    </td>
    
    <td>
      X
    </td>
    
    <td>
      Nome do usuário
    </td>
    
    <td>
      Nickname
    </td>
    
    <td>
      X
    </td>
    
    <td>
    </td>
  </tr>
  
  <tr>
    <td style="font-weight: bold">
      has_excerpt
    </td>
    
    <td>
      X
    </td>
    
    <td>
    </td>
    
    <td>
    </td>
    
    <td>
    </td>
    
    <td>
    </td>
  </tr>
  
  <tr>
    <th colspan="6">
      As tags seguintes não aceitam argumentos; elas são verdadeiras se o modelo de arquivo correspondente está sendo usado para exibir a página atual.
    </th>
  </tr>
  
  <tr>
    <td>
      is_home
    </td>
    
    <td>
      is_search
    </td>
    
    <td>
      is_day
    </td>
    
    <td>
      is_feed
    </td>
    
    <td>
      is_404
    </td>
    
    <td>
      is_comments_popup
    </td>
  </tr>
  
  <tr>
    <td>
      is_front_page
    </td>
    
    <td>
      is_time
    </td>
    
    <td>
      is_month
    </td>
    
    <td>
      is_attachment
    </td>
    
    <td>
      is_trackback
    </td>
    
    <td>
      is_active_sidebar
    </td>
  </tr>
  
  <tr>
    <td>
      is_archive
    </td>
    
    <td>
      is_date
    </td>
    
    <td>
      is_year
    </td>
    
    <td>
      is_singular
    </td>
    
    <td>
      is_preview
    </td>
    
    <td>
      is_admin
    </td>
  </tr>
  
  <tr>
    <th colspan="6">
      As tags seguintes não aceitam argumentos. Elas retornam informações sobre a página que está sendo visualizada.
    </th>
  </tr>
  
  <tr>
    <td>
      comments_open
    </td>
    
    <td>
      pings_open
    </td>
    
    <td>
      is_paged
    </td>
    
    <td>
      in_the_loop
    </td>
  </tr>
</table>

Para melhorar o conteúdo e o aprendizado, criei um <a href="https://tableless.github.com/exemplos/guia-tags-condicionais-wp/index.html" title="Guia de Referência das Tags Condicionais do WordPress" rel="external">Guia de Referência das Tags Condicionais do WordPress</a>.