---
title: Aplicação da Metatag de Autor no HTML
author: Carina Andrade
type: post
date: 2014-04-30
excerpt: Saiba como usar a metatag de Author e como isso afeta os motores de busca. Principalmente o Google.
url: /aplicacao-das-tags-de-marcacao-de-autor-html/
dsq_thread_id: 2636390936
categories:
  - SEO
tags:
  - google
  - metatag
  - SEO

---
As _tags_ do HTML tem uma função importante para a semântica de uma página. Algumas _meta tags_ são conhecidas e amplamente utilizadas em SEO há muitos anos, como a _description_ (com a descrição curta do conteúdo) e as _keywords_ (com as palavras-chave, hoje já ignorada pelos buscadores). Porém há algum tempo a marcação de autor começou a ganhar espaço nas otimizações de sites, por dois grandes motivos: _Snippets_ (resultados de busca) mais ricos; E a credibilidade passada entre artigo e autor.

## Snippets com Informações do Autor

Muitas vezes, um _title_ e uma _description_ pobre não chamam o usuário para um conteúdo que poderia ser muito bom e atender a expectativa dele. Por isso chamar atenção nos resultados de busca é essencial para garantir que seu conteúdo será visto e acessado.

O Google, sabendo que o usuário, muitas vezes, fica indeciso sobre qual conteúdo acessar, começou a mostrar informações extras nas páginas de resultados. São os chamados _rich scnippets_, ou resultados ricos. Hoje o Google disponibiliza uma série de informações extras, dependendo da consulta. Alguns exemplos são avaliação dos usuários, faixas de um álbum, filmes de um determinado ator e inclusive o autor de um artigo (imagem).

[<img class="alignnone size-full wp-image-42275" src="http://tableless.com.br/uploads/2014/04/snippet-com-author.png" alt="snippet-com-author" width="547" height="109" srcset="uploads/2014/04/snippet-com-author.png 547w, uploads/2014/04/snippet-com-author-400x79.png 400w" sizes="(max-width: 547px) 100vw, 547px" />][1]

Mas como o Google faz essa &#8220;mágica&#8221;? Como ele sabe o nome e tem uma foto do autor do artigo? Muito simples! Através do link com o perfil dele no Google Plus. O autor, por sua vez, precisa colocar em suas informações de perfil na rede social, o link para o blog onde é colaborador.

Feita essa ligação, o Google já sabe informações suficientes sobre quem escreveu o conteúdo para exibi-las na SERP (_Search Engine Results Page_).

## Mais Visibilidade e Credibilidade

Um autor identificado consegue herdar a credibilidade adquirida no Plus e com outras publicações. Assim o Google tem mais facilidade em identificar spam. Matt Cutts, do Google, também se pronunciou certa vez, dizendo que quando há indícios de que um usuário gostou de um determinado artigo, ele provavelmente verá mais artigos do mesmo autor nos resultados de busca.

## Como usar Rel=Author e Rel=Me

A aplicação prática é muito simples. Veja a utilização de Rel=Author com a _tag link_:

<pre class="lang-html">&lt;link rel="author" href="https://plus.google.com/u/0/0000000/posts"/&gt;</pre>

Essa tag deve ser colocada entre as tags <head> do HTML.

**Mas qual a diferença entre as duas? Onde devo colocar cada uma?**

A semântica da aplicação diz o seguinte:

**1.** Quando o site/blog tem apenas um autor, pode ser usada apenas a **_tag rel=me_**, com a URL do perfil do autor.

<pre class="lang-html">&lt;link rel="me" href="https://plus.google.com/u/0/00000000/posts"/&gt;</pre>

**2.** Quando o site/blog tem mais de um autor, nos artigos deve ser inserida a **_tag rel=&#8221;author&#8221;_**, com a URL da página do autor no site (Exemplo: <http://tableless.com.br/author/carina/>). E nessa página do autor no site, deve ser inserida a tag **_rel=me_** com a URL do perfil no Google Plus.

**Obs.:** Vale dizer que inserir um link simples na página (na assinatura, por exemplo) para o perfil do Google Plus usando o atributo _rel=author_ ou _rel=me_ também funciona.

<pre class="lang-html">&lt;a href="https://plus.google.com/u/0/0000000/posts"/ rel="author"&gt;Autor&lt;/a&gt;</pre>

Vale lembrar que a marcação deve ser inserida apenas em páginas que tenham um texto ou artigo. Vai contra as diretrizes do Google usar a _tag_ em páginas de categoria ou contato, por exemplo.

## E no perfil do Google Plus?

No perfil do Google Plus você encontra as informações de links e sites onde o usuário é colaborador, na aba Sobre, em seguida na seção Links.

[<img class="alignnone size-full wp-image-42287" src="http://tableless.com.br/uploads/2014/04/author-google-plus.png" alt="author-google-plus" width="759" height="494" srcset="uploads/2014/04/author-google-plus.png 759w, uploads/2014/04/author-google-plus-400x260.png 400w" sizes="(max-width: 759px) 100vw, 759px" />][2]

Pronto, é só inserir o link do Blog em que você escreve.

O Google também recomenda que o autor utilize uma foto sua no perfil. Perfis com foto de um animal, por exemplo, o mecanismo evita exibir nos resultados.

## Como testar?

Você pode testar se suas marcações deram certo na [ferramenta de teste de dados estruturados do próprio Google][3]. Mesmo que os dados do autor ainda não estejam aparecendo nos resultados de busca, se tudo estiver funcionando, o preview irá mostrar.

[<img class="wp-image-42288 aligncenter" src="http://tableless.com.br/uploads/2014/04/testar-rich-snippets.png" alt="testar-rich-snippets" width="696" height="338" srcset="uploads/2014/04/testar-rich-snippets.png 836w, uploads/2014/04/testar-rich-snippets-400x194.png 400w" sizes="(max-width: 696px) 100vw, 696px" />][4]

## Estatísticas do Autor

Com as marcações funcionando, outra vantagem é acompanhar as impressões e cliques dos seus artigos através da Webmaster Tools, em Estatísticas do Autor (acessar com a mesma Google Account do Google Plus): <https://www.google.com/webmasters/tools/labs-author-stats-1>

## Concluindo

Ainda há muito o que descobrir sobre essa relação que o Google estabelece entre o autor de um artigo e sua rede social. Recentemente o buscador reduziu drasticamente a quantidade de resultados com informação de autor. Nota-se que aqueles autores que estão em mais círculos do Google Plus são os que continuaram aparecendo na SERP.

É importante lembrar que os resultados com fotos e informações do autor podem demorar para aparecer, assim como podem aparecer somente para alguns artigos. Vai depender muito da relevância da página e também da autoridade do usuário no Google Plus. Portanto se você é colaborador de algum blog, é legal manter um perfil ativo no Google Plus e começar a ganhar autoridade como usuário.

Para manter a estratégia correta é bom estar atento às próximas novidades do Google, principalmente se o Google Plus começar a ganhar mais espaço entre as redes sociais. Em 2014 é possível que o G+ comece a receber mais usuários ativos, já que recentemente o Google abriu espaço para anúncios com +Plus Ads, o que provavelmente atrairá anunciantes para lá.

 [1]: http://tableless.com.br/uploads/2014/04/snippet-com-author.png
 [2]: http://tableless.com.br/uploads/2014/04/author-google-plus.png
 [3]: http://www.google.com.br/webmasters/tools/richsnippets
 [4]: http://tableless.com.br/uploads/2014/04/testar-rich-snippets.png