---
title: Dicas de como fazer seu próprio framework CSS
author: Diego Eis
type: post
date: 2013-09-03
excerpt: 'Anotações da minha palestra sobre como fazer seu próprio framework CSS. '
url: /dicas-de-como-fazer-seu-proprio-framework-css/
dsq_thread_id: 1665248375
categories:
  - Código
  - CSS
  - CSS3
  - HTML
  - HTML5
  - JavaScript
  - Técnicas e Práticas
tags:
  - CSS
  - frameworks css

---
Algumas anotações da minha palestra na QCon 2013, sobre como fazer seu próprio framework CSS.



<p style="margin-bottom:5px">
  <strong> <a href="https://www.slideshare.net/diegoeis/frameworks-css2" title="Construindo seu framework CSS" target="_blank">Construindo seu framework CSS</a> </strong> from <strong><a href="http://www.slideshare.net/diegoeis" target="_blank">Diego Eis</a></strong>
</p>

### Por que usar Frameworks?

  * Aumentar a eficiência
  * Consistência e padrão de código
  * Compatibilidade mais confiável
  * Fácil manutenção
  * Facilita a repetições de tarefas

### Por que não usar Frameworks?

  * Curva de aprendizado
  * HTML engessado
  * CSS engessado
  * Sopa de classes
  * Tem que manter tudo atualizado o tempo todo
  * Versionamento problemático

### Separe seu CSS em partes

É bom para manutenção, escalabilidade do código e também evita misturar assuntos diferentes.

#### Base

CSS Reset, Tipografia, customizações globais e genéricas do seu layout. Aqui é onde você vai colocar as características comuns, que todo o framework usará.

#### Layout

Grids, responsive e outras decisões de estrutura. Aqui será a casca, a infraestrutura do seu framework. É onde você decide como vai se comportar mas mediaqueries de estrutura e comportamentos de grid.

#### Módulos

Aqui entra o grande trabalho do seu framwork. São os elementos criados em módulos: botões, alertas, tables, tabs, collapses, sliders, headers, listas e etc… 

Alguns desenvolvedores podem querer dividir alguns elementos como collapses, modais e etc em outra parte chamada ESTADOS. Que agrupam elementos que tem comportamentos como abrir e fechar, aparecer e desaparecer, coisas do tipo.

#### Themes

Aqui depende muito da sua necessidade. Pode ser que seu projeto precise ter vários temas de cores ou você quer visuais diferentes (flat e skeumo por exemplo). Aí é bom separar as particularidades visuais de cada cenário em lugares separados.

### Princípios teoricos

**Modular e adaptável**
  
Ou seja, você precisa combinar o quanto quiser todos os elementos o seu framework. Eles precisam ser plugáveis uns aos outros.

**Leve**
  
Escreva o mínimo possível. Não tente abraçar todos os browsers. Gracefull degradation e Progressive Enhancement devem estar no seu sangue.

**Rápido**
  
Mínimo de requisições. Isso quer dizer que você tem que usar o menor número de arquivos possível. Diminua o número de arquivos CSS, JS e Imagens.

**Simples**
  
Precisa ser fácil para fazer manutenção, legível para novos integrantes entenderem rapidamente.

**Tenha poucas dependências**
  
Dependa menos de terceiros. Existem plugins que são indispensáveis como JQuery. Seja criterioso com os plugins que você utilizar

**Regra da similaridade**
  
Se dois elementos são muito parecidos para incluir em uma página, provavelmente eles são muito parecidos para serem incluídos juntos em um site. Escolha um.

### Na prática

**Modularize componentes**
  
Componentes são como legos. Você pluga diversas peças para formar uma peça maior. 

**Evite especificar tags. Mantenha o foco nas classes**
  
É melhor fazer .btn do que a.btn
  
Botões podem ser um link, um input, uma tag button…
  
Deixe as classes livres para customizar qualquer elemento.

**Não trave as dimensões do seu site.**
  
O Grid controla a largura. O conteúdo controla a altura. Não trave alturas ou larguras a não ser que seja extremamente necessário. 

**Minimize seletores. Seja sucinto.**
  
Não faça seletores complexos como: .search fieldset label .btn
  
Seja breve e vá direto ao ponto: .header .search .btn

**Separe o conteúdo do container.**
  
O estilo do conteúdo não pode ser dependente do seu container. Eu posso estilizar qualquer conteúdo independente do container que o elemento está. Trate o container como um módulo e o conteúdo como outro.

**Separe a estrutura do layout**
  
Você pode ter a liberdade de estilizar cada bloco de estrutura do jeito que achar melhor. O container pode ser estruturado de várias formas, com diferentes layouts.

**CSS Incremental: customize objetos aplicando multiplas classes. Mas não abuse.**
  
Aqui você deve ir com cuidado. Um botão pode ter vários tamanhos, defina um tamanho padrão, mas crie outras classes que mudarão o tamanho do botão conforme a necessidade. Fica assim:

<pre class="lang-html">&lt;a href="#" class="btn btn-large"&gt;Bot&atilde;o&lt;/a&gt;
</pre>

Se quiser que esse botão flutue a direita, você pode inserir mais uma classe:

<pre class="lang-html">&lt;a href="#" class="btn btn-large float-right"&gt;Bot&atilde;o&lt;/a&gt;
</pre>

Mas tome cuidado para não misturar muita &#8220;formatação&#8221; no HTML.

**Use font para icones. É melhor ao lidar com diversos tamanhos e cores.**
  
Fonts tem mais facilidade para mudarmos o tamanho, cores e posição. 

**Você pode usar algum pre-processador. Mas cuidado.**
  
Pré-processadores podem te ajudar em diversas tarefas. Mas se não tomar cuidado o código pode ficar muito maior do que se fosse criado à mão.

### Considere usar um framework como base

Não reinvente a roda. Procure um framework que te agrade mais e parta daí.
  
Customize o layout deste framework para a sua necessidade e adicione novas funções às funções existentes.