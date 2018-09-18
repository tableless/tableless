---
title: Analisando a solução para um Sudoku
authors: Tailo Mateus Gonsalves
type: post
image: https://cdn-images-1.medium.com/max/1000/1*appBwh6_RtvocVxwqpplHA.jpeg
date: 2018-08-20
excerpt: Classes de algoritmos inteligentes - Gulosos e programação dinâmica
categories:
  - Back-end
  - Tecnologias e Tendências
tag:
  - Programação dinâmica
  - Algoritmo guloso
  - Sudoku
  - Recursão
---

Em algum momento da sua vida, já ouviu falar sobre o quebra-cabeça, mas se por
acaso não sabe o que é, tome cuidado nas suas pesquisas, existe um grande risco
em se tornar um viciado (assim como eu). Aqui, vamos analisar e discutir
maneiras que podemos resolve-lo, obviamente utilizaremos o auxilio da
tecnologia.

Nosso problema consiste em uma grid 9 x 9, o principal objetivo é preencher as
linhas, as colunas e os sub quadrados 3 x 3 com números não repetidos de 1 a 9
da nossa matriz.

<div style="text-align: center">
![](https://cdn-images-1.medium.com/max/800/1*lTLwAvQ0i1s1mdhmxjcjng.png)
</div>
<span class="figcaption_hack">Sudoku</span>

### Resolvendo o problema

Esse é um problema como qualquer outro, primeiramente devemos analisar o que ele
vai impactar e qual a melhor forma de resolve-lo. Minha primeira solução, você
poderia escrever um **algoritmo com backtracking**. Basicamente teríamos que
percorrer nossa matriz e dessa forma dizer se um determinado número é possível
em determinada posição.

### Backtracking

Um algoritmo de força bruta visita todas as células vazias, preenchendo os
números quando foram válidos. Caso o algoritmo encontre alguma inconformidade,
ele pode descartar todos os casos testados anteriormente.

A animação facilita nosso entendimento:
<div style="text-align: center">
![](https://cdn-images-1.medium.com/max/800/1*ISlzB1fMXIYeovi3OrmyYw.gif)
</div>
<span class="figcaption_hack">Sudoku sendo preenchido</span>

**As vantagens**

* Uma solução é garantida

* Esse algoritmo não é tão complexo, quanto os outros que fazem o mesmo

**A desvantagem**

* O tempo de resolução pode ser relativamente lento, estatisticamente esse
algoritmo pode requerer 15 000 à 90 000 ciclos, sendo cada ciclo uma mudança na
posição de um ponteiro, conforme move-se entre as células.


### Afinal, backtracking é IA?

O conceito de inteligência artificial é muito amplo, e pode ser definido de
várias formas. Mas podemos pensar em algumas características básicas, tais como,
**capacidade de raciocínio** (aplicar regras lógicas para chegar a uma
conclusão) e **aprendizagem** (aprender com os erros e acertos, para que no
futuro consiga executar de forma mais eficaz).

Os famosos algoritmos de procura que conhecemos hoje (aqui entra a técnica de
**backtracking**), no inicio, um programa inteligente tentaria por força bruta
encontrar uma solução através de todas as possibilidades possíveis. 


### Repensando a nossa solução

Podemos utilizar outra forma para resolver nosso problema, aliás, existem várias
outras, mas vamos focar em apenas outra. Começamos analisando onde temos menos
possibilidades para colocar um único número.
<div style="text-align: center">
![](https://cdn-images-1.medium.com/max/800/1*Vv7ulMFh_D8VrrZx_PyJjg.png)
</div>
<span class="figcaption_hack">Gerando novas matrizes</span>

No exemplo acima, escolhemos uma célula que possui duas possibilidades, dessa
forma temos uma nova matriz com os valores 8 e 9, da qual podemos aplicar a
**propagação de restrição** (pode ser usada para reduzir o espaço de pesquisa e
tornar o problema mais fácil para ser resolvido). Aqui temos o famoso caso de
**recursividade**.

### Programação recursiva

Indo direto ao ponto, um programa recursivo tenta resolver algo chamando a si
próprio. O grande detalhe é que na segunda chamada seu valor foi influenciado
pelo valor original, assim, resolvendo problema menores e no final lhe
entregando uma única solução. Não é algo tão simples em entender, talvez com um
exemplo vai facilitar.

Exemplo em Python:

```
def sumR (n):
    if n == 1:
        return 1
    else:
        return n + sumR(n-1)
```

Esta forma acima garante a solução de qualquer sudoku. 

### Algoritmos gulosos

Em cada iteração que esse algoritmo faz, ele escolhe qual a opção mais
“apetitosa” que vê pela frente. Ele toma decisões com base nas informações
disponíveis na própria iteração. O algoritmo guloso jamais volta atras, as suas
**escolhas são definitivas**. Apesar do pouco uso dessa solução, pode se dizer
que são muito **rápidos e eficientes**.

Alguns problemas que podem ser resolvidos com algoritmos gulosos:

* [Mochila
fracionária](https://www.ime.usp.br/~pf/analise_de_algoritmos/aulas/mochila-frac.html)
* [Escalonamento de
intervalos](https://www.ime.usp.br/~pf/analise_de_algoritmos/aulas/intervalos.html)
* [Árvore de
Huffman](https://www.ime.usp.br/~pf/analise_de_algoritmos/aulas/huffman.html)


### Programação dinâmica

Essa técnica consiste em dividir o problema geral em subproblemas mais simples e
ir resolvendo-os de forma iterativa, armazenando os resultados em uma tabela
para serem usados quando quiser. Sendo mais especifico, a ideia é **construir
por etapas uma resposta já obtidas por partes menores**. 

Alguns algoritmos que usam programação dinâmica:

* [Subsequência crescente
máxima](https://www.ime.usp.br/~pf/analise_de_algoritmos/aulas/sscm.html#dynprog2)
* [Subsequência comum
máxima](https://www.ime.usp.br/~pf/analise_de_algoritmos/aulas/sscm.html#LCS)
* [Problema
subset-sum](https://www.ime.usp.br/~pf/analise_de_algoritmos/aulas/mochila-subsetsum.html#dynamic-programming)
* [Problema da mochila
booleana](https://www.ime.usp.br/~pf/analise_de_algoritmos/aulas/mochila-bool.html#prog-din)
* [Dijkstra](https://www.ime.usp.br/~pf/analise_de_algoritmos/aulas/dijkstra.html)

### **As diferenças entre algoritmo guloso e programação dinâmica**

Muitas vezes é difícil diferenciar esses algoritmos, mas eles possuem algumas
**características especificas**:

Guloso:

* Pega a alternativa mais promissora;
* É muito rápido;
* Uma decisão tomada é definitiva.

PD:

* Explora todas as alternativas de maneira eficiente;
* Um pouco lento;
* A cada iteração pode se arrepender de decisões tomadas.


Além desses algoritmos citados, existem vários outros. Alguns mais complexos,
outros nem tanto. Espero que tenha gostado :D

**Agradecimento**: *Esse texto foi revisado por* [Allan
Sene](https://www.facebook.com/allan.sene)

Referências:

* [https://en.wikipedia.org/wiki/Sudoku_solving_algorithms](https://en.wikipedia.org/wiki/Sudoku_solving_algorithms)
* [https://norvig.com/sudoku.html](https://norvig.com/sudoku.html)
* [https://en.wikipedia.org/wiki/Local_consistency](https://en.wikipedia.org/wiki/Local_consistency)
* [https://en.wikipedia.org/wiki/Backtracking](https://en.wikipedia.org/wiki/Backtracking)
* [https://jeffe.cs.illinois.edu/teaching/algorithms/notes/03-backtracking.pdf](https://jeffe.cs.illinois.edu/teaching/algorithms/notes/03-backtracking.pdf)
* [https://en.wikipedia.org/wiki/Constraint_satisfaction](https://en.wikipedia.org/wiki/Constraint_satisfaction)
* [https://en.wikipedia.org/wiki/Search_algorithm](https://en.wikipedia.org/wiki/Search_algorithm)
* [https://medium.com/@pmprakhargenius/sudoku-solver-ai-agent-700897b936c7](https://medium.com/@pmprakhargenius/sudoku-solver-ai-agent-700897b936c7)
* [https://dev.to/willamesoares/what-i-learned-from-implementing-a-sudoku-solver-in-python-3a3g](https://dev.to/willamesoares/what-i-learned-from-implementing-a-sudoku-solver-in-python-3a3g)
* [https://en.wikipedia.org/wiki/Constraint_satisfaction](https://en.wikipedia.org/wiki/Constraint_satisfaction)
* [https://wiki.icmc.usp.br/images/c/cb/SCC211Cap11.pdf](https://wiki.icmc.usp.br/images/c/cb/SCC211Cap11.pdf)
* [https://www.ime.usp.br/~pf/analise_de_algoritmos/aulas/dynamic-programming.html](https://www.ime.usp.br/~pf/analise_de_algoritmos/aulas/dynamic-programming.html)
* [https://www.ime.usp.br/~pf/analise_de_algoritmos/aulas/guloso.html](https://www.ime.usp.br/~pf/analise_de_algoritmos/aulas/guloso.html)