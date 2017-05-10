---
title: CSS3 – Breve introdução ao RGBA
author: Diego Eis
type: post
date: 2011-05-02
excerpt: 'Normalmente em web trabalhamos com cores na forma de hexadecimal. Agora o RGBA nos permite que você aplique em uma determinada cor transparência. '
url: /css3-breve-introducao-a-rgba/
tweetbackscheck:
  - 1356404509
shorturls:
  - 'a:3:{s:9:"permalink";s:52:"http://tableless.com.br/css3-breve-introducao-a-rgba";s:7:"tinyurl";s:26:"http://tinyurl.com/3mbg5e6";s:4:"isgd";s:19:"http://is.gd/R9fE7a";}'
twittercomments:
  - 'a:11:{i:126007285947437056;s:7:"retweet";i:125918556280987648;s:7:"retweet";i:151734836422381568;s:7:"retweet";i:153886273864613888;s:7:"retweet";i:151742617695174657;s:7:"retweet";i:151735554004877313;s:7:"retweet";i:151734970220675073;s:7:"retweet";i:151734887655809024;s:7:"retweet";i:161627565944078336;s:7:"retweet";i:161626587282935809;s:7:"retweet";i:161626465887191040;s:7:"retweet";}'
tweetcount:
  - 18
dsq_thread_id: 503040243
categories:
  - CSS
  - CSS3
  - HTML
  - Técnicas e Práticas
tags:
  - 2011
  - CSS3
  - desenvolvimento web
  - Na Prática
  - padroes web
  - rgba
  - tecnicascss

---
### Introdução ao RGB

Normalmente em web trabalhamos com cores na forma de hexadecimal. É a forma mais comum e mais utilizada desde os primórdios do desenvolvimento web. Mesmo assim, há outros formatos menos comuns que funcionam sem problemas, um destes formatos é o RGB. O RGB são 3 conjuntos de números que começam no 0 e vão até 255 (0% até 100%), onde o primeiro bloco define a quantidade de vermelho (Red), o segundo bloco a quantidade de verde (Green) e o último bloco a quantidade de azul (Blue). A combinação destes números formam todas as cores que você pode imaginar.

No HTML o RGB pode ser usado em qualquer propriedade que tenha a necessidade de cor, como: color, background, border etc. Exemplo:
  
[cc lang=&#8221;css&#8221;]
	  
p {
		  
background:rgb(255,255,0);
		  
padding:10px;
		  
font:13px verdana;
	  
}
  
[/cc]

Este código RGB define que o background o elemento P será amarelo.

### Aplicando o RGBA e a diferença da propriedade OPACITY

Até então nós só podíamos escrever cores sólidas, sem nem ao menos escolhermos a opacidade dessa cor. O CSS3 nos trouxe a possibilidade de modificar a opacidade dos elementos via propriedade opacity. Lembrando que quando modificamos a opacidade do elemento, tudo o que está contido nele também fica transparente e não apenas o background ou a cor dele. [Veja o exemplo e compare][1]. É aí que entra o RGBA. 

O RGBA funciona da mesma forma que o RGB. No caso do RGBA, além dos 3 canais RGB (Red, Green e Blue) há um quarto canal, A (Alpha) que controla a opacidade da cor. Nesse caso, podemos controlar a opacidade da cor de background, borda, color ou qualquer propriedade que contenha cor sem afetar a transparência dos outros elementos:

Veja um exemplo aplicado abaixo:

[cc lang=&#8221;css&#8221;]
	  
p {
		  
background:rgba(255,255,0, 0.5);
		  
padding:10px;
		  
font:13px verdana;
	  
}
  
[/cc]

O último valor é referente ao canal Alpha, onde 1 é totalmente visível e 0 é totalmente invisível. No exemplo acima está com uma opacidade de 50%. 

Como o Hexadecimal, você não precisa decorar todos estes números. Hoje, qualquer programa gráfico já dá o código do RGB da cor utilizada. O Hexadecimal não foi descontinuado. Se caso você tenha alguma cor que não ficará transparente ou algo do tipo, você pode continuar utilizando hexa e para aqueles que tem transparência, você pode utilizar o RGBA sem problemas.

[Veja novamente o exemplo aqui][1] e o [código no github do Tableless][2].

 [1]: http://tableless.github.com/exemplos/rgba/ "Teste de RGBA"
 [2]: https://github.com/tableless/exemplos/tree/gh-pages/rgba "Código no Github"