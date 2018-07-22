---
title: O que você deve saber sobre o funcionamento do React Native
authors: Rafael Câmara
type: post
publishdate: 2018-04-23
date: 2018-04-23
excerpt: Como o React Native realmente funciona por baixo dos panos
image: https://i.imgur.com/r8YDSgE.jpg
categories:
  - javascript
tagS:
  - reactjs
  - Tecnologias e tendências
---

Já faz algum tempo que acompanho diversos artigos e uma coisa que
eu sinto falta é saber quem está por trás daquele post. Então, acabo sempre
dando scroll até o fim do post e procurando entender um pouco melhor sobre o
autor antes mesmo de começar a ler o conteúdo produzido por ele.

Então, pensando nisso, aqui vai uma breve introdução sobre mim: meu nome é
**Rafael Câmara**, sou desenvolvedor *frontend* apaixonado por design, há cerca
de seis anos e atualmente venho focando meus estudos e trabalhos em **React** e
**React Native**.

Durante estes últimos meses de estudos e trabalhos, algumas coisas me
incomodavam profundamente:

* Como o React Native realmente funciona por baixo dos panos, tirando toda a abstração?
* Quais são as suas reais diferenças em relação aos seus "concorrentes" como Ionic/Cordova?

Bem que eu poderia ter entrado no código e ter estudado cada uma das funções a
fim de entender o que faz o React Native ser tão especial, mas como todo bom
desenvolvedor, resolvi recorrer ao nosso querido amigo Google. E uma coisa
acabou me surpreendendo… Você encontra diversos posts sobre como iniciar em
React Native ou como resolver uma determinada situação, mas o conteúdo
relacionado ao seu real funcionamento é muito precário; ainda mais na comunidade
brasileira.

Então partindo disso, resolvi juntar tudo o que eu absorvi durante as horas de
talks, posts e estudos que eu tive e escrever aqui; a fim de ajudar aqueles que
estão dando início aos estudos nessa área e até mesmo para abrir discussões
sobre as conclusões que eu cheguei; agregando assim, mais conhecimento para
todos nós.

Como vocês já devem ter percebido, não estou escrevendo este post para quem tem
o intuito de aprender React Native, mas sim para aqueles que desejam entender
como ele funciona; logo você verá pouquíssimo código aqui *(Não vá embora
haha).* Para aqueles que desejam realmente aprender React Native, recomendo
fortemente o curso do [Tyler McGinnis](https://medium.com/@tylermcginnis); ele
vêm fazendo um trabalho extraordinário na comunidade React e React Native.

[React Native - Tyler McGinnis](https://tylermcginnis.com/courses/react-native/)

### Então vamos começar…

O que o **React Native** faz? Basicamente, ao contrário de aplicações web, que
se utilizam da DOM do navegador para representar os elementos na UI, ele irá
realizar chamadas nativas — *Objective-C para dispositivos iOS e JAVA para
Android* — a fim de renderizar estes elementos.

Entretanto, esta comunicação entre o reino **JavaScript** (React Native) e o
reino **Nativo** (Objective-C/Java) não é feita em um passe de mágica. Existe
"algo" ali que não é responsável apenas por realizar toda essa comunicação, mas
sim também pelo diferencial do React Native para outros frameworks e bibliotecas
do mercado… "Algo" que vêm sendo chamado de **Bridge**.

Muitos desenvolvedores acabam considerando o processo de **Bridge** como
*black-box *e ignoram o que está acontecendo ali. Eles não estão errados em um
primeiro momento, uma vez que este processo não será parte do seu dia a dia de
desenvolvedor mas **poderá ser extremamente útil entender como ele funciona** em
determinadas situações.

### Mas quando irei precisar da Bridge?

Basicamente você sempre estará usufruindo dos benefícios da **Bridge**, uma vez
que ela é a chave para o funcionamento de uma aplicação React Native. Mas você
precisará de entender o seu funcionamento em algumas situações como:

* Integração com third-party SDKs;
* Quando alta performance é crucial para a sua aplicação;
* Quando você está trabalhando com aplicativos já existentes (Android/iOS);
* Você precisa de acessar APIs da plataforma;

### Aplicações React Native

Ok, neste ponto você já deve entender que uma aplicação React Native não
funciona apenas com o JavaScript que nós estávamos acostumados, certo? Existe
algo a mais ali naquela *black-box*.

Para continuar, devemos entender como uma aplicação React Native é estruturada;
de ambos os lados: o lado nativo e o lado do JavaScript que estávamos
acostumados.

É importante fixar que projetos em **React Native** rodam diretamente no
dispositivo do usuário; **nativamente**. E para isso, contamos com a seguinte
arquitetura:

#### Dispositivos Android:

* **JSCore virtual machine:** Destinado ao nosso código JavaScript;
* **Android Runtime:** Para o código Java;

#### Dispositivos iOS:

* **JSCore virtual machine:** Destinado ao nosso código JavaScript;
* **Native Runtime:** Para códigos Objective-C/Swift;

Existem também três importantes threads sendo executadas em uma aplicação
**React Native**, fora as que normalmente já são executadas por aplicações
nativas em background.

A primeira delas é a **main thread**, que também é utilizada por qualquer
aplicação nativa. Ela é responsável por tratar as requisições relacionadas a
renderização de elementos na tela e também pelos gestos reproduzidos pelo
usuário.

A segunda é exclusiva ao React Native, responsável por executar o código
**JavaScript**. O JavaScript é o responsável por toda lógica de negócio da
aplicação. Além de definir a estrutura e as funcionalidades da nossa UI.

E por último, a **Shadow Queue **que é a responsável pelos cálculos referentes
ao layout.

![](https://i.imgur.com/ydShx3h.jpg)

Voltando à analogia que utilizamos anteriormente, podemos considerar que a main
thread e a thread de JavaScript seriam, respectivamente, o **reino Nativo** e o
**reino JavaScript**.

### Comunicação entre os reinos

Um ponto importante aqui é que essas duas threads — esses dois reinos — **nunca
se comunicam diretamente e nunca bloqueiam uma a outra**. Toda essa comunicação
— requisições, medidas de layout, interações com o usuário, etc. — é realizada
através da **Bridge**; que como o próprio nome diz, é a ponte entre o reino
Nativo e o reino JavaScript. Toda a comunicação entre estes dois reinos deve
passar por essa ponte.

> Todo início de interação é iniciado pelo lado nativo, já que eventos de toque na
> tela são tratados no parte nativa da aplicação.

![](https://i.imgur.com/GPwxR0Z.jpg)

Para exemplificar um pouco melhor e entender a responsabilidade de cada uma das
threads, imagine a seguinte situação:

**1. [Nativo]:** Opa JavaScript, tudo bom? O usuário acabou de clicar aqui no
botão **MOSTRAR FILMES**. O que eu preciso fazer?

**2. [JavaScript]:** Fala Nativo! Não tem nenhum filme na lista do usuário. Você
deve renderizar o seguinte texto para ele *"Nenhum filme encontrado!"*.

**3. [Nativo]:** Feito, está renderizado! Estou te enviando a instância do
elemento que eu acabei de criar.

Toda essa comunicação é feita de forma **serializada** e **agrupada**.

Mas como as coisas não são tão simples assim no mundo de desenvolvimento, esta
comunicação seria algo que seguisse o seguinte padrão.

<script src="https://gist.github.com/rafaelcamaram/dedc1c6bf60f1a3a0ed7623549d67491.js"></script>

Nós podemos ver que esta linha está se referindo a uma comunicação **JS->N**, ou
seja, a nossa thread de **JavaScript** está solicitando que a thread **Nativa**
realize alguma ação. *(Esta comunicação poderia também ser N->JS)*

Estamos passando um método de **UIManager** chamado **createView**, a qual
recebe um array como parâmetro que possui as propriedades de uma View que deve
ser criada.

> **UIManager** é o responsável por aplicar comandos do React na plataforma nativa

Esta view que deverá ser criada é elemento chamado **RCTRawText**, que possui
como propriedade text: *“Nenhum filme encontrado!”.*

Mas espere um momento, o que seria este **RCTRawText**?

Para aqueles que não sabem, o React e React Native nos possibilita utilizar
**JSX** para representar os nossos elementos, de uma forma similar ao XML; não é
obrigatório mas é altamente recomendado por ser de simples leitura,
interpretação e por possibilitar a utilização de todo o poder do JavaScript.

[Github do JSX](https://facebook.github.io/jsx/)

Mas infelizmente o nosso reino nativo não sabe como interpretar esse **JSX**.
Logo para resolver isto, o React Native transforma o nosso elemento JSX para uma
linguagem de marcação que pode ser entendida pelo nosso processamento nativo.
Esta linguagem de marcação irá determinar como o elemento de nossa UI deverá
ser.

<script src="https://gist.github.com/rafaelcamaram/4284f2a002c501690ff18ad4791b13c8.js"></script>

Como nós podemos perceber a partir do *gist* a cima, o nosso JSX foi segmentado
em diversos novos elementos que serão utilizados para renderizar o nosso
elemento.

Vale notar que estes elementos da linguagem de marcação não serão renderizados
diretamente na nossa UI. Eles irão apenas auxiliar neste processo, de forma que
o seu elemento de texto *(de acordo com este exemplo) *seja renderizado
**nativamente**.

#### MessageQueue.js

Todas essas mensagens *JS->N* e *N->JS *são recebidas e tratadas pelo o que
chamamos de **MessageQueue,** que possui uma parte nativa e uma correspondente
JavaScript, com o objetivo de realizar o mapeamento entre estes dois mundos.

Quando nós estamos pensando em performance, nós temos que nos preocupar bastante
com o lado JavaScript da **MessageQueue**. Uma vez que nós temos que ter certeza
que a nossa thread JavaScript não está bloqueda e que o MessageQueue não está
congestionado; uma vez que o seu processamento é síncrono.

Caso você já tenha desenvolvido em React Native antes, você muito provavelmente
já se deparou com o sentimento de conseguir dar scroll na tela do seu aplicativo
mas não conseguir clicar em nenhum botão. Isso acontece porque a sua UI é feita
inteiramente de forma nativa, enquanto o JavaScript é o responsável por saber o
que deve ser feito quando um toque é realizado. Neste momento, muito
provavelmente a sua **MessageQueue** estava congestionada e os seus eventos de
toque na tela ainda estavam "esperando" para serem transmitidos.

Existem algumas boas práticas que devem ser seguidas caso você queira evitar
problemas com a MessageQueue, entre eles, os seguintes:

* Evite objetos *"nested"*. Procure sempre deixar os seus objetos o mais planos
possível;
* Evite passar arrays pela bridge;
* Escreva a sua lógica de negócio em apenas do lado JavaScript;

A **MessageQueue** possui um recurso chamado spy (espião) que nós podemos
habilitar que nos permite possuir os logs de todas as mensagens passadas do
contexto JavaScript para o Nativo. Caso você tenha o interesse de ativar o
mesmo, basta você utilizar o método *spy *passando como parâmetro o valor
booleano *true.*

<script src="https://gist.github.com/rafaelcamaram/5f3c94abe80500aed0717716e481b825.js"></script>

Existe uma segunda alternativa para se visualizar os logs passados pela **Bridge
**que se chama **rn-snoopy**. Ele também utiliza o método *spy *da MessageQueue.

Na verdade, o rn-snoopy utiliza **RxJS** e trata os dados da MessageQueue como
stream; o que nos permite filtrar os dados e exibir aquilo que realmente é
pertinente para a nossa situação.

[jondot/rn-snoopy](https://github.com/jondot/rn-snoopy)

### Revisando: Aplicação RN e Comunicação

Então, revisando um pouco sobre o que foi falado *(escrito):*

* Em uma aplicação **React Native** temos dois reinos: Nativo e JavaScript;
* Estes reinos se comunicam apenas através de uma **Bridge**;
* A **Bridge** possui as seguintes características: assíncrona, serializada e
agrupada;
* Apesar da comunicação com a Bridge ser assíncrona, a **MessageQueue** é
síncrona. Logo, ela interpreta as mensagens na ordem de chegada;
* **Uma aplicação React Native é realmente nativa**, uma vez que seus componentes
são renderizados nativamente;
* Podemos visualizar os logs da Bridge utilizando **.spy()** ou o **rn-snoopy**;

### Native Modules e UI Components

Neste ponto você já deve ter uma boa noção do real funcionamento de uma
aplicação React Native e de como acontece a comunicação entre o lado nativo e o
lado JavaScript dessa aplicação.

No entanto, início deste texto, eu disse que você provavelmente iria precisar de
conhecer o funcionamento da Bridge nas seguintes situações:

* Integração com third-party SDKs;
* Quando alta performance é crucial para a sua aplicação;
* Quando você está trabalhando com aplicativos já existentes (Android/iOS);
* Você precisa de acessar APIs da plataforma;

E durante o texto eu não expliquei como você poderia reaproveitar algum método
ou componente que você já possui em sua aplicação Android/iOS. Isto é feito
através de **Native Modules** e **UI Components**, respectivamente.

Entretanto, nós iremos deixar esses dois tópicos para um post futuro. Caso você
tenha interesse, [me siga no Twitter e fique sabendo assim que eu publicar](https://twitter.com/rafaelcamaram). :)

### Últimas Considerações

Espero que vocês tenham aproveitado o conteúdo deste post assim como eu
aproveitei ao escrever :)

O meu objetivo aqui foi tentar passar um pouco do o que eu aprendi nestes
últimos meses de trabalho. Fico à disposição caso alguém tenha alguma dúvida ou
sugestão em relação ao conteúdo passado aqui.

Segue alguns links, caso vocês queiram entrar em contato comigo:

- [https://www.linkedin.com/in/rafaelcamaram](https://www.linkedin.com/in/rafaelcamaram)
- [https://github.com/rafaelcamaram](https://github.com/rafaelcamaram)

Muito obrigado por ter chegado até aqui! :)
