---
title: Manipulação de classes com JQuery
authors: Diego Eis
type: post
date: 2012-03-01
excerpt: Entenda como funciona as funções do JQuery para manipulação de classes nos elementos do HTML.
url: /manipulacao-de-classes-com-jquery/
categories:
  - Javascript
tags:
  - JQuery
  - 2012
  - Na Prática

---
Você já deve saber que o [JQuery][1] é coisa linda de Deus. Existe uma linha muito tênue entre as features que o CSS pode fazer e o que o JQuery pode nos ajudar. A manipulação de classes é uma das facilidades que o JQuery proporciona e facilita infinitamente nossa vida. Essas funções nos ajudam muito quando iremos definir um comportamento dinâmico para os elementos.

## Formas de manipulação de classes

Você pode manipular as classes de elementos do HTML de quatro formas:

**.addClass()**
  
Existem diversas situações onde precisamos adicionar uma ou mais classes em um elemento para executarmos uma ação ou formatarmos o elemento com estilos determinados.

**.removeClass()**
  
Remove uma, várias ou todas as classes dos elementos escolhidos.

**.toggleClass()**
  
Insere ou remove uma ou mais classes dos elementos determinados, alternando entre classes escolhidas.

**.hasClass()**
  
Verifica se qualquer um dos elementos selecionados tem a classe determinada.

### .addClass()

Imagine que você queira adicionar uma classe extra o último elemento LI da lista:

[cc lang=&#8221;html&#8221;]

  * Primeiro
  * Segundo
  * Terceiro

[/cc]

[cc lang=&#8221;javascript&#8221;]
  
$(&#8216;li:last&#8217;).addClass(&#8216;selecionado&#8217;);
  
[/cc]


  
[Link do exemplo de ADDCLASS do JQuery][2]

Para adicionar mais de uma classe, basta fazer como fazemos no CSS: separe com espaços o nome das classes. E se você na sabia, sim, da para colocar mais de uma classe em um mesmo elemento HTML.

[cc lang=&#8221;javascript&#8221;]
  
$(&#8216;li:last&#8217;).addClass(&#8216;selecionado ultimo&#8217;);
  
[/cc]

Você pode adicionar uma classe no elemento ao clicar nele:

[cc lang=&#8221;javascript&#8221;]
  
$(&#8216;li:last&#8217;).click(function(){
      
$(this).addClass(&#8216;selecionado ultimo&#8217;);
  
});
  
[/cc]


  
[Link do exemplo de AddClass com click do JQuery][3]

Você pode ver a [documentação completa dessa feature aqui][4].

### .removeClass()

O **.removeClass()** function da mesma maneira que o **.addClass()**, só que em vez de colocar uma classe, você a remove. Simples assim.

Ainda usando o exemplo acima, vamos retirar a classe _selecionado_ dos elementos e adicionar apenas no elemento clicado. O JS fica assim:

[cc lang=&#8221;javascript&#8221;]
  
$(&#8216;li&#8217;).click(function(){
      
$(&#8216;li&#8217;).removeClass(&#8216;selecionado&#8217;);
      
$(this).addClass(&#8216;selecionado&#8217;);
  
});
  
[/cc]



Muito simples. Você define qual a classe que vai ser removida e pronto, o JQuery faz isso para você.

### .toggleClass()

O **toggleClass** nos ajudaria muito mais no exemplo aplicado acima. Ele alterna uma determinada classe, adicionando e removendo-a sem a necessidade de IFs ou coisas assim.
  
Eles detectam se o elemento tem ou não a classe. Se houver a classe, ele a retira, se não, ele adiciona. A sintaxe é a que segue abaixo:

[cc lang=&#8221;javascript&#8221;]
  
$(&#8216;li&#8217;).click(function(){
      
$(this).toggleClass(&#8216;selecionado&#8217;);
  
});
  
[/cc]


  
[Link do exemplo][5]

### .hasClass()

E por último, o **.hasClass**. Essa função detecta se o elemento tem ou não a classe, e então, sabendo disso, você pode manipulá-lo da maneira que bem entender. No nosso exemplo abaixo iremos apenas detectar qual dos elementos tem a nossa classe. HTML:

[cc lang=&#8221;html&#8221;]

Este é o primeiro parágrafo.

<p class="selected">
  Este é o segundo parágrafo e tem a classe SELECTED
</p>

[/cc]

E o JQuery:

[cc lang=&#8221;jquery&#8221;]
  
$(&#8220;div#result1&#8221;).append($(&#8220;p:first&#8221;).hasClass(&#8220;selected&#8221;).toString());
  
$(&#8220;div#result2&#8221;).append($(&#8220;p:last&#8221;).hasClass(&#8220;selected&#8221;).toString());
  
[/cc]


  
[Link do exemplo][6]

Para ler a documentação dessas funções, [clique aqui][7].

 [1]: https://jquery.com
 [2]: https://jsfiddle.net/tableless/35DJy/
 [3]: https://jsfiddle.net/tableless/JakZ8/
 [4]: https://api.jquery.com/addClass/
 [5]: https://jsfiddle.net/tableless/s76Xc/2/
 [6]: https://jsfiddle.net/tableless/FcTm7/10/
 [7]: https://api.jquery.com/category/manipulation/class-attribute/