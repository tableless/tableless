---
title: Animando com jQuery
author: Michael Granados
type: post
date: 2009-01-05
excerpt: Que tal experimentar fazer uma área onde o usuário clica em um botão de mostrar/ocultar menu?
url: /animando-com-jquery/
aktt_notify_twitter:
  - no
tweetbackscheck:
  - 1356391426
shorturls:
  - 'a:3:{s:9:"permalink";s:43:"http://tableless.com.br/animando-com-jquery";s:7:"tinyurl";s:26:"http://tinyurl.com/3fbk63j";s:4:"isgd";s:19:"http://is.gd/6w1ema";}'
twittercomments:
  - 'a:25:{i:165093192918765568;s:7:"retweet";i:165092717251137538;s:7:"retweet";i:186789423101378560;s:7:"retweet";i:186747114452295680;s:7:"retweet";i:186692405817393153;s:7:"retweet";i:186681153917423616;s:7:"retweet";i:186655732291211264;s:7:"retweet";i:186655695628795905;s:7:"retweet";i:186655687047258114;s:7:"retweet";i:198211749349040129;s:7:"retweet";i:198115887721615361;s:7:"retweet";i:198110105038884864;s:7:"retweet";i:215876876034510849;s:7:"retweet";i:215869515022606336;s:7:"retweet";i:215868714715848704;s:7:"retweet";i:227936961069985793;s:7:"retweet";i:227825841667723264;s:7:"retweet";i:227825668975632384;s:7:"retweet";i:241516619233374210;s:7:"retweet";i:251065037882531840;s:7:"retweet";i:251018368281350144;s:7:"retweet";i:256807785432485888;s:7:"retweet";i:256454292133777411;s:7:"retweet";i:276410235307036672;s:7:"retweet";i:276370497388818433;s:7:"retweet";}'
tweetcount:
  - 50
dsq_thread_id: 503038555
categories:
  - Código
  - JQuery
  - Técnicas e Práticas
tags:
  - animação
  - bibliotecas
  - design
  - fadein
  - fadeout
  - fadeto
  - JQuery
  - programadores

---
Um dos recursos mais procurados pelos designers (e programadores) em bibliotecas é animação. Existem bibliotecas e mais bibliotecas que fazem animações de diversas formas. Em prototype por exemplo, deve-se anexar a biblioteca scriptaculous para que seja possivel realizar animações. Já em mootools existem várias formas de resolver o mesmo problema, sendo assim um pouco mais complicado de lembrar de tudo isso. Por jQuery ser uma biblioteca simples com somente o funcional, o trabalho se torna mais simples, logo mais rápido de desenvolver as soluções.

Em jQuery &#8211; como já vimos aqui e aqui, temos animações que podemos usar nos projetos: slideUp, slideDown, slideToggle, fadeIn, fadeOut e fadeTo, além de show e hide. São efeitos simples que você pode utilizar em qualquer lugar, e suas nomenclaturas também sao simples a ponto de serem intuitivas na hora do serviço de fato.

### Slide

Que tal experimentar fazer uma área onde o usuário clica em um botão de mostrar/ocultar menu? Com apenas duas tags, a jQuery consegue executar essa tarefa.

Tomemos a seguinte marcação:

[cc lang=&#8221;html&#8221;]

<div>
  <!--
Aqui vem a área, que você pode manipulá-la como quiser,
experimente um formulário de login ou um menu inline ou uma
bela imagem.
-->
</div>

[/cc]

Apenas com HTML e CSS fazemos a [versão que funcionará sem javascript][1]. Pense sempre dessa forma, assim você não corre o risco de fazer javascript obstrusivo. É por isso que não foi colocado o link onde o usuário clicará para aparecer e sumir com a área. Veja como ficará este [exemplo estilizado][2] com apenas com algumas linhas de código de CSS.

Feita a primeira e a segunda camada (conteúdo feito no HTML e apresentação feita no CSS) partimos para a interação, que quem comanda é a jQuery. Primeiro, precisamos adicionar o link onde o usuário poderá clicar para fazer a área sumir e reaparecer, faremos isso dinamicamente com a ajuda do nosso Framework preferido. Com o método after (depois em inglês) adicionamos facilmente o nosso link.

[cc lang=&#8221;javascript]$(&#8216;#area&#8217;).after(&#8216;[Mostrar/Esconder Área][3]{#mostra-esconde-area}&#8216;)[/cc]

Após isto, só precisamos adicionar a animação ao nosso botão, fazendo ele animar a área desejada. Com o comando toggle, nem precisamos nos preocupar com o estado no qual a área se encontra, afinal, ele vai aparecer e desaparecer conforme o necessário.

[cc lang=&#8221;javascript]$(&#8216;#mostra-esconde-area&#8217;).click(function(){
  
$(&#8216;#area&#8217;).slideToggle()
  
})[/cc]

Não esqueça que estes comandos devem estar dentro da função de inicialização da jQuery. Então o script final ficará assim.

[cc lang=&#8221;javascript]$(function(){
  
$(&#8216;#area&#8217;).after(&#8216;[Mostrar/Esconder Área][3]{#mostra-esconde-area}&#8216;)
  
$(&#8216;#mostra-esconde-area&#8217;).click(function(){ $(&#8216;#area&#8217;).slideToggle() })
  
})[/cc]

Ao todo para fazermos a animação e a interação, não gastamos mais que cinco linhas de código javascript. Veja no [exemplo final][4] ([ou com pouco CSS][5]), como esse tipo de interação pode dar um gás na sua aplicação.

### Opacidade

Uma outra propriedade que a jQuery trabalha e que pode resultar em ótimas melhorias na usabilidade do usuário é a propriedade _opacity_. Ou seja, a transparencia dos elementos, e graças aos métodos _fadeIn_, _fadeOut_ podemos fazer um _tooltip_ com poucas linhas de código.

Primeiro, escrevemos o HTML necessário. Sempre pensando de forma não obstrusiva, ou seja, se o navegador do usuário não tiver javascript habilitado, ele não deve ter sua navegabilidade atrapalhada.

[cc lang=&#8221;html&#8221;]

  * [Google][6]
  * [Tableless][7]

[/cc]

Com algumas linhas de CSS aplicamos uma [interface interessante][8] para nosso menu. Para a construção usamos o atributo _title_, assim o usuário que não estiver com o javascript habilitado poderá navegar no site vendo todos os recursos que ele teria se o javascript estivesse habilitado.

A primeira tarefa da jQuery é criar um span onde vamos colocar o mesmo texto do atributo. Não podemos manipular o atributo title, ele fica com o padrão do sistema operacional do usuário, já um span podemos implementar o que nossa imaginação mandar, até mesmo criar balões colocando backgrounds, se necessário.

Para fazer isso, precisamos usar o método _each_, que percorre todos os elementos chamados aplicando a cada um uma diretiva específica.

[cc lang=&#8221;javascript]$(&#8216;#menu li a&#8217;).each(function(){
    
$(this).append(&#8216;<span>&#8216;+this.title+&#8217;</span>&#8216;)
    
this.title=&#8221;
  
})[/cc]

No método each nós passamos uma função, nessa função, a palavra-chave &#8220;this&#8221; indica o item que está sendo tratado pelo each (um de cada vez), ou seja, cada link específico. A cada link _appendamos_, ou seja, adicionamos ao fim de seu conteúdo o valor de seu atributo title dentro de uma tag span. Depois, limpamos o valor de seu title. Assim, removemos o tooltip original, deixando apenas o que será aplicado nos próximos passos.

Agora, a mágica. Adicionamos aos links a ação de hover que irá exibir seus filhos (o span que acabamos de adicionar) e ao mesmo tempo adicionamos a ação de sumir quando ele sair, fazemos isso com o próprio hover. Poderiamos fazer isso com os métodos _show_, _hide_ ou mesmo o _toggle_, mas para ficar mais interessante para o usuário, resolvi usar _fadeIn_ e _fadeOut_. Veja que mesmo assim, o código não fica tão impossível de entender.

[cc lang=&#8221;javascript]$(&#8216;#menu li a&#8217;).hover(function() {
    
$(this).children().show()
  
},function(){
    
$(this).children().hide()
  
})[/cc]

Enfim, aplicamos estes dois trechos de script ao nosso &#8220;inicializator-jquery&#8221; que fará com que esse script seja executado apenas após carregar a página, ou seja, quando todos os elementos já tiverem sido carregados. Também adicionamos ao CSS algumas linhas de código para deixar o tooltip amigável. [Veja como é muito][9] interessante esse efeito, agora com o nosso novo tooltip.

A jQuery manipula muito bem efeitos simples (mas que resolvem a esmagadora quantidade de problemas) que muitas bibliotecas insistem em deixar confuso demais ou complexo demais por adicionar mais e mais configurações para cada efeito. Por isso jQuery é uma ferramenta muito poderosa.

 [1]: http://dgmike.com.br/tableless/jquery/caixa-de-ferramentas-simples.html
 [2]: http://dgmike.com.br/tableless/jquery/caixa-de-ferramentas.html
 [3]: #area "Mostrar/Esconder Área"
 [4]: http://dgmike.com.br/tableless/jquery/caixa-de-ferramentas-animado.html
 [5]: http://dgmike.com.br/tableless/jquery/caixa-de-ferramentas-simples-animado.html
 [6]: google.com "Encontre o que você procura"
 [7]: tableless.com.br "Webstandards com Feijão e Farofa"
 [8]: http://dgmike.com.br/tableless/jquery/tooltip-simples.html
 [9]: http://dgmike.com.br/tableless/jquery/tooltip-simples-animado.html "Tooltip simples animado com JQuery"