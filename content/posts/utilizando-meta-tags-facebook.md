---
title: Utilizando as metatags de OpenGraph
author: Victor "reidark" Matias
type: post
date: 2014-01-23
excerpt: O tutorial para compartilhar o conteúdo do seu site no Facebook de forma eficaz.
url: /utilizando-meta-tags-facebook/
dsq_thread_id: 2096849188
categories:
  - HTML
  - O Básico
  - SEO
tags:
  - facebook
  - Facebook meta tags
  - Manipulando o Open Graph
  - Open Graph
  - tableless
  - Utilizando as meta tags do Facebook

---
Creio que você, usuário frenético de facebook já tenha visto algo mais ou menos assim na sua linha do tempo:

<div id="attachment_40213" style="width: 484px" class="wp-caption aligncenter">
  <a href="http://tableless.com.br/uploads/2014/01/imagem-P.jpg"><img class="size-full wp-image-40213" alt="Imagem compartilhamento Facebook." src="http://tableless.com.br/uploads/2014/01/imagem-P.jpg" width="474" height="153" srcset="uploads/2014/01/imagem-P.jpg 474w, uploads/2014/01/imagem-P-329x106.jpg 329w" sizes="(max-width: 474px) 100vw, 474px" /></a>
  
  <p class="wp-caption-text">
    Facebook Share
  </p>
</div>

Esse tipo de compartilhamento é devido ao uso das meta tags que o próprio facebook oferece aos desenvolvedores, as famosas **metas :og** ou **Open Graph**. Elas existem com o intuito de especificar metas no `<head>` para sua publicação no facebook ser a mais agradável e apresentável possível.

## O que você precisa saber e fazer

A syntax para essa tag é básica:

<pre class="lang-html">&lt;head&gt;
&lt;meta property="OG TAG" content="VALOR"&gt;
&lt;/head&gt;</pre>

A seguir veremos as tags que podemos especificar para modificar nossa publicação:

### Locale

<pre class="lang-html">&lt;meta property="og:locale" content="en_US"&gt;</pre>

Nessa tag definimos basicamente o local/idioma da publicação. O valor _default_ dela é _en_US_. É interessante o idioma dessa tag acompanhar o mesmo que está definido dentro do `<html lang="">`.

Eu, particularmente, não uso _pt_BR_ para publicações no facebook, e para ser bem sincero não encontro muitas pessoas que usam. Porém, a documentação do Open Graph diz para optarmos pelo idioma em qual o site, artigo ou portfólio está escrito.

### URL

<pre class="lang-html">&lt;meta property="og:url" content="http://www.meusite.com.br/ola-mundo"&gt;</pre>

A tag URL é usada para definir o link destino da publicação. Ela também é usada para definir o tanto de  likes e shares que uma página possui, sem desmembrar nenhum dado perdido por ai, como um like ali e um like aqui. Tudo é “somado” na URL especificáda.

### Title

<pre class="lang-html">&lt;meta property="og:title" content="Utilizando as meta tags do Facebook."&gt;
&lt;meta property="og:site_name" content="Tableless"&gt;</pre>

No HTML puro, a forma que usamos para especificar, tanto o nome a página quanto o nome do site é a tag `<title>`. As meta tags:og vão um pouco a mais que isso. É fornecido 2 tags para usar em relação ao título da página:

`<property="og:title">` Específica o título da página, assim como essa: _Utilizando as meta tags do Facebook_.

`<property="og:site_name">` Especifica o nome do site: _Tableless_.

### Description

<pre class="lang-html">&lt;meta property="og:description" content="O tutorial para compartilhar o conteúdo do seu site de forma eficaz."&gt;</pre>

Acho que essa tag não necessita de muita explicação. É basicamente a descrição da sua postagem. Mas é importante ressaltar de colocar um bom texto chamativo e interessante, para o usuário ver a publicação, gostar e acessar.

É interessante a sua descrição não ultrapassar o máximo de 200 caracteres.

### Images

<pre class="lang-html">&lt;meta property="og:image" content="www.meusite.com.br/imagem.jpg"&gt;
&lt;meta property="og:image:type" content="image/jpeg"&gt;
&lt;meta property="og:image:width" content="800"&gt; /** PIXELS **/
&lt;meta property="og:image:height" content="600"&gt; /** PIXELS **/</pre>

A syntax mostrada logo a cima seria a ideal para um bom compartilhamento. Lembre-se que imagens são a porta de entrada. Você pode ter um bom título, uma boa descrição, mas nada se compara com o impacto que uma imagem provoca no usuário.

Colocando apenas a URL da imagem já é necessário para que sua postagem a apresente. Porém, quando você não especifica o tamanho da imagem, a miniatura vai ser estabelecida com as dimensões originais, e assim o próprio facebook vai decidir se o thumbnail vai ser:

Pequeno

<div id="attachment_40213" style="width: 484px" class="wp-caption aligncenter">
  <a href="http://tableless.com.br/uploads/2014/01/imagem-P.jpg"><img class="size-full wp-image-40213" alt="Imagem compartilhamento Facebook." src="http://tableless.com.br/uploads/2014/01/imagem-P.jpg" width="474" height="153" srcset="uploads/2014/01/imagem-P.jpg 474w, uploads/2014/01/imagem-P-329x106.jpg 329w" sizes="(max-width: 474px) 100vw, 474px" /></a>
  
  <p class="wp-caption-text">
    Facebook Share Pequeno
  </p>
</div>

Isso acontece porque ela não é grande o suficiente para ser um Thumbanil de modelo grande, e caso tentássemos &#8220;esticar&#8221; a imagem para transformar num thumbanil grande a qualidade ficaria MUITO ruim. Mas não se esqueça, se você especificar na tag uma dimensão pequena, mesmo que sua dimensão original seja grande, ela vai aparecer pequena, como no modelo a cima.

E caso a imagem seja grande, ou se você especificou uma dimensão grande na tag, ela irá aparecer assim:

<div id="attachment_40214" style="width: 330px" class="wp-caption aligncenter">
  <a href="http://tableless.com.br/uploads/2014/01/imagem-G.jpg"><img class="size-medium wp-image-40214" alt="Compartilhamento com Thumbnail grande." src="http://tableless.com.br/uploads/2014/01/imagem-G-320x310.jpg" width="320" height="310" srcset="uploads/2014/01/imagem-G-320x310.jpg 320w, uploads/2014/01/imagem-G-173x168.jpg 173w, uploads/2014/01/imagem-G.jpg 396w" sizes="(max-width: 320px) 100vw, 320px" /></a>
  
  <p class="wp-caption-text">
    Facebook Share Grande
  </p>
</div>

Os formatos que o Facebook aceita é: JPEG, PNG, GIF, e BMP. A dica que eu dou é sempre optar pelo JPG e sempre especificar o formato e as dimensões da imagem. Isso faz o Facebook “entender melhor” o que você está enviando.

### Type

<pre class="lang-html">&lt;meta property="og:type" content="website"&gt;</pre>

Define o tipo do seu site. O valor _default_ desse atributo é o _website_. Geralmente é isso mesmo que é usado, o valor _website_. Mas, caso o seu conteúdo for um artigo, você pode optar pela tag _article_ e assim especificar novos valores (o próprio Tableless faz isso.)

<pre class="lang-html">&lt;meta property="og:type" content="article"&gt;
&lt;meta property="article:author" content="reidark"&gt;
&lt;meta property="article:section" content="Tutoriais"&gt;
&lt;meta property="article:tag" content="Facebook, tags, og, open graph"&gt;
&lt;meta property="article:published_time" content="date_time"&gt;</pre>

## Escopo Final

Especificando todas as meta tags:og o seu cabeçalho tem que ficar preenchido mais ou menos dessa maneira:

<pre class="lang-html">&lt;head&gt;
&lt;meta property="og:locale" content="pt_BR"&gt;

&lt;meta property="og:url" content="http://www.meusite.com.br/ola-mundo"&gt;

&lt;meta property="og:title" content="Título da página ou artigo"&gt;
&lt;meta property="og:site_name" content="Nome do meu site"&gt;

&lt;meta property="og:description" content="Minha boa descrição para intrigar os usuários."&gt;

&lt;meta property="og:image" content="www.meusite.com.br/imagem.jpg"&gt;
&lt;meta property="og:image:type" content="image/jpeg"&gt;
&lt;meta property="og:image:width" content="800"&gt; /** PIXELS **/
&lt;meta property="og:image:height" content="600"&gt; /** PIXELS **/

/** CASO SEJA UM SITE NORMAL **/

&lt;meta property="og:type" content="website"&gt;

/** CASO SEJA UM ARTIGO **/

&lt;meta property="og:type" content="article"&gt;
&lt;meta property="article:author" content="Autor do artigo"&gt;
&lt;meta property="article:section" content="Seção do artigo"&gt;
&lt;meta property="article:tag" content="Tags do artigo"&gt;
&lt;meta property="article:published_time" content="date_time"&gt;
&lt;/head&gt;

</pre>

Lembre-se que essa forma de publicação no Facebook atrai pessoas para seu site, seja tanto para ler um artigo, ou apenas dar uma olhada, e assim acaba sendo uma espécie de SEO para rede sociais. Então não esqueça de acrescentar isso ao seu site, vai te ajudar 😉

Tenha em mente que isso é o básico, mas é essencial.

Caso você queira pular de ponta nessas meta tags Open Graph, entre [aqui][1] e se divirta 🙂

Eu esqueci alguma coisa? Então me ajude, comente aqui em baixo.

Abraços!

 [1]: http://ogp.me/