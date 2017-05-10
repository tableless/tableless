---
title: Melhorando carregamento do WordPress
author: Paulo Rodrigues
type: post
date: 2011-06-09
excerpt: Aprenda dicas úteis para deixar seu site em WordPress mais rápido. Facilitando a vida do usuário e melhorando resultados nos mecanismos de busca.
url: /melhorando-carregamento-wordpress/
tweetbackscheck:
  - 1356388317
shorturls:
  - 'a:3:{s:9:"permalink";s:57:"http://tableless.com.br/melhorando-carregamento-wordpress";s:7:"tinyurl";s:26:"http://tinyurl.com/3wjkjzu";s:4:"isgd";s:19:"http://is.gd/NAVDch";}'
twittercomments:
  - 'a:5:{i:104167377658318848;s:7:"retweet";i:163350088545091584;s:7:"retweet";i:163301091491069954;s:7:"retweet";i:163282805592305664;s:7:"retweet";i:163273661510463488;s:7:"retweet";}'
tweetcount:
  - 11
dsq_thread_id: 503040309
categories:
  - Wordpress
tags:
  - carregamento
  - comprimir arquivos
  - CSS3
  - otimização de imagens
  - SEO
  - Wordpress
  - wp-minify

---
<!--a href="http://tableless.com.br/uploads/2011/05/site-speed.png"><img src="http://tableless.com.br/uploads/2011/05/site-speed.png" alt="Velocidade do site" width="400" height="300" class="alignnone size-full wp-image-3788" srcset="uploads/2011/05/site-speed.png 400w, uploads/2011/05/site-speed-300x225.png 300w" sizes="(max-width: 400px) 100vw, 400px" /></a>
<em>(Imagem retirada de http://www.netpaths.net/blog/how-to-increase-site-speed-for-google-page-load-algorithm/, em 02/06/11 às 21:06)</em-->

A web cresceu, e com isso várias tecnologias e ferramentas foram criadas ou melhoradas para suprir necessidades requisitadas pelos usuários. Ao longo do tempo clientes e usuários vão pedindo sites mais bonitos e atraentes, e também exigindo rapidez. Para quem usa WordPress, existe aperfeiçoamento e acertos para deixar ele mais rápido. Já para quem não usa, lamento, mas é bom prestar atenção algumas dicas, pois podem servir.

### Comprima HTML, CSS e JS

Comprimir arquivos é essencial para reduzir o seu tamanho e melhorar o carregamento, pois menor é o seu tamanho, melhor e mais rápido ele vai abrir.

Para isso, usa-se o WP-Minify, este plug-in auxilia na compressão destes arquivos. [Baixe WP-Minify][1], instale e ative as opções de compressão de que desejar.

**Atenção:** Ativando a compressão de HTML, se o seu código não estiver todo identado, não se espante. Quer uma dica? Se fores assim como eu, ative apenas a compressão do CSS e JS.

### Otimize suas imagens

Por uma necessidade de sites bonitos, na maioria das vezes há um uso excessivo de imagens que na maioria das vezes estão mal otimizadas com alta qualidade.

Tente reduzir o tamanho das imagens do seu site sem que se atinja tanto a sua qualidade. Seja um background ou uma imagem qualquer.

Para reduzir o tamanho de imagens enviadas via WordPress, utilize o [plug-in WP Smush.it][2]

### Use um Plug-in de Cache

Sempre é bom ter um plug-in de cache ativado no WordPress, como já citei no artigo “[Otimizando seu site em WordPress para SEO][3]”, o plug-in de cache, também ajuda no carregamento das páginas.

Re-indico [WP Super Cache][4], [W3 Total Cache][5], [Batcache][6] ou [Hyper Cache.][7]

### Dicas úteis

<ol style="margin-top: 10px">
  <li>
    <strong>Estrutura dos códigos:</strong> A estrutura do código também interfere, seja ele HTML, CSS ou JS. Para HTML, faça um código semântico, sem muitas gambiarras. Confira esse <a href="http://tableless.com.br/6-estrategias-para-melhorar-a-organizacao-do-seu-css-2" title="artigo para melhorar organização do código CSS">artigo para melhorar organização do código CSS</a>, que vai ajudar muito.
  </li>
  <li>
    <strong>Boa hospedagem:</strong> Ter um servidor com melhor qualidade ajuda muito no carregamento. Escolhendo uma boa hospedagem, tente também conter quedas no servidor.
  </li>
  <li>
    <strong>Desative plug-ins desnecessários:</strong> É relevante desativar plug-ins desnecessários ou sem muita utilidade, pois seus arquivos quando requisitados vão ser acionados, aumentando o carregamento final.
  </li>
  <li>
    <strong>Evite muitas requisições:</strong> Evite requisições desnecessárias, seja ela de CSS, JS ou até mesmo de outras páginas.
  </li>
  <li>
    <strong>Mantenha seu WordPress atualizado:</strong> As atualizações do WordPress não vem em vão, pois tem sua importância. Atualizando, você vai melhorar o desempenho, além de evitar vulnerabilidades, aumentando a segurança.
  </li>
</ol>

### Vamos Refletir

**Repare&#8230;** Ter um site bonito, nem sempre é ter um site pesado. Se prestarmos atenção, melhora-se muita coisa no site. Fique atento, pois por alguns milésimos você perder um usuário e/ou ficar com uma posição indesejada nos mecanismos de busca.

**Com o CSS3**, muita coisa vai melhorar. Muita coisa será substituída com os novos elementos. Uma pena que não virou padrão ainda, nos deixa mais triste saber que vai demorar até virar padrão. _(Mesmo assim)_, seja ousado e use alguns elementos.

**Relação com SEO:** Demonstrei certa preocupação com o SEO se tratando deste assunto, pois o carregamento da página vai interferir no seu posionamento em mecanismos de busca, em especial o Google. 

Você pode analisar, através da [ferramenta do Google &#8211; Page Speed][8], a velocidade no carregamento do site. Se você usa Google Analytics, segue uma [dica para analisar o carregamento do site][9].

 [1]: http://wordpress.org/extend/plugins/wp-minify/ "Baixe WP-Minify"
 [2]: http://wordpress.org/extend/plugins/wp-smushit/ "plug-in WP Smush.it"
 [3]: http://tableless.com.br/otimizando-site-wordpress-seo "Otimizando seu site em WordPress para SEO"
 [4]: http://wordpress.org/extend/plugins/wp-super-cache/ "WP Super Cache"
 [5]: http://wordpress.org/extend/plugins/wp-super-cache/ "W3 Total Cache"
 [6]: http://wordpress.org/extend/plugins/batcache/ "Batcache"
 [7]: http://wordpress.org/extend/plugins/hyper-cache/ "Hyper Cache"
 [8]: http://code.google.com/speed/page-speed/ "ferramenta do Google Page Speed"
 [9]: http://www.domicioneto.com/web-analytics/google-analytics/trackpageloadtime-monitorar-carregamento-google-analytics/ "dica para analisar o carregamento do site"