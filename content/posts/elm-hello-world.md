---
title: Seu primeiro Hello World em Elm
authors: Breno Panzolini
type: post
date: 2017-09-07
excerpt: Guia de como instalar o Elm e fazer seu primeiro Hello World.
categories:
  - Javascript
tags:
  - elm
image:  https://cdn-images-1.medium.com/max/720/1*I-3kbXzEIAPAPEGiMcAs0A.png
---

O Elm está ganhando espaço no mundo da programação pelas diversas vantagens e benefícios que ele oferece (você pode conferir uma introdução [nesse outro artigo][1]).

Hoje vamos abordar como instalar o Elm e fazer o seu primeiro Hello World, garanto que se você der uma chance para essa linguagem muito dificilmente vai querer largá-la.

## Instalando o Elm

A forma mais fácil e prática de instalar o Elm é através do **npm**. Porém, se você preferir utilizar um instalador no Windows ou Mac é só acessar a [página oficial][2] e fazer o download.

```
npm install -g elm
```

Atenção: se você estiver utilizando Linux talvez pode ser que ocorra um erro de permissão na hora da instalação (mesmo rodando com privilégios de sudo). Se esse for o seu caso sugiro instalar o Elm através do **yarn** (é mais prático do que alterar as configurações globais do npm).

```
yarn global add elm
```

Após a instalação você terá disponíveis os seguintes comandos:

* elm-repl: é o runtime event loop, permite escrever algumas expressões direto no console.

![elm-repl](https://i.imgur.com/RQT7Jlc.png)

* elm-reactor: inicializa o servidor da sua aplicação (por default na porta 8000).
* elm-make: responsável pelo build do projeto, esse comando é que irá compilar o seu código Elm em JavaScript para ser incluído no browser. Em projetos maiores é comum utilizarmos esse comando junto de ferramentas mais poderosas de build (como Gulp ou Grunt).
* elm-package: faz o download ou publicação dos pacotes do próprio repositório do Elm (você pode conferir a lista completa de pacotes no [catálogo oficial][3]).

## Meu primeiro Hello World!

Agora que você já tem o que é necessário vamos colocar a mão na massa e escrever nosso primeiro código em Elm.

Vamos criar uma pasta para o projeto e um arquivo chamado *Main.elm*

```sh
mkdir elm-helloworld
cd elm-helloworld
touch Main.elm
```

Com o arquivo criado, basta abrir no seu editor favorito (para o exemplo eu estou utilizando o VS Code com a extensão do elm para os *highlights* e o elm-format para identação automática) e escrever o seguinte código:

```elm
module Main exposing(..)

import Html

main = 
  Html.text "Hello World"
```

Sei que provavelmente você ainda não deve estar entendendo nada, mas calma que logo abaixo vamos detalhar linha a linha desse nosso primeiro Hello World.

Para executar o que acabamos de fazer, basta ir no console e chamar o **elm-reactor** para iniciar a aplicação e acessar no browser através do endereço https://localhost:8000/Main.elm.

![elm-reactor](https://i.imgur.com/jSCnIkz.png)

Observação: na primeira vez que acessar a página pode ser que demore alguns instantes, pois nesse primeiro acesso o Elm está baixando todos os pacotes necessários para rodar seu projeto.

## Detalhando o código linha por linha

Vou explicar agora passo a passo o que exatamente cada linha do código acima faz:

1. import Html

O Elm tem vários módulos que não são carregados por padrão. Um deles é o Html, que serve para dar o "output" em Html e por isso começamos primeiramente carregando esse módulo.

2. module Main exposing(..)

Todo arquivo Elm por padrão é um módulo, cujo nome tem que ser igual ao nome do arquivo criado (no caso do exemplo Main). Quando escrevemos um módulo podemos expor determinadas funções para serem utilizadas em outros módulos. O **exposing(..)** significa que estamos expondo todas as funções desse módulo.

3. main = 
     Html.text "Hello World"

Nessa linha foi definida uma função chamada "main" que vai receber o retorno do Html.text passando o parâmetro "Hello World".

Sempre que vamos renderizar um módulo no Elm, por padrão ele irá procurar pela função chamada "main". Repare que se você trocar a linha "main =" por "teste =" e atualizar a página irá ficar em branco pois o "main" não foi definido.

## Melhorando o nosso Hello World

Vamos trocar algumas coisas no nosso código para deixar ele um pouco mais legal e começarmos a explorar mais funcionalidades do Elm.

```elm
import Html

view name =
  "Olá, " ++ name ++ "!"

main = 
  Html.text (view "Breno")
```

Primeiramente criamos uma função chamada *view* que recebe um argumento chamado *name* e então retornamos um texto concatenando esse argumento.

Perceba também que agora na nossa função principal, ao invés de passar um texto fixo, estamos chamando a nossa função *view* passando o argumento.

Como já havíamos executado o elm-reactor, após feita essa alteração não existe a necessidade de executá-lo novamente. Basta salvar o arquivo e atualizar o navegador para ver as modificações.

## Conclusão

Esse artigo foi para mostrar como se fazer a instalação do Elm, e mostrar um pouco dos passos iniciais da linguagem.

No site oficial existe uma [coleção de exemplos][5] para quem quiser se aprofundar mais nos conceitos da linguagem.

No próximo artigo vamos ver como trabalhar com **Decoders**, que é a forma como fazemos para "decodificar" um request JSON. E, a partir daí construir realmente aplicações "reais".

[1]: https://tableless.com.br/introducao-ao-elm/
[2]: https://guide.elm-lang.org/install.html
[3]: https://package.elm-lang.org/
[5]: https://elm-lang.org/examples
