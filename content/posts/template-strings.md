---
title: Template Strings
authors: Bruno Ruiz
type: post
publishdate: 2018-05-24
date: 2018-05-24
excerpt: Criar strings é algo muito fácil em JavaScript. Mas manipular strings não é algo trivial.
image: https://i.imgur.com/Ojf6mzf.png
categories:
  - Javascript
  - Na Prática
tags:
  - javascript
  - Na Prática
---

Criar strings é algo muito fácil em JavaScript. Mas manipular strings não é algo
trivial. Requer um pouco de habilidade, parecida com a habilidade requirida aos
malabaristas.

![](https://i.imgur.com/Ojf6mzf.png)
<span class="figcaption_hack">Photo by [juan pablo
rodriguez](https://unsplash.com/@juanparodriguez?utm_source=medium&utm_medium=referral)
on [Unsplash](https://unsplash.com/?utm_source=medium&utm_medium=referral)</span>

Existem alguns exemplos que mostram como a manipulação de strings não é algo
corriqueiro. Destes exemplos, dois são mais recorrentes:

* Interpolação de strings.
* Múltiplas linhas.

Antes de falarmos sobre estes dois exemplos vamos alinhas os seguintes
conceitos:

* Strings: qualquer sequência de caracteres.
* Caractere: menor unidade de um texto.

## Interpolação de Strings

Conceitualmente **interpolar **é diferente de **concatenar**; apesar de usarmos
estes termos de forma indistinta no dia a dia.

Se possuo duas strings e quero criar uma terceira, podemos concatená-las. Mas se
queremos inserir um trecho de texto dentro de outro, então chamamos isso de
interpolação.

No exemplo abaixo, queremos retornar uma string interpolada com algumas
características passadas no parâmetro de uma função.

O retorno esperado é:* “O aluno Bruno está na oitava série e tem 11 anos de
idade.”*.

    function aluno (aluno, serie, idade){
         return "O aluno "+ aluno +" está na "+ serie +" série."
    };

    aluno("Bruno"," oitava");

Esse código funciona, mas dá para ser melhor!

**Como?**

A resposta é : **Template Strings.**

Template Strings é uma das especificações do ECMAScript 2015 que ajuda a fazer
do código acima um pouco melhor. Veja abaixo a implementação do nosso caso de
estudo com Template Strings.

    function aluno (aluno, serie, idade){
         return `O aluno ${aluno} está na ${serie} série.`
    };

    aluno("Bruno"," oitava");

Se compararmos as duas soluções percebemos que:

* Com Templates Strings não precisamos ficar abrindo e fechando a instrução com
aspas e o sinal de mais (+). Basta adicionar acentos graves no início e no fim
da string.
* Também percebemos que a interpolação pode ser feita apenas adicionando os
parâmetros da função dentro chaves, sendo a de abertura precedida de um cifrão.
* Pessoalmente acredito que a legibilidade do código aumenta bastante.

Essa não é a única possibilidade de uso desta especificação.

## Múltiplas Strings

Uma necessidade muito comum é a de criamos uma string de tags html interpoladas
com algumas variáveis para serem inseridas no DOM.

No entanto, quando temos um volume de marcações que não cabem em uma linha,
precisamos usar um recurso para mantermos a legibilidade das marcações.

Isso pode ser feito da seguinte maneira:

    function resumo_de_compra(produto, valor){
        return "<table style='width:100%'>"+
                 "<tr>"+
                   "<th>Produto</th>"+
                   "<th>Valor da Compra</th>"+ 
                 "</tr>"+
                 "<tr>"+
                   "<td>"+produto+"</td>"+
                   "<td>"+valor+"</td>"+
                 "</tr>"+
               "</table>";
    }

É claro que podemos melhorar o código acima com com Template Strings.

Como?

Veja o que você acha da modificação abaixo:

    function resumo_de_compra(produto, valor){
        return `<table style='width:100%'>
                 <tr>
                   <th>Produto</th>
                   <th>Valor da Compra</th>
                 </tr>
                 <tr>
                   <td>${produto}</td>
                   <td>${valor}</td>
                 </tr>
               </table>`;
    }

Com essa modificação — adição de acentos graves no início e no fim da string —
nós mantemos o código em múltiplas linhas sem a necessidade do uso de aspas e
sinal de mais (+). E quando é necessário interpolar algum valor, isso é feito
sem problemas.

Prático, não é verdade?!

## Finalizando

Essas são algumas possibilidades desta especificação. Existem mais algumas
particularidades a respeito dela, se quiser bater um papo sobre isso deixe seu
comentário abaixo.

Se você já usou em algum outro caso e quer compartilhar, deixe comentário!
