---
title: Funções extras para tratamento de Strings no PHP
author: chaves_dev
type: post
date: 2015-03-09
excerpt: Há alguns dias atrás enquanto estava contribuindo em um webservice, me deparei novamente com um problema para tratamento de strings no PHP, onde precisava fazer algumas operações extras.
url: /funcoes-extras-para-tratamento-de-strings-no-php/
categories:
  - Back-end
  - PHP
tags:
  - caracteres
  - functions
  - php
  - strings
  - substituir

---
Como o projeto já estava atrasado, decidi que seria melhor continuar pesquisando alguma alternativa para resolver o problema da &#8220;limpagem&#8221; de strings, então encontrei a biblioteca [URLify for PHP][1]

A principio ele é uma classe simples em PHP com as funcionalidades que não são nativas do PHP, porém são uma mão na roda na hora de trabalhar com strings em projetos grandes, onde não existe tempo para o dev criar do zero (muito menos testá-los sem perder o foco do problema que realmente importa).

Como trabalho com CakePHP, só tive o trabalho de adicioná-lo no meu diretório &#8216;Lib&#8217;, importar a classe,

<pre class="lang-php">App::uses('URLify','Lib');
</pre>

e chamar a função &#8216;::downcode&#8217;, que transcreve os caracteres especiais para os seus correspondentes no alfabeto (Ex: &#8216;ç&#8217; -> &#8216;c&#8217; ; &#8216;á&#8217; -> &#8216;a&#8217;)

<pre style="font-size:16px" class="lang-php">$mytext = 'caçamba lilás';
   $newtext = URLify::downcode($mytext);
   //cacamba lilas
</pre>

e pronto, mantive meu código limpo, com uma biblioteca leve e elegante.

A classe também possui outros métodos bem legais de filtragem de strings como o &#8216;::add_chars&#8217;, que permite adicionar suas próprias exceções a lista de filtragem de caracteres.

<pre class="lang-php">URLify::add_chars (array (
         '¿' =&gt; '?', '®' =&gt; '(r)', '¼' =&gt; '1/4',
         '¼' =&gt; '1/2', '¾' =&gt; '3/4', '¶' =&gt; 'P'
     ));

     echo URLify::downcode ('¿ ® ¼ ¼ ¾ ¶');
     // "? (r) 1/2 1/2 3/4 P"

</pre>

e o &#8216;::remove_words&#8217;, que pelo nome ja dá pra saber o que faz&#8230;

<pre style="font-size:16px" class="lang-php">URLify::remove_words (array ('remove', 'these', 'too'));
</pre>

E é isso, espero que tenha ajudado alguém, até o próximo post&#8230;

 [1]: https://github.com/jbroadway/urlify " URLify for PHP"