---
title: Primeiros passos com HUGO
authors: Rafael Acioly
type: post
image: https://cdn-images-1.medium.com/max/800/1*24rMpWwzXmNtbdwLzkDhWQ.png
date: 2018-02-16
excerpt: Saiba como instalar o HUGO e utilizar temas prontos feitos pela comunidade.
categories:
  - Front-end
  - Código
  - Tecnologia e Tendências
  - hugo
  - jamstack
tags:
  - hugo
  - jamstack
---

[**HUGO**](https://gohugo.io/) é um gerador de sites estáticos escrito com Golang que vem ganhando muita visibilidade devido a sua rapidez para gerar/compilar conteúdos. Ao lado de Jekyll (escrito em Ruby) ambos os geradores disponibilizam uma gama enorme de recursos para que você possa criar um site ou um blog em minutos.

## Porque HUGO?

* Migração de Wordpress em um piscar de olhos;
* Geração de páginas e posts extremamente rápidos;
* Boa gestão de permalinks;
* Suporta vários tipos de frontmatters: json, toml e yaml;
* Templating usando Sections, Archetypes e Types;
* Oganização e gestão de Taxonomias;
* Suporta Syntax Hightlighting nativamente;
* E tem um monte de extras que talvez você nem precise usar.

Abaixo está um gráfico que compara Jekyll e HUGO na questão tempo para geração de 10 mil páginas.

![comparação em tempo de hugo vs jekyll](https://cdn-images-1.medium.com/max/800/1*NqslqUZ25sFZUSwNz-7X9A.png)

Enquanto HUGO leva cerca de 7.6 segundos para gerar 10 mil páginas, Jekyll demora incríveis 218.61 segundos (mais de 3 minutos)

Para mais informações do benchmark acima veja este artigo (em inglês): https://forestry.io/blog/hugo-vs-jekyll-benchmark/

Se você gosta de acompanhar blogs e artigos brasileiros, você talvez dê uma moral a mais para HUGO em saber que o tableless foi reformulado inteiramente para rodar com seu blog utilizando este gerador, veja neste artigo escrito por Diego Eis (dono do tableless) mostrando as comparações e vantagens desta mudança. https://tableless.com.br/site-tableless-estatico/

Após toda essa informação, acho que já podemos dar uma chance ao HUGO não é?

## Instalação
A primeira coisa que você precisa saber, é que **você não precisa instalar GO para usar o HUGO**. Neste artigo irei mostrar a instalação em distribuições linux baseadas em debian, mas você pode ficar a vontade para instalar em qualquer sistema operacional em segundos: https://gohugo.io/getting-started/quick-start/#step-1-install-hugo

## Faça o download da aplicação compilada:

Acesse as releases do gerador e baixe o arquivo com extensão .deb , após o download você estará apto a executar o arquivo em seu gerenciador de software em seguida clique em instalar.

Com a instalação concluída, você terá disponível em seu terminal o comando hugo que usaremos para gerenciar nosso projeto. Para verificar se a instalação ocorreu corretamente, utilize o seguinte comando:
```sh
$ hugo version

// A saída gerada na data em que este artigo foi criado é:
// Hugo Static Site Generator v0.36 linux/386 BuildDate: 2018-02-05T15:22:28Z
```

## Criando um novo projeto
Para iniciar um novo projeto, vá até sua pasta de preferência e digite em seu terminal:
```sh
$ hugo new site meu-site
```
O código acima criara uma pasta com o nome meu-site com toda a estrutura necessária para você utilizar começar a desenvolvedor seu projeto.

## Download de temas prontos
O site oficial do HUGO possui uma seção dedicada apenas à temas criados pela comunidade e para nossa felicidade, podemos utilizar qualquer um deles em nosso projeto gratuitamente. Neste exemplo utilizarei o [tema “Ananke”](https://github.com/budparr/gohugo-theme-ananke):

Realize o download com os seguintes passos:

```
$ cd meu-site/
$ git init
$ git submodule add “url-do-tema-ananke” themes/ananke
```

> URL do tema: https://github.com/budparr/gohugo-theme-ananke

Após a URL do tema, note que apontamos o download para a pasta themes/ que é onde todos os temas devem obrigatoriamente ficar.

Para finalizar nossa instalação, precisamos informar ao HUGO qual será o tema que utilizaremos, abra o arquivo config.toml na raiz do projeto e defina a chave “theme” com o nome da pasta colocada dentro de themes:

```toml
# arquivo config.toml

baseURL = "https://example.org/"
languageCode = "pt"
title = "My New Hugo Site"
description = "My site description"
theme = "ananke"
```

Agora temos uma instalação do HUGO e um tema para utilizar, para ver o resultado execute o comando abaixo dentro da pasta do projeto:

```sh
$ hugo server -D
```

Este comando executara seu projeto na porta 1313 do localhost; https://localhost:1313

Esqueci algo ou não fui claro em algum ponto? deixe um comentário que ficarei feliz em corrigir ou esclarecer algo! ;)
