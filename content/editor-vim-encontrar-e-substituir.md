---
title: Editor Vim – Encontrar e Substituir
author: Henrique Schreiner
type: post
date: 2015-03-03
excerpt: Dicas de comandos no Vim que podem te ajudar a poupar tempo, dinheiro e deixar o seu cliente feliz e satisfeito.
url: /editor-vim-encontrar-e-substituir/
categories:
  - Código
  - Editores
  - Geral
  - Técnicas e Práticas
tags:
  - editor
  - terminal
  - vim

---
Quem nunca precisou acessar o servidor de um cliente via SSH para resolver um problema de última hora? Um parâmetro errado, uma vírgula faltando pode comprometer a execução de um código.

Quando se tem apenas a tela preta do terminal, é preciso ter conhecimento de alguns comandos muito úteis que podem te ajudar a resolver um problema rapidamente, principalmente se você não tem um computador disponível, podendo também resolver o problema até pelo celular com qualquer App de conexão SSH.

O que muitas pessoas não sabem, é que o editor <a title="Editor Vim" href="http://www.vim.org/" target="_blank">Vim</a>, além de vários outros comandos para se navegar por um código e fazer modificações em massa com expressões regulares, possui um comando chamado **substitute**, muito útil na hora de procurar e substituir uma variável ou um trecho de código. Muitas vezes, esse trecho se repete várias vezes dentro do arquivo e algumas expressões regulares podem te ajudar a substituí-los de uma vez só, economizando tempo e facilitando a sua vida. Existem muitas opções, mas provavelmente essas serão as que mais vão ser úteis:

<p style="padding-left: 30px">
  &#8211; Encontra cada ocorrência de <strong>&#8216;foo&#8217;</strong> (em todas as linhas) e substitui por <strong>&#8216;bar&#8217;</strong>:
</p>

<pre class="lang-bash">:%s/foo/bar/g</pre>

<p style="padding-left: 30px">
  &#8211; Encontra cada ocorrência de <strong>&#8216;foo&#8217;</strong> (apenas na linha atual) e substitui por <strong>&#8216;bar&#8217;</strong>:
</p>

<pre class="lang-bash">:s/foo/bar/g</pre>

<p style="padding-left: 30px">
  &#8211; Substitui cada <strong>&#8216;foo&#8217;</strong> por <strong>&#8216;bar&#8217;</strong>, mas pedindo confirmação primeiro:
</p>

<pre class="lang-bash">:%s/foo/bar/gc</pre>

<p style="padding-left: 30px">
  &#8211; Substitui apenas palavras inteiras que correspondam com <strong>&#8216;foo&#8217;</strong> por <strong>&#8216;bar&#8217;</strong>, pedindo por confirmação:
</p>

<pre class="lang-bash">:%s/\&lt;foo\&gt;/bar/gc</pre>

<p style="padding-left: 30px">
  &#8211; Substitui cada <strong>&#8216;foo&#8217;</strong> (case insensitive) por <strong>&#8216;bar&#8217;</strong>, pedindo por confirmação (usado após o uso de <strong>:set noignorecase</strong> para fazer as consultas serem <strong>case sensitive</strong>, que é o padrão):
</p>

<pre class="lang-bash">:%s/foo/bar/gci</pre>

<p style="padding-left: 30px">
  &#8211; Substitui cada <strong>&#8216;foo&#8217;</strong> (case sensitive) por <strong>&#8216;bar&#8217;</strong>, pedindo por confirmação (usado após o uso de <strong>:set ignorecase</strong> para fazer as consultas serem <strong>case insensitive</strong>):
</p>

<pre class="lang-bash">:%s/foo/bar/gcI</pre>

Alguns outros exemplos de comandos para encontrar e substituir podem ser encontrados <a title="Vim - Search and Replace" href="http://vim.wikia.com/wiki/Search_and_replace" target="_blank">aqui</a> (em inglês).

Espero que estas dicas possam ser úteis e que possam ajudá-lo nos seus trabalhos e melhorar sua produtividade.