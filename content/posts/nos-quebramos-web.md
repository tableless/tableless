---
title: Nós quebramos a web
author: fernahh
type: post
date: 2015-05-04
excerpt: É sempre difícil apontar o erro de alguém. Ainda mais para pessoas que não aceitam críticas. Porém, é preciso olhar para nós mesmos para corrigir nossos problemas.
url: /nos-quebramos-web/
categories:
  - Acessibilidade
  - Artigos
  - Opinião
tags:
  - acessibilidade
  - Progressive Enhancement
  - web

---
Depois das grandes evoluções que tivemos na web (HTML5, CSS3 e novas APIs JavaScript), junto vieram alguns problemas, aquela história de _&#8220;Com grandes poderes vem grandes responsabilidades&#8221;_. As novas features da Open Web são fantásticas. Lembro-me bem quando nós eramos cautelosos no usar certos recursos com medo de não conseguir entregar o conteúdo ao usuário. No fim, surgiram (e surgem) _polyfills_ e n maneiras de darmos _fallback_ ao usuário com menos recursos. Sendo assim, conseguimos entregar um conteúdo rico para usuários com recursos modernos, e o conteúdo com uma experiência mais simples à usuários com recursos simples.

Tudo perfeito? Na teoria sim, na prática não.

## Ao menos tente aplicar Progressive Enhancement {#ao-menos-tente-aplicar-progressive-enhancement}

Em poucas palavras, **Progressive Enhancement** é uma maneira de desenvolver aplicações de forma a suportar browser antigos, conexões lentar, etc. Se você não sabe o que é esse termo, vá atrás porque passou da hora. _(Recomendo esse post do <a title="Diego Eis no Twitter" href="https://twitter.com/diegoeis" target="_blank">@diegoeis</a> sobre o assunto: <a title="Fault Tolerance: a base do Progressive Enhancement" href="http://tableless.com.br/faut-tolerant-base-progressive-enhancement/" target="_blank">Fault Tolerance: a base do Progressive Enhancement</a>)_

Há pouco tempo eu era um hater de aplicações e frameworks que não davam suporte ao PE (Progressive Enhancement) ou dificultavam esse tipo de abordagem. Mas o extremismo nunca é saudável. Em um comentário que fiz em um tweet do <a title="Daniel Filho no Twitter" href="https://twitter.com/danielfilho" target="_blank">@danielfilho</a>, ele respondeu algo que me fez mudar de opinião:

<blockquote class="twitter-tweet" lang="pt">
  <p dir="ltr" lang="en">
    <a href="https://twitter.com/fernahh">@fernahh</a> it might not support it. but you need to be aware that it’s not everyone who lives on the 1st world & have blazing fast connection.
  </p>
  
  <p>
    — Daniel Filho (@danielfilho) <a href="https://twitter.com/danielfilho/status/585604385440432129">8 abril 2015</a>
  </p>
</blockquote>

**É isso!** Nem todo mundo tem uma internet rápida ou o último release do navegador mais moderno. A ideia da web sempre foi ser inclusiva e entregar o conteúdo a todos. Mas por que não fizemos isso? Por que estamos usando o HTML só pra carregar uma tag `<script>`? Ao menos tente aplicar Progressive Enhancement. Tudo depende de onde sua aplicação irá rodar, quem serão os usuários dela, mas se estiver na &#8220;web pública&#8221;, considere (muito) o PE.

## A web é acessível {#a-web--acessvel}

A web em sua forma mais simples é acessível. Veja <a title="Exemplo de uma página acessível" href="http://codepen.io/fernahh/pen/OVJNWB" target="_blank">esse exemplo no Codepen</a>, só usei [Normalize][1] e HTML.

Contraste perfeito. Links legíveis. Botões que parecem botões. Um leitor de tela provavelmente se daria bem lendo o conteúdo dessa página, mesmo sem uma extensão com [WAI-ARAI][2]. Um usuário provavelmente interpretaria rápido a informação com elementos expressados dessa forma.

Mas se a web na sua forma mais crua é acessível, por que desenvolvedores fazem isso?

<div style="width: 510px" class="wp-caption aligncenter">
  <a href="http://sighjavascript.tumblr.com/" target="_blank"><img class="" src="http://41.media.tumblr.com/49748cc0168a329867f45fcc807ae650/tumblr_mslkvjXcmX1sgju96o1_1280.png" alt="Instagram sem JavaScript não funciona." width="500" height="400" /></a>
  
  <p class="wp-caption-text">
    Exemplo do tumblr &#8220;Sign, JavaScript&#8221; (http://sighjavascript.tumblr.com/)
  </p>
</div>

Todos tem a resposta para a pergunta acima na ponta da língua: desenvolvedores fazem isso pelo _hype_ de usar novas tecnologias, mas esquecem de atender todos os usuários, **quebrando a web**.

## O reencontro com o caminho para uma web inclusiva {#o-reencontro-com-o-caminho-para-uma-web-inclusiva}

Estamos seguindo o embalo das novas tecnologias deixando de lado o mais básico que um desenvolvedor web deve saber, que consiste em aprender protocolos, algoritimos, HTML, CSS e JavaScript. Apenas com esses caras já conseguimos entregar o conteúdo com uma experiência bacana ao usuário.

Estude padrões.

_Frameworks_, bibliotecas e pré-processadores são fantásticos, mas primeiro vamos fazer o que a web se propôs a fazer desde seu início: **ser inclusiva**.

 [1]: http://necolas.github.io/normalize.css/
 [2]: http://tableless.com.br/wai-aria-estendendo-o-significado-das-interacoes/