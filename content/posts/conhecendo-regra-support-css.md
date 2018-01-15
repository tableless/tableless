---
title: Conhecendo o @supports do CSS
authors: Diego Eis
type: post
publishdate: 2018-01-29
date: 2018-01-22
excerpt: Entendendo como funciona a regra de condição @supports
image: https://i.imgur.com/5Xk9hFS.jpg
categories:
  - CSS
  - support
  - Na prática
tags:
  - css
  - front-end
---

E se você pudesse testar se um browser tem suporte a uma determinda propriedade do CSS? E se o browser não tivesse o suporte, você dissesse para ele usar uma outra propriedade como fallback? É esse teste que o `@supports` faz.

A regra `@supports` do CSS te deixa testar se o browser tem suporte ou não a features específicas do CSS. Isso se chama `feature query`. A regra é simples: Coloque a regra no topo do seu código ou dentro de qualquer grupo condicional, assim como você usa o `@media`, você usará o `@supports`. 

Essa é checagem mais básica:

```
@supports (propriedade: valor) {
	/* se o browser suportar a propriedade especificada acima, esse bloco será executado */
}
```

### Palavra-chave NO
Se você quiser testar se o browser **não** tem suporte a uma propriedade, basta usar a palavra `not` antes da propriedade:

```
@supports not (propriedade: valor) {
	/* se o browser NÃO suportar a propriedade especificada acima, esse bloco será executado */
}
```

### Palavra-chave OU
Agora vamos supor que você queira testar se o browser tem suporte a uma propriedade *ou* outra:

```
@supports (propriedade: valor) or
          (outra-propriedade: valor) {
	/* se o browser suportar a uma ou outra propriedade especificada acima, esse bloco será executado */
}
```

### Palavra-chave E
Testando se o browser suporte várias propriedades, você usa a palavra chave *and*:

```
@supports (propriedade: valor) and
          (outra-propriedade: valor) {
	/* se o browser suportar todas propriedade especificadas, esse bloco será executado */
}
```

Você pode usar as palavras-chave **or** e **and** ao mesmo tempo se achar necessário:

```
@supports ( (propriedade: valor) or (outra-propriedade: valor) ) and (outra-propriedade: valor) {
	/* Executa esse bloco */
}
```

Perceba que colocamos as propriedades de checagem `or` dentro de um parenteses extra.

Dá para fazer coisas do tipo:

```
@supports (display: flexbox) and (not (display: inline-grid))
```

## Exemplo
Um uso prático seria testar a propriedade `display: flex` nos browsers:

```
div.parent {
  width: 100%;
}

div.child {
  float: left;
}

@supports (display: flex) and (display: flex) {
  div.parent {
    display: flex;
  }
  div.child {
    flex: 1;
    float: none;
  }
}
```

## Suporte dos browsers
O suporte dos browsers é bastante abrangente:

[![](https://i.imgur.com/WBXrPNp.png)](https://caniuse.com/#search=%40support)

Lembrando que os browsers já são tolerantes a erros, ou seja, se ele não entender alguma propriedade ou valor do CSS, ele simplesmente ignora a linha e continua seu trabalho. Logo, o `@supports` é bastante útil como forma de fallback, direcionando o browser a usar uma propriedade em vez de outra.

## Usando no JavaScript
O JS entende o `@supports` pelo método `CSS.supports`, que retorna um valor Booleano, indicando se o browser suporta ou não determinada propriedade: valor do CSS.

```
var supportsFloatLeft = CSS.supports("float", "left");
supportsFloatLeft;
# -> true/false
```

![](https://i.imgur.com/bOc8Gza.gif)


Link da [documentação oficial](https://drafts.csswg.org/css-conditional-3/#at-supports).