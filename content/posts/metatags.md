---
title: Metatags – Breve introdução de uso e teoria
author: Diego Eis
type: post
date: 2008-01-11
excerpt: Metatags servem dar informação sobre seu site para sistemas de buscas ou outras aplicações. Metadados são estruturas de informações que descrevem características de uma fonte de informação.
url: /metatags/
aktt_notify_twitter:
  - no
tweetbackscheck:
  - 1356387202
shorturls:
  - 'a:3:{s:9:"permalink";s:32:"http://tableless.com.br/metatags";s:7:"tinyurl";s:26:"http://tinyurl.com/3oxqvl4";s:4:"isgd";s:19:"http://is.gd/IwSaiU";}'
twittercomments:
  - 'a:1:{i:14108532416716800;s:7:"retweet";}'
tweetcount:
  - 1
dsq_thread_id: 503037866
categories:
  - Browsers
  - Podcasts
  - Técnicas e Práticas
tags:
  - 2008
  - desenvolvimento web
  - html
  - metatags
  - tableless
  - xhtml

---
Metadados são dados sobre dados. Informações sobre a própria informação. Metadados são estruturas de informações que descrevem características de uma fonte de informação.
  
Metadados servem para ajudar seres humanos ou máquinas a localizar e descrever informações, melhorando o gerenciamento e uso destas informações.

Existem uma série de padrões para se criar Metadados, mas por você ser um possível profissional que trabalha com web, a que vai te interessar mais são as Metatags. <!--more-->Metatags são tags do HTML que lhe permitem inserir informações sobre o website. Você às utiliza para informar seres humanos e aplicações, embora sejam as aplicações que fazem melhor uso destas informações.

As metatags são colocadas dentro da tag HEAD do seu documento HTML. Abaixo veja um exemplo de sintaxe:

<pre>&lt;meta name="description" content="Tableless.com.br - Site sobre melhores práticas de desenvolvimento utilizando Padrões Web." /&gt;</pre>

Sistemas de buscas como Google utilizam as metatags para mostrar informações sobre o site nos resultados de busca.O Google especificamente ignora as metatags de Keywords, mas utiliza muito a metatag Description para exibir a descrição dos sites nos resultados de busca.

### Diferença entre metatags HTTP-EQUIV e NAME

Quando o usuário clica em algum link na página, o servidor recebe uma requisição do browser via protocolo HTTP (uma série de regras que definem um diálogo entre o cliente e o servidor &#8211; [mais aqui][1]). O servidor dá uma série de repostas ao browser, que por sua vez mostrará na tela o que o servidor mandar.

Quando você utiliza o uma metatag HTTP-EQUIV, você controla alguns destes comandos, como por exemplo o cacheamento da página ou redirecionamento para outro endereço.

Já os metatags NAME não utilizam este tipo de conversa. Eles são responsáveis apenas em passar informações sobre o website para sistemas ou aplicações &#8211; como sistemas de busca.

### Metatags importantes para uso

#### Description

<pre>&lt;meta name="description" content="Tableless.com.br - Site sobre melhores práticas de desenvolvimento utilizando Padrões Web." /&gt;</pre>

A metatag description serve para informar uma descrição sobre o site. Nesta metatag você vai dizer para que serve o site, qual o assunto principal. É importante saber que os sistemas de busca indexam em média 250 caracteres desta metatag. Cuidade com este limite, pode ser que a descrição do site saia pela metade nos resultados de pesquisa.

#### Keywords

<pre>&lt;meta name="keywords" content="xhtml, ajax, javascript, padroes web, tableless, desenvolvimento web"&gt;</pre>

Nesta metatag você colocará as palavras chaves relativas ao assunto do site. Se você utilizar algum CMS ou sistema de blogging &#8211; como o wordpress &#8211; é interessante que seja feito um estudo para inserir as tags das postas nestas metatags.

#### Robots

<pre>&lt;meta name="robots" content="valor, valor, valor" /&gt;</pre>

Você pode controlar o que os robôs de busca irão indexar ou não indexar em sua página. Normalmente esta metatag é utilizada em alguma página que você não queira que o sistema de busca indexe.

  * **none**: os robôs ignoram a página. É equivalente ao noindex e ao nofollow.
  * **noindex**: a página não será indexada por um sistema de busca.
  * **nofollow**: impede que os robôs de busca sigam os links da página.
  * **noimageindex**: impede que as imagem sejam indexadas. Isso não inclui os textos.
  * **noimageclick**: ignora links colocados diretamente em imagens.
  * **all**: sem restrições de indexação
  * **index**: robôs são permitidos para incluir esta página nas buscas.
  * **follow**: robôs podem seguir os links da página para encontrar outras páginas.

#### Language

<pre>&lt;meta name="language" content="pt-br" /&gt;</pre>

Você define qual a linguagem da página.

#### Author

<pre>&lt;meta name="author" content="Diego Eis, Elcio Luiz Ferreira" /&gt;</pre>

Informa qual são os autores ou o autor da página.

#### Pragma

<pre>&lt;meta http-equiv="pragma" content="no-cache" /&gt;</pre>

Informa que o navegador não deverá cachear a página.

É importante notar que não é necessário colocar muitas metatags em suas páginas. Apenas utilize aquelas que realmente serão úteis. Se você utiliza algo como o WordPress, é interessante encontrar plugins que ajudem na publicação de metatags nas páginas. Aqui no [Tableless][2] eu utilizo o Plugin para WordPress chamada [AddMetaTags][3].

Uma lista maior de metatags você pode encontrar aqui: <http://vancouver-webpages.com/META/>. Há bastante informação também [aqui][4].

 [1]: http://www.obasicodaweb.com/introducao-ao-http
 [2]: http://tableless.com.br/
 [3]: http://www.g-loaded.eu/2006/01/05/add-meta-tags-wordpress-plugin/
 [4]: http://www.library.uq.edu.au/iad/ctmeta4.html