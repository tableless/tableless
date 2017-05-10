---
title: Sobre nomes e sobrenomes
author: Diego Eis
type: post
date: 2006-07-16
url: /sobre-nomes-e-sobrenomes/
tweetbackscheck:
  - 1355358732
shorturls:
  - 'a:3:{s:9:"permalink";s:48:"http://tableless.com.br/sobre-nomes-e-sobrenomes";s:7:"tinyurl";s:26:"http://tinyurl.com/42ndtcq";s:4:"isgd";s:19:"http://is.gd/JRc8k5";}'
twittercomments:
  - 'a:2:{i:10665222859657216;s:7:"retweet";i:10450313265811456;s:7:"retweet";}'
tweetcount:
  - 2
dsq_thread_id: 503035688
categories:
  - Artigos
tags:
  - cotidiano
  - Técnicas e Práticas

---
Nomenclatura no desenvolvimento web é um assunto que muitas vezes é ignorado pela maioria dos profissionais. E é o que muitas vezes causa problemas no decorrer do projeto.
  
Escolher nomes adeqüados, tanto para arquivos quanto para nomes de variáveis, identificação de elementos, seções e etc, é tão importante quanto qualquer outra parte do projeto. Este pequeno detalhe pode ser o começo de uma grande confusão sem volta.

Imagine um site simples com elementos básicos como um cabeçalho, uma coluna na esquerda, uma coluna no meio para o conteúdo e outra coluna no lado direito, e por último o rodapé.
  
Ao criar a estrutura XTHML para este site, o primeiro nome que vem a cabeça para nomear, por exemplo a coluna da esquerda é: **id=&#8221;colunaesquerda&#8221;**. Ou algo parecido, não é?
  
Este nome, com certeza é muito sugestivo e objetivo. Mas, infelizmente, pode lhe trazer problemas sérios. Suponha que este site seja feito com CSS, que lhe dá facilidade para mudar o layout facilmente mudando algumas linhas de código. Você ou seu cliente resolve que o site deve mudar um pouco de visual. Que a coluna da esquerda, deveria agora ficar do lado direito, e vice-versa.
  
Então, você localiza no CSS o objeto chamado **#colunaesquerda** e o posiciona à direita. Localiza o objeto **#colunadireita** e o posiciona à esquerda. Conseguiu calcular o problema? O elemento **#colunaesquerda** não é mais a coluna da esquerda, ele está alinhado agora a direita. Não parece estranho um objeto se chamar **#colunaesquerda** estar alinhado à direita?
  
Imagine o trabalho que será mudar este nome nos arquivos? Provavelmente você fará um post-it com esta observação e guardará embaixo do teclado, onde ele ficará esquecido até a próxima limpeza da faxineira.

Ter bons nomes é uma questão de semântica. Não é raro acontecer casos como o citado acima. Isto pode se tornar uma bola de neve. Uma vez errado, ficará errado até o final do projeto, e quanto mais tempo o erro continuar, mais dificil será corrigi-lo. Por isso, preste bem atenção quanto a nomenclatura de elementos.

Uma dica que sempre dou aos alunos [aqui nos cursos][1], é nomear os elementos da página de acordo com sua função: Se na coluna da esquerda houver o menu principal do site, nomeio o div como **#menuprincipal** ou simplesmente **#menu**. Se a coluna da direita houver publicidade por exemplo, nomeie esta coluna como **#publicidade** e não **#colunadireita**. Isso evitará muito transtorno durante o desenvolvimento do projeto. Nomeie os elementos de acordo com sua função.

Esta regra de nomeclatura também pode ser aplicado à arquivos. Já falei aqui sobre [Modulação de CSS][2]. Se você irá criar arquivos CSS individuais para cada seção do site, nomeie de acordo com a função da seção do site. Se é um CSS que irá formatar o menu principal, o arquivo poderia se chamar **menuprincipal.css**_._ Nem preciso dizer que nomes como **menu\_principal\_coluna_esquerda.css** __não são boas pedidas.

Lembre-se que nomenclatura dos elementos pode ser questão de semântica. É coisa séria e pode trazer muitos problemas se não for pensado direito. Gaste uns segundos a mais para elaborar nomes melhores. Não dói e previne dor de cabeça.

 [1]: http://visie.com.br/cursos/
 [2]: http://tableless.com.br/css-modular-breve-explicacao