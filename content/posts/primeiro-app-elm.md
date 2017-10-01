---
title: Desenvolvendo sua primeira aplicação com Elm
author: Breno Panzolini
type: post
date: 2017-09-30
excerpt: Como escrever aplicações dinâmicas no Elm fazendo requisições HTTP e interpretando JSON.
categories:
  - Elm
  - JavaScript
tags:
  - Elm
  - JavaScript
image:  https://cdn-images-1.medium.com/max/720/1*I-3kbXzEIAPAPEGiMcAs0A.png
---

Assim como em todos frameworks ou libs de SPA, no Elm o meio mais comum para interagirmos com os dados que estão no servidor e dessa forma criar aplicações "dinâmicas" é através de APIs. Fazemos uma requisição, aguardamos uma resposta do servidor e atualizamos a tela de acordo com os dados recebidos.

Antes de partimos para o código recomendo que você tenha lido os artigos anteriores em que fiz uma [introdução ao Elm](https://tableless.com.br/introducao-ao-elm) e mostrei como fazer a [instalação e o Hello World](https://tableless.com.br/elm-hello-world).

Nesse artigo vamos criar uma aplicação um pouco mais próxima da realidade, ou seja, vamos fazer uma requisição em uma API e alterar o conteúdo dinamicamente de acordo com os dados obtidos.

# Criando a estrutura do projeto

Vamos começar criando uma pasta e um arquivo chamado **Main.elm** dentro dela.

```sh
$ mkdir projeto
$ cd projeto
$ touch Main.elm
```

Após feito isso, abra seu editor de código favorito e vamos começar a desenvolver.

# O código

Vamos começar importando todos os pacotes e módulos que iremos utilizar, não se preocupe pois ao longo do artigo vamos entender qual o papel de cada um destes módulos.

```elm
module Main exposing (..)

import Html exposing (..)
import Html.Attributes exposing (..)
import Html.Events exposing (..)
import Http
import Json.Decode as Decode

```

Apenas uma observação é que o módulo **Http** não faz parte dos pacotes básicos do Elm, e por isso precisamos utilizar o comando **elm-package** para instalá-lo.

```sh
$ elm-package install elm-lang/http
```

O próximo passo é criarmos o nosso modelo, para esse exemplo vamos fazer uma aplicação que busque um GIF aleatório, portanto nosso modelo terá a seguinte estrutura:

```elm
...

type alias Modelo =
    { assunto : String
    , urlGif : String
    }
```





```elm

```


```elm

```







