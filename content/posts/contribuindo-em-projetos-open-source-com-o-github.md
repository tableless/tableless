---
title: Contribuindo em projetos open source com o github
author: William Martins
type: post
date: 2013-06-21
excerpt: Conheça os primeiros passos para contribuir para projetos pelo GitHub. Ideal para iniciantes!
url: /contribuindo-em-projetos-open-source-com-o-github/
dsq_thread_id: 1409976107
categories:
  - Mercado e Comportamento
  - O Básico
  - Técnicas e Práticas
  - Tecnologia e Tendências
tags:
  - 2013
  - como contribuir usando o github
  - comunidade
  - github
  - iniciantes
  - o basico
  - open source

---
Projetos open source são o que há de mais legal no mundo do desenvolvimento quando se quer aprender novas tecnologias e envolver-se em projetos, seja codificando, documentando, testando ou realizando qualquer tipo de atividade que envolve um projeto.

Uma das principais ferramentas para o envolvimento em projetos open source é o <a href="http://www.github.com" target="_blank">github</a>. Este artigo explica como utilizar essa ferramenta para envolver-se em projetos, visando realizar contribuições em projetos.

## Primeiros passos

Antes de tudo é necessário conhecer minimamente a ferramenta e o seu fluxo de trabalho, portanto, é recomendada a leitura de dois artigos:

<http://tableless.com.br/iniciando-no-git-parte-1/>

<http://tableless.com.br/iniciando-no-git-parte-2/>

## Let&#8217;s go

O primeiro passo é a criação de uma conta no site do github, assim, basta entrar em <https://github.com/> e preencher o formulário de cadastro.

[<img class="size-medium wp-image-37719 aligncenter" alt="Formulário de cadastro - github" src="http://tableless.com.br/uploads/2013/06/formulário-de-registro-github-552x310.png" width="552" height="310" srcset="uploads/2013/06/formulário-de-registro-github-552x310.png 552w, uploads/2013/06/formulário-de-registro-github-299x168.png 299w, uploads/2013/06/formulário-de-registro-github.png 677w" sizes="(max-width: 552px) 100vw, 552px" />][1]

O segundo passo consiste em baixar a aplicação ‘git’, esta será a responsável por toda a manipulação que realizaremos nos repositórios aos quais desejamos contribuir. Recomendo que seja lido primeiramente o artigo elaborado pelo Diego Eis, na seção ‘Instalando o git’, disponível em <http://tableless.com.br/iniciando-no-git-parte-1/>, ou então, se preferir, o próprio pessoal do github disponibiliza uma série de instruções para instalar e configurar o git, estas estão disponíveis em <https://help.github.com/articles/set-up-git>.

# Conceitos básicos

Para começar a trabalhar com o git de forma colaborativa é necessário conhecer dois conceitos básicos relacionados ao uso da ferramenta. Esses conceitos são o conceito de fork e de pull request.

## Fork

O fork consiste em realizar a cópia de um repositório de alguém, adicionando esse repositório aos nossos repositórios. Em linhas gerais, nos tornamos os ‘donos’ do repositório o qual estamos realizando o fork (mas o original se mantém intacto).

O fork é o primeiro passo para colaborar em um projeto. Por exemplo, percebemos que existe um problema em um arquivo nos exemplos para iniciantes disponíveis no tableless (<http://tableless.com.br/para-iniciantes/>) e queremos realizar a correção. Como o projeto está no github, podemos colaborar! Para isso, navegamos até o repositório (<https://github.com/tableless/iniciantes>) e clicamos na opção fork, localizada no canto direito da página.

<p style="text-align: center">
  <a href="http://tableless.com.br/uploads/2013/06/opções-do-repositório-github.png"><img class="size-full wp-image-37722 aligncenter" alt="Opções disponíveis no repositório" src="http://tableless.com.br/uploads/2013/06/opções-do-repositório-github.png" width="413" height="56" srcset="uploads/2013/06/opções-do-repositório-github.png 413w, uploads/2013/06/opções-do-repositório-github-329x44.png 329w" sizes="(max-width: 413px) 100vw, 413px" /></a>
</p>

Ao clicar em fork, o repositório em questão é copiado para a nossa base de repositórios e então viramos donos do repositório o qual copiamos, ficando este inclusive disponível na listagem dos nossos repositórios. Notem o símbolo &#8216;Y&#8217; indicando que o repositório foi criado a partir de um fork.

<p style="text-align: center">
  <a href="http://tableless.com.br/uploads/2013/06/lista-de-repositórios-atualizada.png"><img class="size-full wp-image-37720 aligncenter" alt="Lista de repositórios atualizada" src="http://tableless.com.br/uploads/2013/06/lista-de-repositórios-atualizada.png" width="251" height="32" /></a>
</p>

Agora podemos trabalhar no repositório criado normalmente, executar commits e pushs sem problemas, como se fosse um repositório novo que criamos do zero. Quando terminarmos de realizar as modificações e tivermos realizado os commits e push’s necessários podemos solicitar que o dono do repositório integre o que fizemos com o repositório original através de um pull request (explicado a seguir).

## Pull request

O pull request consiste em uma solicitação de integração das nossas modificações com o repositório que realizamos um fork.

Para realizar um pull request devemos ir até o repositório gerado pela operação de fork (na nossa base de repositórios). Lá, encontraremos um botão chamado ‘pull request’:

<p style="text-align: center">
  <a href="http://tableless.com.br/uploads/2013/06/opções-pull-request.png"><img class="size-full wp-image-37721 aligncenter" alt="Opção de pull request" src="http://tableless.com.br/uploads/2013/06/opções-pull-request.png" width="497" height="55" srcset="uploads/2013/06/opções-pull-request.png 497w, uploads/2013/06/opções-pull-request-329x36.png 329w" sizes="(max-width: 497px) 100vw, 497px" /></a>
</p>

Clicando em pull request, podemos escolher a origem e o destino do nosso pull request:

<p style="text-align: center">
  <a href="http://tableless.com.br/uploads/2013/06/realizando-pull-request.png"><img class="size-medium wp-image-37723 aligncenter" alt="Origem e destino do pull request" src="http://tableless.com.br/uploads/2013/06/realizando-pull-request-588x52.png" width="588" height="52" srcset="uploads/2013/06/realizando-pull-request-588x52.png 588w, uploads/2013/06/realizando-pull-request-329x29.png 329w, uploads/2013/06/realizando-pull-request-660x59.png 660w, uploads/2013/06/realizando-pull-request.png 913w" sizes="(max-width: 588px) 100vw, 588px" /></a>
</p>

Também podemos escrever um título e comentários sobre o nosso pull request:

<p style="text-align: center">
  <a href="http://tableless.com.br/uploads/2013/06/comentários-e-descrição-pull-request.png"><img class="size-medium wp-image-37718 aligncenter" alt="Comentários e descrição do pull request" src="http://tableless.com.br/uploads/2013/06/comentários-e-descrição-pull-request-520x310.png" width="520" height="310" srcset="uploads/2013/06/comentários-e-descrição-pull-request-520x310.png 520w, uploads/2013/06/comentários-e-descrição-pull-request-282x168.png 282w, uploads/2013/06/comentários-e-descrição-pull-request.png 685w" sizes="(max-width: 520px) 100vw, 520px" /></a>
</p>

Clicando em ‘Send pull request’, enviamos as nossas modificações para que as mesmas sejam validadas pela comunidade. Isso permite que seja feita uma avaliação sobre o que foi feito. Dessa forma, o dono do repositório poderá integrar as mudanças realizadas ao código do projeto.

# E agora, como posso contribuir?

Uma vez feitas as configurações necessárias e conhecendo os conceitos de fork e pull request, basta realizarmos as seguintes ações para contribuirmos para um projeto:

  1. Realiza-se um fork do projeto para o qual se quer contribuir.

  2. Clona-se o repositório criado através do fork para o nosso ambiente de trabalho (como explicado em <http://tableless.com.br/iniciando-no-git-parte-1/> na seção ‘Clonando um projeto’).

  3. Realizam-se as modificações /correções / novas implementações desejadas.

  4. Realiza-se o commit de nossas modificações.

  5. Faz-se o push para o nosso repositório (que criamos através de um fork no passo 1).

Nesse exato momento, nosso repositório criado no passo 1 estará a frente do repositório original (o qual fizemos um fork). Agora já estamos aptos a submeter nossas modificações usando o recurso de pull request.

Assim, basta irmos até o nosso repositório (que criamos fazendo um fork no passo 1) e clicarmos em ‘pull request’. Seleciona-se então o repositório e o branch de destino e o repositório e o branch de origem. Nesse momento, podemos escrever um título para o nosso pull request e também adicionar comentários sobre o que estamos fazendo. Finalizado o preenchimento dos campos, basta clicar em ‘send pull request’.

A partir de agora, é necessário esperar para ver se a comunidade e os donos do repositório aprovam a mudança realizada. Se a mesma for aprovada, o dono do repositório pode realizar um merge do que fizemos com o projeto em questão, unificando assim o código.

# Vamos por a mão na massa? 🙂

A melhor forma de aprender é praticar, dessa forma, criei um repositório chamado ‘learning-to-contribute’, o qual tem a intenção de receber os pull requests de quem quiser aprender a contribuir para projetos open-source antes de tentar fazer isso com projetos ‘reais’.

Para tal, é só entrar no link <https://github.com/wmartins/learning-to-contribute> e clicar em fork, a partir daí é só seguir os passos explicados nesse artigo e enviar um pull request para mim.

Sempre que possível vou aceitar os requests realizados para vocês verem o que foi explicado em ação!

Mandem seus requests!

 [1]: http://tableless.com.br/uploads/2013/06/formulário-de-registro-github.png