---
title: Tudo o que você precisa saber sobre Sitemaps
author: thiago-pacheco
type: post
date: 2013-01-21
excerpt: Saiba como montar e como funciona um sitemap.xml
url: /tudo-que-voce-precisa-saber-sobre-sitemaps/
dsq_thread_id: 1024163999
categories:
  - O Básico
  - SEO
tags:
  - buscadores
  - google
  - SEO
  - sitemap

---
Sitemap é uma maneira fácil de informar aos motores de buscas sobre as páginas do seu site que estão disponíveis para indexação, esse tipo de arquivo é útil e válido para qualquer tipo de site seja institucional, e-commerce, blog, sites de pequeno médio ou grande porte.

Graças ao padrão definido pelas empresas Google, Microsoft e Yahoo, os motores de buscas podem encontrar as suas páginas muito mais rápido, reduzindo assim a quantidade de tempo que leva para o seu site ou uma nova página aparecer nos resultados de busca.

**Ao criar um Sitemap** para nossos sites temos que ter em mente duas coisas:

  1. O Sitemap não garante que uma página será adicionada ao índice do buscador ou que o seu site tenha um posicionamento melhor.
  2. O Sitemap é para um &#8220;robô&#8221; ler, então é primordial que você responsável pelo site, envie as URLs válidas, caso contrário a autoridade do seu site pode estar abalada.

## Conheça os tipos de Sitemap

Todos os tipos de sitemap tem um limite de tamanho, é recomendado que fique com menos de 50MB ou até 50 mil URLs por arquivo, caso seu site seja muito grande nada impede de você criar uma segmentação de Sitemaps.

### Estrutura Básica de um Sitemap

Certifique-se que todas as URLs do seu arquivo estejam no mesmo host, outro ponto importante é o tamanho da URL é permitido até 2.048 caracteres.

<pre class="lang-pre">&lt;?xml version="1.0" encoding="UTF-8"?&gt;
&lt;urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9"&gt;
    &lt;url&gt;
        &lt;loc&gt;http://www.seusite.com.br/&lt;/loc&gt;
        &lt;lastmod&gt;2013-01-13&lt;/lastmod&gt;
        &lt;changefreq&gt;weekly&lt;/changefreq&gt;
        &lt;priority&gt;0.6&lt;/priority&gt;
    &lt;/url&gt;
&lt;/urlset&gt;</pre>

  * A tag **loc** é utilizado para ligar a página, basta digitar a URL entre as tags
  * A tag **lastmod** apresenta a data em que a página foi modificada pela última vez
  * A tag **changefreq** é a freqüencia de variação média da página (horária, diária, semanal, mensal, anual)
  * Você também pode priorizar determinadas páginas através da tag **priority**. Valores de prioridade variam 0,0 até 1,0 (1,0 é o mais importante)

### Índice de Sitemaps

Se você tiver mais de um Sitemap, poderá listá-los em um arquivo de **índice de Sitemaps** e enviar esse arquivo ao Google, nesse caso você não precisa enviar cada arquivo de Sitemap individualmente.

<pre class="lang-xml">&lt;?xml version="1.0" encoding="UTF-8"?&gt;
&lt;sitemapindex xmlns="http://www.sitemaps.org/schemas/sitemap/0.9"&gt;
    &lt;sitemap&gt;
        &lt;loc&gt;http://www.website.com/sitemap1.xml&lt;/loc&gt;
    &lt;/sitemap&gt;
    &lt;sitemap&gt;
        &lt;loc&gt;http://www.website.com/sitemap2.xml&lt;/loc&gt;
    &lt;/sitemap&gt;
&lt;/sitemapindex&gt;</pre>

### Sitemap de Notícias

Essa é a **estrutura de um Sitemap** voltado para o Google News, geralmente utilizado por grandes portais pois possuem uma grande demanda de URLs com constantes atualizações.

<pre class="lang-xml">&lt;?xml version="1.0" encoding="UTF-8"?&gt;
&lt;urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9"
xmlns:news="http://www.google.com/schemas/sitemap-news/0.9"&gt;
    &lt;url&gt;
        &lt;loc&gt;http://www.example.org/business/article55.html&lt;/loc&gt;
        &lt;news:news&gt;
            &lt;news:publication&gt;
                &lt;news:name&gt;Jornal de Exemplo&lt;/news:name&gt;
                &lt;news:language&gt;en&lt;/news:language&gt;
            &lt;/news:publication&gt;
            &lt;news:access&gt;Subscription&lt;/news:access&gt;
            &lt;news:genres&gt;PressRelease, Blog&lt;/news:genres&gt;
            &lt;news:publication_date&gt;2008-12-23&lt;/news:publication_date&gt;
            &lt;news:title&gt;Empresas A e B discutem fusão&lt;/news:title&gt;
            &lt;news:keywords&gt;negócios, fusão&lt;/news:keywords&gt;
            &lt;news:stock_tickers&gt;NASDAQ:A, NASDAQ:B&lt;/news:stock_tickers&gt;
        &lt;/news:news&gt;
    &lt;/url&gt;
&lt;/urlset&gt;</pre>

### Sitemap de Vídeos

Também é possível criar um **Sitemap para vídeos**, os formatos permitidos para os buscador rastrear são: WMV, MP4, MPEG, MPG, m4v, asf, fvl, swf, avi, RA e RAM.

<pre class="lang-xml">&lt;urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9"
xmlns:video="http://www.google.com/schemas/sitemap-video/1.1"&gt;
&lt;url&gt;
    &lt;loc&gt;http://www.website.com/video-page.html&lt;/loc&gt;
    &lt;video:video&gt;
    &lt;video:thumbnail_loc&gt;http://www.website.com/video-thumbnail.jpg&lt;/video:thumbnail_loc&gt;
    &lt;video:title&gt;Most Awesome Video Ever&lt;/video:title&gt;
    &lt;video:description&gt;As the title says: this is the most awesome video ever.&lt;/video:description&gt;
    &lt;video:content_loc&gt;http://www.website.com/video.mp4&lt;/video:content_loc&gt;
    &lt;video:duration&gt;120&lt;/video:duration&gt;
    &lt;/video:video&gt;
    &lt;/url&gt;
&lt;/urlset&gt;</pre>

Há uma abundância de outras tags que você pode adicionar, como uma classificação, ver contagem, restrições, etc. Todas as tags disponíveis pode ser encontrada dentro de recursos para <a href="https://www.google.com.br/webmasters/tools" target="_blank">Webmasters do Google</a>.

### Sitemap de Imagens

O **Sitemap de imagem** pode ser muito útil para obter um tráfego &#8220;extra&#8221; através de resultados de pesquisas por imagens no Google.

<pre class="lang-xml">&lt;?xml version="1.0" encoding="UTF-8"?&gt;
 &lt;urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9"
  xmlns:image="http://www.google.com/schemas/sitemap-image/1.1"&gt;
 &lt;url&gt;
   &lt;loc&gt;http://example.com/exemplo.html&lt;/loc&gt;
   &lt;image:image&gt;
     &lt;image:loc&gt;http://example.com/image.jpg&lt;/image:loc&gt; 
   &lt;/image:image&gt;
   &lt;image:image&gt;
     &lt;image:loc&gt;http://example.com/foto.jpg&lt;/image:loc&gt;
   &lt;/image:image&gt;
 &lt;/url&gt; 
&lt;/urlset&gt;</pre>

### Sitemap para Celular

Com o crescimento do mercado Mobile é natural que as pessoas comecem a buscar mais através do seus dispositivos móveis, é um fato inevitável saia na frente do seus concorrentes comece com o **Sitemap para celular** e depois saiba <a href="http://www.seomonkey.com.br/mobile/dicas-para-otimizacao-mobile" target="_blank">como otimizar o seu site para mobile</a>.

<pre class="lang-xml">&lt;?xml version="1.0" encoding="UTF-8" ?&gt;
 &lt;urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9"
        xmlns:mobile="http://www.google.com/schemas/sitemap-mobile/1.0"&gt;
    &lt;url&gt;
   &lt;loc&gt;http://celular.example.com/artigo100.html&lt;/loc&gt;
        &lt;mobile:mobile/&gt;
    &lt;/url&gt;
&lt;/urlset&gt;</pre>

## Validando o Sitemap

Todos nós já esquecemos de fechar uma tag, pensando nisso o Google disponibilizou uma opção de testar o seu Sitemap antes de enviar, para acessar basta entrar no Google Webmasters Tools > Otimização > Sitemaps:
  
![][1]

**DICA**: Se você tiver um blog com um Feed RSS ou Atom, poderá enviar a URL desse feed como um Sitemap, outra maneira simples de fazer é criar um arquivo TXT com uma URL por linha.

## Conclusão

Deseja ter mair relevância nos buscadores, comece facilitando a indexação do seu site através do Sitemap.

 [1]: http://www.seomonkey.com.br/img/ferramentas-para-webmasters-otimizacao-sitemaps.jpg