---
title: 'HTML5: Elemento AUDIO'
author: Diego Eis
type: post
date: 2010-12-14
excerpt: A tag audio é suportada pela maioria dos browsers atuais. Ela representa um som ou um stream de audio e pode ser utilizada agora. Leia como.
url: /elemento-tag-audio/
tweetbackscheck:
  - 1356399030
shorturls:
  - 'a:3:{s:9:"permalink";s:42:"http://tableless.com.br/elemento-tag-audio";s:7:"tinyurl";s:26:"http://tinyurl.com/3wlgeym";s:4:"isgd";s:19:"http://is.gd/pDos7J";}'
twittercomments:
  - 'a:0:{}'
enclosure:
  - |
    |
        http://tableless.com.br/uploads/2010/12/LouisArmstrongAllHisStars-StruttinWithSomeBarbecue.mp3
        3418240
        audio/mpeg
        
  - |
    |
        http://tableless.com.br/uploads/2010/12/LouisArmstrongAllHisStars-StruttinWithSomeBarbecue.ogg
        5257958
        audio/ogg
        
dsq_thread_id: 503039824
categories:
  - Código
  - HTML5
  - Técnicas e Práticas
tags:
  - 2010
  - CSS3
  - html5
  - Na Prática
  - tableless
  - tutorial

---
O elemento `audio` do HTML5 representa um som ou um stream de áudio. Atributos como: `src, preload, autoplay, loop e controls` podem ser utilizados em todos elementos de media, como o elemento `audio`.

### Formatos suportados

Os formatos de audio suportados são:

<table class="reference" cellspacing="0" cellpadding="0" border="1" width="100%">
  <tr>
    <th width="20%" align="left">
      Formato
    </th>
    
    <th width="16%" align="left">
      IE 8
    </th>
    
    <th width="16%" align="left">
      Firefox 3.5
    </th>
    
    <th width="16%" align="left">
      Opera 10.5
    </th>
    
    <th width="16%" align="left">
      Chrome 3.0
    </th>
    
    <th width="16%" align="left">
      Safari 3.0
    </th>
  </tr>
  
  <tr>
    <td>
      Ogg Vorbis
    </td>
    
    <td>
      <span class="marked">Não</span>
    </td>
    
    <td>
      Sim
    </td>
    
    <td>
      Sim
    </td>
    
    <td>
      Sim
    </td>
    
    <td>
      <span class="marked">Não</span>
    </td>
  </tr>
  
  <tr>
    <td>
      MP3
    </td>
    
    <td>
      <span class="marked">Não</span>
    </td>
    
    <td>
      <span class="marked">Não</span>
    </td>
    
    <td>
      <span class="marked">Não</span>
    </td>
    
    <td>
      Sim
    </td>
    
    <td>
      Sim
    </td>
  </tr>
  
  <tr>
    <td>
      Wav
    </td>
    
    <td>
      <span class="marked">Não</span>
    </td>
    
    <td>
      Sim
    </td>
    
    <td>
      Sim
    </td>
    
    <td>
      <span class="marked">Não</span>
    </td>
    
    <td>
      Sim
    </td>
  </tr>
</table>

Como no caso dos vídeos, ainda é um problema termos um formato que funcione com sucesso em todos os browsers. Enquanto isso, para mantermos a compatibilidade precisamos servir diversos formatos. 

### Sintaxe

A sintaxe é muito simples:

<pre lang="HTML">&lt;audio src="http://tableless.com.br/uploads/2010/12/LouisArmstrongAllHisStars-StruttinWithSomeBarbecue.mp3" controls="controls">&lt;/audio>
</pre>

Colocando um conteúdo dentro da tag para que browsers que não suportam possam baixar este arquivo.

<pre lang="HTML" line="1">&lt;audio src="http://tableless.com.br/uploads/2010/12/LouisArmstrongAllHisStars-StruttinWithSomeBarbecue.mp3" controls="controls">
   Você pode <a href="http://www.publicdomain2ten.com/2010/09/louis-armstrong-all-his-stars-struttin-with-some-barbecue-mp3/">baixar essa música gratuitamente no Public Domain 2Ten.</a>
&lt;/audio>
</pre>

Suponha então que você tenha que servir dois tipos de formatos de audio para cobrir a maioria dos browsers:

<pre lang="HTML">&lt;audio controls="controls">
  &lt;source src="http://tableless.com.br/uploads/2010/12/LouisArmstrongAllHisStars-StruttinWithSomeBarbecue.ogg" type="audio/ogg" />
  &lt;source src="http://tableless.com.br/uploads/2010/12/LouisArmstrongAllHisStars-StruttinWithSomeBarbecue.mp3" type="audio/mpeg" />
   Você pode <a href="http://www.publicdomain2ten.com/2010/09/louis-armstrong-all-his-stars-struttin-with-some-barbecue-mp3/">baixar essa música gratuitamente no Public Domain 2Ten.</a>
&lt;/audio>
</pre>

Resultado:
  
<audio controls="controls"><source src="http://tableless.com.br/uploads/2010/12/LouisArmstrongAllHisStars-StruttinWithSomeBarbecue.ogg" type="audio/ogg" /><source src="http://tableless.com.br/uploads/2010/12/LouisArmstrongAllHisStars-StruttinWithSomeBarbecue.mp3" type="audio/mpeg" />Você pode [baixar essa música gratuitamente no Public Domain 2Ten.][1]</audio>

Se você entrar com o Internet Explorer, provavelmente ele mostrará a mensagem para baixar o arquivo que colocamos. 😉

### Os atributos possíveis

<table class="reference" cellspacing="0" cellpadding="0" border="1" width="100%">
  <tr>
    <th align="left" width="20%">
      Atributo
    </th>
    
    <th align="left" width="20%">
      Valor
    </th>
    
    <th align="left" width="50%">
      Descrição
    </th>
  </tr>
  
  <tr>
    <td>
      autoplay
    </td>
    
    <td>
      autoplay
    </td>
    
    <td>
      Define que o audio começará a ser tocado assim que ele estiver pronto.
    </td>
  </tr>
  
  <tr>
    <td>
      controls
    </td>
    
    <td>
      controls
    </td>
    
    <td>
      Os controles serão mostrados.
    </td>
  </tr>
  
  <tr>
    <td>
      loop
    </td>
    
    <td>
      loop
    </td>
    
    <td>
      Define que o audio começará a ser tocado novamente quando terminar.
    </td>
  </tr>
  
  <tr>
    <td>
      preload
    </td>
    
    <td>
      preload
    </td>
    
    <td>
      Define que o audio será carregado enquanto a página é lida. Esse atributo é ignorado caso o atributo autoplay estiver definido.
    </td>
  </tr>
  
  <tr>
    <td>
      src
    </td>
    
    <td>
      <i>url</i>
    </td>
    
    <td>
      URL do arquivo a ser tocado.
    </td>
  </tr>
</table>

Você tem algum controle sobre o player que aparece no browser com CSS. Testando aqui, customizamos largura, altura, colocamos float e position. Por natureza ele é um elemento de bloco. Isso acontece também com os elemento sde vídeo. A graça disso tudo é que tanto o elemento de vídeo quanto o elemento de audio são tratados como elementos do HTML e não como plugins. Isso nos dá essa flexibilidade de customização via CSS, facilitando muito as coisas.

O elemento `audio` do HTML5 representa um som ou um stream de áudio. Atributos como: `src, preload, autoplay, loop e controls` podem ser utilizados em todos elementos de media, como o elemento `audio`.

### Formatos suportados

Os formatos de audio suportados são:

<table class="reference" cellspacing="0" cellpadding="0" border="1" width="100%">
  <tr>
    <th width="20%" align="left">
      Formato
    </th>
    
    <th width="16%" align="left">
      IE 8
    </th>
    
    <th width="16%" align="left">
      Firefox 3.5
    </th>
    
    <th width="16%" align="left">
      Opera 10.5
    </th>
    
    <th width="16%" align="left">
      Chrome 3.0
    </th>
    
    <th width="16%" align="left">
      Safari 3.0
    </th>
  </tr>
  
  <tr>
    <td>
      Ogg Vorbis
    </td>
    
    <td>
      <span class="marked">Não</span>
    </td>
    
    <td>
      Sim
    </td>
    
    <td>
      Sim
    </td>
    
    <td>
      Sim
    </td>
    
    <td>
      <span class="marked">Não</span>
    </td>
  </tr>
  
  <tr>
    <td>
      MP3
    </td>
    
    <td>
      <span class="marked">Não</span>
    </td>
    
    <td>
      <span class="marked">Não</span>
    </td>
    
    <td>
      <span class="marked">Não</span>
    </td>
    
    <td>
      Sim
    </td>
    
    <td>
      Sim
    </td>
  </tr>
  
  <tr>
    <td>
      Wav
    </td>
    
    <td>
      <span class="marked">Não</span>
    </td>
    
    <td>
      Sim
    </td>
    
    <td>
      Sim
    </td>
    
    <td>
      <span class="marked">Não</span>
    </td>
    
    <td>
      Sim
    </td>
  </tr>
</table>

Como no caso dos vídeos, ainda é um problema termos um formato que funcione com sucesso em todos os browsers. Enquanto isso, para mantermos a compatibilidade precisamos servir diversos formatos. 

### Sintaxe

A sintaxe é muito simples:

<pre lang="HTML">&lt;audio src="http://tableless.com.br/uploads/2010/12/LouisArmstrongAllHisStars-StruttinWithSomeBarbecue.mp3" controls>&lt;/audio>
</pre>

Colocando um conteúdo dentro da tag para que browsers que não suportam possam baixar este arquivo.

<pre lang="HTML">&lt;audio src="http://tableless.com.br/uploads/2010/12/LouisArmstrongAllHisStars-StruttinWithSomeBarbecue.mp3" controls="controls">
   Você pode <a href="http://www.publicdomain2ten.com/2010/09/louis-armstrong-all-his-stars-struttin-with-some-barbecue-mp3/">baixar essa música gratuitamente no Public Domain 2Ten.</a>
&lt;/audio>
</pre>

Suponha então que você tenha que servir dois tipos de formatos de audio para cobrir a maioria dos browsers:

<pre lang="HTML">&lt;audio controls>
  &lt;source src="http://tableless.com.br/uploads/2010/12/LouisArmstrongAllHisStars-StruttinWithSomeBarbecue.ogg" type="audio/ogg" />
  &lt;source src="http://tableless.com.br/uploads/2010/12/LouisArmstrongAllHisStars-StruttinWithSomeBarbecue.mp3" type="audio/mpeg" />
   Você pode <a href="http://www.publicdomain2ten.com/2010/09/louis-armstrong-all-his-stars-struttin-with-some-barbecue-mp3/">baixar essa música gratuitamente no Public Domain 2Ten.</a>
&lt;/audio>
</pre>

Resultado:
  
<audio controls><source src="http://tableless.com.br/uploads/2010/12/LouisArmstrongAllHisStars-StruttinWithSomeBarbecue.ogg" type="audio/ogg" /><source src="http://tableless.com.br/uploads/2010/12/LouisArmstrongAllHisStars-StruttinWithSomeBarbecue.mp3" type="audio/mpeg" />Você pode [baixar essa música gratuitamente no Public Domain 2Ten.][1]</audio>

Se você entrar com o Internet Explorer, provavelmente ele mostrará a mensagem para baixar o arquivo que colocamos. 😉

### Os atributos possíveis

<table class="reference" cellspacing="0" cellpadding="0" border="1" width="100%">
  <tr>
    <th align="left" width="20%">
      Atributo
    </th>
    
    <th align="left" width="20%">
      Valor
    </th>
    
    <th align="left" width="50%">
      Descrição
    </th>
  </tr>
  
  <tr>
    <td>
      autoplay
    </td>
    
    <td>
      autoplay
    </td>
    
    <td>
      Define que o audio começará a ser tocado assim que ele estiver pronto.
    </td>
  </tr>
  
  <tr>
    <td>
      controls
    </td>
    
    <td>
      controls
    </td>
    
    <td>
      Os controles serão mostrados.
    </td>
  </tr>
  
  <tr>
    <td>
      loop
    </td>
    
    <td>
      loop
    </td>
    
    <td>
      Define que o audio começará a ser tocado novamente quando terminar.
    </td>
  </tr>
  
  <tr>
    <td>
      preload
    </td>
    
    <td>
      preload
    </td>
    
    <td>
      Define que o audio será carregado enquanto a página é lida. Esse atributo é ignorado caso o atributo autoplay estiver definido.
    </td>
  </tr>
  
  <tr>
    <td>
      src
    </td>
    
    <td>
      <i>url</i>
    </td>
    
    <td>
      URL do arquivo a ser tocado.
    </td>
  </tr>
</table>

Você tem algum controle sobre o player que aparece no browser com CSS. Testando aqui, customizamos largura, altura, colocamos float e position. Por natureza ele é um elemento de bloco. Isso acontece também com os elemento sde vídeo. A graça disso tudo é que tanto o elemento de vídeo quanto o elemento de audio são tratados como elementos do HTML e não como plugins. Isso nos dá essa flexibilidade de customização via CSS, facilitando muito as coisas.

### Caminho das pedras para customizar

Você pode criar seu próprio player se preferir. Você pode manipular os controles de som como PLAY, PAUSE, VOLUME com outros elementos do HTML. Isso facilita a customização do player caso você não queira utilizar o player padrão do browser. Se souber um pouco de Javascript, você já entenderá o que pode ser feito com o código abaixo.

<pre lang="HTML"><div class="controlsplayer">
  <button onclick="javascript: document.getElementById('player').play()">Play</button>
    <button onclick="javascript: document.getElementById('player').pause()">Pause</button>
    <button onclick="javascript: document.getElementById('player').volume += 0.1">Aumenta Volume</button>
    <button onclick="javascript: document.getElementById('player').volume -= 0.1">Diminui Volume</button>
  
</div>
</pre>

Teste abaixo:

<audio id="player" controls><source src="http://tableless.com.br/uploads/2010/12/LouisArmstrongAllHisStars-StruttinWithSomeBarbecue.ogg" type="audio/ogg" /><source src="http://tableless.com.br/uploads/2010/12/LouisArmstrongAllHisStars-StruttinWithSomeBarbecue.mp3" type="audio/mpeg" />Você pode [baixar essa música gratuitamente no Public Domain 2Ten.][1]</audio>

<div class="controlsplayer" style="padding:20px;">
  <button onclick="javascript: document.getElementById('player').play()">Play</button><br /> <button onclick="javascript: document.getElementById('player').pause()">Pause</button><br /> <button onclick="javascript: document.getElementById('player').volume += 0.1">Aumenta Volume</button><br /> <button onclick="javascript: document.getElementById('player').volume -= 0.1">Diminui Volume</button>
</div>

Customizando estes botões com CSS e aprimorando o Javascript, você consegue fazer um player bem desenhado e que funciona em diversas plataformas.

 [1]: http://www.publicdomain2ten.com/2010/09/louis-armstrong-all-his-stars-struttin-with-some-barbecue-mp3/