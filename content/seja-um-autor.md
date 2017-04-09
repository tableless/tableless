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

O Tableless é um projeto aberto, logo, para submeter um artigo para nós, basta enviar um Pull Request com seu artigo. Nós iremos avaliar e provavelmente sugerir algumas modificações. Como é um projeto aberto, a comunidade pode olhar também e sugerir modificações no seu texto. Não se envergonhe.

## Cuidado com artigos repetidos

Se você já publicou algum artigo repetido no seu blog pessoal, tudo bem. Mas tente não publicar artigos que já foram publicados em outros sites de conteúdo. Geralmente o Google não gosta disso e muito provavelmente o seu leitor já deve ter lido esse artigo em outros sites.

## Tópicos principais

Você pode escrever qualquer assunto relacionado aos tópicos abaixo. Se você achar necessário, sugira um novo tópico para incluirmos na lista:

*   **HTML:** HTML5, linguagens de marcação, semântica, novidades;
*   **JavaScript:** JQuery, linguagem, métodos, truques, soluções, tutoriais;
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
*   **Agile:** metodologias ágies e relacionados;

## O que nunca vamos publicar

*   Press Releases. Nós não iremos publicar nenhum pré release ao menos nenhum de graça. Por isso ["vendemos" um espaço para quem quer anunciar no site.](http://tableless.com.br/anuncie-no-tableless/) ;-)
*   Venda de produtos. A não ser que você [queira anunciar aqui no Tableless](http://tableless.com.br/anuncie/), nós não vamos publicar nada desse tipo.

## Submeta agora seu artigo

Os artigos são baseados em Markdown. Logo, você precisa escrever seu artigo em Markdown antes de submeter para nós. Se você tiver um artigo em HTML, você pode convertê-lo [usando esse serviço](https://domchristie.github.io/to-markdown/). Além disso, é *OBRIGATÓRIO* o padrão de frontmatter no seu artigo, como segue abaixo:

<pre class="lang-yaml">
---
title: Nome do seu artigo
author: Seu nome
type: post
image: endereco-da-imagem-de-destaque/image.jpg
date: 2017-01-19
excerpt: Um resumo do seu artigo. Não precisa ser muito longo, mas o suficiente para que os usuários saibam em poucas palavras sobre o que é o seu artigo. É aqui que eles se interessarão pelo seu texto.
categories:
  - Browsers
  - Destaques
  - Notícias
---
</pre>

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

Para submeter seu artigo, siga os passos:

1. Você não precisa clonar o projeto para submeter um artigo, apenas [siga esse link](https://github.com/tableless/tableless-static/new/master/content) e escreva o artigo ou cole um artigo já escrito em Markdown. Esta é a página de criação de novo arquivo no GitHub que você já deve conhecer;
2. Coloque o nome do seu arquivo seguindo esse padrão: **nome-do-artigo.md**. Lembre-se que o artigo deve ser escrito em Markdown. Se seu artigo fizer uso de imagens, coloque em algum seriviço de host de imagens como o [imgh.us](imgh.us) ou [imgur.com](imgur.com) e coloque apenas o endereço da imagem no artigo;
3. Depois de ter terminado, logo abaixo da área de escrita, há um campo para escrever as informações de commit. Coloque um título no commit e uma descrição sobre o artigo;
4. Feito isso, selecione a opção **Create a new branch for this commit...** e submeta um Pull Request para a branch Master;
5. Aguarde os comentários e a aprovação do pessoal do Tableless; Sucesso! :-D

**ATENÇÃO:** Se seu artigo usar imagens, use serviços como o [imgur.com](imgur.com) para exibir suas imagens. Nós não versionamos as imagens do seu artigo.