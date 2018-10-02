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

# O test coverage

Resumindo cobertura de testes é uma métrica que mede o quanto do seu código está coberto por testes. Na maioria dos cenários a equipe define um valor de cobertura que será garantido pelos testes.

Atingir 100% de cobertura é praticamente impossível, vejo cenários entre 70-80% como bem viáveis para a maioria das aplicações, mas é exatamente nesse ponto que aparece outra enxurrada de perguntas: Será que uma cobertura maior é melhor para o meu código? Se eu adicionar mais testes (para aumentar a cobertura) isso realmente significa que meu código está melhor testado?

Pela minha experiência como desenvolvedor, muitas vezes me pegava escrevendo mais testes apenas para melhorar a cobertura, porém muitos desses testes acabavam não cobrindo a funcionalidade como um todo.

Aumentar a cobertura dos testes é relativamente simples, basta chamar a função com parâmetros diferentes, instanciar objetos, etc, que as linhas vermelhas que mostram o nosso código não coberto vão aos poucos desaparecendo.

Para quem é do mundo JavaScript, umas das bibliotecas mais famosas para cobertura de testes é a [Istanbul](https://istanbul.js.org/), não vou entrar em detalhes sobre implementação pois não é o foco do artigo, porém já adianto que ela é bem simples e se integra facilmente com praticamente todos os frameworks de testes (mocha, AVA, tap, etc.).
