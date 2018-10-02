---
title: Vida longa aos testes de mutação
authors: Breno Panzolini
type: post
date: 2018-10-02
excerpt: Explicação sobre o por que test coverage não é uma métrica necessariamente boa e como podemos melhorar a qualidade dos nossos testes com testes de mutação.
categories:
  - NodeJS
  - JavaScript
tags:
  - NodeJS
  - JavaScript
image: https://stryker-mutator.io/images/strykerman.png
---

Hoje em dia, frente às vantagens competitivas do mercado ter um produto bom pode não ser o suficiente. É necessário e praticamente mandatório para todas as empresas que querem se destacar a habilidade de **evoluir o produto sem quebrar o que já existe**.

Quantas vezes já não deixamos de usar determinado produto ou serviço pelo simples fato da página não carregar corretamente, ou de erros bizarros acontecerem? Como resultado disso vejo cada vez mais as empresas preocupadas com a qualidade dos seus produtos.

Uma das técnicas mais comuns (entenda que comum não necessariamente significa fácil de ser adotada) é a execução de testes automatizados juntos com os *pipelines* de integração contínua e de deploy, a famosa dupla CI/CD (continuous integration/continuous deployment).

Mas aí é que vem a enxurrada de perguntas: Quanto de teste é necessário? Será que meus testes realmente são consistentes? Será que realmente estou testando direito? Quanto de cobertura preciso ter para dormir em paz?

Nesse artigo quero tentar desmitificar alguns pontos sobre *test coverage* que muitas pessoas têm (inclusive eu até um tempo atrás) e apresentar um conceito que pode ajudar muitas pessoas e empresas a cada vez mais garantirem uma qualidade maior: **mutation tests**.
