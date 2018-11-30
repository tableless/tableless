---
title: Datas no PHP com Carbon
authors: Breno Panzolini
type: post
date: 2018-11-30
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

A forma mais simples de instlar o Carbon no nosso projeto é através do **Composer**:

```sh
$ composer require nesbot/carbon
```

Com ele instalado, vamos criar um arquivo `teste.php` com o seguinte código:

```php
<?php

require 'vendor/autoload.php';

use Carbon\Carbon;
```

# Funcionalidades

Agora, vamos ver algumas das funcionalidades que a biblioteca disponibiliza para trabalharmos com datas.

Para não ficar repetitivo, vou considerar em todos os exemplos que o passo anterior já foi executado, ou seja, já foi feito o `require` do autoload e o `use` da classe. Além disso em todas as execuções dos testes vou executar o comando `php teste.php` para mostrar a saída.
