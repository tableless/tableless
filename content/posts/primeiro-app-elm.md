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
    { busca : String
    , urlGif : String
    }


init : String -> ( Modelo, Cmd Msg )
init busca =
    ( Modelo busca ""
    , getNovoGif busca
    )
```

Além do modelo, também criamos uma função chamada **init** que será responsável por iniciar o estado do nosso modelo. Não se preocupe pois no final quando juntarmos todas as partes ficará mais clara a responsabilidade da função init.

Após criado o modelo, é hora de criar o **update** e as **mensagens**.

```elm
...

type Msg
    = BuscarGif
    | NovoGif (Result Http.Error String)


update : Msg -> Modelo -> ( Modelo, Cmd Msg )
update msg modelo =
    case msg of
        BuscarGif ->
            ( Modelo modelo.busca "", getNovoGif modelo.busca )

        NovoGif (Ok urlGif) ->
            ( Modelo modelo.busca urlGif, Cmd.none )

        NovoGif (Err _) ->
            ( modelo, Cmd.none )
```

Entenda as mensagens como as possíveis ações que podem acontecer no seu sistema, ou seja, o clique de um botão, a resposta de uma requisição HTTP, o preenchimento de um formulário, etc. 

Já o update é responsável por receber uma mensagem e alterar o nosso modelo, ou seja, podemos considerar o update como a **principal função do projeto**, pois é ela que será responsável por receber uma mensagem e saber como o seu modelo precisa "responder".

Agora vamos criar a nossa **view**, que basicamente será responsável por receber o nosso modelo e mostrar as informações na tela.

```elm
...

view : Modelo -> Html Msg
view modelo =
    div []
        [ h1 [] [ text modelo.busca ]
        , button [ onClick BuscarGif ] [ text "Buscar Gif" ]
        , br [] []
        , img [ src modelo.urlGif ] []
        ]
```

A primeira vista essa sintaxe pode parecer bem estranha, especialmente para quem está acostumado a escrever HTML "comum", porém lembrem-se de que o Elm é outra linguagem e que no final compila para JavaScript e por isso sua sintaxe é diferente.

No Elm todos os elementos HTML são seguidos de dois colchetes, no primeiro passamos os atributos do elemento e no segundo o conteúdo.

No nosso exemplo temos um *button*, repare que no primeiro colchete passamos um atributo *onClick* passando o nome da mensagem que criamos anteriormente, e no segundo colchete passamos o texto que queremos que apareca no botão.

Agora que já temos quase tudo pronto, vamos criar de fato a função que será responsável por buscar um novo GIF.

```elm
...

getNovoGif : String -> Cmd Msg
getNovoGif topic =
    let
        url =
            "https://api.giphy.com/v1/gifs/random?api_key=dc6zaTOxFJmzC&tag=" ++ topic
    in
        Http.send NovoGif (Http.get url decodeGifUrl)


decodeGifUrl : Decode.Decoder String
decodeGifUrl =
    Decode.at [ "data", "image_url" ] Decode.string
```

Essa função é bem simples, ela basicamente busca um Gif e reparem que quando a requisição for finalizada a mensagem **NovoGif** que criamos é "acionada".

Agora todo que já temos todas as partes do nosso projeto, vamos apenas juntar tudo isso na nossa função **main**.

```elm
...

main =
    Html.program
        { init = init "dogs"
        , view = view
        , update = update
        , subscriptions = always Sub.none
        }
```

# Executando o projeto

Para testarmos o nosso projeto, precisamos rodar o comando **elm-reactor** para que o servidor seja iniciado, e após isso acessar a url http://localhost:8000/Main.elm.

Apenas uma observação é que nesse primeiro acesso a página pode demorar um pouco para carregar, pois é nesse momento que o Elm está baixando todos os pacotes que estamos utilizando no projeto.

![imagem do projeto](https://i.imgur.com/guOzS2W.png)

# Conclusão

Nesse artigo vimos como criar uma aplicação em Elm que seja mais próximo de uma aplicação "real", ou seja, temos requisição HTTP e uma view dinâmica que é alterada de acordo com as alterações que nosso modelo sofrem.

Até agora escrevemos apenas código Elm, no próximo artigo vou pegar esse exemplo e mostrar como fazer o *build* da nossa aplicação Elm para de fato termos um JavaScript e podermos utilizar nas nossas aplicações e servidores web.
