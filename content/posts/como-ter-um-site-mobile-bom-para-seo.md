---
title: Como ter um site mobile bom para SEO
author: Carina Andrade
type: post
date: 2016-01-26
url: /como-ter-um-site-mobile-bom-para-seo/
categories:
  - SEO

---
Há alguns anos ter um site mobile era um diferencial. Hoje, para quem se preocupa com sua presença na internet, estar preparado para receber usuários de dispositivos móveis é vital. Afinal, para muitos brasileiros o primeiro, e muitas vezes único, contato com a internet tem sido através de um celular.

## O impacto no trabalho de SEO

Para que todo o trabalho de desenvolvimento de uma versão mobile seja bem aproveitado atraindo visitantes dos mecanismos de busca é preciso que ele obedeça às diretrizes de qualidade do Google e não ‘atrapalhe’ o desempenho da versão desktop. Para isso alguns cuidados são necessários, dependo do tipo de site mobile que está sendo desenvolvido.

## Tipos de site mobile

Há, basicamente, três tipos de site mobile mais utilizados:

### Sites responsivos

Esse é o modelo indicado pelo Google, apesar de que os outros dois tipos, se configurados corretamente, funcionam muito bem. Nesse caso o conteúdo é o mesmo, nas mesmas URLs, mas o site se adapta a diversos tamanhos de tela usando recursos do CSS.

Esse tipo de site não gera muito problema para a estratégia de SEO porque as páginas são as mesmas. O único cuidado necessário é **não bloquear via robots.txt** os recursos necessários para o Google conseguir renderizar a página, como diretórios de arquivos CSS e JS. É preciso que os robôs tenham acesso para entender que o layout é adaptável.

### Sites dinâmicos

Esse tipo apresenta conteúdos diferentes para usuários em dispositivos móveis usando as mesmas URLs do site desktop. O layout é adaptado via programação no momento do acesso.

Para saber qual conteúdo exibir, o dispositivo que está acessando o site é identificado através do cabeçalho HTTP Vary. Após a identificação do user agent*, o site deve exibir o melhor conteúdo para ele. Isso vai guiar não somente os navegadores dos usuários, mas também os robôs de busca do Google.

### Sites em URLs diferentes (m.site.com)

O site mobile é desenvolvido separadamente e hospedado, geralmente, em um subdomínio _m.site.com_.

Para esse tipo de site mobile é muito importante atentar para as configurações necessárias para preservar o SEO do site. Lembre-se de usar corretamente as tags &#8220;alternate&#8221; e &#8220;canonical&#8221; para prevenir a duplicação de conteúdo e relacionar a versão mobile com a versão desktop.

Nas páginas para desktop `a tag rel="alternate"` indica que exite uma outra versão da página, uma versão alternativa. Essa tag é inserida na seção <head> do HTML, no seguinte formato:

<pre>&lt;link rel="alternate" media="only screen and (max-width: 640px)" href="http://m.site.com.br/pagina-1.html" /&gt;</pre>

Note que a página indicada deve ser a exata correpondente na versão mobile. É errado usar a página inicial do site em todas as tags alternate, por exemplo.

Da mesma forma, **nas páginas para dispositivos móveis** é preciso adicionar, no <head> do HTML de cada página, uma tag rel=&#8221;canonical&#8221; apontando para a URL desktop correspondente. Dessa forma:

<pre>&lt;link rel="canonical" href="http://www.site.com.br/pagina-1.html" /&gt;</pre>

Essa tag vai mostrar ao robô de busca, enquanto ele rastreia as páginas mobile, qual é a versão original da página. Isso previne a duplicação de conteúdo.

Também é possível indicar a URL &#8220;alternate&#8221; através do **sitemap** de páginas. Mas de qualquer forma, a tag &#8220;canonical&#8221; continua sendo necessária nas páginas da versão mobile para correta interpretação dos mecanismos de busca.

Veja como inserir a URL **alternate** **no sitemap**:

<pre class="lang-xml">&lt;?xml version="1.0" encoding="UTF-8"?&gt;
&lt;urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9" xmlns:xhtml="http://www.w3.org/1999/xhtml"&gt;
 &lt;url&gt;
 &lt;loc&gt;http://www.site.com.br/pagina-1.html/&lt;/loc&gt;
 &lt;xhtml:link
     rel="alternate"
     media="only screen and (max-width: 640px)"
     href="http://m.site.com.br/pagina-1.html" /&gt;
 &lt;/url&gt;
&lt;/urlset&gt;</pre>

Além disso também é muito importante fornecer os conteúdos adequados para cada tipo de dispositivo (identificando o user-agent*) através de redirecionamento com **status code 301**. Assim como na configuração de sites dinâmicos (que falamos acima), isso ajuda não somente conduzir o navegador ao melhor conteúdo, como também ajuda os buscadores a saber que o site está preparado para receber acessos via desktop e mobile.

Por fim, deixo um checklist de itens importantes para ter um site mobile bom para SEO

  * Em sites em subdomínios, use corretamente as tags &#8220;alternate&#8221; e &#8220;canonical&#8221; para prevenir a duplicação de conteúdo e relacionar a versão mobile com a versão desktop corretamente;
  * Em sites dinâmicos e em subdomínios direcione os usuários e user-agents* para a versão correta, identificando o dispositivo de acesso.
  * Em sites dinâmicos e responsivos, não bloqueie acesso aos diretórios com os arquivos CSS e JS do layout;
  * Dê a opção de o usuário acessar a versão desktop mesmo se acessar o site a partir de um celular. Ele pode se sentir mais confortável ou necessitar de alguma funcionalidade que existe apenas no desktop;
  * Adapte o conteúdo pensando no comportamento do usuário. Pessoas acessando a partir de celulares geralmente não lêem grandes textos ou esperam uma página muito grande e pesada carregar. Otimize o conteúdo para mobile;
  * Acompanhe o Google Analytics e o Search Console para saber se sua versão mobile está se saindo bem.

Todo o investimento na criação de um site mobile pode ser desperdiçado se a preocupação com SEO e com os usuários não for levada em conta. Ter um site mobile é vital, o diferencial está em torná-lo um aliado das demais estratégias de marketing digital. Não poupe esforços nesse trabalho. Essas são algumas dicas básicas, você pode ir além 😉

_*User-agent: Uma sequência de caracteres que identificam navegadores e outras aplicações web. É através do user-agent que é possível saber qual o dispositivo utilizado pelo usuário (smartphone, computador, etc), qual é o navegador e outros detalhes._

&nbsp;