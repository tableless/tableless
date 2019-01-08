---
title: Compilando sua aplicação Elm
authors: Breno Panzolini
type: post
date: 2017-10-22
excerpt: Como fazer a compilação de uma aplicação escrita Elm para JavaScript e assim poder utilizar no browser.
categories:
  - Javascript
tags:
  - elm
image:  https://cdn-images-1.medium.com/max/720/1*I-3kbXzEIAPAPEGiMcAs0A.png
---

No [artigo anterior](https://tableless.com.br/primeiro-app-elm) vimos como desenvolver uma aplicação completa em Elm (com requisições HTTP e HTML dinâmico). 

Porém até agora temos apenas código escrito em Elm, e com isso precisamos compilar esse código para uma linguagem que os navegadores consigam interpretar, ou seja, **JavaScript**.

No post de hoje vamos ver como compilar nosso fonte para poder utilizá-lo de fato nas nossas aplicações.

# O elm-make

Após a instalação do Elm temos disponíveis alguns comandos, como já explicado [nesse outro artigo](https://tableless.com.br/elm-hello-world/). Um desses comandos é justamente o **elm-make**, que será o responsável por pegar todo o nosso código escrito em Elm e compilar para JavaScript.

Apenas uma observação inicial é que o foco desse post será apenas na parte de compilação de uma aplicação Elm, e por isso sugiro que você tenha desenvolvido a aplicação do [artigo anterior](https://tableless.com.br/primeiro-app-elm).

## Compilando o nosso arquivo Main.elm

Para compilar o nosso arquivo Main.elm vamos navegar até a pasta onde ele se encontra e criar uma nova pasta chamanda **dist**. É dentro dessa pasta que vamos compilar o nosso código.

```sh
$ mkdir dist
```

Com a pasta criada vamos executar o seguinte comando:

```
$ elm-make Main.elm --output dist/elm.js
```

No comando acima, estamos falando para o compilador pegar o arquivo Main.elm, fazer o build e jogar o arquivo gerado dentro da pasta dist. Se tudo ocorrer normalmente você verá a mensagem abaixo:

![Buld Elm](https://i.imgur.com/5skH9yr.png)

## Utilizando o nosso arquivo compilado

Agora que já temos o nosso arquivo JavaScript compilado vamos desenvolver uma página em HTML para poder utilizá-lo. Vou criar um arquivo chamando index.html dentro da pasta *dist* (que foi o local onde compilamos nossa aplicação Elm).

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <title>Aplicação Elm</title>
  </head>
  <body>
    <div id="app"></div>

    <script src="./elm.js"></script>
    <script>
      Elm.Main.embed(document.getElementById("app"))
    </script>
  </body>
</html>
```

Repare que o nosso código HTML é bem simples, ele é apenas um *wrapper* da nossa aplicação principal. Notem que o mecanismo é bem parecido com o que acontece em outros frameworks de SPA como Angular ou React.

O que estamos fazendo nesse HTML é importar nosso arquivo **elm.js** que foi compilado no passo anterior e falar que vamos querer carregar nossa aplicação dentro de uma div chamada app.

Se você seguiu o passo a passo certinho, a sua estrutura de pastas deve ser semelhante ao da imagem abaixo:

![Estrutura de pastas](https://i.imgur.com/XozyDRa.png)

## Testando nossa aplicação

Nesse momento nossa aplicação final já está pronta, e com isso basta abrir o arquivo *index.html* em qualquer navegador para ver o resultado final.

![Aplicação final](https://i.imgur.com/DPKNEWJ.png)

# Conclusão

Nesse artigo aprendemos como pegar a nossa aplicação desenvolvida na linguagem Elm e fazer sua compilação através do comando **elm-make** para JavaScript para dessa forma podermos utilizá-la nos nossos projetos.

É importante falar que o arquivo JavaScript gerado pelo elm-make não está minificado, por isso se você deseja colocar uma aplicação Elm em produção sugiro utilizar alguma outra ferramenta de build junto com o processo apresentado nesse post (como um Gulp, por exemplo) para realizar minificação e o *uglify* do arquivo final.
