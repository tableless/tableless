---
title: Tudo que você queria saber sobre Git e GitHub, mas tinha vergonha de perguntar
author: Daniel Schmitz
type: post
date: 2015-10-07
excerpt: 'Crie, compartilhe, acompanhe e versione projetos com o poder do git,  tudo na nuvem pelo github.'
url: /tudo-que-voce-queria-saber-sobre-git-e-github-mas-tinha-vergonha-de-perguntar/
categories:
  - Git
  - O Básico
  - Tooling
tags:
  - git
  - github

---
Este artigo traz a você tudo que precisa saber para se tornar um desenvolvedor que possa dominar tanto o git, quanto o Github. Nosso objetivo é trazer os conhecimentos necessários para que você possa, a partir do zero, dominar os conceitos gerais do git, e usar o github para &#8220;hospedar&#8221; seus projetos pessoais e acompanhar outros projetos de seu interesse.

## O que é git?

Git é um sistema de controle de versão de arquivos. Através deles podemos&nbsp;desenvolver projetos&nbsp;na qual diversas pessoas podem contribuir simultaneamente no mesmo, editando e criando novos arquivos e permitindo que os mesmos possam existir sem o risco de suas alterações serem sobrescritas.

Se não houver um sistema de versão, imagine o caos entre duas pessoas abrindo o mesmo arquivo ao mesmo tempo. Uma das aplicações do git é justamente essa, permitir que um arquivo possa ser editado ao mesmo tempo por pessoas diferentes. Por mais complexo que isso seja, ele tenta manter tudo em ordem para evitar problemas para nós desenvolvedores.

Outro fator importante do git (e essa é um dos seus diferenciais em relação ao svn &#8211; caso vc o conheça) é a possibilidade de criar, a qualquer momento, vários `snapshots` do seu projeto, ou como chamamos mais &#8220;nerdmenete&#8221;, branch. Suponha que o seu projeto seja um site html, e você deseja criar uma nova seção no seu código HTML, mas naquele momento você não deseja que estas alterações estejam disponíveis para mais ninguém, só para você. Isso é, você quer alterar o projeto (incluindo vários arquivos nele), mas ainda não quer que isso seja tratado como &#8220;oficial&#8221; para outras pessoas, então vc cria um branch (como se fosse uma cópia espelho) e então trabalha apenas nesse branch, até acertar todos os detalhes dele. Após isso, você pode fazer um merge de volta do seu branch até o projeto original. Veja bem, se tudo isso que você leu só ajudou a te confundir mais &#8211; respire fundo &#8211; e siga em frente. Com exemplos tudo fica melhor.

## O que é github?

O <a href="https://github.com/" target="_blank">Github</a> é um serviço web que oferece diversas funcionalidades extras aplicadas ao git. Resumindo, você poderá usar gratuitamente o github para hospedar seus projetos pessoais. Além disso, quase todos os projetos/frameworks/bibliotecas sobre desenvolvimento open source estão no github, e você pode acompanhá-los através de novas versões, contribuir informando bugs ou até mesmo enviando código e correções. Se você é desenvolvedor e ainda não tem github, você está atrasado e essa é a hora de correr atrás do prejuízo.

## Instalando git

O git é um programa que pode ser instalado <a href="http://git-scm.com/download/win" target="_blank">neste link</a> para Windows, <a href="http://git-scm.com/download/mac" target="_blank">neste</a> para Mac, ou então através do comando `sudo apt-get install git` para plataformas Linux/Debian, como o Ubuntu. Se você usa uma VM na nuvem, como o <a href="http://c9.io" target="_blank">cloud9</a> ou <a href="https://koding.com/" target="_blank">koding</a>, o git já estará disponível em sua linha de comando.

> Nossa metodologia é fazer com que você aprenda git já utilizando o github, então vamos a sua configuração!

## Criando a conta no GitHub

O github não possui instalação, ele é um serviço, e caso você não tenha uma conta, chegou a hora de criá-la, <a href="https://github.com/" target="_blank">neste link</a>. Após criar a conta, você verá um botão verde `+New Repository` na qual poderá criar um repositório de acordo com a tela a seguir.

<img src="http://tableless.com.br/uploads/2015/09/github.png" alt="github" width="750" height="477" class="alignleft size-full wp-image-51160" />

Nesta imagem estamos criando um repositório cujo nome é `site`, de domínio público (podem ser criados reps privados pagando uma mensalidade), e com o arquivo `README.md` embutido, que contém uma descrição do seu projeto. Para que possamos começar a entender como o git funciona, é fundamental criar um rep como este para os nossos testes.

Após a criação do repositório, ele estará disponível no endereço `https://github.com/<username>/site`, onde `username`é o login que você usou para se cadastrar. Acessando esta url temos a seguinte resposta:

<img src="http://tableless.com.br/uploads/2015/09/github_site.png" alt="github_site" width="1051" height="780" class="alignleft size-full wp-image-51163" />

Temos muitas informações nesta tela, pois ela é a tela principal do seu projeto. Explicaremos algumas informações ao longo deste artigo, por enquanto repare apenas no botão `HTTPs Clone Url` na parte inferior à direta. Esta URl será necessária para que possamos &#8220;clonar&#8221; este projeto em nosso ambiente de estudo (sua máquina windows, mac, linux ou a vm). Clique no botão de copiar URL e perceba que a seguinte URL está na área de transferência: `https://github.com/<username>/site.git`

## Configurando o git

Existem 2 pequenos passos para configurar o seu GIT para ter um acesso mais simplificado ao github. Aqui estaremos estabelecendo que, sempre que necessitar, você irá fornecer o seu login e senha ao GitHub. Existem meios para salvar a senha em local seguro, mas vamos pular esta etapa. Para abrir um terminal GIT no Windows, basta criar uma pasta no seu sistema e, nela, clicar com o botão direito do mouse e escolher `Git Bash Here`. Em sistemas mac/linux você já está acostumado a usar o terminal/console, o git estará lá disponível. Neste artigo estaremos utilizando a máquina virtual cloud9, que você pode aprender a usá-la neste <a href="http://tableless.com.br/programando-na-nuvem-com-o-cloud9/" target="_blank">artigo</a>.

Então, com o seu terminal git aberto, vamos digitar:

<pre>$ git config --global user.name "YOUR NAME"
$ git config --global user.email "YOUR EMAIL ADDRESS"
</pre>

Estas configurações ficam alocadas no arquivo `~/.gitconfig`, onde o ~ é o seu diretório home. No Windows, ele fica em `c:\Usuarios\<username>\.gitconfig`. Veja a figura a seguir com a minha configuração no cloud9.

<img src="http://tableless.com.br/uploads/2015/09/git_config.png" alt="git_config" width="300" height="146" class="alignleft size-medium wp-image-51167" />

## Vamos clonar!

Então o que temos até agora é o git configurado para utilizar o github e o projeto no github criado. Precisamos trazer este projeto para o nosso git, e este processo se chama `clonar`. Então, quando você quiser começar um projeto utilizando git, você cria ele no github e clona na sua máquina. O comando para clonar o projeto é `git clone "url"`, veja:

<pre>git clone https://github.com/&lt;username&gt;/site.git
</pre>

<img src="http://tableless.com.br/uploads/2015/09/git_clone.png" alt="git_clone" width="720" height="223" class="alignleft size-full wp-image-51172" />

Perceba que, ao fazer o git clone, o projeto é baixado para a sua máquina, e uma pasta com o nome do projeto é criada.

> Quer dizer que qualquer pessoa pode baixar o meu projeto? Sim, isso é natural, já que o seu repositório está público. Qualquer um pode clonar ele para si, mas eles não podem alterar os seus arquivos, isso não vai acontecer, exceto que você permita.

## Comandos iniciais do git

Com o repositório na sua máquina, vamos aprender 4 comandos iniciais que farão parte da sua vida a partir de agora:

  * `git add <arquivos...>` Este comando adiciona o(s) arquivo(s) em um lugar que chamamos de INDEX, que funciona como uma área do git no qual os arquivos possam ser enviados ao Github. É importante saber que ADD não está adicionando um arquivo novo ao repositório, mas sim dizendo que o arquivo (sendo novo ou não) está sendo preparado para entrar na próxima revisão do repositório.
  * `git commit -m "comentário qualquer"` Este comando realiza o que chamamos de &#8220;commit&#8221;, que significa pegar todos os arquivos que estão naquele lugar INDEX que o comando `add` adicionou e criar uma revisão com um número e um comentário, que será vista por todos. 
  * `git push` Push (empurrar) é usado para publicar todos os seus commits para o github. Neste momento, será pedido a sua senha.
  * `git status` Exibe o status do seu repositório atual </ul> 
    ## Vamos praticar!
    
    Chegou o momento de praticar um pouco o que vimos até agora, e com bastante calma para que você possa entender cada passo. Após clonar o seu projeto, crie o arquivo `index.html` na pasta site que é o seu repositório git. Após criar o arquivo, execute o comando `git status`. A resposta é semelhante a figura a seguir:
    
    <img src="http://tableless.com.br/uploads/2015/09/git_touch_index.png" alt="git_touch_index" width="628" height="284" class="alignleft size-full wp-image-51179" />
    
    Ou seja, o comando `git status` nos trouxe várias informações, que iremos ignorar a princípio, exceto pelo `Untracked files`, dizendo que existe um arquivo que não está sendo &#8220;mapeado&#8221; pelo git. Para preparar este arquivo para o seu versionamento, usamos o comando `git add`, veja:
    
    <img src="http://tableless.com.br/uploads/2015/09/git_add.png" alt="git_add" width="600" height="272" class="alignleft size-full wp-image-51180" />
    
    Agora temos o nosso arquivo index.html no INDEX do repositório, ou se você quiser pensar: &#8220;preparado para um commit&#8221;. Para commitar este arquivo, usamos:
    
    <img src="http://tableless.com.br/uploads/2015/09/git_commit.png" alt="git_commit" width="760" height="248" class="alignleft size-full wp-image-51182" />
    
    Após &#8220;commitar&#8221; o arquivo, ele já está presente no nosso repositório local, tanto que realizamos o comando `git status` novamente e ele retornou que não havia nada de novo no projeto. Perceba agora que, mesmo recarregando o projeto no github, nada muda. Ou seja, estas mudanças até agora foram locais, você pode realizar várias operações antes de publicá-las no github. Para publicar, usamos o comando `git push`:
    
    <img src="http://tableless.com.br/uploads/2015/09/git_push.png" alt="git_push" width="600" height="255" class="alignleft size-full wp-image-51184" />
    
    Após realizar o git push podemos ver no site github as mudanças realizadas no projeto:
    
    <img src="http://tableless.com.br/uploads/2015/09/github_site2.png" alt="github_site2" width="812" height="552" class="alignleft size-full wp-image-51185" />
    
    Desta forma, aprendemos os 4 comandos mais básicos do git, e com ele podemos começar a compreender como funciona o processo de versionamento de arquivos com git e github.
    
    ### Errei a mensagem do commit, como arrumo?
    
    Imagine que você tenha errado a mensagem que escreveu no commit ou simplesmente queira melhorar a descrição do seu trabalho. Você já comitou a mensagem mas ainda não fez o push das suas modificações para o servidor. Nesse caso você usa a flag `--amend`. Fica assim:
    
    <pre class="lang-shell">$ git commit --amend</pre>
    
    O `git commit --amend` modifica a mensagem do commit mais recente, ou seja, o último commit feito por você no projeto. Além de você mudar a mensagem do commit, você consegue adicionar arquivos que você se esqueceu ou retirar arquivos comitados por engano. O git cria um commit totalmente novo e corrigido.
    
    ## Cadê o git pull?
    
    Ainda existe um comando importante neste processo, que é o `git pull`. Ele é usado para trazer todas as modificações que estão no github para o seu projeto local. Isso é vital quando existem projetos mantidos por mais de uma pessoa, ou se você possui duas máquinas e precisa manter a sincronia entre elas. Supondo que você possui uma máquina no trabalho e outra em casa. Ambas tem o repositório local ligado ao github. Quando você executar um `git push` em uma das máquinas, terá que realizar um `git pull` na outra.
    
    Para exemplificar, vamos alterar o arquivo README.md diretamente no github. Isso é possível clicando no arquivo e depois clicando no ícone para edição, conforme a imagem a seguir.
    
    <img src="http://tableless.com.br/uploads/2015/09/github_edit.png" alt="github_edit" width="935" height="356" class="alignleft size-full wp-image-51241" />
    
    Após clicar em edit, adicione algum texto, forneça uma mensagem de commit e clique no botão &#8220;Commit Changes&#8221;. Com isso, uma nova revisão no seu projeto é criada, mas como ela foi gerada no github, o seu projeto local está desatualizado. Para atualizar o seu projeto, use `git pull`, e perceba que o arquivo README.md é atualizado de acordo com a sua última revisão, semelhante a figura a seguir.
    
    <img src="http://tableless.com.br/uploads/2015/09/git-pull.png" alt="git-pull" width="520" height="285" class="alignleft size-full wp-image-51242" />
    
    ## Melhorando o conceito do comando git add
    
    Possivelmente você imaginou que o comando `git add` é usado para novos arquivos, mas isso não é verdade. O comando `add` é usado para adicionar qualquer alteração de arquivo ao INDEX do git, que é uma área especial onde os arquivos estão sendo preparados para o commit. Quando usamos `add`, estamos dizendo que o arquivo estará adicionando ao próximo commit, quando este for realizado. Isso é necessário porque nem sempre queremos que todos os arquivos que alteramos sejam comitados.
    
    Vamos a um exemplo simples, adicionando o seguinte código no arquivo index.html:
    
    <pre class="lang-html">&lt;!DOCTYPE html&gt;
&lt;html&gt;
&lt;head&gt;
&lt;meta charset="UTF-8"&gt;
    &lt;title&gt; Meu Site &lt;/title&gt;
&lt;/head&gt;
&lt;body&gt;
&lt;/body&gt;
&lt;/html&gt;
</pre>
    
    Após salvar este modelo html, o comando git status irá apresentar:
    
    <pre>modified:   index.html
</pre>
    
    Para adicionar o arquivo e prepará-lo para o commit, usamos `git add index.html`. Desta forma, ele está pronto para usarmos o comando `git commit`, o que não faremos agora. Antes disso, altere novamente o arquivo e adicione algum texto entre as tags body, por exemplo:
    
    <pre class="lang-html">&lt;!DOCTYPE html&gt;
&lt;html&gt;
&lt;head&gt;
&lt;meta charset="UTF-8"&gt;
    &lt;title&gt; Meu Site &lt;/title&gt;
&lt;/head&gt;
&lt;body&gt;
 Esse é meu site
&lt;/body&gt;
&lt;/html&gt;
</pre>
    
    Após alterar o arquivo, temos a seguinte situação:
    
      1. Adicionamos o conteúdo html no arquivo index.html
      2. Realizamos `git add index.html`
      3. Alteramos index.html e adicionamos o texto entre as tags body
    
    Neste momento, faça: `git commit -m "Alteração no arquivo index.html"`, e após isso, faça: `git push`. Analise agora no github se a sua alteração na tag body está visível. Ela não estará. Mas porque isso aconteceu? Quando usamos o comando `git add`, aquela alteração no body ainda não tinha sido escrita, então ela não estará pronta até que você faça novamente o comando `git add`. Em termos técnicos, a segunda alteração que fez ainda não está na INDEX do repositório. Como tarefa, faça novamente `git add index.html`, `git commit` e `git push`
    
    ## Trabalhando com branches
    
    Branches e mergers sempre foram os pesadelos de qualquer gerenciador de versão (ok, do svn&#8230;). No git, o conceito de branch tornou-se algo muito simples e fácil de usar. Mas quando que temos que criar um branch? Imagine que o seu site está pronto, tudo funcionando perfeitamente, mas surge a necessidade de alterar algumas partes dele como forma de melhorá-lo. Além disso, você precisa manter estas alterações tanto no computador de casa quanto do trabalho. Com isso temos um problema, se você começa a alterar os arquivos em casa, para na metade da implementação, e precisa terminar no trabalho, como você iria comitar tudo pela metade e deixar o site incompleto?
    
    Para isso existe o conceito de branch, que é justamente ramificar o seu projeto em 2, como se cada um deles fosse um repositório, e depois juntá-lo novamente. Voltando ao github, perceba o detalhe da imagem a seguir.
    
    <img src="http://tableless.com.br/uploads/2015/09/master.png" alt="master" width="821" height="344" class="alignleft size-full wp-image-51249" />
    
    Sem saber, você já está em um branch, que chamamos de master. Perceba também que, sempre que usávamos `git status`, o nome do branch é exibido, e sempre que comitávamos ou fazíamos o push, o mesmo aparecia. Ou seja, até este momento fizemos todas as alterações no master. Você pode criar um branch no github ou em linha de comando. Inicialmente, vamos pelo github, criando o branch &#8220;new_menu&#8221;.
    
    <img src="http://tableless.com.br/uploads/2015/09/new_branch.png" alt="new_branch" width="468" height="328" class="alignleft size-full wp-image-51250" />
    
    Criamos o branch new_menu, e para que possamos trabalhar nele, usamos o comando `git checkout new_menu`. No primeiro momento que você cria este branch no github, é necessário realizar o comando `git pull` no seu projeto para que ele possa saber que este branch foi criado. Após realizar `git pull`, pode-se alterar para o novo branch, conforme a imagem a seguir.
    
    <img src="http://tableless.com.br/uploads/2015/09/new_menu.png" alt="new_menu" width="604" height="299" class="alignleft size-full wp-image-51252" />
    
    Neste momento, estamos no branch `new_menu`, e tudo que fizermos agora será pertencente a ele. Caso haja necessidade de voltar ao branch master, basta realizar o comando `git checkout master`.
    
    > Atenção, o comando `checkout` do git não é o mesmo do checkout do svn, caso você o conheça. Ambos tem sentidos totalmente diferentes. 
    
    Então, entando no branch new_menu, vamos adicionar um simples menu na página:
    
    <pre class="lang-html">&lt;!DOCTYPE html&gt;
&lt;html&gt;
&lt;head&gt;
&lt;meta charset="UTF-8"&gt;
    &lt;title&gt; Meu Site &lt;/title&gt;
&lt;/head&gt;

&lt;body&gt;
    Meu Site
    
    &lt;ul&gt;
        &lt;li&gt;&lt;a href="index.html"&gt;Home&lt;/a&gt;&lt;/li&gt;
        &lt;li&gt;&lt;a href="sobre.html"&gt;Sobre&lt;/a&gt;&lt;/li&gt;
        &lt;li&gt;&lt;a href="contato.html"&gt;Contato&lt;/a&gt;&lt;/li&gt;
    &lt;/ul&gt;
    
&lt;/body&gt;
&lt;/html&gt;
</pre>
    
    Após criar o menu, certifique-se de estar no branch new_menu e faça o commit, conforme a figura a seguir.
    
    <img src="http://tableless.com.br/uploads/2015/09/new_menu_commit.png" alt="new_menu_commit" width="716" height="536" class="alignleft size-full wp-image-51254" />
    
    Agora temos algumas modificações no branch new\_menu, e podemos trabalhar nesse branch por quanto tempo for necessário, já que o master está intacto. Aqui temos uma funcionalidade interessante, que se destaca em relação as outras ferramentas de versionamento. Suponha que, no meio do seu desenvolvimento do menu, surge a necessidade de resolver um bug crítico no master, algo como &#8220;está faltando o h1 no título do seu site&#8221;&#8230;. Ou seja, estamos no branch new\_menu e precisamos alterar o master. Para isso, use o comando `git checkout master`. Ao fazer isso, retornamos ao master e aquele menu que criamos não está mais presente, conforme a figura a seguir.
    
    <img src="http://tableless.com.br/uploads/2015/09/back_to_master.png" alt="back_to_master" width="624" height="686" class="alignleft size-full wp-image-51255" />
    
    É claro que não perdemos o menu, ele está apenas no branch new_menu. Quando retornarmos a ele, voltará. Agora altere o título do site, incluindo o h1, veja:
    
    <pre class="lang-html">&lt;!DOCTYPE html&gt;
&lt;html&gt;
&lt;head&gt;
&lt;meta charset="UTF-8"&gt;
    &lt;title&gt; Meu Site &lt;/title&gt;
&lt;/head&gt;

&lt;body&gt;
    &lt;h1&gt;Meu Site&lt;/h1&gt;
&lt;/body&gt;

&lt;/html&gt;</pre>
    
    Após alterar, faça commit e o push! Veja:
    
    <img src="http://tableless.com.br/uploads/2015/09/git_push2.png" alt="git_push2" width="687" height="529" class="alignleft size-full wp-image-51256" />
    
    Agora que resolvemos o problema do título, podemos voltar ao new_menu: `git checkout new_menu`. Após realizar este comando, temos o menu de volta no arquivo index.html, mas veja que o título não possui a tag H1. Isso acontece que estamos em outro branch. Tudo que acontece no master, fica no master. Tudo que acontece no new\_menu, fica no new\_menu
    
    ## Merge com conflitos
    
    Se desejar trazer o título do master para o new_menu, devemos fazer uma operação chamada `merge`, que irá juntar um código no outro. Então, estando no branch new_menu, e querendo trazer uma alteração do master para este branch, precisamos realizar o seguinte comando: `git merge master`. Caso existam alterações nas mesmas linhas entre mesmos arquivos, um conflito será gerado, como no exemplo a seguir:
    
    <img src="http://tableless.com.br/uploads/2015/09/conflict.png" alt="conflict" width="595" height="616" class="alignleft size-full wp-image-51259" />
    
    Este é um exemplo de conflito que podo ocorrer quando realizamos um merge, indicado em `1`. Perceba que o código html possui uma definição entre dois blocos, o primeiro, em `2` mostra como é o código do branch new_menu, e o segundo bloco, em `3`, mostra como é o código no branch master. Edite o arquivo repassando para a seguinte forma:
    
    <img src="http://tableless.com.br/uploads/2015/09/merge2.png" alt="merge2" width="578" height="613" class="alignleft size-full wp-image-51260" />
    
    Ou seja, ajustamos os dois blocos, como se fosse um merge manual. Após resolver o conflito, vamos prepará-lo para o commit no branch new_menu, com o comando `git add`. Veja:
    
    <img src="http://tableless.com.br/uploads/2015/09/merge3.png" alt="merge3" width="779" height="105" class="alignleft size-full wp-image-51261" />
    
    Ou seja, resolvemos o conflito &#8220;na mão&#8221; e depois comitamos normalmente.
    
    ## Merge sem conflitos
    
    Quando não alteremos a mesma linha de um arquivo em branches diferentes, conseguimos realizar um merge sem ocasionar conflitos. Isso pode ser notado ao trazermos o menu do branch new_menu para o master, da seguinte forma:
    
    <img src="http://tableless.com.br/uploads/2015/09/merge4.png" alt="merge4" width="585" height="652" class="alignleft size-full wp-image-51262" />
    
    Se não houver conflitos, basta realizar um commit normal para confirmar o merge.
    
    ## Vendo branches e merges
    
    O github possui uma ferramenta gráfica para exibir os branches e merges do seu projeto. Clique no ícone em forma de gráfico no menu à direita do site e clique na aba Network, para se ter um resultado semelhante a figura a seguir:
    
    <img src="http://tableless.com.br/uploads/2015/09/graph.png" alt="graph" width="1027" height="446" class="alignleft size-full wp-image-51265" />
    
    ## Lendo mais
    
    Você pode ler mais sobre git e entender mais sobre controles de versão, nesses artigos do Tableless:
    
      * <a href="http://tableless.com.br/alguns-comandos-git/" target="_blank">Comandos Iniciais do Git</a> 
      * <a href="http://tableless.com.br/slides-devs-10-git/" target="_blank">Apresentações sobre GIT</a> 
      * <a href="http://tableless.com.br/iniciando-no-git-parte-1/" target="_blank">Iniciando com GIT &#8211; Parte 1</a> 
      * <a href="http://tableless.com.br/iniciando-no-git-parte-2/" target="_blank">Iniciando com GIT &#8211; Parte 2</a> 
      * <a href="http://tableless.com.br/git-com-interface-grafica/" target="_blank">Git com Interface Gráfica</a>