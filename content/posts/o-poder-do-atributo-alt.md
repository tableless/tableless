---
title: O poder do atributo “ALT”
author: Leonardo Lima
type: post
date: 2015-02-27
excerpt: 'Técnicas que podem resolver vários problemas que desenvolvedores web enfrentam, caso não utilizem a atributo <strong>ALT</strong> corretamente.'
url: /o-poder-do-atributo-alt/
categories:
  - Acessibilidade
  - Geral
  - HTML
  - HTML5
  - SEO
  - Técnicas e Práticas

---
Ao desenvolver um website, temos que pensar em acessibilidade para que seja visto por qualquer usuário. Tendo em vista que sua equipe planejou um website acessível, vocês pensaram em colocar em todas as imagens o atributo&#8221;ALT&#8221;. Pois, websites hoje em dia tem centenas ou milhares de imagens. Já imaginou você olhando para um quadro com uma imagem sem descrição nenhuma, pois é assim que um deficiente visual pode se sentir ao acessar seu website com várias imagens e ao executar um software sintetizador de voz, não tem nenhuma informação do que está na página.

## Requisitos para o texto servir de alternativa para imagem

O texto alternativo é uma maneira de fazer uma informação visual acessível.O texto alternativo permite que a informação seja renderizada de diversas maneiras e por vários user agents.Por exemplo, um deficiente visual vai escutar a informação contida no atributo&#8221;ALT&#8221; da imagem, utilizando um sintetizador de voz.

## Exemplos de usuários que são beneficiados com o uso do texto alternativo nas imagens

  * Está com conexão muito baixa e está navegando com imagens desabilitadas;
  * Eles estão usando um navegador somente texto;
  * Eles têm problemas de carregar imagens ou a fonte de uma imagem está errado.
  * Eles têm uma deficiência visual e usa um sintetizador de voz;

## Vamos orientar o usuário

Quantas vezes você acessou um site que o atributo está vazia(empty). Será que esqueceram ou quem desenvolveu o site não sabe do poder do atributo alt? Agora, quando acessamos um site com milhares de imagens e todas elas com o atributo preenchida corretamente, essas imagens serão muito bem rederizadas pelos buscadores (Google,Bing e Duckduckgo).
  
Outra ajuda muito importante que os desenvolvedores não prestam atenção é que se o seu usuário for um deficiente visual, como você vai ajudar que a imagem seja entendida pelo sintetizador de voz instalado na máquina senão tem nada preenchido.Cuide bem do seu usuário.

## Exemplos do uso correto e incorreto do atributo alt

Uma utilização correta do atributo alt, logo abaixo.

<pre class="lang-html">&lt;ul&gt;
  &lt;li&gt;&lt;button&gt;&lt;img src="b.png" alt="Bold"&gt;&lt;/button&gt;&lt;/li&gt;
  &lt;li&gt;&lt;button&gt;&lt;img src="i.png" alt="Italics"&gt;&lt;/button&gt;&lt;/li&gt;
  &lt;li&gt;&lt;button&gt;&lt;img src="strike.png" alt="Strike through"&gt;&lt;/button&gt;&lt;/li&gt;
  &lt;li&gt;&lt;button&gt;&lt;img src="blist.png" alt="Bulleted list"&gt;&lt;/button&gt;&lt;/li&gt;
  &lt;li&gt;&lt;button&gt;&lt;img src="nlist.png" alt="Numbered list"&gt;&lt;/button&gt;&lt;/li&gt;
  &lt;/ul&gt;
</pre>

Agora vamos mostrar uma maneira incorreta, mas uma das mais comuns de acontecer.

<pre class="lang-html">&lt;ul&gt;
  &lt;li&gt;&lt;button&gt;&lt;img src="b.png" alt="img btn1"&gt;&lt;/button&gt;&lt;/li&gt;
  &lt;li&gt;&lt;button&gt;&lt;img src="i.png" alt="img btn2"&gt;&lt;/button&gt;&lt;/li&gt;
  &lt;li&gt;&lt;button&gt;&lt;img src="strike.png" alt="img btn3"&gt;&lt;/button&gt;&lt;/li&gt;
  &lt;li&gt;&lt;button&gt;&lt;img src="blist.png" alt="img btn4"&gt;&lt;/button&gt;&lt;/li&gt;
  &lt;li&gt;&lt;button&gt;&lt;img src="nlist.png" alt="img btn5"&gt;&lt;/button&gt;&lt;/li&gt;
  &lt;/ul&gt;
</pre>

Vamos observar que o atributo alt dessa maneira apenas quem vai entender será o time que desenvolveu o site, agora quando o google for renderizar essas imagens não vai ter nenhum sentido a imagem e o texto alternativo.
  
Como devemos utilizar corretamente o texto alternativo, veja no [link][1].

## Quando saber que o atributo alt é poderoso

Quando você desenvolve um site e não precisa explicar nada para o usuário sobre as imagens, apenas o atributo alt já explica o que é cada imagem, então você está começando a entender mais sobre o **poder do atributo alt**.
  
Abraço galera até a próxima.

## Referência

[W3C Techniques for providing useful text alternatives][2]

 [1]: https://jsfiddle.net/leonardo403/z89nty4o/embedded/result/
 [2]: http://www.w3.org/TR/html-alt-techniques/