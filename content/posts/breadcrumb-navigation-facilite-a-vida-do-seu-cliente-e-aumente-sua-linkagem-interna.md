---
title: Breadcrumb Navigation – Facilite a vida do seu cliente e aumente sua linkagem interna
author: Douglas Faria
type: post
date: 2013-08-18
excerpt: |
  |
    Utilizando dados estruturados é possível criar um breadcrumb bem bacana que, além de auxiliar o seu cliente na navegação interna do seu site, aparece nas pesquisas e aumenta sua linkagem interna.
url: /breadcrumb-navigation-facilite-a-vida-do-seu-cliente-e-aumente-sua-linkagem-interna/
dsq_thread_id: 1614078330
categories:
  - SEO
tags:
  - 2013
  - breadcrumbs
  - SEO

---
## O que é Breadcrumb?

É uma estrutura de navegação que auxilia o usuário a se localizar entre as páginas (níveis) do website. Para cada nível da estrutura, é criado um link da sessão correspondente. Assim, caso o usuário queira ir direto para a sessão de Eletrônicos, bastaria clicar no nível “Eletrônico”.  Veja na prática:

[<img class=" wp-image-38563 " alt="Exemplo de Breadcrumb aplicado ao website" src="http://tableless.com.br/uploads/2013/08/exemplo-de-breadcrumb-navigation-588x158.png" width="353" height="95" srcset="uploads/2013/08/exemplo-de-breadcrumb-navigation-588x158.png 588w, uploads/2013/08/exemplo-de-breadcrumb-navigation-329x88.png 329w, uploads/2013/08/exemplo-de-breadcrumb-navigation.png 631w" sizes="(max-width: 353px) 100vw, 353px" />][1]

## Porque eu devo utilizar breadcrumb?

Primeiramente, é uma forma bem legal de demonstrar a organização do seu site, de mostrar ao usuário onde ele está e contextualizá-lo, melhorando a experiência desse visitante.

Outro fator é que o Google privilegia sites que o ajudam a melhorar suas pesquisas com informações de maior relevância. Assim é possível mostrar ao Google essa hierarquia que existe no seu site. Contribua com ele e ele irá contribuir com você!

## Dados Estruturados e Rich Snippets

Dados estruturados são informações formatadas por um padrão comum aos mecanismos de Busca como Google, Bing eYahoo. Através deles o mecanismo refina a busca e obtém informações mais precisas e relevantes. O Google utiliza desse artifício para interpretar e criar [**rich snippets**][2] para o seu site. Veja a imagem:

[<img class="size-medium wp-image-38564" alt="Exemplo direto na pesquisa do Google, utilizando dados estruturados." src="http://tableless.com.br/uploads/2013/08/exemplo-de-breadcrumb-navigation-na-pesquisa-do-google-588x82.png" width="588" height="82" srcset="uploads/2013/08/exemplo-de-breadcrumb-navigation-na-pesquisa-do-google-588x82.png 588w, uploads/2013/08/exemplo-de-breadcrumb-navigation-na-pesquisa-do-google-329x46.png 329w, uploads/2013/08/exemplo-de-breadcrumb-navigation-na-pesquisa-do-google-660x92.png 660w, uploads/2013/08/exemplo-de-breadcrumb-navigation-na-pesquisa-do-google.png 953w" sizes="(max-width: 588px) 100vw, 588px" />][3]

Caso você queira dar uma lida sobre marcação de Dados Estruturados, aqui no Tableless tem um artigo bem bacana do [Thiago Santos][4]:

<http://tableless.com.br/schema-marcacao-de-dados-estruturados/#.Ug0KEZIp-lU>

## Linkagem Interna 

Essa é a grande sacada para aumentar a relevância da página. A linkagem interna, uma estratégia de **Link Building**, é uma ótima prática para sua campanha de SEO, pois aumenta fortemente a navegação e o PageRank da página. Isso acontece quando linkamos outras páginas com alta relevância (Pagerank) na nossa página em questão.

O que você precisa fazer é montar uma boa arquitetura do projeto e escolher os nomes dos níveis de forma estratégica com palavras chave e termos relevantes (sem exageros aqui, por favor!) e criar os links de forma clara e objetiva.

## Mas então, como fazemos o breadcrumb?

É bem simples! Esse é o código de um breadcrumb básico, sem a marcação de dados estruturados:

<pre class="lang-html">&lt;div&gt;

	&lt;a class="hiddenSpellError" href="/eletronicos/"&gt;Eletr&ocirc;nicos&lt;/a&gt; &raquo;

	&lt;a class="hiddenSpellError" href="/eletronicos/televisores/"&gt;Televisores&lt;/a&gt; &raquo;

	&lt;a class="hiddenSpellError" href="/eletr&ocirc;nicos/televisores/tv-led"&gt;TV LED&lt;/a&gt; &raquo;

	&lt;a class="hiddenSpellError" href="/eletronicos/televisores/tv-led/samsung"&gt;Samsung&lt;/a&gt; &raquo;

TV-Slim-LED-32-Full-HD-Samsung-32F5200

&lt;/div&gt;
</pre>

**1. Adicione o atriburo itemprop=&#8221;breadcrumb&#8221;: **

<pre class="lang-html">&lt;div itemprop="breadcrumb"&gt;

	&lt;a class="hiddenSpellError" href="/eletronicos/"&gt;Eletr&ocirc;nicos&lt;/a&gt; &raquo;

	&lt;a class="hiddenSpellError" href="/eletronicos/televisores/"&gt;Televisores&lt;/a&gt; &raquo;

	&lt;a class="hiddenSpellError" href="/eletr&ocirc;nicos/televisores/tv-led"&gt;TV LED&lt;/a&gt; &raquo;

	&lt;a class="hiddenSpellError" href="/eletronicos/televisores/tv-led/samsung"&gt;Samsung&lt;/a&gt;&nbsp; &raquo;

TV-Slim-LED-32-Full-HD-Samsung-32F5200

&lt;/div&gt;
</pre>

**OBS: Repare que a página atual não possui link!**

** 2. Deixe a tag body dessa forma:**

<pre class="lang-html">&lt;body itemscope itemtype="http://schema.org/WebPage"&gt;
</pre>

** 3. Pronto! Agora é só usar e aguardar a indexação do Google!**

## Boas práticas para um bom breadcrumb

  * Use no topo da página, de preferência, logo após o seu Header
  * Não exagere! Utilize nomes estratégicos, mas que beneficiem a navegabilidade do usuário.
  * Crie um design elegante e amigável, nada de extravagâncias aqui!
  * Separe os níveis de forma clara e
  * Destaque os links
  * Defina com clareza a página atual
  * A página atual (último item do breadcrumb) não deve ser link
  * E lembrem-se: Breadcrumbs não substituem a navegação principal

Você também pode usar listas para fazer os breadcrumbs. Não há problema. Subjetivamente, um breadcrumb é uma lista de links, logo, usar listas ordenadas ou até mesmo não ordenadas é totalmente semântico.

Um exemplo usando listas seria assim:

<pre class="lang-html">&lt;div itemprop="breadcrumb"&gt;
	&lt;ul&gt;
		&lt;li&gt;&lt;a class="hiddenSpellError" href="/eletronicos/"&gt;Eletr&ocirc;nicos&lt;/a&gt; &raquo;&lt;/li&gt;

		&lt;li&gt;&lt;a class="hiddenSpellError" href="/eletronicos/televisores/"&gt;Televisores&lt;/a&gt; &raquo;&lt;/li&gt;

		&lt;li&gt;&lt;a class="hiddenSpellError" href="/eletr&ocirc;nicos/televisores/tv-led"&gt;TV LED&lt;/a&gt; &raquo;&lt;/li&gt;

		&lt;li&gt;&lt;a class="hiddenSpellError" href="/eletronicos/televisores/tv-led/samsung"&gt;Samsung&lt;/a&gt;&nbsp; &raquo;&lt;/li&gt;

	&lt;li&gt;TV-Slim-LED-32-Full-HD-Samsung-32F5200&lt;/li&gt;
	&lt;/ul&gt;
&lt;/div&gt;
</pre>

## Conclusão

Não deixe de implementar o Breadcrumb em seu site, pois são vários os benefícios. Com ele você melhora a experiência do usuário e potencializa as chances de aparecer bem nas buscas.

Como é simples de se fazer, torna-se um ótimo recurso para as suas estratégias de SEO e uma forma de mostrar um site mais organizado.

 [1]: http://tableless.com.br/uploads/2013/08/exemplo-de-breadcrumb-navigation.png
 [2]: https://support.google.com/webmasters/answer/99170?hl=pt-BR
 [3]: http://tableless.com.br/uploads/2013/08/exemplo-de-breadcrumb-navigation-na-pesquisa-do-google.png
 [4]: http://tableless.com.br/author/thiagosantos/