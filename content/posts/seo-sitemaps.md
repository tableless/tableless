---
title: SEO – Sitemaps
author: Diego Eis
type: post
date: 2008-07-02
excerpt: Saiba como funciona o sitemap.xml
url: /seo-sitemaps/
aktt_tweeted:
  - 1
tweetbackscheck:
  - 1356437651
shorturls:
  - 'a:3:{s:9:"permalink";s:36:"http://tableless.com.br/seo-sitemaps";s:7:"tinyurl";s:26:"http://tinyurl.com/3bebl89";s:4:"isgd";s:19:"http://is.gd/CpQbnY";}'
twittercomments:
  - 'a:2:{i:164408104405053440;s:7:"retweet";i:164396722502635520;s:7:"retweet";}'
tweetcount:
  - 3
dsq_thread_id: 503038264
categories:
  - Artigos
  - SEO
  - Técnicas e Práticas
  - Tecnologia e Tendências
tags:
  - desenvolvimento web
  - Na Prática
  - SEO
  - sitemap
  - xml

---
O [Sitemaps é um formato simples de XML][1] que serve para informar aos sistemas de buscas sobre seus endereços disponíveis para indexação. Esse XML relaciona as URLs existentes do seu site, com algumas informações como data da última atualização, prioridade da página em relação às outras páginas e freqüencia de atualização.

O sitemap.xml é um arquivo que pode ser [gerado automaticamente por um plugin][2] ou até mesmo escrito à mão pelo desenvolvedor.
  
<!--more-->


  
O código básico do Sitemap:
  
[cc lang=&#8221;xml&#8221;]<?xml version="1.0" encoding="UTF-8"?>


  
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
  
<url>
      
<loc>http://www.example.com/</loc>
  
    _<lastmod>2005-01-01</lastmod>_
  
_    <changefreq>monthly</changefreq> <priority>0.8</priority>_
  
</url>
  
</urlset>[/cc]
  
As tags que podem ser inseridas no sitemap.xml são essas:

**<urlset>**
  
Executa o encapsulamento do arquivo e faz referência ao padrão de protocolo atual.

**<url>**
  
Tag pai de cada entrada de URL. O restante das tags são as tags filhas dessa tag.

**<loc>**
  
URL da página. Esse URL deve começar com um protocolo (como http) e terminar com
  
uma barra final, caso seja exigido pelo seu servidor. Esse valor deve conter menos
  
de 2.048 caracteres.

**<lastmod>**
  
A data da última modificação do arquivo. Essa data deve estar no formato de [
  
data e hora do W3C][3]. Esse formato permite omitir o horário, se desejar, e
  
usar AAAA-MM-DD.

Lembre-se de que esta tag é separada do cabeçalho If-Modified-Since (304) que o servidor pode retornar, e os mecanismos de pesquisa podem usar as informações de ambas as fontes de forma diferente.

**<changefreq>**
  
A freqüência com que a página é alterada. Esse valor fornece informações gerais para os mecanismos de pesquisa e pode ser que ele não corresponda exatamente à freqüência de indexação da página. Os valores válidos são:

  * always
  * hourly
  * daily
  * weekly
  * monthly
  * anual
  * never

O valor &#8220;always&#8221; deve ser usado para descrever os documentos que sempre são alterados quando acessados. O valor &#8220;never&#8221; deve ser usado para descrever os URLs arquivados. Observe que o valor dessa tag é considerado uma _dica_ e não um comando. Mesmo que os indexadores de mecanismo de pesquisa possam considerar essas informações ao tomar decisões, pode ser que indexem as páginas marcadas como &#8220;horárias&#8221; com menos freqüência do que isso e talvez façam a indexação de páginas marcadas como &#8220;anualmente&#8221; com mais freqüência do que isso. Os indexadores podem indexar páginas marcadas como &#8220;nunca&#8221; periodicamente, para que possam lidar com alterações inesperadas
  
nessas páginas.

**<priority>**
  
A prioridade desse URL em relação a outros URLs do mesmo site. Os valores válidos vão de 0.0 a 1.0. Esse valor não afeta o modo como as páginas são comparadas às páginas em outros sites — apenas permite que os mecanismos de pesquisa saibam quais páginas você considera mais importantes para os indexadores.

A prioridade padrão de uma página é 0,5.
  
Observe que não é provável que a prioridade atribuída a uma página influencie a posição dos URLs nas páginas de resultados de um mecanismo de pesquisa. Os mecanismos de pesquisa podem usar essas informações quando selecionam entre URLs no mesmo site. Use essa tag para aumentar a probabilidade de a maioria das páginas importantes estarem presentes em um índice de pesquisa.

Além disso, observe que a atribuição de uma prioridade alta a todos os URLs no site provavelmente não o ajudará. Como a prioridade é relativa, ela só é usada para priorizar os URLs do seu site.

[Tabela retirada do sitemaps.org][4]

### Local dos arquivos sitemaps.xml

É importante saber que o local que o sitemap.xml é colocado determina o quais urls podem ser colocadas no arquivo. Exemplo: fiz um [sitemap.xml][5] para o [site de treinamentos da Visie][6] cuja URL é visie.com.br/treinamento. No meu sitemap.xml apenas poderá haver URLs que comecem com visie.com.br/treinamento e não apenas visie.com.br.

Todas as URLs que estão no Sitemap precisam utilizar o mesmo protocolo &#8211; no exemplo da Visie estou utilizando o HTTP &#8211; e precisam estar no mesmo host que o Sitemap. Por exmeplo, se o Sitemap estiver localizado em: visie.com.br/treinamento/sitemap.xml, ele não pode incluir URLs de um subdominio.visie.com.br.

### Informando os buscadores que seu sitemap.xml existe

Há duas maneiras fáceis para avisar aos sistemas de busca que seu sitemap.xml está disponível:

  * Enviando o seu Sitemap por meio da interface de envio do mecanismo de pesquisa
  * Especificando a localização do Sitemap no seu arquivo robots.txt

**Enviando o seu Sitemap por meio da interface de envio do mecanismo de pesquisa.** O Google tem um local muito interessante onde além de informar o endereço do seu sitemap.xml você pode ter uma série de outras informações importantes para seu site, é o [Google Webmaster Tools][7].

**Especificando a localização do Sitemap no seu arquivo robots.txt.** Para indicar o sitemap.xml pelo robots.txt basta acrescentar essa linha: Sitemap: <local\_do\_Sitemap>

Se você quiser, você pode colocar vários endereços de Sitemaps, bastando inserir várias linhas como as de cima indicando os endereços dos respectivos sitemaps.

Ter um sitemap.xml não garante que você uma URL seja ou não mais indexada que as outras. Mesmo assim, é um adendo para que os buscadores fiquem mais informados com os endereços do seu site. Se você não utiliza nenhum plugin para que o sitemap.xml seja gerado automaticamente, fique atento às atualizações das URLs. Você pode estar informando aos buscadores URLs antigas e isso pode afetar nos resultados organicos com o do Google. Se você quiser testar alguns plugins ou programas para gerar seu sitemap.xml automaticamente, [visite este link][2].

 [1]: http://www.sitemaps.org/pt_BR/index.php
 [2]: http://code.google.com/sm_thirdparty.html
 [3]: http://www.w3.org/TR/NOTE-datetime
 [4]: http://www.sitemaps.org/pt_BR/protocol.php
 [5]: http://visie.com.br/treinamento/sitemap.xml
 [6]: http://visie.com.br/treinamento/
 [7]: https://www.google.com/webmasters/tools/