---
title: 'O futuro chegou: O elemento picture'
author: Victor "reidark" Matias
type: post
date: 2014-06-10
excerpt: Se você tinha problemas com imagens responsivas, agora não tem mais...
url: /o-futuro-chegou-o-elemento-picture/
dsq_thread_id: 2744674958
categories:
  - Artigos
  - Browsers
  - Código
  - HTML
  - Mobile
  - Notícias
  - Responsive Web Design (RWD)
tags:
  - picture
  - responsive images
  - rwd
  - srcset

---
O título é muito tentador, não é? Então, eu apenas estou completando o que a [Dani Guerrato][1] disse nesse artigo sobre [Imagens Responsivas (Elemento Picture)][2]. O &#8220;futuro&#8221;, agora, é nosso querido presente.

No dia 04/06/2014 o site [A List Apart postou um artigo][3] falando sobre o elemento _picture_ que era estudado há um bom tempo e foi **finalmente** implementado para testes no Google Chrome Canary (Browser para testes das mais novas coisas que inventam). E, como ressalva, outros browsers, como o [Firefox][4], já estão atrás de adicionar no seu ambiente de testes.

## O grande problema da atual imagem responsiva

Antes dessa grande notícia sobre o `picture`, outras &#8220;soluções&#8221; eram usadas por desenvolvedores pelo mundo à fora. Uma delas é o famoso e básico `max-width: 100%;`. No começo, acharam que era a melhor solução, só esqueceram de lembrar que ele apenas adaptava o tamanho de uma imagem que já era grande, ou seja, o visual ficava bacana, mas o tamanho da requisição ainda era do tamanho nativo da imagem. Por mais que ela estivesse aparecendo bonita, sem quebrar o layout, um usuário que acessava pelo celular ainda carrega aquela imagem de dimensão 800&#215;600.

Mas, o pessoal não desanimou, e após se deparar com o problema a cima, foi proposto o grande [picturefill][5], que é basicamente uma cópia fiel ao `picture`, só que usa uma muleta: Javascript.

Particularmente dizendo, essa foi a melhor solução encontrada, já que praticamente simulava o nativo `picture` de cima em baixo. Porém, muitos ainda reclamavam (por algum motivo) sobre ter que forçar um Javascript para fazer funcionar, sendo que o próprio era levíssimo. 

## A introdução ao picture

O picture foi a solução mais plausível, semântica e dentro dos &#8220;web standards&#8221; proposto pela comunidade. Com o [grande apoio de todos][6], conseguiram criar um [rascunho na própria W3][7] para futuras discussões sobre o mesmo.

**Mas então, o que há de tão bom nisso?**

Esse novo elemento nós dá a &#8220;simples&#8221; opção de escolher qual imagem é mais adequada para cada tamanho de tela que acessar o site. Seja uma TV, Desktop, Smartphone, Tablet, Kindle ou qualquer outra coisa que conseguirmos usar. 

Na prática, faremos algo mais ou menos assim:

<pre class="lang-html">&lt;picture&gt;
   &lt;source media="(min-width: 500px)" src="grande.jpg"&gt;
   &lt;source media="(min-width: 250px)" src="medio.jpg"&gt;
   &lt;source src="pequena.jpg"&gt;
   &lt;img src="pequena.jpg" alt=""&gt;
   &lt;p&gt;Textos&lt;/p&gt;
&lt;/picture&gt;
</pre>

Dentro do elemento picture, inserimos o source com os devidos tamanhos a serem &#8220;verificados&#8221; e assim carregar a imagem certa para aquela tela. Pense nisso como uma media querie inline para imagens :). Porém, como alguns navegadores <del>ie</del> podem não suportar o elemento picture, colocamos um fallback com o antigo elemento img, assim a imagem ainda aparecerá, mesmo sendo num navegador de dinossauros.

Outra opção também será usar o atributo `srcset`, onde é definido várias imagens para cada media, e assim, o navegador &#8220;escolhe&#8221; a melhor imagem para exibir. A adaptação fica mais ou menos assim:

<pre class="lang-html">&lt;picture&gt;
   &lt;source media="(min-width: 500px)" srcset="grande-1.jpg 1x, grande-2.jpg 2x"&gt;
   &lt;source media="(min-width: 250px)" srcset="medio-1.jpg 1x, medio-2.jpg 2x"&gt;
   &lt;source srcset="pequena-1.jpg 1x, pequena-2.jpg 2x"&gt;
   &lt;img src="pequena-1.jpg" alt=""&gt;
   &lt;p&gt;Textos&lt;/p&gt;
&lt;/picture&gt;
</pre>

O legal do srcset, é que com a ajuda do autor e do próprio navegador, a escolha da imagem fica &#8220;inteligente&#8221;. O user-agent analisa a conexão do usuário, questões de experiência de usuário, preferências do usuário entre outras coisas.

## Colocando em prática

No post do A List Apart, ele ensinam como podemos fazer os testes no elemento picture. Você basicamente tem que: 

  1. Ter o [Chrome Canary][8] instalado.
  2. Apos adquirir o navegador, coloque isso na barra de endereço: `chrome://flags/#enable-experimental-web-platform-features`
  3. Clique em _enable_.
  4. Reinicie o navegador.

Após seguir esses passos, entre no Chrome Canary e visite o [teste que eu fiz do elemento picture já funcionando][9]. Para testar é simples, vai redimensionando o navegador e dando refresh na página, a imagem vai mudar de acordo com o tamanho da tela. O legal é, caso você tente entrar num navegador normal, vai aparecer a imagem &#8220;Fallback&#8221;.

Faça o teste você também, é bom já ir pegando as &#8220;manhas&#8221;.

## Permanecendo com os pés no chão

É muito legal saber que a comunidade conseguiu tudo isso, mas não vamos nos apressar demais. Ainda está em fase de testes, porém [vamos apoiar e ajudar][10] ao máximo essa nova fase. 

Queria mostrar que, com a ajuda de todos, conseguiram implementar uma nova funcionalidade ao html extremamente essencial. Agora é questão de tempo para os navegadores mais novos irem experimentando e levando a ideia cada vez mais adiante.

## Levante a bandeira

Bem amigos, creio que agora seja uma hora importante para toda a comunidade. Queria vir mostrar que o picture não é mais um simples &#8220;rascunho&#8221; e sim uma importante funcionalidade que será implementando de acordo com o tempo.

A notícia sobre os testes com o picture foi extremamente excitante, por isso espero que possamos discutir aqui nos comentários o futuro disso.

Deixarei alguns links úteis, caso queiram ver:

Post on A List Apart: [Testing Responsive Images][3]
  
Issues about picture and bugs: [Issues on Github][10]
  
Picture on W3: [The picture element][7]
  
ResponsiveImages.org: [About picture][11]

É isso ai galera, abraços!

 [1]: http://tableless.com.br/author/daniguerrato/
 [2]: http://tableless.com.br/imagens-responsivas-de-alta-performance/
 [3]: http://alistapart.com/blog/post/testing-responsive-images/
 [4]: https://bugzilla.mozilla.org/show_bug.cgi?id=870022
 [5]: https://github.com/scottjehl/picturefill
 [6]: https://gist.github.com/Wilto/547b88c657b511fb1dc5
 [7]: http://www.w3.org/TR/html-picture-element/
 [8]: http://www.google.com/intl/en/chrome/browser/canary.html
 [9]: http://www.reidark.com.br/picture.html
 [10]: https://github.com/yoavweiss/Blink/issues
 [11]: http://responsiveimages.org/