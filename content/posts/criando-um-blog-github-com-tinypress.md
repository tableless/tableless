---
title: Criando um “blog” no Github com tinypress.
author: Victor "reidark" Matias
type: post
date: 2014-04-25
excerpt: Uma ferramenta minimalista para criar um blog estático no Github. Simples, rápido e sem gastar nada.
url: /criando-um-blog-github-com-tinypress/
dsq_thread_id: 2634428903
categories:
  - Artigos
  - Notícias
tags:
  - blog estático
  - github
  - github blog
  - github jekyll
  - github pages
  - tinypress

---
Amigos, amigos, amigos, a internet é imprevisível. Há um tempo atrás eu trouxe pra vocês o novo CMS chamado [Ghost][1]. E eu, navegando por ai, vagarosamente, me esbarro (novamente) nessa ferramenta excepcional chamada [Tinypress][2], que é praticamente um novo &#8220;gerenciador&#8221; de [blog][3] com integração ao Github.

## Eu não entendo nada de Github, e agora?

Calma, muita calma. Não precisa ficar desesperado, nesse básico tutorial você vai ver que não precisa entender muito de github para ter seu próprio blog hospedado lá. O tinypress faz praticamente tudo automático, e você só vai mexer nos códigos caso você queira, e, se quiser, acompanhe porque vou mostrar nesse artigo como pode ser feito.

## O que é o Tinypress?

[<img src="http://tableless.com.br/uploads/2014/04/Captura-de-Tela-2014-04-23-às-20.51.26.png" alt="Tinypress Github Blog" width="682" height="258" class="aligncenter size-full wp-image-42246" srcset="uploads/2014/04/Captura-de-Tela-2014-04-23-às-20.51.26.png 682w, uploads/2014/04/Captura-de-Tela-2014-04-23-às-20.51.26-400x151.png 400w" sizes="(max-width: 682px) 100vw, 682px" />][4]

Antes de tudo eu já aviso: Ele cria um blog estático. Ok, pra alguns isso não seria novidade nenhuma, mas para quem não sabe o que é: Blog estático é basicamente páginas HTML ou Markdown (nesse caso) serem geradas em forma de post. Sim, não existe conexão com um banco de dados para puxar informações, é tudo estático, tá tudo ali, tudo escrito em documento já pronto. O que o tinypress faz é puxar essas páginas e exibir elas em forma de post. Mais ou menos como funciona o Middleman ou o Jekyll, para quem já se aventurou por estas bandas.

O tinypress funciona basicamente assim:

  1. Você entra no site e libera o acesso no github para a aplicação do tinypress.
  2. Escolha entre os templates já prontos.
  3. Escolher o nome do blog e a quantidade de posts por página.
  4. Se você não tiver um repositório de página pessoal ainda (seunome.github.io) ele automaticamente cria uma (repositório público).
  5. Pronto, você já está hábil para começar a fazer publicações.

## Interface e como postar

[<img src="http://tableless.com.br/uploads/2014/04/Captura-de-Tela-2014-04-23-às-21.12.44.png" alt="Tinypress Interface" width="728" height="254" class="aligncenter size-full wp-image-42248" srcset="uploads/2014/04/Captura-de-Tela-2014-04-23-às-21.12.44.png 728w, uploads/2014/04/Captura-de-Tela-2014-04-23-às-21.12.44-400x139.png 400w" sizes="(max-width: 728px) 100vw, 728px" />][5]

A interface é básica, porém, é tudo que você precisa para escrever um texto, artigo ou qualquer coisa para um blog. Sim, quando eu digo básico, é **bem** básico mesmo, hehe. Mas existem coisas bacanas na publicação do post, tem como escolher as tags, categorias, url amigável entre outros. A é, também tem como você escolher o post como publicado ou apenas draft (rascunho).

[<img src="http://tableless.com.br/uploads/2014/04/Captura-de-Tela-2014-04-23-às-21.21.01.png" alt="Tinypress advanced options" width="665" height="284" class="aligncenter size-full wp-image-42249" srcset="uploads/2014/04/Captura-de-Tela-2014-04-23-às-21.21.01.png 665w, uploads/2014/04/Captura-de-Tela-2014-04-23-às-21.21.01-400x170.png 400w" sizes="(max-width: 665px) 100vw, 665px" />][6] 

Assim como as páginas no github, o Tinypress usa a linguagem Markdown para os posts. Caso você não saiba &#8220;escrever&#8221; em .markdown (.md) olhe sua syntax básica [aqui][7]. Relaxa, não é nada difícil, dá pra aprender rapidinho, até porquê você não vai usar nada avançado, por isso foque mais em aprender o uso de links, títulos, imagens e afins. Recomendo fortemente aprender essa linguagem não apenas para o blog, mas para te beneficiar ao escrever para alguns repositórios do github em outros projetos, visto que a linguagem usada é o markdown.

tinypress tem resquicios de que foi criada com Jekyll, um &#8220;gerador&#8221; estático de &#8220;blogs&#8221;, você não precisa saber Jekyll para manusear os posts e coisas do tipo, mas caso queira mudar alguma coisa no código principal, aqui fica a dica do [Jekyll][8].

## E o repositório, como fica?

Assim como eu expliquei no começo desse artigo, usarei algumas explicações básicas no meio do texto para os menos familiarizados conhecerem melhor o github.

Pra quem ainda não se aventurou no universo do github, **repositório** (público) é como se fosse uma pasta sua, com arquivos do formato que desejar para outras pessoas verem (ou não) suas aplicações, códigos e outras coisas, e assim formar um grande universo _open source_. Não preciso nem falar que é online né, haha.

O tinypress cria seu repositório de blog(seunome.github.io), ou seja, sua página no github. Dentro dele ele coloca os arquivos necessários para o blog rodar. Para verificar como ficou o meu repositório, entre [aqui][9].

**Lembrete:** Você só altera os arquivos se você quiser, nada do que está aqui é obrigatório, leia caso realmente queira alterar alguma coisa no template. 

Você pode alterar os arquivos na unha. Eu não sou o tipo de cara que gosta de mexer no que tá queto, mas, com certeza, num futuro próximo vou alterar um pouco do CSS do tema e talvez até criar um tema próprio. E como fazer isso? Navegue nas pastas do seu repositório. Como nós vamos ir direto na pasta onde se encontra o tema (css) vá até: _seu-repositório/public/css_ ([reidark.github.io/public/css][10]). Pronto, ai está todo o CSS dá página, altere como desejar.

*** Como eu altero esses arquivos:?**
  
**R:** Olha, pra alterar meus repositórios no Github, eu gosto de usar o github for PC/MAC. É o software do github que você baixa na sua máquina e consegue editar facilmente seus repositórios. Você pode fazer o download aqui: [Windows][11] ou [MAC][12]. Depois de baixado, é só abrir e logar sua conta. Depois de logar sua conta você terá acesso a todos os seus repositórios, para alterá-los, basta &#8220;clonar&#8221; esse repositório para algum lugar do seu computador. Pronto, agora faça suas alterações, brinque, fuce. Após você salvar o arquivo, no software do github vai ter um &#8220;commit pendente&#8221; que seria basicamente uma alteração no arquivo original. Basta você ir lá, &#8220;commitar&#8221; (enviar) essa alteração que é basicamente apertar 1 botão e pronto!

Caso você tenha dúvidas para alterar os arquivos, é só olhar naquela mesma página em que você efetuou o download, lá tem explicações.

Você também pode usar o Git (provavelmente os mais experientes com versionamento irão fazer isso), mas isso eu já consideraria um pouco avançado, porém, você é livre para [aprender Git][13] (altíssimo recomendado).

## Eu devo fazer esse blog?

É aqui que eu queria chegar. Eu recomendaria esse tipo de blog estático para desenvolvedores e pessoas evangelizadoras do _open source_. Lembre-se, o seu blog é código aberto (repositório público) e qualquer um pode xeretar por lá, isso significa que eles podem te ajudar, enviando commits para melhorar, ou apenas olhar.

Não coloque esperanças em criar um baita blog de entretenimento com essa ferramenta, claramente ela não foi feita pra isso (caso você queira tentar, você é livre, meu amigo). Mas eu defendo totalmente a idéia de desenvolvedores criarem blogs para a postagem de artigos pessoais e outras coisas para o avanço do código aberto, já que nossa comunidade é basicamente movida a isso.

Sejam livres para inovar, até porque essas coisas são feitas para isso!

Espero que eu tenha conseguido apresentar essa nova ferramenta bacana pra vocês. Caso ela tenha algumas novas versões, pode ter certeza que eu volto pra mostrar, haha.

Alguns links que podem ser interessantes:

Site Oficial &#8211; [tinypress.co][2]
  
Twitter Oficial &#8211; [@tinypress][14]
  
Meu blog criado com tinypress (básico) &#8211; [reidark.github.io][15]

Abraços 🙂

 [1]: http://tableless.com.br/ghost-simples-e-perfeita-plataforma-para-publicacoes/
 [2]: https://tinypress.co/
 [3]: http://reidark.github.io/criando-paginas-no-github/
 [4]: http://tableless.com.br/uploads/2014/04/Captura-de-Tela-2014-04-23-às-20.51.26.png
 [5]: http://tableless.com.br/uploads/2014/04/Captura-de-Tela-2014-04-23-às-21.12.44.png
 [6]: http://tableless.com.br/uploads/2014/04/Captura-de-Tela-2014-04-23-às-21.21.01.png
 [7]: http://daringfireball.net/projects/markdown/syntax
 [8]: http://jekyllrb.com/docs/github-pages/
 [9]: https://github.com/reidark/reidark.github.io
 [10]: https://github.com/reidark/reidark.github.io/tree/master/public/css
 [11]: https://windows.github.com/
 [12]: https://mac.github.com/
 [13]: http://tableless.com.br/iniciando-no-git-parte-1/
 [14]: https://twitter.com/tinypress_co
 [15]: http://reidark.github.io/