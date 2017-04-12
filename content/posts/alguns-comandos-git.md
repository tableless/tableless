---
title: Comandos iniciais do Git
author: Candido Souza
type: post
date: 2015-01-09
excerpt: Conheça os comandos básicos do Git nesse artigo simples.
url: /alguns-comandos-git/
categories:
  - Código
  - Editores
  - Técnicas e Práticas
  - Tecnologia e Tendências
tags:
  - comandos
  - git
  - terminal

---
O Git é um [sistema de controle de versão][1]. Com o Git você não perderá seu trabalho, vai poder voltar para a versões anteriores, recuperando a versão do seu código de antes de ter cometido o erro e poderá criar e trabalhar diversas versões em paralelo.

Uma ótima leitura que indico é o livro <a title="Livro Pro Git" href="http://git-scm.com/book/en/v2" target="_blank">Pro Git</a>, escrito por Scott Chacon. Ele descreve corretamente sobre o controle de versão. Olhe só:

#### O que é controle de versão, e por que você deve se importar?

&#8220;O controle de versão é um sistema que registra as mudanças feitas em um arquivo ou um conjunto de arquivos ao longo do tempo, de forma que você possa recuperar versões específicas.

Se quer manter todas as versões de uma imagem ou layout, usar um Sistema de Controle de Versão (Version Control System ou VCS) é uma decisão sábia. Ele permite reverter arquivos e projetos inteiros para um estado anterior, compara mudanças feitas ao decorrer do tempo, vê quem foi o último a modificar algo que pode estar causando problemas, quem introduziu um bug e quando, e muito mais. Usar um VCS normalmente significa que caso tenha estragado ou perdido algum arquivo, poderá facilmente reavê-los. Além disso, você pode controlar tudo sem maiores esforços.&#8221;

## Vamos lá!

Bom, depois dessa aula com Scott Chacon, vamos ver alguns códigos!

Lembrando que todos os comandos aqui devem ser feitos pelo Terminal, Console, GitBash, entre outros e o não recomendado Prompt de Comando do Windows, incluindo entradas e saídas de pastas, tudo por comandos!

### Iniciando o Git

Entre no diretório que deseja controlar a versão e inicie o Git assim:

<pre class="lang-bash">git init</pre>

Feito isso, seus arquivos ainda não estão sendo versionados, mas eles estão esperando para serem adicionados no estágio de controle. Para fazer isso digite o comando

<pre class="lang-bash">git add nome-do-arquivo-incluindo-extensão</pre>

Se você precisa adicionar todos os arquivos do diretório, basta digitar:

<pre class="lang-bash">git add .</pre>

Saber o status do projeto é importante. Com o comando abaixo você consegue ver quais arquivos estão fora do controle, quais foram modificados e estão esperando por uma descrição de modificação etc:

<pre class="lang-bash">git status</pre>

Voltando ao estágio anterior do adicionamento:

<pre class="lang-bash">git reset HEAD nome-do-arquivo</pre>

Commit &#8211; Comitando:

<pre class="lang-bash">git commit -m "Mensagem do commit"</pre>

Adicionando e comitando ao mesmo tempo:

<pre class="lang-bash">git commit -a -m "Mensagem do commit"</pre>

### Voltando commits a versões anteriores

Voltar um commit:

<pre class="lang-bash">git reset HEAD~1</pre>

Voltar dois commits:

<pre class="lang-bash">git reset HEAD~2</pre>

Voltando um commit e deixando o arquivo no estagio anterior:

<pre class="lang-bash">git reset HEAD~1 --soft</pre>

Voltando um commit e excluindo o arquivo, deixando no estágio anterior:

<pre class="lang-bash">git reset HEAD~1 --hard</pre>

Verificando o histórico de commits:

<pre class="lang-bash">git log</pre>

Verificando o que foi mudado, diferença entre um arquivo e outro:

<pre class="lang-bash">git log -p</pre>

Verificando os 2 últimos commits:

<pre class="lang-bash">git log -p -2</pre>

Mostrando as estatísticas de todos os commits:

<pre class="lang-bash">git log --stat</pre>

Mostrando todos os commits, cada um em uma linha:

<pre class="lang-bash">git log --pretty=oneline</pre>

Mostrando todos os commits dos últimos 2 dias até o momento atual

<pre class="lang-bash">git log --since=2.days</pre>

Criando um branch &#8211; uma ramificação

<pre class="lang-bash">git checkout -b nome-do-branch</pre>

Verificando em que branch você está

<pre class="lang-bash">git branch</pre>

Voltando para o branch master

<pre class="lang-bash">git checkout master</pre>

### Jogando o branch criado no branch master

Entre como branch master:

<pre class="lang-bash">git merge nome-do-branch-que-foi-criado</pre>

### Grudando o branch criado no branch master sem o commit

Somente localmente &#8211; localhost, entre como branch master:

<pre class="lang-bash">git rebase nome-do-branch-que-foi-criado</pre>

Removendo um branch:

<pre class="lang-bash">git branch -D nome-do-branch</pre>

Vendo branchs remotos:

<pre class="lang-bash">git branch -a</pre>

Mostrando o início do hash, quem comitou, quanto tempo atrás, mensagem: descrição do commit:

<pre class="lang-bash">git log --pretty=format: "%h - %an, %ar : %s"</pre>

Deletando arquivos:

<pre class="lang-bash">git rm nome-do-arquivo</pre>

Deletando todos os aquivos removidos ao mesmo tempo:

<pre class="lang-bash">git ls-files --deleted | xargs git rm</pre>

### Ignorando arquivos

Existem alguns arquivos que muito provavelmente você não vai precisar versionar, como por exemplo os arquivos de cache do SASS, arquivos de configuração e etc. Nesse caso você precisa fazer com que o controle de versão ignore estes arquivos. Para tanto, crie um arquivo chamado **.gitignore**. Feito isso, dentro deste arquivo, digite o nome ou o endereço das pastas que você quer ignorar. Um exemplo:

<pre class="lang-javascript"># See http://help.github.com/ignore-files/ for more about ignoring files.
#
# If you find yourself ignoring temporary files generated by your text editor
# or operating system, you probably want to add a global ignore instead:
# git config --global core.excludesfile ~/.gitignore_global

# Ignore bundler config
/.bundle

# Ignore the build directory
/build

# Ignore Sass' cache
/.sass-cache

# Ignore .DS_store file
.DS_Store
.cache
.rvmrc

vendor/*

.DS_Store

# Vim
*.swp
*.swo

Gemfile.lock
.vagrant
Vagrantfile

# rbenv
.ruby-version

# Ignore deploy related files
deploy

Gemfile.lock

</pre>

O arquivo **.gitignore** fica na raiz do projeto.

### Clonando e puxando alterações de projetos

Clonando um projeto remoto:

<pre class="lang-bash">git clone url-do-projeto</pre>

Fazendo um clone de outros branchs:

<pre class="lang-bash">git checkout -b nome-do-branch origin/ nome-do-branch</pre>

Trazendo, puxando as alterações feitas por outros usuários:

<pre class="lang-bash">git pull origin master</pre>

Sincronizando tudo que está no repositório remoto:

<pre class="lang-bash">git pull</pre>

Enviando o(s) projeto(s), arquivo(s) para o repositório:

<pre class="lang-bash">git push origin master</pre>

Enviando um branch para o repositório:

<pre class="lang-bash">git push origin nome-do-branch</pre>

### Tags

As tags servem para marcar uma etapa. Imagine que você vai lançar uma versão, que resolve uma série de problemas. Você pode marcar aquela etapa criando uma tag. Assim fica simples de fazer qualquer rollback do projeto para uma tag específica em vez de voltar para um commit. Você sabe que tudo o que foi feito até aquela tag está funcionando.

Criando tags:

<pre class="lang-bash">git tag versão-da-tag</pre>

Listando tags:

<pre class="lang-bash">git tag -l</pre>

Enviando a tag para o repositório

<pre class="lang-bash">git push origin master --tags</pre>

Removendo as tags criadas localmente:

<pre class="lang-bash">git tag -d versão-da-tag</pre>

Removendo tag no repositório remoto:

<pre class="lang-bash">git push origin :refs/tags/versão-da-tag</pre>

## Concluindo

Se você quer continuar ou iniciar seus estudos com Git, indico o link do livro citado acima, é um ótimo começo, se tiver problemas com o inglês, encontrará várias versões em português. 

O Akita fez um [screencast para quem está começando com Git][2]. Vale a pena ver.

O pessoal da CodeSchool juntamente com o GitHub fizeram uma página exclusivamente para ensinar Git na prática. [Visite aqui][3].

Há também a [documentação do Git][4] que é bastante completa.

 [1]: http://tableless.com.br/introducao-das-premissas-dos-controles-de-versao/ "Introdução das premissas dos controles de versão"
 [2]: http://www.akitaonrails.com/2010/08/17/screencast-comecando-com-git
 [3]: https://try.github.io/levels/1/challenges/1
 [4]: http://www.git-scm.com/