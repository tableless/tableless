---
title: Colocar Rodapé fixo no fim da página
author: Diego Eis
type: post
date: 2010-01-12
excerpt: Como deixar o Rodapé fixo fim da página quando houver pouco conteúdo.
url: /colocar-rodape-fixo-no-bottom/
aktt_notify_twitter:
  - no
tweetbackscheck:
  - 1356391400
shorturls:
  - 'a:3:{s:9:"permalink";s:53:"http://tableless.com.br/colocar-rodape-fixo-no-bottom";s:7:"tinyurl";s:26:"http://tinyurl.com/42ny4bw";s:4:"isgd";s:19:"http://is.gd/pYGzBz";}'
twittercomments:
  - 'a:2:{i:33228918613868546;s:6:"136995";i:33229249532014592;s:6:"136996";}'
tweetcount:
  - 2
dsq_thread_id: 503026001
categories:
  - CSS
  - HTML
  - Técnicas e Práticas
tags:
  - CSS
  - Na Prática
  - tableless
  - tecnicascss
  - tutorial
  - xhtml

---
Você já precisou ter o rodapé fixo no fim da página algum dia. Normalmente os clientes chatos acham feio aquele rodapé terminando no meio da página quando há pouco conteúdo. Há uma técnica no CSS que resolve isso. Não funciona no IE6, já aviso agora. Na verdade, tem um jeito de funcionar, mas não quero te acostumar mal. 🙂

Lembrando que você pode fazer isso facilmente com JQuery. 

Suponha que você tenha o código HTML:

<pre class="lang-html">&lt;!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
	"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd"&gt;

&lt;html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en"&gt;
&lt;head&gt;
	&lt;meta http-equiv="Content-Type" content="text/html; charset=utf-8"/&gt;

	&lt;title&gt;Tableless.com.br&lt;/title&gt;
&lt;/head&gt;

&lt;body&gt;
	
&lt;div class="geral"&gt;
	&lt;div class="header"&gt;
		HEADER
	&lt;/div&gt;
	&lt;div class="aside fleft"&gt;
		ESQUERDA
	&lt;/div&gt;
	&lt;div class="aside fright"&gt;
		DIREITA
	&lt;/div&gt;
	&lt;div class="content"&gt;
		&lt;p&gt;
		Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin augue erat, ullamcorper pulvinar malesuada ultricies, mollis non magna. Curabitur quis nisi ut ligula ultricies gravida. Suspendisse elit justo, vulputate in facilisis sed, tristique id nisi. Maecenas risus quam, suscipit eu vehicula ut, ultricies in neque. Donec gravida tristique turpis ut interdum. Donec lacinia nisi id enim lacinia sit amet facilisis est ullamcorper. Curabitur ipsum libero, sollicitudin nec rhoncus quis, congue non ipsum. Etiam at eros dolor. Mauris non erat vitae leo faucibus fermentum. In consectetur, diam eget faucibus dignissim, urna justo pretium dui, nec eleifend neque velit vitae odio. Nam et tristique turpis. In dictum commodo sem ut dignissim. In convallis quam non tortor posuere sed ornare nulla pulvinar. Suspendisse placerat turpis in tortor rutrum nec mollis nulla posuere. Integer tellus est, rhoncus ut sagittis eget, mattis a velit. Vestibulum ante ipsum primis in faucibus orci luctus et ultrices posuere cubilia Curae; Quisque gravida posuere orci nec ornare. Donec elit nulla, aliquam eget cursus a, commodo sed odio.
		&lt;/p&gt;
		&lt;p&gt;
		Duis id metus enim, sed dignissim magna. Quisque dapibus pulvinar diam eget adipiscing. Ut aliquet ipsum quis lorem elementum lacinia. Vestibulum feugiat ultrices orci, vel sollicitudin nibh rutrum eu. In gravida tincidunt ornare. Aenean vestibulum leo eu orci egestas semper. Proin euismod dapibus tempor. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos himenaeos. Suspendisse rutrum purus eget lectus ultricies a consectetur ante laoreet. Phasellus ullamcorper gravida risus vitae convallis. Curabitur ante lorem, faucibus in tincidunt quis, ullamcorper at lectus. Fusce fermentum blandit varius. Donec a quam id massa bibendum commodo sit amet vel felis. Sed magna nibh, convallis nec dignissim non, vestibulum adipiscing ipsum. Mauris cursus fringilla tortor eu feugiat. Vivamus vestibulum dapibus justo, porttitor luctus nisi posuere at. Nunc mi elit, suscipit id venenatis at, suscipit nec purus. Donec malesuada fringilla tempor. Pellentesque vehicula diam a magna commodo sagittis. Nulla facilisi. 
		&lt;/p&gt;
	&lt;/div&gt;
	&lt;div class="footer"&gt;
		FOOTER
	&lt;/div&gt;
&lt;/div&gt;

&lt;/body&gt;
&lt;/html&gt;

</pre>

E o seguinte CSS:

<pre class="lang-css">*  {
	margin:0;
	padding:0;
}

html, body {height:100%;}

.geral {
	min-height:100%;
	position:relative;
	width:800px;
}

.footer {
	position:absolute;
	bottom:0;
	width:100%;
}

.content {overflow:hidden;}
.aside {width:200px;}
.fleft {float:left;}
.fright {float:right;}
</pre>

Na linha 6, você faz com que as tags body e html tenham 100% de altura. Isso fará com que o rodapé entenda que o limite dos dois elementos seja o final da janela do navegador.

Na linha 8, defino que a largura mínima do div GERAL, que é o div que envolve todo o site, seja de 100%. E defino um position: relative; para que o footer seja referenciado por ele.

Na linha 14, eu defino um position: absolute; e bottom:0; para footer, forçando sempre para o final do div.
  
Se houver pouco conteúdo o Rodapé fica lá embaixo, se houver muito, o rodapé desce junto com o conteúdo.

Funciona em IE7+ e em bons browsers.

Link para o arquivo de exemplo: [Footer fixo no Rodapé][1]

 [1]: http://tableless.com.br/uploads/2010/01/footer.html