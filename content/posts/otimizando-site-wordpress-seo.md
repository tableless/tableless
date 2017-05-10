---
title: Otimizando seu site em WordPress para SEO
author: Paulo Rodrigues
type: post
date: 2011-03-17
excerpt: Vamos ver como podemos aperfeiçoar seu site em WordPress para SEO e veja a importância de fazer isso.
url: /otimizando-site-wordpress-seo/
tweetbackscheck:
  - 1356390827
shorturls:
  - 'a:3:{s:9:"permalink";s:53:"http://tableless.com.br/otimizando-site-wordpress-seo";s:7:"tinyurl";s:26:"http://tinyurl.com/3duuw5s";s:4:"isgd";s:19:"http://is.gd/thQNGN";}'
twittercomments:
  - 'a:16:{i:126323578588233730;s:7:"retweet";i:126272383425318913;s:7:"retweet";i:126045268079673344;s:7:"retweet";i:126034119594487808;s:7:"retweet";i:125989528107360256;s:7:"retweet";i:125981861548793856;s:7:"retweet";i:125979997730123776;s:7:"retweet";i:125979969598918658;s:7:"retweet";i:125978568277762048;s:7:"retweet";i:125978432654950400;s:7:"retweet";i:125978192111603713;s:7:"retweet";i:145643854236884993;s:7:"retweet";i:145643827909242880;s:7:"retweet";i:145638748644835328;s:7:"retweet";i:163103148200837120;s:7:"retweet";i:163094327231381504;s:7:"retweet";}'
tweetcount:
  - 60
dsq_thread_id: 503015731
categories:
  - Técnicas e Práticas
  - Wordpress
tags:
  - 2011
  - Akismet
  - All in One SEO Pack
  - cache
  - otimização de sites
  - permalinks
  - plugin
  - robots
  - Semântica
  - SEO
  - sitemaps
  - spam
  - Wordpress

---
Uma característica que defina o WordPress é a **customização**. Em poucas linhas conseguimos soluções significantes. Seja trabalhando com suas funções ou com seus plugins, temos resultados objetivos para preparar um Blog e até mesmo um site de grande porte, como temos hoje, vários exemplos disso.

Elogiam muito o WordPress por ele ter uma facilidade para [otimização de sites][1] (SEO). Antes de começarem a ler as dicas que vou citar, faça a seguinte reflexão: O que é um site hoje, sem ser bem indexado pelos mecanismos de busca?

### Melhore a tag title do seu site

Você acha mesmo que a tag de título do seu site não tem importância? Espero que não, pois é com ela que os mecanismos de busca reconhecem uma das primeiras informações do seu site.

Coloque o seu título da seguinte forma: 

[cce lang=&#8221;php&#8221;]

<title>
  <?php wp_title(“|”, true, ‘right’); ?><?php bloginfo(‘name’); ?>
</title>[/cce]

A função **wp_title** imprime vários resultados a depender da sua página.

### Links permanentes (Permalinks)

Quem usa WordPress e não usa essa função básica, não sabe o que está perdendo. A URL também tem uma função importante para indexação de sites, pois também é reconhecido antes da página ser carregada. O seu site sairia na frente de diversas URL’s que usam aqueles parâmetros grandes e sem semântica.

Dentro de seu painel de administração, procure por Settings (Configurações) e depois Links Permanentes (Permalinks). Selecione a opção Custom Structure (Estrutura Personalizada) e altere sua estrutura para: 

[cce lang=&#8221;html&#8221;]/%category%/%postname%/[/cce]

### Otimizando as metas do seu site

Para otimizar as metas, utilize o plug-in [All in One SEO Pack][2], com esse plug-in conseguimos facilmente manipular as metas e também títulos do site. Com ele, alteram-se as metas de descrição e keywords (palavras-chave) da página inicial e também dos posts, além dos títulos de cada página. 

[Baixe o plug-in][2], instale-o e ative.

### Mecanismos de busca odeiam SPAM

Os mecanismos de busca odeiam SPAM, ou seja, odeiam conteúdo ruim e/ou desnecessário. Existe um plug-in que modera spam no seu site, chama-se Akismet. Geralmente ele já é incluído quando você instala o WordPress, mas caso não encontre depois que instalar, [baixe-o][3] e ative-o.

Para usar do plug-in é necessário resgatar um código gerado pelo [site][4] deles.

### Use semântica no seu código

Do que adianta ter todos esses aperfeiçoamentos no seu site e seu site não estiver com um código semântico? Por isso trabalhe com um código de qualidade para que não haja dificuldade para seu código ser lido pelos mecanismos de busca.

Use alt e title para as imagens, não esqueçam, pois as imagens só podem ser lidas desta maneira. Trabalhe bem com as tags de título <h1>, <h2>, <h3>, <h4>, <h5>, <h6>, e estabeleça uma hierarquia entre elas. 

### Utilize sempre um plug-in de cache

A partir da demanda do seu site e ele for crescendo em questão de conteúdo, é sempre bom ter um plug-in de cache para diminuir o carregamento da sua página, sendo assim os mecanismos de busca não terão dificuldades para carregar seu site.

Indico [WP Super Cache][5], [W3 Total Cache][6], [Batcache][7] ou [Hyper Cache.][8]

Tenho certeza que com um deles, seu site estará em boas mãos em relação ao cache.

### Sitemaps (mapa do site)

Para os mecanismos de busca, um sitemap ajuda nas buscas de páginas, pois ele relaciona as URL existentes no seu site. Leia esse [artigo][9] e veja o porquê do uso de sitemaps.

O WordPress tem um plug-in que gera um sitemap já otimizado para mecanismos de busca. 

Use o [Google SiteMap Generator][10] e não tenha possíveis problemas para este assunto.

### Crie um bom Meta Robôs

É importante você ter um robots.txt na raiz do seu site, que é um arquivo funciona como filtro para os Crawlers e os robôs dos mecanismos de busca, permitindo ou não acesso a páginas do seu site.

Crie um arquivo em txt, chamado robots.txt com o seguinte código:

[cce lang=&#8221;html&#8221;]
  
User-agent: *
  
Disallow: /cgi-bin
  
Disallow: /wp-admin
  
Disallow: /wp-includes
  
Disallow: /wp-content/plugins
  
Disallow: /wp-content/cache
  
Disallow: /wp-content/themes
  
Disallow: /trackback
  
Disallow: /feed
  
Disallow: /comments
  
Disallow: /category/\*/\*
  
Disallow: */trackback
  
Disallow: */feed
  
Disallow: */comments
  
Disallow: /\*?\*
  
Disallow: /*?
  
Allow: /wp-content/uploads

\# Google Image
  
User-agent: Googlebot-Image
  
Disallow:
  
Allow: /*

\# Google AdSense
  
User-agent: Mediapartners-Google*
  
Disallow:
  
Allow: /*

\# digg mirror
  
User-agent: duggmirror
  
Disallow: /

Sitemap: http://www.seusite.com.br/sitemap.xml
  
[/cce]

Envie para o servidor e ponha na raiz do seu site.

E no header.php do seu tema, adicione o código:

[cce lang=&#8221;php&#8221;]

<?php
  
if(is\_single() || is\_page() || is\_category() || is\_home()) {
      	  
echo &#8216;<meta name=&#8221;robots&#8221; content=&#8221;all,noodp&#8221; />&#8217;;
  
}
  
else if(is_archive()) {
      	  
echo &#8216;<meta name=&#8221;robots&#8221; content=&#8221;noarchive,noodp&#8221; />&#8217;;
  
}
  
else if(is\_search() || is\_404()) {
      	  
echo &#8216;<meta name=&#8221;robots&#8221; content=&#8221;noindex,noarchive&#8221; />&#8217;;
  
}
  
?>

[/cce]

### Faça um bom conteúdo

Não adianta ter um site todo otimizado para os mecanismos e eles não terem o que buscar de conteúdo no seu site. Fazer um bom conteúdo é essencial para qualquer indexação de artigo, página, textos ect. 

Também não se esqueça de trabalhar com as redes sociais, pois maior quantidade de links gerados para o seu site, maior relevância ele terá.

Seja sempre objetivo e claro na suas publicações, tenho certeza que terá um bom resultado. Vale ressaltar que o Google está punindo quem copia conteúdo, muito cuidado.

Caso tenha futuras dúvidas, o WordPress oferece no seu codex um [guia para otimização de SEO][11]

 [1]: http://www.oitobitdigital.com.br/servico/otimizacao-de-sites-seo/
 [2]: http://wordpress.org/extend/plugins/all-in-one-seo-pack/ "Plug-in All in One SEO Pack"
 [3]: http://wordpress.org/extend/plugins/akismet/ "Akismet plug-in"
 [4]: http://akismet.com/ "Site Akismet"
 [5]: http://wordpress.org/extend/plugins/wp-super-cache/ "WP Super Cache"
 [6]: http://wordpress.org/extend/plugins/wp-super-cache/ "W3 Total Cache"
 [7]: http://wordpress.org/extend/plugins/batcache/ "Batcache"
 [8]: http://wordpress.org/extend/plugins/hyper-cache/ "Hyper Cache"
 [9]: http://tableless.com.br/seo-sitemaps "Artigo SEO Sitemaps Tableless"
 [10]: http://wordpress.org/extend/plugins/google-sitemap-generator/ "Plug-in Google SiteMap Generator"
 [11]: http://codex.wordpress.org/Search_Engine_Optimization_for_WordPress "Guia para otimização de SEO WordPress"