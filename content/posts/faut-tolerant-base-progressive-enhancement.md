---
title: 'Fault Tolerance: a base do Progressive Enhancement'
author: Diego Eis
type: post
date: 2014-02-17
excerpt: Entenda por que o Fault Tolerance é a base para o Progressive Enhancement e também do Adaptive web Design.
url: /faut-tolerant-base-progressive-enhancement/
dsq_thread_id: 2279044377
categories:
  - Adaptive Web Design (AWD)
  - CSS
  - HTML
  - Responsive Web Design (RWD)
tags:
  - adaptive web design
  - fault tolerance
  - progressive

---
Fault Tolerance é como as máquinas tratam um erro quando ele acontece. É a habilidade do sistema continuar em operação quando uma falha inesperada ocorre. Isso [acontece a todo momento com seu cérebro][1]. O sistema não pode parar até que esse erro seja resolvido, logo o sistema dá um jeito para que esse erro não afete todo o resto do sistema. A natureza inteira trabalha dessa forma. Os browsers trabalham dessa forma. É por isso que você consegue testar as coisas maravilhosas do CSS3 e do HTML5 sem se preocupar com browsers antigos.

## Já temos as vantagens do fault tolerance desde o início

Por exemplo, quando escrevemos uma propriedade de CSS que o browser não reconhece, ele simplesmente ignora aquela linha e passa para a próxima. Isso acontece o tempo inteiro quando aplicamos novidades do CSS ou do HTML. Lembra-se quando os browsers não reconheciam os novos tipos de campos de formulários do HTML5? O browser simplesmente substituía o campo desconhecido pelo campo comum de texto. 

Isso é importante por que o que se faz hoje no desenvolvimento de um website, continuará funcionando de alguma forma daqui 10 anos. Como os browsers tem essa tolerância a falhas, linguagens como HTML e CSS ganham poder para evoluir o tempo inteiro, sem os bloqueios das limitações do passado.

> Fault Tolerance é como as máquinas tratam um erro quando ele acontece.

Entender a importância do Fault Tolerance é a chave para entender o Progressive Enhancement. Na verdade o Progressive Enhancement não seria possível se essa tolerância de falhas não existisse em browsers e outros meios de acesso.

## Tudo sobre acessibilidade

Fundamentalmente, Progressive Enhancement é tudo sobre acessibilidade. Na verdade o termo acessibilidade é normalmente usado para indicar que o conteúdo deve ser acessível para pessoas com necessidades especiais. O progressive enhancement trata isso mas na ótica de que todo mundo tem necessidades especiais e por isso o acesso ao conteúdo deveria ser facilitado para qualquer pessoa em qualquer tipo de contexto. Isso inclui facilmente pessoas que acessam websites via smartphones, por exemplo, onde a tela é pequena e algumas das facilidades que existem no desktops estão ausentes.

## Níveis de tolerância

Nós passamos por alguns níveis ao desenvolver algo tendo como método o Progressive Enhacement. Esses níveis tem como objetivo sempre servir primeiro o conteúdo e depois todas as funcionalidades e comportamentos que podem melhorar o consumo deste conteúdo e também de toda a página.

A base para tolerar erros é sempre manter um fallback quando algo ruim acontecer. A primeira camada geralmente é dar um fallback básico, conhecido pela maioria dos dispositivos. Esse fallback geralmente é servir um conteúdo em forma de texto. Isso é óbvio por que texto é um conteúdo acessível para praticamente qualquer meio de acesso existente hoje. Muitos dos elementos do HTML tem um fallback de texto para casos onde elemento não seja carregado ou não seja reconhecido. Lembra do atributo ALT? Até mesmo nas tags de vídeo e audio, como abaixo:

<pre class="lang-html">&lt;video src="video.ogg" controls&gt;
  Texto de fallback.
&lt;/video&gt;
</pre>

A segunda camada é a **semântica** do HTML. Cada elemento do HTML tem sua função e principalmente seu significado. Eles acrescentam significados a qualquer informação exibida pelo HTML e muitas vezes estendem o significado que o texto sozinho não conseguiria.

**Texto é universal.**

A terceira camada de experiência é a camada visual, onde o CSS e também as imagens, audios e vídeos são as responsáveis. É onde a coisa fica bonita e interativa. Aqui você sente mais a tolerância dos browsers a falhas. Usamos o tempo inteiro propriedades que nos ajudarão a melhorar a implementação de layouts, mas que em browsers antigos podem não ser renderizados. Experimentamos isso a todo momento.

A quarta camada é a camada de interatividade ou comportamento. O Javascript toma conta dessa parte controlando os elementos do HTML, muitas vezes controlando propriedades do CSS para realizar ações de acordo com as interações do usuário.

A camada final é uma extensão da semântica dos elementos do HTML. Aí é onde inserimos as iniciativas de WAI-ARIA. É onde vamos guiar leitores de telas e outros meios de acesso para elementos e pontos importantes na estrutura que o layout se baseia. Indicando quais regiões e elementos são referência de navegação.

Nós sempre podemos resumir as camadas em 3:

  * **Camada de conteúdo:** HTML semântico e rico com WAI-ARIA e tags corretas;
  * **Camada de formatação:** CSS e estilos;
  * **Camada de comportamento:** Javascript;

## Adaptive Web Design

Responsive design é bacana, coisa linda de Deus. Mas ainda está longe de ser algo que seja a solução para todos os problemas. Tudo está caminhando para algo mais flexível. A ideia do Responsive é muito, muito legal quando é aplicado a websites de conteúdo, blogs, websites institucionais, pequenos portais e etc. Mas quando vamos ambientes mais complexos, como fazer o administrativo de um produto, você tem elementos burocráticos difíceis de adequarmos em todas as telas. 

> Fault Tolerance deve ser levado em conta em todos os seus projetos web.

A ideia do Adaptive Web Design é que você entregue exatamente a melhor experiência que o usuário pode receber no contexto em que ele se encontra. A palavra &#8220;contexto&#8221; tem sido muito usada quando conversamos sobre mobilidade. Contexto significa todo o ambiente e a forma com que seu usuário está consumindo o seu conteúdo naquele momento. Ele pode estar parado em um ônibus cheio, ou andando enquanto procura uma informação&#8230; Ele pode estar assistindo TV ou cozinhando. Cada contexto influência em como ele vai consumir seu conteúdo. Não existe maneira de adaptar o conteúdo e as formas de uso para cada um dos tipos de contexto. Por esse motivo, a única saída de ter certeza (ou o máximo de certeza) é deixar as coisas simples.

Há diversas maneiras de se fazer isso, mas antes que façamos soluções mirabolantes, temos que ter em mente que boa parte do trabalho já é feito pelos browsers e que podemos nos ater ao simples. Você não pode esperar que o usuário de mobile use seu site em um celular da mesma maneira que ele o usa em um Desktop. É por isso que você adapta elementos e a estrutura.

Fault Tolerance deve ser levado em conta em todos os seus projetos web. Pensar assim te dá flexibilidade para avançar corrigindo problemas sem prejudicar todo o processo. 

#### Leia mais

  * [Sobre Progressive Enhancement &#8211; Bem vindo a Xangrilá &#8211; Parte 1][2]
  * [Understanding Progressive Enhancement Techniques in Web Design][3]
  * [What is the difference between Responsive e Adaptive Design][4]
  * [The difference between adaptive design and Responsive Deisgn][5]

 [1]: http://super.abril.com.br/ciencia/revolucao-cerebro-446545.shtml
 [2]: http://tableless.com.br/bem-vindo-a-xangrila-parte-1/ "Bem vindo a Xangri-lá – Parte 1"
 [3]: http://www.techrepublic.com/blog/web-designer/understanding-progressive-enhancement-techniques-in-web-design/1809/
 [4]: http://www.techrepublic.com/blog/web-designer/what-is-the-difference-between-responsive-vs-adaptive-web-design/
 [5]: http://www.searchenginepeople.com/blog/the-difference-between-adaptive-design-and-responsive-design.html