---
title: 'Anotações palestra: O futuro do JavaScript'
author: Diego Eis
type: post
date: 2014-05-20
excerpt: Essa são as minhas anotações da palestra do Jaydson Gomes sobre as principais mudanças da próxima versão do Javascript.
url: /anotacoes-da-palestra-jaydson-gomes-16elw/
dsq_thread_id: 2700228622
categories:
  - Eventos e Workshops

---
Anotações da palestra do Jaydson Gomes no evento 16 Encontro Locaweb de 2014 chamada **O Futuro do Javascript**.

## História

  * Brendan Eich (CTO Mozilla) inventou o Javascript. Diz ele que foi em 10 dias.
  * O javascript foi criado em 1995 e pode ser conhecido por vários nomes: Mocha, LiveScript, Javascript e ECMAScript.
  * O Javascritp está baseado no ECMAScript, seguindo a especificação ECMA-262
  * Em 1999 apareceu a versão ECMA-3 (ES3). Ele incluiu algumas efeatures como expressões regulares, try/catch e outras.
  * Em 2008 a ES4 a versão foi abandonada. Por isso pulamos ela.
  * Mas em 2009 houve várias melhores na linguagem, aí surgiu a versão ES5
  * Tabela de compatibilidade da versão ES5. @kangax http://kangax.github.io/es5-compat-table/
  * CoffeScript é interessante porque ajuda na evolução da linguagem e da comunidade.
  * A versão ES6 do Javascript sai em Dezembro deste ano, com um bando de features bacanas. Há uma certa discussão sobre algumas novas features, como o Douglas Crockford não concordam com algumas features.

## Arrows functions

  * É introduzido um novo operador que é um atalho para a criação de funções: **=>**
  * Lexical this binding
  * Not newable
  * Can&#8217;t change this
  * Always anonymous

## Classes

  * Houve muita discussão por causa da inserção de **classes** no Javascript.
  * Para quem programa com Orientação a Objetos do modo clássico, já está acostumado a utilizar classes e vai conseguir trabalhar sem muitos problemas.
  * Isso não muda nada na linguagem. Vira uma opção a mais de uso.

## Templates Strings

  * Multiline strings
  * Basic string formatting
  * HTML escaping
  * Localization of strings:

<pre class="lang-javascript">var name = "Bob", time = "today";
console.log(`Hello ${name}, how are you ${time}?`)</pre>

## Parametros

  * Rest
  * Spread
  * Default

## Block Scope

  * Let
  * Const

## Modulos

  * Módulos tem sido discutido a muito tempo no Javascript

## Promise

  * Uma promise representa um valor não necessariamente conhecido no seu tempo de criação.
  * Promises permitem associas handlers de sucesso ou erro de uma ação assíncrona

  * Compilador onde você escreve em ES5 e ele compila para ES6. O próprio Google usa isso nos seus projetos. (<http://github.com/google/traceur-compiler>)