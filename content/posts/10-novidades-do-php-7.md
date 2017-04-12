---
title: 10 novidades do PHP 7
author: Roberto Beraldo
type: post
date: 2015-09-29
excerpt: O PHP 7 deve ser lançado até o final desde ano de 2015. Há muitas novidades. Mostro aqui 10 delas, inclusive a melhoria no desempenho
url: /10-novidades-do-php-7/
categories:
  - PHP
tags:
  - Novidades
  - php
  - php7

---
O PHP 7 está prestes a ser lançada oficialmente, até o final deste ano de 2015.

A versão _Release Candidate_ (RC) do PHP 7 foi lançada no dia 21 de agosto. Sendo uma versão RC, não haverá implementações novas no PHP 7.0, apenas correções de bugs.

Vou apresentar aqui algumas novidades e recursos novos desta versão do PHP.

## 1. Desempenho Fantástico

O PHP 7 teve seu motor remodelado. Com isso, houve um grande ganho de desempenho.

Em alguns casos, é possível alcançar <a href="http://rberaldo.com.br/php-7-9-vezes-mais-rapido-que-php-5-6/" target="_blank">até 9 vezes mais velocidade</a>. Mas esse número pode variar conforme a plataforma e a aplicação utilizada nos testes.

Eu utilizei o script para benchmark criado pela própria equipe do PHP, disponibilizado junto com o código-fonte da linguagem. Em comparação com a versão 5.6, consegui aproximadamente 9 vezes mais velocidade usando o PHP 7. Expliquei esse teste com mais detalhes <a href="http://rberaldo.com.br/php-7-9-vezes-mais-rapido-que-php-5-6/" target="_blank">neste meu artigo</a>.

2. MySQL Removido

Desde o PHP 5.5, <a href="http://PS: funções mysql_* estão obsoletas desde o PHP 5.5  e já foram removidas no PHP 7. Prefira usar MySQLi ou PDO. Veja mais aqui: http://www.ultimatephp.com.br/php-por-que-nao-utilizar-funcoes-mysql" target="_blank">as funções mysql_* eram consideradas obsoletas</a>. Ou seja, tudo indicava que elas seriam removidas em um futuro bem próximo.

Pois bem. A hora chegou.

No PHP 7, as funções mysql\_* (como mysql\_connect(), mysql_query() e outras) deixaram de existir. Agora é preciso utilizar MySQLi ou PDO.

<a href="http://www.ultimatephp.com.br/como-usar-pdo-com-banco-de-dados-mysql/" target="_blank">Recomendo utilizar PDO</a>, por ser mais robusta e ser independente de SGBD.

3. Funções ereg_* Removidas

Além das funções mysql\_\*, as funções ereg\_\* e eregi\_* (como ereg(), ereg\_replace, eregi() e outras) eram consideradas obsoletas desde o PHP 5.3.

Elas também foram removidas no PHP 7.

Agora é preciso usar as funções preg_*, da <a href="http://php.net/manual/pt_BR/book.pcre.php" target="_blank">biblioteca PCRE</a>, como preg\_match e preg\_replace.

As funções preg_* exigem delimitadores. Consequentemente, é possível utilizar <a href="http://php.net/manual/pt_BR/reference.pcre.pattern.modifiers.php" target="_blank">modificadores</a>, como &#8220;i&#8221; e &#8220;u&#8221;. O &#8220;i&#8221;, por exemplo, significa case-insensitive. Ou seja, se você usava eregi\_\*, passará a usar preg\_\*, sempre com o modificador &#8220;i&#8221;.

## 3. Erros Fatais e Exceções

No PHP 7, erros fatais passaram a ser Exceções. Isso quer dizer que eles podem ser tratados em bloco try/catch, sem interromper a execução do script.

Para exemplificar, vamos executar este código (no PHP 7, não no PHP 5):

<pre class="lang-php">ereg('^[a-z]$', 'php7');
echo "FIM";
</pre>

Veremos este erro:

<pre>Fatal error: Uncaught Error: Call to undefined function ereg()...
</pre>

E o texto &#8220;FIM&#8221; não será exibido. Isso ocorre pois a exceção interrompe o script.

Agora execute este script:

<pre class="lang-php">try
{
    ereg('^[a-z]$', 'php7');
}
catch (Error $e)
{
    echo "Ocorreu um erro: " . $e-&gt;getMessage();
}

echo "FIM";
</pre>

Você verá a seguinte saída:

<pre>Ocorreu um erro: Call to undefined function ereg()
FIM
</pre>

Ou seja, nossa aplicação tratou a exceção e a execução continuou normalmente.

## 4. Construtores do PHP 4 Obsoletos

Antes do PHP 5, os construtores recebiam o mesmo nome da classe. Por exemplo:

<pre class="lang-php">class ClassePHP4
{
    function ClassePHP4()
    {
        echo "Construtor chamado";
    }
}
</pre>

Isso continuou funcionando no PHP 5, mas era recomendado usar o método `__construct`, ficando desta forma:

<pre class="lang-php">class ClassePHP5
{
    public function __construct()
    {
        echo "Construtor chamado";
    }
}
</pre>

O PHP 7 recomenda que seja usado método `__construct` em vez do método com o mesmo nome da classe. Ou seja, o uso de construtores no padrão do PHP 4 continuará sendo possível, mas é um recurso obsoleto (_Deprecated_).

Para testar isso, vamos executar este código:

## 5. Indução de Tipos: _Scalar Types_

PHP é uma linguagem **NÃO** tipada.

Aos poucos ela vem ganhando alguns recursos que a torna fracamente tipada.

Isso significa que podemos criar códigos mais consistentes e menos suscetíveis a erros e problemas.

O PHP 5 já possui o recurso de <a href="http://php.net/manual/pt_BR/language.oop5.typehinting.php" target="_blank">Indução de Tipos</a>.

É possível definir alguns tipos para parâmetros de métodos e funções. Mas só é possível definir dois tipos: arrays (o tipo &#8220;array&#8221;) e objetos (com o nome da classe).

A partir do PHP 7, poderemos usar outros tipos também: int, float, string e bool.

Esses tipos podem ser definidos nos parâmetros de funções e métodos, como já era feito no PHP 5. Mas agora há uma novidade: também poderemos definir o tipo do retorno.

## 6. Tipo de Retorno de Funções e Métodos

Seguindo a mesma ideia da Indução de Tipos que vimos anteriormente, o PHP 7 vai permitir definir o tipo de retorno de uma função ou método.

Basta seguir esta sintaxe:

<pre class="lang-php">function nomeFuncao() : tipo
{
    // corpo da função
}
</pre>

Por exemplo:

<pre class="lang-php">function soma($x, $y) : float
{
    return $x + $y + 1.5;
}
</pre>

E, claro, pode usar todos os tipos suportados: int, float, string, bool, array e objeto.

## 7. Novo Operador _Spaceship_ (`<=>`)

Esse operador recebe o nome de &#8220;_Spaceship_&#8221; em algumas outras linguagens, e é usado para comparação numérica.

Se você já usou a função `strcmp()`, com certeza vai entender esse operador sem dificuldades.

Mesmo se não usou, é simples de entender.

Veja estes exemplos:

<pre class="lang-php">var_dump(2 &lt;=&gt; 3); // retorna -1
var_dump(2 &lt;=&gt; 2); // retorna 0
var_dump(2 &lt;=&gt; 1); // retorna 1
</pre>

Ou seja, o operador `<=>` retorna um destes 3 valores:

&#8211; retorna -1 quando o primeiro operando é menor que o segundo
  
&#8211; retorna 0 quando os dois operandos são iguais
  
&#8211; retorna 1 quando o segundo operando é maior que o primeiro

## 9. _Null Coalesce Operator_ (operador `??`)

O nome parece complicado, mas ele faz algo bem simples.

Ele é útil para verificar a existência de variáveis, como fazemos com valores de `$_GET` ou `$_POST`, usando `isset`.

Ele faz com que esta linha:

<pre class="lang-php">$email = $_POST['email'] ?? 'valor padrão';
</pre>

&#8230; seja transformada nesta:

<pre class="lang-php">$email = isset($_POST['email']) ? $_POST['email'] : 'valor padrão';
</pre>

Super simples!

## 10. Classes Anônimas

O PHP, a partir da versão 5.4, permite a criação de <a href="http://php.net/manual/pt_BR/functions.anonymous.php" target="_blank">Funções Anônimas</a>. Elas são úteis especialmente para criação de _callbacks_ ou para usar em parâmetros de funções, como `array_map()`.

A partir do PHP 7, podemos criar Classes Anônimas também.

Podemos, por exemplo, fazer uma função retornar uma classe, definida ns própria expressão `return`:

<pre class="lang-php">function createObject()
{
    return new class{
        public function test()
        {
            echo "test" . PHP_EOL;
        }
    };
}

$obj = createObject();
$obj-&gt;test();
</pre>

Há outros casos de uso, como em testes de software.

Você pode ver a proposta e alguns casos de uso no <a href="https://wiki.php.net/rfc/anonymous_classes" target="_blank">RFC que descreve esse recurso</a>.

## Conclusão

O PHP 7 traz diversas novidades. E, se você seguia as Boas Práticas e padrões que o PHP recomendava, a partir da versão 5.5, provavelmente terá pouquíssimos problemas (ou nenhum) para migrar para o PHP 7.

Se quiser conhecer melhor essas novidades e algumas outras, criei um <a href="http://cursophp7.ultimatephp.com.br" target="_blank">curso gratuito</a>, onde mostro com mais detalhes cada um desses novos recursos. Também mostro como instalar o PHP 7, sem afetar a sua instalação atual do PHP 5.

**<a href="http://cursophp7.ultimatephp.com.br" target="_blank">Clique aqui e se inscreva no meu curso gratuito do PHP 7</a>**

Bons estudos e fique de olho no PHP 7!