---
title: PSR - Seguindo Padrões em PHP
authors: Morais Junior
type: post
image: https://dunglas.fr/wp-content/uploads/2015/05/PSR-7.png
date: 2018-04-21
excerpt: Poucos conhecem o PSR, ele é um padrão para escrita de códigos em PHP que deve ser seguido :)
categories:
  - PHP
---
# Padrão Básico de Codificação
O PSR nasceu com o objetivo de criar um padrão universal de desenvolvimento, criado pelo PHP Framework Interoperability Group é o principal padrão utilizado hoje em dia, portanto se você trabalha com algum framework ou utiliza alguma biblioteca de terceiro, já teve contato com esse padrão e nem sabia :)
Este documento engloba muitas regras e tem várias versões, pode ser complicado de se colocar em prática com perfeição, mas para isso existem ferramentas e validadores que irão ajudar nessa tarefa, dentres eles o PHP_CodeSniffer, entrarei em detalhes sobre ele no próximo artigo, por hoje iremos focar no padrão.

Descreverei aqui apenas um resumo, mas você pode se aprofundar no link abaixo:
[PHP Framework Interoperability Group](https://www.php-fig.org/ "PHP Framework Interoperability Group")

## Geral
- O código DEVE usar 4 espaços para indentação ao invés de tabs..
- Cada linha deve ter 80 caracteres ou menos. 
- As linhas em branco PODEM ser adicionadas para aumentar a legibilidade e para indicar blocos de código relacionados.

## Arquivos
- Todos os arquivos PHP DEVEM usar o fim da linha Unix LF (linefeed).
- Todos os arquivos PHP DEVEM terminar com uma única linha em branco.
- A tag de fechamento ?> DEVE ser omitida em arquivos que contêm apenas PHP.
- NÃO DEVE haver espaço em branco no final de linhas.
- Palavras-chave do PHP DEVEM ser em letra minúscula (lower case).
- As constantes do PHP true, false e null DEVEM ser em letra minúscula (lower case).

## Classes e Namespaces
- Os arquivos devem conter apenas código PHP.
- Os arquivos DEVEM usar apenas as tags `<?php` and `<?=` tags.
- Arquivos devem usar apenas UTF-8.
- O nome das classes deve ser declarado em: StudlyCaps.
- Os métodos em: camelCase
- Você precisa colocar uma linha em branco apos declarações de namespace e use.
- Aberturas e fechamento de classes e dos metodos nas classes devem estar em uma linha isolada.
- A visibilidade deve ser declara em todos os métodos das classes (Public, Protected ou Private).
- As constantes de classe DEVEM ser declaradas em maiúsculas com os separadores de sublinhado.
- A palavra-chave VAR não deve ser usada para declarar uma propriedade.

```php
<?php  
namespace Vendor\Package;

use FooInterface;
use BarClass as Bar;
use OtherVendor\OtherPackage\BazClass;

class Foo extends Bar implements FooInterface
{
    public $foo = null;
    
    public function sampleMethod($a, $b = null)
    {
        if ($a === $b) {
            bar();
        } elseif ($a > $b) {
            $foo->bar($arg1);
        } else {
            BazClass::bar($arg2, $arg3);
        }
    }

    final public static function bar()
    {
        // method body
    }
}
```

## Blocos de controle e funções
- Palavras-chave de controle (if, while, for, foreach, switch) devem ter um espaço entre a o fechamento do parêntese e abertura do bloco.
- Na lista de argumentos, NÃO DEVE haver um espaço antes de cada vírgula e DEVE haver um espaço após cada vírgula.
- Blocos de controle como if devem ter a abertura de bloco na mesma linha e fechamento em uma linha isolada


```php
<?php
function foo()
{
    // function body
}

if($argumento1,espaço $argumento2,espaço $argumento3  = [])espaço{
    4espaçoes codigo
}
```

Atualmente existe a [PSR-4](https://www.php-fig.org/psr/psr-4/ "PSR-4") porém é muito importante se manter atualizado e sempre consultar a documentação oficial no [PHP-FIG](https://www.php-fig.org/ "PHP-FIG") :)
