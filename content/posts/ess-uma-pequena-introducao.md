---
title: WordPress – Uma pequena introdução
author: Diego Eis
type: post
date: 2008-02-10
excerpt: 'Entenda o básico do Wordpress. '
url: /wordpress-uma-pequena-introducao/
aktt_notify_twitter:
  - no
tweetbackscheck:
  - 1356388504
shorturls:
  - 'a:3:{s:9:"permalink";s:56:"http://tableless.com.br/wordpress-uma-pequena-introducao";s:7:"tinyurl";s:26:"http://tinyurl.com/3f2k6fg";s:4:"isgd";s:19:"http://is.gd/ge53uV";}'
twittercomments:
  - 'a:1:{i:37304100383105025;s:6:"137043";}'
tweetcount:
  - 1
dsq_thread_id: 503037903
categories:
  - O Básico
  - Wordpress
tags:
  - 2008
  - Browsers
  - cms
  - CSS
  - desenvolvimento web
  - php
  - tableless.com.br
  - tags
  - Template Tags
  - Wordpress
  - xhtml
  - xml
  - xslt

---
O WordPress não foi feito para ser um CMS. Ele foi criado primeiramente para suprir necessidades de criação de blogs. Por acaso, talvez como se fosse um acidente, começamos a utilizá-lo para criar websites, desde os mais simples até os mais complicados. O pessoal do WordPress curtiu a ideia e agora está melhorando cada vez mais o sistema para que ele se torne um CMS de verdade, mesmo assim mantendo toda a simplicidade do WordPress original. E o melhor, é tudo de graça.

Quero mostrar aqui o caminho das pedras. O que você precisa aprender para não ficar batendo cabeça no começo. É coisa simples.

### Criando o index.php e o style.css

Para fazer um tema de WordPress, você precisa apenas de dois arquivos: **index.php** e o **style.css**.

O **style.css** tem uma pequena sintaxe no começo do arquivo com informações do autor do Template. Essas informações serão utilizadas pelo WordPress na tela de Templates.

A sintaxe que está escrita no meu **style.css** é este:

<pre class="lang-css">/*  
Theme Name: Oficina WordPress da Tableless
Theme URI: http://tableless.com.br/
Description: O layout do Tableless
Version: 1.0
Author: Diego Eis
Author URI: http://tableless.com.br/

	 http://tableless.com.br

	This theme was designed and built by Diego Eis,
	whose blog you will find at http://tableless.com.br/

*/
</pre>

Você pode utilizar esse código e modificar para ficar com suas informações. Não precisa decorar, isso é coisa de maluco. 😉

Crie um **style.css** com este código dentro. Não iremos utilizar o CSS neste artigo.

Crie também um **index.php** com a estrutura básica de HTML. Eu utilizo sempre assim:

<pre class="lang-html">&lt;!DOCTYPE html&gt;

&lt;html lang="pt-br"&gt;
&lt;head&gt;
	&lt;meta http-equiv="Content-Type" content="text/html; charset=utf-8" /&gt;
	&lt;title&gt;&lt;/title&gt;
&lt;/head&gt;
&lt;body&gt;

&lt;/body&gt;
&lt;/html&gt;
</pre>

Daqui para frente, irei colocar apenas o código que irá dentro do BODY do documento. Portanto, tudo que iremos ver agora, insira dentro do BODY do seu documento.

### As Template Tags

O segredo do WordPress são as Template Tags. Você pode conferir todas aqui: <http://codex.wordpress.org/Template_Tags>

Os templates do wordpress são escritos em PHP. Isso torna pro designer um pouco complicado, mas não muito. Se você souber um pouco de PHP, fazer um template é muito fácil, porque PHP é uma linguagem que todo mundo usa. Para facilitar, o WordPress chama as funções do PHP que são utilizadas pelo seu sistema de Template Tags. As Template Tags não passam de funções PHP que recuperam do banco, informações que você precisará para compor o conteúdo do site. Para o programador isso não muda nada. Mas para o pessoal que não é tão íntimo assim com a linguagem PHP, a forma que usamos essas &#8220;funções&#8221; (Template Tags) facilita demais.

### O Loop &#8211; Listando os posts na página

O Loop é o responsável pelo trecho de código que será repetido para cada post impresso na tela.

<pre class="lang-php">&lt;?php while ( have_posts() ) : the_post (); ?&gt;

&lt;?php endwhile; ?&gt;
&lt;/pre&gt;
Pra voc&ecirc; chamar os posts do blog &eacute; muito simples. Voc&ecirc; come&ccedil;ar&aacute; utilizando duas Template Tags dentro deste c&oacute;digo de Loop.
&lt;pre class="lang-php"&gt;
&lt;?php while ( have_posts() ) : the_post (); ?&gt;
&lt;h2&gt;&lt;? the_title(); ?&gt;&lt;/h2&gt;
&lt;? the_content(); ?&gt;
&lt;?php endwhile; ?&gt;
</pre>

A primeira Template Tag que coloquei foi a the_title(). Ela chama os títulos dos posts do site.
  
A segunda, the_content() chama o conteúdo dos posts. O Conteúdo vem escrito da forma que você criou no WordPress.

Apenas com esse código acima, você não faz um blog completo. Um blog tem outras características importantes. E são elas que iremos ver agora. 

### Características de um Blog

Há algumas características que compõem um blog. Essas características são encontradas geralmente em blogs, isso não quer dizer que em sites de notícias não podem contem essas características:

  * Comentários
  * Categorias
  * Data, autor
  * Feed
  * Arquivo (histórico)
  * Busca
  * Permalink

Não iremos mostrar em nosso código como se faz Comentários nem Categorias. O Artigo iria ficar muito mais complicado. Portanto, se estiver interessado, faça a [Oficina de WordPress da Visie][1]. 

Vamos agora melhorar um bocado esse código para que o site se pareça mais com um blog.

Primeiro, vamos colocar Permalinks nos títulos dos posts.

<pre class="lang-php">&lt;?php while ( have_posts() ) : the_post (); ?&gt;

&lt;h2&gt;&lt;a href="&lt;? the_permalink(); ?&gt;"&gt;&lt;? the_title(); ?&gt;&lt;/a&gt;&lt;/h2&gt;
&lt;? the_content(); ?&gt;

&lt;?php endwhile; ?&gt;
</pre>

### Autor e Data

A Template Tag que iremos utilizar é a the\_author\_posts\_link() para Autor, que colocará a o nome do Autor com o link para seus posts. E a the\_time() para colocar a data.

<pre class="lang-php">&lt;?php while ( have_posts() ) : the_post (); ?&gt;

&lt;p&gt;por &lt;? the_author_posts_link(); ?&gt; em &lt;? the_time(); ?&gt;&lt;/p&gt;

&lt;h2&gt;&lt;a href="&lt;? the_permalink(); ?&gt;"&gt;&lt;? the_title(); ?&gt;&lt;/a&gt;&lt;/h2&gt;
&lt;? the_content(); ?&gt;

&lt;?php endwhile; ?&gt;
</pre>

Você pode deixar a Template Tag the_time do jeito que você quiser. Ela usa aquela tabela de formatação padrão de data do PHP, você pode encontrar essa tabela aqui: http://php.net/date/
  
Iremos formatar nossa data aqui:

<pre class="lang-php">&lt;?php while ( have_posts() ) : the_post (); ?&gt;

&lt;p&gt;por &lt;? the_author_posts_link(); ?&gt; em &lt;? the_time(d/m/Y); ?&gt;&lt;/p&gt;

&lt;h2&gt;&lt;a href="&lt;? the_permalink(); ?&gt;"&gt;&lt;? the_title(); ?&gt;&lt;/a&gt;&lt;/h2&gt;
&lt;? the_content(); ?&gt;

&lt;?php endwhile; ?&gt;
</pre>

### BUSCA

Para colocar um formulário de busca é muito simples. O código do formulário será:

<pre class="lang-php">&lt;form action="&lt;? bloginfo('home'); ?&gt;"&gt;
&lt;input name="s" type="text" id="busca" value="&lt;? =$_GET['s'] ?&gt;" /&gt;
&lt;input type="submit" value="Procurar" /&gt;
&lt;/form&gt;
</pre>

A Template Tag bloginfo() tráz do banco informações sobre o site. Neste caso, ele vai trazer a URL da home do site.
  
Os inputs do formulário de busca do WordPress já vem com nomes pré-definidos, o input de busca, por exemplo, chama-se **s**.

Nosso código está assim agora.

<pre class="lang-php">&lt;form action="&lt;? bloginfo('home'); ?&gt;"&gt;
&lt;input name="s" type="text" id="busca" value="&lt;? =$_GET['s'] ?&gt;" /&gt;
&lt;input type="submit" value="Procurar" /&gt;
&lt;/form&gt;

&lt;?php while ( have_posts() ) : the_post (); ?&gt;

&lt;p&gt;por &lt;? the_author_posts_link(); ?&gt; em &lt;? the_time(d/m/Y); ?&gt;&lt;/p&gt;

&lt;h2&gt;&lt;a href="&lt;? the_permalink(); ?&gt;"&gt;&lt;? the_title(); ?&gt;&lt;/a&gt;&lt;/h2&gt;
&lt;? the_content(); ?&gt;

&lt;?php endwhile; ?&gt;
</pre>

### Arquivo e Histórico

Para criar os arquivos, ou histórico, iremos utilizar a Template Tag: wp\_get\_archives().

<pre class="lang-php">&lt;? wp_get_archives(); ?&gt;
</pre>

Por padrão, essa Template Tag irá gerar uma lista de links dos meses que há posts. Preste bem atenção no código HTML que ele retorna. Ele cria uma lista de LI sem UL ou OL envolta.

Por tanto, temos que escrever dessa forma:

<pre class="lang-php">&lt;ul&gt;
&lt;? wp_get_archives(); ?&gt;
&lt;/ul&gt;
</pre>

Ele faz deste modo caso você queira colocar uma CLASS ou ID para nomear a lista.

### Linkando o FEED o arquivo CSS

O WordPress já cria os Feeds automaticamente. O trabalho que temos é colocar um link para o que o visitante consiga copiar o endereço do RSS e cadastrar no leitor de Feeds preferido dele. Podemos oferecer em RSS, RSS 2 ou ATOM. Existem pessoas que oferecem os três formatos. Vamos oferecer apenas um formato: o RSS2.

A tag link tem um atributo &#8216;rel&#8217;. O atributo rel é mandatório, ele vai dizer qual será o resto da tag. Se você por exemplo colocar o valor rel=&#8221;stylesheet&#8221;, você está dizendo ao navegador que essa tag link é relativo a uma folha de estilo.

O valor &#8216;alternate&#8217; diz ao navegador que estamos diponibilizando o conteúdo de nosso site em um meio alternativo:

<pre class="lang-php">&lt;link rel="alternate" ...
&lt;link rel="stylesheet" ...
</pre>

A tag type serve para indicar o tipo de arquivo que será carregada. No caso da folha de estillo, existem dois tipos que são utilizados hoje: o XSLT, que é utilizado para formatar código XML. E o tipo CSS, que é para formatar código HTML. 

<pre class="lang-php">&lt;link rel="alternate" type="application/rss+xml" href="&lt;? bloginfo('rss_url'); ?&gt;" /&gt;
&lt;link rel="stylesheet" type="text/css" href="&lt;? bloginfo('stylesheet_url'); ?&gt;" /&gt;
</pre>

Novamente iremos utilizar a tag boginfo(). Agora ela irá buscar o endereço do RSS e do CSS.

Perceba que utilizamos neste exemplo apenas um arquivo, o **index.php** para listar o conteúdo. O WordPress tem uma maneira eficaz de hierarquia de arquivos. Por exemplo: nós precisamos de um arquivo chamado archives.php para criar a lista de histórico. Na falta deste arquivo, o WordPress utiliza o **index.php** para criar a lista. Se tivéssemos feito o archives.php e colocado o código que utlizamos acima que cria a lista de histórico, o WordPress não utilizará o **index.php**.

 [1]: http://visie.com.br/wordpress/ "Oficina de WordPress da Visie"