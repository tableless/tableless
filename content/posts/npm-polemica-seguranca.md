---
title: 'NPM e a polêmica de segurança'
authors: Diego Eis
type: post
date: 2018-01-07
image: https://i.imgur.com/pIfQLqG.jpg
excerpt: 'A polêmica sobre a falta de segurança em códigos de terceiros'
categories:
  - Notícias
  - JavaScript
  - Técnicas e Práticas
  - Tecnologia e Tendências
  - Mercado e Comportamento
tags:
  - noticias
  - javascript
---

Quando estamos desenvolvendo um projeto, nós podemos ganhar um tempo não tendo que reinventar a roda, principalmente quando o assunto é implementar algo que alguém no mundo já deve ter feito. Logo, o time começa a procurar algum código pronto de alguém que já resolveu o mesmo problema que você. 

Isso acontece muito em sites em Wordpress: sempre há um plugin que resolve o seu problema. Geralmente os desenvolvedores de sites em Wordpress não pensam duas vezes em usar os plugins disponibilizados pela comunidade. Aí é que entra o problema: o uso indiscriminado de plugins prejudica muito a segurança do sistema, abrindo brechas de segurança.

Um camarada quis fazer um teste para ver até onde ele conseguiria chegar. Então, ele criou um código que captura da página os dados de todos os forms da página, joga num cookie e envia o payload para um servidor dele. O problema é: como ele vai colocar isso no maior números e sites? Invadir servidores está fora de coditação, logo, ele decidiu que faria isso colocando seu código no código dos outros. Então ele começou a contribuir enviando Pull Requests para alguns projetos open source que estavam disponíveis no NPM. 

Em pouco tempo alguns projetos aceitaram seus PRs, adicionando o código como dependência. Assim, projetos que adicionavam determinados pacotes do NPM, que tinham esse projeto rodando como dependência, estavam rodando código malicioso que roubava dados dos usuários, inclusive dados de senha e cartões de crédito.

> I’m now getting about 120,000 downloads a month, and I’m proud to announce, my nasty code is executing daily on thousands of sites, including a handful of Alexa-top-1000 sites, sending me torrents of usernames, passwords and credit card details.

Você pode [ver toda a história aqui](https://hackernoon.com/im-harvesting-credit-card-numbers-and-passwords-from-your-site-here-s-how-9a8cb347c5b5).

Felizmente a história é mentira. O cara não fez realmente um pacote do NPM que rouba as informações das pessoas, mas é importante ter um alerta desse por várias razões, o mínimo:

1. Não coloque qualquer dependência no seu projeto. O time precisa se perguntar sempre se a inserção daquele pluginzinho vai salvar a vida deles ou se com um ou dias de trabalho eles não conseguem resolver o problema com uma solução mais personalizada e provavelmente usando menos código.
1. Pesquise sobre a dependência. Saiba se é popular no mercado, se há atualizações recentes, se houve problemas de segurança, processo de manutenção e etc. Sempre que você usa uma dependencia você está dando uma parte do seu projeto para outra pessoa cuidar. 
1. Se você tem um projeto open source que é usado em vários outros projetos, tenha um processo sério de code review.

É sempre bom lembrar [daquele caso do cara que quebrou](https://qz.com/646467/how-one-programmer-broke-the-internet-by-deleting-a-tiny-piece-of-code/) o mundo deletando um pedacinho de código.

O Jose Aguinanga [escreveu um artigo bem legal falando sobre como é aprender JS em 2016](https://hackernoon.com/how-it-feels-to-learn-javascript-in-2016-d3a717dd577f). Estamos em 2018 e quase nada mudou. Eu sei que o artigo fala muito sobre o ambiente de desenvolvimento JS que ficou bastante complexo nos últimos anos, mas entenda: se seu time tentar manter o projeto o mais simples possível, vocês terão um projeto mais saudável. Comece adicionando as complexidades de forma progressiva, se o projeto realmente pedir. Você não precisa começar o projeto com toda a stack ReactJS (ou qualquer outro framework, biblioteca, plugins etc) instalada. Comece simples e tente se manter simples o maior tempo possível. É bom ter um balanceamento entre manter o que é realmente necessário e o "quero usar porque é mó legal".
