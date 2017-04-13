---
title: Manipulando janelas e arquivos no VIM
author: weslleyaraujo
type: post
date: 2015-03-11
excerpt: Algumas dicas para trabalhar de maneira rápida com múltiplos arquivos no VIM.
url: /manipulando-janelas-e-arquivos-no-vim/
categories:
  - Editores
tags:
  - editores
  - vi
  - vim

---
Como sabemos, o VIM é um editor muito poderoso e está disponível na maioria dos sistemas UNIX.

Uma das coisas que sempre senti dificuldades foi a forma de manipular janelas e eventualmente gerenciar os arquivos que estou trabalhando.
  
Vou mostrar algumas técninas que aprendi durante o tempo, e que hoje me ajudam a resolver esses problemas.

**NOTA: OS COMANDOS ABAIXOS DEVEM SER EXECUTADOS USANDO O <a href="http://en.wikibooks.org/wiki/Learning_the_vi_Editor/Vim/Modes" target="_blank">&#8220;NORMAL MODE&#8221;</a> QUE VOCÊ PODE ACESSAR USANDO A TECLA \`ESC\`.
  
** 

## Abrir arquivos de qualquer lugar

Um comandos mais interessantes é o **:edit** que permite você acessar arquivos de qualquer lugar desde a raiz do seu computador!

Na prática ele funciona assim:

<pre class="lang-bash">:edit &lt;caminho-para-meu-arquivo&gt;</pre>

ou de uma forma mais simples usando somente:

<pre class="lang-bash">:e &lt;caminho-para-meu-arquivo&gt;</pre>

## Divindo as janelas

Uma outra feature bem legal do é o **split window**, que permite fazer a divisão das janelas do seu workspace e trabalhar abertamente entre elas.

Há dois tipos diferentes:

  * **:vsp** vertical split
  * **:sp** split (horizontal)

A forma como esses comandos funcionam são bem similares ao **:edit**: você pode simplesmente indica como vai ser essa divisão e passa como parâmetro o path do seu arquivo:

<pre class="lang-bash">:vsp &lt;caminho-para-meu-arquivo&gt;
</pre>

ou horizontal:

<pre class="lang-bash">:sp &lt;caminho-para-meu-arquivo&gt;</pre>

Legal! E como mudo meu foco para cada uma dessas &#8220;janelas&#8221;?

Você pode mover o seu foco usando o comando **ctrl + w** seguido da direção que a sua janela se encontra:

<img class="aligncenter size-full wp-image-47538" src="http://tableless.com.br/uploads/2015/03/present-vim.gif" alt="present-vim" width="710" />

_a tecla **w** é usada lembrar a palavra **window**_.

## Conclusão

O Vim pode ser um grande amigo com o tempo. É uma longa jornada para se adaptar com todas as particularidades desse editor, mas aos poucos tudo se torna mais fácil e bastante produtivo. 🙂