---
title: Templates no Hugo - Entendendo o básico do range
authors: Diego Eis
type: post
publishdate: 2018-01-29
date: 2018-01-29
image: https://i.imgur.com/9z3fw2C.jpg
excerpt: Entenda como interar nas arrays do Hugo
categories:
  - Hugo
  - jamstack
  - Wordpress
  - CMS
tags:
  - Hugo
  - jamstack
  - Wordpress
  - CMS
---

Do mesmo jeito que [o Wordpress tem seus Loops](https://tableless.com.br/o-loop-do-wordpress/), onde você mostra uma listagem de informações, o Hugo usa um comando chamado `range`, que itera em uma array e mostra a listagem na tela. A sintaxe é bem simples:

```
{{ range array }}
  {{ . }}
{{ end }}
```

Lembrando que o Hugo é um gerador de páginas estáticas baseada em Golang. Logo, o `range` é [um comando da linguagem Go](https://gobyexample.com/range), do mesmo jeito que o Loop do Wordpress é o comando `while` do PHP. Se você não manja nada de programação, não se preocupe, apenas foque de que para você mostrar uma lista de coisas na tela, você vai usar o comando `range`.

Bom, sabendo que o `range` vai te listar as coisas, você precisa saber o que listar. Vamos começar mostrando uma listagem de posts/páginas. O Hugo guarda as páginas numa coleção chamada `.Pages`. O exemplo abaixo vai te trazer a lista de todas as páginas do site:

```
{{ range .Pages }}
  {{ . }} <br>
{{ end }}
```

O resultado é algo mais ou menos assim:

```
Page("Templates no Hugo - Entendendo o básico do range")
Page("Crud\u00a0com Node.js e MongoDB (Express + Mongoose) na KingHost")
Page("Gerenciando aplicações Node.js com PM2")
Page("Os textos mais acessados no Tableless em 2017")
Page("Dicas de front-end para designers")
Page("Salesforce Lightning Design System")
Page("Utilizando Fragment no React")
```

Veja que o `{{ . }}` é o que chamamos de **contexto** no Hugo, ou **the dot** para os íntimos. Quando estamos mostrando uma coleção de informação, o `{{ . }}` se refere ao contexto atual daquele loop. Entenda que a informação que o `{{ . }}` vai mostrar depende do seu contexto, assim [como o `this` do JavaScript](https://tableless.com.br/javascript-entendendo-o-this/), dependendo do lugar que ele é usado, ele estará responsável por mostrar determinadas informações. Vale um outro post sobre isso, mas por agora, entenda que como o `{{ . }}` está dentro do loop de `.Pages`, o contexto é trabalhar com a coleção de páginas do site.

O `.Pages` tem algumas variáveis que podemos usar, o `.Title` é uma dessas variáveis e ela é responsável por mostrar o título da página:

```
{{ range .Pages }}
  {{ .Title }} <br>
{{ end }}
```

O resultado fica assim:

```
Templates no Hugo - Entendendo o básico do range
Crud com Node.js e MongoDB (Express + Mongoose) na KingHost
Gerenciando aplicações Node.js com PM2
Os textos mais acessados no Tableless em 2017
Dicas de front-end para designers
Salesforce Lightning Design System
Utilizando Fragment no React
```

Comparando com o Wordpress:

```
<?php while (have_posts()) : the_post(); ?>
  <?php the_title(); ?> <br>
<?php endwhile; ?>
```

## first e last

Agora imagine que você queira mostrar os primeiros posts mais atuais. O delimitador `first` vai cuidar disso para gente. Ele pega os **os primeiros resultados de uma coleção** e mostra para gente. Veja um exemplo abaixo:

```
{{ range first 10 .Pages }}
  {{ .Title }} <br>
{{ end }}
```

Se você pode mostrar os primeiro, você também pode mostrar os últimos:

```
{{ range last 10 .Pages }}
  {{ .Title }} <br>
{{ end }}
```

## where

Estamos listando até agora todas as páginas de um site. Se você está fazendo um blog ou algo que tenha **posts**, em algum momento você vai precisar listar apenas os posts/artigos do site, para tanto, você poderá usar o `where`, que vai filtrar as informações de uma listagem, para resultados que apenas contenham uma característica em comum. Veja:

```
{{range last 10 (where .Pages "Type" "post")(where .Params.categories "html") }}
  {{.Title }} <br>
{{end}}
```

Nesse caso, estamos mostrando as 10 páginas mais antigas, que sejam do tipo **post**.

Perceba que colocamos entre parênteses, que é para agruparmos o filtro. Se você não tivesse feito isso, o Hugo iria achar que o `where .Pages "Type" "post"` fizesse parte do comando `last` e não é. 

## Filtrando por Taxonomia

Você também pode mostrar apenas posts de uma determinada taxonomia. Taxonomia no Hugo é questão para outro artigo, mas imagine que taxonomias são formas para que você relacione conteúdo no Hugo. Uma forma de fazer isso em blogs são as **categorias**. Logo, você pode listar todas as páginas que estão dentro de uma determinada Taxonomia, no nosso caso, todos os posts de uma determinada categoria:

```
{{ range first 10 .Site.Taxonomies.categories.javascript }}
  {{ .Title }} <br>
{{ end }}
```

## Direto da documentação

Você pode se aprofundar melhor sobre o Range e algumas das coisas que falei aqui nos links abaixo:

1. [https://gohugo.io/variables/page/](https://gohugo.io/variables/page/)
1. [https://gohugo.io/functions/range/#readout](https://gohugo.io/functions/range/#readout)
1. [https://gohugo.io/functions/first/](https://gohugo.io/functions/first/)
1. [https://gohugo.io/functions/where/](https://gohugo.io/functions/where/)
1. [https://gohugo.io/templates/taxonomy-templates/](https://gohugo.io/templates/taxonomy-templates/)
1. [https://gohugo.io/content-management/taxonomies/](https://gohugo.io/content-management/taxonomies/)