---
title: 'Lições sobre semântica #2'
authors: Diego Eis
type: post
date: 2004-11-30
url: /licoes_sobre_semantica_2/
tweetbackscheck:
  - 1355163108
shorturls:
  - 'a:3:{s:9:"permalink";s:48:"https://tableless.com.br/licoes_sobre_semantica_2";s:7:"tinyurl";s:26:"https://tinyurl.com/3kfdd49";s:4:"isgd";s:19:"https://is.gd/SbDcZo";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 503032137
categories:
  - Geral
tags:
  - Técnicas e Práticas

---
E lá vamos nós de novo&#8230; Estou devendo a todos um artigo sobre semântica. Quero dizer que estou no processo&#8230; semântica é um assunto um tanto abrangente, então, aguardem.
  
Abaixo, mais uma questão sobre semântica. Qual a opinião de vocês?

**Situação**: Estou desenvolvendo um artigo, escrevendo no meu blog ou simplesmente fazendo um texto para um trabalho na faculdade. Achei na internet uma frase muito legal sobre o assunto que estou escrevendo, e gostaria de colocar no meu trabalho, artigo ou post do blog. A questâo é a seguinte:

**Que tag é mais apropriada para colocar esta frase no meu texto?**

  1. <cite> Aqui vai a frase importante que achei.</cite>
  2. <q> Aqui vai a frase importante que achei.</q>
  3. <blockquote> Aqui vai a frase importante que achei.</blockquote>

Qual a sua opinião?! Comente!~

**CONCLUSÃO:**
  
Acabemos com as dúvidas!
  
Esta situação é um tanto complicada. Para resolver este problema, nada melhor que aprender o que cada tag faz. Este é o óbvio da questão, e é a razão por estarmos aqui discutindo. Então, vamos as definições:

**Tag &#8220;cite&#8221;**: Ela serve para defifinir uma **citação**. Espere, não um texto ou uma frase, mas sim o nome do AUTOR ou o nome da FONTE de onde você tirou o texto ou a frase. Exemplo:
  
Horrível coisa é cair nas mãos do Deus vivo.<cite> Apóstolo Paulo</cite>
  
Ok?!

**Tag &#8220;q&#8221; e &#8220;blockquote&#8221;**: As duas tags &#8220;q&#8221; e &#8220;blockquote&#8221; são para definir o texto da citação. Com apenas um diferencial: A tag &#8220;q&#8221; define textos pequenos e a &#8220;blockquote&#8221; textos grandes. Logo, no exemplo acima, usaríamos a tag &#8220;q&#8221;:
  
<q>Horrível coisa é cair nas mãos do Deus vivo.</q> <cite>Apóstolo Paulo</cite>

Se o texto fosse maior:
  
<blockquote>5 Pois os vivos sabem que morrerão, mas os mortos não sabem coisa nenhuma, nem tampouco têm eles daí em diante recompensa; porque a sua memória ficou entregue ao esquecimento.
  
6Tanto o seu amor como o seu ódio e a sua inveja já pereceram; nem têm eles daí em diante parte para sempre em coisa alguma do que se faz debaixo do sol. </blockquote><cite>Salomão</cite>

Então, resumindo: A tag &#8220;cite&#8221; é apenas para definir o nome do Autor ou Fonte de onde você tirou o texto. As tags &#8220;q&#8221; e &#8220;blockquote&#8221; servem para definir os textos da citação. Tag &#8220;q&#8221; para textos pequenos e a tag &#8220;blockquote&#8221; para textos grandes.

Ao usar as tags &#8220;q&#8221; e &#8220;blockquote&#8221; você defini um atributo chamado &#8220;cite&#8221;. O valor deste atributo é a URL de onde você tirou a citação.
  
<q cite=&#8221;https://elcio.locaweb.com.br/poesias/autor.asp?cod=1&#8243;>Feliz aquele que é capaz de amar até mesmo aquilo que não compreende.</q>
  
Entendido?

Portanto, a resposta da pergunta do começo do post, é que seria mais semântico usarmos a tag &#8220;q&#8221; para a frase, seguido da tag &#8220;cite&#8221; para definir o autor da frase.

Abaixo, veja os links que usei como referência:

  * [The <blockquote> tag][1]
  * [The <q> tag][2]
  * [9.2.2 Quotations: The BLOCKQUOTE and Q elements][3]
  * [9.2.1 Phrase elements: EM, STRONG, DFN, CODE, SAMP, KBD, VAR, CITE, ABBR, and ACRONYM][4]

Espero que as dúvidas tenham sido respondidas.

 [1]: https://www.w3schools.com/tags/tag_blockquote.asp
 [2]: https://www.w3schools.com/tags/tag_q.asp
 [3]: https://www.w3.org/TR/REC-html40/struct/text.html#edef-Q
 [4]: https://www.w3.org/TR/REC-html40/struct/text.html#edef-CITE