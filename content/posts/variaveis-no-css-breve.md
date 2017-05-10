---
title: Variáveis no CSS – Breve
author: Diego Eis
type: post
date: 2012-06-18
excerpt: Variáveis no CSS, em breve, perto de você.
url: /variaveis-no-css-breve/
tweetbackscheck:
  - 1356397249
shorturls:
  - 'a:3:{s:9:"permalink";s:47:"http://tableless.com.br/variaveis-no-css-breve/";s:7:"tinyurl";s:26:"http://tinyurl.com/7pmtt7n";s:4:"isgd";s:19:"http://is.gd/XFV5ds";}'
twittercomments:
  - 'a:20:{i:214690961366855680;s:7:"retweet";i:217596171898720256;s:7:"retweet";i:217595628048486400;s:7:"retweet";i:217593919465205761;s:7:"retweet";i:214801979539599360;s:7:"retweet";i:214750053301104640;s:7:"retweet";i:214709153980104704;s:7:"retweet";i:214703607709306882;s:7:"retweet";i:214701474750529536;s:7:"retweet";i:214700639077400576;s:7:"retweet";i:214694115584122882;s:7:"retweet";i:214692824459911169;s:7:"retweet";i:214690830915604480;s:7:"retweet";i:214690383437889536;s:7:"retweet";i:214690121201631233;s:7:"retweet";i:214689960467505152;s:7:"retweet";i:214689755596734464;s:7:"retweet";i:228108059120119808;s:7:"retweet";i:228099654582157313;s:7:"retweet";i:228098743646437376;s:7:"retweet";}'
tweetcount:
  - 94
dsq_thread_id: 731020812
categories:
  - CSS
  - Notícias
tags:
  - CSS
  - variaveis
  - w3c
  - webkit

---
Escrever variáveis no CSS é uma das features mais esperadas nesses últimos tempos. [Préprocessadores como SASS e LESS][1] já disponibilizam este recurso, mas ter essas facilidades no próprio CSS, sem a necessidade de utilizar qualquer outra ferramenta é muito mais do que útil.

O WebKit tem trabalhado nesse assunto [utilizando a documentação do W3C][2]. E provavelmente já teremos daqui um tempo a possibilidade de utilizar variáveis em browsers que suportam webkit. Se os outros browsers andarem rápido, como o Webkit, muito em breve teremos full-support em todos os browsers, obviamente, browsers antigos ficarão fora dessa. E quando eu digo antigo, incluo até o IE9 e talvez o IE10 e também outros browsers conhecidos. Mesmo assim, com menos risco, já que os outros browsers tem auto-update.

### Sintaxe

A sintaxe é simples, embora eu não tenha gostado.

[cc lang=&#8221;css&#8221;]
  
:root {
      
var-title-color: green;
  
}

h1 { background-color: var(title-color); }
  
[/cc]

Eu começaria tirando o **&#8211;** (traço) logo depois da palavra **var**. Assim fica parecido com Javascript.
  
Você pode nomes juntos também, sem problemas.

[cc lang=&#8221;css&#8221;]
  
:root {
      
var-FontSizeArticle: 13px;
  
}

article { font-size: var(FontSizeArticle); }
  
[/cc]

O Webkit tem dado [alguns exemplos de código aqui][3]. [A documentação][2] ainda está bem no começo. Mesmo assim, do jeito que as coisas estão andando rápidas, variáveis no CSS estarão presentes na casa de toda família em breve.

 [1]: http://tableless.com.br/estruturacao-de-client-side-preprocessadores-framewoks-e-bibliotecas-parte-1/ "Estruturação de Client-side – Parte 1: Préprocessadores, Framewoks e Bibliotecas"
 [2]: http://www.w3.org/TR/css-variables/
 [3]: http://trac.webkit.org/browser/trunk/LayoutTests/fast/css/variables