---
title: 'Front-end e WordPress: uma relação de amor e amizade'
author: Italo Góis
type: post
date: 2015-05-28
excerpt: Conheça os tópicos mais comuns sobre a sintaxe de funcionamento do Wordpress, o CMS que ajuda desenvolvedores front-end a criarem sites mesmo sem o conhecimento de linguagens de programação.
url: /front-end-e-wordpress-uma-relacao-de-amor-e-amizade/
categories:
  - CMS
  - O Básico
  - Wordpress
tags:
  - cms
  - front-end
  - Wordpress

---
É&nbsp;bastante comum o&nbsp;desenvolvedor front-end conseguir trabalho como freelancer e precisar do desenvolvedor back-end para tornar&nbsp;o site dinâmico. O&nbsp;cliente fica&nbsp;feliz,&nbsp;pois de forma rápida, ele consegue criar novas páginas, postagens, atualizando por conta própria o conteúdo. Mas atualmente, o&nbsp;front-end não precisa mais desta dependência:&nbsp;ele pode usar o WordPress.

Ok, mas o WordPress usa PHP, uma&nbsp;linguagem back-end, correto?

Sim, mas isto não é impede de tornar a ferramenta facilmente configurável, mesmo que você não entenda de linguagens de programação.

O objetivo deste post não é oferecer&nbsp;um conhecimento da linguagem, mas levantar os tópicos mais comuns sobre a&nbsp;sintaxe de funcionamento da ferramenta.

## O WordPress

O WordPress foi criado para ser usado como uma plataforma de criação e administração de blogs, mas hoje ele evoluiu bastante,&nbsp;e&nbsp;tornou-se um grande CMS (gerenciador de conteúdo), que é utilizado para criar sites dos mais simples aos mais complexos.

<a href="https://wordpress.org/showcase/" target="_blank">Confira o showcase</a> que mostra grandes sites que foram criados com o uso deste CMS.

## A Hierarquia

Para transformar seu site HTML em um tema, é necessário conhecer a <a href="http://tableless.com.br/hierarquia-de-arquivos-do-wordpress/" target="_blank">hierarquia de arquivos do WordPress</a>.

## A Simplicidade

Como dito anteriormente, não é necessário ter conhecimentos avançados em PHP. O WordPress possui muitas funções nativas, como por exemplo, buscar&nbsp;o título da página, criar queries personalizadas, acessar informações de usuários, entre outras.

Tais funções nativas evitam o desperdício de tempo e raciocínio, pois muito delas foram confeccionadas para atender as mais comuns&nbsp;utilidades assim como os casos mais específicos.

Veja o exemplo de algumas delas:

  * **the_title()**Retorna o título da página ou do post;
  * **the_excerpt()**Traz o resumo do post e da página;
  * **the_content()**Traz o conteúdo completo da página ou do post;
  * **the_category()**Traz todas as categorias de um determinado post;
  * **single\_cat\_title()**Traz o nome da categoria.

[Aqui tem&nbsp;uma lista com todas as funções do WordPress][1].

## E o banco de dados?

O WordPress já vem com a configuração do banco de dados.&nbsp;Basta conhecer como funciona a função **WP_Query()** e passar através de um&nbsp;parâmetro o que você deseja&nbsp;acessar.&nbsp;Como este é um post para&nbsp;iniciantes&nbsp;em&nbsp;Wordpress, é possível criar de forma rápida _queries_, _posts types_ e outras funcionalidades para que o tema funcione corretamente utilizando&nbsp;o site [GenerateWP][2]. Com ele você pode gerar&nbsp;funcionalidades como: _shortcodes_, _sidebars_, posições de menu, entre outras.

## Custom Post Type, o que é isso?

**Custom Post Type** é uma maneira de criar conteúdos personalizados para o seu site. Exemplo: o WordPress possui os _custons&nbsp;post types &nbsp;_**Post** e **Page**, mas você pode criar um _post type_ chamado Portfólio, Filmes, Imóveis, etc.

Nestes _posts types_ também é possível criar campos personalizados. Para saber mais sobre Posts Types confira este artigo do Paulo Rodrigues [Custom Post Types WordPress][3]

 [1]: https://codex.wordpress.org/Function_Reference
 [2]: http://generatewp.com/
 [3]: http://tableless.com.br/custom-post-types-wordpress/