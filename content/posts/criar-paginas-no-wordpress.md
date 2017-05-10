---
title: Criar páginas no WordPress
author: Pedro Rogério
type: post
date: 2008-08-26
url: /criar-paginas-no-wordpress/
aktt_tweeted:
  - 1
tweetbackscheck:
  - 1356396382
shorturls:
  - 'a:3:{s:9:"permalink";s:50:"http://tableless.com.br/criar-paginas-no-wordpress";s:7:"tinyurl";s:26:"http://tinyurl.com/3ruo3ca";s:4:"isgd";s:19:"http://is.gd/m4cqKS";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 503038418
categories:
  - Artigos
  - Técnicas e Práticas
  - Wordpress
tags:
  - Wordpress

---
O WordPress permite total controle sobre a criação de conteúdo, inclusive a criação de novas páginas.

Para termos acesso a esse recurso, utilizamos o método <a title="wp_list_pages ()" rel="external" href="http://codex.wordpress.org/Template_Tags/wp_list_pages">wp_list_pages ()</a>, método pelo qual, após a criação das páginas, elas são mostradas automaticamente no seu site, pois a grande maioria dos templates para WordPress já vem com essa função, que fica localizada no arquivo header.php do tema do WordPress, gerando uma lista de páginas semelhante a essa:

<!--more-->


  
 `O WordPress permite total controle sobre a criação de conteúdo, inclusive a criação de novas páginas.

Para termos acesso a esse recurso, utilizamos o método <a title="wp_list_pages ()" rel="external" href="http://codex.wordpress.org/Template_Tags/wp_list_pages">wp_list_pages ()</a>, método pelo qual, após a criação das páginas, elas são mostradas automaticamente no seu site, pois a grande maioria dos templates para WordPress já vem com essa função, que fica localizada no arquivo header.php do tema do WordPress, gerando uma lista de páginas semelhante a essa:

<!--more-->


  
` 

Após as páginas serem criadas, você pode ocultar certas páginas para que elas não apareçam na navegação, mostrar páginas em um ordem diferente, tudo isso a partir da interface adiministrativa do WordPress.

### Ocultar páginas da navegação

Você não quer que a página Arquivos apareça em seu menu, para que isso aconteça, siga os seguintes passos:

  1. Vá até o administrativo de seu WordPress, entre em **Gerenciar > Páginas**.
  2. Você verá uma lista de todas as páginas criadas.
  3. Aqui precisamos pegar o ID de cada página para podermos ocultá-las posteriormente.
  4. Coloque o mouse sobre o nome da página e você observará na URL, semelhante a essa: **http://seusite.com.br/wp-admin/page.php?action=edit&post=4**, que o número que vem após o &post= é o ID da página, nessa URL seria o ID 4.
  5. Agora devemos modificar o método <a title="wp_list_pages ()" rel="external" href="http://codex.wordpress.org/Template_Tags/wp_list_pages">wp_list_pages ()</a> no arquivo header.php do seu tema WordPress. Para evitar problemas futuros, efetue um backup do arquivo para segurança.
  6. Abra o arquivo, procure por wp\_list\_pages().
  7. Adicione o arqumento: “exclude=4″.

``O WordPress permite total controle sobre a criação de conteúdo, inclusive a criação de novas páginas.

Para termos acesso a esse recurso, utilizamos o método <a title="wp_list_pages ()" rel="external" href="http://codex.wordpress.org/Template_Tags/wp_list_pages">wp_list_pages ()</a>, método pelo qual, após a criação das páginas, elas são mostradas automaticamente no seu site, pois a grande maioria dos templates para WordPress já vem com essa função, que fica localizada no arquivo header.php do tema do WordPress, gerando uma lista de páginas semelhante a essa:

<!--more-->


  
 `O WordPress permite total controle sobre a criação de conteúdo, inclusive a criação de novas páginas.

Para termos acesso a esse recurso, utilizamos o método <a title="wp_list_pages ()" rel="external" href="http://codex.wordpress.org/Template_Tags/wp_list_pages">wp_list_pages ()</a>, método pelo qual, após a criação das páginas, elas são mostradas automaticamente no seu site, pois a grande maioria dos templates para WordPress já vem com essa função, que fica localizada no arquivo header.php do tema do WordPress, gerando uma lista de páginas semelhante a essa:

<!--more-->


  
` 

Após as páginas serem criadas, você pode ocultar certas páginas para que elas não apareçam na navegação, mostrar páginas em um ordem diferente, tudo isso a partir da interface adiministrativa do WordPress.

### Ocultar páginas da navegação

Você não quer que a página Arquivos apareça em seu menu, para que isso aconteça, siga os seguintes passos:

  1. Vá até o administrativo de seu WordPress, entre em **Gerenciar > Páginas**.
  2. Você verá uma lista de todas as páginas criadas.
  3. Aqui precisamos pegar o ID de cada página para podermos ocultá-las posteriormente.
  4. Coloque o mouse sobre o nome da página e você observará na URL, semelhante a essa: **http://seusite.com.br/wp-admin/page.php?action=edit&post=4**, que o número que vem após o &post= é o ID da página, nessa URL seria o ID 4.
  5. Agora devemos modificar o método <a title="wp_list_pages ()" rel="external" href="http://codex.wordpress.org/Template_Tags/wp_list_pages">wp_list_pages ()</a> no arquivo header.php do seu tema WordPress. Para evitar problemas futuros, efetue um backup do arquivo para segurança.
  6. Abra o arquivo, procure por wp\_list\_pages().
  7. Adicione o arqumento: “exclude=4″.

`` 

Agora a página Arquivos não será mostrada no menu do seu site.

### Mostrar páginas em uma ordem diferente

No geral elas são ordenadas alfabeticamente, mas você pode indicar um número para alterar essa ordem:

  1. Vá até **Gerenciar > Páginas**.
  2. Escolha a página que deseja editar.
  3. Abaixo você verá: Ordem da página, no campo mostrado digite &#8220;1&#8221;.
  4. Agora devemos efetuar a alteração no arquivo header.php, passando o seguinte argumento no método wp\_list\_pages().

```O WordPress permite total controle sobre a criação de conteúdo, inclusive a criação de novas páginas.

Para termos acesso a esse recurso, utilizamos o método <a title="wp_list_pages ()" rel="external" href="http://codex.wordpress.org/Template_Tags/wp_list_pages">wp_list_pages ()</a>, método pelo qual, após a criação das páginas, elas são mostradas automaticamente no seu site, pois a grande maioria dos templates para WordPress já vem com essa função, que fica localizada no arquivo header.php do tema do WordPress, gerando uma lista de páginas semelhante a essa:

<!--more-->


  
 `O WordPress permite total controle sobre a criação de conteúdo, inclusive a criação de novas páginas.

Para termos acesso a esse recurso, utilizamos o método <a title="wp_list_pages ()" rel="external" href="http://codex.wordpress.org/Template_Tags/wp_list_pages">wp_list_pages ()</a>, método pelo qual, após a criação das páginas, elas são mostradas automaticamente no seu site, pois a grande maioria dos templates para WordPress já vem com essa função, que fica localizada no arquivo header.php do tema do WordPress, gerando uma lista de páginas semelhante a essa:

<!--more-->


  
` 

Após as páginas serem criadas, você pode ocultar certas páginas para que elas não apareçam na navegação, mostrar páginas em um ordem diferente, tudo isso a partir da interface adiministrativa do WordPress.

### Ocultar páginas da navegação

Você não quer que a página Arquivos apareça em seu menu, para que isso aconteça, siga os seguintes passos:

  1. Vá até o administrativo de seu WordPress, entre em **Gerenciar > Páginas**.
  2. Você verá uma lista de todas as páginas criadas.
  3. Aqui precisamos pegar o ID de cada página para podermos ocultá-las posteriormente.
  4. Coloque o mouse sobre o nome da página e você observará na URL, semelhante a essa: **http://seusite.com.br/wp-admin/page.php?action=edit&post=4**, que o número que vem após o &post= é o ID da página, nessa URL seria o ID 4.
  5. Agora devemos modificar o método <a title="wp_list_pages ()" rel="external" href="http://codex.wordpress.org/Template_Tags/wp_list_pages">wp_list_pages ()</a> no arquivo header.php do seu tema WordPress. Para evitar problemas futuros, efetue um backup do arquivo para segurança.
  6. Abra o arquivo, procure por wp\_list\_pages().
  7. Adicione o arqumento: “exclude=4″.

``O WordPress permite total controle sobre a criação de conteúdo, inclusive a criação de novas páginas.

Para termos acesso a esse recurso, utilizamos o método <a title="wp_list_pages ()" rel="external" href="http://codex.wordpress.org/Template_Tags/wp_list_pages">wp_list_pages ()</a>, método pelo qual, após a criação das páginas, elas são mostradas automaticamente no seu site, pois a grande maioria dos templates para WordPress já vem com essa função, que fica localizada no arquivo header.php do tema do WordPress, gerando uma lista de páginas semelhante a essa:

<!--more-->


  
 `O WordPress permite total controle sobre a criação de conteúdo, inclusive a criação de novas páginas.

Para termos acesso a esse recurso, utilizamos o método <a title="wp_list_pages ()" rel="external" href="http://codex.wordpress.org/Template_Tags/wp_list_pages">wp_list_pages ()</a>, método pelo qual, após a criação das páginas, elas são mostradas automaticamente no seu site, pois a grande maioria dos templates para WordPress já vem com essa função, que fica localizada no arquivo header.php do tema do WordPress, gerando uma lista de páginas semelhante a essa:

<!--more-->


  
` 

Após as páginas serem criadas, você pode ocultar certas páginas para que elas não apareçam na navegação, mostrar páginas em um ordem diferente, tudo isso a partir da interface adiministrativa do WordPress.

### Ocultar páginas da navegação

Você não quer que a página Arquivos apareça em seu menu, para que isso aconteça, siga os seguintes passos:

  1. Vá até o administrativo de seu WordPress, entre em **Gerenciar > Páginas**.
  2. Você verá uma lista de todas as páginas criadas.
  3. Aqui precisamos pegar o ID de cada página para podermos ocultá-las posteriormente.
  4. Coloque o mouse sobre o nome da página e você observará na URL, semelhante a essa: **http://seusite.com.br/wp-admin/page.php?action=edit&post=4**, que o número que vem após o &post= é o ID da página, nessa URL seria o ID 4.
  5. Agora devemos modificar o método <a title="wp_list_pages ()" rel="external" href="http://codex.wordpress.org/Template_Tags/wp_list_pages">wp_list_pages ()</a> no arquivo header.php do seu tema WordPress. Para evitar problemas futuros, efetue um backup do arquivo para segurança.
  6. Abra o arquivo, procure por wp\_list\_pages().
  7. Adicione o arqumento: “exclude=4″.

`` 

Agora a página Arquivos não será mostrada no menu do seu site.

### Mostrar páginas em uma ordem diferente

No geral elas são ordenadas alfabeticamente, mas você pode indicar um número para alterar essa ordem:

  1. Vá até **Gerenciar > Páginas**.
  2. Escolha a página que deseja editar.
  3. Abaixo você verá: Ordem da página, no campo mostrado digite &#8220;1&#8221;.
  4. Agora devemos efetuar a alteração no arquivo header.php, passando o seguinte argumento no método wp\_list\_pages().

``` 

Sua página a partir de agora será listada por essa ordem. Para alterar a ordem de outras páginas, basta seguir os passos e alterar a ordem como você quiser.

Se você quer saber mais sobre WordPress, [visite a seção exclusiva do Tableless][1].

 [1]: http://tableless.com.br/wordpress/