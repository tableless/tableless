---
title: Sobre Cor e Webdesign II
author: Dani Guerrato
type: post
date: 2013-09-23
excerpt: |
  |
    Entenda a diferença entre matiz, luminosidade e saturação, aprenda a criar paletas de cores funcionais e conheça a fórmula mágica do contraste.
url: /cor-webdesign-2/
dsq_thread_id: 1786535740
categories:
  - Design
tags:
  - classes funcionais
  - contraste
  - cor
  - cores
  - design
  - matiz
  - saturação
  - teoria da cor

---
No [primeiro artigo][1] desta série discutimos os sistemas de cores e apresentamos algumas ferramentas úteis para a criação e organização de paletas. Hoje vamos mergulhar mais a fundo na teoria da cor e discutir aspectos como características, combinação de cores, função, legibilidade e técnicas para escolher &#8211; sem depender de &#8220;bom gosto&#8221; ou chute &#8211; uma boa paleta de cores para a web.

## Propriedades

Não vou entrar muito na parte física ou psicológica da coisa, ok? Existem muitos lugares onde vocês podem (e devem) ler sobre isto. Como o objetivo aqui é teoria da cor especificamente para a internet vamos dar uma revisada básica nos conceitos fundamentais e partir para as dicas práticas.

Basicamente podemos classificar as cores através de alguns aspectos. São eles&#8230;

## Matiz

Grau que um estimulo de cor pode ser descrito como parecido ou diferente de outro. Confuso, né? Pense na matiz como a personalidade da cor. As matizes são mais ou menos análogas aos nomes que damos para as tonalidades diferentes de cores. É pela matiz que você diferencia o azul do vermelho e do verde, por exemplo. Mas pense na cor pura, sem adição de preto ou branco. Azul marinho ou azul pastel são a mesma matiz: azul.

<img class="alignnone size-full wp-image-39010" alt="matiz" src="http://tableless.com.br/uploads/2013/09/matiz.jpg" width="660" height="400" srcset="uploads/2013/09/matiz.jpg 660w, uploads/2013/09/matiz-277x168.jpg 277w, uploads/2013/09/matiz-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />

## Saturação

A saturação é a intensidade da cor. Imagens com alta saturação são mais vivas e vibrantes. Já imagens com baixa saturação são mais neutras e mudas, mais próximas do cinza. Se você reduzir toda a saturação de uma imagem no monitor ela vai ficar somente em tons de cinza.

<img class="alignnone size-full wp-image-39012" alt="saturacao" src="http://tableless.com.br/uploads/2013/09/saturacao.jpg" width="660" height="400" srcset="uploads/2013/09/saturacao.jpg 660w, uploads/2013/09/saturacao-277x168.jpg 277w, uploads/2013/09/saturacao-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />

## Luminosidade

A luminosidade é a escala de claridade. Esta propriedade está ligada a percepção de brilho. Quanto maior a luminosidade de uma cor mais próxima ela estará do branco e quanto menor a luminosidade mais próxima ela estará do preto.

<img class="alignnone size-full wp-image-39009" alt="luminosidade" src="http://tableless.com.br/uploads/2013/09/luminosidade.jpg" width="660" height="400" srcset="uploads/2013/09/luminosidade.jpg 660w, uploads/2013/09/luminosidade-277x168.jpg 277w, uploads/2013/09/luminosidade-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />

# Contraste

Em linhas gerais contraste é uma relação de oposição ou distinção entre dois objetos. Ou seja: coisas que são diferentes umas das outras. Em teoria da cores isto pode significar uma diferença em relação a matiz, saturação e / ou luminosidade. Viu por que era importante entender os outros conceitos? Quanto mais alto o contraste mais diferentes são as cores e portanto mais fácil de serem distinguidas, quanto mais baixo mais próximas elas são e mais difícil é esta tarefa.

<img class="alignnone size-full wp-image-39004" alt="contraste3" src="http://tableless.com.br/uploads/2013/09/contraste3.jpg" width="660" height="400" srcset="uploads/2013/09/contraste3.jpg 660w, uploads/2013/09/contraste3-277x168.jpg 277w, uploads/2013/09/contraste3-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />

## Uma questão de percepção

A percepção de contraste varia de pessoa para pessoa e pode piorar com fatores como envelhecimento ou deficiências visuais… Ou seja, bom contraste é questão de acessibilidade! Algumas pesquisas indicam que jogar videogames melhor a percepção de contraste, então está aí uma boa desculpa para a jogatina!

## Bom vs. Mal Contraste

Mas não basta ser simplesmente diferente para ser bom. Você já sabe intuitivamente que algumas combinações de cores são esquisitas. Um texto magenta em um fundo verde limão, por exemplo, é bem difícil de ler. Em termos práticos, principalmente quando estamos falando de fundos para texto, contraste entre luminosidade diferentes são mais confortáveis para a visão. Por isto que é ótimo ler textos pretos em um fundo branco. Ou vice-versa. Evite cores de luminosidade semelhante, mesmo que elas possuam matizes diferentes.

<img class="alignnone size-full wp-image-39002" alt="contraste1" src="http://tableless.com.br/uploads/2013/09/contraste1.jpg" width="660" height="400" srcset="uploads/2013/09/contraste1.jpg 660w, uploads/2013/09/contraste1-277x168.jpg 277w, uploads/2013/09/contraste1-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />

Quer um bom teste prático? Se o texto estiver vibrando (dando a impressão de estar pulsando) significa que é péssimo para a leitura!

### A fórmula do contraste

Ainda está na dúvida? Bem, a [W3C criou uma fórmula][2] para medir o contraste levando em conta a relação entre brilho e diferença de cor.

Vamos considerar:

R = vermelho
  
G = verde
  
B = azul
  
1 = cor número 1
  
2 = cor número 2

Para calcular o brilho (luminoside) utilize o valor RGB sendo:
  
((R X 299) + (G X 587) + (B X 114)) / 1000

Para calcular a diferença de cor:
  
(máximo (R1, R2) &#8211; mínimo (R1, R2)) + (máximo (G1, G2) &#8211; mínimo (G1,G2)) + (máximo (B1, B2) &#8211; mínimo (B1, B2))

O contaste está bom se o brilho for maior que 125 e a diferença de cor maior que 500.

Se você não curte matemática use esta [calculadora][3]. Basta inserir os valores em HEX ou RGB.

### Baixo contraste como estilo

Antes de sair apontando o dedo que o layout do amiguinho está com baixo contraste lembrem-se que existem alguns contextos onde isto é proposital. A intenção pode ser diminuir o destaque de algum elemento ou simplesmente criar um efeito interessante. Mas utilize esta técnica com moderação e apenas para trechos curto de texto. Tudo bem utilizar o baixo contraste em um banner &#8211; título branco sobre imagem colorida, por exemplo &#8211; mas se você utilizar esta técnica para grandes blocos de texto é provável que seu usuário nem se dê ao trabalho de ler. Alias, quanto menor mais importante o contraste!

# Circulo Cromático

Bem, um mano chamado Goethe achou que seria interessante organizar esta zona. Em 1810 ele dividiu as cores do espectro visível (aquelas do arco-íris que a gente aprende na escola) em um circulo cromático, ou, para os íntimos, roda das cores. Quanto mais longe uma cor estiver no círculo, maior o contraste.

<img class="alignnone size-full wp-image-39008" alt="goethe" src="http://tableless.com.br/uploads/2013/09/goethe.jpg" width="660" height="400" srcset="uploads/2013/09/goethe.jpg 660w, uploads/2013/09/goethe-277x168.jpg 277w, uploads/2013/09/goethe-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />

Este círculo cromático foi a base de diversos sistemas de cores. De métodos artísticos para mistura de cores até esquemas voltados para a computação gráfica. O RGB e o CMYK possuem os seus próprios círculos cromáticos.

<img class="alignnone size-full wp-image-39011" alt="rgb" src="http://tableless.com.br/uploads/2013/09/rgb.jpg" width="660" height="400" srcset="uploads/2013/09/rgb.jpg 660w, uploads/2013/09/rgb-277x168.jpg 277w, uploads/2013/09/rgb-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />

## Complementares

Cores complementares são as cores opostas no circulo cromático. Como o contraste é super alto elas são bem uteis para chamar atenção. Isto pode, dependendo da situação, até salvar a vida de uma pessoa. Boias e botes salva-vidas, por exemplo, são laranjas para contrastar com o azul do mar. E azul e laranja são &#8211; você já adivinhou &#8211; cores complementares! Este tipo de contraste é ótimo para ressaltar elementos em imagens e layouts.

<img class="alignnone size-full wp-image-39001" alt="complementares" src="http://tableless.com.br/uploads/2013/09/complementares.jpg" width="660" height="400" srcset="uploads/2013/09/complementares.jpg 660w, uploads/2013/09/complementares-277x168.jpg 277w, uploads/2013/09/complementares-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />

Mas tome cuidado! A tendência é que cores complementares produzam vibrância e ressaltarem a luminosidade uma da outra quando próximas. Ou seja, contraste deste tipo são péssimos para textos. Quando combinados com matizes com luminosidade alta o efeito é desastroso. Lembra-se do texto rosa no fundo verde? Pois é. São cores complementares no circulo RGB.

<img class="alignnone size-full wp-image-39003" alt="contraste2" src="http://tableless.com.br/uploads/2013/09/contraste2.jpg" width="660" height="400" srcset="uploads/2013/09/contraste2.jpg 660w, uploads/2013/09/contraste2-277x168.jpg 277w, uploads/2013/09/contraste2-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />

## Análogas

São as cores vizinhas no circulo. Pelas matizes serem mais parecidas o contraste tende a ser mais baixo e a combinação mais harmoniosa.

<img class="alignnone size-full wp-image-39000" alt="analogas" src="http://tableless.com.br/uploads/2013/09/analogas.jpg" width="660" height="400" srcset="uploads/2013/09/analogas.jpg 660w, uploads/2013/09/analogas-277x168.jpg 277w, uploads/2013/09/analogas-511x310.jpg 511w" sizes="(max-width: 660px) 100vw, 660px" />

# Paletas funcionais

Ok. Chega de teoria. Vamos ver como aplicar estas informações para a criação de layouts. Lembre-se que em design você não deve escolher nada aleatoriamente ou por que &#8220;fica bonitinho&#8221;. É preciso ter um propósito e uma função para os elementos e com a cor não poderia ser diferente. Uma técnica útil é atribuir uma função para cada cor e desta forma transmitir significado.

#### Principal

O primeiro passo é escolher uma matiz principal. Normalmente esta cor já está definida no branding e costuma corresponder a cor dominante do logotipo, por exemplo. Se não for o caso tente tomar uma decisão de acordo com a mensagem que você deseja transmitir. Leve em consideração os temas retratados neste artigo e pesquise ao menos o básico sobre psicologia das cores. Esta cor principal deverá ser utilizada para elementos como títulos em destaque, links, botões, navegação, etc.

#### Secundária

O segundo passo é definir uma cor secundária. A função desta cor será criar um contraste com a primeira. Ela é útil para itens da interface que demandam extrema atenção como chamadas para a ação (botões de compra, cadastro, login, etc.) ou títulos pontuais. Esta cor deverá ser utilizada com cuidado para que crie realmente um destaque em relação ao restante do layout. Uma dica é escolhe ruma cor análoga ou complementar como cor secundária.

#### Base

Com estas duas cores definidas o próximo passo é definir uma base. Esta é a cor que vai servir de background, portanto escolha matizes que tenham pouca vibrância. Procure utilizar tons neutros como preto, branco, cinza ou uma variação com grande contraste da cor principal. Por exemplo, se sua matiz principal for azul escuro você pode definir um azul bem clarinho como base. Ou vice-versa.

#### Texto

A próxima função é texto. O segredo aqui é criar um bom contraste com a base. A legibilidade é essencial. Na dúvida utilize base branca e texto preto ou cinza escuro. Não tem como errar!

#### Alerta

Esta é a cor utilizada para momentos de extrema atenção como mensagens de erro e validação de formulário. Matizes quentes como amarelo, vermelho e laranja costumam ser boas cores de alerta. Lembre-se que isto não significa necessariamente textos. Esta cor pode ser utilizada como background de uma janela, ícone ou botão, por exemplo. Com o uso inteligente das cores o seu usuário intuitivamente sabe quando aconteceu ou não um problema sem precisar ao menos ler a mensagem.

#### Sucesso

A função desta cor é transmitir textos relacionados a acertos. A mensagem foi enviada com sucesso? O formulário validou sem erros? O arquivo foi salvo? Utilize cores de sucesso. Matizes frias como azul e verde costumam ser ótimas para passar o recado. Novamente o uso não precisa se restringir a textos.

## Classes funcionais

Com uma ajudinha de um pré-processador você pode transformas estas matizes em variáveis e mixins. Desta forma reaproveitar o código fica muito mais fácil. Este é o segredo básico dos frameworks e dominando esta técnica você pode criar o seu próprio muito mais facilmente. E pensando nestas funções deste a fase de criação do layout o desenvolvimento se torna muito mais ágil.

<img class="alignnone size-full wp-image-39005" alt="funcao1" src="http://tableless.com.br/uploads/2013/09/funcao1.jpg" width="660" height="201" srcset="uploads/2013/09/funcao1.jpg 660w, uploads/2013/09/funcao1-329x100.jpg 329w, uploads/2013/09/funcao1-588x179.jpg 588w" sizes="(max-width: 660px) 100vw, 660px" />

Vejamos como ficaria a paleta apresentada acima em CSS + LESS. Primeiro definimos as variaveis:

<pre class="lang-css">@principal:  #008fb2;
@secundaria: #ef7200;
@base:       #fbfbfb;
@texto:      #333;
@alerta:     #bf0500;
@sucesso:    #0abf7e;</pre>

Abaixo definimos a cor base como background do corpo do documento, a cor padrão para todos os textos, a cor principal como cor para links.

<pre class="lang-css">body {
background: @base;
color: @texto;
}

a {
color: @principal;
}</pre>

<img class="alignnone size-full wp-image-39015" alt="funcao-exemplo" src="http://tableless.com.br/uploads/2013/09/funcao-exemplo.jpg" width="660" height="201" srcset="uploads/2013/09/funcao-exemplo.jpg 660w, uploads/2013/09/funcao-exemplo-329x100.jpg 329w, uploads/2013/09/funcao-exemplo-588x179.jpg 588w" sizes="(max-width: 660px) 100vw, 660px" />

Este é um pequeno exemplo do que pode ser feito utilizando cores funcionais e pré-processadores. Mas as possibilidades são infinitas. Podemos criar variações mantendo a matiz das cores e apenas modificando valores como matiz e saturação para criar efeitos interessantes. Podemos, por exemplo, escurecer em 20% a cor principal para um efeito de hover.

<pre class="lang-css">a:hover {
color: darken(@principal, 20%);
}</pre>

<img class="alignnone size-full wp-image-39007" alt="funcao3" src="http://tableless.com.br/uploads/2013/09/funcao3.jpg" width="660" height="112" srcset="uploads/2013/09/funcao3.jpg 660w, uploads/2013/09/funcao3-329x55.jpg 329w, uploads/2013/09/funcao3-588x99.jpg 588w" sizes="(max-width: 660px) 100vw, 660px" />

É possível criar variações bem interessantes apenas variando a cor e luminosidade.

<img class="alignnone size-full wp-image-39006" alt="funcao2" src="http://tableless.com.br/uploads/2013/09/funcao2.jpg" width="660" height="201" srcset="uploads/2013/09/funcao2.jpg 660w, uploads/2013/09/funcao2-329x100.jpg 329w, uploads/2013/09/funcao2-588x179.jpg 588w" sizes="(max-width: 660px) 100vw, 660px" />

É claro, se você não curte utilizar pré-processadores pode fazer este tipo de mistura na unha. Só é um pouquinho mais trabalhoso, mas no final você tem um layout super harmonioso. Experimente criar variações de saturação, mistura e combinação de cores para efeitos interessantes.

### Mais funções

As funções apresentadas aqui são apenas sugestões. Você pode criar quantas outras desejar como padrões para informações, risco, elementos inativos, etc. A sua imaginação é o limite.

# Blocagem de cor

Uma caracteristica do flat design é o uso de poucos elementos como linhas, sombras, ribbons, etc. A separação de conteúdo pode ser feita através de blocos de cores diferentes. Isto funciona bem principalmente para sites com uma grande quantidade de rolagem vertical. Esta técnica é chamada de color blocking.

## Um mini case

No [portfólio][4] da minha empresa eu utilizei o color blocking para separar os trabalhos de cada cliente na página inicial. Cada bloco deveria ser mais ou menos correspondente a matiz dominante do case apresentado, por isto criei uma boa quantidade de variações (24 matizes). Desta maneira o bloco sempre combina com a identidade visual de cada cliente.

[<img class="alignnone size-full wp-image-39013" alt="paleta-exemplo" src="http://tableless.com.br/uploads/2013/09/paleta-exemplo.jpg" width="660" height="527" srcset="uploads/2013/09/paleta-exemplo.jpg 660w, uploads/2013/09/paleta-exemplo-210x168.jpg 210w, uploads/2013/09/paleta-exemplo-388x310.jpg 388w" sizes="(max-width: 660px) 100vw, 660px" />][5]

Para evitar a junção de cores vibrantes eu intercalei blocos coloridos com neutros (brancos com texto preto e vice-versa). Na maior parte dos blocos os textos e botões ficaram nas cores brancas, mas para evitar problemas de contraste utilizei o cinza escuro para cores com alta luminosidade como no caso do amarelo.

# Não esqueça de calibrar o monitor&#8230;

Eu lembro quando estava na minha fase sobrinha, dando os primeiros passos na área de design. Um dos primeiros jobs que fiz foi um cartão postal com uma ilustração de um boneco de neve fofo e um céu azulzinho… Exceto que quando olhei em outro computador o céu estava bege! Na verdade todas as cores estavam esquisitas. O problema era o meu monitor que estava muito, mas muito mal calibrado. Eu consegui corrigir o trabalho a tempo, mas o resultado poderia ter sido desastroso. Monitores &#8211; principalmente os fabricados na China vendidos a preço de banana &#8211; precisam ser calibrados de tempos em tempos. Não é algo que você precisa fazer todo o dia. Cerca de uma vez por mês é o ideal. É possível modificar o perfil de cores através das configurações padrões do seu sistema, utilizar softwares específicos, ferramentas online ou até mesmo através de um hardware chamado colorímetro (o que é muito mais preciso). Então se o Twitter parece cinza ou Youtube laranja faça ao seu cliente e a si mesmo um favor: calibre seu monitor. Ou você pode acabar com um céu bege.

## Esteja preparado para o pior

Por mais irônico que pareça, as vezes o seu monitor está bem calibrado DEMAIS e isto pode causar uns pepinos… Em um mundo ideal isto não seria um problema. Alias, do ponto de vista da criação gráfica a fidelidade de cores é imprescindível. Mas na real é bem difícil que o usuário padrão se preocupe com isto. A não ser que o seu público alvo esteja apenas entre designers, cineastas, fotógrafos e gamers é bem provável que grande parte das pessoas estão acessando o seu site de um monitor vagabundo. Para garantir que todos os usuários &#8211; com o monitor bem calibrado ou não &#8211; tenham uma experiência bacana teste seu trabalho na maior quantidade de telas possíveis! Experimente o layout especialmente naquele tubão pré-histórico da casa da sua avó&#8230; Assim você terá uma idéia do pior que pode acontecer.

## Outras influências

Vale lembrar que não é só a calibração que influência na percepção de cores. A iluminação ambiente e configurações do computador como modo de economia de energia também podem produzir diferenças de contraste, brilho e saturação. O objetivo aqui não é ficar com as cores idênticas em todas as máquinas, pois isto é impossível, mas manter um bom nível de contraste, leitura e acessibilidade é essencial. De nada adianta um layout que só fica bacana no seu computador, certo?

# Conclusão

Bem, esta foi só a ponta do iceberg. Existe muito a ser estudado sobre teoria das cores. Ainda restam os aspectos físicos, biológicos, psicológicos, culturais, colorimetria&#8230; Mas com este artigo vocês já tem as ferramentas básicas para criarem ótimas paletas de cores funcionais. Até a próxima!

 [1]: http://tableless.com.br/sobre-cor-e-webdesign/ "Sobre Cor e Webdesign"
 [2]: http://www.w3.org/TR/AERT#color-contrast "W3C.org - Color Contrast"
 [3]: http://snook.ca/technical/colour_contrast/colour.html "Colour Contrast"
 [4]: http://www.popupdesign.com.br "PopUp Design"
 [5]: http://www.popupdesign.com.br