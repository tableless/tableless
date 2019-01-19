---
title: Um pouco sobre CSS Grid Layout
authors: Matheus Alves
type: post
image: https://source.unsplash.com/dzCBKa8rIAM/748x500
date: 2019-01-19
excerpt: Tutorial básico da tecnologia padrão do CSS para criação de grids.
categories:
  - CSS
  - Semântica
---

O CSS Grid Layout é uma tecnologia do CSS que [desde 2017][caniuse] está
presente na maioria dos principais navegadores modernos. Ela nos permite criar
*layouts* baseados em *grids* de uma forma extremamente rápida, fácil e...
padronizada. Apresentarei rapidamente nesse artigo um pouco das principais
coisas que você pode fazer com essa *feature*.

## Introdução

Não há segredo algum para dar início a um elemento simples. Para isso basta
criar uma estrutura HTML com um *container* e alguns itens que farão parte do
*layout*. Veja uma estrutura bem simples para começar:

<script src="https://gist.github.com/theuves/93daecd4b552b10682927a1fb9c8de8d.js"></script>

Após isso, você terá duas opções para fazer com que o elemento `.grid` seja uma
*grid*: ou você usa `display: grid` ou `display: inline-grid`. A diferença entre
essas duas opções, pode-se dizer, que é a mesma entre `block` e `inline-block`.

Para o exemplo usaremos somente `display: grid`.

<script src="https://gist.github.com/theuves/d30c575500f367ea4f8c556f5045be69.js"></script>

Veja o resultado:

{{< codepen
  hash="wRLZap"
  user="theuves"
  tab="css,result"
>}}

## Configuração básica do *container*

Se você olhou o resultado do código anterior, percebeu que não houve nada de
interessante. Pelo contrário, tudo ficou como se você tivesse definido um
simples `display: block`, visto que todos os itens ficaram um embaixo do outro
sem nenhuma coluna definida – posto que esse é o principal objetivo do CSS Grid
Layout.

Para que possamos montar a nossa *grid*, antes devemos definir qual será o seu
formato, por exemplo: 3 colunas × 2 linhas – que é o que será usado nesse
exemplo. Depois disso, usa-se a propriedade `grid-template-columns` para
definir a quantidade de colunas e a largura de cada uma delas e consequentemente
fazer a quebra de linhas que é automática.

<script src="https://gist.github.com/theuves/43b3a6ad167f80656e9d8348370e63f7.js"></script>

Isso é bem intuitivo, onde percebe-se facilmente que haverá três colunas e que
elas terão, respectivamente, 100px, 200px e 300px. Veja o exemplo no CodePen:

{{< codepen
  hash="yGdrJZ"
  user="theuves"
  tab="css,result"
>}}

No entanto, se você quisesse colunas com larguras iguais, relativas à largura
do *container* (onde, consequentemente, cada coluna teria cerca de 33,3% de 
largura), bastaria adicionar a propriedade `auto` para todas, ficando:

<script src="https://gist.github.com/theuves/c327278ced4b328a3f5dc2bb31571376.js"></script>

> **DICA:** Quando você tiver um caso como esse, no CSS Grid, você terá a
possibilidade de utilizar a função `repeat()` e economizar algumas dedadas no
teclado, além de deixar o código mais atraente. Nesse caso em específico
poderiamos ter usado `repeat(3, auto)`. Veja mais sobre essa função no [MDN web
docs][mdn_repeat] (em inglês).

Se tem `grid-template-columns`, certamente deveria ter também
`grid-template-rows`. E tem! Com essa propriedade você basicamente definirá a
altura de suas linhas. Sem segredos: é o mesmo sistema das colunas.

## Configuração básica dos itens

Agora que foi apresentado algumas configurações para o *container* que abrigará
os itens, é importante saber qual configuração os itens podem ter. As
propriedades existentes para os itens do CSS Grid Layout se resumem
simplesmente em definições para a localização e o espaço ocupado por eles.
Desse modo, por exemplo, você pode fazer com um que um item ocupe o espaço de
outros itens também, permitindo, assim, que você não fique preso apenas à
*containers* quadriculados.

Para isso temos as seguintes propriedades:

- `grid-row-start` - que recebe a linha vertical em que deve iniciar,
- `grid-row-end` - que recebe a linha vertical em que deve acabar,
- `grid-column-start` - que recebe a linha horizontal em que deve iniciar e
- `grid-column-end`- que recebe a linha horizontal em que deve acabar.

> **DICA:** Há algumas formas abreviadas para tudo isso. Você pode usar somente
[`grid-row`][mdn_grid-row] ou [`grid-column`][mdn_grid-column] e receber dois
valores de `*-start` e `*-end` respectivamente. Ou você também pode usar
[`grid-area`][mdn_grid-area] que recebe respectivamente: `*-row-start`,
`*-column-start`, `*-row-end` e `*-column-end` separados por uma barra (`/`).
Você pode entender melhor o funcionamento desses atalhos clicandos nos *links*
e lendo a documentação detalhada de cada um (em inglês).

Veja um exemplo simples do que essas propriedades podem fazer:

{{< codepen
  hash="oJrRWq"
  user="theuves"
  tab="css,result"
>}}

Observe que o *style* que define o comportamento do item 1 é:

<script src="https://gist.github.com/theuves/a95352acd3d62219ac6ee3686deafa21.js"></script>

Um código como esse pode ser um pouco contra-intuitivo, pois veja que o
`grid-row-end` é 3 enquanto só temos 2 linhas e não 3. Isso ocorre pois o valor
recebido por essas propriedades não se referem à linha DE cada item e sim à
linha ENTRE cada item. Veja a ilustração abaixo para entender o funcionamento
desses tipos de linha:

![IFuncionamento das linhas](https://i.imgur.com/NccapEu.png)

Desse modo, o código do exemplo mais acima inicia entre a borda e o começo da
linha do item 1 e termina no final da linha do item 2.

> **DICA**: Para facilitar o entendimento de um código como esse, poderiamos
ter simplesmente usado `span` antes da linha do item. Por exemplo:
`grid-row-end: span 2`. Isso deixaria mais claro que deveria terminar na linha
2 dos itens.

## Distância entre itens

Se você prestou atenção no último exemplo de código no CodePen, viu que há um
espaço entre os itens, certo?! Para distanciar um item de outro, você
intuitivamente poderia pensar em usar `margin` dentro deles, porém, essa não
seria a melhor solução para o problema. O CSS oferece as seguintes propriedades
para fazer isso padronizadamente:

- [`grid-column-gap`][mdn_grid-column-gap] - que distancia os itens das colunas
- [`grid-row-gap`][mdn_grid-row-gap] - que distancia os itens das linhas e
- [`grid-gap`][mdn_grid-gap] - que é uma forma abreviada dos outros.

Observe que essas propriedades devem ser definidas dentro do *container* e não
dentro dos itens. Além disso, tenha em mente que `grid-gap` pode receber um
único valor que será usado tanto para a coluna quanto para a linha ou pode
receber dois valores: um para a linha e outro para a coluna, respectivamente.

## Alinhamento de itens

O CSS também nos dá a possibilidade de alinhar os itens __dentro do
*container*__, tendo as propriedades `justify-content` (para o alinhamento
horizontal dos itens) e `align-content` (para o alinhamento vertical dos itens).
Contudo, essas propriedades não são exclusivas do CSS Grid Layout. Veja no *MDN
web docs* a documentação delas e tenha uma experiência interativa do que cada
valor pode fazer, acessando [aqui][mdn_justify-content] (para `justify-content`)
e [aqui][mdn_align-content] (para `align-content`).

## Nomeando itens

Essa, sem dúvidas, é a parte mais interessante do CSS Grid Layout, no qual,
podemos nomear cada item e fazê-los se posicionarem automaticamente no
*container*, sem a necessidade de configurar `grid-row`, `grid-column` ou
qualquer outra coisa do gênero, além de deixar o código extremamente semântico.

Para isso, basta definir a propriedade `grid-template-areas` como um *template*
do itens do *container* e em seguida "linkar" as definições desse *template*
dentro de cada item como a propriedade `grid-area`.

Veja a seguinte estrutura HTML:

<script src="https://gist.github.com/theuves/9f1f6ca518e84e3b9eac699d4b9b0702.js"></script>

E a seguinte definição CSS:

<script src="https://gist.github.com/theuves/9b43411b47002dd72de04a96a1b0195c.js"></script>

Agora veja o resultado no CodePen:

{{< codepen
  hash="ZVdVGP"
  user="theuves"
  tab="css,result"
>}}

## Mais informações

Isso tudo é o básico que pude colocar em um artigo de rápida leitura. Caso você
queira se aprofundar na tecnologia, poderá ver a documentação da
[Mozilla][mdn_grid-layout] ou da [W3Schools][w3schools] (ambos em inglês). Há
também um artigo interessante no CSS-Tricks chamado [*A Complete Guide to
Grid*][css-tricks] (em inglês também) que você pode dar uma conferida para
estudar um pouco mais.

[caniuse]:https://caniuse.com/#feat=css-grid
[mdn_repeat]:https://developer.mozilla.org/en-US/docs/Web/CSS/repeat
[mdn_grid-row]:https://developer.mozilla.org/en-US/docs/Web/CSS/grid-row
[mdn_grid-column]:https://developer.mozilla.org/en-US/docs/Web/CSS/grid-column
[mdn_grid-area]:https://developer.mozilla.org/en-US/docs/Web/CSS/grid-area
[mdn_grid-column-gap]:https://developer.mozilla.org/en-US/docs/Web/CSS/grid-column-gap
[mdn_grid-row-gap]:https://developer.mozilla.org/en-US/docs/Web/CSS/grid-row-gap
[mdn_grid-gap]:https://developer.mozilla.org/en-US/docs/Web/CSS/grid-gap
[mdn_justify-content]:https://developer.mozilla.org/en-US/docs/Web/CSS/justify-content
[mdn_align-content]:https://developer.mozilla.org/en-US/docs/Web/CSS/align-content
[mdn_grid-layout]:https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Grid_Layout
[w3schools]:https://www.w3schools.com/css/css_grid.asp
[css-tricks]:https://css-tricks.com/snippets/css/complete-guide-grid/
