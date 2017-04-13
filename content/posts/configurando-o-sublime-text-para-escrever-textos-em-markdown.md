---
title: Configurando o Sublime Text para escrever textos em MarkDown
author: Daniel Schmitz
type: post
date: 2015-10-26
url: /configurando-o-sublime-text-para-escrever-textos-em-markdown/
categories:
  - Editores
tags:
  - corretor ortográfico
  - editor
  - ide
  - mark down
  - md
  - sublime text

---
Neste artigo aprenderemos como configurar alguns plugins para o Sublime Text 2, para que você possa ter uma melhor experiência ao escrever textos em português com a linguagem de marcação de texto MarkDown, muito comum na criação de livros, artigos, tutoriais, e claro, dos arquivos README.md do GitHub.

## Instalando o Sublime Text 2

Você ainda não usou o Sublime Text? Eu duvido! Mas se não usou, aqui está a receita para a sua instalação:

<pre class="lang-bash">sudo add-apt-repository ppa:webupd8team/sublime-text-2
sudo apt-get update
sudo apt-get install sublime-text  
</pre>

Ou acesse [o site oficial do Sublime Text][1], clicar em download e instalar.

## Instalando o dicionário em português

Após muito &#8220;fuçar&#8221; eu encontrei um dicionário em português que atende completamente as minhas necessidades como escritor. Tenho usado ele nos meus livros e recomendo para você também, lembrando que existem alguns dicionários antigos que estão perdidos por aí. Para você não perder tempo, criei um repositório no github com os arquivos corretos. 

Para instalar o dicionário, primeiro acesse [este repositório][2] e clique no botão `Download Zip` (ou faça `git clone` se for natural para você). Após fazer o download, copie a pasta `Languages` para o seu diretório de configuração do Sublime Text, que depende do sistema operacional:

  * Windows: %APPDATA%\Sublime Text 2
  * Linux: ~/.config/sublime-text-2/Packages/
  * Mac: ~/Library/Application Support/Sublime Text 2

Após copiar a pasta Languages, volte ao Sublime Text e acesse  `View > Dictionary > Languages > pt_br > Portuguese(Brazilian)`. Com o dicionário selecionado, use a tecla de atalho `F6` para habilitar/desabilitar o spell check. As palavras que não estiverem no dicionário serão sublinhadas em vermelho, e pode-se usar o menu de contexto para correção.

## Instalando o Package Control

O Package Control é o gerenciador de pacotes do Sublime Text. Para instalar ele, você deve acessar <https://packagecontrol.io/installation#st2> e copiar todo texto que está na aba &#8220;Sublime Text 2&#8221;. Após copiar, vá ao Sublime Text, navegue até `View > Show Console` e cole o texto no console que abre na parte inferior do Sublime. Após executar o comando, o Package Control é instalado e você deve reiniciar o editor. Talvez seja necessário reiniciar algumas vezes até o Package Control estabilizar.

## Instalando pacotes essenciais

Para instalar um pacote, tecle `CTRL+SHIFT+P` que é a tecla padrão do Sublime para executar comandos, e digite &#8220;install package&#8221; no menu de contexto. Aguarde alguns segundos e um novo menu cheio de pacotes será exibido. O primeiro que deve ser instalado é o `MarkDown Editing`. Cuidado para não instalar Markdown Extended ao invés do Markdown Editing. Selecione-o e aguarde a instalação finalizar.

Outro pacote necessário para instalação é o `Monokai Extended`. Instale-o da mesma forma que fez com o pacote anterior. 

## Configuração

Agora vamos configurar nossos pacotes. Para isso, é necessário acessar `Preferences > Package Settings > MarkDown Editing > Markdown GFM Settings - USER` e adicionar a seguinte configuração:

<pre class="lang-json">{
    "color_scheme": "Packages/Monokai Extended/Monokai Extended.tmTheme",
    "draw_centered": true,
    "wrap_width": 40,
    "word_wrap": true,
    "line_numbers": true
}
</pre>

Você pode alterar os parâmetros conforme a sua vontade. Nos parâmetros acima, já temos um visual semelhante a seguir:

<img src="http://tableless.com.br/uploads/2015/10/Captura-de-tela-de-2015-10-17-072103.png" alt="Captura de tela de 2015-10-17 07:21:03" width="1366" height="768" class="alignleft size-full wp-image-51761" />

## Configurações extras

As configurações acima serão aplicadas somente aos arquivos com a extensão `.md`. Para realizar algumas configurações globais, você deve editar abrir `Preferences > Settings - User`, e pode adicionar os parâmetros que desejar, conforme o exemplo a seguir:

<pre class="lang-json">{
    "color_scheme": "Packages/Color Scheme - Default/Monokai.tmTheme",
    "font_face": "Ubuntu",
    "font_size": 20,
    "line_numbers": true,
    "tab_size": 4,
    "translate_tabs_to_spaces": true
}
</pre>

## Temas

Existem diversos temas para serem instalados pelo Package Control. Um deles é o `Soda`. Instale o package `Soda - Theme` e após a instalação, volte ao `Settings - User` e adicione a seguinte linha:

<pre class="lang-json">{
    ....conf iniciais
    "translate_tabs_to_spaces": true,
   <strong> "theme": "Soda Dark.sublime-theme"</strong>
}
</pre>

Reinicie o Sublime Text 2 e pronto, temos uma configuração bem legal para editar arquivos Mark Down, veja:

<img src="http://tableless.com.br/uploads/2015/10/Captura-de-tela-de-2015-10-17-073140.png" alt="Captura de tela de 2015-10-17 07:31:40" width="1366" height="768" class="alignleft size-full wp-image-51763" />

## Outros pacotes

O sublime tem diversos packages úteis, vou deixar alguns a seguir que mais uso:

  * git &#8211; Execute os comandos do git pelo ctrl+shift+p 
  * GitGutter &#8211; Exibe as alterações de um arquivo git no editor
  * Clipboard &#8211; History &#8211; History da área de transferência

Deixe nos comentários os pacotes que você usa.

 [1]: http://www.sublimetext.com/
 [2]: https://github.com/danielschmitz/sublime_text_2_for_markdown