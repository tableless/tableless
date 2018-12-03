---
title: Datas no PHP com Carbon
authors: Breno Panzolini
type: post
date: 2018-12-02
excerpt: Como utilizar o pacote Carbon para trabalhar de maneira mais eficiente com datas no PHP.
categories:
  - PHP
tags:
  - Datas
  - PHP
image:  https://vegibit.com/wp-content/uploads/2015/11/Easy-PHP-Dates-and-Times-With-Carbon.jpg
---

Algum tempo atrás escrevi um artigo sobre [como trabalhar com datas no JavaScript](https://tableless.com.br/trabalhando-com-moment/). Nesse artigo trago algo semelhante, porém agora para o mundo PHP utilizando a biblioteca **Carbon**.

# Sobre o Carbon

O **Carbon** é uma biblioteca que herda a classe **DateTime** do PHP e que facilita a manipulação e operação com datas no PHP.

O repositório oficial do Carbon pode ser encontrado no [GitHub](https://github.com/briannesbitt/Carbon) e a documentação oficial no [site](https://carbon.nesbot.com/docs/).

# Instalando a biblioteca

Antes de começar, é bom se atentar na compatibilidade da versão do Carbon com a versão do PHP, segundo a documentação oficial:

- 1.x é compatível com PHP 5.3+
- 2.x é compatível com PHP 7.1.8+

A forma mais simples de instalar o Carbon no nosso projeto é através do **Composer**:

```sh
$ composer require nesbot/carbon
```

Com ele instalado, vamos criar um arquivo `teste.php` com o seguinte código:

```php
<?php

require_once 'vendor/autoload.php';

use Carbon\Carbon;
```

# Funcionalidades

Agora, vamos ver algumas das funcionalidades que a biblioteca disponibiliza para trabalharmos com datas.

Para não ficar repetitivo, vou considerar em todos os exemplos que o passo anterior já foi executado, ou seja, já foi feito o `require` do autoload e o `use` da classe. Além disso em todas as execuções dos testes vou executar o comando `php teste.php` para mostrar a saída.

## Data atual

```php
$agora = Carbon::now();
print_r($agora);

$instancia = new Carbon();
print_r($instancia);
```

![now](https://i.imgur.com/Zt4iG2z.png)

Os dois exemplos tiveram o mesmo efeito, exceto obviamente pelos milisegundos.

## Timezone

Com o Carbon também é muito tranquilo de se trabalhar com timezone, basta passar a opção no momento de criação da classe.

```php
$saoPaulo = Carbon::now(new DateTimeZone('America/Sao_Paulo'));
$recife = Carbon::now(new DateTimeZone('America/Recife'));
$londres = Carbon::now(new DateTimeZone('Europe/London'));

print('São Paulo - ' . $saoPaulo . PHP_EOL);
print('Recife - ' . $recife . PHP_EOL);
print('Londres - ' . $londres . PHP_EOL);
```

![timezone](https://i.imgur.com/pYTpeci.png)

## Adição e Subtração

Temos diversas funções para adicionar e subtrair valores em uma data. Vou mostrar apenas algumas, porém todas seguem a mesma lógica.

```php
$d = Carbon::create(2018, 01, 01, 0);

print($d->addCenturies(2) . PHP_EOL);
print($d->subCenturies(2) . PHP_EOL);

print($d->addHour() . PHP_EOL);
print($d->subHour() . PHP_EOL);

print($d->addMinutes(10) . PHP_EOL);
print($d->subMinutes(10) . PHP_EOL);

// Métodos genéricos para manipulação
print($d->add(10, 'minutes') . PHP_EOL);
print($d->sub('1 day') . PHP_EOL);
```

![add e sub](https://i.imgur.com/LwTwUqz.png)

## Formatação

Todas as opções de formatação se baseiam no método `format()` da própria classe `DateTime`, porém temos algumas funções que já facilitam alguns formatos mais comuns.

```php
$d = Carbon::now();

print($d->toDateString() . PHP_EOL);
print($d->toTimeString() . PHP_EOL);
print($d->toDateTimeString() . PHP_EOL);
```

![formatação](https://i.imgur.com/m4xBi7C.png)

# Conclusão

Esse post foi para introduzir e mostrar algumas funções básicas da biblioteca **Carbon**, tenho certeza de que se você estiver trabalhando com datas no PHP é uma excelente escolha para facilitar o seu desenvolvimento.

Aconselho para os que querem conhecer as demais funções e facilidades da biblioteca que consultem a [documentação oficial](https://carbon.nesbot.com/docs/).
