---
title: Efeito cascata, herança e especificidade do CSS
author: Diego Eis
type: post
date: 2009-07-21
excerpt: O efeito cascata do CSS é controlado pela especificidade e pela herança das propriedades.
url: /efeito-cascata-e-especificidade-do-css/
aktt_notify_twitter:
  - no
tweetbackscheck:
  - 1356387792
shorturls:
  - 'a:3:{s:9:"permalink";s:62:"http://tableless.com.br/efeito-cascata-e-especificidade-do-css";s:7:"tinyurl";s:26:"http://tinyurl.com/43gkch5";s:4:"isgd";s:19:"http://is.gd/DTTZWt";}'
twittercomments:
  - 'a:3:{i:165491705905283073;s:7:"retweet";i:165484399696162816;s:7:"retweet";i:165483793149464576;s:7:"retweet";}'
tweetcount:
  - 5
dsq_thread_id: 503039185
categories:
  - CSS
  - Técnicas e Práticas
tags:
  - 2009
  - CSS
  - desenvolvimento web
  - Na Prática
  - tecnicascss

---
#### Herança

Existem algumas propriedades do CSS que quando aplicadas aos &#8220;elementos pais&#8221;, os &#8220;elementos filhos&#8221; herdam a característica aplicada no pai. Um exemplo disso é a propriedade **color**. Quando aplicamos a propriedade **color** em um elemento **div**, o texto dos elementos contidos no **div** são coloridos de acordo com a propriedade.

<pre class="lang-css">div {
   color: green;
}
</pre>

O texto que há dentro deste **div** irá ter a cor verde, independente se este texto está &#8220;solto&#8221; dentro do **div** ou se ele está dentro de um parágrafo, por exemplo. Ou seja, os filhos herdaram o resultado desta propriedade. A mesma coisa acontece para, por exemplo, a propriedade **font-size**.

Há também as propriedades não herdadas pelos &#8220;filhos&#8221;. Estas propriedades geralmente são propriedades referentes a formatação da caixa, como por exemplo a propriedade **width**, **height**, **margin**, **padding** e assim por diante.

Essa herança é responsável por uma parte da cascata. É aí que está uma das primeiras vantanges de se utilizar o CSS no desenvolvimento com padrões. A vantagem da herança é exatamente podermos modificar poucas linhas do CSS para fazer alterações no site inteiro, sem ter que caçar elemento por elemento e modificando suas propriedades.

A herança é largamente utilizada em frameworks de CSS ou até mesmo em técnicas para que a customização de layouts seja explorada de forma automática ou manual pelo cliente, como homes de portais, e-commerce etc. Assim, o controle fica mais genérico, e é aí que entra a especificidade do CSS para controlar o detalhe.

##### O valor INHERIT

O valor inherit é utilizada em propriedades destinadas aos elementos filhos. Suponha que você tem um elemento **div**. Este elemento **div** tem uma borda e você quer que seus filhos tenham a mesma borda. Veja o código:

<pre class="lang-css"><div id="pai">
  <div>
    um filho
  </div>
    
  
  <div>
    outro filho
  </div>
  
</div>
</pre>

No CSS, o normal seria fazer isso:

<pre class="lang-css">div#pai {
  border: 2px solid black;
}

div#pai div {
  border: 2px solid black;
}
</pre>

Se você quisesse modificar a borda do pai e mesmo assim manter a borda do filho, teria que fazer das alterações no código. O valor **inherit** serve para que o filho sempre herde um determinado valor de uma determinada propriedade do pai. Quando o valor do pai muda, o valor do filho também. Veja o código e o [#### Herança

Existem algumas propriedades do CSS que quando aplicadas aos &#8220;elementos pais&#8221;, os &#8220;elementos filhos&#8221; herdam a característica aplicada no pai. Um exemplo disso é a propriedade **color**. Quando aplicamos a propriedade **color** em um elemento **div**, o texto dos elementos contidos no **div** são coloridos de acordo com a propriedade.

<pre class="lang-css">div {
   color: green;
}
</pre>

O texto que há dentro deste **div** irá ter a cor verde, independente se este texto está &#8220;solto&#8221; dentro do **div** ou se ele está dentro de um parágrafo, por exemplo. Ou seja, os filhos herdaram o resultado desta propriedade. A mesma coisa acontece para, por exemplo, a propriedade **font-size**.

Há também as propriedades não herdadas pelos &#8220;filhos&#8221;. Estas propriedades geralmente são propriedades referentes a formatação da caixa, como por exemplo a propriedade **width**, **height**, **margin**, **padding** e assim por diante.

Essa herança é responsável por uma parte da cascata. É aí que está uma das primeiras vantanges de se utilizar o CSS no desenvolvimento com padrões. A vantagem da herança é exatamente podermos modificar poucas linhas do CSS para fazer alterações no site inteiro, sem ter que caçar elemento por elemento e modificando suas propriedades.

A herança é largamente utilizada em frameworks de CSS ou até mesmo em técnicas para que a customização de layouts seja explorada de forma automática ou manual pelo cliente, como homes de portais, e-commerce etc. Assim, o controle fica mais genérico, e é aí que entra a especificidade do CSS para controlar o detalhe.

##### O valor INHERIT

O valor inherit é utilizada em propriedades destinadas aos elementos filhos. Suponha que você tem um elemento **div**. Este elemento **div** tem uma borda e você quer que seus filhos tenham a mesma borda. Veja o código:

<pre class="lang-css"><div id="pai">
  <div>
    um filho
  </div>
    
  
  <div>
    outro filho
  </div>
  
</div>
</pre>

No CSS, o normal seria fazer isso:

<pre class="lang-css">div#pai {
  border: 2px solid black;
}

div#pai div {
  border: 2px solid black;
}
</pre>

Se você quisesse modificar a borda do pai e mesmo assim manter a borda do filho, teria que fazer das alterações no código. O valor **inherit** serve para que o filho sempre herde um determinado valor de uma determinada propriedade do pai. Quando o valor do pai muda, o valor do filho também. Veja o código e o][1] 

<pre class="lang-css">div#pai {
  border: 2px solid black;
}

div#pai div {
  border: inherit;
}
</pre>

#### Especificidade

A especificidade define os detalhes. Quando você define no **body** as propriedades **font-family**, **font-size**, essas propriedades são herdadas por toda árvore de elementos do documento. Isso tráz uma uniformidade para o texto, mas nem todos os elementos terão esse valor genérico de **font**, logo você terá que ser mais específico e definir valores diferentes de font para estes elementos. É aí que a mágica acontece.

Suponha que você tenha o seguinte código:

<pre class="lang-html">&lt;div class="content"&gt;
   &lt;p&gt;
        Vivamus in leo lacus. &lt;em&gt;Nam condimentum viverra odio&lt;/em&gt;, non molestie orci commodo sit amet. &lt;strong&gt;&lt;em&gt;Proin aliquet leo eu&lt;/em&gt;&lt;/strong&gt; ipsum adipiscing tristique vestibulum nunc gravida. In porta dignissim enim sit amet vulputate. Quisque lacinia malesuada convallis. Sed sit amet orci non lacus sollicitudin pellentesque. 
   &lt;/p&gt;
&lt;/div&gt;
   &lt;p&gt;
        Vivamus in leo lacus. &lt;em&gt;Nam condimentum viverra odio&lt;/em&gt;, non molestie orci commodo sit amet. &lt;strong&gt;&lt;em&gt;Proin aliquet leo eu&lt;/em&gt;&lt;/strong&gt; ipsum adipiscing tristique vestibulum nunc gravida. In porta dignissim enim sit amet vulputate. Quisque lacinia malesuada convallis. Sed sit amet orci non lacus sollicitudin pellentesque. 
   &lt;/p&gt;
</pre>

E também o código CSS:

<pre class="lang-css">em {
   background: red;
}
</pre>

Definimos no código acima que os elementos **em** terão o **background** vermelho. Isso irá capturar os 4 elementos **em** que colocamos no HTML. Correto? Ótimo. Estamos sendo bem genéricos aqui. Ele irá capturar todos os elementos **em**, não importa onde ele esteja. Vamos analisar outro código CSS:

<pre class="lang-css">em {
   background: red;
}

div p em {
   background: green;
}
</pre>

Já mudamos toda a história com este seletor. Queremos dizer que apenas os **em** que estão dentro de **p** e que por sua vez estão dentro de um **div** terão o **background** verde. Deixamos a regra mais específica excluindo todos os elementos **em** que estão fora do **div**. Os **em** que estão fora do **div** continuam com o **background** vermelho.

No caso acima, a ordem não altera o resultado da renderização. O seletor mais específico sempre é o que vai funcionar.

Essa explicação é bem básica. Contudo, entendendo como ela funciona, você sabe o que acontece com seletores mais complexos.

#### O valor !important

A especificidade apresenta muitos problemas quando a equipe é grande e o código CSS está gigante. Você tenta fazer uma alteração em um determinado objeto, e nada funciona. Isso acontece porque alguém já definiu um seletor mais específico que o seu e definiu um valor diferente para sua propriedade, e isso te impede de fazer a alteração que precisa. Essa seria uma cena clássica, mas há outros cenários cujo o uso do valor **!important**.
  
O **!important** indica que aquela propriedade sempre será a principal, e que nunca será substituída mesmo que o seletor seja mais complexo. Veja:

<pre class="lang-css">p {
   color: black;
}

div p {
   color: red;
}
</pre>

No código acima, o parágrafo terá a cor vermelha por conta do seletor **div p** ser mais específico. 

<pre class="lang-css">p {
   color: black !important;
}

div p {
   color: red;
}
</pre>

Agora, mesmo o seletor **div p** sendo mais específico, ele não controlará o elemento. O **!important** está jogando toda a relevancia para o **color: black;**.
  
Use com cuidado. Se você colocar muitos **!important** no seu código, a utilidade deste valor se perderá. [Veja o exemplo][2].

 [1]: http://tableless.com.br/uploads/2009/07/inherit.html "exemplo do valor inherit do CSS"
 [2]: http://tableless.com.br/uploads/2009/07/important.html