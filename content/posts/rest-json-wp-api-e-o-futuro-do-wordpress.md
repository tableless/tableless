---
title: WP Rest API – O futuro do WordPress
author: Cezar Augusto
type: post
date: 2015-12-07
excerpt: 'Conheça o futuro do WordPress: uma API RESTFul, a ser integrada no Core, que dispõe em formato JSON todas as informações necessárias para o desenvolvimento agnóstico em WordPress. Esteja pronto para criar aplicações Web/Mobile utilizando o WordPress ou utilize seus conhecimentos na sua linguagem de programação favorita e diga <em>adeus</em> ao PHP.'
url: /rest-json-wp-api-e-o-futuro-do-wordpress/
categories:
  - Tecnologia e Tendências
  - Wordpress
tags:
  - api
  - json
  - rest
  - RESTful
  - Wordpress
  - wp

---
## TL;DR

O WP-API é a nova aposta do WordPress. Atualmente, funciona como um plugin do WordPress, a ser incorporado em duas etapas no Core, que expõe o conteúdo em uma arquitetura REST dispondo-o em formato JSON, pronto para consumo em outras linguagens/sites/aplicações/aplicativos.

## Índice

  * [Conceito][1]
  * [O que o API significa para o WordPress?][2]
  * [Se esse é o futuro, do que o WP-API é capaz?][3] 
      * [Romper laços com o PHP][4]
      * [Fazer uma integração mobile de verdade.][5]
      * [Front-End modular][6]
      * [Back-End com a sua assinatura][7]
      * [Mais um incentivo para você entrar na vibe do JavaScript e seguir a nova ordem mundial][8]
  * [Ao expôr meu conteúdo, o WP-API não oferece nenhum risco à segurança?][9]
  * [Como funciona o WP-API][10] 
      * [Um pouco de HTTP][11]
      * [O que significa REST?][12]
      * [API? é tipo&#8230; APP?][13]
  * [Instalando o plugin e fazendo sua primeira requisição][14] 
      * [Para obter uma lista de Posts][15]
      * [Para visualizar um post específico][16]
      * [Para obter uma lista de Páginas][17]
      * [Para visualizar uma página especifica][18]
      * [Requisitando uma Categoria ou tag de determinado post][19]
      * [Obtendo uma lista de Categorias][20]
      * [Lista de Tags][21]
      * [Lidando e visualizando conteúdo com Custom Post Types][22]
      * [Usando o ACF? Você ainda está na zona de conforto!][23]
  * [Palavras finais][24]

## Conceito {#conceito}

Considerada a próxima grande aposta do WordPress (plataforma utilizada por ~25% dos sites em todo mundo), com a primeira fase prevista para a versão 4.4 em dezembro deste ano (2015) e integração total na versão 4.5, o WP-API (também conhecido como JSON API ou REST API) expõe as informações de um site feito em WordPress para que sites externos/aplicações/aplicativos consumam seus dados. Na data deste artigo, o WP-API está disponível como <a href="https://wordpress.org/plugins/rest-api/" target="_blank">plugin</a> e os desenvolvedores estão otimistas sobre a  <a href="https://make.wordpress.org/core/tag/json-api/" target="_blank">integração com o core do WP</a>.

O WP-API foi criado para facilitar a interação de sites em WordPress com outros sites/aplicações. O API permite que outros serviços sejam integrados ao WordPress e abre a possiblidade para que os mesmos criem, leiam, atualizem e deletem seu conteúdo (CRUD), sem necessariamente terem uma instalação local do WordPress.

**Antes que você questione:** sem autenticação, apenas a leitura do conteúdo é possível. [Mais abaixo][9]

Imagine [desenvolver seu blog em WordPress usando Rails? Django? Node? Java???][4]

_Quê cara, tá maluco? Que post é esse?_

Essa realidade é possível porque a Web é feita de [HTTP][11], que tem equivalentes CRUD com seus verbos POST, GET, PUT e DELETE, e o [API][13] é feito usando uma [arquitetura REST][12].

No momento, desenvolver em WordPress requer algum conhecimento em PHP. Com o API, o PHP se tornará algo estritamente opcional, habilitando o desenvolvedor a utilizar seus conhecimentos em HTML, CSS e JavaScript/Ruby/Python/C#/FORTRAN (ok, forcei), o que for, para desenvolver seus temas, integrações, aplicações mobile e tudo o que a juventude de agora gosta de desenvolver. _A saber_: um API é uma porção de códigos que permite que outras aplicações acessem seus dados na web em uma forma mais simples (vide o API do YouTube, Facebook, Instagram e agora o WordPress).
  
Sendo um API RESTful, o WP-API permite que aplicações bem interessantes sejam criadas [utilizando uma interface JSON][10].

## O que o API significa para o WordPress? {#prowp}

VIDA. FUTURO. DOMINAÇÃO DO MERCADO. UM APLICATIVO DA SUA EMPRESA CONSUMINDO DATA DO SITE FEITO EM WORDPRESS.

<img class="size-large wp-image-52378 aligncenter" src="http://tableless.com.br/uploads/2015/11/wp.jpg" alt="wp" width="280" height="157" />

O API evolui o WordPress como um CMS para uma aplicação completa. Veja: o API cria um padrão para que outras linguagens consigam interagir diretamente com seu conteúdo.

## Se esse é o futuro, do que o WP-API é capaz? {#futuro}

Com a pretensão de usar a força da marca para incentivar desenvolvedores de outras linguagens a construir suas aplicações utilizando o WordPress, sejam elas plugins, temas, integrações, aplicações ou aplicativos, o WP-API amplifica o leque do WordPress à um nível inimáginável há alguns anos e talvez faça você perder seu preconceito. A ferramenta chega com as seguintes promessas:

### Romper laços com o PHP {#php}

À parte da cultura da boca-torta criada no passado, o PHP ainda é a força-motriz por trás de 80% dos sites do mundo e tem o suporte de gigantes como Facebook, Wikipedia e o próprio WordPress. Entretanto, nos últimos anos houveram avanços significativos em linguagens como Ruby, Python, Go e claro, JavaScript, seja em termos de ferramentas, escalabilidade ou frameworks disponíveis.

O WP-API dá aos desenvolvedores dessas linguagens acesso imediato à todo o leque de funcionalidades do WordPress. Razão suficiente para captar a atenção dos desenvolvedores e proprietários de sites. Quando pensamos na grandiosidade do ecossistema do WordPress e nas possibilidades que os desenvolvedores tem de gerar receita com ele (sejam temas ou plugins), o potencial de portar sites inteiros feitos em WordPress para outras linguagens/plataformas é algo tentador em termos de experiência e, claro, receita.

### Fazer uma integração mobile de verdade. {#mobile}

Com a popularização de frameworks como Foundation e Bootstrap, grande parte dos sites desenvolvidos nos últimos anos chegaram a um padrão aceitável em termos de visualização de conteúdo em dispositivos móveis, mas uma integração de verdade está longe de ser um padrão.

Estava.

Usando o WP-API, desenvolvedores mobile poderão lidar com sites em WordPress como lidariam com qualquer serviço de <a href="https://en.wikipedia.org/wiki/Mobile_Backend_as_a_service" target="_blank">Mobile Back End as a Service (MBaaS ou BaaS)</a>. Este ponto sozinho já é suficiente para habilitar um site em WordPress como uma possibilidade para servir de backend para aplicações mobile nativas e serve de fundação para todos os tipos de integrações no futuro.

Quando considerada a quantidade de sites rodando WP, que têm uma versão completamente distinta de suas versões mobile, o escopo para integrações futuras é imenso. O ideal de ter um banco de dados e diversas aplicações consumindo suas informações, agora é possível de forma genuína e descomplicada.

### Front-End modular {#frontend}

Do ponto de vista do API, o front-end do WordPress é só mais uma aplicação externa consumindo seus dados. Aplicações MVW (model, view, whatever) como AngularJS, EmberJS, MeteorJS, BackboneJS, poderão facilmente fazer suas requisições e montar o workflow dos seus sonhos sem se preocupar com as entrelinhas de desenvolvimento em WP.
  
A expectativa é ver uma revolução em plugins e temas para desenvolvedores e donos de site ao redor do mundo (são 25% da web, considere).

### Back-End com a sua assinatura {#backend}

A potencial integração do REST API no core abre a possibilidade de reimaginar o admin do WordPress. Imagine que todas as funcionalidades do core estão abertas à você, com nenhum visual para te limitar. Chega de editar cores e imagens para tentar deixar o admin &#8220;do seu jeito&#8221;, ou baixar o <a href="https://wordpress.org/plugins/user-role-editor/" target="_blank">User Role Editor</a> para proibir seus clientes de destruírem seu trabalho, ou usar uma função para injetar CSS com um <tt>"display: none"</tt> em coisas que você não gostaria que estivessem visíveis. Com o API, o controle é todo seu.

### Mais um incentivo para você entrar na vibe do JavaScript e seguir a nova ordem mundial {#javascript}

Convenhamos: o JavaScript está criando uma nova ordem mundial. É hype, é futuro, é presente, opiniões divergentes. Em comum: é JavaScript. Frameworks MV** e outros menos conhecidos estão ditando uma tendência, que acredito seguir linear por um bom tempo.

O WP-API faz do WordPress um companheiro ideal para essas tecnologias. Na visão de desenvolvedor, poder utilizar tecnologias de vanguarda mantendo sua bagagem em WordPress, é o mundo ideal.

## Ao expôr meu conteúdo, o WP-API não oferece nenhum risco à segurança? {#seguranca}

Não. Não propriamente por conta do WP-API.

A informação que o API fornece é, naturalmente, o que um site WordPress dispõe por padrão publicamente. A única diferença entre o front-end de um site e o WP-API é a forma como as informações são apresentadas. Por padrão não é possível, sem autenticação, apagar, atualizar ou criar nada &#8211; apenas ler o conteúdo (requisição GET).

Claro que novas funcionalidades expõem novos riscos. Porém, por ora, nenhuma vulnerabilidade foi encontrada e manter seu WordPress atualizado é um método simples e confiável de se manter seguro.

## Como funciona o WP-API {#como}

O WP-API é acessado por HTTP e retorna requisições em formato JSON. Ambos fáceis de utilizar e com grande suporte pelas linguagens de programação mais populares, através de bibliotecas como Net::HTTP (Ruby), Requests (Phyton) e GoReq (Go), para citar alguns.

Eu poderia me limitar a dizer que o WP-API é uma REST API, o que ficaria abstrato e não é o objetivo do artigo. O WP-API é empolgante, mas se você não tem nenhuma base sobre o que significa uma arquitetura REST, HTTP e requisições em geral, procurei expôr os conceitos mais básicos abaixo.

Antes de falar de REST, é necessário entender alguns conceitos de HTTP.

### Um pouco de HTTP {#http}

Ele assina pelo nome de Hypertext Transfer Protocol (HTTP) e é um conjunto de regras que determina como informações podem ser enviadas e recebidas e quais mensagens devem ser retornadas em resposta às requisições.

Por exemplo, quando uma requisição é enviada pelo cliente e recebida com sucesso pelo servidor, a mensagem (conhecida como código de retorno, acompanhado de uma frase explicativa) é um variante de 200 (onde o número mais importante é a casa da centena, onde 2 significa sucesso na requisição). A mais famosa talvez seja a 404 &#8211; Not Found, que retorna um valor inexistente para sua requisição (onde o primeiro número quatro significa _erro no cliente_).

Outros protocolos bem conhecidos são o POP3 e o SMTP, que são usados para receber e enviar e-mails, respectivamente.

O HTTP tem duas funções distintas: servidor e cliente. Em geral, o cliente envia a requisição e o servidor responde. É feito basicamente do _header_ (que contém metadata e informações importantes para o HTTP) e do _body_ (que contém o conteúdo da mensagem).
  
Hypertext Transfer Protocol ou HTTP é a alma da web. É utilizado todas as vezes que você transfere um documento, ou faz uma solicitação AJAX.

Se quiser mais informações, o TutsPlus tem <a href="http://code.tutsplus.com/tutorials/a-beginners-guide-to-http-and-rest--net-16340" target="_blank">um ótimo tutorial</a>, que usei como referência, com uma <a href="http://code.tutsplus.com/pt/tutorials/a-beginners-guide-to-http-and-rest--net-16340?ec_unit=dropdown-language" target="_blank">igualmente ótima tradução</a> feita pelo <a href="http://tutsplus.com/authors/thierry-rene" target="_blank">Thierry Rene</a>. Vale cada palavra.

Concordo com o autor do link de referência sobre o conhecimento de HTTP não ser comum entre desenvolvedores, o que também considero importante e recomendo a leitura.

### O que significa REST? {#rest}

<img class="alignnone size-medium wp-image-52376" src="http://tableless.com.br/uploads/2015/11/rest.jpg" alt="rest" width="279" height="157" />
  
REST é definido por _Representational State Transfer_! Entendi tudo, deixa eu dormir agora, obrigado.

> Arquitetura: De acordo com uma citação do <cite><a href="https://pt.wikipedia.org/wiki/Arquitetura" target="_blank">Wikipedia</a></cite>: a arquitetura lidaria com qualquer problema de agenciamento, organização, estética e ordenamento de componentes em qualquer situação de arranjo espacial.

Uma arquitetura REST é uma uma forma de organizar as interações entre sistemas. Ele define padrões, o que pode e o que não se deve fazer. A arquitetura fornece uma forma padronizada de como acessar dados. Em geral, sistemas seguem um padrão de comandos. Execute informação X, receba informação Y. Em uma arquitetura REST, o acesso é fornecido por recursos. O que significa que, em uma URL, tudo o que é passado são recursos que podem ser consumidos, não existem comandos inseridos e procura-se utilizar uma URL _humanamente legível_.

#### Exemplo de comando em uma URL.

Supondo que eu, ao acessar o site de minha empresa, gostaria de procurar por um vendedor admitido em 2015:

<pre class="lang-html">http://siteincrivel.com.br/equipe.php?funcao=vendedor&admissao=2015</pre>

Repare na instrução ao servidor: busque por vendedores admitidos em 2015. Enquanto a instrução pode ser facilmente interpretada, _equipe_ não é um recurso.

Se a requisição fosse feita em uma arquitetura REST, minha URL seria:

<pre class="lang-html">http://siteincrivel.com.br/equipe/admissao/2015/funcao/vendedor/</pre>

A URL, sem parâmetros, identifica o recurso que você deseja manipular de forma que eu obtenha informações precisas em todas as camadas. Fazer a requisição em um diretório retorna uma lista de recursos. Por exemplo, retirar &#8220;vendedor&#8221; da URL poderia me fornecer informações sobre todas as funções contratadas no ano de 2015.

Veja: a arquitetura não abomina o uso de parâmetros na URL, que podem ser utilizados como uma espécie de filtro ou outra forma conveniente.

Por fim, os sistemas que seguem os princípios REST são chamados de RESTFul.

### API? é tipo&#8230; APP? {#api}

Não, não.

Um API (application programming interface) é uma forma simples de se comunicar com uma aplicação. Através de <u>endpoints*</u> definidos, os desenvolvedores podem fazer seus programas e scripts interagirem com a aplicação.

* Endpoints são definidos por suas funções, que podem ser acessados por HTTP. É a forma que o WP-API (que agora que você pegou a manha eu posso dizer: é um REST API) provê suas informações e permite seus desenvolvedores manipularem o WordPress, podendo ser a publicação de um post, atualização de uma página ou a exclusão de um comentário.

Certo, Cezar. Tudo isso parece mágico, linda teoria. Agora, como posso começar com o WP-API?

## Instalando o plugin e fazendo sua primeira requisição {#instalacao}

<img class="alignnone size-full wp-image-52375" src="http://tableless.com.br/uploads/2015/11/plugin_v2b.jpeg" alt="plugin_v2b" width="766" height="343" />
  
Os exemplos utilizados requerem a versão 2 do API. Para baixá-lo, vá ao repositório do WordPess: <a href="https://wordpress.org/plugins/rest-api/" target="_blank">https://wordpress.org/plugins/rest-api/</a>

Depois de baixado, basta fazer a instalação. A instalação ocorre da mesma forma que qualquer outro plugin do WordPress.

### Visualizando o conteúdo _like a boss_ ou A primeira requisição a gente nunca esquece

Se você usa o Chrome, baixe a extensão do <a href="https://chrome.google.com/webstore/detail/postman/fhbjgbiflinjbdggehcddcbncdddomop" target="_blank">Postman</a>. O postman, dentre suas finalidades, vai servir para o propósito de visualizar o conteúdo da maneira correta.

#### Para todas as requisições que faremos, tome nota dessa instrução

Para visualizar sua primeira requisição, abra o Postman (você pode digitar o endereço no browser diretamente, se você não se importar com um monte de código chapado na tela) e digite na URL (válido para todos os exemplos abaixo):

<pre class="lang-html">http://siteincrivel.com.br/wp-json/wp/v2/REQUISIÇÃO_AQUI.</pre>

Onde _siteincrivel_ é o seu site e _REQUISIÇÃO_AQUI_ será a requisição que vocẽ deseja fazer, dentre as possibilidades:

### Para obter uma lista de Posts {#posts}

<pre class="lang-html">http://siteincrivel.com.br/wp-json/wp/v2/posts</pre>

### Para visualizar um post específico {#post}

<pre class="lang-html">http://siteincrivel.com.br/wp-json/wp/v2/{id}</pre>

Onde {id} é o ID do Post que você precisa.

### Para obter uma lista de Páginas {#paginas}

<pre class="lang-html">http://siteincrivel.com.br/wp-json/wp/v2/pages</pre>

### Para visualizar uma página especifica: {#pagina}

<pre class="lang-html">http://siteincrivel.com.br/wp-json/wp/v2/pages/{id}</pre>

Onde {id} é o ID da página que você precisa.

### Para visualizar uma lista de categorias ou tags

Categorias e Tags são consideradas taxonomias. As taxonomias, diferente de posts e páginas, funcionam pelo slug e não pelo ID. O ID é necessário apenas para chamadas de Posts/Páginas.

Os elementos de uma categoria ou tag, são consideradas pelo WordPress como termos (terms). Portanto ao criar a categoria _Marketing_, você está dizendo ao WordPress que a taxonomia Categoria tem um termo chamado _Marketing_.

Sendo assim:

### Requisitando uma Categoria ou tag de determinado post: {#catags}

<pre class="lang-html">http://demo.wp-api.org/wp-json/wp/v2/posts/{id_do_post}/terms/category/</pre>

<pre class="lang-html">http://demo.wp-api.org/wp-json/wp/v2/posts/{id_do_post}/terms/tag/</pre>

### Obtendo uma lista de Categorias {#cat}

Nossa categoria modelo (Marketing) deverá aparecer aqui

<pre class="lang-html">http://siteincrivel.com.br/wp-json/wp/v2/terms/category</pre>

### Lista de Tags {#tag}

<pre class="lang-html">http://seusite.com.br/wp-json/wp/v2/terms/tag</pre>

### Lidando e visualizando conteúdo com Custom Post Types: {#cpt}

Por padrão, o WP-API não autoriza a visualização direta de CPT. Para autorizar a requisição, abra o arquivo onde você armazena as informações sobre CPT do seu tema (em geral no <tt>functions.php</tt>, ou qualquer <tt>include</tt> que você tenha feito) e adicione o argumento (dentro de <tt>$args</tt>, por favor):

<pre class="lang-html">show_in_rest =&gt; true</pre>

Caso você tenha feito corretamente, o endereço abaixo vai listar os posts relacionados àquele CPT:

<pre class="lang-html">http://siteincrivel.com.br/wp-json/wp/v2/{nome_do_cpt}</pre>

### Usando o ACF? Você ainda está na zona de conforto! {#acf}

A integração com o ACF é extensa para o objetivo do post, o que não importa muito, pois <a href="https://wordpress.org/plugins/acf-to-wp-api/" target="_blank">existe um plugin excelente</a> que cumpre a maioria das finalidades do ACF. Seja feliz.

## Palavras finais {#final}

Vejo em muitos grupos e em alguns sites sobre o futuro do WordPress, que o sistema está em declínio e alguns absurdos também. O WP-API é uma grande aposta e suas promessas fazem merecer um olhar atento à nova funcionalidade.

Se quiser um _modelo_ para começar, pode tentar o <a href="https://github.com/Automattic/picard" target="_blank">Picard</a>, feito em ReactJS pela própria Automattic, ou se quiser uma ideia sobre mais possibilidades do API, o Make WordPress Core tem uma <a href="https://make.wordpress.org/core/2015/07/23/rest-api-whos-using-this-thing/" target="_blank">thread</a> sobre aplicações que desenvolvedores estão trabalhando.

E você, tem alguma opinião a respeito? Desenvolveu alguma aplicação com o WP-API? Deixe um comentário, eu adoraria saber!

<cite>Referências:</cite>

  * <a href="http://wp-api.org/" target="_blank">http://wp-api.org/</a>
  * <a href="https://feelingrestful.com/" target="_blank">https://feelingrestful.com/</a>
  * <a href="http://observer.com/2015/07/wordpress-rest-api/" target="_blank">http://observer.com/2015/07/wordpress-rest-api/</a>
  * <a href="http://jacklenox.com/2015/03/30/building-themes-with-the-wp-rest-api-wordcamp-london-march-2015/" target="_blank">http://jacklenox.com/2015/03/30/building-themes-with-the-wp-rest-api-wordcamp-london-march-2015/</a>
  * <a href="http://torquemag.io/client-side-applications-powered-by-the-wordpress-json-rest-api/" target="_blank">http://torquemag.io/client-side-applications-powered-by-the-wordpress-json-rest-api/</a>
  * <a href="https://premium.wpmudev.org/blog/wordpress-rest-api/" target="_blank">https://premium.wpmudev.org/blog/wordpress-rest-api/</a>
  * <a href="https://wpengine.com/blog/josh-pollock-wordpress-rest-api-finely-tuned-consultant/" target="_blank">https://wpengine.com/blog/josh-pollock-wordpress-rest-api-finely-tuned-consultant/</a>
  * <a href="http://premium.wpmudev.org/blog/using-wordpress-rest-api/" target="_blank">http://premium.wpmudev.org/blog/using-wordpress-rest-api/</a>
  * <a href="https://apppresser.com/wp-api-post-submission/" target="_blank">https://apppresser.com/wp-api-post-submission/</a>
  * <a href="https://blog.nexcess.net/2015/06/04/what-does-the-new-rest-api-mean-for-wordpress/" target="_blank">https://blog.nexcess.net/2015/06/04/what-does-the-new-rest-api-mean-for-wordpress/</a>
  * <a href="http://www.wpwhitesecurity.com/wordpress-security/wordpress-rest-api-and-the-security-worries/" target="_blank">http://www.wpwhitesecurity.com/wordpress-security/wordpress-rest-api-and-the-security-worries/</a>
  * <a href="http://www.sitepoint.com/wp-api/" target="_blank">http://www.sitepoint.com/wp-api/</a>
  * <a href="https://1fix.io/blog/2015/07/20/query-vars-wp-api/" target="_blank">https://1fix.io/blog/2015/07/20/query-vars-wp-api/</a>
  * <a href="http://code.tutsplus.com/tutorials/a-beginners-guide-to-http-and-rest--net-16340" target="_blank">http://code.tutsplus.com/tutorials/a-beginners-guide-to-http-and-rest&#8211;net-16340</a>
  * <a href="https://make.wordpress.org/core/2015/07/23/rest-api-whos-using-this-thing/" target="_blank">https://make.wordpress.org/core/2015/07/23/rest-api-whos-using-this-thing/</a>

 [1]: #conceito
 [2]: #prowp
 [3]: #futuro
 [4]: #php
 [5]: #mobile
 [6]: #frontend
 [7]: #backend
 [8]: #javascript
 [9]: #seguranca
 [10]: #como
 [11]: #http
 [12]: #rest
 [13]: #api
 [14]: #instalacao
 [15]: #posts
 [16]: #post
 [17]: #paginas
 [18]: #pagina
 [19]: #catags
 [20]: #cat
 [21]: #tag
 [22]: #cpt
 [23]: #acf
 [24]: #final