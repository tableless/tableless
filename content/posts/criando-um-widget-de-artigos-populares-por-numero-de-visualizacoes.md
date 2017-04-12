---
title: Criando um widget de “Artigos Populares” por numero de visualizações
author: Léo Juoli
type: post
date: 2015-08-13
url: /criando-um-widget-de-artigos-populares-por-numero-de-visualizacoes/
categories:
  - Wordpress
tags:
  - desenvolvimento web
  - tableless
  - tutorial
  - Wordpress

---
Recentemente tive que implementar um widget de artigos populares para um cliente. Acontece que até então a única maneira que eu sabia fazer isso era ordenando os posts por número de comentários. Propus a solução ao meu cliente e o mesmo disse que queria que o mesmo fosse ordenados por número de visualizações. Bom, nunca tinha feito isso, então corri atrás de alguns artigos &#8220;gringos&#8221; explicando como fazer e me espantei sobre como era simples.

Primeiro de tudo, precisamos encontrar uma maneira de registrar cada visita do artigo. Para que isso seja possível adicionamos esse código no **functions.php** do tema:

<pre class="lang-php">/* Populares */
function wpb_set_post_views($postID) {
$cookie = strtotime(date('Y-m-d'));
 $pv_url = 'wpmidia_'.md5($_SERVER['REQUEST_URI']);
 
 if( is_single() && !isset($_COOKIE[$pv_url]) ){
 $count_key = 'wpb_post_views_count';
 $count = get_post_meta($postID, $count_key, true);
 if($count==''){
 $count = 0;
 delete_post_meta($postID, $count_key);
 add_post_meta($postID, $count_key, '0');</pre>

<pre>setcookie($pv_url, $cookie, time()+3600, COOKIEPATH, COOKIE_DOMAIN, false); // 1 hora
 }else{
 $count++;
 update_post_meta($postID, $count_key, $count);
 setcookie($pv_url, $cookie, time()+3600, COOKIEPATH, COOKIE_DOMAIN, false); // 1 hora
 }
 }
}
//To keep the count accurate, lets get rid of prefetching
remove_action( 'wp_head', 'adjacent_posts_rel_link_wp_head', 10, 0);
function wpb_track_post_views ($post_id) {
 if ( !is_single() ) return;
 if ( empty ( $post_id) ) {
 global $post;
 $post_id = $post-&gt;ID; 
 }
 wpb_set_post_views($post_id);
}
add_action( 'wp_head', 'wpb_track_post_views');</pre>

A segunda função **wpb\_track\_post_views** vai basicamente chamar a primeira função toda vez que o tipo de página for &#8220;single&#8221;, ou seja, em todos os artigos. É essencial que seu template tenha a chamada `wp_head();` no header do tema. A primeira função vai registrar mais uma visualização do post em nosso banco de dados pela variável `$count_key`. Só que tem um pequeno problema que já contornamos no nosso código: toda vez que um usuário der refresh na página ele registraria mais uma visualização, isso faria com que usuários comuns conseguissem burlar, sem querer (ou por querer, sei lá), os posts. Como dito, conseguimos driblar isso, no código usamos o `setcookie` para criar um cookie no navegador e impedir que a função seja chamada nos próximos 3600 segundos ou 1 hora (você pode alterar se quiser).

Dito isso, não adiantaria nada se não pudêssemos chamar essa função. Para isso adicionamos mais um trecho no **functions.php** do tema:

<pre class="lang-php">function wpb_get_post_views($postID){
 $count_key = 'wpb_post_views_count';
 $count = get_post_meta($postID, $count_key, true);
 if($count==''){
 delete_post_meta($postID, $count_key);
 add_post_meta($postID, $count_key, '0');
 return "0 View";
 }
 return $count.' Views';
 }</pre>

A função acima serve também para retornar o numero de visualizações que o artigo teve, basta chama-la com wpb\_get\_post_views($id), sendo $id o ID do artigo.

Agora que implementamos todas as funções precisamos exibir isso em algum lugar e o código abaixo serve justamente para isso:

<pre class="lang-html">&lt;ul&gt;
 &lt;?php $popularpost = new WP_Query( array( 'posts_per_page' =&gt; 5, 'meta_key' =&gt; 'wpb_post_views_count', 'orderby' =&gt; 'meta_value_num', 'order' =&gt; 'DESC' ) );
 while ( $popularpost-&gt;have_posts() ) : $popularpost-&gt;the_post();
 ?&gt;
 &lt;li&gt;
 &lt;small&gt;&lt;?php the_category(', '); ?&gt;&lt;/small&gt;
 &lt;a href="&lt;?php echo get_permalink(); ?&gt;" title="&lt;?php the_title_attribute(); ?&gt;"&gt;
 &lt;h3&gt;&lt;?php the_title(); ?&gt;&lt;h3&gt;
 &lt;/li&gt;
 &lt;?php
 endwhile;
 wp_reset_query();
 ?&gt;
 &lt;/ul&gt;</pre>

Você pode adicionar thumbnails, links e afins como o de costume.

O que achou? Tem uma solução melhor? Comenta!