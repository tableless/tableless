---
title: Pontuação de especificidade da CSS
author: Diego Eis
type: post
date: 2011-04-25
excerpt: Entenda como o browser calcula a especificidade do seu seletor e evite conflitos entre estilos.
url: /pontuacao-especificidade-css/
tweetbackscheck:
  - 1356397672
shorturls:
  - 'a:3:{s:9:"permalink";s:52:"http://tableless.com.br/pontuacao-especificidade-css";s:7:"tinyurl";s:26:"http://tinyurl.com/3ce4bcl";s:4:"isgd";s:19:"http://is.gd/yGYm4z";}'
twittercomments:
  - 'a:10:{i:129293865323728896;s:7:"retweet";i:129191757375225856;s:7:"retweet";i:129181835682004994;s:7:"retweet";i:129179365765423104;s:7:"retweet";i:129179030611173376;s:7:"retweet";i:151369580315545600;s:7:"retweet";i:151367903579607041;s:7:"retweet";i:158724569199415296;s:7:"retweet";i:169585953051131904;s:7:"retweet";i:182259699406737409;s:7:"retweet";}'
tweetcount:
  - 17
dsq_thread_id: 503040210
categories:
  - CSS
  - HTML
  - Técnicas e Práticas
tags:
  - 2011
  - CSS
  - CSS3
  - desenvolvimento web
  - tecnicascss

---
Você pode ler algo sobre [herança e especificadade do CSS aqui][1]. O problema é que nesse artigo eu não explico muito sobre a pontuação da especificidade do CSS. Como que o browser calcula qual propriedade é mais especifica que outra? 

### Para que serve?

A graça do CSS é que você pode manipular os estilos de diversos elementos com pouco esforço. Se você quer modificar a font de todos os parágrafos ou títulos do seu site é simples de se fazer mudando um parâmetro da linha onde é definida a propriedade `font`. Se você quiser definir estilos restritos para os botões por exemplo, também é muito simples, basta criar uma classe e pronto. Você tem toda a flexibilidade que precisa para formatar os elementos do layout.

O problema é que uma hora ou outra você cai no problema de herança de estilos, onde alguns elementos herdam estilos de elementos criados para outros propósitos. Isso acontece que você utilizou mesmas tags, ou colocou elementos do mesmo gênero, mas com funções visuais diferentes dentro de um mesmo pai e assim por diante.
  
Outro problema é quando uma pessoa define um determinado estilo para um elemento P, por exemplo. Depois, com o passar do projeto, outra pessoa tenta formatar um parágrafo em outro determinado ponto do layout, mas não consegue, porque os estilos estão entrando em conflito com um código criado a tempos atrás. Aí entra o trabalho de investigação para descobrir em qual ponto está o código que causa o conflito de propriedades. E isso acontece porque um seletor mais específico que o seu foi criado, e isso sobrescreve seu código.

Seu seletor pode ser algo parecido:

<pre lang="CSS" line="1">.content p {color:red;}
</pre>

E colocam um seletor mais específico, assim:

<pre lang="CSS" line="1">.content article p {color:blue;}
</pre>

Logo, um problema de conflito pode acontecer. E acredite, isso é mais comum do que você pensa, principalmente em projetos onde várias pessoas escrevem client-side.

### Cálculo de especificidade

Como o browser define o grau de prioriedades dos seletores? É simples: ele pontua o seletor de acordo com sua estrutura. Cada elemento, classe, id e etc vale pontos de especificidade. A pontuação é somada numa estrutura simples que começam com zeros (0), assim: 0,0,0,0. A estrutura é composta por quatro números, quanto mais o número estiver na esquerda, mais específico e mais força ele tem sobre outros seletores. Veja a tabela a baixo:

| Seletor           | Pontuação | Descrição                                                                                                                        |
| ----------------- | --------- | -------------------------------------------------------------------------------------------------------------------------------- |
| div ul li a       | 0,0,0,4   | 4 elementos, 4 pontos na primeira casa                                                                                           |
| div.content ul li | 0,0,1,3   | Uma classe vale um ponto na segunda casa. Mais 3 elementos, mais 3 pontos na primeira casa.                                      |
| a:hover           | 0,0,1,1   | Um elemento, um ponto na primeira casa. Mais uma pseudo-classe, que equivale a uma classe e logo ganha um ponto na segunda casa. |
| div.menu a:hover  | 0,0,2,2   | Dois elementos, dois pontos na primeira casa. Mais uma classe e uma pseudo-classe, mais dois pontos na segunda casa.             |
| #content p        | 0,1,0,1   | Um ID equivale a um ponto na terceira casa. Mais um elemento, que equivale a um ponto na primeira casa.                          |
| article#content p | 0,1,0,2   | Dois elementos, dois pontos na primeira casa. Um ID, um ponto na terceira casa.                                                  |

Simples, ahn?!

Agora vamos entender melhor. Veja o seletor abaixo:

<pre lang="CSS" line="1">header nav ul li a {color:blue;}
</pre>

Como tem 5 elementos descritos, a pontuação é 0,0,0,5.
  
Se colocarmos uma classe nos links e escrevermos assim:

<pre lang="CSS" line="1">.itemlink {color:red;}
</pre>

Cada classe equivale a uma pontua na segunda casa, ficando assim: 0,0,1,0. Quanto mais para esquerda, mais prioriedade o seletor tem. Logo, o nosso seletor acima, que tem um ponto na segunda casa por causa da classe (0,0,1,0) é mais específico que o primeiro seletor que escrevemos, que tem 5 ítens (0,0,0,5) e sobrescreverá o estilo. Se colocarmos um ID, como no exemplo abaixo:

<pre lang="CSS" line="1">#menu a {color:yellow;}
</pre>

A prioridade fica 0,1,0,1. Um elemento, um ponto na primeira casa, um ID um ponto na terceira casa. Tendo ID, a prioridade aumenta mais ainda que a classe, e este seletor sobrescreverá todos os outros que fizemos.

### A Quarta Casa

Nos exemplos acima vimos até a terceira casa. A quarta casa é utilizada em duas ocasiões: 1) quando colocamos CSS inline, ou seja, diretamente no elemento HTML e quando temos o valor **`!important`** declarado no valor do código CSS. Logo:

<pre lang="CSS" line="1">#menu a {color:yellow;}
</pre>

O código acima tem pontuação 0,1,0,0. E perde para o código abaixo:

<pre lang="HTML" line="1"><a href="#" style="color: purple">Home</a>
</pre>

Colocando o STYLE diretamente no elemento temos uma pontuação de 1,0,0,0. Não importa se outros seletores tem ID, CLASS e etc&#8230; Ele sempre vai sobrepor porque é pontuado na última casa.

A mesma coisa acontece quando utilizamos o !important. Segue o código:

<pre lang="CSS" line="1">#menu a {color:yellow !important;}
</pre>

Tem a mesma pontuação do atributo STYLE: 1,0,0,0.

### E quando há a mesma pontuação?

Suponhamos que dois seletores tenham a mesma pontuação, como abaixo:

<pre lang="CSS" line="1">.menu a {color:yellow;}
.optItem a {color:blue;}
</pre>

Pontuação: 0,0,1,1. Um elemento, uma classe. O desempate nesse caso é: quem veio por último ganha.
  
No nosso exemplo acima o browser leu que os links dentro do elemento CLASS MENU fiquem com cor AMARELO. Logo depois ele leu que estes mesmos links ficassem com cor AZUL, então essa linha sobrescreveu a anterior.

### Recomendações

É interessante que você resolva os problemas de conflito utilizando o próprio seletor, sem apelar para o `!important` ou o atributo `style`. Assim você mantém o código sob controle. Se começarmos a colocar muito `!important` no meio do código, equivale a regra de: se todo o mundo é importante, ninguém é importante. E então o `!important` perde seu efeito e passará a ser inútil.

 [1]: http://tableless.com.br/efeito-cascata-e-especificidade-do-css "Leia mais sobre especificadade e herança do CSS"