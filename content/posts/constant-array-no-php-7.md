---
title: Constant Array no PHP 7
author: Rodrigo Brandão
type: post
date: 2016-02-18
excerpt: Com o lançamento do PHP 7, agora é possível criar constantes do tipo array (vetor).
url: /constant-array-no-php-7/
categories:
  - Back-end
  - Código
  - PHP
tags:
  - php
  - php7

---
Até o lançamento da versão do PHP 7, só era possível criar constantes com dados do tipo _inteiro_, _float_, _string_, _boolean_, ou _NULL_, mas com o PHP 7 agora é possível criar constantes do tipo _array_.
  
<!--more-->

Vamos lá. Definindo uma constante:

<pre>define("CONSTANT", "Olá Constantes.");
echo CONSTANT; // Resultando em: "Olá Constantes."
</pre>

### Com o PHP 7 criando uma constante do tipo array (matrizes)

Exemplo de constante array:

<pre>// array simples:

define("CONSTANT_ARRAY", ['pera', 'uva', 'maça',]);
echo 'Eu gosto de comer ' . CONSTANT_ARRAY[1];
// Resultando em: "Eu gosto de comer uva"
</pre>

Também é possível usar arrays multidimensionais:

Exemplo de constante array multimensional:

<pre>// array multidimensional:
define("CONSTANT_ARRAY_MULTIDIMENSIONAL", [
'frutas' =&gt; ['pera', 'uva', 'maça',],
'carros' =&gt; ['fusca', 'chevette', 'passat',],
'mulheres' =&gt; ['loira', 'ruiva', 'morena',],
]);
echo 'Eu gosto de comer ' . CONSTANT_ARRAY_MULTIDIMENSIONAL['frutas'][1];
// Resultando em: "Eu gosto de comer uva"
echo '&lt;br&gt;';
echo 'meu carro é um ' . CONSTANT_ARRAY_MULTIDIMENSIONAL['carros'][2];
// Resultando em: "Meu carro é um passat"
echo '&lt;br&gt;';
echo 'As ' . CONSTANT_ARRAY_MULTIDIMENSIONAL['mulheres'][0] . 's são mais bonitas.';
// Resultando em: "As loiras são mais bonitas."
</pre>

Só lembrando, as constantes são _case sensitive_, ou seja, se você declarou a mesma em letras maiúsculas, só poderá usá-la com letra maiúscula.

### Usando a sintaxe **const**

Também é possível utilizar a sintaxe **const** para criar uma constante no PHP, mas essa só poderá ser usada dentro de uma classe:

<pre>class MinhaClasse
{
const MINHACONSTANTE = ['pera', 'uva', 'maça',];

public static function constante() {
return self::MINHACONSTANTE;
}
}
</pre>

No exemplo acima usei um array simples, a mesma usado no primeiro exemplo, mas agora dentro da classe _MinhaClasse_.

Seu uso seria algo assim:

<pre>$meuArray = MinhaClasse::constante();
print_r($meuArray);
</pre>

O código acima irá imprimir:

<pre>Array ( [0] =&gt; pera [1] =&gt; uva [2] =&gt; maça )</pre>

[<img class="alignnone size-full wp-image-52669" src="http://tableless.com.br/uploads/2016/01/Captura-de-tela-de-2016-01-02-16-17-16.png" alt="Constant Class PHP com array" width="491" height="303" />][1]

Lembrando que, para obter sucesso com os exemplos acima, é necessário ter a versão 7 do PHP ou superior. As demais versões não dão suporte á constantes do tipo _array_.

No exemplo, também foi usado a _short sintaxe_ do array. Você também pode usar a sintaxe antiga, mas é uma questão de gosto pessoal. Eu, particularmente, quando escrevo um array, sempre procuro usar a versão curta. Além de ser mais bonita e simples, também se aproxima de outras linguagens, como o JavaScript, por exemplo.

 [1]: http://tableless.com.br/uploads/2016/01/Captura-de-tela-de-2016-01-02-16-17-16.png