---
title: 'Sections: elemento article – Parte 4'
author: Diego Eis
type: post
date: 2010-10-25
excerpt: O elemento article define um bloco de informação, texto, comentários e etc. Ele é um elemento mais específico que o section ou que o div.
url: /section-elemento-article/
aktt_notify_twitter:
  - yes
tweetbackscheck:
  - 1356470903
shorturls:
  - 'a:3:{s:9:"permalink";s:48:"http://tableless.com.br/section-elemento-article";s:7:"tinyurl";s:26:"http://tinyurl.com/3msr8ps";s:4:"isgd";s:19:"http://is.gd/e7o2xV";}'
twittercomments:
  - 'a:6:{i:202779216335478787;s:7:"retweet";i:202771255529713666;s:7:"retweet";i:202771244641304577;s:7:"retweet";i:202769131785826304;s:7:"retweet";i:202768171176968192;s:7:"retweet";i:202760990826303489;s:7:"retweet";}'
tweetcount:
  - 11
dsq_thread_id: 503039677
categories:
  - Código
  - HTML5
tags:
  - 2010
  - desenvolvimento web
  - html5
  - padroes web
  - Semântica
  - tableless

---
Você deve marcar a área do conteúdo do seu site com um DIV com um ID do tipo: conteudo, texto, main, content e etc&#8230; Normalmente esta é uma área nobre. O Google e outros sistemas de busca não tem com saberem onde fica o bloco do texto principal do site. Não havia nenhuma indicação dizendo que determinado elemento é se trata do bloco que carrega a informação principal do site. O **article** surgiu para suprir essa necessidade.

### O que a especificação diz

> &#8220;The article element represents a component of a page that consists of a self-contained composition in a document, page, application, or site and that is intended to be independently distributable or reusable, e.g. in syndication. This could be a forum post, a magazine or newspaper article, a blog entry, a user-submitted comment, an interactive widget or gadget, or any other independent item of content.&#8221;

O elemento **article** representa uma seção de conteúdo do site, que forma uma parte independente do documento. Dentro do **article** você colocará uma post de blog, artigo, texto, posts em fóruns e etc. Você pode marcar os comentários de um blog com **article**. Todo o conteúdo do **article** pode ser reutilizado em feeds ou outros meios de &#8220;sindicação&#8221; (syndication).

O **article** pode conter uma estrutura como essa:
  
[cc lang=&#8221;html&#8221;]<article> <header> 

# Título do post

<time datetime="12-03-1983" pubdate="pubdate">03 de Dezembro de 1983</time>

Texto de introdução.</header> 

## Um outro título

Texto do post.

Texto do post.

Texto do post.</article> 

[/cc]

Veja que o **article** envolve tudo o que é relacionado ao conteúdo do post: data, introdução, título e etc. Você não precisa agregar tudo isso no **article** se não quiser.

### De olho na semântica

Alguns podem confundir os elementos de **article**, **section** e **div**. Entenda que o **article** é um elemento mais específico que o **section** e o **div**. O **article** indica que um determinado bloco leva um conteúdo importante. O **section** é apenas um bloco de separação de assuntos diferentes. O **div**, o mais genérico de todos apenas é aplicado para separar elementos em blocos, por isso ele não carrega nenhum significado semântico. Para entender melhor:

  * Para informação e conteúdo que fará sentido se visto fora do seu site como em leitores de RSS ou outros meios, utilize o **article**.
  * Para separar e organizar conteúdos de diversos assuntos em blocos diferentes, utilize o **section**.
  * Para utilização não semântica, detalhes genéricos e etc, utilize **div**.