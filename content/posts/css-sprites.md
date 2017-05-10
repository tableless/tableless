---
title: CSS Sprites
author: Zeno Rocha
type: post
date: 2012-01-16
excerpt: Como fazer de forma moderna e sem chatices
url: /css-sprites/
shorturls:
  - 'a:3:{s:9:"permalink";s:31:"http://tableless.com.br/?p=6446";s:4:"isgd";s:19:"http://is.gd/zXFW2Y";s:7:"tinyurl";s:26:"http://tinyurl.com/7fzye82";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 767905273
categories:
  - CSS
  - O Básico

---
Um tópico recorrente na discussão sobre performance no lado do cliente é o famoso CSS Sprite. O problema é que muita gente conhece a técnica, muita gente reconhece sua importância, mas aplicar que é bom, nada. 

Por isso, vou mostrar hoje algumas ferramentas que podem te ajudar nessa missão.

## O que é?

Pra quem não conhece, essa é uma técnica que se baseia em combinar diversas imagens em uma só, em busca de diminuir o número de requisições HTTP para o servidor. E essa é apenas uma de suas aplicações, no mundo dos games, por exemplo, ela é muito usada para fazer animações.

Imagine um menu como esse:

<img class="alignnone size-full wp-image-6451" src="http://tableless.com.br/uploads/2012/07/esc.jpg" alt="" width="720" height="51" srcset="uploads/2012/07/esc.jpg 720w, uploads/2012/07/esc-300x21.jpg 300w" sizes="(max-width: 720px) 100vw, 720px" />

Fazer uma requisição para cada uma das imagens é muito ruim em termos de performance, por isso podemos recorrer aos CSS Sprites da seguinte maneira. Montamos nossa lista não-ordenada de elementos, mas ao invés de utilizarmos a tag _img_, aplicamos uma classe para cada um dos itens.

<pre class="lang-html">&lt;ul&gt;
	&lt;li class="escudos atletico-mg"&gt;&lt;/li&gt;
	&lt;li class="escudos botafogo"&gt;&lt;/li&gt;
	&lt;li class="escudos coritiba"&gt;&lt;/li&gt;
&lt;/ul&gt;
</pre>

Para então no CSS, utilizarmos como _background_ apenas uma imagem que contém todos os escudos. E para cada um dos elementos, colocamos a posição X e Y dentro dessa imagem que contém todos eles.

<pre class="lang-css">.escudos {
	background: url('images/sprite.png') no-repeat;
}

.atletico-mg {
	background-position: 0 -416px;
}

.botafogo {
	background-position: 0 -557px;
}

.coritiba {
	background-position: 0 -185px;
}
</pre>

Assim conseguimos diminuir o tamanho em KB dos dados trafegados e também o número de requisições HTTP para o servidor.

## Como fazer?

Para aplicar essa técnica você pode recorrer ao Photoshop colocando todas as imagens em um só arquivo e então buscando a posição X e Y com a régua. Uma excelente alternativa para pessoas masoquistas.

Já para pessoas normais, existem boas ferramentas como o [SpriteCow][1] e o [SpritePad][2] que te auxiliam nesse trabalho.

Agora, se você quer algo que realmente agilize seu trabalho, seja na criação ou na manutenção de CSS Sprites, então apresento-lhe o [Sprite Generator][3] do [Compass][4].

Confere aí o vídeo que gravei especialmente pra vocês 🙂

 [1]: http://spritecow.com
 [2]: http://wearekiss.com/spritepad
 [3]: http://compass-style.org/help/tutorials/spriting/
 [4]: http://compass-style.org/