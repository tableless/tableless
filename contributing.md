# Como contribuir no Tableless?
O Tableless é um projeto Open Source, feito para a comunidade de profissionais de internet criarem conteúdo e compartilharem conhecimento. Você contribuir conosco sendo um Autor ou com código. Fique à vontade para nos dar sugestões e críticas também.

## Contribuindo com um artigo
Nós usamos o HUGO como sistema de publicação. Ele é um gerador de arquivos estático assim como o Middleman ou o Jekyll. Logo, seu arquivo deve ser escrito em [Markdown](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet). Um ponto essencial é seguir o padrão do que chamamos de Frontmatter. Ele é a primeira coisa que deve haver em seu Markdown e serve para que o HUGO entenda informações essenciais do seu artigo. Veja abaixo o padrão:

```
---
title: Título do seu artigo
author: Seu nome
type: post
date: yyyy-mm-dd
excerpt: Uma descrição legal sobre o seu artigo. Não muito grande, nem muito pequeno.
image: https://i.imgur.com/o8vBHXX.png
categories:
  - javascript
  - jquery
---
```

- Na chave **author**, coloque o nome que você quer que apareça para os usuários. Esse nome deve ser igual em todos os seus artigos publicados.
- Na chave **image**, coloque o endereço de uma imagem de destaque. Essa imagem aparecerá na Home quando seu artigo estiver em destaque. A dimensão dela deve ser 500x400 ou maior. 
- Na chave **categories**, você categoriza seu post de acordo com seu assunto. Abaixo segue uma lista de categorias que você poderá usar.
- Todo seu artigo deverá ser escrito em Markdown. Um [Cheatsheet da sintaxe do Markdown poderá ser encontrada aqui](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet).
- Veja um [exemplo de artigo aqui](https://raw.githubusercontent.com/tableless/tableless-static/master/content/posts/github-game-jam.md).
- O arquivo do seu artigo deverá estar dentro da pasta `/content/posts/`, com o nome na extensão `.md`.

### Fazendo um Pull Request
Para que seu post seja publicado, você deve fazer um Pull Request, inserindo o arquivo do seu post na pasta `/content/posts/`. Nossos editores irão avaliar seu Pull Request. Assim que seu commit for mergeado, ele será automaticamente publicado depois de alguns minutos.

### Categorias que podem ser usadas
Abaixo segue a lista de categorias que poderão ser usadas nos seus artigos. Você também poderá adicionar categorias novas caso seja necessário. Sugerimos que coloque sempre mais de uma categoria.

- CSS
- Less
- SASS
- Acessibilidade
- Web Semântica
- GIT
- WordPress
- Agile e Gestão
- Traduções
- Série Bonito de se ver
- Apresentações e Slides
- Browsers
- Convertidos
- Semântica
- SEO
- Na prática
- Joomla
- Drops
- Editores de código
- Eventos e Workshops
- Freebies
- Laravel
- Mercado e comportamento
- Opinião
- Notícias
- Microdata
- O Básico
- Podcasts
- Tecnologia e Tendências
- Ferramentas
- Traduções
- UX
- Design
- Vídeos tutoriais
- PHP
