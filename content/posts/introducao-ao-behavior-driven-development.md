---
title: Introdução ao Behavior Driven Development
author: Jefersson Nathan
type: post
date: 2014-02-21
excerpt: Hoje em dia, se quisermos escrever um bom software. Nossos programadores devem ser especialistas na regra de domínio de nossa aplicação. Não mas...
url: /introducao-ao-behavior-driven-development/
dsq_thread_id: 2275298239
categories:
  - PHP
  - Técnicas e Práticas
tags:
  - bdd
  - php
  - tdd
  - testes
  - testes automatizados
  - testes unitários

---
O **BDD** _(Behavior Driven Development ou Desenvolvimento guiado por comportamento)_, é uma resposta ao **TDD**, criado em 2003, por _Dan North_, e tem se expandido bastante nos últimos anos. Seu foco é obter um código testado a partir de um conjunto de cenários que descrevem como a aplicação ou unidade de código deverá se comportar em determinada situação.

### As práticas de **BDD** incluem:

  * Envolver as partes interessadas no processo através de _Outside-in Development_
  * Usar linguagem ubíqua para descrever o comportamento de uma aplicação
  * Automatizar os exemplos para provê um feedback rápido e testes de regressão
  * Usar **_SHOULD_** na hora de descrever o comportamento de software para ajudar esclarecer responsabilidades e permitir que funcionalidades do software sejam questionadas
  * Usar dublês de teste _(mocks, stubs, fakes, dummies, spies)_ para auxiliar na colaboração entre módulos e códigos que ainda não foram escritos

## E&#8230;

O grande lance do BDD, é que nos trabalhamos com comportamentos de uma maneira que
  
qualquer pessoa possa entender ou escrever novos testes. Baseado no que espera que
  
a aplicação executa o aferir uma ação específica.
  
_Qual a vantagem disso?_ O especialista do domínio pode escrever testes.
  
O gerente de projetos pode escrever testes. o PO pode escrever testes baseados
  
no que ele espera da aplicação. O padeiro da esquina pode escrever testes
  
também. Qualquer um pode descrever o que espera da aplicação sem a necessidade
  
de ter habilidades de um programador.

## Cenários

Cada cenário descreve uma ação que será aferida e testada. Eles devem conter
  
passos lógicos e simple de como obter um resultado específico a partir de uma sequência
  
de ações.

Exemplo:

**Cenário 1:** _Quantidade de items no estoque_

  * Dado que há 5 items no estoque
  * E um cliente comprou 2 items do estoque
  * Então quando contar os items restantes no estoque
  * Terei 3 items

Como podemos perceber, desenvolvedores podem se concentrar exclusivamente nas razões pelas quais o código deve ser criado, e não em detalhes técnicos, além de minimizar traduções entre a linguagem técnica na qual o código é escrito e outras linguagens de domínio.