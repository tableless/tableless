---
title: Lançado Firefox 3.5
author: Diego Eis
type: post
date: 2009-07-01
excerpt: O Firefox 3.5 foi lançado e está com uma série de modificações, principalmente atualizações para facilitar o desenvolvimento com HTML e CSS. Baixe, teste e compartilhe!
url: /lancado-firefox-3-5/
aktt_notify_twitter:
  - yes
aktt_tweeted:
  - 1
tweetbackscheck:
  - 1356455438
shorturls:
  - 'a:3:{s:9:"permalink";s:43:"http://tableless.com.br/lancado-firefox-3-5";s:7:"tinyurl";s:26:"http://tinyurl.com/42cvtal";s:4:"isgd";s:19:"http://is.gd/umV7VH";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 503039087
categories:
  - Browsers
  - CSS
  - HTML
tags:
  - Browsers
  - CSS
  - firefox
  - html
  - html5

---
A Mozilla acaba de lançar a versão 3.5 do Firefox. Esta versão traz uma [série de atualizações interessantes][1] tanto para usuários quanto para nós desenvolvedores. Fiz um resumo de algumas novas características logo abaixo. Irei fazer alguns posts posteriores explicando mais detalhadamente as propriedades e outras funcionalidades.

### Elementos de Áudio e Vídeo do HTML5

A adoção de algumas características do HTML5 está se tornando cada vez mais frequente nos novos browsers. Isso é bom porque não precisaremos esperar tanto para que todos os browsers tenham suporte a grande parte das características do HTML5, Javascript e CSS3.

No Firefox 3.5, é nativo o suporte aos elementos de áudio e vídeo do HTML 5. Isso inclui suporte para encodes de vídeo Ogg Theora e Vorbis para áudio. O código para incluir um vídeo é basicamente este:

<pre lang="html" line="1">&lt;video src="http://v2v.cc/~j/theora_testsuite/320x240.ogg" autoplay>  
Atenção: Seu browser não suporta esse formato.
&lt;/video>  
</pre>

A mensagem que está entre a tag VIDEO é mostrada caso o browser não reconheça o formato de vídeo.
  
Caso o browser não abra o formato de vídeo OGG, você pode indicar para que ele abra um outro formato automaticamente, veja o código:

<pre lang="html" line="1">&lt;video autoplay>  
  &lt;source src="video.ogg" type="video/ogg">  
  &lt;source src="video.mov">  
  Atenção: Seu browser não suporta esse formato.
&lt;/video> 
</pre>

### @font-face &#8211; Suporte a fontes externas

A **[propriedade @font-face][2]** serve para que apliquemos fontes aos sites que não sejam default no computador do visitante. Ele era apenas suportado em browsers com motores Webkit, agora o Firefox trouxe essa possibilidade, aumentando o número de usuários que suportam essa característica. 

A sintaxe:

<pre lang="css" line="1">@font-face {
  font-family: "Bitstream Vera Serif Bold";
  src: url("http://developer.mozilla.org/@api/deki/files/2934/=VeraSeBd.ttf");
}
    
body { font-family: "Bitstream Vera Serif Bold", serif }
</pre>

Você define primeiramente a fonte que irá ser utilizada, indicando seu source para que o browser possa localizá-la e assim fazer o download para ser aplicada. Feito isso, você pode utilizá-la nos elementos normalmente, como você faz com as fontes default.

Já falamos sobre [propriedade @font-face][2] aqui.

### Opacity

Agora não precisamos mais utilizar o prefixo **-moz-** antes da propriedade OPACITY. Antes utilizávamos para testes apenas. Agora o pessoal do Firefox tirou esse prefixo para favorecer a propriedade OPACITY, sem prefixo. Eu nunca gostei destes prefixos, mesmo assim, essas coisas evitam erros de funcionalidades entre os browsers, já que um pode interpretar de forma diferente propriedades que ainda não foram realmente lançadas. 

A propriedade **opacity** modifica a opacidade dos elementos, onde o valor 0 é totalmente transparente, e 1 é totalmente visível.

<pre lang="css" line="1">div {
   opacity: 0.3;
   border: 3px solid black;
   background: orange;
}
</pre>

### E um bando de outras atualizações

E há uma série de outras atualizações interessantes para os desenvolvedores, veja uma [lista completa aqui][3].

Daqui pra frente os browsers irão forçar ainda mais a evolução do desenvolvimento web em todos os sentidos. Eles estão cada vez mais implementando coisas novas, que se dependessem do mercado, iriam começar a serem utilizadas daqui a alguns anos. Graças a esta concorrência entre os navegadores, essas novas novidades estão sendo suportadas cada vez mais cedo e podemos começar a utilizar para melhorar os projetos a partir de agora. 

[Baixe o Firefox 3.5 aqui.][4]

 [1]: http://www.mozilla.com/en-US/firefox/performance/
 [2]: http://tableless.com.br/font-face
 [3]: https://developer.mozilla.org/En/Firefox_3.5_for_developers
 [4]: http://www.mozilla.com/en-US/firefox/upgrade.html