---
title: Retina.js – Imagens para telas retina
author: Diego Eis
type: post
date: 2012-07-16
excerpt: Mostre imagens de alta qualidade em dispositivos retina sem muito trabalho.
url: /retina-js-imagens-para-telas-retina/
tweetbackscheck:
  - 1355473793
shorturls:
  - 'a:3:{s:9:"permalink";s:60:"http://tableless.com.br/retina-js-imagens-para-telas-retina/";s:7:"tinyurl";s:26:"http://tinyurl.com/85yg99h";s:4:"isgd";s:19:"http://is.gd/sYPi0O";}'
twittercomments:
  - 'a:17:{i:224920258115411968;s:7:"retweet";i:224914519267348482;s:7:"retweet";i:224913457210859520;s:7:"retweet";i:224912992326778881;s:7:"retweet";i:224846900199821313;s:7:"retweet";i:226363114134843392;s:7:"retweet";i:226314926602477569;s:7:"retweet";i:226293444132347905;s:7:"retweet";i:230121405465886721;s:7:"retweet";i:230085185675333633;s:7:"retweet";i:228572990877609985;s:7:"retweet";i:228570606738735104;s:7:"retweet";i:228570345509113857;s:7:"retweet";i:250310127905812480;s:7:"retweet";i:250310099703328768;s:7:"retweet";i:261614456340107264;s:7:"retweet";i:271367185325228032;s:7:"retweet";}'
tweetcount:
  - 36
dsq_thread_id: 767503739
categories:
  - HTML
  - JavaScript
tags:
  - 2012
  - JavaScript

---
Nós já falamos sobre como as [imagens de seu website podem aparecer em dispositivos que utilizam tela retina ou com telas HD][1]. Até hoje não havia nenhuma alternativa de verdade para você poder fazer um chaveamento automático, até a chegada do [Retina.js][2].

O Retina.js é um script em javascript que te ajuda a entregar as imagens corretas para os dispositivos corretos sem muita dor de cabeça.
  
Quando os usuários carregam a página, o retina.js checa se há uma versão de alta resolução para cada imagem do site no seu servidor. Se houver uma variação da imagem em alta resolução, o script irá mostrá-la.

Por exempo, se você tem uma imagem na sua página assim:

<pre class="lang-html">&lt;img src="img/destaque.png"&gt;
</pre>

O script procura no servidor se há uma alternativa dessa imagem no mesmo caminho da imagem original, assim:

<pre class="lang-html">&lt;img src="img/destaque@2x.png"&gt;
</pre>

Logo, você só precisa criar uma imagem em alta qualidade, colocar o nome dessa imagem igual a da imagem original (de baixa qualidade) seguido do &#8220;**@2x**&#8220;.

Para instalar é simples e indolor.
  
Basta colocar a chamada do script lá embaixo, antes de fechar o body e pronto.

<pre class="lang-html">&lt;script type="text/javascript" src="retina.js"&gt;&lt;/script&gt; 
</pre>

Com certeza podia ser incluído na Modernizr. 🙂

Leia mais e faça o [download do script aqui][2].

 [1]: http://tableless.com.br/qualidade-de-imagens-e-densidade-de-pixels/
 [2]: http://retinajs.com/