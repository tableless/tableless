+++
authors = "Pedro Henrique Santiago"
canonical = ""
categories = ["reactjs", "javascript"]
date = "2019-02-18T10:00:00-03:00"
excerpt = "Nova feature que chegou na versão 16.8.0, um dos assuntos mais hype do começo de 2019."
image = "https://cdn-images-1.medium.com/max/800/1*JNXG7niZ6gJp7QyilGIm6w.jpeg"
publishdate = "2019-02-18T10:00:00-03:00"
sponsor = ""
tags = ["hook", "reactjs"]
title = "React Hooks"
type = "post"

+++
# O que é React Hook?

**React Hook** é uma feature que permite que você use estado e outras features do React sem ter a necessidade de escrever uma classe. Com React Hook você vai poder:

* Utilizar estado em funções que são componentes
* Executar funções quando o componente é montado e quando ele vai desmontar
* Adicionar a context api mais facilmente para refletir as mudanças em um componente funcional
* Criar suas próprias abstrações que brincam com os lifecycles do React e utilizar elas em componentes funcionais

# Por que criaram os hooks?

Os hooks surgiram por conta de três problemas que frequentemente aconteciam tanto com a linguagem Javascript quando com a lib React.

# Primeiro motivo: É difícil reutilizar lógica entre componentes.

Se você já utiliza React você pode perceber que você tem que ficar se repetindo mil vezes ao tentar reutilizar lógica, como por exemplo conectar-se a um provedor de estado, como por exemplo o connect do Redux.

Você precisa ficar toda hora utilizando High Order Componentes ou criando Render Props para conseguir reutilizar lógica sem precisar ficar escrevendo muito código, quando não, você precisa até criar seus próprios High Order Componentes. Isto resolve o problema em partes, mas não é tão bom, pois você cria um componente onde não tem a menor necessidade dele, apenas para se comunicar com o componente que seu HoC engloba.

O React foca muito na DX (Developer Experience) e para isso tem muitas ferramentas onde ajuda o desenvolvedor, o uso excessivo de HoC\`s pode afetar isso, pois olhe por exemplo como inspecionamos um elemento que utiliza muitas High Order Components:

![](https://cdn-images-1.medium.com/max/800/1*J1sMvsSjjr3Z8ZJjE_Fc-A.jpeg)

Facinho de realizar o debug, não?  
Além de dificultar a visualização do que realmente desejamos, temos que manter todos estes componentes em memória desnecessariamente.

# Segundo Motivo: Componentes complexos se tornam difíceis de serem compreendidos.

Imagine que você tem um componente complexo, onde ele precisa lidar com coisas que não são relacionados ao seu componente. Por exemplo, seu componente tem a necessidade de começar 3 contadores que funcionam em tempos diferentes e também tem que parar estes contadores quando o componente deixar de ser montado.

Observe o exemplo a seguir:

Veja como a criação e momento de parada de cada contador suja o código, agora imagine que o componente precisa realizar esta mesma operação para 20 contadores.

Será que não existe maneira melhor de resolver isso? Os hooks mostram uma maneira muito mais eficiente para chegar ao mesmo resultado.

# Terceiro motivo: Classes confundem.

O Javascript tem classes construídas com base em protótipos, isso significa que as classes do Javascript não funcionam como na maioria das linguagens que vemos no mercado como Java, C#, Ruby…  
Quando você utiliza a palavra Class (que entrou na ES6) dentro do seu código, você está utilizando um protótipo porém de forma mascarada, pois Class é apenas um syntax sugar (isso mesmo, só para ficar mais bonitinho) de um protótipo, logo, as classes não vão funcionar como o esperado.

Quanto utilizamos classes utilizamos muito o this no código, e isso em Javascript também gera muita confusão pois funciona diferente em outras linguagens, por exemplo o código abaixo:

Aqui funciona corretamente, mas e se quisermos usar o this de outra maneira?

Aqui temos um erro, pois agora o this ficou preso no contexto da função passada para o forEach e no protótipo desta função não foi possível encontrar a propriedade nome.

Além do problema com protótipos as classes também apresentam problemas para as ferramentas que utilizamos com react, pois elas não minificam tão bem quanto funções e além disso apresentam problemas para o [hot reloading](https://github.com/gaearon/react-hot-loader), tornando não confiável e em alguns casos até impossível.

# Como eles resolvem estes problemas?

Agora que os problemas já estão bem claros, vamos ver como os hooks resolvem estes problemas que temos.  
Com os Hooks utilizamos apenas funções, além deles serem funções que importamos diretamente do React, utilizamos apenas dentro dos componentes funcionais, assim conseguimos nos livrar das classes.

Aqui temos um exemplo de um componente utilizando o hook UseState:

Viu? Apenas funções, não precisamos mais criar nosso estado dentro do constructor de uma classe, também não precisamos mais ficar tomando cuidado com o uso do this, para saber se o this.setState ou this.state está no local correto por exemplo. Agora não temos mais a necessidade de ficar codificando com o this para lidar com o escopo que estamos.

Componentes complexos se tornam mais simples, e conseguimos reutilizar muito mais lógica. Compare estes dois componentes onde em preto é o código que se torna desnecessário, azul o estado, verde a context api e em amarelo os efeitos colaterais.

![](https://cdn-images-1.medium.com/max/800/0*KsXOObZ9ysVRPpI9)

Agora o **mesmo** componente com hooks, veja também como tudo que tem o mesmo sentido permanece agrupado, facilitando o entendimento do código:

![](https://cdn-images-1.medium.com/max/800/1*CpcHtzvIkWaehU7lrNT6HA.png)

<blockquote class="twitter-tweet"><p lang="en" dir="ltr">ok so - I took dan&#39;s classes/hooks code from react conf, blacked out the &#39;unnecessary&#39; bits, then colour coded bits by &#39;concern&#39;. so much nicer. the effect is amplified in more complex components, where concerns are split and mixed across lifecycle methods. <a href="https://t.co/nPUzQcisFt">pic.twitter.com/nPUzQcisFt</a></p>&mdash; Sunil Pai (@threepointone) <a href="[https://twitter.com/threepointone/status/1056594421079261185?ref_src=twsrc%5Etfw](https://twitter.com/threepointone/status/1056594421079261185?ref_src=twsrc%5Etfw "https://twitter.com/threepointone/status/1056594421079261185?ref_src=twsrc%5Etfw")">October 28, 2018</a></blockquote> <script async src="[https://platform.twitter.com/widgets.js](https://platform.twitter.com/widgets.js "https://platform.twitter.com/widgets.js")" charset="utf-8"></script>

Surreal, não?!

Isso tudo vai facilitar muito para os desenvolvedores causando menos confusões, facilitando a criação e refatoração de componentes e também para as ferramentas, pois antes o [hot reload](https://facebook.github.io/react-native/blog/2016/03/24/introducing-hot-reloading#hot-reloading) não conseguia replicar o código que ficava dentro do constructor e agora o minify consegue minificar ainda mais.

# Devo utilizar hooks?

Com certeza! Não precisa passar toda sua base de código para hooks refatorando todas suas classes, principalmente se você não tiver testes, aí de fato não seria uma boa ideia mesmo. Porém os hooks podem co-existir com as classes, não tem problema os novos componentes seus utilizarem hooks e outros permanecerem em classes.