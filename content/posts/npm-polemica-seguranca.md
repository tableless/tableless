---
title: 'NPM e a polêmica de segurança'
authors: Diego Eis
type: post
date: 2018-01-07
image: https://i.imgur.com/pIfQLqG.jpg
excerpt: 'A polêmica sobre a falta de segurança em códigos de terceiros'
categories:
  - Notícias
  - Javascript
  - Técnicas e Práticas
  - Tecnologia e Tendências
  - Mercado
tags:
  - noticias
  - javascript
---

Quando estamos desenvolvendo um projeto, nós podemos ganhar um tempo não tendo que reinventar a roda, principalmente quando o assunto é implementar algo que alguém no mundo já deve ter feito. Logo, o time começa a procurar algum código pronto de alguém que já resolveu o mesmo problema que você.

Isso acontece muito em sites em Wordpress: sempre há um plugin que resolve o seu problema. Geralmente os desenvolvedores de sites em Wordpress não pensam duas vezes em usar os plugins disponibilizados pela comunidade. Aí é que entra o problema: geralmente, na impetuosidade de resolver o problema, o time usa indiscriminadamente plugins e outras dependencias sem o mínimo de pesquisa, fragilizando muito a segurança do sistema e abrindo várias brechas por conta do código alheio.

Pensando nisso, um camarada resolveu fazer um teste para ver até onde ele conseguiria chegar. Então, ele criou um código que captura os dados de todos campos de uma página deem match com `input[type="password"]`, `name="cardnumber"`, `name="cvc"` e páginas que contenham palavras "**credit card**", "**checkout**", "**login**", "**password**" etc. Feito isso, ele começou a ouvir o evento disparado quando o usuário desse focus nesses campos, aí pegava os dados, jogava num cookie e enviava o payload para um servidor dele.

Com o código feito e funcionando, ele teria que "infectar" o máximo de sites que ele conseguisse. Mas isso é um problema. Como você pega um código malicioso e implementa nos sites alheios? Invadir servidores estava fora de cogitação… logo, ele teve uma ideia: ele começou a submeter Pull Requests, contribuindo para alguns projetos open source front-end que estavam disponíveis no NPM. Se esses caras aceitassem seu PR, o código seria inserido como dependência no pacote NPM e seria automaticamente instalado assim que os devs começassem a usar o pacote nos seus projetos.

Em pouco tempo alguns projetos aceitaram seus PRs. Assim, projetos que adicionavam determinados pacotes do NPM, que tinham esse projeto rodando como dependência, estavam rodando código malicioso que roubava dados sensíveis dos usuários.

> I’m now getting about 120,000 downloads a month, and I’m proud to announce, my nasty code is executing daily on thousands of sites, including a handful of Alexa-top-1000 sites, sending me torrents of usernames, passwords and credit card details.

Você pode [ver toda a história aqui](https://hackernoon.com/im-harvesting-credit-card-numbers-and-passwords-from-your-site-here-s-how-9a8cb347c5b5).

Felizmente a história é mentira. O cara não fez realmente um pacote do NPM que rouba as informações das pessoas, mas é importante ter um alerta desse por várias razões, o mínimo:

1. Sempre cogite não colocar uma dependência no projeto. O time precisa se perguntar sempre se a inserção daquele pluginzinho vai salvar a vida deles ou se com um ou dois dias de trabalho eles não conseguem resolver o problema com uma solução mais personalizada e provavelmente usando menos código.
1. Se vocês decidirem inserir alguma dependência, pesquise bastante sobre ela. Saiba se é popular no mercado, se há atualizações recentes, se houve problemas de segurança anteriormente, se há um ciclo de manutenção e principalmente quem tem contribuído para o projeto. Sempre que você usa uma dependência você está dando uma parte do seu projeto para outra pessoa cuidar e essa pessoa (ou grupo) pode não ter o mesmo apreço com o código que seu time tem.
1. Se você tem um projeto open source que é usado em vários outros projetos, tenha um processo sério de code review. Code Review não é só uma prática interna dos times, mas para qualquer projeto de desenvolvimento de software.

É sempre bom lembrar [daquele caso do cara que quebrou](https://qz.com/646467/how-one-programmer-broke-the-internet-by-deleting-a-tiny-piece-of-code/) o mundo deletando um pedacinho de código.

O Jose Aguinanga [escreveu um artigo bem legal falando sobre como é aprender JS em 2016](https://hackernoon.com/how-it-feels-to-learn-javascript-in-2016-d3a717dd577f). Estamos em 2018 e quase nada mudou. Eu sei que o artigo fala muito sobre o ambiente de desenvolvimento JS que ficou bastante complexo nos últimos anos, mas entenda: se seu time tentar manter o projeto o mais simples possível, vocês terão um projeto mais saudável. Comece adicionando as complexidades de forma progressiva, se o projeto realmente pedir. Você não precisa começar o projeto com toda a stack ReactJS (ou qualquer outro framework, biblioteca, plugins etc) instalada. Comece simples e tente se manter simples o maior tempo possível. É bom ter um balanceamento entre manter o que é realmente necessário e o "quero usar porque é mó legal".
