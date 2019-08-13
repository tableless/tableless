---
title: Vida longa aos testes de mutação
authors: Breno Panzolini
type: post
date: 2018-10-02
excerpt: Explicação sobre o por que test coverage não é uma métrica necessariamente boa e como podemos melhorar a qualidade dos nossos testes com testes de mutação.
categories:
  - JavaScript
  - NodeJS
tags:
  - NodeJS
  - testes
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

# Testes de mutação

Uma das soluções que temos frente à busca implacável pela cobertura de testes são os **testes de mutação**.

Para resumir, testes de mutação são **testes que testam os nossos testes**, como assim? São testes que incluem mudanças no nosso código criando os **mutantes** e rodando os nossos testes repetidamente sobre essa "nova versão" de código. Se os testes passarem isso significa que eles não foram capazes de identificar e matar os mutantes mostrando que o nosso teste não é tão "forte" assim.

Vamos ao exemplo para tentar deixar as coisas mais claras, vamos supor que dada uma idade precisamos verificar se ela é maior que 18 anos, para isso teríamos uma função parecida com essa:

```js
function verificaIdade (idade) {
  if (idade >= 18) {
    return true
  } else {
    return false
  }
}

test('teste verificaIdade') {
  expect(verificaIdade(10)).toBeFalsy()
  expect(verificaIdade(20)).toBeTruthy()
}
```

No cenário acima os testes iriam passar bem como a cobertura estaria em **100%**, porém como já mencionei a cobertura não é o melhor indicador para garantir a qualidade dos nossos testes.

Ao executar alguns **testes de mutação** no código acima pequenas alterações seriam feitas, como por exemplo mudar o `>=` por `>` e com isso esperar que meu teste falhe. Como você já deve ter percebido eu não estou testando a idade 18 corretamente, significando que meus testes podem ser bons mas eles ainda não são suficientes para garantir todas as possibilidades do meu código.

Para melhorar esse cenário mecionado poderíamos adicionar um novo teste:

```js
expect(verificaIdade(18)).toBeTruthy()
```

Esse tipo de análise que acabamos de realizar é muito melhor para responder à perguntas como: "Quão bom meus testes são?".

## Testando os nossos testes

Uma ferramente bem legal para realizarmos testes de mutação é o [Stryker Mutator](https://stryker-mutator.io/), que é bem fácil de ser executado via *CLI* e que suporta a maioria dos frameworks de testes (mocha, jasmine, jest, etc.) e cuja execução mostra a resiliência dos nossos testes como um todo.

Novamente como o foco desse artigo não é explicar sobre uma ferramenta específica sugiro que para quem se interessou pelo assunto que dê uma olhada no [quickstart](https://stryker-mutator.io/stryker/quickstart) que é bem simples e legal de ser feito. 

# Conclusão

Esse post foi para mostrar alternativas para a qualidade dos nossos testes do que apenas o *test coverage* e com isso melhorar os nossos projetos como um todo.

Só queria deixar claro para não entenderem errado o objetivo do post e nem desprezarem as métricas de cobertura de testes, esse valor ainda é muito importante. O objetivo é mostrar que esse valor por si só não garante a qualidade do nosso projeto e que existem ferramentas muito legais para nos ajudar a cada vez mais entregar código melhor.

Então vamos matar os mutantes?