---
title: All Animation CSS3 – Criar animações CSS3 nunca foi tão fácil
authors: Clovis Neto
type: post
date: 2014-10-13
excerpt: Animações cross-browser que darão mais ênfase a suas páginas como controles deslizantes, efeitos 3D’s, etc...
url: /animation-css3-criar-animacoes-css3-nunca-foi-tao-facil/
categories:
  - CSS3
  - Javascript
tags:
  - JQuery
---
Criar animações para nossos websites era algo &#8220;impensável&#8221; no passado. Com o surgimento do CSS3 e a morte do flash, a criação de websites dinâmicos, animados e leves, foi ficando cada vez mais fácil. Quem diria que há 7 anos atrás poderíamos alterar nossas animações para web sem precisar ter o flash instalado na nossa máquina ou até mesmo criar sites com efeitos paralax? Os devs antigos sabem bem o que estou querendo dizer.

Assim como o HTML5, o CSS3 também veio com várias novidades interessantes e revolucionárias&#8230; Entre elas temos a propriedade **animation.** Com esta riquíssima propriedade, podemos produzir transições apenas com CSS. Mas isso você já sabe. Mesmo assim, a propriedade animation e também o método keyframe podem ser ruins de gerenciar quando temos muita animação em um mesmo site. Ai, se houver um framework que ajude esse trabalho, nossa vida se torna mais fácil. É aí que entra o All Animation CSS3.

# O framework All Animation CSS3

Bastante empolgado com estas riquíssimas possibilidades que a propriedade animation nos oferece, eu e o Jeftar Mascarenhas resolvemos criar um framework de animações css3, que graças a Deus está dando &#8220;alguns acessos&#8221;, e hoje irei compartilhar com meus amigos &#8220;dev&#8217;s ninjas&#8221;. Seu nome é o **All Animation CSS3**.

## &#8220;All &#8230;&#8221; oquê?

O nome soa meio irônico pois All Animation CSS3 (todas as animações css3) nada mais é que um framework que reúne ricas animações CSS3 para você utilizar no seu projeto acadêmico ou comercial. Contém um conjunto de animações, divertidas para deixar seu projeto mais sexy. São animações cross-browser que darão mais ênfase a suas páginas como controles deslizantes, efeitos 3D’s e etc&#8230;

## Quando usar?

Como qualquer framework, seu objetivo é agilizar o processo de criação no seu dia-a-dia. Se você assumiu um projeto grande, cujo o período de tempo é muito curto e com certeza, não teria tempo pra desenvolver animações interessantes&#8230; utilizar este framework seria ótimo para ganhar uns &#8220;timers&#8221; a mais.

## Quando não usar?

Como citei acima, o All Animation é  muito bom para quem está com uma carga de trabalho muito alta e um curto período de tempo pra desenvolver, mas se você tem um tempo extra para desenvolver seus projetos, então pode ficar à vontade para criar suas animações na mão.

# &#8220;Muito bem, eu quero utilizar nos meus projetos&#8221;

## Por onde começar:

É fácil integrar o framework no nosso projeto 😀 , veremos passo a passo como ultilizá-lo.

#### Passo 1, inclua os arquivos necessários no head, para que suas animações funcionem corretamente:

<pre class="lang-html">&lt;link rel="stylesheet" type="text/css" href="yourpath/all-animation.css" /&gt;
&lt;script type="text/javascript" src="yourpath/jquery.js"&gt;&lt;/script&gt;</pre>

#### Passo 2, dentro das delimitações da tag body, coloque a seguinte estrutura html:

<pre class="lang-html">&lt;div id="animation"&gt;&lt;/div&gt;
&lt;button class="anny-class"&gt;Trigger class, go!&lt;/button&gt;</pre>

> **Obs: &#8220;<button>&#8221; **é opcional, pois você também pode criar uma animação sem precisar de um ativador (pois o button funciona como um disparador da animação)**</p></blockquote> 
> 
> ### Passo 3, você pode usar a seguinte linha de código jQuery, para disparar a sua animação:
> 
> <pre class="lang-javascript">$(".anny-class").click(function(){
 $("#animation").addClass("journal");
});
</pre>
> 
> _journal é uma das classes que o nosso framework disponibiliza para nós usarmos_
> 
> &nbsp;
> 
> Caso queira adicionar o efeito em algum determinado tempo, você pode adicionar um temporizador:
> 
> <pre class="lang-javascript">setTimeout(function(){
 $("#animation").addClass("journal");
},2000);
</pre>
> 
> # Atenção:
> 
> Se você optar adicionar mais alguma animação em um elemento que já sofreu uma outra animação do All Animation, ou queira reiniciar a animação, você terá que remover a classe da última animação e inserir a sua, ex:
> 
> <pre class="lang-javascript">$("#animation").removeClass("journal").addClass("four-rock");</pre>
> 
> Temos várias classes no lugar da class journal, vejamos quais são:
> 
> ### Especiais:
> 
> <ul class="task-list">
>   <li>
>     dance
>   </li>
>   <li>
>     journal
>   </li>
>   <li>
>     pulse
>   </li>
>   <li>
>     pulse-slow
>   </li>
>   <li>
>     jamp
>   </li>
>   <li>
>     four-rock
>   </li>
> </ul>
> 
> ### Bounce:
> 
> <ul class="task-list">
>   <li>
>     enter-up-bounce
>   </li>
>   <li>
>     enter-down-bounce
>   </li>
>   <li>
>     enter-right-bounce
>   </li>
>   <li>
>     enter-left-bounce
>   </li>
>   <li>
>     scale-bounce
>   </li>
>   <li>
>     jump-bounce
>   </li>
> </ul>
> 
> ### Perspective:
> 
> <ul class="task-list">
>   <li>
>     tree-flip-right
>   </li>
>   <li>
>     tree-flip
>   </li>
>   <li>
>     tree-flip-up
>   </li>
>   <li>
>     tree-flip-down
>   </li>
>   <li>
>     flip-left-bounce
>   </li>
>   <li>
>     rotate-flip
>   </li>
>   <li>
>     flip-right-bounce
>   </li>
> </ul>
> 
> ### Fading Entrances:
> 
> <ul class="task-list">
>   <li>
>     flip-top
>   </li>
>   <li>
>     flip-left
>   </li>
>   <li>
>     flip-right
>   </li>
>   <li>
>     flip-bottom
>   </li>
> </ul>
> 
> ### >Rotate:
> 
> <ul class="task-list">
>   <li>
>     rotate-flip-down
>   </li>
>   <li>
>     rotate-down-bounce
>   </li>
>   <li>
>     rotate-out
>   </li>
> </ul>
> 
> ### >Agrecives:
> 
> <ul class="task-list">
>   <li>
>     flash-bang
>   </li>
>   <li>
>     bomba
>   </li>
> </ul>
> 
> Não irei listar todas, até porque estou adicionando mais com o passar do tempo 😀
> 
> # 
> 
> # Mais alguém utiliza?
> 
> Segundo o google analytics, no primeiro mês que lancei este framework , mais de 127 países usaram o All Animation em seus projetos 😀
> 
> # Finalizando&#8230;
> 
> Segue abaixo dois links para mais informações:
> 
> <a title="Ir para à página do All Animation CSS3" href="https://clovisdasilvaneto.github.io/all-animation/" target="_blank">Clique aqui para visualizar uma demo, dos efeitos</a>
> 
> <a title="clique aqui para abrir o repositório no github" href="https://github.com/clovisdasilvaneto/all-animation" target="_blank">Github, clique aqui</a>
> 
> Por hoje é só meus amigos ninjas, obrigado pela atenção, e até a próxima. 😀