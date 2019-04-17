---
title: 'Flutter: porque você deveria apostar nesta tecnologia'
authors: Fabiano Santana
type: post
date: 2019-04-17
image: https://cdn-images-1.medium.com/max/2560/1*1Ccy1Bt4uAC2vXqyZ6zPNQ.png
excerpt: 'Porque você deveria apostar nesta tecnologia.'
categories:
  - Javascript
  - ReactJS
tags:
  - Flutter
  - ReactJS
  - Dart
---

Primeiro começarei contando o motivo de ter escolhido aprender e especializar em desenvolvimento híbrido com Flutter invés de virar especialista React Native e o motivo é bem simples: **Fluidez**

*****

## React Native

Para quem já desenvolveu aplicativos nativos sabe a dificuldade de manter o código atualizado caso o aplicativo tiver obrigatoriedade de funcionar nas duas plataformas *Android* e *iOS*. Enxergando essa deficiência a equipe do *Facebook* criou o **React Native** e disponibilizou-o como framework open source no ano de 2015 para o público.

### O que é esse tal de React Native?

React Native é um framework de desenvolvimento híbrido utilizando Javascript como base para criar aplicativos nativos utilizando apenas um código fonte padrão. Diferente do **ionic** que também servia para criar aplicativos híbridos, o React Native não funciona sobre uma WebView, ele possui uma *engine* (bridge) que ao emular o aplicativo no aparelho essa bridge faz um mapeamento dos componentes criados usando javascript com os componentes nativos do SO, aumentando assim o desempenho do aplicativo.

### Problemas ao utilizar React Native

Embora React Native seja uma das melhores soluções para construir aplicativos híbridos, ele ainda não possui a mesma fluidez de um aplicativo construído utilizando apenas recursos nativo, e mesmo que ainda haja muitas empresas utilizando-o em seus aplicativos a sociedade não é mais a mesma do ano de lançamento (2015), as pessoas estão cada vez mais impacientes e qualquer gargalo durante o uso é motivo para desinstalar o aplicativo.

*****

![](https://cdn-images-1.medium.com/max/800/1*k_aQA6TG9rrqu8gz0drG9g.png)
<span class="figcaption_hack">Analisando os gráficos acima referentes a pesquisas realizadas durante o ano de 2018/2019 percebe-se a crescente busca por flutter</span>

### Flutter: uma nova solução

![](https://cdn-images-1.medium.com/max/600/1*42zsz13tv08yERlHsZCdOw.gif)
<span class="figcaption_hack">Demonstração aplicativo em [Flutter](https://flutter.dev/)</span>

Com a mesma proposta do React Native de criar aplicativos híbridos utilizando apenas uma base de código surgiu o Flutter, desenvolvido e atualizado pela equipe da Google.

## O que é Flutter?

Como dito anteriormente, o Flutter é um framework para desenvolvimento híbrido de aplicativos utilizando a linguagem [Dart](https://www.dartlang.org/) como base de criação dos aplicativos.

## Porque usar Flutter?

Diferente do React Native que possui um intermediário (bridge) entre a UI e o dispositivo, o Flutter fica na camada do UI e não chama os componentes nativos do SO, ele é **desenhado diretamente** em um canvas que aumenta a performance e fluidez a nível de um aplicativo desenvolvido exclusivamente nativo. Além do ganho com performance o Flutter é uma tecnologia recente de fácil aprendizado e já possui algumas features sendo desenvolvidas, dentre elas:

* Flutter para Web
* Flutter para Desktop

Ou seja, você irá construir um aplicativo que poderá ser reaproveitado para suas web applications e também desktop. Esse é um sonho para muitos desenvolvedores, ter apenas uma base de código para toda a camada de apresentação.

Além dos benefícios de performance nativa, o Flutter possui muita flexibilidade para a criação de UI personalizadas, animações e facilidade em acessar os recursos do aparelho (geolocalização, galeria, etc…).

## Como funciona o flutter?

Se você está habituado com o termo "componente" vai se identificar rápido. O Flutter possui os "widgets" que seria a mesma coisa de um componente. Um widget é uma árvore que pode conter um ou mais filhos(widgets), e esses filhos são renderizados conforme a construção desta árvore. Muito parecido com o DOM do html.

![](https://cdn-images-1.medium.com/max/800/1*j49HIY0az28VWMDrmUu9eg.png)

Abaixo um exemplo de widget na prática

<script src="https://gist.github.com/fabianosanttana/dade0549cbcbfaf1b5ce0351f9f5cb4d.js"></script>

Observe acima, temos **Container** que possui uma propriedade **child** que pode receber outro widget, no exemplo utilizei **Center** que por sua vez possui suas propriedades e também tem uma propriedade **child **que pode receber outro widget**.**

## Fuchsia: O novo OS do google

![](https://cdn-images-1.medium.com/max/800/1*2af3pcH8Ue-uTLkJoEElAw.jpeg)

Se você é um profissional que quer estar na frente, vai uma dica para você. O Google está lançando um novo sistema para mobile, ainda não se sabe se esse sistema substituirá Android, se o React Native dará suporte porém o que se sabe é que **Flutter** será usado para criar aplicativos para esse novo sistema.

## Conclusão

Mesmo sendo uma tecnologia recente e sem mercado, aprender Flutter é uma aposta que pode dar muito certo. Algumas grandes empresas (Alibaba, Groupon, Google, etc…) notaram isso e estão migrando para Flutter.

Quando comecei a aprender eu achei realmente muito divertido a construção de aplicativos usando Dart. Outra coisa, conhecimento nunca é demais, se você já desenvolve em React Native como eu, aprender mais uma tecnologia não irá te diminuir como profissional.

