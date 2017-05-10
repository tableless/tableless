---
title: Introdução ao CSS 3D – Flip Card
author: Diego Eis
type: post
date: 2011-12-21
excerpt: Entenda como funciona o CSS 3D e suas aplicações.
url: /introducao-ao-css-3d-flip-card/
tweetbackscheck:
  - 1356394605
shorturls:
  - 'a:3:{s:9:"permalink";s:31:"http://tableless.com.br/?p=4792";s:7:"tinyurl";s:26:"http://tinyurl.com/7oh62ow";s:4:"isgd";s:19:"http://is.gd/Vwt4Tq";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 511601273
categories:
  - Código
  - CSS
  - CSS3
  - HTML
  - Mercado e Comportamento
  - Técnicas e Práticas
  - Tecnologia e Tendências
tags:
  - 2011
  - CSS
  - CSS3
  - desenvolvimento web
  - Na Prática
  - tecnicascss
  - web standards

---
O CSS 3D é sem dúvida uma das features do CSS mais aguardadas por todas as crianças do Brasil. Fala a verdade! Fazer efeitozinhos com sombra, gradientes, transparências e etc já foi um dia na vida do desenvolvimento algo bacana. Hoje é muito fora de moda. Carne de vaca, sabe? Por isso o CSS 3D é tão esperado. Ele trará para a web efeitos visuais para layout que antes só viamos em sistemas que rodam em smartphones, tipo um iPhone ou nos sistemas operacionais mais populares como Linux e OSX.

Mas não se anime muito. Eu sei que você está ansioso para sair por aí colocando efeitos 3D de CSS em tudo quanto é aplicação. Mas calma&#8230; entenda que o CSS foi feito para estilizar documentos. Você o utiliza para melhorar a experiência dos usuários nos diversos dispositivos e não para enfeitar seu website como se fosse uma penteadeira. Lembra-se dos websites cheios de gifs animados? Pois é, cuidado para não cair no mesmo erro. Você estará utilizando o CSS 3D da maneira certa se seus efeitos passarem desapercebidos pelo usuário ao utilizar seu sistema. Encher seu sistema com efeitos a cada clique ou a cada ação pode fazer com que o usuário perca tempo e a paciência.

Mas vamos ao que interessa. 

### O suporte

Infelizmente isso ainda está restrito para browsers. O Internet Explorer não tem suporte ainda e nem tem data para tal. Todos os exercícios que você ver neste post são feitos para browsers que tem WebKit como motor de renderização. Por isso teste em seu Chrome ou no seu Safari. Eu testei no Chrome porque o Safari mostrou algumas inconsistências. O Opera está esperando as especificações de CSS Transforms amadurecerem para adicionar este recurso. Testei no Firefox 8.0.1 e o exercício não funcionou. 

A degradação do CSS 3D para os browsers que não o suportam é um pouco infeliz. Sugiro que se você for utilizar essas features, tente fazê-lo em projetos restritos para que não haja problemas com usuários de browsers antigos. Se ainda assim você quiser arriscar, crie soluções especifica para seu projeto, fazendo com que a experiência do seu cliente não seja muito prejudicada.
  
Sugiro que [utilize a biblioteca Modernizr][1] para identificar os browsers que não entendem o CSS 3D.

### Tudo é uma questão de perspectiva

Para falar de 3D, precisamos falar sobre perspectiva. Para ativar uma área 3D o elemento precisará de perspectiva.
  
Você pode aplicar a perspectiva ao elemento de duas formas: utilizando diretamente a propriedade **perspective** ou adicionando um valor **perspective()** na propriedade **transform**.

<pre class="lang-css">div {
  -webkit-perspective: 600;
}
</pre>

Ou:

<pre class="lang-css">div {
  -webkit-transform: perspective(600);
}
</pre>

Estes dois formatos são os gatilhos que ativam a área 3D onde o elemento irá trabalhar.

O valor da perspectiva determina a intensidade do efeito. Imagine como se fosse a distância de onde vemos o objeto. Quanto maior o valor, mais perto o elemento estará, logo, menos intenso será o visual 3D. Logo, se colocarmos um valor de _2000_, o objeto não terá tantas mudanças visuais e o efeito 3D será suave. Se colocarmos _100_, o efeito 3D será muito visível, como se fosse um inseto olhando um objeto gigante.

Você também precisa entender sobre o [ponto de fuga][2]. O ponto de fuga por padrão está posicionado no centro. Você pode modificar essa posição com a propriedade **perspective-origin**, que é muito parecido com a propriedade **transform-origin**, que define onde a ação de transformação do objeto acontecerá, nesse caso [quando falamos de ações 2D][3]. A propriedade **perspective-origin** afeta os eixos X e Y do elemento filho.

[Veja um exemplo com dois elementos][4]: um com pouca perspectiva e outra com muita perspectiva. 

### CSS 3D Transforms

Se você ainda não leu sobre CSS Transforms você pode [ler algo aqui][5] e [ver em ação aqui][6]. As propriedades são praticamente iguais, mas aplicadas para os princípios de 3D e não 2D.

Você deve estar acostumado a trabalhar com os eixos X e Y no CSS padrão. No CSS 3D podemos manipular também o eixo Z, que representa a profundidade.
  
[Veja um exemplo utilizando os valores **rotateY, rotateX e translateZ**][7]. Perceba que no **translateZ** eu utilizei valores negativos e positivos. Quando utilizo o valor negativo, o objeto fica &#8220;mais longe&#8221;, se coloco valores positivos, o objeto fica &#8220;mais perto&#8221;.

Abaixo segue uma imagem do resultado do exemplo:
  
[<img src="http://tableless.com.br/uploads/2011/12/img-transform3d.png" alt="" title="img-transform3d" width="801" height="706" class="alignnone size-full wp-image-4795" srcset="uploads/2011/12/img-transform3d.png 801w, uploads/2011/12/img-transform3d-300x264.png 300w" sizes="(max-width: 801px) 100vw, 801px" />][7]

Nós podemos utilizar também alguns atalhos para estes valores onde podemos definir as três dimensões de uma vez:

  * translate3d(x,y,z)
  * scale3d(x,y,z)
  * rotate3d(x,y,z,angle)

Muito importante: ao utilizar as propriedades resumidas, os browsers ativam automaticamente a aceleração por hardware no Safari para que as animações tenham uma melhor performance. 

## Fazendo o efeito de Card Flip

O efeito de Card Flip é muito conhecido entre os usuários de iPhone. Para ter ideia de como é o efeito <a href="http://tableless.github.com/exemplos/css3d/cardflip/cardflip.html" title="Exemplo de efeito card flip com CSS 3 3D" target="_blank">veja o exemplo final</a>.

A estrutura HTML é esta:

<pre class="lang-html">&lt;section class="geral"&gt;
  &lt;div class="carta"&gt;
    &lt;figure class="frente"&gt;&lt;img src="card-front.jpg"&gt;&lt;/figure&gt;
    &lt;figure class="atras"&gt;&lt;img src="card-back.jpg"&gt;&lt;/figure&gt;
  &lt;/div&gt;
&lt;/section&gt;
</pre>

O elemento _.geral_ é onde iniciaremos o ambiente 3D. O elemento _.carta_ age como container dos objetos 3D. Cada face da carta está separada por um elemento **figure**, com uma imagem.

Para começar, precisamos aplicar a perspectiva para o elemento _.geral_ iniciar o espaço 3D.

<pre class="lang-css">.geral { 
	width: 200px;
	height: 293px;
	position: relative;
	margin:10% auto 0;
	-webkit-perspective: 500;
}
</pre>

Defini uma largura e altura, coloquei um **position: relative;** para que os elementos dentro dele sejam posicionados se referenciando por ele. Coloquei uma margem só para separá-lo do topo do body a fim de conseguirmos ver melhor os efeitos.
  
Por fim, coloquei a propriedade **-webkit-perspective: 500;** para aplicarmos o efeito 3D. O valor de 500 faz uma boa perspectiva.

Agora definiremos as dimensões da carta e suas propriedades.

<pre class="lang-css">.carta {
  width: 100%;
  height: 100%;
  position: absolute;
  -webkit-transition: -webkit-transform 1s;
}
</pre>

Largura e altura precisam ser de 100% para definir a área que o 3D irá aplicar. O **position: absolute;** é necessário para que as cartas fiquem relativas ao elemento _.geral_. A propriedade **-webkit-transition: -webkit-transform 1s;** define o tempo de transição do efeito, neste caso ele vai durar 1 segundo. 

Formatando as cartas:

<pre class="lang-css">.carta figure {
  margin:0;
  display: block;
  position: absolute;
  width: 100%;
  height: 100%;
  -webkit-backface-visibility: hidden;
}
</pre>

Vamos direto para a propriedade **-webkit-backface-visibility: hidden;** já que as outras dispensam comentários. Essa propriedade faz com que a face de trás da carta não apareça e nem se sobreponha no momento do efeito.
  
E finalmente, para fazer com que a parte de trás da carta apareça no verso correto, nós temos que rotacioná-la.

<pre class="lang-css">.atras{-webkit-transform: rotateY(180deg);}
</pre>

E feito se completa com o trigger para fazer a animação acontecer. Nesse caso farei com um hover no elemento _.carta_, onde iremos rotacioná-lo em -180 graus.

<pre class="lang-css">.carta:hover {
  -webkit-transform: rotateY(-180deg);
}
</pre>

E Voilá! Se quiser brincar um pouco, modifique a origem da transformação com a propriedade **-webkit-transform-origin**. Adicionando essa linha, a transformação acontece para a direita em vez de ser pelo centro, como é o padrão:

<pre class="lang-css">.carta:hover {
  -webkit-transform: rotateY(-180deg);
  -webkit-transform-origin: right center;
}
</pre>

### 3Drollover.css

Encontrei uma biblioteca muito interessante que nos permite fazer estes efeitos de forma fácil e de acordo com os princípios do OOCSS. É necessário apenas estruturar da forma correta e trocar as classes de acordo com o efeito que você quer fazer. Coisa muito simples.

O nome da biblioteca é [3Drollover][8]. Clone no seu computador e divirta-se. Dá para usar em projetos facilmente. Veja abaixo um vídeo que mostra os efeitos:



### Para ler mais

  * Leia a [documentação oficial do W3C sobre CSS 3D Transforms][9].
  * Pessoal do [WebKit explicando sobre outras propriedades do CSS 3D Transforms][10].
  * Você pode [brincar um pouco com as propriedades do CSS 3D aqui][11].

 [1]: http://tableless.com.br/utilizando-a-biblioteca-modernizr/ "Utilizando a Biblioteca Modernizr"
 [2]: http://pt.wikipedia.org/wiki/Perspectiva_(gráfica) "Wikipedia: sobre ponto de fuga"
 [3]: http://tableless.github.com/exemplos/cssanimation.html
 [4]: http://tableless.github.com/exemplos/css3d/cardflip/propriedade-perspective.html
 [5]: http://tableless.com.br/introducao-ao-css-animation/ "Introdução ao CSS Animation"
 [6]: http://tableless.github.com/exemplos/csstransforms/
 [7]: http://tableless.github.com/exemplos/css3d/cardflip/propriedade-transform.html
 [8]: https://github.com/codepo8/3drollovers.css
 [9]: http://dev.w3.org/csswg/css3-3d-transforms/
 [10]: http://www.webkit.org/blog/386/3d-transforms/
 [11]: http://desandro.github.com/3dtransforms/examples/perspective-03.html