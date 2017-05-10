---
title: Microdados do HTML5
author: Diego Eis
type: post
date: 2012-09-28
excerpt: Microdados dando mais significado à informação.
url: /microdados-do-html5/
tweetbackscheck:
  - 1356399447
dsq_thread_id: 862914570
shorturls:
  - 'a:3:{s:9:"permalink";s:44:"http://tableless.com.br/microdados-do-html5/";s:7:"tinyurl";s:26:"http://tinyurl.com/8j3peck";s:4:"isgd";s:19:"http://is.gd/0OEuse";}'
twittercomments:
  - 'a:14:{i:251689744457687042;s:7:"retweet";i:251685389151133696;s:7:"retweet";i:251682302214684672;s:7:"retweet";i:251676492902301696;s:7:"retweet";i:251675529323884544;s:7:"retweet";i:258581364012638208;s:7:"retweet";i:258575924121976832;s:7:"retweet";i:258572990294396928;s:7:"retweet";i:258572886795759616;s:7:"retweet";i:258572146769543168;s:7:"retweet";i:263273144754769920;s:7:"retweet";i:265440415480688640;s:7:"retweet";i:274143690455388161;s:7:"retweet";i:274141410918297601;s:7:"retweet";}'
tweetcount:
  - 27
categories:
  - Acessibilidade
  - Código
  - HTML5
  - Mercado e Comportamento
  - Tecnologia e Tendências
tags:
  - 2012
  - html
  - informacao
  - microdados
  - microformats
  - w3c

---
Como você diz para o sistema de busca que uma resenha em determinado site é uma resenha? E como você disponibiliza informações sobre seu evento como o local, data e etc para serviços na internet? Informação é para ser utilizada e reutilizada. Ela é reciclada diversas vezes por diversos motivos e por diversos meios. 

A especificação de Microdados do HTML define um mecanismo que permite que máquinas &#8211; leia-se meios de acesso como scripts, aparelhos, sistemas, serviços etc &#8211; reconheçam dados que possam ser embedados em documentos HTML de uma forma fácil. Esses dados devem ser legíveis para seres humanos e para máquinas, sendo também compatíveis com outros formatos de dados existentes como RDF ou JSON.

Os Microdados são atributos colocados nas tags do HTML com informações para complementar seu significado. O Google dá um exemplo muito interessante. Veja abaixo um texto sobre uma determinada pessoa: 

<pre class="lang-html">&lt;div&gt; 
  Meu nome é Bob Smith, mas todos me chamam de Smithy. Esta é a minha página inicial:
  &lt;a href="http://www.example.com"&gt;www.example.com&lt;/a&gt;
  Moro em Albuquerque, Novo México, e trabalho como engenheiro na ACME Corp.
&lt;/div&gt;
</pre>

Agora esse mesmo código recheado de Microdados:

<pre class="lang-html">&lt;div itemscope itemtype="http://data-vocabulary.org/Person"&gt;
  Meu nome é &lt;span itemprop="name"&gt;Bob Smith&lt;/span&gt; 
  mas todos me chamam de &lt;span itemprop="nickname"&gt;Smithy&lt;/span&gt;.
  Esta é a minha página inicial:
  &lt;a href="http://www.example.com" itemprop="url"&gt;www.example.com&lt;/a&gt;
  Moro em Albuquerque, Novo México, e trabalho como &lt;span itemprop="title"&gt;engenheiro&lt;/span&gt;
  na &lt;span itemprop="affiliation"&gt;ACME Corp&lt;/span&gt;.
&lt;/div&gt;
</pre>

Nesse código indicamos que o texto se trata de uma pessoa (itemtype), cujo nome (itemprop=&#8221;name&#8221;) é Bob Smith mas o apelido (itemprop=&#8221;nickname&#8221;) é Smithy. Ele também tem um website (itemprop=&#8221;url&#8221;), é engenheiro (itemprop=&#8221;title&#8221;) e trabalha (itemprop=&#8221;affiliation&#8221;) na ACME Corp.

Quando você, ser humano, lê este texto, entende todas essas informações. O problema é que as &#8220;máquinas&#8221; não conseguem interpretar textos (ainda). Por isso é interessante que indiquemos essas informações para que possamos reutilizá-las de alguma maneira útil em outros projetos. Essas informações complementares são úteis para scripts que criamos todos os dias em nossos sistemas.

A ideia é que a informação seja acessível por qualquer coisa. Qualquer coisa mesmo. Se você pode ler, uma máquina deve ler também. Se uma máquina deve ler, ela precisa intepretar essa informação, como você faz. Por isso é importante que uma mesma linguagem seja conversada entre máquina e ser humano. 

A ideia de existir informações complementares para expandir o significado de informações em elementos do HTML não é nova. Os microformats já haviam tentado entrar na moda uma vez, sem sucesso. Houveram poucos adeptos e muitos serviços resolveram simplesmente não adotar a tecnologia. Agora, com uma nova época no desenvolvimento web, onde diversas necessidades tem surgido, algumas empresas voltaram a se interessar pelo assunto. Veja o trabalho que alguns buscadores <a href=&#8221;http://tableless.com.br/schema-marcacao-de-dados-estruturados/&#8221;>tem feito com o Schema</a>. 

Lembre-se que o objetivo principal é entregar conteúdo para o usuário não importa o que ele esteja usando. Se for uma App ou um sistema web, se for um celular ou um óculos, não importa, ele deve conseguir consumir essas informações.

Leia mais sobre microdados [aqui][1] e [aqui][2].

 [1]: http://tableless.com.br/introducao-a-microdata-no-html5/
 [2]: http://tableless.com.br/schema-marcacao-de-dados-estruturados/