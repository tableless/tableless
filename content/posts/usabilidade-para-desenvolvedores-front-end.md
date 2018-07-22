---
title: Usabilidade para desenvolvedores front-end
authors: Talita Pagani
type: post
date: 2010-10-13
excerpt: A usabilidade possui diversos critérios a serem trabalhados durante todo o processo de desenvolvimento de uma interface, mas no dia-a-dia podemos melhorar a experiência do usuário através de pequenos detalhes.
url: /usabilidade-para-desenvolvedores-front-end/
categories:
  - Design
  - CSS
  - HTML
tags:
  - usabilidade
  - front-end
---
A usabilidade é uma qualidade das interfaces que caracteriza a facilidade de uso. Várias diretrizes sobre usabilidade de interfaces web foram desenvolvidas ao longo dos últimos 15 anos e o interesse em proporcionar interfaces de fácil utilização tem crescido entre designers e desenvolvedores.
  
Entre as várias diretrizes de usabilidade, os princípios convergem para a seguinte tríade:

  * **Fácil de usar:** o uso da interface deve ser intuitivo, com recursos de fácil reconhecimento e elementos que não dificultem a navegação, leitura, interpretação, clique, etc.
  * **Fácil de aprender:** uso de termos, ícones, padrões de interface e recursos de ajuda que possibilitem novos usuários reconhecer e facilmente aprender como utilizar a interface. Consistência é fundamental neste quesito.
  * **Fazer com que o usuário não cometa erros:** neste quesito entram entram dicas, ajuda, validação, boas mensagens de erro e outros recursos que possam prevenir a ocorrência de erros e ajudar o usuário na correção dos mesmos.

Mas, na prática, como podemos implementar estes princípios? Neste artigo apresento algumas dicas simples de usabilidade que podemos praticar efetivamente durante o rotina de desenvolvimento do HTML e do CSS.

### Facilitando a leitura com line-height

Um espaçamento adequado entre linhas permite que as pessoas possam ler um texto com maior facilidade e mais rapidamente. O espaçamento não pode ser muito reduzido, pois pode deixar o texto &#8220;amontoado&#8221;, nem muito extenso, caso contrário as pessoas terão dificuldade de encontrar a próxima linha.
  
Particularmente recomendo utilizar espaçamento de 1.5 relativo ao tamanho da fonte, ou seja, se você utilizar fonte de 12px, o espaçamento entre as linhas será de 18px. No CSS, controlamos o espaçamento entre linhas com o `line-height`.

### Utilize margins e paddings para distinguir itens

Espaços em branco entre os elementos da página podem ser usado a favor da usabilidade e também da arquitetura de informação do seu site. Creio que muitos já devem ter passado pela situação de alguém falar o seguinte a respeito de um site que você fez: &#8220;Ah, mas esse conteúdo X não tem a ver com o Y? É porque estava tudo junto então achei que tinha a ver&#8221;.
  
Os espaços entre itens permite identificar quais elementos estão relacionados e quais são distintos. Portanto, utilize `margin` e/ou `padding` mais generosas para afastar elementos que sejam distintos e aproxime os elementos que estejam relacionados, evitando erros de interpretação e mesmo de utilização de alguns recursos presentes na página. Isto serve principalmente para:

  * Estabelecer relação entre títulos e texto
  * Identificar rótulo de formulário e o campo a qual ele se refere
  * Imagens e o respectivo conteúdo textual
  * Páginas que tenham múltiplos formulários ou outros recursos com botões de ação que possam fazer com que o usuário clique em um determinado botão pensando ser relativo a outro recurso

### O logo deve ser clicável

Por uma convenção que foi sendo consolidada ao longo do anos, os usuários tendem a clicar no logotipo para retornar à página inicial e é frustrante quando isso não ocorre, pois já é uma ação que o usuário espera ao clicar no logo. Independente do logo ser uma imagem ou um background dentro de uma outra tag, deve-se colocar um link para a página inicial do site.

### Textos que não são links não devem ser sublinhados

Atualmente, nem todo link precisa estar sublinhado para transmitir a ideia de link, mas todo texto sublinhado ainda transmite a ideia de link. É intuitivo o usuário clicar em uma palavra sublinhada esperando acessar uma página (imagine então se, além de sublinhado, o texto estiver em azul, como já vi em alguns lugares). Portanto, é aconselhável que, para dar ênfase em palavras nos textos, sejam utilizadas as tags `strong`, `em` que já têm essa função.

### Atributos &#8220;alt&#8221; e &#8220;title&#8221; para imagens

O atributo `alt` para a tag `img` tem a função de fornececer um texto alternativo caso a imagem não seja carregada ou caso um browser leitor de tela esteja analisando o conteúdo da página. Por isso, é importante que este texto tenha uma boa descrição sobre o conteúdo da imagem. Mas em algumas imagens é interessante que ela não somente tenha um texto alternativo, mas que também exiba uma dica descritiva da imagem ao passar o mouse sobre ela. Isto é muito útil, por exemplo, ao utilizar ícones que indiquem ações, status ou representem link para algum conteúdo sem o uso de um texto descritivo junto à imagem. Para isso, podemos utilizar o atributo `title` do HTML.

### Associando label à campos de formulário

A tag `label` serve para associar um rótulo a um campo de formulário. Mas muitos desenvolvedores esquecem de realizar essa associação através do atributo `for`, que deve remeter ao `id` do campo de formulário.
  
A principal vantagem dessa associação é permitir que o usuário selecione o campo do formulário ao clicar no `label`, o que facilita muito especialmente no caso de campos do tipo `checkbox` ou `radio`, pois aumenta a região clicável, ajuda diminuir o tempo e a chance de erros para selecionar estes campos.

### Destaque o campo ativo do formulário com :focus

Quando um usuário estiver preenchendo um formulário, ele deve perceber claramente em qual campo está inserindo os dados, pois somente mostrar o cursor dentro do campo pode não ser suficiente.
  
Para isso, pode-se utilizar a pseudo-classe `:focus` no CSS para o seletor de `input`, que possibilita aplicar um estilo ao elemento quando ele recebe foco para receber dados do teclado, como uma borda mais espessa ou de outra cor e um background diferenciado, como no exemplo abaixo:

<pre lang="css">/* Campos no estado normal possuem um background neutro e uma borda clara */
input.text, select, textarea
{ background: #FFF; border: 1px solid #999; }

/* Campos no estado :focus possuem um background diferenciado e uma borda de maior destaque */
input.text:focus, select:focus, textarea:focus
{ background: #FFC; border: 2px solid #D8A561; }</pre>

A usabilidade possui muitos outros critérios a serem trabalhados durante todo o processo de desenvolvimento de uma interface para a web, mas no dia-a-dia podemos melhorar a experiência do usuário através de pequenos detalhes.