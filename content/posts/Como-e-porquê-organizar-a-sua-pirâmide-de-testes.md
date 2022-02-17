---
title: Como e porquê organizar a sua pirâmide de testes
authors: Lucas Lacava
type: post
image: https://i.imgur.com/zovWaVc.png
date: 2022-02-17
excerpt: Como organizo minha pirâmide de testes para meus projetos front-end no BEES Brasil.
categories:
  - Front-end
  - Testes
---

# Como e porquê organizar a sua pirâmide de testes

Mais do que funcionalidades novas, o que queremos são funcionalidades confiáveis. E a melhor maneira para alcançar isso é através de testes. Repare que o plural aqui é proposital, caro leitor e cara leitora: **não confie em apenas um tipo de teste.** 

Dito isso, meu incentivo ‘é para que você organize uma **pirâmide de testes** para o seu projeto. 

# O que é uma pirâmide de testes?

De maneira objetiva, a pirâmide de testes é um modo de representar quais testes cobrirão o seu projeto, sendo a sua base composta por testes mais rápidos e baratos (para serem feitos e executados) e no topo ficam os testes que são mais demorados e caros. 

![Fonte: [https://kentcdodds.com/blog/write-tests](https://kentcdodds.com/blog/write-tests)](https://i.imgur.com/LdPQ534.png)

Fonte: [https://kentcdodds.com/blog/write-tests](https://kentcdodds.com/blog/write-tests)

# Mas eu tenho 100% de cobertura em um tipo de teste, já não é suficiente?

Muitas vezes somos levados à acreditar que números representam a total e absoluta verdade, [mas podem ser facilmente manipulados](https://www.intrinseca.com.br/livro/624/), além de criar uma falsa sensação de segurança no projeto. Também há casos em que para se chegar nos 100% de cobertura há um trabalho imenso, desgaste do time, testes desnecessários e provavelmente mal escritos, com o único objetivo de alcançar um número.

> Distribuir testes é mapear necessidades, responsabilidades e prioridades. Dividir para conquistar
> 

## Testes de unidade

Comece pelo básico, testando as menores partes do seu código, especialmente funções. De acordo com os parâmetros, o que ela deve retornar? Qual operação deve realizar? O componente deveria conter 3 botões? A função deve ser disparada no click do botão e executar uma ação? Tudo isso (e além) pode ser testado nesta etapa. 
Sugestão de ferramentas:  [Jest](https://jestjs.io/pt-BR/), [Enzyme](https://enzymejs.github.io/enzyme/), [Testing library](https://testing-library.com/docs/react-testing-library/intro/) 

## Testes de componente

Nesta etapa é possivel testar a aplicação da maneira como quem a utiliza vai vê-la, testando inclusive comportamentos do seu componente e fluxos da aplicação. Ao clicar em um botão, ele deve abrir um modal com um formulário? Esse formulário deve ser preenchido, com campos numéricos, texto, checkboxes obrigatórios? Ao clicar no botão, a pessoa deve ser redirecionada para outra url? Precisa validar o comportamento de um componente de input? Esses são apenas alguns cenários em que é possível realizar testes de componente. Essa etapa possui um atrativo, ja que é muito visual, pois, ao escrever testes de componente a pessoa que está desenvolvendo vê a aplicação e consegue ver o motivo de erros também, tornando a solução mais fácil de ser encontrada. 

Sugestão de ferramentas: [Cypress](https://www.cypress.io/), [Puppeteer](https://pptr.dev/), [Playwright](https://playwright.dev/)

## Testes visuais

Aqui é possível testar se o estado atual da sua aplicação está igual ao padrão determinado (através de *screenshots*). Vamos supor que alguém mudou por acidente a cor de um botão, o tamanho, ou a font-family de um texto. Através de testes visuais esses erros seriam identificados e corrigidos antes de serem mergeados com a branch principal. 

Sugestão de ferramentas: [Percy](https://percy.io/) 

## Testes de contrato

Este tipo de teste visa garantir a integridade na comunicação entre front-end e back-end, garantindo que a resposta do back-end possua exatamente a mesma estrutura e tipo de dados que o front-end espera, evitando surpresas e quebras de aplicação indesejadas.

Sugestão de ferramentas: [Pact io](https://docs.pact.io/)

## Testes end-to-end

Os testes end-to-end (e2e) são os mais demorados (tanto para implementação, quanto para execução) e provavelmente ficam quase no topo da pirâmide de testes, atrás dos testes manuais, porém também são um dos tipos de testes que mais entregam valor e confiabilidade na aplicação. Estes testes são realizados em ambientes integrados e testam toda a aplicação com dados reais (sem mocks) em ambientes semelhantes ao de produção.

[Selenium](https://www.selenium.dev/), [Robot](https://robotframework.org/), [Cypress](https://www.cypress.io/)

## Leia mais:

[https://martinfowler.com/bliki/TestPyramid.html](https://martinfowler.com/bliki/TestPyramid.html)

[https://kentcdodds.com/blog/write-tests](https://kentcdodds.com/blog/write-tests)

[https://willianjusten.com.br/entendendo-testes-de-software#qualidade](https://willianjusten.com.br/entendendo-testes-de-software#qualidade)

[https://medium.com/creditas-tech/a-pirâmide-de-testes-a0faec465cc2](https://medium.com/creditas-tech/a-pir%C3%A2mide-de-testes-a0faec465cc2)

Espero de verdade que o artigo tenha sido útil pra você que chegou até aqui 🙂

Eu sou Front-End Engineer no BEES, e se quiser bater um papo sobre o conteúdo, sobre desenvolvimento front-end ou sobre como é trabalhar no BEES Brasil, a vida e tudo mais: fico à disposição [aqui no LinkedIn.](https://www.linkedin.com/in/lucaslacava/)
