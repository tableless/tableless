---
title: O que é Design Atômico?
author: Dani Guerrato
type: post
date: 2013-06-24
excerpt: Conheça a nova metodologia para criação e desenvolvimento de layouts através de sistemas de interface modulares.
url: /o-que-e-design-atomic/
dsq_thread_id: 1419149085
categories:
  - Adaptive Web Design (AWD)
  - Artigos
  - Design
  - Mercado e Comportamento
  - Responsive Web Design (RWD)
  - Tecnologia e Tendências
tags:
  - 2013
  - atomic design
  - brad frost
  - guias de estilo
  - metodologia
  - responsive design

---
Neste artigo vamos bater um papo sobre os atuais problemas de prototipagem para design responsivo e conhecer um novo método que, através de analogias científicas curiosas e ferramentas inspiradas em Guias de Estilo, promete modificar a maneira como entendemos, organizamos e desenvolvemos interfaces.

## O estado atual do webdesign

O advento do design responsivo em 2010 transformou a maneira como projetamos interfaces para a web. 3 anos se passaram desde então e a possibilidade de ter um conteúdo unificado presente em múltiplos dispositivos já é uma realidade concreta. Diversas técnicas e boas práticas de sintaxe e semântica foram propostas e consolidadas. Foram criados boilerplates, frameworks, scripts e plugins para facilitar o desenvolvimento front-end. Mas embora o design responsivo tenha sido uma mudança extremamente positiva e aceita na industria ainda temos um problema: os dias tem apenas 24 horas.

Desenvolver um layout consistente e funcional em diferentes browsers, sistemas operacionais e dispositivos consome muito mais tempo do que os métodos tradicionais. O velho esquema em cascata  wireframe > mock-up em psd > layout > aprovação está a cada dia mais difícil de manter já que a quantidade de trabalho literalmente triplicou. Enquanto antes tínhamos que criar apenas um template de layout (desktop) hoje temos que pensar em smartphones, tablets, televisores&#8230; Isto significa três vezes mais wireframes, três vezes mais mock-ups e três vezes mais reuniões. Já sabemos como escrever códigos responsivos, mas uma lacuna ainda sobra. Como criar layouts para este novo cenário e como apresentar isto como um produto entregável?

Diversos designers estão tentando responder a esta pergunta, mas até agora não existem respostas definitivas. O fato é que se continuarmos a pensar em sites apenas como páginas isoladas a tendência é que a dificuldade de desenvolvimento aumente progressivamente a medida que novos aparelhos sejam inseridos no mercado. É necessária a criação de um novo modelo que melhore o fluxo de trabalho de designers e desenvolvedores! Mas qual?

## Mini bootstraps, para todos os clientes!

Eu já falei aqui no Tableless [sobre Guias de Estilos][1] e como eles podem ajudar a resolver alguns destes problemas, tanto no âmbito do design quanto do front-end. Para quem não está familiarizado com o conceito, basicamente são bibliotecas modulares de elementos de design, snippets de código e padrões da user interface. Algo como um [mini Twitter Bootstrap][2] criado especialmente para cada projeto. As vantagens são muitas como a organização, documentação e melhoria na comunicação entre os profissionais já que os conceitos de design estão todos unificados em um local.

### Do que, afinal, interfaces são feitas?

Escolher quais elementos incluir no Guia de Estilos pode causa algumas dúvidas. O Designer Tyler Sticka tentou responder algumas delas ao [compilar uma tabela][3]  contabilizando os elementos mais comuns em diversos boilerplates e frameworks famosos. O resultado é bem interessante e pode servir de ponto de partida para a criação de seu próprio guia. Foram compilados mais de 160 elementos diferentes. É claro, nem todos os itens vão ser utilizados sempre. Mas vale a pena conhecer para entender a extensão do que é possível criar.

### O contra dos Guias de Estilo

Embora esta solução seja ótima da perspectiva do designer e do desenvolvedor ela ainda demanda muito tempo, o que é quase um luxo em alguns projetos. E para alguns clientes ainda pode ser difícil de entender como aquele monte de elementos abstratos aparentemente aleatórios pode de fato se transformar magicamente em um site na internet. E isto é compreensível, afinal, é difícil dizer se gosta de um rosto apenas olhando o nariz. Mas como todo Pokémon evolui entra em cena o&#8230;

## Design atômico

Dizer que você faz &#8220;design atômico&#8221; não significa (infelizmente) que agora podemos projetar bio organismos no Photoshop ou algo parecido. Na verdade é só uma analogia para explicar como os diferentes componentes de uma página podem interagir&#8230;. Esta metodologia para a criação de interfaces foi criada pelo webdesigner [Brad Frost][4]  e explicada em detalhes na conferência Beyond Tellerrand, na Alemanha (você pode conferir o [vídeo da palestra][5] em inglês).

Da mesma forma que Guias de Estilo, o design atômico também é modular. Ele parte do pressuposto que as páginas na internet na realidade são sistemas, ou seja,  conjuntos de elementos interconectados que formam um todo organizado. Inspirado pelas aulas de química do colegial Frost percebeu que os componentes de uma página da internet se comportam de maneira muito parecida com a de átomos, moléculas e organismos. Páginas na internet são basicamente compostas por um grupo finito de elementos (tags HTML) que podem se agrupar de diferentes maneiras para criar sistemas complexos.

[<img class="alignnone size-full wp-image-37823" alt="atomic-design" src="http://tableless.com.br/uploads/2013/06/atomic-design.jpg" width="660" height="340" srcset="uploads/2013/06/atomic-design.jpg 660w, uploads/2013/06/atomic-design-326x168.jpg 326w, uploads/2013/06/atomic-design-588x302.jpg 588w, uploads/2013/06/atomic-design-601x310.jpg 601w" sizes="(max-width: 660px) 100vw, 660px" />][6]

### Os Átomos

<interludio ciêntifico>
  
A palavra átomo quer dizer &#8220;aquilo que não pode ser dividido&#8221;. E quando surgiu este conceito na ciência no inicio do século XIX, de fato ele era considerado a menor parte da matéria (ironicamente a ciência depois descobriram que é possível dividir átomos em partes menores, mas isto não vem ao caso). O fato é que os átomos se juntam para formar moléculas que se juntam para formar organismos que são&#8230; bem, tudo. Os átomos aqui são os blocos de construção do universo. Algo como peças de lego que você pode montar e combinar para criar elementos maiores.
  
</interludio ciêntifico>

Bem, no Atomic Design os átomos funcionam da mesma forma. São os menores elementos disponíveis em linguagem de marcação de texto: tags. Os átomos são elementos isolados que não precisam de um contexto para existir. Pense em coisas soltas como labels, inputs, campos de formulário, botões, títulos, parágrafos&#8230;  ou até mesmo elementos abstratos como paleta de cores e font-stacks. Estes são os blocos básicos utilizados para construir elementos maiores.

<img class="alignnone size-full wp-image-37841" alt="exemplo-de-atomo" src="http://tableless.com.br/uploads/2013/06/exemplo-de-atomo.jpg" width="660" height="340" srcset="uploads/2013/06/exemplo-de-atomo.jpg 660w, uploads/2013/06/exemplo-de-atomo-326x168.jpg 326w, uploads/2013/06/exemplo-de-atomo-588x302.jpg 588w, uploads/2013/06/exemplo-de-atomo-601x310.jpg 601w" sizes="(max-width: 660px) 100vw, 660px" />

### Moléculas

Moléculas aqui são basicamente agrupamentos de um ou mais átomos. As moléculas fazem os componentes isolados funcionarem com um propósito único. Uma label um campo de formulário e um botão não são uteis isoladamente, mas juntos podem cumprir uma função específica como realizar uma busca. Um conjunto de headings torna-se a molécula hgroup.

<img class="alignnone size-full wp-image-37842" alt="exemplo-de-molecula" src="http://tableless.com.br/uploads/2013/06/exemplo-de-molecula.jpg" width="660" height="142" srcset="uploads/2013/06/exemplo-de-molecula.jpg 660w, uploads/2013/06/exemplo-de-molecula-329x70.jpg 329w, uploads/2013/06/exemplo-de-molecula-588x126.jpg 588w" sizes="(max-width: 660px) 100vw, 660px" />

### Organismos

Você pode pensar neles como uma colagem de elementos. Da mesma maneira que uma molécula é um conjunto de átomos, organismos são um conjunto de moléculas. Normalmente isto vai corresponder a uma seção do site como header, footer, sidebar, etc. Ao contrário das moléculas, os organismos podem ter diversos propósitos funcionando paralelamente. Um header, por exemplo,  pode possuir elementos como logotipo, navegação, formulário de login, campo de busca, call to action, etc. E cada um deles realiza uma ação específica. Um conjunto formado por moléculas como hgroup, span e data pode ser o organismo cabeçalho de um artigo.

<img class="alignnone size-full wp-image-37843" alt="exemplo-de-organismo" src="http://tableless.com.br/uploads/2013/06/exemplo-de-organismo.jpg" width="660" height="193" srcset="uploads/2013/06/exemplo-de-organismo.jpg 660w, uploads/2013/06/exemplo-de-organismo-329x96.jpg 329w, uploads/2013/06/exemplo-de-organismo-588x171.jpg 588w" sizes="(max-width: 660px) 100vw, 660px" />

### Templates

Okay, aqui a metáfora de ciência acabou. Isto acontece por que a partir desta etapa já é possível mostrar algo para o cliente e ele provavelmente pode achar você meio maluco se tentar explicar seu layout utilizando um modelo atômico.  É melhor continuar com um vocabulário familiar&#8230; Templates são &#8211; você provavelmente adivinhou &#8211; conjuntos de organismos. Neste momento o design começa a ficar mais concreto. Você pode pensar em templates como wireframes de HTML de baixa fidelidade. Aqui já é possível visualizar o esqueleto do seu site ao vivo de maneira interativa. Seguindo com o nosso exemplo teríamos a página completa composta por diversos organismos.

<img class="alignnone size-full wp-image-37845" alt="exemplo-de-template" src="http://tableless.com.br/uploads/2013/06/exemplo-de-template.jpg" width="660" height="502" srcset="uploads/2013/06/exemplo-de-template.jpg 660w, uploads/2013/06/exemplo-de-template-220x168.jpg 220w, uploads/2013/06/exemplo-de-template-407x310.jpg 407w" sizes="(max-width: 660px) 100vw, 660px" />

### Páginas

As página são a evolução dos templates para um design de alta fidelidade mais complexo com cor, tipografia e conteúdo. Através da página é possível ver todos os elementos menores como imagens e videos no contexto real e assim validar a efetividade do template. Após os ajustes necessários você tem o produto final. Este seria o nosso exemplo de wireframe com um conteúdo &#8220;real&#8221;.

<img class="alignnone size-full wp-image-37844" alt="exemplo-de-pagina" src="http://tableless.com.br/uploads/2013/06/exemplo-de-pagina.jpg" width="660" height="612" srcset="uploads/2013/06/exemplo-de-pagina.jpg 660w, uploads/2013/06/exemplo-de-pagina-181x168.jpg 181w, uploads/2013/06/exemplo-de-pagina-334x310.jpg 334w" sizes="(max-width: 660px) 100vw, 660px" />

### Vantagens do Modelo

O Design Atômico promove uma evolução linear de objetos abstratos menos complexos até o produto final. Através desta metodologia podemos estabelecer um padrão para a criação de sistemas de design, com partes reutilizáveis com uma progressão lógica de montagem. Dependendo do gosto da sua equipe isto pode significar até mesmo a remoção de mockups estáticos no Photoshop, o que representa um ganho de tempo e produtividade. A possibilidade de testar os átomos, moléculas e organismos em um ambiente real também garante que o seu produto final seja a prova de erros. Outra vantagem é a facilidade de mudanças e ajustes, diminuindo o impacto negativo de refações no fluxo de trabalho. Basta trocar a ordem ou combinação de elementos para criar novas páginas.

### O Laboratório do Designer

O modelo teórico do design atômico já é interessante e relevante por si só. Mas Frost criou uma ferramenta que funciona como uma mistura de sandbox e boilerplate: o [Pattern Lab][7]. Através da ferramenta podemos construir sistemas de design utilizando uma biblioteca de componentes em PHP, um conjunto de padrões comuns de user interface, uma suite de testes responsiva, dentre outros recursos. Tudo dividido e organizado entre átomos, moléculas e organismos de maneira que você possa criar suas próprias páginas e templates.  Alias, os exemplos utilizados neste artigo foram totalmente retirados do Pattern Lab.

[<img class="alignnone size-full wp-image-37850" alt="patternlab" src="http://tableless.com.br/uploads/2013/06/patternlab.jpg" width="660" height="260" srcset="uploads/2013/06/patternlab.jpg 660w, uploads/2013/06/patternlab-329x129.jpg 329w, uploads/2013/06/patternlab-588x231.jpg 588w" sizes="(max-width: 660px) 100vw, 660px" />][8]

A vantagem em relação aos Frameworks é que esta biblioteca é aberta, flexível e te dá espaço para criar seus próprios componentes da maneira que você bem entender. Tudo isto pronto para você  incluir, organizar e agrupar módulos como quiser através de tags PHP. Algo bem parecido com a sintaxe do WordPress, por exemplo. Se você se interessou basta visitar o [repositório no Github][9] para começar a brincar. Se você não curte PHP, tudo bem. Já existe uma galera criando versões para outras linguagens de programação. Você pode conferir o port para [Jekyll neste outro repositório][10].

Para ser sincera o layout padrão do Pattern Lab é bem feio. Mas esta é a intenção mesmo. A idéia é ser um facilitador para a criação do SEU design. Então todo visual é simples e neutro de maneira que você possa acrescentar seu próprio CSS. Ou seja, o Pattern Lab é propositalmente incompleto. A intenção aqui não é ser um framework, mas um conjunto de módulos que incluem os elementos mais utilizados em Guias de Estilo e outras coisas que as vezes esquecemos / são difíceis de incluir em mock-ups estáticos como padrões para animação em CSS, avatares de usuário, animação de loading, tags de áudio&#8230;

<img class="alignnone size-full wp-image-37846" alt="exemplo-animations" src="http://tableless.com.br/uploads/2013/06/exemplo-animations.jpg" width="660" height="260" srcset="uploads/2013/06/exemplo-animations.jpg 660w, uploads/2013/06/exemplo-animations-329x129.jpg 329w, uploads/2013/06/exemplo-animations-588x231.jpg 588w" sizes="(max-width: 660px) 100vw, 660px" />

### Não faz milagres

A ferramenta possui alguns fatores contra. Por ser toda baseada em includes existe uma certa dificuldade de integração com outras linguagens dinâmicas. O Pattern Lab pode ser legal para a criação de protótipos como mock-ups e wireframes, mas a não ser que você esteja planejando um site estático este não é o meio ideal para o desenvolvimento do produto final. Como os módulos são fechados isto impossibilita a implantação de um sistema de manutenção de conteúdo. Existem algumas discussões para contornar este problema, mas este é o cenário atual.

&nbsp;

## A Web do futuro

A criação de Frost vai muito além da metáfora bonitinha. O que eu acho verdadeiramente empolgante é ver pessoas buscando soluções diferentes para velhos problemas, criando discussões relevantes e procurando coletivamente novas formas de transformar a maneira como construímos interfaces. O fato é que a metáfora de Frost não apenas ajuda a entender interfaces modulares de maneira mais clara, mas em pouquíssimo tempo [já foi até ampliada][11] para englobar conceitos como breakpoints. Não tenho dúvida que estes conceitos devem ser ainda mais aperfeiçoados no futuro. Esta pode não ser a solução definitiva para o problema de itens entregáveis, mas é um bom caminho a ser explorado e testado. Basta que cada um contribua com suas próprias idéias para criarmos melhores soluções e experiências para designers, desenvolvedores, clientes e usuários.

### Saiba mais

[Atomic Design][12]
  
[Brad Frost @ #BTCONF][13]
  
[Atomic Design Makes Me Feel Like a Chemist][14]

 [1]: http://tableless.com.br/guia-de-estilos/#.UcOkIPagkR4 "Guias de Estilos"
 [2]: http://daverupert.com/2013/04/responsive-deliverables/ "Responsive Deliverables"
 [3]: http://blog.cloudfour.com/common-patterns/ "Common Patterns"
 [4]: http://bradfrostweb.com/blog/post/atomic-web-design/ "Atomic Web Design"
 [5]: http://vimeo.com/channels/beyondtellerrand/67476280 "Atomic Design - Beyond Tellerrand"
 [6]: http://bradfrostweb.com/blog/post/atomic-web-design/
 [7]: http://patternlab.bradfrostweb.com/ "Pattern Lab"
 [8]: http://patternlab.bradfrostweb.com/
 [9]: https://github.com/bradfrost/patternlab "Pattern Lab"
 [10]: https://github.com/zakkain/patternlab-jekyll "Pattern Lab Jekyll"
 [11]: http://www.benedfit.com/2013/06/atomic-design-phases-and-mesophases.html "Atomic design phases and mesophases"
 [12]: http://bradfrostweb.com/blog/post/atomic-web-design/ "Atomic Design"
 [13]: http://jancbeck.com/articles/btconf-brad-frost/ "Brad Frost @ #BTCONF"
 [14]: http://notebookandpenguin.com/atomic-design-makes-me-feel-like-a-chemist/ "Atomic Design Makes me Feel Like a Chemist"