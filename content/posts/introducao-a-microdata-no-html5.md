---
title: Introdução a Microdata no HTML5
authors: Talita Pagani
type: post
date: 2010-12-20
excerpt: De forma similar aos microformats, microdata do HTML5 permite representar determinadas informações de forma mais semântica.
url: /introducao-a-microdata-no-html5/
categories:
  - html
tags:
  - html5
  - Tecnologia e Tendências
  - microdados
  - microdata
  - microformats
  - Semântica
---
Provavelmente você já ouviu falar de [microformats][1], um padrão que permite representar informações de modo mais semântico no XHTML, como, por exemplo, informações de contato (_hCard_) ou dados de um evento (_hCalendar_).

No HTML5, temos o _microdata_, conceito semelhante aos microformats e RDFa, um padrão de representação de informações que estende as potencialidades semânticas do HTML5.

As informações representadas através de _microdata_ utilizam elementos pertencentes a um vocabulário específico que deve ser referenciado no documento HTML. O vocabulário é a especificação das propriedades utilizadas e qual tipo de informação elas representam.

Atualmente, vocabulários de _microdata_ podem ser encontrados no site <https://www.data-vocabulary.org/>, contendo especificações para descrever eventos, empresas, pessoa, produto e até breadcrumbs (caminhos de navegação de um site). No site podem ser encontradas as propriedades referentes a cada especificação e uma descrição de finalidade e utilização.

Ao utilizar este tipo de padrão para descrição de dados, você possibilita que mecanismos de busca entendam estas informações dentro do contexto semântico definido e facilita a outras aplicações reconhecer e importar estes dados de seu site. E isto não é uma projeção para o futuro, o mecanismo de busca do Google já reconhece _microdata_ e possui artigos no [Help Center do Webmasters Tools][2], portanto, já pode ser utilizado.

### Como utilizar microdata no HTML5

Primeiro é preciso determinar uma tag que será o escopo do _microdata_, ou seja, será o elemento que contém as informações. Para isso, essa tag deve possuir a propriedade **itemscope** e também a propriedade **itemtype** com o valor indicando o vocabulário de _microdata_ a ser utilizado para que o mecanismo de busca saiba que tipo de informação irá encontrar dentro das tags deste elemento.

Vamos exemplificar que desejamos exibir um microdata com informações de uma organização. Primeiro definimos uma **div** como escopo:

<pre class="lang-html">&lt;div itemscope itemtype="https://data-vocabulary.org/Organization"&gt;
&lt;/div&gt;
</pre>

As tags que estarão dentro desta **div** devem conter a propriedade **itemprop** para identificar qual elemento (propriedade) aquela tag estará representando. No caso do vocabulário _Organization_ temos elementos como name (nome da empresa), tel (telefone), geo (coordenadas geográficas como latitude e longitude), entre outras. Também é possível adicionar microdata aninhado, ou seja, outro vocabulário microdata para detalhar alguma informação.

Neste exemplo, além das propriedades do vocabulário _Organization_, iremos também utilizar de modo aninhado o microdata _Address_, especificando detalhes do endereço.

<pre class="lang-html">&lt;div itemscope itemtype="https://data-vocabulary.org/Organization"&gt;
    &lt;h1 itemprop="name"&gt;Tableless &ndash; Treinamento e Desenvolvimento Web&lt;/h1&gt;
    &lt;p itemprop="tel"&gt;11 9999-9999&lt;/p&gt;
    &lt;p itemprop="address" itemscope itemtype="https://data-vocabulary.org/Address"&gt;
      &lt;span itemprop="street-address"&gt;Rua do Tableless, 232&lt;/span&gt;,
      &lt;span itemprop="locality"&gt;S&atilde;o Paulo&lt;/span&gt;,
      &lt;span itemprop="region"&gt;SP&lt;/span&gt;.
    &lt;/p&gt;
&lt;/div&gt;
</pre>

Utilizar tecnologias como _microdata_, _microformarts_ ou _RDFa_ só vem a enriquecer as informações que podem ser oferecidas em páginas HTML e ajudar a construir uma web mais semântica.

Saiba mais sobre microdata no artigo [Microdata: HTML5’s Best-Kept Secret][3].

 [1]: https://tableless.com.br/para-ficar-de-olho-microformats "Microformatos"
 [2]: https://www.google.com/support/webmasters/bin/topic.py?topic=21997
 [3]: https://www.webmonkey.com/2010/09/microdata-html5s-best-kept-secret/