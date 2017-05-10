---
title: Não troque todas as suas imagens por background!
author: Elcio Ferreira
type: post
date: 2007-03-16
url: /nao-troque-todas-as-suas-imagens-por-background/
tweetbackscheck:
  - 1356251011
shorturls:
  - 'a:3:{s:9:"permalink";s:71:"http://tableless.com.br/nao-troque-todas-as-suas-imagens-por-background";s:7:"tinyurl";s:26:"http://tinyurl.com/3fuugc3";s:4:"isgd";s:19:"http://is.gd/gIYG5X";}'
twittercomments:
  - 'a:5:{i:8232404506386432;s:7:"retweet";i:18524183449305089;s:7:"retweet";i:21344047213842432;s:7:"retweet";i:34027031129890816;s:7:"retweet";i:50243902250287104;s:7:"retweet";}'
tweetcount:
  - 5
dsq_thread_id: 503036813
categories:
  - Geral
tags:
  - acessibilidade
  - image-replacement
  - Na Prática
  - tecnicascss

---
Às vezes é bom repetir os fatos básicos, principalmente porque tem sempre gente chegando e começando a aprender.

Uma dúvida muito comum, que eu vejo se repetir há alguns anos, é onde usar e onde não usar imagens no background via CSS. Para quem está chegando agora, a questão básica é que existem duas maneiras de se fazer uma imagem aparecer na tela. Cada uma delas tem suas vantagens e desvantagens e é melhor usada para um fim específico. Mas muita gente usa apenas um método ou o outro.

Uma delas é inserir uma tag HTML:

`<img src="seta.gif" alt="Prosseguir" />`

A outra é inserir essa imagem como background de uma tag qualquer através do CSS:

`a.prosseguir {<br />
   background: white url(seta.gif) top left no-repeat;<br />
}`

As diferenças entre eles, embora não apareçam à primeira olhada no site, são substanciais. Experimente, por exemplo, desligar o CSS daqui do Tableless. Você vai ver que todas as imagens que compôem o layout, incluindo logotipo e as sombras laterais, vão desaparecer. Vão sobrar apenas umas imagenzinhas do Feedburner e da barra lateral direita.

Quem trabalha com tabelas geralmente usa apenas o primeiro método. Infelizmente muita gente aprendendo a construir layouts Tableless com CSS, ao aprender o segundo método, tem abandonado completamente o uso da tag img. É um exagero comum entre os novatos, assim como [abandonar completamente o uso da tag table][1].

Por que o Diego escolheu algumas imagens para ir no meio do código HTML e outras para inserir como background CSS? A regra é simples, como todo o resto na dobradinha XHTML+CSS, imagens que fazem parte de seu conteúdo vão no HTML, imagens que são apenas elementos de layout vão no CSS.

Veja, por exemplo, [este meu post sobre o Performancing][2]. Há, no topo e no rodapé, dois gradientes. Experimente desligar o CSS. Você vai ver que algumas imagens foram mantidas. Todas elas fazem parte do conteúdo da página:

  * O banner para o [Workshop Produtividade Web 2.0][3].
  * O screenshot do Performancing.
  * A setinha para cima do Rec6 e a corretinha do Linkk.
  * O banner do Firefox
  * Minha foto.

Há outra maneira, que talvez você ache mais simples, para explicar isso. Imagine-se fazendo o redesign do site. Todas as imagens que você deve manter exatamente como estão são conteúdo. Todas as que você vai querer mudar são layout. Veja isso no exemplo acima. Você não muda um banner, a foto do autor do site ou o screenshot de um programa porque fez um redesign em seu site. Mas, claro, bordas, sombras, fundos, chanfros, linhas separadoras, logotipos, tudo isso pode mudar.

Uma última coisa em que você pode pensar é na indexação pelo Google Bot. Ao fazer uma pesquisa de imagens, você vai querer que as pessoas encontrem em seu site um screenshot de programa, a foto de uma celebridade, um diagrama de explicação de uma teoria ou uma foto de um animal. Mas as imagens decorativas só vão atrapalhar.

Há ainda um terceiro caso que pode confundí-lo, que é o image replacement. Mas sobre isso [o Diego já escreveu bastante][4].

 [1]: http://tableless.com.br/forum/viewtopic.php?t=3821
 [2]: http://blog.elcio.com.br/performancing/
 [3]: http://curso.visie.com.br/go/2/http://visie.com.br/afiliados/6/visie.com.br/workshop/
 [4]: http://tableless.com.br/aprenda/image-replacement-ou-imagens