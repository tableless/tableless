---
title: Criando efeitos de páginas de livro no seu front-end
author: Fabio Soares
type: post
date: 2016-01-14
excerpt: Uma breve introdução da biblioteca Turn.js para fazer efeitos de páginas de livros no seu front-end.
url: /criando-efeitos-de-paginas-de-livro-no-seu-front-end/
categories:
  - Código
  - HTML5
  - JavaScript
  - JQuery
  - UX
tags:
  - html5
  - JavaScript
  - JQuery

---
O <a href="http://www.turnjs.com/" target="_blank">Turn.js</a> é uma biblioteca JavaScript que faz o conteúdo parecer um livro ou revista de verdade, usando as vantagens do HTML5.

É uma biblioteca baseada no jQuery, versão 1.7 ou superior, então é um requerimento básico.
  
Temos o suporte para os navegadores:

  * Chrome 12+
  * Safari 5+
  * Firefox 10+
  * Internet Explorer 9+

## Na prática

Como exemplo, vamos usar como base a história criada por  <a href="http://adagadegelo.deviantart.com/art/A-Historia-Nao-Contada-Da-Estrela-Azul-572943339" target="_blank">Rodrigo Martins</a>, que tranformou em quadrinhos o meme da internet &#8220;Já acabou, Jéssica&#8221;.

Vamos utilizar _divs_ para criar as páginas do livro:

<pre class="lang-html">&lt;div id="quadrinho"&gt; &lt;!-- Criando um novo quadrinho --&gt;
	&lt;div class="hard" id="capa"&gt;&lt;/div&gt; &lt;!-- Criando a capa --&gt;
	&lt;div class="hard"&gt;&lt;/div&gt; &lt;!-- Criando a parte de trás da capa --&gt;
	&lt;div class="page" id="pagina-2"&gt;&lt;/div&gt; &lt;!-- Criando as páginas --&gt;
	&lt;div class="page" id="pagina-3"&gt;&lt;/div&gt;
	&lt;div class="page" id="pagina-4"&gt;&lt;/div&gt;
	&lt;div class="page" id="pagina-5"&gt;&lt;/div&gt;
	&lt;div class="page" id="pagina-6"&gt;&lt;/div&gt;
	&lt;div class="page" id="pagina-7"&gt;&lt;/div&gt;
	&lt;div class="page" id="pagina-8"&gt;&lt;/div&gt;
	&lt;div class="page" id="pagina-9"&gt;&lt;/div&gt;
	&lt;div class="hard"&gt;&lt;/div&gt;
	&lt;div class="hard"&gt;&lt;/div&gt; &lt;!-- Criando a contracapa --&gt;
&lt;/div&gt;
&lt;script src="https://code.jquery.com/jquery-2.1.1.min.js"&gt;&lt;/script&gt;
&lt;script src="https://raw.githubusercontent.com/blasten/turn.js/master/turn.min.js"&gt;&lt;/script&gt;
</pre>

Foi utilizado as classes padrões ._page_ em casos de páginas comuns, e a classe ._hard_ para a capa e contracapa.

Agora vamos adicionar alguns estilos:

<pre class="lang-css">#quadrinho{ //Definindo o tamanho
    width: 800px; 
    height: 600px;
}
#quadrinho .page{ //Definindo os valores padrão para todas as páginas
    background-color: #FFF; //Fundo branco porque, caso não carregue as imagens, ela não fique transparente.
    background-size: cover; //O Fundo precisa cobrir toda a página
}
#quadrinho .hard{
    background-color: #CCC; //Fundo cinza para diferenciar das páginas comuns
    background-size: cover;
}

// Definindo as páginas que servirão de exeplo
#capa{
	background: url("http://tableless.com.br/uploads/2015/11/Paginas-01.png");
}
#pagina-2{
	background: url("http://tableless.com.br/uploads/2015/11/Paginas-02.png");
}
#pagina-3{
	background: url("http://tableless.com.br/uploads/2015/11/Paginas-03.png");
}
#pagina-4{
	background: url("http://tableless.com.br/uploads/2015/11/Paginas-04.png");
}
#pagina-5{
	background: url("http://tableless.com.br/uploads/2015/11/Paginas-05.png");
}
#pagina-6{
	background: url("http://tableless.com.br/uploads/2015/11/Paginas-06.png");
}
#pagina-7{
	background: url("http://tableless.com.br/uploads/2015/11/Paginas-07.png");
}
#pagina-8{
	background: url("http://tableless.com.br/uploads/2015/11/Paginas-08.png");
}
#pagina-9{
	background: url("http://tableless.com.br/uploads/2015/11/Paginas-09.png");
}
</pre>

Cada página do quadrinho recebe seu próprio _background_, contendo o conteúdo desejado.

E por fim, só é preciso colocar 5 linhas de JavaScript:

<pre class="lang-javascript">$("#quadrinho").turn({
    width: 800, // Para definir a largura da página
    height: 600, // Para definir a altura da página
});
</pre>

E pronto: basta abrir o navegador e ser feliz. 🙂

Quem quiser ver o resultado basta <a href="http://codepen.io/anon/pen/Vezozz" target="_blank">clicar aqui</a>. [Link atualizado]

Acesse:
  
<a href="http://turnjs.com/" target="_blank">Website do Turn.js</a>
  
<a href="https://github.com/blasten/turn.js" target="_blank">Github do Turn.js</a>