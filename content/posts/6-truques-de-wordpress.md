---
title: 6 truques básicos do functions.php do WordPress
author: Diego Eis
type: post
date: 2014-04-22
excerpt: Alguns truques para personalizar e melhorar o functions.php do seu tema.
url: /6-truques-de-wordpress/
dsq_thread_id: 2630396166
categories:
  - Wordpress
tags:
  - functions
  - truques
  - Wordpress

---
O **functions.php** é o arquivo de funções do seu tema. É nele que você habilita os menus, cria widgets e define uma série de configurações dos temas de WordPress. Essas são 5 pequenos truques que uso nos meus projetos em WordPress.

## Como tirar a barra de admin

Eu odeio aquela barra de administração que o WordPress coloca no site quando estamos logados. Eles atrapalham muitas vezes o desenvolvimento do projeto, por isso enquanto estou desenvolvendo, eu desabilito essa feature. Para fazer isso basta inserir uma linha no functions.php:

<pre class="lang-php">add_filter('show_admin_bar', '__return_false');
</pre>

## Atualizando o WordPress sem necessidade de FTP

Com apenas um clique você consegue atualizar seu WordPress pela própria interface administrativa. Basta clicar um botão e pronto. Eu geralmente atualizo o WordPress localmente, comito via git e depois atualizo os arquivos no server.

Geralmente, por motivos de segurança, quando o WordPress é atualizado pela interface administrativa, ele pede as informações de FTP. Como não tenho FTP instalado nem no server, nem local, eu desabilito essa parte. Para isso, uso a linha abaixo:

<pre class="lang-php">define('FS_METHOD','direct');
</pre>

## Definindo o tamanho padrão das imagens

Quando você sobe uma imagem no WordPress, por padrão ele salva algumas imagens em tamanhos específicos. Isso é bom porque você pode usar imagens menores quando necessário em vez de usar no tamanho original. Por isso é bom que você configure o tamanho das imagens geradas de acordo com o seu layout.

<pre class="lang-php">if ( function_exists( 'add_theme_support' ) ) {
	add_theme_support( 'post-thumbnails' );
	set_post_thumbnail_size( 650, 250, true ); // Tamanho da largura das imagens.
}
</pre>

## Adicionando EXCERPT nas páginas do WordPress

No WordPress há duas maneiras de cadastrar textos: usando páginas ou posts. Páginas contém textos mais estáticos, que vão mudar pouco. Os posts tem uma ordem cronológica, indicam novidades e etc. Os Excerpts são os resumos que fazem a introdução exclusivamente de posts. Mas as vezes, em alguns projetos, precisamos usar em Páginas também. Essa linha habilita o uso de excerpts em páginas:

<pre class="lang-php">add_post_type_support( 'page', 'excerpt' );
</pre>

## Retirando a metatag WordPress Generator

Geralmente o WordPress coloca uma metatag indicando que o site foi gerado com WordPress e também qual a versão do CMS. 

<pre class="lang-html">&lt;meta name="generator" content="WordPress 3.2.1"&gt;
</pre>

Eu, particularmente, não preciso disso, bem como muitos sites por aí. Essa linha retira a metatag.

<pre class="lang-php">remove_action('wp_head', 'wp_generator');
</pre>

## Inserindo a imagem de destaque para o FEED

No WordPress há como definir uma imagem de destaque para os posts. Essa imagem, por padrão, não é inserida quando os leitores leem o post via feed. Para habilitar isso, basta inserir as linhas abaixo:

<pre class="lang-php">add_filter('the_content_feed', 'rss_post_thumbnail');
function rss_post_thumbnail($content) {
	global $post;
	if( has_post_thumbnail($post->ID) )
		$content = '&lt;p&gt;' . get_the_post_thumbnail($post->ID, 'thumbnail') . '&lt;/p&gt;' . $content;
	return $content;
}
</pre>

E pronto. 😉