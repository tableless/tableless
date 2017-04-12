---
title: Acessibilidade básica no formulário de contato
author: Orivelton Cesar
type: post
date: 2016-08-08
url: /acessibilidade-basica-no-formulario-de-contato/
categories:
  - Acessibilidade
  - HTML
  - HTML5
tags:
  - acessibilidade

---
Um dos itens indispensáveis em um site é o formulário de contato, já pensou deixar ele acessível para todos na web? Na atualidade a acessibilidade vem sendo levada a sério com o avanço das tecnologias web e as supostas padronizações dos navegadores, e a acessibilidade hoje na web é muito importante, e a chegada do HTML5 deixou marcação do HTML mais explicativa para usuários acessíveis.

## WCAG 2.0 o que é ?

Quando se fala em diretrizes de acessibilidade  a [WCAG][1] que está na versão 2.0 abrange um vasto conjunto de recomendações, o resumo já define bem o que é a WCAG 2.0;

&#8220;As Diretrizes de Acessibilidade para Conteúdo Web (WCAG) 2.0 abrangem um vasto conjunto de recomendações que têm como objetivo tornar o conteúdo Web mais acessível. O cumprimento destas diretrizes fará com que o conteúdo se torne acessível a um maior número de pessoas com incapacidades, incluindo cegueira e baixa visão, surdez e baixa audição, dificuldades de aprendizagem, limitações cognitivas, limitações de movimentos, incapacidade de fala, fotossensibilidade bem como as que tenham uma combinação destas limitações. Seguir estas diretrizes fará também com que o conteúdo Web se torne mais usável aos utilizadores em geral.&#8221;

## Proposta

Nesse post irei mostrar um formulário de contato básico, validado pelo W3C e nível &#8220;AAA&#8221; nas baterias de teste do [AccessMonitor][2] que são baseados nas diretrizes WCAG 2.0, se desejar saber mais sobre o AccessMonitor veja a documentação nesse [link][3].

## Elementos acessíveis

No HTML temos elementos importantes para fazer com que seu formulário de contato tenha o mínimo de acessibilidade possível, abaixo alguns deles;

**[label][4], ****[fieldset][5], ****[Um dos itens indispensáveis em um site é o formulário de contato, já pensou deixar ele acessível para todos na web? Na atualidade a acessibilidade vem sendo levada a sério com o avanço das tecnologias web e as supostas padronizações dos navegadores, e a acessibilidade hoje na web é muito importante, e a chegada do HTML5 deixou marcação do HTML mais explicativa para usuários acessíveis.

## WCAG 2.0 o que é ?

Quando se fala em diretrizes de acessibilidade  a [WCAG][1] que está na versão 2.0 abrange um vasto conjunto de recomendações, o resumo já define bem o que é a WCAG 2.0;

&#8220;As Diretrizes de Acessibilidade para Conteúdo Web (WCAG) 2.0 abrangem um vasto conjunto de recomendações que têm como objetivo tornar o conteúdo Web mais acessível. O cumprimento destas diretrizes fará com que o conteúdo se torne acessível a um maior número de pessoas com incapacidades, incluindo cegueira e baixa visão, surdez e baixa audição, dificuldades de aprendizagem, limitações cognitivas, limitações de movimentos, incapacidade de fala, fotossensibilidade bem como as que tenham uma combinação destas limitações. Seguir estas diretrizes fará também com que o conteúdo Web se torne mais usável aos utilizadores em geral.&#8221;

## Proposta

Nesse post irei mostrar um formulário de contato básico, validado pelo W3C e nível &#8220;AAA&#8221; nas baterias de teste do [AccessMonitor][2] que são baseados nas diretrizes WCAG 2.0, se desejar saber mais sobre o AccessMonitor veja a documentação nesse [link][3].

## Elementos acessíveis

No HTML temos elementos importantes para fazer com que seu formulário de contato tenha o mínimo de acessibilidade possível, abaixo alguns deles;

**[label][4], ****[fieldset][5], ****][6] e [optgroup][7].**

## Elemento label

Esse é o cara da combinação do conjunto de atributos &#8220;for&#8221; e &#8220;id&#8221;, relacionando de forma clara o seu rótulo, indicando ao usuário o elemento de entrada de dados a ser editado, deixar de fazer esse relacionamento entre  &#8220;for&#8221; e &#8220;id&#8221; certamente vai deixar o usuário confuso, e não é uma coisa difícil de fazer, veja o exemplo abaixo;

<pre>&lt;label for="nome"&gt;Nome&lt;/label&gt;
&lt;input type="text" id="nome"&gt;</pre>

Atualmente não precisa mais envolver a label no input, pois as tecnologias mais modernas já procuram por o rótulo na hora da edição, o conjunto de atributos &#8220;for&#8221; e &#8220;id&#8221; pode ser utilizado com todos elementos de formulário, exceto o elemento button.

## Elementos fieldset e legend

O elemento fieldset é responsável por agrupar itens no formulário que tenham características em comum e sempre dentro do elemento form.

O elemento legend é utilizado em conjunto com o fieldset e deve estar dentro do mesmo, fazendo dessa forma o melhor  entendimento do usuário e toda vezes que um elemento for anunciado será precedido o elemento legend.

<pre>&lt;form&gt;
  &lt;fieldset&gt;
    &lt;legend&gt;Formulário de contato&lt;/legend&gt;
  &lt;/fieldset&gt;
&lt;/form&gt;

</pre>

## Elemento optgroup

O elemento optgroup é utilizado juntamente com o select, o optgroup é a mesma ideia do fieldset e legend dando título e agrupando itens do elemento select quando tem necessidade.

Cada optgroup recebe um &#8220;label&#8221; que será o título do grupo, veja o exemplo:

<pre>&lt;form&gt;
 &lt;label for="lista"&gt;Lista&lt;/label&gt;
 &lt;select id="lista"&gt;
  &lt;optgroup label="Diretoria"&gt;
   &lt;option&gt;Maria&lt;/option&gt;
   &lt;option&gt;José&lt;/option&gt;
   &lt;option&gt;João&lt;/option&gt;
  &lt;/optgroup&gt;
  &lt;optgroup label="Comercial"&gt;
   &lt;option&gt;Pedro&lt;/option&gt;
   &lt;option&gt;Antonio&lt;/option&gt;
   &lt;option&gt;Manoel&lt;/option&gt;
  &lt;/optgroup&gt;
 &lt;/select&gt;
&lt;/form&gt;

</pre>

O elemento optgroup juntamente com o atributo label (Diretoria e Comercial) deixa os elementos mais acessíveis e organizados em um select.

## Formulário nível &#8220;AAA&#8221; pelo AccessMonitor e validado pelo W3C

Abaixo um formulário simples, com as recomendações minimas de acessibilidade.

<pre>&lt;!DOCTYPE html&gt;
&lt;html lang="pt-br"&gt;
 &lt;head&gt;
 &lt;title&gt;Formulário de contato&lt;/title&gt;
 &lt;meta charset="UTF-8"&gt;
 &lt;/head&gt;
 &lt;body&gt;
 &lt;div class="container"&gt;
 &lt;a href="#formulario"&gt;
 Entre em contato por meio de nosso formulário de contato.
 &lt;/a&gt;
 &lt;form method="post" action="form.php" id="formulario"&gt;
 &lt;h1&gt;Formulário de contato&lt;/h1&gt;
 &lt;h2&gt;Entre em contato que teremos o imenso prazer em responder sua mensagem.&lt;/h2&gt;

 &lt;label for="nome"&gt;Nome&lt;/label&gt;
 &lt;input type="text" id="nome"&gt;

 &lt;label for="email"&gt;E-mail&lt;/label&gt;
 &lt;input type="email" id="email"&gt;

 &lt;label class="label label-primary" for="telefone"&gt;Telefone&lt;/label&gt;
 &lt;input type="tel" id="telefone" class="form-control" maxlength="11"&gt;

 &lt;label for="departamento"&gt;Escolha um departamento&lt;/label&gt; 
 &lt;select id="departamento"&gt;
 &lt;option&gt;Selecione&lt;/option&gt;
 &lt;option&gt;Atendimento&lt;/option&gt;
 &lt;option&gt;Comercial&lt;/option&gt;
 &lt;option&gt;Elogios&lt;/option&gt;
 &lt;option&gt;Reclamações&lt;/option&gt;
 &lt;/select&gt;

 &lt;label for="mensagem"&gt;Mensagem&lt;/label&gt;
 &lt;textarea id="mensagem"&gt;&lt;/textarea&gt;
 &lt;input type="submit" value="Enviar"&gt;
 &lt;/form&gt;
 &lt;/div&gt;
 &lt;/body&gt;
&lt;/html&gt;

</pre>

A recomendação da WCAG 2.0 é que sempre tenha um link e que ele seja o primeiro, em  que ele envie para o conteúdo principal, por isso o link &#8220;Entre em contato por meio de nosso formulário de contato&#8221;.

## Últimas considerações

Trabalhar em projetos que envolve acessibilidade é muito mais complexo, sou prova viva disso, ter atenção em como você escreve seu código é primordial. Colocar em mente que escrever um bom código é sinônimo de alcançar o máximo de pessoas possíveis, e as tecnologias estão ai cada dia evoluindo mais, vai querer separar alguém de um conteúdo <span style="line-height: 1.5;">relevante só por falta de caprichar nos seus códigos? As recomendações de acessibilidade nos permite disponibilizar o acesso a esses conteúdos de forma mais confortável para o usuário. </span><span style="line-height: 1.5;">Um dos teste mais básicos de acessibilidade é você conseguir navegar pelo site usado o TAB, se você ficar travado em algo ou não consegui chegar no conteúdo que deseja isso é indício<b> </b>que </span><span style="line-height: 1.5;">precisa de melhorias. </span>

<span style="line-height: 1.5;">Em vários site de e-commerce não tem a possibilidade de efetuar um fluxo de compra com um leitor de tela, pois etapas</span><span style="line-height: 1.5;"> como </span><span style="line-height: 1.5;">validações de campos, plugins,  falta de hierarquia de cabeçalho deixa a desejar, tonando o conteúdo inacessível. Eu acredito em uma web para todos, sei que nas correrias de projetos a acessibilidade é deixada de lado, mais sempre que possível construa tudo pensando em todos. </span>

 [1]: https://www.w3.org/Translations/WCAG20-pt-PT/
 [2]: http://www.acessibilidade.gov.pt/
 [3]: http://www.acessibilidade.gov.pt/accessmonitor/nota_tecnica.html
 [4]: http://www.w3schools.com/tags/tag_label.asp
 [5]: http://www.w3schools.com/Tags/tag_fieldset.asp
 [6]: http://www.w3schools.com/tags/tag_legend.asp
 [7]: http://www.w3schools.com/tags/tag_optgroup.asp