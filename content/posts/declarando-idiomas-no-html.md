---
title: Declarando idiomas no HTML
author: Diego Eis
type: post
date: 2012-01-09
excerpt: O conteúdo online pode ser acessado no mundo inteiro, não importa seu idioma. Para tanto o idioma deve ser declarado corretamente para que os meios de acesso entreguem o conteúdo da melhor forma possível.
url: /declarando-idiomas-no-html/
tweetbackscheck:
  - 1356410927
shorturls:
  - 'a:3:{s:9:"permalink";s:51:"http://tableless.com.br/declarando-idiomas-no-html/";s:7:"tinyurl";s:26:"http://tinyurl.com/7v2fwt4";s:4:"isgd";s:19:"http://is.gd/Gxy6fG";}'
twittercomments:
  - 'a:18:{i:156318348102209536;s:7:"retweet";i:158880776753127424;s:7:"retweet";i:158880283515559936;s:7:"retweet";i:158880103647031297;s:7:"retweet";i:156456745433182208;s:7:"retweet";i:156353572135645184;s:7:"retweet";i:156342476226048001;s:7:"retweet";i:156341100276219904;s:7:"retweet";i:156338214406324224;s:7:"retweet";i:156336567588372480;s:7:"retweet";i:156334911966552064;s:7:"retweet";i:156323094183690240;s:7:"retweet";i:156320238772822016;s:7:"retweet";i:156319087566389248;s:7:"retweet";i:169917455915945985;s:7:"retweet";i:169190738054230016;s:7:"retweet";i:169136300765626368;s:7:"retweet";i:169135689307389952;s:7:"retweet";}'
tweetcount:
  - 68
dsq_thread_id: 532390998
categories:
  - Acessibilidade
  - HTML
  - HTML5
  - Técnicas e Práticas
tags:
  - 2012
  - desenvolvimento web
  - html
  - html5
  - tableless
  - usabilidade

---
Publicar conteúdo na web definitivamente não é a mesma coisa da publicação de conteúdo nos meios impressos. Quando imprimimos o conteúdo, temos como foco um determinado público de uma determinada região. Eu, estando no Brasil, não vou fazer uma revista em no idioma Japonês. Quando falamos publicação de conteúdo online a coisa muda de cenário. O conteúdo online pode ser acessado no mundo inteiro, não importa seu idioma. Obviamente se você conhece outros idiomas, você amplia suas possibilidades para encontrar conteúdo e novos sites. 

Os desenvolvedores do mundo inteiro juntamente com os fabricantes de browsers e outros interessados, querem ter certeza que os navegadores, robôs de busca, leitores de tela e outros sistemas detectem da forma ideal o idioma correto.

A declaração do idioma no código HTML não determina a informação no [encoding de caractére do texto][1] nem a direção de leitura do texto em outros idiomas. Essas definições precisam ser declaradas separadamente.

Nós precisamos definir o idioma por alguns motivos:

  * Melhor pronunciação do texto em leitores de tela. 
  * Para que os buscadores possam indexar o website no buscador do respectivo idioma. Por exemplo: não tem sentido o Google ranqueear muito bem um site em português no Google americano.
  * Selecionar as fonts corretas para mostrar na tela. Nesse caso para idiomas como Chinês.
  * Para que os browsers escolham o dicionário correto para a correção gramatical nativa em textos e formulários.
  * Renderizar a página rapidamente &#8211; o browser carrega o documento mais rápido quando o browser sabe qual o idioma nativo.

### Definindo o idioma padrão do documento

Existem algumas maneiras que você pode definir o idioma padrão no documento exibido ou em partes do texto para aqueles termos em idiomas diferentes.

Podemos definir diretamente via metatag nativa:

<pre class="lang-html">&lt;meta http-equiv="Content-Language" content="pt-br"&gt;
</pre>

Pela Metatag podemos definir vários valores no atributo content:

<pre class="lang-html">&lt;meta http-equiv="Content-Language" content="pt-br, en, fr, it"&gt;
</pre>

Via **HTTP Header**:

<pre class="lang-html">HTTP/1.1 200 OK
Date: Fri, 30 Dez 2011 10:46:04 GMT
Server: Apache/1.3.28 (Unix) PHP/4.2.3
Content-Location: CSS2-REC.en.html
Vary: negotiate,accept-language,accept-charset
TCN: choice
P3P: policyref=http://www.w3.org/2001/05/P3P/p3p.xml
Cache-Control: max-age=21600
Expires: Wed, 05 Nov 2003 16:46:04 GMT
Last-Modified: Tue, 12 May 1998 22:18:49 GMT
ETag: "3558cac9;36f99e2b"
Accept-Ranges: bytes
Content-Length: 10734
Connection: close
Content-Type: text/html; charset=utf-8
Content-Language: pt-br
</pre>

Via atributo **lang** nos elementos do HTML. 

<pre class="lang-html">&lt;p&gt;N&oacute;s utilizamos o &lt;span lang="en"&gt;mouse&lt;/span&gt; para navegar na &lt;span lang="en"&gt;web&lt;/span&gt; por meios dos &lt;span lang="en"&gt;browsers&lt;/span&gt;.
</pre>

Assim indicamos, principalmente para os leitores de tela, quais termos ele deve ler com o idioma nativo do termo.

Temos o costume de indicar o atributo **lang** no elemento **html** logo no início do documento para indicar que todo o conteúdo contido dentro do **html** está escrito em um determinado idioma.

<pre class="lang-html">&lt;!DOCTYPE html&gt;
&lt;html lang="pt-br"&gt;
&lt;head&gt;
  &lt;title&gt;T&iacute;tulo&lt;/title&gt;
&lt;/head&gt;
&lt;body&gt;
&lt;/body&gt;
&lt;/html&gt;
</pre>

### Ordem de herança

Os meios de acesso, normalmente browsers, seguem esses passos de verificação para identificar o idioma:

  1. Verifica se elemento HTML que tem o atributo **lang**, se não,
  2. Verifica se pai mais próximo ao termo que tenha o atributo **lang**, se não,
  3. Verifica se o documento tem a metatag definida <meta http-equiv=&#8221;content-language&#8221; content=&#8221;pt-br&#8221;>, se não,
  4. Verifica se o HTTP Header Content-Language tem uma tag de idioma definido. Se não,
  5. O idioma é tratado como não reconhecido.

O W3C recomenda que você sempre utilize o **lang** no elemento **html** para definir o idioma padrão de todo o conteúdo e também em todo o termo encontrado no texto com idioma diferente do definido como padrão.

Declarações de idioma baseados nestes atributos são importantes para a maioria das aplicações web hoje, que vão desde as [corretores ortográficos][2] embutidos diretamente nos browsers até leitores de telas que interpretam as páginas web, etc etc.

Estas possibilidades são interessantes para que possamos globalizar ainda mais nossos projetos. Imagine por exemplo um website que ensina Russo para Chineses. É interessante que possamos marcar os termos dos dois idiomas de forma que os mecanismos trabalhem adequadamente em diversos meios de acesso. Os browsers precisam identificar quando o texto está em Russo ou quando está em Chinês. Os buscadores também precisam entender essa diferença, bem como os leitores de tela.

Aos poucos vamos padronizando características que antes eram ignoradas no desenvolvimento web. Não são ações muito difíceis de aplicar. Para começar, basta colocar o atributo **lang** no elemento **html** dos seus documentos e pronto.

##### Referências

Artigo que [explica os Charsets, encodes e tabelas de caractéres no HTML][1].

Veja aqui a [documentação oficial do W3C][3] que fala sobre este assunto.

 [1]: http://tableless.com.br/charsets-e-encodes-tabelas-de-caracteres/ "Charsets e Encodes – Tabelas de caracteres"
 [2]: http://br.mozdev.org/firefox/ortografia
 [3]: http://www.w3.org/TR/i18n-html-tech-lang/