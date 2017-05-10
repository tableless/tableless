---
title: 'Coisas úteis que não funcionam no IE #1 – seletor inteligente'
author: Diego Eis
type: post
date: 2006-09-15
url: /coisas-uteis-que-nao-funcionam-no-ie-1-seletor-inteligente/
tweetbackscheck:
  - 1356171217
shorturls:
  - 'a:3:{s:9:"permalink";s:82:"http://tableless.com.br/coisas-uteis-que-nao-funcionam-no-ie-1-seletor-inteligente";s:7:"tinyurl";s:26:"http://tinyurl.com/3u94cro";s:4:"isgd";s:19:"http://is.gd/XEdnaE";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 503036005
categories:
  - Artigos
  - Browsers
  - Geral
  - Tecnologia e Tendências
tags:
  - Técnicas e Práticas

---
Sempre digo uma frase nos meus cursos, que qualquer dia desses vai virar lenda. Enquanto estou explicando alguma técnica, seletor ou alguma outra propriedade extremamente útil para os alunos, no final da explicação, vem a frase: Só que isso não funciona no IE.

Os alunos sempre estão com aquelas caras de maravilhados e vendo um milhão de problemas resolvidos quando mostro alguma propriedade ou técnica de CSS miraculosa. Mas sempre essas caras são substituídas por expressões de, como eu poderia dizer, desgosto, ao mencionar a frase acima.

O IE 6 não é um browser ruim. Ele só é um browser velho, antigo.

O intuito deste post &#8211; e de vários outros, tomara &#8211; é tentar mostrar algumas propriedades e técnicas que por algum motivo, não funcionam no IE. Não vou dar soluções&#8230; mesmo porque muitas delas não terão solução pelo simples fato de que simplesmente o IE não tem suporte a determinada situação. Mas que isso sirva de aprendizado a todos, e que possa ser útil para resolver problemas em browsers que tem um pouco mais de qualidade no suporte aos padrões.

### Seletor Inteligente

Hoje, usamos uma parte muito restrita da teoria dos seletores de CSS2. Você fica fadado a usar apenas seletor agrupado (p, div, h1 &#8211; por exemplo) e seletor encadeado. E com essas duas formas, você consegue se virar.
  
Acontece que há algumas situações que você não consegue obter total controle sem ter que definir um tipo de identificação aos objetos.
  
Por exemplo:

`Sempre digo uma frase nos meus cursos, que qualquer dia desses vai virar lenda. Enquanto estou explicando alguma técnica, seletor ou alguma outra propriedade extremamente útil para os alunos, no final da explicação, vem a frase: Só que isso não funciona no IE.

Os alunos sempre estão com aquelas caras de maravilhados e vendo um milhão de problemas resolvidos quando mostro alguma propriedade ou técnica de CSS miraculosa. Mas sempre essas caras são substituídas por expressões de, como eu poderia dizer, desgosto, ao mencionar a frase acima.

O IE 6 não é um browser ruim. Ele só é um browser velho, antigo.

O intuito deste post &#8211; e de vários outros, tomara &#8211; é tentar mostrar algumas propriedades e técnicas que por algum motivo, não funcionam no IE. Não vou dar soluções&#8230; mesmo porque muitas delas não terão solução pelo simples fato de que simplesmente o IE não tem suporte a determinada situação. Mas que isso sirva de aprendizado a todos, e que possa ser útil para resolver problemas em browsers que tem um pouco mais de qualidade no suporte aos padrões.

### Seletor Inteligente

Hoje, usamos uma parte muito restrita da teoria dos seletores de CSS2. Você fica fadado a usar apenas seletor agrupado (p, div, h1 &#8211; por exemplo) e seletor encadeado. E com essas duas formas, você consegue se virar.
  
Acontece que há algumas situações que você não consegue obter total controle sem ter que definir um tipo de identificação aos objetos.
  
Por exemplo:

` 

Note o código acima.
  
Suponha que você gostaria aumentar apenas os formulários de **texto**, colocar uma largura de 300px, por exemplo. Como você faria?
  
Simplesmente colocaria uma classe ou id em cada um dos formulários de texto e então aumentaria. Não é?

``Sempre digo uma frase nos meus cursos, que qualquer dia desses vai virar lenda. Enquanto estou explicando alguma técnica, seletor ou alguma outra propriedade extremamente útil para os alunos, no final da explicação, vem a frase: Só que isso não funciona no IE.

Os alunos sempre estão com aquelas caras de maravilhados e vendo um milhão de problemas resolvidos quando mostro alguma propriedade ou técnica de CSS miraculosa. Mas sempre essas caras são substituídas por expressões de, como eu poderia dizer, desgosto, ao mencionar a frase acima.

O IE 6 não é um browser ruim. Ele só é um browser velho, antigo.

O intuito deste post &#8211; e de vários outros, tomara &#8211; é tentar mostrar algumas propriedades e técnicas que por algum motivo, não funcionam no IE. Não vou dar soluções&#8230; mesmo porque muitas delas não terão solução pelo simples fato de que simplesmente o IE não tem suporte a determinada situação. Mas que isso sirva de aprendizado a todos, e que possa ser útil para resolver problemas em browsers que tem um pouco mais de qualidade no suporte aos padrões.

### Seletor Inteligente

Hoje, usamos uma parte muito restrita da teoria dos seletores de CSS2. Você fica fadado a usar apenas seletor agrupado (p, div, h1 &#8211; por exemplo) e seletor encadeado. E com essas duas formas, você consegue se virar.
  
Acontece que há algumas situações que você não consegue obter total controle sem ter que definir um tipo de identificação aos objetos.
  
Por exemplo:

`Sempre digo uma frase nos meus cursos, que qualquer dia desses vai virar lenda. Enquanto estou explicando alguma técnica, seletor ou alguma outra propriedade extremamente útil para os alunos, no final da explicação, vem a frase: Só que isso não funciona no IE.

Os alunos sempre estão com aquelas caras de maravilhados e vendo um milhão de problemas resolvidos quando mostro alguma propriedade ou técnica de CSS miraculosa. Mas sempre essas caras são substituídas por expressões de, como eu poderia dizer, desgosto, ao mencionar a frase acima.

O IE 6 não é um browser ruim. Ele só é um browser velho, antigo.

O intuito deste post &#8211; e de vários outros, tomara &#8211; é tentar mostrar algumas propriedades e técnicas que por algum motivo, não funcionam no IE. Não vou dar soluções&#8230; mesmo porque muitas delas não terão solução pelo simples fato de que simplesmente o IE não tem suporte a determinada situação. Mas que isso sirva de aprendizado a todos, e que possa ser útil para resolver problemas em browsers que tem um pouco mais de qualidade no suporte aos padrões.

### Seletor Inteligente

Hoje, usamos uma parte muito restrita da teoria dos seletores de CSS2. Você fica fadado a usar apenas seletor agrupado (p, div, h1 &#8211; por exemplo) e seletor encadeado. E com essas duas formas, você consegue se virar.
  
Acontece que há algumas situações que você não consegue obter total controle sem ter que definir um tipo de identificação aos objetos.
  
Por exemplo:

` 

Note o código acima.
  
Suponha que você gostaria aumentar apenas os formulários de **texto**, colocar uma largura de 300px, por exemplo. Como você faria?
  
Simplesmente colocaria uma classe ou id em cada um dos formulários de texto e então aumentaria. Não é?

`` 

Há uma maneira &#8211; que você já sabe que não funciona no IE &#8211; de fazer isso sem a necessidade de sujar tanto o código com ID e CLASS.
  
Note o código css:

```Sempre digo uma frase nos meus cursos, que qualquer dia desses vai virar lenda. Enquanto estou explicando alguma técnica, seletor ou alguma outra propriedade extremamente útil para os alunos, no final da explicação, vem a frase: Só que isso não funciona no IE.

Os alunos sempre estão com aquelas caras de maravilhados e vendo um milhão de problemas resolvidos quando mostro alguma propriedade ou técnica de CSS miraculosa. Mas sempre essas caras são substituídas por expressões de, como eu poderia dizer, desgosto, ao mencionar a frase acima.

O IE 6 não é um browser ruim. Ele só é um browser velho, antigo.

O intuito deste post &#8211; e de vários outros, tomara &#8211; é tentar mostrar algumas propriedades e técnicas que por algum motivo, não funcionam no IE. Não vou dar soluções&#8230; mesmo porque muitas delas não terão solução pelo simples fato de que simplesmente o IE não tem suporte a determinada situação. Mas que isso sirva de aprendizado a todos, e que possa ser útil para resolver problemas em browsers que tem um pouco mais de qualidade no suporte aos padrões.

### Seletor Inteligente

Hoje, usamos uma parte muito restrita da teoria dos seletores de CSS2. Você fica fadado a usar apenas seletor agrupado (p, div, h1 &#8211; por exemplo) e seletor encadeado. E com essas duas formas, você consegue se virar.
  
Acontece que há algumas situações que você não consegue obter total controle sem ter que definir um tipo de identificação aos objetos.
  
Por exemplo:

`Sempre digo uma frase nos meus cursos, que qualquer dia desses vai virar lenda. Enquanto estou explicando alguma técnica, seletor ou alguma outra propriedade extremamente útil para os alunos, no final da explicação, vem a frase: Só que isso não funciona no IE.

Os alunos sempre estão com aquelas caras de maravilhados e vendo um milhão de problemas resolvidos quando mostro alguma propriedade ou técnica de CSS miraculosa. Mas sempre essas caras são substituídas por expressões de, como eu poderia dizer, desgosto, ao mencionar a frase acima.

O IE 6 não é um browser ruim. Ele só é um browser velho, antigo.

O intuito deste post &#8211; e de vários outros, tomara &#8211; é tentar mostrar algumas propriedades e técnicas que por algum motivo, não funcionam no IE. Não vou dar soluções&#8230; mesmo porque muitas delas não terão solução pelo simples fato de que simplesmente o IE não tem suporte a determinada situação. Mas que isso sirva de aprendizado a todos, e que possa ser útil para resolver problemas em browsers que tem um pouco mais de qualidade no suporte aos padrões.

### Seletor Inteligente

Hoje, usamos uma parte muito restrita da teoria dos seletores de CSS2. Você fica fadado a usar apenas seletor agrupado (p, div, h1 &#8211; por exemplo) e seletor encadeado. E com essas duas formas, você consegue se virar.
  
Acontece que há algumas situações que você não consegue obter total controle sem ter que definir um tipo de identificação aos objetos.
  
Por exemplo:

` 

Note o código acima.
  
Suponha que você gostaria aumentar apenas os formulários de **texto**, colocar uma largura de 300px, por exemplo. Como você faria?
  
Simplesmente colocaria uma classe ou id em cada um dos formulários de texto e então aumentaria. Não é?

``Sempre digo uma frase nos meus cursos, que qualquer dia desses vai virar lenda. Enquanto estou explicando alguma técnica, seletor ou alguma outra propriedade extremamente útil para os alunos, no final da explicação, vem a frase: Só que isso não funciona no IE.

Os alunos sempre estão com aquelas caras de maravilhados e vendo um milhão de problemas resolvidos quando mostro alguma propriedade ou técnica de CSS miraculosa. Mas sempre essas caras são substituídas por expressões de, como eu poderia dizer, desgosto, ao mencionar a frase acima.

O IE 6 não é um browser ruim. Ele só é um browser velho, antigo.

O intuito deste post &#8211; e de vários outros, tomara &#8211; é tentar mostrar algumas propriedades e técnicas que por algum motivo, não funcionam no IE. Não vou dar soluções&#8230; mesmo porque muitas delas não terão solução pelo simples fato de que simplesmente o IE não tem suporte a determinada situação. Mas que isso sirva de aprendizado a todos, e que possa ser útil para resolver problemas em browsers que tem um pouco mais de qualidade no suporte aos padrões.

### Seletor Inteligente

Hoje, usamos uma parte muito restrita da teoria dos seletores de CSS2. Você fica fadado a usar apenas seletor agrupado (p, div, h1 &#8211; por exemplo) e seletor encadeado. E com essas duas formas, você consegue se virar.
  
Acontece que há algumas situações que você não consegue obter total controle sem ter que definir um tipo de identificação aos objetos.
  
Por exemplo:

`Sempre digo uma frase nos meus cursos, que qualquer dia desses vai virar lenda. Enquanto estou explicando alguma técnica, seletor ou alguma outra propriedade extremamente útil para os alunos, no final da explicação, vem a frase: Só que isso não funciona no IE.

Os alunos sempre estão com aquelas caras de maravilhados e vendo um milhão de problemas resolvidos quando mostro alguma propriedade ou técnica de CSS miraculosa. Mas sempre essas caras são substituídas por expressões de, como eu poderia dizer, desgosto, ao mencionar a frase acima.

O IE 6 não é um browser ruim. Ele só é um browser velho, antigo.

O intuito deste post &#8211; e de vários outros, tomara &#8211; é tentar mostrar algumas propriedades e técnicas que por algum motivo, não funcionam no IE. Não vou dar soluções&#8230; mesmo porque muitas delas não terão solução pelo simples fato de que simplesmente o IE não tem suporte a determinada situação. Mas que isso sirva de aprendizado a todos, e que possa ser útil para resolver problemas em browsers que tem um pouco mais de qualidade no suporte aos padrões.

### Seletor Inteligente

Hoje, usamos uma parte muito restrita da teoria dos seletores de CSS2. Você fica fadado a usar apenas seletor agrupado (p, div, h1 &#8211; por exemplo) e seletor encadeado. E com essas duas formas, você consegue se virar.
  
Acontece que há algumas situações que você não consegue obter total controle sem ter que definir um tipo de identificação aos objetos.
  
Por exemplo:

` 

Note o código acima.
  
Suponha que você gostaria aumentar apenas os formulários de **texto**, colocar uma largura de 300px, por exemplo. Como você faria?
  
Simplesmente colocaria uma classe ou id em cada um dos formulários de texto e então aumentaria. Não é?

`` 

Há uma maneira &#8211; que você já sabe que não funciona no IE &#8211; de fazer isso sem a necessidade de sujar tanto o código com ID e CLASS.
  
Note o código css:

``` 

E agora o CSS:

`input[type="text"] {width:300px;}`

Este seletor seleciona os objetos INPUT que tenham o atributo TYPE com o valor TEXT. Ou seja, ele irá ser herdado apenas para os campos de texto. Todos os outros tipos de campos não serão afetados. Assim você consegue selecionar apenas um grupo de elementos que tenham um certo atributo.
  
Este tipo de seletor não fica preso a apenas campos de formulário. Você pode usar para selecionar qualquer outro objeto do HTML. 

Se o IE entendesse este seletor&#8230;