---
title: Estilizar e formatar placeholder de inputs
author: Diego Eis
type: post
date: 2014-02-26
excerpt: Como formatar o texto do atributo placeholder.
url: /estilizar-e-formatar-placeholder-de-inputs/
dsq_thread_id: 2321835699
categories:
  - CSS
  - HTML5
tags:
  - CSS
  - CSS3
  - html
  - html5
  - placeholder

---
O atributo **placeholder** foi uma das maravilhas herdadas do HTML5. Eu me lembro de todas as gambiarras em Javascript e CSS que fazíamos para simular o que o atributo placeholder faz tão facilmente.

O atributo placeholder é uma pequena dica, uma pequena frase, uma palavra, que tem o intuito de ajudar o usuário a entender como ele deve preencher aquele formulário. Entenda que e o placeholder NÃO deve ser usado como alternativa para a LABEL. Ou seja, aquela prática de colocar um **display: none** nas labels e deixar apenas o placeholder visível não é legal. Também não é aconselhável ter uma descrição gigante. Para isso, use o atributo TITLE.

Como esse atributo simplesmente insere um texto contextual no campo de formulário, muitos devs acham que não há maneira de formatá-lo, trocando cor, tamanho, font e etc&#8230; Mas há! E é bem simples. Infelizmente você ainda precisa usar prefixos para funcionar, mas logo mais, quem sabe, não será mais necessário.

Para formatar o atributo placeholder dos campos de formulários e textareas, basta manipular a pseudo-class ::placeholder. Não me perguntem por que é uma pseudo classe não e um pseudo elemento. Mas isso é só um detalhe.



**Dica:** Eu poderia ter agrupado os seletores pra facilitar a leitura, o problema é que se um dos browsers não reconhece um dos seletores, ele acabam invalidando o grupo inteiro, aí nada funcionaria. Nesse caso a solução é colocar separado mesmo.

Veja a [documentação oficial][1] direto do WHATWG.

 [1]: http://developers.whatwg.org/common-input-element-attributes.html#the-placeholder-attribute