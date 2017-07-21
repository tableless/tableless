---
title: Começando desenvolver com o PostCSS
author: Júlio Carneiro
type: post
date: 2017-07-21
excerpt: Reinvente o modo como você escreve seu CSS.
image: http://i.imgur.com/GXiOjKP.jpg
categories:
  - CSS
  - postcss
tags:
  - postcss
  - Técnicas e Práticas
---

Desta vez vou trazer o PostCSS pra vocês, achei bem interessante e resolvi trazer um passo a passo de como iniciar e utilizar alguns plugins prontos pra facilitar a nossa vida ;D

O PostCSS é uma ferramenta relativamente nova (como tudo hoje em dia no front-end), ele visa reinventar o modo que escrevemos o css. Munido de plugins e ferramentas personalizadas ele trabalha da mesma forma que o SASS e outros pré-processadores, ele transforma sintaxes e recursos estendidos em CSS moderno e adéqua para o navegador.

_Certo Júlio, mas como ele faz isso? Simples, com JavaScript meu caro!_

O JavaScript transforma os nossos estilos muito mais rapidamente do que outros processadores. Usando task-runners como Gulp ou Grunt, podemos transformar estilos através do processo de construção, muito parecido com o processo de compilação do SASS e do LESS. Devido ao uso de uma API, o PostCSS nos permite criar plugins e ferramentas personalizadas para qualquer coisa que necessitamos.

O PostCSS move todo o código necessário para criar funções, utilidades e mixins fora de nossas folhas de estilo e os envolve como plugins. Agora, para cada projeto, podemos escolher as ferramentas necessárias, incluindo plugins em nosso task-runner, no caso o Gulp.

Nota: Uma versão completa (Gulp e Grunt) da ferramenta está disponível no GitHub . Sinta-se livre para usá-lo como um modelo inicial e modifica-lo conforme necessário.

## Configurando o PostCSS junto ao Gulp

Primeiro vamos instalar o Gulp e o gulp-postcss em nosso projeto, na pasta do projeto vamos abrir o terminal e executar o comando:

```bash
npm install gulp gulp-postcss
```

Feito isso vamos abrir o gulpfile.js e lá vamos escrever a tarefa que queremos que o Gulp execute pra gente:

```ruby
var gulp = require('gulp');
var postcss = require('gulp-postcss');
gulp.task('postcss', function () {
    return gulp.src('./style.css')
        .pipe(postcss([]))
        .pipe(gulp.dest('./prod'));
});
```

Para executar a tarefa basta digitar “gulp postcss” no seu terminal. Não vou abordar a configuração do PostCSS no Grunt pois acredito que isso seja muito do gosto da pessoa em utilizar tal task-runner, eu prefiro o Gulp então ensinarei nele. Caso use o Grunt de uma olhada pela internet que você encontra fácil como fazer essa configuração ok?

## Instalando Plugins

Agora vamos para a parte mais legal, o poder do PostCSS não está nele em si e sim nos plugins, então vamos instalar e ver como essa bagaça realmente funciona e para que ela vai ser útil no nosso trabalho.

A lista de plugins para o PostCSS pode ser encontrada na página no GitHub do PostCSS e, como todos os pacotes da NPM, os plugins podem ser instalados através da linha de comando, hoje vou mostrar para vocês o plugin “postcss-brazilian-portuguese-stylesheets” para termos uma noção de como funciona a ferramenta, este plugin traduz algumas coisas digitadas em nosso css em portugues para o correto que seria o inglês, ex:

```css
body {
    largura: 100px;
    altura: 100px;
}
```

Quando rodarmos o Gulp com o PostCSS vamos estar compilando o nosso trecho de código para:

```css
body {
    width: 100px;
    height: 100px;
}
```

Vamos instalar o plugin primeiro em nosso projeto e chamar ele no task-runner:

```ruby
npm install postcss-brazilian-portuguese-stylesheets
```

Depois de instalado vamos adicionar o plugin no nosso gulpfile.js igual como se estivéssemos adicionando uma dependência:

```ruby
var gulp = require('gulp');
var postcss = require('gulp-postcss');
var brazilianStyleSheets = require('postcss-brazilian-portuguese-stylesheets');
gulp.task('postcss', function () {
    return gulp.src('./style.css')
        .pipe(postcss([brazilianStyleSheets]))
        .pipe(gulp.dest('./prod'));
});
```

Pronto, muito fácil, com tudo configurado podemos rodar o comando “gulp postcss” em nosso terminal e ver o resultado na pasta “/prod”, lá estará nosso arquivo style.css compilado com o código css correto. Também podemos passar parametros para o plugin e fazer com que ele se comporte do jeito que quisermos, mas isso vou mostrar em outro post. Vou dar outro exemplo de como vamos escrever o css e como ele vai ficar depois de compilar:

```css
div {
    margem: 0 automatico;
    largura:200px;
    altura:200px;
    imagemFundo: url(img/imagem.jpg) naoRepetir;
}
```

Depois de compilado ele ficará assim:

```css
div {
    margin: 0 auto;
    width:200px;
    height:200px;
    background-image: url(img/imagem.jpg) no-repeat;
}
```

Este foi um exemplo que eu aprendi no BeMean, o curso é gratuito e você pode fazer pelo próprio youtube, já me ensinou bastante coisa e eu achei esse exemplo perfeito para poder mostrar algumas coisas que o PostCSS faz. As possibilidades são infinitas, mesmo, e caso vocês curtirem bastante esse post eu vou trazer mais de como instalar outros plugins mais legais e mais úteis, de qualquer jeito você pode dar uma explorada no http://postcss.parts que você vai encontrar MUITOS plugins e como instala-los.

Espero que tenham curtido o post, mostrem interesse curtindo e comentando e façam com que eu tenha mais vontade de escrever ;D Obrigado a todos pela leitura, um abraço.