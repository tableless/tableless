---
title: Comprei um Chromebook. E agora?
author: Marcelo Matzembacher
type: post
date: 2015-04-28
excerpt: Saiba, basicamente, como é um ambiente de desenvolvimento em um Chromebook. Levantei até um Wordpress. ;-)
url: /comprei-um-chromebook-e-agora/
categories:
  - Código
  - Tecnologia e Tendências
tags:
  - caret
  - chromebook
  - cloud9
  - codeanywhere
  - sublime text

---
Estamos em 2015, ano do futuro, do design responsivo e das aplicações na nuvem. Sério cara, ler essa frase em voz alta chega a arrepiar os cabelinhos do braço direito. Os hackers estão cada vez mais loucos, o Google está cada dia mais rico e o número de desenvolvedores web não para de crescer em todo o mundo. Somos muitos fazendo a mesma coisa, ou quase isso. Com toda a demanda de profissionais aptos a desenvolver códigos limpos, comentados e bem estruturados, as empresas investem uma boa parte dos seus recursos em hardware. Hoje se você vai num evento de JavaScript, por exemplo, pro lado que você olhar tem alguém com o Mac na mão, um Sublime Text aberto, um terminal rodando trocentas aplicações, Photoshop, Phonegap, Github, PageSpeed, Safari, Chrome, Firefox, Opera sem falar no tweetdeck, gmail e mais umas 250 abas abertas no navegador. É muita coisa rodando ao mesmo tempo!

Comprei um <a href="https://www.google.com/chromebook/" target="_blank">Chromebook</a>. E agora?

Como fica a vida de um desenvolver sem todos os recursos que um Mac oferece? Como você vai fazer para dar suporte a uma aplicação que usa Sass, tem o Grunt rodando, tem um time de mais 10 programadores todos dando suporte a mesma aplicação?

O primeiro pensamento que vem a cabeça é: &#8211; Cara, não tem como.

Destas linhas em diante eu vou contar uma história de superação, de conquista, de coragem e determinação de um Chromebook na tentativa de conseguir a vaga de emprego como Hardware Oficial de Desenvolvimento. Ou HOD para os mais íntimos.

O Chromebook, para quem ainda não conhece é um notebook que roda o sistema operacional da Google, o Chrome OS. Ele é baseado em Linux, utiliza as extensões de browser criadas para o Chrome como seus softwares principais e não tem como você instalar por exemplo, o Sublime Text.  Falando de um jeito menos amoroso: Ele não tem windows. Não tem como você instalar um programa nele. Você não tem espaço em disco para armazenamento. Um Chromebook vem como 16gb SSD e o modelo que eu tenho vem com uma tela de 11 polegadas. Pensando assim a primeira vontade que dá é a de desistir e fazer um empréstimo no banco para comprar uma máquina com um hardware mais forte. Calma que nem tudo está perdido. Lembram quando eu falei sobre as empresas investirem boa parte dos seus recursos em hardware? Essa foi a deixa para neste ponto do post eu dizer: tem como gastar menos com hardware e fazer mais. Existem excelentes soluções na nuvem que oferecem além dos recursos que você precisa para desenvolver suas aplicações web. Continue a leitura que você vai entender o que eu estou dizendo.

Levando em consideração que você já possui algum conhecimento em desenvolvimento web, eu quero compartilhar com vocês a minha experiência como desenvolvedor front-end utilizando um Chromebook. Abaixo eu vou apresentar algumas soluções que eu encontrei para usar o meu Chromebook como HOD e desenvolver aplicações usando HTML, CSS e JavaScript usando o Sublime Text e acessando todos os recursos de um servidor.

Um exemplo bem legal é o **<a href="http://thomaswilburn.net/caret/" target="_blank">Caret</a>**, editor de códigos bem simples porém muito funcional. O Caret é aquele tipo de editor honesto, que não oferece muita perfumaria e faz exatamente o que se propõe a fazer. Abaixo eu mostro uma imagem onde eu só abri ele e colei um JavaScript do Google Maps. Você pode ver que o Caret já reconhece o tipo de código como sendo JavaScript. Como o Chrome OS é um sistema baseado em cloud, se por acaso você estiver em um ambiente off-line (e eu espero que isso nunca aconteça) ainda assim é possível escrever as suas aplicações web, criar exemplos ou até mesmo melhorar os seus estudos.

[<img class="alignnone size-full wp-image-48364" src="http://tableless.com.br/uploads/2015/04/Screenshot-2015-04-18-at-16.06.24.png" alt="Screenshot 2015-04-18 at 16.06.24" width="1366" height="768" />][1]

Existem também diversas IDEs em Cloud que oferecem excelentes recursos para quem é desenvolvedor. Uma delas é o **Codeanywhere**.

O Codeanywhere já vem com o Sublime Text incorporado. com o Emmet já funcionando, e todos os recursos de escrita de código que você precisa diretamente dentro do seu navegador. Com o CA você consegue acessar facilmente seus repositórios no Github ou no Bitbucket, além de startar rapidamente um ambiente de desenvolvimento para HTML5, C++, PHP e muitos outros conforme da pra ver na imagem abaixo.

[<img class="alignnone size-full wp-image-48365" src="http://tableless.com.br/uploads/2015/04/Screenshot-2015-04-18-at-15.55.15.png" alt="Screenshot 2015-04-18 at 15.55.15" width="1366" height="768" />][2]

Mas se você está trabalhando num projeto com uma complexidade maior, que exige mais recursos, existe uma outra ferramenta que oferece tudo o que você vai precisar para desenvolver qualquer tipo de aplicação web.

Eu estou falando do <a href="https://c9.io/" target="_blank"><strong>Cloud 9</strong></a>.

Sem a menor sombra de dúvidas essa é hoje a melhor IDE para desenvolvimento web baseada na nuvem e que ainda permite que você utilize uma conta gratuita com 1gb de espaço para armazenamento e 512mb de RAM. Para você ter uma ideia, o Cloud 9 entrega para você um servidor Ubuntu, onde é possível usar todos os recursos de um server Linux e através do terminal dar um npm install &#8230;

O _C9_ oferece recursos para quem desenvolve em HTML5, CSS3, JavaScript, Ruby, Phyton, PHP, CoffeeScript e Node.js, além de permitir que você configure as suas variáveis de ambiente. Se no editor de códigos que você utiliza hoje você personalizou teclas de atalho para facilitar o seu dia a dia, você pode simplesmente importar o arquivo com o mapa dos atalhos e utilizar no Cloud 9. É tudo em JSON. Ele também possui um editor rápido de imagens, que permite cortar, girar e redimensionar diretamente no browser.

[<img class="alignnone size-full wp-image-48368" src="http://tableless.com.br/uploads/2015/04/Screenshot-2015-04-19-at-14.17.22.png" alt="Screenshot 2015-04-19 at 14.17.22" width="1365" height="704" />][3]

&nbsp;

Olhando a raiz de arquivos dá pra ver que no meu ambiente de desenvolvimento eu startei um wordpress. Vai dizer que não é uma interface linda, né? E isso tudo rodando dentro do teu browser 🙂

Vamos pensar assim: Uma solução em cloud que permite que o meu ambiente de desenvolvimento esteja sempre ao meu alcance, não importa aonde eu esteja e sem que eu precise carregar junto comigo um notebook. Tudo o que eu preciso é de um browser e uma conexão com a internet.

Continuando as experiências &#8230;

Veja que dentro do diretório ceva tem um outro diretório que é chamado de ruivo (no caso sou eu). Óbvio que isso é mais um teste para mostrar o que você pode fazer com essa ferramenta em cloud. Vamos ver como ficou o meu ambiente de produção.

O serviço que eu dei start quando criei a minha conta (wordpress) <a href="http://ceva-realruivo.c9.io/" target="_blank">pode ser acessado por aqui</a>.

Esse outro diretório chamado de ruivo (no caso eu de novo) tem uma estrutura em HTML, CSS e JS que eu fiz apenas para testar e <a href="http://ceva-realruivo.c9.io/ruivo/" target="_blank">pode ser acessada por aqui</a>.

Todo o conteúdo disponível nesses links está partindo de uma ferramenta que eu rodo pelo browser. É grátis! Você pode usar como ambiente de produção e permitir ao seu cliente, por exemplo, acompanhar em tempo real o andamento dos processos através da URL gerada pelo próprio Cloud 9.

Tem muito recurso disponível para quem é desenvolvedor e precisa de um ambiente de produção sempre ao alcance dos dedos. No Chromebook essas são algumas soluções de baixo custo que eu encontrei. E você quer mais motivos para comemorar? Por ser um sistema Google você tem todos os recursos da Chrome Developer Tools para testar os seus códigos. Você ainda pode usar o acesso remoto do Chrome para trabalhar remotamente, ou simplesmente colaborar no projeto de alguém.

[<img class="alignnone size-full wp-image-48370" src="http://tableless.com.br/uploads/2015/04/Screenshot-2015-04-18-at-16.28.22.png" alt="Screenshot 2015-04-18 at 16.28.22" width="1365" height="693" />][4]

&nbsp;

É muito fácil colaborar em códigos de terceiros, desenvolver aplicativos, clonar frameworks para agilizar processos. Desenvolver para a web deixou de ser um processo engessado há muito tempo. O simples fato de utilizar um Chromebook para trabalhar, faz você pensar de um modo diferente, agir de maneiras diferentes e desenvolver em novos e incríveis ambientes.

Qual criança nunca viu formas de desenhos estranhos numa nuvem?

Até a próxima.

&nbsp;

 [1]: http://tableless.com.br/uploads/2015/04/Screenshot-2015-04-18-at-16.06.24.png
 [2]: http://tableless.com.br/uploads/2015/04/Screenshot-2015-04-18-at-15.55.15.png
 [3]: http://tableless.com.br/uploads/2015/04/Screenshot-2015-04-19-at-14.17.22.png
 [4]: http://tableless.com.br/uploads/2015/04/Screenshot-2015-04-18-at-16.28.22.png