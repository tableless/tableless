---
title: Iniciando no GIT – Parte 2
author: Diego Eis
type: post
date: 2012-11-22
excerpt: Commit, Push e Pull. Entenda o que fazer depois que modificar arquivos.
url: /iniciando-no-git-parte-2/
tweetbackscheck:
  - 1356393277
shorturls:
  - 'a:3:{s:9:"permalink";s:49:"http://tableless.com.br/iniciando-no-git-parte-2/";s:7:"tinyurl";s:26:"http://tinyurl.com/ceqpfkt";s:4:"isgd";s:19:"http://is.gd/sKmy4V";}'
twittercomments:
  - 'a:13:{i:274212844919222272;s:7:"retweet";i:274212778967961600;s:7:"retweet";i:274209157748502528;s:7:"retweet";i:272137459779907584;s:7:"retweet";i:272082829716893696;s:7:"retweet";i:271976153319890944;s:7:"retweet";i:271724965462691840;s:7:"retweet";i:271688569326800896;s:7:"retweet";i:271688195924705280;s:7:"retweet";i:278558260628451330;s:7:"retweet";i:281460997875695616;s:7:"retweet";i:281459505919823873;s:7:"retweet";i:280025936605347840;s:7:"retweet";}'
tweetcount:
  - 35
dsq_thread_id: 934706952
categories:
  - O Básico
  - Técnicas e Práticas
tags:
  - 2012
  - controle de versão
  - git
  - versionamento

---
Já leu a [primeira parte desse artigo][1]? 

[No primeiro artigo][1] aprendemos sobre como funciona o Git, como iniciar um projeto e como inserimos os arquivos que serão controlados pelo sistema. 

## Status

Antes de tudo você precisa entender em qual status os arquivos se encontram. Você pode modificar um arquivo, mas não commita-lo. Veja abaixo uma imagem direto do site do Git que mostra os diversos status dos arquivos.

Você já clonou ou iniciou seu projeto no Git e agora vai fazer modificações nos arquivos e enviar essas modificações para o repositório. Lembre-se que os arquivos em seu Work Directory podem estar **traked** ou **untracked**. Vou manter os termos em inglês para você se familiarizar melhor. Arquivos com status **tracked** são arquivos que já estão inseridos no repositório. Eles podem ser **unmodified** (que não foram modificados por você), **modified** (que foram modificados por você) ou **staged** (que são os arquivos que acabaram de ser mudados).

<img src="http://tableless.com.br/uploads/2012/11/18333fig0201-tn.png" alt="" title="18333fig0201-tn" width="500" height="317" class="alignnone size-full wp-image-7272" srcset="uploads/2012/11/18333fig0201-tn.png 500w, uploads/2012/11/18333fig0201-tn-300x190.png 300w" sizes="(max-width: 500px) 100vw, 500px" />

Esse ciclo é repetido diversas e diversas vezes. Veja abaixo um exemplo:

[<img src="http://tableless.com.br/uploads/2012/11/git2-1024x549.jpg" alt="" title="git2" width="640" height="343" class="alignnone size-large wp-image-7273" srcset="uploads/2012/11/git2-1024x549.jpg 1024w, uploads/2012/11/git2-300x161.jpg 300w, uploads/2012/11/git2.jpg 1131w" sizes="(max-width: 640px) 100vw, 640px" />][2]

## Commit

Suponha que você resolveu um bug no projeto. É hora de commitar suas modificações. Essas modificações serão inseridas no histórico do projeto e ficarão disponíveis para que os outros integrantes da equipe.

Ao commitar você escreve uma descrição sobre o que foi feito ali. Assim essa modificação não fica perdida e todo mundo sabe do que se trata aquela mudança. Você documenta essa mudança. É mais ou menos isso que é o commit.
  
Quando você commita uma modificação, os arquivos editados saem do status staged e voltam para o status unmodified. Claro, por que teoricamente aquela alteração já foi feita e agora os arquivos voltam com o status de sem modificações.

O comando é este:

<pre>git commit -m "Resolvendo bug da modal sobreposta na página de pagamentos."</pre>

Se você fizer um **git log** no projeto, você consegue visualizar uma lista de todos os commits enviados para o projeto, seus commits e commits de outros integrantes. Veja abaixo:

<img src="http://tableless.com.br/uploads/2012/11/Screen-Shot-2012-11-19-at-12.17.50-PM.png" alt="" title="Screen Shot 2012-11-19 at 12.17.50 PM" width="756" height="609" class="alignnone size-full wp-image-7274" srcset="uploads/2012/11/Screen-Shot-2012-11-19-at-12.17.50-PM.png 756w, uploads/2012/11/Screen-Shot-2012-11-19-at-12.17.50-PM-300x241.png 300w" sizes="(max-width: 756px) 100vw, 756px" />

## Pull

Não é só você que está fazendo modificações nos arquivos, mas também sua equipe. Por isso é importante que você deixe o projeto sempre atualizado. Para isso você precisa trazer as modificações que eles fizeram e commitaram para o seu repositório local. Você vai usar o comando **pull** para trazer essas modificações:

<pre>git pull</pre>

Feito isso vai até o servidor buscar todas as modificações a partir da versão do seu repositório local, ele vai baixar essas modificações e fará um merge automático nos arquivos necessários que foram modificados. Coisa linda&#8230; alguém deve ter modificado o mesmo arquivo que você, o Git vai entender isso e vai juntar seu código com o dele, automaticamente&#8230; Claro que pode ser que de conflitos caso vocês tenham modificado a mesma linha, mas aí é outra história, vemos mais pra frente como resolver isso. Se quiser se adiantar, procure sobre o comando **diff**.

## Push

Você modificou os arquivos, commitou descrevendo o que fez exatamente naquela modificação e agora precisa enviar tudo isso para o servidor. O comando **git push** empurra as suas modificações para o servidor, incluido-as no histórico do projeto. Quando os outros integrantes da equipe fizerem um **git pull**, essas modificações serão baixadas e incluídas no repositório local da pessoa.

<pre>git push</pre>

O Git Push só pode ser feito se você executou o **git pull** antes. Isso é uma forma de você ter o seu repositório atualizado e também para evitar possíveis conflitos no projeto. Quando você faz o pull, se der algum conflito de código, você deverá resolve-los para depois enviar o novo código novamente.

Há algumas outras opções tanto no Pull e no Push que podemos utilizar para especificar o branch para onde iremos empurrar ou buscar atualizações. Mas isso fica para outra hora.

A [documentação do Git][3] é muito fácil de ler e entender. É bem objetiva e não perde tempo blá blá blá&#8230; Recomendo que você leia e entenda melhor como utilizar o git nos seus projetos. Nada de FTP, SFTP e outras coisas&#8230; Isso é coisa do passado.

Veja um vídeo que mostra os comandos básicos do GIT:

 [1]: http://tableless.com.br/iniciando-no-git-parte-1/
 [2]: http://tableless.com.br/uploads/2012/11/git2.jpg
 [3]: http://git-scm.com/docs