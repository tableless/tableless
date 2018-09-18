---
title: Datas no JavaScript com Moment.js
authors: Breno Panzolini
type: post
date: 2018-02-28
excerpt: Como utilizar o pacote Moment.js para trabalhar de maneira mais eficiente com datas no JavaScript.
categories:
  - Javascript
  - NodeJS
tags:
  - Javascript
  - NodeJS
image:  https://imasters.com.br/wp-content/uploads/2014/02/moment-js.jpg
---

Trabalhar com datas no JavaScript utilizando a biblioteca padrão pode ser muito complicado e "chato" em diversos cenários e situações do dia a dia. Nesse post vou mostrar como utilizar algumas das principais funções do [**Moment.js**](https://momentjs.com/) para facilitar nosso desenvolvimento e a manipulação de datas.

## Sobre o Moment.js

O Moment.js é um pacote open source que pode ser utilizado para validar, manipular e fazer o parse de datas no JavaScript de uma maneira muito poderosa (para os que já utilizam JavaScript há algum tempo, sabem muito bem que em certos cenários utilizar a biblioteca padrão pode ser bem chatinho).

O repositório oficial do Moment.js pode ser encontrado no [GitHub](https://github.com/moment/moment) e a documentação oficial no [site](https://momentjs.com/docs/).

## Instalando o pacote

O Moment.js foi desenvolvido para funcionar tanto no browser como no Node.js e por isso ele pode ser instalado através de diversos gerenciadores de pacotes, como por exemplo: npm, bower, nuget, etc.

Para instalar o moment utilizando o npm, basta utilizar o comando:

```sh
$ npm install moment
```

*Obs: as demais formas de instalação podem ser lidas na [documentação.](https://momentjs.com/docs/#/use-it/)*

## Parse

Existem diversas funções no Moment.js responsáveis por fazer o parse de datas, vou mostrar algumas que são mais utilizadas:

#### Data Atual

Para obter a data e hora atual basta chamar a função `moment()`.

```
const now = moment()
```

#### Convertendo uma String

Quando estamos criando um objeto moment a partir de uma string, a biblioteca primeiro checa se a string está no formato [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) para realizar a conversão:

```
const dia = moment("2018-25-02")
```

Caso a biblioteca não consiga converter a string informada em data o método `isValid()` irá retornar false:

```
moment("abcxyz").isValid() // false
```

#### Convertendo um Unix Timestamp

Para criar um objeto moment a partir de um *unix timestamp* utilizamos a função `unix()`:

```
const day = moment().unix(1318781889)
```

## Manipular

Depois de já ter criado um objeto moment, podemos utilizar diversas funções para manipular o seu valor.

#### Adicionando e Subtraindo

Podemos usar a função `add(Number, String)` para adicionar valores da mesma forma que a `subtract(Number, String)` para subtrair valores:

```
moment("2018-02-24").add(2, "days") // 2018-02-26
moment("2018-02-24").add(1, "year").subtract("1", "days") // 2019-02-23
```

*Obs: todos os tipos disponíveis podem ser encontrados na [documentação.](https://momentjs.com/docs/#/manipulating/add/)*

#### Início e Fim

Podemos usar as função `startOf(String)` e `endOf(String)` para transformar o objeto moment para o início do período informado:

```
moment().startOf("year") // 2018-01-01 00:00:00.000
moment().endOf("year") // 2018-12-31 23:59:59.999
```

## Formatação

A biblioteca do Moment.js nos oferece várias funções para realizar a formatação de data, vou mostrar como exemplo a utilização da função `format(String)`.

```
moment().format("dd/MM/yyyy HH-mm") // 25/02/2018 13-35
moment("abcxyz").format('YYYY MM DD') // "Invalid date"
```

## Comparações

As funções que mais gosto em toda a bibliotaca do Moment.js são as responsáveis pelas comparações entre datas, pois elas facilitam muito esse tipo de trabalho no JavaScript. Entre as mais comuns podemos citar:

#### Antes e Depois

Podemos usar as função `isBefore()` e `isAfter()` para comparar as datas:

```
moment('2017-10-20').isBefore('2017-10-21'); // true
moment('2017-10-20').isBefore('2010-12-31', 'year'); // false
moment('2017-10-20').isBefore('2018-01-01', 'year'); // true
```

#### Entre

Podemos usar a função `isBetween()` para comparar se uma data está entre outras duas datas:

```
moment('2010-10-20').isBetween('2010-10-19', '2010-10-25'); // true
```

## Conclusão

Esse post foi para introduzir e mostrar algumas funções básicas do pacote **Moment.js**, tenho certeza de que se você estiver trabalhando com datas no JavaScript ele é um excelente pacote para introduzir diversas funções para facilitar o seu desenvolvimento.

O Moment ganhou tanto sucesso para a manipulação de datas no JavaScript que o seu criador estava até trabalhando com a equipe *core* de desenvolvimento do Node.js para introduzir algumas das funcionalidades dentro do pacote padrão de datas do Node.

Aconselho para os que querem conhecer as demais funções e facilidades do pacote que consulte a [documentação oficial](https://momentjs.com/docs/).
