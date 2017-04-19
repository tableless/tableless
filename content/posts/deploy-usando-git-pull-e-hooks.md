---
title: Deploy usando git pull e hooks
author: Diego Eis
type: post
date: 2016-07-18
aliases: 
  - /?p=55107
  - /deploy-usando-git-pull-e-hooks/
titulo_personalizado:
  - 'Fazendo deploy usando <strong>git hooks</strong>'
categories:
  - Destaques

---
Se você tem qualquer projeto pessoal, você já deve ter tido a necessidade de como fazer, de forma fácil, a automatização do deploy. Para tentar automatizar os meus projetos, eu tentei usar vários serviços como CodeShip, DeployBot e etc… Esses caras são bem legais, por que te dão uma série de integrações, históricos etc. Mas as vezes você nem precisa de tanto, você só quer dar um push no projeto local pro seu repositório remoto e esse repositório atualizar seu projeto em produção. E nada mais simples do que o **git hooks** pra fazer isso.

Vou mostrar mais ou menos como é o meu processo para atualizar meu [blog pessoal][1]. A ideia é que você crie um repositório utilizando a flag `--bare`. E aqui vale uma pequena explicação: geralmente, quando você cria um repositório git, você faz um `git init` na sua máquina. O git cria uma pasta `.git` dentro da sua pasta local, contendo todas as referências de mudanças e etc. Mas ainda esse código não está compartilhado com ninguém. Para você compartilhar, você precisa subir para um repositório, em algum lugar, por exemplo no GitHub. Quando você cria um repositório remoto lá no GitHub, você referencia seu projeto local com o repositório remoto assim:

<pre class="lang-shell">git remote add origin git@github.com:diegoeis/diegoeis.com.git
</pre>

Esse repositório remoto não é um repositório de trabalho, ele é um repositório que contém apenas as referências de mudanças do seu código e nada mais. Isso quer dizer que ele não tem os arquivos do seu projeto. Esse é um repositório apenas para compartilhamento, nada mais. É com esse link que todos os outros membros do seu time irão adicionar o projeto em suas máquinas.

Nós vamos criar esse tipo de repositório na nossa máquina em produção, por que assim conseguimos configurar um hook para detectar quando submetermos uma alteração no nosso projeto. Para tanto, você precisa rodar o comando `git init --bare` no seu servidor. Isso vai gerar um repositório nu, contendo apenas as referências e não os arquivos de trabalho. No meu server fiz assim:

<pre class="lang-shell">mkdir public/diegoeis.com.git
cd public/diegoeis.com.git
git init --bare
</pre>

Pronto, isso foi o suficiente para criar um repositório bare vazio. Ele vai ser o nosso `origin` no nosso repositório local. Para tanto, fazemos assim na máquina local, dentro do seu projeto:

<pre class="lang-shell">cd diegoeis.com
git remote add origin meu_usuario_do_servidor@meu_dominio.com:/public/diegoeis.com.git
</pre>

Pronto, agora eu adicionei um repositório remoto ao meu projeto. Se você entender bem, você faz a mesma coisa quando vai clonar um projeto usando GitHub ou qualquer outro sistema de gerenciamento de Git como GitLab, Bitbucket etc. Só que eles criam o repositório bare para você.

Feito isso, vamos voltar para o seu servidor, lá você vai clonar o seu projeto. Isso vai criar uma pasta normal, que você já conhece.

<pre class="lang-shell">git clone public/diegoeis.com.git /var/www/diegoeis.com
</pre>

### Git Hooks

Com esse &#8220;setup&#8221; feito, agora eu posso ir para o que importa, que é configurar meu hook. Lá no seu servidor, dentro do repositório bare que foi criado, encontre a pasta `hooks`, e dentro dela tem um arquivo chamado `post-receive`. Esse cara é o hook que vai detectar algo depois do recebimento de uma mudança. Você vai colocar esse código:

<pre class="lang-shell">#!/bin/bash
cd /public/diegoeis.com
env -i git reset —hard
env -i git pull origin master
exit
</pre>

Bom, são comandos bash, simples: entra na pasta do meu site, reseta o repositório e faz um pull com as últimas alterações. Esse `env -i` é um truque que faz os comandos serem executados na pasta que você entrou ali no seu comando bash. Se não houver esse `env -i`, todos os comandos git que você rodar, vão tentar rodar na pasta fora do seu repositório. Colocando essa flag, isso não vai acontecer. O Felix Geisendörfer [sofreu com isso e falou como funciona aqui nesse artigo][2].

Por último, você precisa tornar o **post-receive** um arquivo executável rodando:

<pre class="lang-shell">chmod +x /public/diegoeis.com.git/hooks/post-receive
</pre>

Agora, toda vez que você fizer um git push para o seu repositório remoto, ele vai atualizar e mostrar algo mais ou menos assim:

<pre class="lang-shell">Counting objects: 19, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (19/19), done.
Writing objects: 100% (19/19), 1.99 KiB | 0 bytes/s, done.
Total 19 (delta 14), reused 0 (delta 0)
remote: HEAD is now at 9c1acad build
remote: From /public/diegoeis.com
remote:  * branch            master     -> FETCH_HEAD
remote:    9c1adac..c1bc7ed  master     -> origin/master
remote: Updating 9c1adac..c1bc7ed
remote: Fast-forward
remote:  build/assets/css/style.css                       |  2 +-
remote:  build/feed.xml                                   | 12 ++++++———
remote:  build/index.html                                 |  2 +-
remote:  source/articles/organizando-a-informacao.html.md | 12 ++++++———
remote:  6 files changed, 21 insertions(+), 19 deletions(-)
To user@diegoeis.com:/public/diegoeis.com.git/
   9c1acad..c5bb7ed  master -> master
</pre>

E quase que instantaneamente seu repositório em prod vai estar atualizado.

O [Akita fez uma artigo em 2010][3] (!) falando sobre o mesmo assunto e existem uma série de [outros artigos][4] pela internet explicando a mesma coisa, é só procurar. E porque eu quis fazer um artigo igual? Só por que eu nunca tinha feito algo assim. ;-D

 [1]: http://diegoeis.com
 [2]: http://debuggable.com/posts/git-tip-auto-update-working-tree-via-post-receive-hook:49551efe-6414-4e86-aec6-544f4834cda3
 [3]: http://www.akitaonrails.com/2010/02/13/deploy-com-git-push
 [4]: https://githowto.com/bare_repositories