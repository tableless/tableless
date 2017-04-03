---
title: O básico sobre Expressões Regulares
author: Diego Eis
type: post
date: 2016-06-15
excerpt: Desmistificando as Expressões Regulares.
url: /o-basico-sobre-expressoes-regulares/
titulo_personalizado:
  - 'Entendendo o básico sobre <strong>Expressões Regulares</strong>'
categories:
  - Código
  - Destaques
  - JavaScript
  - Técnicas e Práticas
tags:
  - expressões regulares
  - regexp

---
Expressão Regular é uma das ferramentas mais úteis que você pode ter. Vira e mexe as Expressões Regulares (RegExp) resolvem desde problemas de Find & Replace no editor até validação de dados em diversos níveis do seu projeto. Mas geralmente a gente só lê sobre Expressões Regulares quando precisamos decifrar aquela linha maluca e ainda assim de um jeito meio descuidado, tateando e tentando fazer dar certo uma combinação de caracteres sem sentido.

## Entendendo as Expressões

Uma Expressão Regular é uma representação para que você encontre padrões em um texto. Esse texto pode ser qualquer coisa, desde o valor de um campo de formulário ou simplesmente um search no seu editor de código predileto… Não importa… O objetivo é filtrar padrões em um punhado de informação textual.

Se você entender que uma Expressão Regular é apenas uma representação formada por símbolos, você não vai ter dificuldades. Cada símbolo representa um tipo de informação. Por exemplo: o `.` (ponto) é um curinga. Ele significa que você pode selecionar qualquer caractere, ou seja, qualquer letra, caractere especial ou número. Exceto a quebra de linha, que é representado pelo símbolo `\n`.

### Classe de caracteres

Vamos começar pelo mais fácil: quando você faz uma busca, você pode buscar uma combinação de caracteres específica, por exemplo: no seu editor de código, se você fizer uma busca por **a**, ele vai te mostrar todas as letras **a** do documento. Mas e se você quiser procurar todas as letras **a** e as letras **e**? Simples, você faz um agrupamento utilizando os colchetes `[]`. Essa expressão irá encontrar todos os caracteres que estiverem dentro dos colchetes. <a target="_blank" href="http://rubular.com/r/i7apRSchRh">Veja esse exemplo, onde ele filtra as letras <code>[ue]</code></a>. Isso se chama **classe de caracteres**, onde você encontra vários caracteres diferentes ao mesmo tempo.

Bom, se você quiser selecionar TODAS as letras do texto, você não precisa escrever o alfabeto inteiro dentro dos colchetes, basta só usar a representação `[A-z]`. Isso quer dizer que ele pega as letras de A até Z, maiúsculas ou minúsculas.

Se você quiser pegar os números, por exemplo, use `[0-9]`. Se quiser todas as letras e todos números: `[A-z0-9]`. Pra facilitar a expressão, você pode usar `\w`, que vai dar no mesmo.

Para você fazer uma negação da Classe criada, basta adicionar um `^` dentro da classe. Por exemplo, você quer pegar todas as combinações que não sejam formadas pela sequência `es`: `[^es]`. <a target="_blank" href="http://rubular.com/r/v5TNAzCQKa">Veja esse exemplo aqui</a>.

Exemplos de classes de caracteres:

  * A expressão `[a-z]` reconhece todas as letras minúsculas.
  * A expressão `[A-Z]` reconhece todas as letras maiúsculas.
  * A expressão `[A-z]` reconhece todas as letras maiúsculas e minúsculas.
  * A expressão `[A-Z0-9]` reconhece todas as letras maiúsculas e números.
  * A expressão `[a-e]` reconhece as letras **a**, **b**, **c**, **d** e **e**.

Atalhos para as classes mais comuns:

  * A classe `\w` recupera todos os caracteres alpha numericos, ou seja, letras e números, mas não acentos ou caracteres especiais. É o equivalente a `[a-zA-Z_0-9]`
  * A classe `\W` pega TODOS os caracteres que não seja alpha numericos, ou seja, pontuações e espaços.
  * A classe `\s` é o equivalente `[ \t\n\x0B\f\r]`
  * A classe `\d` é o equivalente `[0-9]`

E as classses de negação. Lembrando que basta colocar o sinal de `^` logo depois do colchete inicial `[`:

  * A expressão de classe `[^y]` reconhece qualquer caractere, exceto y.
  * A expressão de classe `[^a-e]` reconhece qualquer caractere, exceto **a**, **b**, **c**, **d** e **e**.
  * A expressão de classe `[^\d]` reconhece qualquer caractere, exceto 0, 1, 2, 3, 4, 5, 6, 7, 8 e 9. 

### Múltiplos padrões

Imagine agora que você queira encontrar dois padrões diferentes de caracteres, por exemplo, duas palavras. Bastando usar o símbolo `|` (pipe), que vai significar **OU**. Nesse caso a expressão irá reconhecer um ou o outro padrão. <a target="_blank" href="http://rubular.com/r/QScUEY0F1D">Veja esse exemplo</a> onde recuperamos o retorno das palavras **dolor** ou **labore**.

### Âncoras

As âncoras recuperam a posição **entre os caracteres, mas não os caracteres em si**. Por exemplo, a expressão `^dolor`, vai recuperar as palavras **dolor** que estiverem no início da linha (<a target="_blank" href="http://rubular.com/r/xLTGYJY1fz">veja o exemplo</a>). A expressão `dolor$` vai recuperar o termo que estiver no final da linha (<a target="_blank" href="http://rubular.com/r/FdBuPNAeWE">veja o exemplo</a>).

### Modos

Agora, suponha que você queira pegar uma sequência que contenha um termo parecido, mas que possa estar com algumas letras maiúsculas ou minúsculas. Por exemplo os termos **Lorem**, **lorem**, **loRem**, **lOrEm** etc, bastaria usar a representação `(?i)` antes do termo a ser buscada. A expressão ficaria assim `(?i)lorem`. <a target="_blank" href="http://rubular.com/r/oEesGNpNcZ">Veja este exemplo aqui</a>.

### Brincando de validar um email

Uma tarefa muito corriqueira é a validação de campos de e-mail. Sem entrar nas polêmicas (validar essas coisas sempre é chato), mas é legal para treinar o que você acabou de ler. A expressão para fazer a validação é essa:

<pre class="lang-javascript">^\w*(\.\w*)?@\w*\.[a-z]+(\.[a-z]+)?$
</pre>

Explicando:

  * A expressão `^` indica o começo da string/linha.
  * `\w*` pega qualquer caracteres alpha numericos, é o equivalente a `[a-zA-Z0-9_]`. O asterísco é quantitativo, detectando qualquer quantidade desses caracteres, iniciando no 0 e indo até o infinito.
  * A expressão `(\.\w*)?` significa: parenteses inicia um agrupamento. A expressão `\.` detecta literamente um ponto **.**. A expressão `\w*` qualquer quantidade de caracteres alpha numéricos.
  * O ponto de interrogação (`?`) é quantitativo: determina que o que vier imediatamente antes dele aparecer na expressão 0 ou 1 vez. Nessa expressão ele aparece duas vezes.
  * O arroba seria o arroba do email mesmo&#8230; 
  * `\w*` que aparece depois do arroba já falamos várias vezes logo acima. 
  * `\.[a-z]` pega um ponto seguido de letras minúsculas. vai detectar algo como **.com**, **.net**, etc&#8230;
  * `+` significa que o que estiver imediatamente antes dele precisa aparecer 1 ou mais vezes no termo.
  * `(\.[a-z]+)`: abrimos novamente um agrupamento com o parenteses. `\.` pega o ponto. A classe `[a-z]` seleciona qualquer letra minúscula. E o mais aparece novamente, dizendo que tudo aquilo que estiver antes dele deve aparecer pelo menos 1 vez
  * E a expressão `$` pra finalizar significa final da string.

Veja funcionando abaixo:



#### Para você testar e aprender

Existem alguns sites pra facilitar a criação e o debug das expressões regulares, veja abaixo:

  * <https://regex101.com/r/vS7vZ3/224#javascript>
  * <http://rubular.com>

  * <http://aprenda.vidageek.net/aprenda/regex>
  * <http://turing.com.br/material/regex/introducao.html#>
  * <https://msdn.microsoft.com/pt-br/library/az24scfc(v=vs.110).aspx>