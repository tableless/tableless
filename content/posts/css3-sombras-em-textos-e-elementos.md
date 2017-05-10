---
title: CSS3 – Sombras em textos e elementos
author: Diego Eis
type: post
date: 2011-06-16
excerpt: Sombras em elementos e textos. O CSS3 nos trouxe essa possibilidade. Saiba como funciona as propriedades text-shadow e box-shadow.
url: /css3-sombras-em-textos-e-elementos/
tweetbackscheck:
  - 1356422306
shorturls:
  - 'a:3:{s:9:"permalink";s:58:"http://tableless.com.br/css3-sombras-em-textos-e-elementos";s:7:"tinyurl";s:26:"http://tinyurl.com/3rhtmzp";s:4:"isgd";s:19:"http://is.gd/yAiUvJ";}'
twittercomments:
  - 'a:14:{i:129005267408011264;s:7:"retweet";i:128794304012488704;s:7:"retweet";i:128782801267990528;s:7:"retweet";i:128781696266014720;s:7:"retweet";i:128775883149418496;s:7:"retweet";i:128749204188307456;s:7:"retweet";i:128728147079331840;s:7:"retweet";i:128697006494453761;s:7:"retweet";i:155326084773191680;s:7:"retweet";i:155104929781002240;s:7:"retweet";i:155059206842630146;s:7:"retweet";i:155041493973864448;s:7:"retweet";i:155039139656507393;s:7:"retweet";i:169916200808222721;s:7:"retweet";}'
tweetcount:
  - 46
dsq_thread_id: 503028104
categories:
  - CSS
  - CSS3
  - HTML
tags:
  - 2011
  - CSS3
  - desenvolvimento web
  - html5
  - Na Prática
  - tecnicascss

---
Uma das vantagens mais interessantes que o CSS3 nos dá é a possibilidade de cada vez menos abrirmos o Photoshop. Não precisamos mais abrir o Photoshop para criar bordas arredondadas, gradientes e agora até mesmo sombras. Agora temos a possibilidade de inserirmos sombras em textos e em elementos. As propriedades tem nomes diferentes mas a mesma sintaxe. Veja abaixo:

[cc lang=&#8221;html&#8221;]
  
p {
      
text-shadow: 5px 5px 5px rbga(0,0,0,0.5);
      
box-shadow: 5px 5px 5px rgba(0,0,0,0.5);
  
}
  
[/cc]

Esqueça agora o nome da propriedade e entenda melhor seus parâmetros: colocamos 3 números e por último a cor. Na cor utilizamos RGBA para termos controle sobre o canal de transparência da cor. Você pode ver um [artigo sobre RGBA neste link][1].

Agora vamos entender o significado dos números: os dois primeiros números se referem a posição da sombra: o primeiro número é referente a posição vertical começando pelo topo e o segundo número é referente a posição horizontal, começando pela esquerda. 

O terceiro número se refere ao Blur. Sua sombra pode ser rígida ou &#8220;esfumaçada&#8221;. Isso depende do design que você criou o pegou para implementar. Você controla a rigidez da sombra por este número. 

Praticamente todo o controle de sombra que você tem no Illustrator, você agora tem com o CSS3.

Na minha opinião pessoal há ainda algumas features que poderiam ser incluídas nessa especificação como por exemplo a possibilidade de colocarmos sombras apenas nos lados que quisermos e termos o controle individual das sombras. Mais ou menos como temos na propriedade border, onde podemos inserir borda apenas de um lado do objeto e podemos controlar as características dessa borda.

Você [pode ver um exemplo em nosso Github][2]. Lembre-se que codificar é de graça&#8230; Faça um teste agora, antes de deixar este post de lado. 😉

 [1]: http://tableless.com.br/css3-breve-introducao-a-rgba "Entenda como funciona o RGBA"
 [2]: http://tableless.github.com/exemplos/css3-shadow.html "Exemplo de sombra com CSS3"