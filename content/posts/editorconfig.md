---
title: EditorConfig
author: Diego Eis
type: post
date: 2013-08-19
excerpt: EditorConfig, um plugin que salva a vida de equipes inteiras.
url: /editorconfig/
dsq_thread_id: 1617492381
categories:
  - CSS
  - CSS3
  - Editores
  - JavaScript
  - O Básico
tags:
  - 2013
  - editorconfig
  - editores

---
Você já deve ter visto discussões em equipes para definir o estilo de código usado em projetos. Discutir se será tabs ou espaços, o tamanho do tab, charset e etc. Todo mundo tem que configurar o editor igualmente para que não quebre nenhum arquivo e fique aquela bagunça. Não existia solução de verdade para isso, até agora. Cada um usa um editor diferente, com configurações diferentes e muito pior, todo mundo tem um gosto pessoal diferente. É aí que entra o [EditorConfig][1].

O EditorConfig ajuda a definir e manter estilos de códigos consistentes entre diversos editores. Ele é um simples arquivo que guarda as configurações de estilo do código, o seu editor predileto lê estas configurações e entende exatamente qual a configuração utilizar para cada formato de arquivo.

<pre class="lang-json">; Pra todos os arquivos
[*]
charset = utf-8
end_of_line = lf
insert_final_newline = true

; Estilo de identação em arquivos HTML
[*.html]
indent_style = tab
indent_size = 4

; Estilo de identação em arquivos CSS
[*.css]
indent_style = tab
indent_size = 4

; Estilo de identação em arquivos JS dentro do diretório Scripts
[scripts/*.js]
indent_style = tab
indent_size = 2
</pre>

Interessante, ahn?

Como funciona? Simples: você baixa e instala um plugin para seu editor, aí você cria um arquivo .editorconfig com as configurações escolhidas, coloca este arquivo na raiz do seu projeto (ou em pastas específicas) e pronto.

Tem plugins para diversos editores: Sublime Text, TextMate, VIM, Notepad++, gEdit, PHPStorm, PyCharm, RubyMine, Visual Studio e outros.

Obviamente que os integrantes da equipe devem brigar apenas uma vez, para definir qual será o estilo base do código. Depois disso é só escrever um EditorConfig e pronto.

 [1]: http://editorconfig.org