---
title: Sobre desenvolvimento multi-device
author: Diego Eis
type: post
date: 2014-06-30
excerpt: Como classificar melhor os dispositivos para um bom desenvolvimento web.
url: /sobre-desenvolvimento-multi-device/
dsq_thread_id: 2798205509
categories:
  - Adaptive Web Design (AWD)
  - CSS
  - Mobile
  - Responsive Web Design (RWD)
tags:
  - adaptive web design
  - mobile
  - responsive

---
Hoje existem uma série de dispositivos misturados em pelo menos três categorias que conhecemos: smartphones, tablets e desktops. Mas onde começa um e termina outro? Um smartphone de seis ou sete polegadas é um tablet? Se você acha que não existem smartphones deste tamanho, pesquise sobre o Fonepad da Asus para ter um exemplo. Dividir os aparelhos pelo tamanho da tela ou por features já não é mais tão seguro como antes. Então como podemos desenhar uma linha para delimitar onde inicia e onde termina um smartphone e começa um tablet? Ou um tablet e um notebook ou um desktop?

Todos os meses a indústria cria novas definições de aparelhos. Veja o caso dos Phablets, que são os smartphones gigantes, como o Sony Z Ultra e o Nokia Lumia 1520. Há também os híbridos, que o Windows 8 tem trazido à tona e que estão se popularizando cada vez mais. É por isso que é muito difícil fazer uma classificação por features ou por tamanhos. Tudo é muito parecido.

Sem dúvida é importante que você entenda o dispositivo que o seu cliente tem usado, mas mais importante do que isso é entender o contexto em que o cliente usa esses dispositivos. Não é muito difícil imaginar como é esse comportamento. Pense em como **você** usa seus gadgets. Pense exatamente nas situações e lugares onde você usa seu smartphone, o seu tablet e quando você decide usar seu PC. Perceba que há um padrão de comportamento bastante comum entre todos os usuários destes dispositivos. Há uma questão ergonômica envolvida, onde decidimos qual dos dispositivos usar.

## Classificação ergonômica

A primeira vez que vi essa maneira de diferenciar os dispositivos foi em uma palestra do Luke Wroblewski. E achei que faz bastante sentido essa divisão, por enquanto, por que a ergonomia dos aparelhos é algo que não muda muito. A classificação é a seguinte:

Os aparelhos que você consegue usar com apenas uma mão, em pé, em lugares apertados, no ônibus, metro e etc, ficam no grupo **palm**.

Aparelhos que geralmente são usados em lugares mais confortáveis, principalmente em casa, em um sofá ou na cama, que normalmente precisam das duas mãos para serem manuseados, ficam no grupo **lap**.

Agora os aparelhos grandes, que normalmente ficam &#8220;presos&#8221; a uma mesa, em um ambiente controlado, sem muita perturbação e que geralmente é onde o usuário tem um nível de foco bem alto, são colocados no grupo **desk**.

Essa classificação é muito mais amigável e sabemos que não vai mudar daqui um ou dois anos por causa de um novo aparelho maluco que possa surgir. Isso também permite planejar o produto para uma continuidade mais previsível de tamanhos de telas.

Mas há outros pontos que precisam ser levados em consideração. Embora eles sejam classificados por este fator ergonômico, como é a interação com cada dispositivo?

## Classificação via interação

As interações mais comuns existentes hoje são touch e teclado/mouse. Há interações que fogem desse padrão, que ainda são bem incomuns como as feitas com o Kinect ou até o Leap Motion.

Mas ainda sim não é seguro traçar uma linha dividindo os dispositivos com essas interações. Há o caso dos notebooks híbridos e aqueles tablets que podemos conectar um teclado e um mouse.

Há uma mistura nessa classificação e isso te coloca em um cenário onde o usuário vai usar sua interface com um mouse ou o próprio dedo em qualquer aparelho. Não há bala de prata aqui, mas ainda assim você **não precisa fazer duas interfaces** para cada tipo de interação. Isso é caro, dá trabalho e sua equipe vai pirar antes do fim do projeto.

## Desenhando e desenvolvendo uma vez

Produzir algo para todos os dispositivos e prevendo todas as circunstancias pode ser algo bem fácil de fazer. Mas isso é uma maneira nova e bem diferente de fazer tudo o que você já sabe. Você vai continuar desenhando uma interface que envolve todas as possibilidades. Aqui vão 5 premissas básicas:

  1. Trabalhe pensando em Mobile First
  2. Tenha em mente a continuidade dos tamanhos de telas
  3. Pense em um futuro onde todos os dispositivos serão de alta resolução
  4. Otimize para touch
  5. Suporte cursores e teclados

Essas premissas precisam ser seguidas no processo de desenvolvimento todo, mas as áreas de ux/design e front-end tem um papel mais crítico no caminho. Há muita discussão antes de digitar uma linha de código. Nas experiências que tenho passado, depois dessas grandes discussões, a taxa de retrabalho e refatoração de código é bem pequena.