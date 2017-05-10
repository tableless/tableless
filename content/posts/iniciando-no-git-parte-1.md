---
title: Iniciando no GIT – Parte 1
author: Diego Eis
type: post
date: 2012-11-19
excerpt: Entenda o que é o Git e como iniciar um projeto.
url: /iniciando-no-git-parte-1/
tweetbackscheck:
  - 1356388952
shorturls:
  - 'a:3:{s:9:"permalink";s:31:"http://tableless.com.br/?p=7263";s:7:"tinyurl";s:26:"http://tinyurl.com/c4pazzm";s:4:"isgd";s:19:"http://is.gd/5zK81e";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 934536242
categories:
  - O Básico
  - Técnicas e Práticas
tags:
  - 2012
  - codigo
  - controle versao
  - git

---
Não esqueça de ler a [segunda parte desse artigo][1]. 

Se você não trabalha com nenhum controle de versão ainda ou nem sabe o que isso significa, dá uma lida [nesse texto antes de começarmos aqui][2].

Controles de versão são sistemas que controlam o código gerado em projetos. Se você e mais alguém precisam editar o mesmo arquivo em um mesmo projeto, como você faz? Espera o primeiro editar, salvar e depois subir no FTP só para aí então você abrir o arquivo e fazer suas alterações?

Esse cenário se repete em muitas empresas, de todos os tamanhos. Os controle de versão ajudam a resolver esse e outros problemas de gerenciamento de código e organização. Um dos controles de versão mais conhecidos é o GIT.

> Git é um sistema de controle de versão distribuído com ênfase em velocidade. O Git foi inicialmente projetado e desenvolvido por Linus Torvalds para o desenvolvimento do kernel Linux. &#8211; [Wikipedia, GIT][3]

## Como funciona o GIT?

Normalmente a maioria dos controles de versão guardam as mudanças do código como alterações de um determinado arquivo. Ou seja, a cada mudança no arquivo, o sistema guarda essa mudança apenas e não o arquivo inteiro.

O Git pensa um pouco diferente: ele trata os dados como snapshots. Cada vez que commitamos (commitar é enviar alterações para o controle de versão) ou salva o estado do projeto no Git, ele basicamente guarda um snapshot de como todos os arquivos estão naquele momento e guarda a referência desse estado. Para os arquivos que não foram modificados, ele não guarda uma nova versão, ele apenas faz um link para a versão anterior idêntica que já foi guardada em outro momento.

Esta imagem vem direto do GitHub. Fica mais fácil entender como ele atrela um commit no outro usando snapshots.
  
<img src="http://tableless.com.br/uploads/2012/11/gh-mac-app.png" alt="Github" width="1960" height="1062" class="alignnone size-full wp-image-40447" srcset="uploads/2012/11/gh-mac-app.png 1960w, uploads/2012/11/gh-mac-app-310x168.png 310w, uploads/2012/11/gh-mac-app-572x310.png 572w" sizes="(max-width: 1960px) 100vw, 1960px" />

## Áreas de operação

Os locais de operação são as áreas onde os arquivos irão transitar enquanto estão sendo editados e modificados. São 3: Working Directory, Stage Area, Git directory.

O Git Directory é onde o Git guarda os dados e objetos do seu projeto. Ele é o diretório mais importante do Git e é ele que será copiado quando alguém clonar (clonar é copiar o projeto para a sua máquina) o projeto.

O Work Directory é onde você vai trabalhar. Os arquivos ficam aí para poderem ser usados e alterados quantas vezes quiser para você. É basicamente sua pasta de arquivos dos projeto.

Quando você faz uma alteração em algum arquivo, ele vai para o Staging Area, que é uma área intermediária. Basicamente o Staging Area contém o Git Directory com os arquivos modificados, onde ele guarda as informações sobre o que vai no seu próximo commit. Veja a imagem abaixo direto do [site do Git][4].

<img class="alignnone size-full wp-image-7264" title="18333fig0106-tn" src="http://tableless.com.br/uploads/2012/11/18333fig0106-tn.png" alt="" width="500" height="460" srcset="uploads/2012/11/18333fig0106-tn.png 500w, uploads/2012/11/18333fig0106-tn-300x276.png 300w" sizes="(max-width: 500px) 100vw, 500px" />

## Instalando o Git

Se você tem Windows [baixe o EXE direto deste link][5] e instale.

Ele vai instalar para você os comandos do Git para serem usados no terminal e uma uma interface padrão para quem não está acostumado a usar linhas de comando.

No Mac você tem vários caminhos, [baixando o installer][6], usando Macports:

<pre>$ sudo port install git-core +svn +doc +bash_completion +gitweb</pre>

E até mesmo usando Brew.

<pre>brew install git</pre>

Com Linux eu preciso falar? 😉

Yum.

<pre>$ yum install git-core</pre>

Ou apt-get.

<pre>$ apt-get install git-core</pre>

## Configurando suas informações

A primeira coisa que você deve fazer depois de instalar o Git é definir seu usarname e email. Isso é importante por que os seus commits usarão essas informações para identificar o autor das mudanças. Pois é&#8230; Se alguém fizer alguma merda no projeto e quebrar todo o sistema, é possível saber quem, quando e qual linha foi o autor do apocalipse.

É simples, no terminal escreva:

<pre>$ git config --global user.name "John Doe"
$ git config --global user.email johndoe@example.com
</pre>

## Controlando um projeto

Pelo terminal mesmo, entre na pasta do projeto que você quer iniciar o controle e use o comando:

<pre>git init</pre>

Esse comando vai criar um diretório invisível dentro do projeto chamado **.git**. Ele contém todos os arquivos necessários do seu repositório. Aqui, neste ponto, nada dos seus arquivos ainda estão sendo controlados. Você apenas criou um &#8220;lugar&#8221; (branch) para o Git colocar os arquivos.

O próximo comando vai inserir os arquivos que você quer controlar. Normalmente a gente controla TUDO o que está no projeto. Mas isso tem que ser combinado com a equipe antes. Em um projeto que envolve um CMS com o WordPress, por exemplo, é normal controlar tudo, até os arquivos do WordPress. Mas se em um projeto você guarda pastas de layouts, pastas de wireframes, protótipos e etc, é interessante não colocar isso no Git. Mas aí vai de equipe para equipe, de projeto pra projeto.

O comando para adicionar os arquivos é:

<pre>git add .</pre>

Para você ver o status, use o comando **git status**, aí você verá tudo o que foi incluído no projeto. Veja o screenshot abaixo para ter uma ideia:

![][7]

Feito isso você vai precisar inserir seu primeiro commit. Vamos dar mais detalhes sobre o comando commit no próximo artigo, por agora fique com essa linha:

<pre>git commit -m "Primeiro commit - Inserindo os arquivos iniciais do projeto"</pre>

Agora você mandou uma alteração para o Git.

### Clonando um projeto

Pode ser que já exista um projeto no Git criado e você só precise clonar para seu computador. Para isso você vai usar o comando **git clone**.

Quando você clona um projeto, o Git recebe a cópia de todos os dados que tem no servidor. Cada versão de cada arquivo da história inteira do projeto é puxada quando você roda o comando **git clone**.

Para clonar um projeto você precisa ter a URL do Git daquele projeto em específico. O comando completo fica mais ou menos assim:

<pre>git clone https://github.com/tableless/exemplos.git</pre>

Pode testar com o endereço acima. Ele é nosso diretório do Git de exemplos no GitHub.

No próximo artigo a gente mostra os comandos **commit**, **push** e **pull**.

Veja um vídeo que mostra os comandos básicos do GIT:

 [1]: http://tableless.com.br/iniciando-no-git-parte-2/
 [2]: http://tableless.com.br/introducao-das-premissas-dos-controles-de-versao/ "Introdução das premissas dos controles de versão"
 [3]: http://pt.wikipedia.org/wiki/Git
 [4]: http://git-scm.com/
 [5]: http://code.google.com/p/msysgit
 [6]: http://code.google.com/p/git-osx-installer
 [7]: http://tableless.com.br/uploads/2012/11/Screen-Shot-2012-11-19-at-11.21.33-AM.png