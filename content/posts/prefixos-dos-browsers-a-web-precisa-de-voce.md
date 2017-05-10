---
title: 'Prefixos dos browsers: A web precisa de você'
author: Diego Eis
type: post
date: 2012-02-13
excerpt: Por uma web mais livre.
url: /prefixos-dos-browsers-a-web-precisa-de-voce/
tweetbackscheck:
  - 1356436655
shorturls:
  - 'a:3:{s:9:"permalink";s:68:"http://tableless.com.br/prefixos-dos-browsers-a-web-precisa-de-voce/";s:7:"tinyurl";s:26:"http://tinyurl.com/6qkql7z";s:4:"isgd";s:19:"http://is.gd/GkktW1";}'
twittercomments:
  - 'a:26:{i:169043082690564097;s:7:"retweet";i:169044650131337216;s:7:"retweet";i:169191951898390528;s:7:"retweet";i:169088392645181441;s:7:"retweet";i:169086105277317120;s:7:"retweet";i:169065048008962050;s:7:"retweet";i:169064943512068097;s:7:"retweet";i:169062792782036992;s:7:"retweet";i:169061065546670080;s:7:"retweet";i:169056063553945600;s:7:"retweet";i:169054519085371392;s:7:"retweet";i:169052757653856257;s:7:"retweet";i:169050512895909888;s:7:"retweet";i:169047362646450177;s:7:"retweet";i:169046449844264960;s:7:"retweet";i:169044839017611266;s:7:"retweet";i:169044263722696704;s:7:"retweet";i:169043997367607296;s:7:"retweet";i:169043684875190272;s:7:"retweet";i:169043156912979968;s:7:"retweet";i:169043046590197760;s:7:"retweet";i:172705389035520000;s:7:"retweet";i:172700988640202752;s:7:"retweet";i:172700927369805825;s:7:"retweet";i:172698204171808768;s:7:"retweet";i:172698076593668096;s:7:"retweet";}'
tweetcount:
  - 128
dsq_thread_id: 574353149
categories:
  - Mercado e Comportamento
  - Notícias
  - Tecnologia e Tendências
tags:
  - 2012
  - Browsers
  - CSS

---
Desenvolver apenas para um único browser não é legal. Isso já aconteceu conosco quando o Internet Explorer ganhou a batalha contra a Netscape. Era comum encontrar sites com o aviso &#8220;Este site funciona apenas em Internet Explorer&#8221;. Este é o motivo pelo qual muitos ainda estão presos ao IE com um legado difícil. Hoje você tem plena certeza de que é necessário manter a compatibilidade crossbrowser dos projetos. 

A combinação da grande variação de browsers no mercado com as mais as novas features do CSS resultam em problemas de compatibilidade. Você quer utilizar uma feature que ainda está sendo estudada, e que somente o Firefox, por exemplo, suporta. Se você simplesmente utilizar a propriedade no seu CSS, os browsers que não suportam essa propriedade, ou que suportam mas com uma sintaxe diferente, podem dar problemas. Aí é que entra os prefixos de browsers.

O prefixo é muito útil para podermos experimentar features que ainda estão sendo estudadas e que são rascunhos nos documentos do W3C. Prefixos são úteis por que nos direcionam para um caminho seguro sob as inconsistências entre propriedades e browsers. 

### Como utilizar um prefixo

Não se assuste, se você utilizará uma propriedade de CSS que ainda está sendo planejada mas ainda assim quer aplicar em seu projeto para que os usuários de novos browsers possam usufruir com uma melhor experiência ao acessar seu site, seu código pode ficar um pouco confuso. Por isso, organize-se melhor ao decidir quais propriedades você gostará de experimentar.
  
Para exemplo vamos utilizar a propriedade border-radius. Se quisessemos fazer uma borda arredondada com 10px, faríamos assim:

<pre class="lang-css">div {
   -webkit-border-radius: 10px;
   -moz-border-radius: 10px;
   -ms-border-radius: 10px;
   -o-border-radius: 10px;
   border-radius: 10px;
}
</pre>

Note que colocamos por último a propriedade verdadeira, sem nenhum prefixo, essa propriedade cobrirá os browsers que não precisam da utilização de prefixos para renderizar a propriedade, por exemplo o Opera e o Internet Explorer 9.

### O problema

Atualmente estamos beirando a mesma situação citada no início do artigo. O Firefox, Opera e Microsoft estão pensando em suportar o prefixo **-webkit-**. O problema é que os desenvolvedores estão utilizando em seus projetos apenas o prefixo **-webkit-** para algumas propriedades do CSS3. Isto é muito ruim.

Se todos os browsers suportarem um mesmo prefixo o mercado será &#8220;controlado&#8221; por apenas um fabricante de browser que poderá ditar as regras sobre quais propriedades do CSS poderão ser implementadas primeiro. Ok, ok, meu sonho era que um browser sob o engine **webkit** dominasse mesmo. Mas isso foi quando o IE era o browser mais utilizado e a Microsoft não havia aberto os olhos ainda. Mas concorrência é ótimo em qualquer lugar, até na web.

O pessoal está conversando sobre algumas possibilidades de soluções. Uma interessante e na minha opinião mais inteligente, é a criação de um prefixo neutro, utilizado por todos os browsers para indicar novas features. Algo como -alpha- ou -beta- e assim por diante.

Todos os grandes nomes da web estão se mobilizando para que a web não fique em volta de um único browser. Tenha em mente que o pessoal do **-webkit-** não está fazendo nada de errado, nós estamos.

**Daniel Glazman**, Co-chairman do W3C CSS Working Group escreveu um post, muito preocupado e chamando toda a comunidade de desenvolvedores a adequarem seus sites e a entenderem o grande problema que isso pode ser tornar. Veja uma parte do post:

> Without your help, without a strong reaction, this can lead to one thing only and we&#8217;re dangerously not far from there: other browsers will start supporting/implementing themselves the -webkit-* prefix, turning one single implementation into a new world-wide standard. It will turn a market share into a de facto standard, a single implementation into a world-wide monopoly. Again. It will kill our standardization process. That&#8217;s not a question of if, that&#8217;s a question of when.

Veja o [post completo aqui][1].

O [Web Standards Project também se mobilizou][2].

E aí? Vai mudar sua atitude? O que você pensa sobre isso?
  
Como você pode ajudar? 

[Assine essa petição][3] para os fabricantes de browsers não suportarem o prefixo webkit e espalhe para seus colegas a notícia. E claro, ao usar os prefixos para os browsers, utilize todos e não apenas um.

<small><a href="http://carrosantigos.wordpress.com/2011/07/25/freedom-riders-i-stand-among-heroes/">Foto do post</a></small>

 [1]: http://www.glazman.org/weblog/dotclear/index.php?trackback/5454
 [2]: http://bit.ly/x9LxGx
 [3]: http://www.change.org/petitions/microsoft-mozilla-opera-dont-make-webkit-prefixes-a-de-facto-standard