---
title: Design em código com Machine Learning no AirBnb
authors: Benjamin Wilkins
type: post
publishdate: 2018-01-17
date: 2018-01-17
image: https://i.imgur.com/SgsZU4J.png
excerpt: Como o Airbnb gera código a partir das suas interfaces de baixa fidelidade
categories:
  - Design
  - UX
  - Tecnologia e Tendências
  - Opinião
  - Traduções
  - Na Prática
  - Mercado
  - Artigos
  - Código
tags:
  - front-end
  - automatizacao
  - mercado
  - sketch
---

_O tempo necessário para testar uma ideia deveria ser zero._ Essa foi a primeira sentença que eu escrevi considerando a visão de equipe de ferramentas de design. Nós acreditamos que, nos próximos anos, a tecnologia irá permitir times desenharem novos produtos de uma forma expressiva e intuitiva, **enquanto elimina simultaneamente obstáculos do processo de desenvolvimento de produtos**.

Da forma que estamos hoje, cada passo no fluxo de design e todo artefato produzido se torna inútil no final do processo. O trabalho é interrompido a partir do momento que uma disciplina finaliza uma porção do projeto e passa a responsabilidade para outra disciplina: Progresso do projeto vindo das reuniões com stakeholders para o time de design para o time de engenharia; requisições se tornam explorações, explorações se tornam mockups e protótipos, e isto é entregue para os desenvolvedores para se tornarem produtos de fato. Mas cada um desses passos incomodos são, na sua essência, uma tradução do significado compartilhado de um objetivo comum, com especialistas altamente capacitados como tradutores de cada domínio.

Então, como nós agilizamos o processo para criar uma visão mais verdadeira? Nosso time começou a explorar métodos para tornar o tempo de teste para zero. 
Conforme nós aprendermos e construirmos, nós iremos compartilhar o que estamos trabalhando por aqui.

## Do esboço ao produto

Esboçar algo é visto como uma fase inicial natural. Como designers de interface, esboçar é um método intuitivo para expressar um conceito. Nós esperamos ver como isso irá ficar, pulando alguns passos do ciclo de desenvolvimento de produto e traduzindo instantaneamente nossos esboços em produtos finais. 

![](https://i.imgur.com/U97JBFF.png)

O sistema de design do Airbnb é bem documentado e cada componente no sistema foi nomeado. Nós desenvolvemos uma teoria de trabalho onde algoritmos de machine learning podem classificar um grupo complexo de centenas de simbolos feitos a mão - mesmo escritos em caractéres chineses - com um alto grau de precisão, então eles devem estar habilitados a classificar os 150 componentes no nosso sistema e ensinar uma máquina a reconhecê-los.

Nós construímos um protótipo inicial usando algo em torno de uma dúzia de componentes desenhados à mão como dados de treinamento, algoritmos de machine learning open source e um pouco de código para renderizar no browser componentes do nosso sistema de design. Nós ficamos bem surpresos com o resultado:

<video width="715" height="430" controls preload="metadata" src="https://airbnb.design/wp-content/uploads/2017/10/WireframeClassifiersmall.mp4?_=1">
  <source type="video/mp4" src="https://airbnb.design/wp-content/uploads/2017/10/WireframeClassifiersmall.mp4?_=1"><a href="https://airbnb.design/wp-content/uploads/2017/10/WireframeClassifiersmall.mp4">https://airbnb.design/wp-content/uploads/2017/10/WireframeClassifiersmall.mp4</a>
</video>

Este sistema tem um enorme potencial. Nós experimentamos usar essa mesma tecnologia para fazer protótipos a partir de desenhos feitos em um quadro branco, para traduzir mocks de alta fidelidedade em especificações de componentes para nossos engenheiros e traduzir código de produção em arquivos de design para nossos designers.

## Exploração em andamento

Conforme o movimento de sistemas de design fica mais popular e as interfaces ficam mais padronizadas, nós acreditamos que a inteligência artificial será a próxima geração de ferramentas para ajudar tanto design quanto desenvolvimento. Nós estamos ansiosos por compartilhar nosso trabalho a comunidade de designers e desenvolvedores que estão explorando esse novo campo pra ver onde isso nos levará. Fique antenado para futuros updates, já que vamos continuar experimentando e construindo.

Para saber mais sobre nosso pensando e visão sobre esse assunto, veja um vídeo de uma talk que eu dei sobre **pensamento simbolico e sistemas de design** (symbolic thinking and design systems).

<iframe width="560" height="315" src="https://www.youtube.com/embed/z5XxgxBz3Fo" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>

Muito obrigado para os outros membros do time do Design Techonology por ajudar a levar esse projeto pra frente: Jon Gold, Gavin Owens, David Chen e Lucas Smith

***

Este post foi traduzido com a gentil autorização do [Benjamin Wilkins](https://twitter.com/thatbenlifetho) (Design Technologist no Airbnb). Veja o [post original aqui](https://airbnb.design/sketching-interfaces/).