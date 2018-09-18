---
title: Boas práticas para projetos JAMStack
authors: Diego Eis
type: post
date: 2018-04-11
excerpt: Saiba algumas boas práticas (várias já conhecidas) para projetos JAMStack
image: https://i.imgur.com/CSyNzIJ.jpg
categories:
  - front-end
tags:
  - jamstack
  - código estático
  - netlify
  - hugo
  - git
  - Tecnologias e tendências
---

A revolução dos sites usando uma arquitetura baseada em JavaScript, APIs e código pré gerado chama-se [JAMStack](https://tableless.com.br/revolucao-dos-sites-com-jamstack/). Essa forma de fazer websites tem como objetivo aliviar a arquitetura para manter websites ou sistemas. Pegue como exemplo o Tableless, onde nós tínhamos toda uma arquitetura sendo mantida com Wordpress e banco de dados de MySQL e [atualmente é todo estático](https://tableless.com.br/site-tableless-estatico/), usando Hugo, hospedado no Netlify e código guardado no Git. 

Para fazer isso, não é difícil, mas existem boas práticas que você pode seguir para facilitar sua vida, são elas:

## Seria interessante usar um CDN

Não é um ponto obrigatório (aliás, nenhum desses tópicos é), mas além do seu site já ficar muito leve por conta do carregamento de  HTML puro, dá para melhorar se usarmos um CDN. Como os projetos baseados na ideia de JAMStack não precisam de sites server-side, eles podem ser distribuídos de forma mais fácil.

O mais conhecido é o [CloudFlare](https://www.cloudflare.com/br/), mas tem um monte de outros, que podem ou não deixar você colocar seus assets lá, mas normalmente já disponibilizam os frameworks e bibliotecas mais populares para você usar em seus projetos. Alguns:

- [Google Hosted Libraries](https://developers.google.com/speed/libraries/#libraries)
- [Yandex CDN](https://tech.yandex.ru/jslibs/)
- [jsDelivr](https://www.jsdelivr.com/)
- [cdnjs](https://cdnjs.com/)

## Seu código fica no GIT

Essa é uma boa prática para vida. Hoje é muito difícil times não usarem o [Git](https://tableless.com.br/iniciando-no-git-parte-1/) como o versionador de código padrão. Mas com um projeto JAMStack, qualquer deve conseguir baixar o projeto e rodar em minutos na própria máquina. Nada de clonar banco de dados, ou instalar banco na máquina. Isso reduz a quase zero a fricção de contribuir para projetos baseados na ideia de JAMStack, além de simplificar o workflow de teste e staging.

## Ferramentas de Build

Dependendo do projeto, é interessante o uso de uma ferramenta de build. A ideia é que tudo seja automatizado. O resultado precisa ser arquivos de HTML, CSS e JS estáticos, mas eles devem ser buildados de forma que as boas práticas sejam mantidas. Usar pré/pós-processadores de CSS, WebPacks da vida, Gulp, Grunt, Babel e essas coisas é uma boa pedida. Basicamente é o que você já deve fazer hoje em projetos que usam algum framework JS, só que com uma stack muito mais simples.

Aqui no Tableless, basicamente, uso só SASS para entregar o CSS e nada mais. Tem um mínimo de JS, as imagens estão no imgur. A geração do dos arquivos estáticos que guardam as páginas e os conteúdos do site é feito pelo pelo Hugo. Então eu dispensei qualquer outra complexidade.

## Builds Automatizados

Por que o JAMStack é feito com código pré-buildado, ou seja, ele precisa ser buildado antes de ser publicado, a mudança de conteúdo  ou interface não vai pro ar enquanto você não rodar um build. Quando você sobe um código novo para o seu repositório, seu ambiente tem que entender isso, fazer o build e publicar automaticamente seu projeto. Eu sei que existem uma série de sistema para fazer isso, mas todas elas são mais complexas exatamente pelo motivo de que a maioria dos projetos tem dependências de linguagens back-end. Em um website simples com JAMStack, você pode usar webhooks ou uma plataforma de publicação que tem esse serviço de automatização, tipo a Netlify que nós usamos aqui. Fiz um artigo que fala sobre esse [processo entre GIT e Netlify aqui](https://tableless.com.br/deploy-automatico-com-git-netlify/).

## Atomic Deploys

Atomic Deploys são deploys onde todo o sistema só vai pro ar quando finalizar o upload de todos os arquivos modificados. Em projetos JAMStacks, que geralmente são sites de conteúdo ou sites que tem muitas páginas, é comum fazer várias mudanças, seja de conteúdo ou interface, necessitando fazer deploys de vários arquivos. Até subir cada um dos arquivos, pode haver um tempo de inconsistências até que o processo de upload termine. 

## Invalidação de Cache

Como estamos falando de arquivos estáticos, é comum termos problemas com cache. Nesse caso, nós temos que ter certeza que nosso ambiente, principalmente se estivermos usando CDN, está invalidando direito o cache. Você precisa ter certeza de que os browsers farão o download dos arquivos novos. Quem nunca teve problemas com cache de CSS que nunca atualizar, né?

O Netlify, que é o host mais popzinho para arquiteturas JAMStacks nas o [Instant Cache Invalidation](https://www.netlify.com/blog/2015/09/11/instant-cache-invalidation/) sem esforço.

## Concluindo

Muito do que eu falei aqui são coisas que fazemos no dia a dia. Mas geralmente fazemos isso só para uma parte do projeto, seja ela no front-end ou na parte de DevOps. Mesmo assim, há times que mal tem seu workflow de publicação para produção automatizado. Já vi lugares onde o time de front-end precisa buildar seus assets, porque o workflow de publicação fazia apenas um git pull no servidor. Quando falamos sobre websites com o pensamento de ter uma arquitetura leve como a ideia do JAMStack propõe, é levar toda essa facilidade para um novo nível.

Obviamente um projeto JAMStack nem se compara com projetos enorme, sistemas complexos e etc. Estamos falando aqui de basicamente websites de todos os tamanhos. Mas pensa na polêmica levando ao extremo: todo o projeto onde o front-end tem APIs como dependência, pode ser tratado como um projeto JAMStack. Obviamente guardada as devidas proporções dos projetos e seus respectivos stacks e necessidades.