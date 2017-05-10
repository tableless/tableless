---
title: WebP, hora de brincar?
author: Franklin Nilson
type: post
date: 2014-02-28
excerpt: Imagens menores que podem ajudar a tornar a web mais rápida.
url: /webp-hora-de-brincar/
dsq_thread_id: 2153677098
categories:
  - Tecnologia e Tendências
tags:
  - ages
  - w3c
  - webp

---
O Google sempre tenta ao máximo melhorar a qualidade e eficiência da web. Dessa vez ele tenta poupar alguns KB a mais nos formatos de imagens com o recente formato WebP, que foi anunciado em 2010 e ganhou visibilidade ao longo dos últimos anos, mas sem ter conseguido muita adesão ainda.

O WebP é um formato de imagem da Google que fornece a mesma qualidade de arquivos como PNG e JPG com tamanhos reduzidos. O novo formato é de até 26% menor se comparadas com PNG&#8217;s, lembrando que a transparência é suportada. E pode chegar a 34% menor em comparação a JPEG, então já é hora de deixar os seus projetos mais velozes.

> Acredito que a preparação dos projetos para esse novo formato não será uma perda de tempo, porém, brevemente o WebP será uma realidade em diversas plataformas.

Mas qual a vantagem real dessa nova extensão? A vantagem em usar WebP é que este formato reúne todos os privilégios dos outros formatos populares em uma única extensão. Com uma imagem WebP você pode criar animações, como os GIFs, usar transparência, como nas PNG, usar qualidade relativamente superior à um JPG. Atualmente o uso do WebP foi testado pelo Facebook que economizou mais de 20% do tráfego total na rede, sem perder a qualidade.

Então, precisa de algo mais significativo que isso? A aposta da Google é reunir todos os formatos em apenas um, com vários benefícios.

De acordo com o HTTPArchive, as imagens de um site representam 60% do tamanho total da página. Infelizmente, uma das desvantagens para WebP é que apenas Opera e Chrome suportam.
  
Mas isso pode estar prestes a mudar porque o Firefox está reconsiderando sua decisão de rejeitar WebP. 

Recentemente utilizei em um projeto que desenvolvi (não posso informar por questões de privacidade) e a performance melhorou bastante.

A conversão das imagens para WebP é simples, e já consta com um tutorial rápido no site da google, nesse  [link][1]

Então vamos lá, depois de converter as imagens abaixo, veja um fallback para as plataformas que ainda não suportam o formato Webp. A brincadeira foi realizada da seguinte forma no html:

<pre class="lang-html">&lt;img alt="Informação da Imagem" src="carregamento.gif" /&gt;</pre>

Acima temos no Source uma imagem de carregamento até o load ser concluído, no &#8220;data-img&#8221; teremos a url da imagem no formato comum onde serão apresentadas em navegadores sem suporte ao Webp, em seguida o &#8220;data-webp&#8221; com o link da imagem Webp. Obs.: A estrutura html acima obteve êxito na validação do W3C.

O segredo para facilitar essa brincadeira é utilizar a última versão do Modernizr junto a biblioteca Jquery.
  
Nesse caso o Modernizr informará na tag HTML que o navegador suporta ou não WebP (no caso o html possuirá a classe &#8220;webp&#8221;).

<pre class="lang-html">&lt;body&gt;
	&lt;img src="carregamento.gif" data-img="imagem.png" data-webp="imagem.webp" alt="Informação da Imagem" /&gt;
	&lt;script src='jquery-1.10.2.min.js'&gt;&lt;/script&gt;
	&lt;script src='modernizr-latest.js'&gt;&lt;/script&gt;
&lt;/body&gt;
</pre>

Incluído os itens acima iremos criar uma função simples para que no carregamento da página o Source da imagem se altere para o browser com suporte:

<pre class="lang-javascript">$(window).load( function(){ // Carregamento do site
var item = $('html').hasClass('webp') ? 'webp' : 'img'; // Atribui o valor a variável item
function getWebp(item) { // Nome da função recebendo a variável item
	$('img').each( function(){ // Busca todas as imagens do site
		$( this ).attr('src', $( this ).data( item ) ); // Trocará o Source da imagem
	});
}
getWebp( item ); // Inicia a função passando a variável item como o parâmetro 
});
</pre>

Caso ocorra alguma chamada no css também ficaria simples a chamada Webp, seguindo a seguinte estrutura:

<pre class="lang-css">html.webp tagComBackground{
	background: url(imagem.webp);
}
html tagComBackground{
	background: url(imagem.jpg);
}</pre>

Um ponto que se deve levar em consideração é que o ato de gravar imagens da web se tornou algo bem comum, mas neste novo formato os usuários não conseguirão ver ou editar sem recorrer a programas que reconhecem arquivos Webp.

Porém, acredito que quanto mais pessoas tiverem problemas com essa tecnologia, mais rápido os problemas irão ser consertados, fazendo que o WebP seja adquirido em todos os browsers e softwares de edição de imagens. Rumo a internet mais rápida!

 [1]: https://developers.google.com/speed/webp/docs/precompiled?hl=pt-BR