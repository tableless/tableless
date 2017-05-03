---
title: Seja um autor
excerpt: Escreva conosco e compartilhe conteúdo com o Brasil inteiro.
author: Diego Eis
type: page
date: 2016-04-09
---

Este é o canal para que todos os interessados em compartilhar ideias, ensinar ou expor opiniões sobre assuntos ligados ao mercado de web possam colaborar. Se você estava esperando uma oportunidade, a hora é essa. ;-)

## Quem pode ser um autor?

Qualquer um. Se você está interessado, leia atentamente os próximos parágrafos:

O Tableless é um projeto aberto, logo, para submeter um artigo para nós, basta [escrever seu artigo e enviar um Pull Request](https://github.com/tableless/tableless-static/new/master/content/posts). Nós iremos avaliar e provavelmente sugerir algumas modificações. Como é um projeto aberto, a comunidade também pode olhar e sugerir modificações no seu texto. Não se envergonhe.

## Cuidado com artigos repetidos

Se você já publicou algum artigo repetido no seu blog pessoal, tudo bem. Mas tente não publicar artigos que já foram publicados em outros sites de conteúdo. Geralmente o Google não gosta disso e muito provavelmente o seu leitor já vai ter lido esse artigo em outros sites. Mesmo assim, fique à vontade para publicar o que achar que seja elevante. 

## Tópicos principais

Você pode escrever qualquer assunto relacionado aos tópicos abaixo. Se você achar necessário, sugira um novo tópico para incluirmos na lista:

*   **HTML:** HTML5, linguagens de marcação, semântica, novidades;
*   **JavaScript:** JQuery, linguagem, métodos, truques, soluções, tutoriais etc;
*   **CSS:** técnicas, truques, teorias, práticas, soluções, tutoriais;
*   **Wordpress:** criação de temas, plugins, técnicas, massetes, truques, tutoriais;
*   **UX e Design**: processo, prática, dicas, truques, soluções, tutoriais;
*   **Tipografia:** seleção de fonts, ferramentas, tutoriais, design;
*   **Back-end** ruby, php, python, truques, dicas, tutoriais;
*   **Mobile:** desenvolvimento, técnicas, métodos, responsive, design, iPad, iPhone, Android, Blackberry, Windows Phone;
*   **Photoshop** e **Illustrator**: truques, técnicas, tutoriais;
*   **Freebies:** coleções de ícones, themes, templates, plugins etc;
*   **Ferramentas:** dicas de editores, browsers, scripts etc;
*   **Browsers:** notícias e novidades, truques, mercado, serviços e features;
*   **Notícias:** notícias relacionadas ao desenvolvimento web e o mercado de web/internet;
*   **Mercado:** cenário atual do mercado como um todo;
*   **Agile:** metodologias ágeis, gestão e relacionados;

## O que nunca vamos publicar

*   Press Releases. Nós não iremos publicar nenhum press release, ao menos nenhum de graça. Por isso ["vendemos" um espaço para quem quer anunciar no site.](http://tableless.com.br/anuncie-no-tableless/) ;-)
*   Venda de produtos. A não ser que você [queira anunciar aqui no Tableless](http://tableless.com.br/anuncie-no-tableless/), nós não vamos publicar nada desse tipo.

## Submeta agora seu artigo

Os artigos são baseados em Markdown. Logo, você precisa escrever ou converter seu texto para Markdown antes de submeter para nós. Se você tiver um artigo em HTML, você pode convertê-lo [usando esse serviço](https://domchristie.github.io/to-markdown/). Além disso, é *OBRIGATÓRIO* o padrão de frontmatter no seu artigo, como segue abaixo:

Para submeter seu artigo, siga os passos:

1. Você não precisa clonar o projeto para submeter um artigo, apenas [siga esse link](https://github.com/tableless/tableless-static/new/master/content/posts) e escreva/cole o artigo em Markdown. Esta é a página de criação de novo arquivo no GitHub que você já deve conhecer;
2. Coloque o nome do seu arquivo seguindo esse padrão: **nome-do-artigo.md**. 
3. Se seu artigo fizer uso de imagens, suba-o em algum serviço de host de imagens como o [imgh.us](imgh.us) ou [imgur.com](imgur.com) e coloque apenas o endereço da imagem no artigo;
4. Depois de ter terminado, logo abaixo da área de escrita, há um campo para escrever as informações de commit. Coloque um título no commit e uma descrição sobre o artigo;
5. Feito isso, selecione a opção **Create a new branch for this commit...** e submeta um Pull Request para a branch Master;
6. Aguarde os comentários e a aprovação do pessoal do Tableless; Sucesso! :-D

**ATENÇÃO:** Se seu artigo usar imagens, use serviços como o [imgur.com](imgur.com) para exibir suas imagens. Nós não versionamos as imagens do seu artigo.

Qualquer dúvida, pode falar conosco via [twitter](http://twitter.com/tableless/) ou nos envie um [e-mail](mailto:contato@tableless.com.br).

### Frontmatter
<pre class="lang-yaml">
---
title: Nome do seu artigo
author: Seu nome
type: post
image: http://imgur.com/endereco-da-imagem-de-destaque.jpg
date: 2017-01-19
excerpt: Um resumo do seu artigo. Não precisa ser muito longo, mas o suficiente para que os usuários saibam em poucas palavras sobre o que é o seu artigo. É aqui que eles se interessarão pelo seu texto.
categories:
  - Browsers
  - Destaques
  - Notícias
---
</pre>

### Shortcodes
O Hugo possibilita a criação de shortcodes para facilitar a edição de posts. Se você alguns serviços para embedar código ou vídeos, basta usar os shortcodes abaixo:

#### Codepen
Para adicionar um embed do seu experimento com Codepen, use o código de shortcode abaixo (criado pelo [Angelo Lucas](https://github.com/tableless/tableless-static/pull/6)):

<pre class="lang-html">
{{&lt; codepen
  hash="[Obrigatório]" 
  user="[Obrigatório]"
  author="[Opcional]"
  title="[Opcional]"
  theme="[Opcional]"
  tab="[Opcional]"
  height="[Opcional]"
&gt;}}
</pre>

#### YouTube
Para adicionar o YouTube, use o código abaixo. Troque o `id` do exemplo pelo `id` do seu vídeo:

<pre class="html">
{{&lt; youtube id="w7Ft2ymGmfc" autoplay="true" &gt;}}
</pre>

#### Speaker Deck
Para o Speaker Deck:

<pre>
{{&lt; speakerdeck 4e8126e72d853c0060001f97 &gt;}}
</pre>


### Categorias
Ali em *categorias*, coloque as categorias já existentes no site, ou se não souber, deixe em branco que os nossos editores comentarão no momento do Pull Request. Mas algumas categorias que você pode aplicar são: 

* Browsers
* Design
* Back-end
* Front-end
* Mobile
* CSS
* HTML
* JavaScript
* AngularJS
* ReactJS
* Ajax
* NodeJS
* jQuery
* Wordpress
* Mercado e Comportamento
* Tecnologia e Tendências
* Código
* Agile e Gestão
* PHP
* Acessibilidade
* Semântica
* Microdata
* RDFa
* SEO
* Git
* Opinião

Você pode ver um arquivo de [artigo de exemplo aqui](https://raw.githubusercontent.com/tableless/tableless-static/master/content/carreira-de-front-end-vai-morrer.md).

