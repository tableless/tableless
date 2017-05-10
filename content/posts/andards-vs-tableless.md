---
title: Web Standards vs Tableless
author: Diego Eis
type: post
date: 2006-07-27
url: /web-standards-vs-tableless/
tweetbackscheck:
  - 1356358846
shorturls:
  - 'a:3:{s:9:"permalink";s:50:"http://tableless.com.br/web-standards-vs-tableless";s:7:"tinyurl";s:26:"http://tinyurl.com/452t7ux";s:4:"isgd";s:19:"http://is.gd/kzgdBB";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 503035771
categories:
  - Artigos
  - Geral
tags:
  - cotidiano

---
Eu já falei muito sobre este assunto aqui, mas vejo que alguns desenvolvedores ainda tem dúvidas&#8230; Mesmo assim, pode servir de aviso para os marinheiros de primeira viagem.
  
O Henrique escreveu no blog dele também sobre isso: [Tableless vs Web Standards][1]. Aliás, nós combinamos para escrevermos quase que ao mesmo tempo&#8230; 🙂

Talvez, se você nunca tenha me ouvido falar sobre o assunto, possa parecer um tanto assustador, mas ouça bem: Se um site é Tableless, não quer dizer que ele siga os Padrões.
  
Pois é&#8230;

Você pode fazer um site com divs por todos os lados. Colocar vários divs aninhados, como fazia com Tabelas antigamente. Você pode até, se quiser, fazer um site inteiro [usando apenas listas][2]. Acontece que você não estará seguindo os padrões da mesma maneira que você não seguia quando fazia um site com Tabelas.

Já disse aqui, mas não custa nada repetir: Semântica é alma do negócio. [Semântica é que manda][3]. Nas recomendações do W3C, cada objeto tem sua função. Cada tag tem seu papel a cumprir, tem sua identificação. Você não pode simplesmente fazer um título com um DIV. Se alguma aplicação navegar em sua página, e se deparar com este objeto como ele vai saber que este texto é um Título? E é assim com os outros elementos também.

Um site feito com estas características, também passa na validação. Passar na validação quer dizer que o site é Tableless? Não passar na validação quer dizer que o site deixou de ser Tableless? Passar na validação quer dizer que o site segue os padrões?
  
Se você colocar um <p> e formatar por CSS para ele ter características (fonte, tamanho, etc) de um título, ele vai passar na validação? Claro que vai! Ele segue os padrões?

O termo Tableless é polêmico. Tableless é apenas um nome. Aqui no brasil este termo pegou, lá fora não. Os gringos usam o termo &#8220;CSS Layout&#8221; para se referir a um site que segue os padrões, da mesma forma que usamos o &#8220;Tableless&#8221;. No fundo, no fundo é tudo a mesma coisa, mas temos que tomar cuidado com esta observação: Um site tableless não é sinônimo de seguir os padrões. Um Layout feito com CSS não é sinônimo de site que segue padrões.

O Henrique falou muito sobre o assunto no [post][1], mas, se você quiser entender mais sobre o assunto, leia alguns artigos publicados aqui mesmo no Tableless:

  *  [Aplicações comem conteúdos. Só os bem tratados][4]
  * [Semântica é que manda][3]
  * [A Web Semântica][5]
  * [Lições sobre Semântica #1][6]
  * [Lições sobre Semântica #2][7]

 [1]: http://www.revolucao.etc.br/archives/tableless-vs-web-standards/
 [2]: http://www.google.com.br/url?sa=t&ct=res&cd=1&url=http%3A%2F%2Fsomerandomdude.net%2Fprojects%2Fwebdev%2Fdivless%2F&ei=qkvJRJmfBby4auvdiNIM&sig2=3qylQ-STKkAeV06n6JS2FA
 [3]: http://tableless.com.br/a-semantica-e-que-manda
 [4]: http://tableless.com.br/aplicacoes-comem-conteudo
 [5]: http://tableless.com.br/aprenda/a-web-semantica/
 [6]: http://tableless.com.br/licoes_sobre_semantica_1
 [7]: http://tableless.com.br/licoes_sobre_semantica_2