---
title: Botões em UI Design
authors: Willian Matiola
type: post
paid: true
publishdate: 2018-01-15
date: 2018-01-15
image: https://i.imgur.com/9z3fw2C.jpg
excerpt: O botão é um dos elementos de UI mais comuns e está presente em praticamente qualquer interface.
categories:
  - Design
  - UX
tags:
  - design
  - ux
  - frameworks
---

O botão é um dos elementos de UI mais comuns e está presente em praticamente
qualquer interface. Contudo, embora seja relativamente simples criar um botão,
não podemos deixar de lado a quantidade de nuances que podemos analisar para
criá-los de uma maneira melhor.

Neste artigo nós vamos nos aprofundar em várias características que compõem um
botão. Mergulharemos em diversos aspectos que te ajudarão a entender as melhores
formas de explorar esse elemento que pode ser pequeno em tamanho, mas grande em
possibilidades.

## Anatomia de um botão

Vamos fazer um exercício rápido. Imagine rapidamente um botão. Imaginou? Será
que sua imaginação levou você a formar a imagem mental de um botão retangular,
com alguma cor, bordas arredondadas e o texto centralizado no meio? Se sim, bem
vindo ao clube.

Mas além desses três grandes atributos — *cor, forma e tipografia* — podemos
destrinchá-lo ainda mais.

![](https://i.imgur.com/ciMiQe4.png)
<span class="figcaption_hack">Anatomia de um Botão — UI Lab</span>

Analisando a imagem acima, podemos contabilizar mais 4 características:
**padding **(espaçamento interno entre o texto e a forma do botão), **margem
**(espaçamento do botão com outros elementos na interface), bordas arredondadas
e sombra. Além disso, temos todas as características da tipografia utilizada:
cor, tamanho, peso e família da fonte.

Um botão simples como o nosso exemplo tem 11 características. E nós nem
incluímos um ícone para ele, porque se tivéssemos feito, a quantidade de
características seria bem maior. E quando colocamos isso num contexto em que
**cada detalhe de design importa**, já temos aí várias tomadas de decisões na
hora de criarmos nossos botões.

## Tipos de botões

Existem diversos tipos de botões e cada um deles têm uma função bem específica
dentro da interface. Neste tópico veremos aqueles que acho os mais comuns.

### **CTA — Call to Action**

O botão *Call to Action* — chamada para ação em português — , é utilizado para
indicar ao usuário o que ele deve fazer primeiro na tela. Ele geralmente possui
uma forma diferenciada dos demais botões. Pode ter um tamanho maior ou uma cor
que tenha um contraste acentuado em relação aos outros elementos. É muito comum
ver esses botões em *landing pages* que estão vendendo algum produto ou serviço.

![](https://i.imgur.com/JX9VdCw.png)
<span class="figcaption_hack">[Product Page — Hotjar](https://dribbble.com/shots/4074050-Product-page-Hotjar)</span>

![](https://i.imgur.com/FUxkUDo.png)
<span class="figcaption_hack">[Financial Application
Website](https://dribbble.com/shots/4068584-Finance-Application-Website)</span>

![](https://i.imgur.com/GLoBzMH.png)
<span class="figcaption_hack">[Pencakdoor](https://dribbble.com/shots/4063006-Pencakdoor)</span>

### Primário

O botão primário é aquele que será **utilizado com maior frequência** dentro da
interface. É por meio dele que indicaremos aos usuários todas as ações que
queremos que ele faça. Por conta disso, suas características precisam chamar
atenção, mas não da mesma forma que o CTA.

Para definir o estilo do botão primário você pode explorar as cores da marca ou
uma cor que se diferencie da interface. Nos exemplos a seguir podemos perceber
como o designer definiu uma cor de destaque para os botões primários em ambas as
interfaces.

![](https://i.imgur.com/YEg3p4k.png)

![](https://i.imgur.com/8Afj7XS.png)

![](https://i.imgur.com/U5XX51M.png)

![](https://i.imgur.com/QgfTxme.png)

### Secundário

O botão secundário é utilizado quando queremos mostrar duas ações mas a primeira
delas é a ação principal. No MacOS, por exemplo, quando queremos esvaziar a
lixeira, o sistema mostra uma caixa de diálogo com duas opções: *Cancel* (em
branco) e *Empty Trash* (em azul). Como nossa ação principal é, de fato,
esvaziar a lixeira, o botão primário ganha mais destaque do que a ação
secundária.

![](https://i.imgur.com/JNjaC21.png)

É sempre bom lembrar que os botões secundários, em hipótese alguma, devem se
parecer com botões desabilitados. Isso quer dizer que você deve evitar o uso do
cinza em botões secundários porque pode acontecer algo assim:

![](https://i.imgur.com/p3e8lXN.png)
<span class="figcaption_hack">Qual deles está desabilitado e qual deles é o secundário?</span>

### Ghost Button

Esse tópico vai ser um pouco mais longo que os anteriores. Isso porque há
algumas controvérsias no uso dos G*host Buttons*.

Mesmo que você desconheça o termo, provavelmente já deve ter visto algum botão
fantasma por aí. Eles são formas sem preenchimento e possuem apenas uma borda e
tipografia. Há quem diga que sua origem veio depois que a Microsoft lançou o
sistema de design Metro, outros atribuem o seu aparecimento depois que Apple
lançou o iOS 7. Independente de quem começou com isso, é certo que de lá pra cá
eles ganharam bastante popularidade.

![](https://i.imgur.com/BpHJ0sD.jpg)
<span class="figcaption_hack">Vários exemplos de Ghost Buttons</span>

Agora vamos aos prós e contras desse estilo.

**Prós:**

* São muito fáceis de criar;
* Criam um ponto focal em sites que são essencialmente imagéticos. Em outras
palavras, se você coloca um *Ghost Button* em cima de uma imagem com um
contraste adequado você consegue chamar atenção sem sobrecarregar visualmente o
site.
* Melhoram a estética. Por sua natureza simplista, conseguem manter a interface
*clean.*
* São fáceis de integrar. Novamente, por serem simples, se adaptam facilmente em
diferentes estilos.

**Contras:**

* Contraste. Quando colocados sobre uma imagem ou vídeo, podem acabar
desaparecendo por falta de contraste.
* Clareza. Dependendo da sua audiência e do contexto em que ele é aplicado, pode
ser difícil identificá-lo como um botão.
* Conversão. Vários testes ([teste
1](https://www.elevatedthird.com/news-insights/ghost-buttons-good-bad-spooky-part-1),
[teste
2](https://www.elevatedthird.com/news-insights/ghost-buttons-good-bad-spooky-part-2))
realizados comparando um *Ghost Button* com um botão normal mostraram uma
diminuição significativa na conversão das páginas com o botão fantasma.

Como designer, cabe a você encontrar as melhores soluções para driblar os
problemas que um *Ghost Button* pode trazer para o projeto. E nunca é tarde para
lembrar que um *Ghost Button* tem mais valor como botão secundário do que como
primário. Muitos designers utilizam essa abordagem para destacar o botão
principal ao mesmo tempo que mantém a interface limpa.

![](https://i.imgur.com/M7VMhLj.jpg)
<span class="figcaption_hack">Ghost Buttons sendo utilizados como auxiliar ao botão primário.</span>

Na dúvida, sempre teste o que é melhor para atingir os objetivos do projeto!

### Botões com ícones

Você vai encontrar ícones nos botões tanto no lado esquerdo quanto no direito.
Confesso que não consegui encontrar nenhuma especificação a respeito disso, mas
*a priori*, se observarmos bem, o ícone do lado esquerdo sempre tenta
representar a ação primária do botão, já o ícone do lado direito geralmente
significa que haverá uma continuação da ação.

Os ícones do lado esquerdo são mais representativos, já os do lado direito
geralmente são setas. Pode parecer confuso mas os exemplos a seguir vão clarear
melhor o que eu quero dizer.

![](https://i.imgur.com/Q8EMPB5.jpg)
<span class="figcaption_hack">Botões com ícones no lado esquerdo.</span>

![](https://i.imgur.com/f3QVSGh.jpg)
<span class="figcaption_hack">Botões com ícones no lado direito.</span>

Ainda sobre o assunto, um colega que trabalha com UX na Booking argumentou que
na cultura ocidental existe uma **correlação** **de progresso** quando o ícone
está do lado direito. Todavia, correlacionar um ícone do lado direito com uma
ação de continuidade vai depender do contexto onde ele está inserido.

A **cultura** e o **ecossistema** são dois contextos para levar em consideração.
Culturalmente, países orientais leem da direita pra esquerda e essa é a sensação
de progresso deles. E quando falamos de ecossistema, se todos os botões com
ícones no lado direito indicam progresso, quando houver algum deles que deveria
se encaixar, mas não se encaixa nesse ecossistema, vai haver uma quebra no
padrão que estava sendo estabelecido desde o começo.

**Alinhamento de ícones nos botões: **para encerrar essa seção, gostaria de
deixar uma imagem com dicas práticas de como alinhar seus ícones dentro dos
botões.

![](https://i.imgur.com/sAiXKg6.png)
<span class="figcaption_hack">Por Vadim Zaycev — [Veja o post
original](https://medium.com/@vadimzaycev/rules-of-creating-buttons-with-icon-120d2980bef8)</span>

### Floating Action Button (FAB)

Esse tipo de botão foi introduzido pela primeira vez no [Material
Design](https://material.io/), o sistema de design da Google.

![](https://i.imgur.com/aCrhjjw.jpg)
<span class="figcaption_hack">Floating Action Button</span>

Nas [especificações do Material
Design](https://material.io/guidelines/components/buttons-floating-action-button.html#)
encontraremos que o FAB é utilizado para promover uma **ação primaria na UI**.
Também é recomendado que não seja utilizado mais de um FAB na tela e que se opte
por um dos dois tamanhos disponíveis: o **padrão (56px)** ou o **mini (40px)**.

Devido a sua flexibilidade e capacidade de adaptação em diferentes cenários, o
FAB acabou sendo uma solução interessante para diversos casos. Mas é necessário
bom senso para não torná-lo uma muleta para soluções pobres de Design.

![](https://i.imgur.com/kkP9Irh.gif)

![](https://i.imgur.com/W4Qapmu.gif)
<span class="figcaption_hack">Exemplos de Floating Action Button</span>

## Tamanhos

Os tamanhos mais comuns são: **pequeno**, **médio** e **grande**. Você pode
também adicionar os tamanhos **extra pequeno** e **extra grande** se for
necessário.

Um bom exemplo de tamanhos bem definidos pode ser encontrado no [style guide da
Marvel App](https://marvelapp.com/styleguide/). Eles possuem o botão **extra
small** com 24px de altura, o **small** com 30px e os próximos botões progridem
sua altura de 10 em 10px. Além disso, o *font-size* sofre alteração em 3
ocasiões: no botão *extra small* (14px), no botão *extra large* (18px) e os
demais com 16px

![](https://i.imgur.com/T4pC6tw.jpg)
<span class="figcaption_hack">Botões da Marvel App</span>

Outro tipo de tamanho que você precisa se preocupar é quando estamos projetando
**apps mobile**. A maioria das ações em um *smartphone* ou *tablet* é feita com
os **dedos indicador** ou o **dedão**. Pensando nisso, qual o tamanho ideal para
os botões no mobile?

De acordo com um estudo realizado pelo [MIT Touch
Lab](https://touchlab.mit.edu/publications/2003_009.pdf), a média do dedo
**indicador** das pessoas é de 1.6 a 2cm, que equivale a **47–57 pixels**. Já a
média de tamanho do **dedão** é de 2.5cm, ou **72 pixels**.

Em telas muito pequenas e dependendo da quantidade de botões que precisam
aparecer, ficará difícil utilizar os tamanhos acima. O mais adequado nesse
cenário é ler as *guidelines* dos sistemas que você está desenvolvendo. A Apple,
por exemplo, recomendava que os botões tivessem no mínimo 44x44px; já o guia do
Windows Phone da Microsoft recomendava um tamanho mínimo de 34px. Então faça o
trabalho de casa e tente não colocar botões muito pequenos ou muito grandes na
sua UI Mobile.

## Cores

Tratando-se de cores não há muito segredo. Geralmente as próprias cores da marca
servem como auxílio para quando precisamos escolher as cores para os botões da
UI. A **cor primária** da sua marca acaba servindo, em muitos casos, como a cor
do **botão primário**, a **cor secundária** como a do botão **secundário**, e
assim por diante.

Mas antes de sair colorindo tudo por aí, você deve prestar atenção em algumas
coisas:

**Contraste:** um botão só é eficiente quando ele é percebido, e para isso
acontecer ele precisa de contraste. É necessário que a cor do botão contraste
com o fundo onde ele está inserido. E também é necessário que a cor do texto
dentro do botão tenha contraste com a cor do próprio botão.

![](https://i.imgur.com/TtJZlMB.jpg)

**Contexto: **tente pensar no contexto como o ambiente na qual aquela cor estará
inserida. Se você já estudou um pouco sobre **psicologia das cores** e os
significados que elas carregam, sabe que cada cor pode funcionar melhor se o
contexto onde ela for aplicada é compatível. Um bom exemplo é: seu site ou
sistema quer dar um ar de tranquilidade e segurança para o usuário, você
provavelmente não usará cores quentes (vermelho, laranja e amarelo), porque elas
aceleram nossos batimentos cardíacos ou despertam sensações de agitação e
inquietude.

**Acessibilidade:** de acordo com o site
[https://www.color-blindness.com](https://www.color-blindness.com/), 1 em cada 12
homens (8%) e 1 em cada 200 mulheres (0.5%) sofre de algum tipo de
**daltonismo**, ou seja, possuem dificuldade de enxergar e diferenciar certas
cores. Sabendo disso, podemos fazer a escolha das cores de uma maneira que
abrange essa parcela de pessoas e garanta uma experiência agradável para elas
também.

![](https://i.imgur.com/b9iXhx3.jpg)
<span class="figcaption_hack">Uma pessoa com o tipo de daltonismo Deuteranopia não consegue diferenciar o
vermelho do verde em alguns casos.</span>

Se você utiliza Sketch App para criar suas interfaces, instale o plugin
**Spark**. Ele possibilita testar rapidamente como suas cores se comportam em
diferentes cenários de daltonismo.

## Estados

Os estados dos botões servem para dar feedback ao usuário sobre as ações que
estão acontecendo quando há uma interação com o botão.

![](https://i.imgur.com/3YSSbqC.jpg)

A definição dos estados são:

* **Normal:** o estado padrão do botão, como ele é exibido naturalmente na
interface;
* **Hover:** o estado quando o cursor do mouse está sobre o botão;
* **Pressionado:** acontece quando clicamos e mantemos o clique ou também pode ser
visto em situações onde temos mais de uma opção para escolher
* **Foco:** não costuma ser muito utilizado, mas ele mostra o botão com uma luz
clara ao redor. Você verá esse estado mais presente em campos de formulários;
* **Inativo:** botões inativos são indicados com a cor cinza e sua ação
está…inativa.
* **Progresso:** o estado que indica que uma ação ainda está acontecendo.

## Estilos

Além das diferentes formas geométricas que podemos utilizar, também temos um
leque bem grande de estilos. Trouxe aqui os cinco mais populares e serei breve
em relação a cada um deles.

### **Flat**

Lembro que a primeira vez que vi o estilo *flat* foi na proposta da Microsoft
com o Metro. Depois disso vários sites e sistemas passaram a adotar esse estilo.

![](https://i.imgur.com/EOeIzSe.jpg)
<span class="figcaption_hack">Botões Flat</span>

Como o próprio nome já diz, o estilo *flat* — plano — é essencialmente uma única
cor, sem profundidade e sem nenhum efeito.

Há quem defenda o estilo e há quem recrimine. O argumento é que botões *flat*
**não deixam claro para o usuário que ele é algo clicável**.

### **Almost Flat**

Como solução a problemática dos botões flat surgiu a vertente dos botões *almost
flat* (quase plano). A única diferença do seu antecessor é que os botões agora
possuem uma leve sombra para indicar que ele é um elemento clicável.

![](https://i.imgur.com/vklhYsp.jpg)
<span class="figcaption_hack">Botões Almost Flat</span>

Se não estou enganado, a Google foi a responsável pela introdução desse estilo
ao mostrar no Material Design a relação das sombras e elevações de um elemento
baseando em estudos de objetos reais.

### **Skeumórfico**

O estilo Skeumórfico teve seu fim em 2012 quando a Apple, sua maior entusiasta,
mudou a interface do iOS 7 para o estilo flat.

![](https://i.imgur.com/YeXKvw2.jpg)
<span class="figcaption_hack">Botões Skeumórficos</span>

Em poucas palavras, os elementos skeumórficos tendem a se parecer com objetos da
vida real. Uma calculadora digital vai ter sombras e luzes para simular uma
calculadora real, um app de notas vai simular o papel e o couro, e todo o tipo
de breguice que você pode imaginar.

E sendo sincero, não sinto saudades dessa época.

### Gradiente

Uma outra alternativa ao estilo *flat* foi aplicar gradientes nos botões. Eles
podem variar de gradientes horizontais a gradientes verticais.

![](https://i.imgur.com/aPLRMrN.jpg)
<span class="figcaption_hack">Botões com Gradiente</span>

Particularmente gosto bastante desse estilo. Mas é necessário cuidado e prática
para criar gradientes que tenham contraste com o fundo e sejam visualmente bem
resolvidos.

### Gradiente iluminado

Uma evolução do estilo anterior que ganhou tração em 2017 e parece que seguirá
firme e forte em 2018 são os botões com gradientes iluminados. Você
provavelmente já deve ter visto algo desse tipo no Dribbble ou Behance.

![](https://i.imgur.com/nr9nmRE.jpg)
<span class="figcaption_hack">Botões com Gradiente Iluminado</span>

Adicionar uma luz no botão só vai dobrar os cuidados que você vai precisar ter
na hora de aplicá-lo em alguma interface.

## Tom de voz do botão

![](https://i.imgur.com/ragnU7X.png)
<span class="figcaption_hack">Botões do site enjoei.com.br</span>

Não adianta ter um botão bonito se ele não comunica direito, certo? O tom de voz
de um botão é, essencialmente, como ele vai comunicar qual é a sua ação. Se você
criou um botão de download é esperado que ele comunique "**Baixar**" e não
"**Clique aqui**".

O tom de voz dos botões é algo que tem que estar alinhado com o tom de voz da
sua marca. Um exemplo prático e muito bem feito do que eu estou falando pode ser
visto em toda a interface do Enjoei. Eles fazem um belo trabalho de [Interface
Writing](https://medium.com/ui-lab-school/interface-writing-amigÃ¡vel-para-maximizar-a-experiÃªncia-de-uso-de-um-produto-a2b8a668afc7)!

## Conclusão

Você talvez não acredite, mas deixei de fora muitas coisas que ainda podemos
falar sobre botões. Como mencionei logo no início do artigo, temos muitas
nuances para prestar atenção se quisermos criar esses elementos de uma forma
realmente bem feita.

Mas acredito que este artigo já é o suficiente para apresentar as possibilidades
que nós podemos explorar. Principalmente se estivermos desenvolvendo sistemas de
design com vários componentes.

Espero que tenha gostado e fique a vontade para comentar.

## Referências

* [Primary & Secondary Action Buttons](https://uxplanet.org/primary-secondary-action-buttons-c16df9b36150)
* [Better CTA Buttons: Step by Step in UI Design](https://medium.muz.li/malachidigest-e5b0244209a4)
* [Best Practices for Buttons — The User Experience of colors](https://uxplanet.org/best-practices-for-buttons-b7048479d440)
* [Ghost Buttons in UX Design](https://uxplanet.org/ghost-buttons-in-ux-design-4cf3717334f8)
* [Compact & Powerful: Great Examples of Floating Action Buttons in Interfaces](https://stories.uplabs.com/compact-powerful-great-examples-of-floating-action-buttons-in-interfaces-7079b9926cb5)
* [Buttons in Design Systems](https://medium.com/eightshapes-llc/buttons-in-design-systems-eac3acf7e23?ref=heydesigner-weekly)
* [Buttons in UI Design: The Evolution of Style and Best Practices](https://uxplanet.org/buttons-in-ui-design-the-evolution-of-style-and-best-practices-56536dc5386e)
* [Rules of creating buttons with icon](https://medium.com/@vadimzaycev/rules-of-creating-buttons-with-icon-120d2980bef8)
