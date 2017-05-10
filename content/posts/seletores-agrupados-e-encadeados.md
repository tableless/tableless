---
title: Seletores Agrupados e Encadeados
author: Diego Eis
type: post
date: 2009-03-09
excerpt: Sobre seletores agrupados e seletores encadeados. Explicação rápida e básica.
url: /seletores-agrupados-e-encadeados/
aktt_notify_twitter:
  - no
tweetbackscheck:
  - 1356451601
shorturls:
  - 'a:3:{s:9:"permalink";s:56:"http://tableless.com.br/seletores-agrupados-e-encadeados";s:7:"tinyurl";s:26:"http://tinyurl.com/3bxmxho";s:4:"isgd";s:19:"http://is.gd/8gcuc0";}'
twittercomments:
  - 'a:1:{i:10026108443435009;s:7:"retweet";}'
tweetcount:
  - 1
dsq_thread_id: 503038907
categories:
  - CSS
  - Técnicas e Práticas
tags:
  - Código
  - CSS
  - seletores
  - serie-seletores

---
O CSS é responsável por formatar e manipular toda informação exibida pelo HTML, de forma que o layout fique fiel ao que o designer desenhou. Essa é a explicação básica e resumida sobre a função do CSS.

A idéia principal é não misturar o código de Formatação com a Informação do site.<!--more--> Elas devem ser independentes, para que as modificações em cada uma não influeciem o funcionamento da outra. Para isso, você precisa conseguir selecionar qualquer elemento do HTML pelo CSS.

**Aviso: Este primeiro post terá como objetivo contextualizar o assunto. Faremos uma série de artigos sobre seletores, e é importante entendermos como eles funcionam.**

O &#8220;seletor&#8221; é o responsável por essa função de selecionar o elemento, a estrutura da sintaxe é exatamente essa:

<pre lang="CSS" line="1">seletor {
   propriedade: valor;
}
</pre>

**Propriedade e valor** são as características que você gostaria de modificar no elemento.
  
**Seletor** é o elemento que você irá selecionar no código HTML.

Nesta série de artigos, iremos mostrar como os seletores funcionam e seus tipos. Começaremos desde o básico até o manipulação de filhos e seletores complexos. 

Aviso aos navegantes: Farei essa série nivelando as possibilidades por cima. Ou seja, ignorarei solenemente browsers antigos ou que não suportam algumas possibilidades.

### Seletores Agrupados

Quando você deseja fazer com que vários elementos tenham as mesmas características, você irá agrupá-los em um mesmo seletor. A separação dos elementos é feita por vírgulas. Veja um exemplo:

<pre lang="CSS" line="1">strong, em, span {
 color: red;
}
</pre>

Os elementos STRONG, EM e SPAN terão a mesma cor.

### Seletores Encadeados

O CSS trabalha com especificidade. Suponhamos que você queira que o EM tenha cor de letra vermelha, você irá fazer assim:

<pre lang="CSS" line="1">em {
 color: red;
}
</pre>

Mas você tem uma série de EMs na página, e talvez você queira que apenas o EM que está dentro de STRONG fique com a cor vermelha. Você terá que especificar isso no seu seletor:

<pre lang="CSS" line="1">strong em {
 color: red;
}
</pre>

No seletor acima estou dizendo que o EM que está dentro do STRONG terá cor vermelha. Lê-se da direita para esquerda, por que é a ordem do HTML. O código HTML seria mais ou menos assim:

<pre lang="html" line="1"><p>
  A idéia do Tableless é sem dúvida <strong>melhorar o <em>nosso mercado</em></strong>. 
  
</p>
</pre>

Um seletor encadeado um pouco mais longo:

<pre lang="CSS" line="1">.content .post-text p strong em {
 color: red;
}
</pre>

O HTML deste seletor seria este:

<pre lang="html" line="1"><div class="content">
  <div class="post-text">
    <p>
      A idéia do Tableless é sem dúvida <strong>melhorar o <em>nosso mercado</em></strong>. 
      		
    </p>
    	
  </div>
  
</div>
</pre>

Juntando os **seletores agrupados** e o **seletores encadeados**, ficaria mais ou menos assim:

<pre lang="CSS" line="1">.content .post-text p strong em, .content .post-text p strong a {
 color: red;
}
</pre>

Note que a vírgula separa os elementos. Logo após da vírgula é iniciado um novo seletor para modificar um outro elemento no HTML.

Se você quer acompanhar essa pequena campanha, veja no Twitter o que nós podemos fazer sem o IE6. Siga o hash [#semie6][1].

 [1]: http://search.twitter.com/search?q=%23semie6