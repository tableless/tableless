---
title: Dicas de front-end para designers
authors: Markus Domenegheti
type: post
image: https://i.imgur.com/X5edSIv.jpg
date: 2017-12-24
excerpt: Dicas de front-end para designers visando agilizar o desenvolvimento do site e manter maior fidelidade ao layout.
categories:
  - Design
  - Semântica
  - Na prática
  - CSS
---


É comum o front-end receber um layout e ter que fazer pequenas alterações direto na programação para resolver um problema. O excesso dessas pequenas alterações podem afetar o resultado final do projeto. Essas alterações geralmente podem ser evitadas, resultando no aumento da fidelidade do site com o layout e diminuindo o tempo de desenvolvimento.

> Baseado na minha experiência, vou dar algumas dicas para usar na criação de um layout.

Defina os tons das cores
------------------------

Evite tons de cores muito parecidos. Aconselho definir uma paleta de cores com suas variações, e usá-la em todas as páginas na criação. Inclusive para os tons de cinza, muito usados em layouts web. Disponibilize a paleta de cores usada, pode ajudar muito.

### Por quê?

É comum a utilização de pré-processadores no desenvolvimento dos sites, e neles são definidos apelidos para as cores comuns no layout, facilitando muitos processos no desenvolvimento.

![](https://i.imgur.com/wW4HzjK.jpg)

Reutilize os ícones
-------------------

Normalmente sites têm ícones padrões como setas e botões de fechar, que podem ser reaproveitados de outras formas. No caso das imagens serem SVG, é possível até mesmo mudar alguns atributos do elemento, como cor e borda. Pergunte ao front-end como ele trabalha.

### Por quê?

Pode influenciar no tempo de carregamento da página e impedir o reaproveitamento de código.

![](https://i.imgur.com/sJWUUkR.jpg)

Informe-se sobre o que será administrável
-----------------------------------------

Algumas áreas do site podem ser administráveis pelo usuário via painel. Com isso, pode-se tomar vários cuidados na criação do layout. Nas áreas em que o texto for administrável pelo usuário, utilize fontes que tenham as variações necessárias (como negrito e itálico).

### Por quê?

Geralmente o painel de controle do site oferece essas opções de customização, por isso devem ser previstas.

![](https://i.imgur.com/pd4sC4h.jpg)

Utilize transparência apenas se houver necessidade
--------------------------------------------------

Transparências devem ser utilizadas apenas quando houver necessidade. Não utilize transparência para diminuir o tom das cores por exemplo, defina a cor exata que irá usar.

### Por quê?

Ao alterar a opacidade, o hexadecimal da cor não muda, podendo confundir na hora do desenvolvimento.

![](https://i.imgur.com/4pOsXGT.jpg)

Procure referências dentro do layout
------------------------------------

Caso for dar continuidade na criação de outro designer ou precisar alterar o layout, procure referências dentro do próprio layout. Muitas vezes você pode reaproveitar elementos que já foram criados ou criar novos usando as mesmas características.

### Por quê?

Influencia no reaproveitamento de código e melhora a usabilidade do site.

![](https://i.imgur.com/HYSKs3e.jpg)

Por hoje é só isso, com certeza vou fazer uma parte dois para esse assunto, espero que tenham gostado.
Eu iria adorar se um designer criasse um artigo reverso com sugestões para os front-ends, alguém se candidata?
