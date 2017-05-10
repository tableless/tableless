---
title: Passwords em Mobiles
author: Diego Eis
type: post
date: 2012-11-11
excerpt: Melhorando a experiência do usuário não mascarando o password em mobiles.
url: /passwords-em-mobiles/
tweetbackscheck:
  - 1356437173
shorturls:
  - 'a:3:{s:9:"permalink";s:31:"http://tableless.com.br/?p=7214";s:7:"tinyurl";s:26:"http://tinyurl.com/bbblb93";s:4:"isgd";s:19:"http://is.gd/mNcE1U";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 923713978
categories:
  - Acessibilidade
  - Mobile
  - Técnicas e Práticas
  - UX
tags:
  - 2012
  - desenvolvimento web
  - mobiles
  - tableless

---
Estava conversando outro dia com um pessoal sobre melhores práticas em sites/sistemas mobile. Um dos pontos foi a forma que tratamos senhas em mobiles. Em desktops e outros terminais (como caixas eletrônicos) é necessário que sua senha seja escondida conforme você a digita. Isso é bom por que pode ter algum engraçadinho perto de você, olhando a sua tela. Com mobile é um pouco diferente. Normalmente você está com o dispositivo na sua mão, utilizando-o perto do seu corpo, bem difícil de alguém tentar ficar bisbilhotando, e se estiver é fácil de esconder. 

Tendo esse cenário em mente, vamos pensar em outro ponto para discutir: é um saco digitar senhas com teclados pequenos e touchs. Quem nunca ao errar a digitação no meio da senha, apaga todo o campo e começa a digitar novamente desde o começo?

Quando você digita a sua senha e aparecem aqueles asteríscos, eles mais atrapalham você do que ajudam na sua segurança. A forma com que tratamos senhas faz com que o usuário escolha senhas simples de serem escritas e na sua maioria das vezes fáceis de descobrir. E não é culpa dos usuários: se você escolhe uma senha pequena e simples, você erra menos ao digitar.

> “Masking passwords doesn&#8217;t even increase security, but it does cost you business due to login failures.” &#8230;and it&#8217;s worse on mobile. -Nielsen Norman Group

O [LukeW escreveu um texto sobre isso muito completo][1]. Recomendo sua leitura.

No Mac, por exemplo, há sempre aquele checkbox de mostrar senhas.

![][2]

Em mobile geralmente eles te mostram o caracteres que foi digitado por último por alguns instantes, assim se você for rápido e tiver dedos grandes, consegue ver se digitou a letra correta antes do caractere se transformar no • .

Há custos ao mascarar as senhas, tanto em mobiles quanto em desktops. Lembre-se que a internet está chegando a pessoas que não tenta experiência computacional. Mascarar as senhas trazem alguns problemas de usabilidade:

  1. Usuários cometem mais erros quando eles não enxergam o que estão digitando. Obviamente.
  2. Os usuários mais inexperientes, quando ficam incertos sobre digitar corretamente a senha, eles escolhem criar senhas mais simples ou fazem um simples copy/paste de sua senha de um arquivo de texto.

São dois problemas de usabilidade que viram problemas de segurança! Quantas vezes você não ouviu histórias de pessoas que guardam suas senhas escritas em folhas de papel? Ou guardam tudo no email?

Uma prática interessante é inserir um checkbox ou alguma outra forma para que o usuário mostre a senha na hora do login. Isso facilitaria a digitação do usuário, não haveria tantas ocorrências de bloqueio de senha, lembrete de senha etc e o usuário não ficaria sem paciência ao utilizar seu sistema&#8230;

![][3]

Lembre-se que o usuário está competindo a atenção com outras coisas ao utilizar seu sistema mobile. Ele pode estar em pé, no ônibus, chacoalhando o tempo todo. Ter um botãozinho que o ajude a digitar a senha sem tantos problemas é interessante. A experiência melhora e usuário fica feliz.

Leia mais sobre o assunto:

  * [Password masking, and the difference between usability and user experience][4]
  * [Stop Password Masking][5]
  * [Fundamental Guidelines for Web Usability][6]
  * [Mobile Design Details: Hide/Show Passwords][1]

 [1]: http://www.lukew.com/ff/entry.asp?1653
 [2]: http://tableless.com.br/uploads/2012/11/Screen-Shot-2012-11-11-at-9.25.25-PM.png
 [3]: http://tableless.com.br/uploads/2012/11/hidepass4.png
 [4]: http://danamckay.wordpress.com/2010/01/22/password-masking-and-the-difference-between-usability-and-user-experience/
 [5]: http://www.useit.com/alertbox/passwords.html
 [6]: http://www.nngroup.com/events/tutorials/usability.html