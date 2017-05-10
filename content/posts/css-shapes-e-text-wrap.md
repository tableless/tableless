---
title: CSS Shapes e Text Wrap
author: Thaiana Poplade
type: post
date: 2014-05-27
excerpt: Que podemos criar formas geométricas e desenhos com CSS, isso já sabemos, mas e se você ainda pudesse fazer seu texto assumir este formato? Conheça CSS Shapes Module 1 e 2.
url: /css-shapes-e-text-wrap/
dsq_thread_id: 2716255140
categories:
  - Geral

---
Manipular textos apenas com o uso de CSS nunca foi tarefa fácil ou em alguns caso, sequer possível. Pensando nisso, a Adobe esta propondo mais uma propriedade para folhas de estilo, que pode salvar vidas :).

Além de criar formatos (retângulos, círculos, triângulos, etc) com CSS, em breve você talvez possa fazer seu texto respeitar o limite do formato e se organizar em volta do elemento. Com isso, fazer aquela capitular, pode ser mais fácil do que parece.

As duas propriedades propostas &#8211; _shape-inside e shape-outside_ &#8211; ainda estão em _draft_ na W3C e até mesmo fazer testes é um pouco trabalhoso, mas vale a pena entender um pouco do que esta por vir e torcer para que essa seja mais uma _feature_ bem sucedida do CSS3.

**Um pouco de CSS Shapes
  
** Você já precisou criar um círculo, apenas com CSS?
  
Se ainda não, abaixo alguns exemplos de formatos bem simples para serem criados com apenas alguns propriedades no CSS.

**Círculo:** o princípio para criação de um círculo é o uso do _border-radius: 100%_ que arredonda os cantos de seu elemento (a <_div>_ no exemplo) até que esses cantos se encontrem. Segundo <a href="http://caniuse.com/" target="_blank">Can I Use</a>, o border-radius está sendo 84% suportado pelos navegadores, exceto IE8.
  
<a href="http://codepen.io/thaipoplade/pen/hFDLj/" target="_blank">CSS Shapes &#8211; Circle</a>

**Triângulo:** para o triângulo o princípio é zerar a altura e a largura do elemento e trabalhar apenas com as bordas, neste caso, do _bottom_, _left_ e _right_. Se você aumentar os valores e trocar as cores, vai entender melhor como funciona e ainda conseguir triângulos com tamanhos de lados diferentes.
  
<a href="http://codepen.io/thaipoplade/pen/HAisq/" target="_blank">CSS Shapes &#8211; Triangle</a>

**Losango:** esta talvez seja uma das mais simples de se fazer. O Losango nada mais é que um quadrado, formato padrão que qualquer elemento com largura e altura fixas assume, com a propriedade transform: rotate que já tem 84% de suporte, exceto pelo IE8 também.
  
<a href="http://codepen.io/thaipoplade/pen/myCgE/" target="_blank">CSS Shapes &#8211; Losango</a>

**Forma criadas, como eu faço para colocar um texto que circunde o elemento?** Nessa hora é que conhecemos a propriedade: _shape &#8211; outside_. O uso da propriedade é simples, basta ter a forma com sua devida largura e altura, adicionar um _float_ e seu texto em seguida. O mais complexo de testar a funcionalidade é que, na aplicação do _shape-outside_, você ainda pode precisa definir algumas outras coisas: &#8211; Que forma o texto vai seguir: hoje as propostas são para “circle”, “ellipse”, “polygon” e “inset” (retângulo); &#8211; Que imagem o texto vai seguir (sim, tem essa mágica também); &#8211; E qual será a distância entre o texto e a forma. Para completar as sugestões, que já são super bem-vindas, a Adobe também está propondo a propriedade _shape-inside_ que faz o texto assumir um formato dentro da figura geométrica ou de uma imagem. Infelizmente, como ainda estão sendo realizadas as propostas e os testes, é muito difícil explicar exatamente como tudo vai funcionar, mas já consegui fazer alguns testes com o _shape-outside_, que já está um pouco mais evoluído, e divido agora com vocês. Detalhe: Você deve precisar de alguns navegadores bem específicos para visualizar o teste. A  Adobe indica também: http://html.adobe.com/webplatform/enable/

<a href="http://codepen.io/thaipoplade/pen/LJvhG/" target="_blank">Testing CSS Shape Outside</a>

Alguns links interessantes:

**CSS Shapes (criando formas com CSS puro) **
  
<a href="http://www.css3shapes.com/" target="_blank">http://www.css3shapes.com/</a>

**Proposta da Adobe**
  
<a href="http://html.adobe.com/webplatform/layout/shapes/" target="_blank">http://html.adobe.com/webplatform/layout/shapes/</a>

**Na W3C
  
** Outside
  
<a href="http://dev.w3.org/csswg/css-shapes-1/" target="_blank">http://dev.w3.org/csswg/css-shapes-1/</a>

Inside
  
<a href="http://dev.w3.org/csswg/css-shapes-2" target="_blank">http://dev.w3.org/csswg/css-shapes-2</a>

Até a próxima.

😉

&nbsp;