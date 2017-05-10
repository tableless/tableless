---
title: Include Tags WordPress, conheça alguns truques legais
author: Wanderson Macêdo
type: post
date: 2014-06-13
excerpt: 'Sabe aquelas tags de inclusão de arquivos do WordPress, chamadas de include tags?  Saiba como utilizar cada uma delas de uma forma diferente do que é comumente falado.'
url: /include-tags-wordpress-conheca-alguns-truques-legais/
dsq_thread_id: 2670389421
categories:
  - CMS
  - Wordpress
tags:
  - Include Tags
  - Wordpress

---
Quem já desenvolveu algum tema ou simplesmente deu uma xeretada nos temas que vem na instalação do WordPress, deve ter percebido que em cada um daqueles arquivos há algumas funções que incluem um outro arquivo do tema. Se você já notou isso parabéns: você já conhece as Include Tags, se não, saiba quem são agora mesmo.

## As Include Tags

Você já conhece a função include do PHP? Ela é uma função que simplesmente adiciona/importa um outro arquivo dentro do arquivo em que você usou essa função; geralmente usado para adicionar arquivos de configuração para determinado script funcionar corretamente. O código é algo assim:

<pre class="lang-php">&lt;?php include 'header.php'; ?>
</pre>

As Include Tags WordPress funcionam da mesma maneira, diferenciando somente por serem variações especiais dessa mesma função.

### get_header();

A função get_header importa o arquivo chamado de **header.php** que estiver dentro da pasta do tema em questão. Simples assim. O que não se comenta muito sobre essa função é que ela pode receber um parâmetro. Sendo assim, se passar um parâmetro para esta função, ela trará um resultado diferente do padrão, por exemplo:

<?php get_header(‘home’); ?>

Nesse exemplo o WordPress adicionará ao arquivo em questão um outro arquivo com o nome de **header-home.php**. Se ele encontrar o header-home.php, ele busca o header.php e em último caso (se não encontrado o arquivo) o header.php que está no seguinte diretório do WordPress será importado: **wp-includes/theme-compat/header.php**.

Bom, se você entendeu o funcionamento do get_header(), não vai ter dificuldade nenhuma com as outras Include Tags.

### get_footer();

Funciona da mesma maneira do get\_header(), mudando somente o arquivo que esta função busca, que por padrão é o footer.php. Se passado o parâmetro da mesma que vimos no get\_header() o funcionamento é igual, buscando então o arquivo footer-nome.php e em último caso o do diretório do WordPress é importado, estando esse em: **wp-includes/theme-compat/footer.php**.

_Se você esteve atento, a explicação é simples, e a cada função há somente uma adaptação da explicação anterior! Então não me atentarei a fazer essa adaptação para o restante das funções&#8230;_

### get_sidebar();

O get_sidebar(), funciona da mesma forma das funções anteriores, contudo este busca pelo arquivo sidebar.php ou sidebar-valordoparametro.php ou em último caso o sidebar.php disponibilizado pelo WordPress em: **wp-includes/theme-compat/sidebar.php**.

### get\_template\_part();

Essa diferente das demais: você busca qualquer arquivo que queira incluir. Exemplo:

<?php get\_template\_part(‘loop’); ?>

O resultado disso é a importaçnao do arquivo **loop.php**. É interessante notar que essa função pode receber dois parâmetros, importando assim o arquivo cujo nome esteja de acordo com a seguinte regra: **primeiroparametro-segundoparemetro.php**.

Exemplo:

<?php get\_template\_part(‘loop’,’index’); ?>

Este importaria o arquivo loop-index.php que estiver dentro da pasta do tema.

### get\_search\_form();

Esta função importa um arquivo chamado **searchform.php**, onde encontra-se geralmente o formulário de pesquisa, caso o arquivo não exista, o WordPress gera um formulário de pesquisa padrão e exibe no local onde a função foi chamada.

### comments_template()

E por último e não menos importante o: **comments_template()**. Essa função importa o arquivo comments.php (arquivo usado para exibição de comentários em postagens) e caso não encontre no diretório do tema, ela importa um arquivo padrão do WordPress localizado em: **wp-includes/theme-compat/comments.php**

## O truque de tudo isso

Você deve estar se perguntando, onde está o truque nisso tudo?

O truque está em quando um cliente solicitar ou quando o projeto exigir que uma determinada página do site ou portal que você esteja desenvolvendo precisar de um front-end totalmente diferente do padrão, você simplesmente pode criar um arquivo com esta modificação e incluí-lo onde for necessário.

Estas funções também ajudam bastante no desenvolvimento de themes, quando estamos separando as responsabilidades em módulos. 

Sendo assim, passei a receita de como se prevenir de determinadas situações das quais já passei em meu tempo de desenvolvimento para WordPress.

Isso é tudo pessoal, até o próximo artigo! 😉

Dica: Fique sempre atento a documentação do WordPress! O Codex é a bíblia de tudo o que você pode conhecer sobre WordPress. Não se preocupe em decorar tudo, o Codex do WordPress sempre vai server como referência. Abaixo segue os links:

  * [Include Tags][1]
  * [Codex WordPress][2]

 [1]: http://codex.wordpress.org/Include_Tags
 [2]: http://codex.wordpress.org/