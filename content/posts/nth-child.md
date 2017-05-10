---
title: 'Propriedade do CSS: nth-child'
author: Diego Eis
type: post
date: 2009-07-16
excerpt: 'A pseudo-classe nth-child seleciona elementos dentre uma árvore de elementos se referindo a posição específica de cada um. Você pode por exemplo selecionar os elementos ímpares ou pares. '
url: /nth-child/
aktt_notify_twitter:
  - yes
aktt_tweeted:
  - 1
tweetbackscheck:
  - 1356391794
shorturls:
  - 'a:3:{s:9:"permalink";s:33:"http://tableless.com.br/nth-child";s:7:"tinyurl";s:26:"http://tinyurl.com/42nrmxv";s:4:"isgd";s:19:"http://is.gd/78T9i9";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 503039138
categories:
  - CSS
  - Técnicas e Práticas
tags:
  - 2009
  - CSS
  - CSS3
  - Na Prática
  - seletores
  - tecnicascss
  - web

---
Se você é um cara muito técnico, que adora matemática e números, prefiro que você [leia a documentação do W3C][1] sobre `nth-child`. Ela é mais rica em detalhes sobre o cálculo que essa pseudo-classe faz. Este artigo é para os pobres mortais.

Você já precisou de criar uma tabela zebrada? Eu já, muitas vezes. Provavelmente se você não sabe programar, você precisa chamar um programador para escrever duas ou três linhas de código Javascript ou até mesmo usando JQuery, para fazer a mágica para você. A idéia do CSS, é que nós, designers, possamos controlar a aparência dos elementos HTML. Isso inclui conseguirmos fazer uma maldita tabela zebrada também. Para isso e para outros problemas parecidos, podemos utilizar a pseudo-classe `nth-child`. Com esta pseudo-classe é possível selecionar um determinado elemento dentro de uma árvore de elementos. Por exemplo, podemos selecionar todas as linhas ímpares das tabela. Legal, hein?

#### Cálculo básico

O cálculo utilizado pelo `nth-child` é bastante simples. Você vai usar na maioria das vezes soma. Lembra? A fómula será a seguinte: _an+b_. 

[cc lang=&#8221;css&#8221;]
  
table tbody tr:nth-child(2n+1) {
    
background:lightgray;
  
}
  
[/cc]

O funcionamento é o seguinte: o browser aplica o estilo a cada 2 `tr`.
   
O código abaixo, aplica o estilo a cada 3 `tr`. E assim por diante.

[cc lang=&#8221;css&#8221;]
  
table tbody tr:nth-child(3n+1) {
    
background:lightgray;
  
}
  
[/cc]

Você pode facilitar, utilizando as palavras _odd_ ou _even_, para selecionar os elementos ímpares ou pares da árvore.

[cc lang=&#8221;css&#8221;]
  
table tbody tr:nth-child(odd) {
    
background:lightgray;
  
}
  
[/cc]

Caso você queira pegar 9º, 19º, 29º e assim por diante:
  
[cc lang=&#8221;css&#8221;]
  
table tbody tr:nth-child(10n-1) {
    
background:lightgray;
  
}
  
[/cc]

Se o valor de _a_ (an+b) é igual 0, você não precisa colocar a fórmula, apenas o número referente a ordem do elemento. Exemplo:

[cc lang=&#8221;css&#8221;]
  
table tbody tr:nth-child(1) {
    
background:lightgray;
  
}
  
[/cc]

Neste código, o browser iá colorir o background apenas do primeiro `tr`. 

[Veja o exemplo.][2]

A propriedade `nth-child` faz parte dos seletores do CSS 3 e já pode ser utilizado em browsers atuais.

Se você ainda não leu sobre seletores do CSS, leia estes artigos abaixo:

  * [Seletores encadeados e agrupados][3]
  * [Seletores do CSS &#8211; Pseudo-classes][4]
  * [Seletores Complexos do CSS][5]

 [1]: http://www.w3.org/TR/css3-selectors/#nth-child-pseudo
 [2]: http://tableless.com.br/uploads/2009/07/nth-child-ex1.html
 [3]: http://tableless.com.br/seletores-agrupados-e-encadeados
 [4]: http://tableless.com.br/pseudo-classes-css
 [5]: http://tableless.com.br/seletores-complexos-do-css