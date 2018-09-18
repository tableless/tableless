---
title: Email Marketing – O Inferno – Parte 1
authors: Diego Eis
type: post
date: 2015-04-06
excerpt: Um overview sobre a construção de Email Marketing.
url: /email-marketing-o-inferno-parte-1/
categories:
  - O Básico
  - Técnicas e Práticas
tags:
  - email
  - email marketing
  - tabelas
  - tables

---
Esqueça tudo o que você sabe sobre CSS 3, HTML 5, JavaScript e qualquer outra nova novidade que você tenha visto nos últimos 10 anos. Para fazer uma newsletter você não vai usar nada disso.

Criar email marketing é chato. Não é fácil e provavelmente não vai ficar do jeito que você quer na primeira ou na segunda ou na terceira vez. Se você reclama do Internet Explorer por qualquer motivo, você ainda não teve que lidar com os clientes de email. É um mundo totalmente diferente do que conhecemos e estamos acostumados.

Eu sei que você gostaria que eu estivesse exagerando, mas não estou. Cada cliente de email tem suas restrições de segurança e tem seu suporte específico aos padrões web. Clientes de email online, como o Gmail tem preocupações totalmente diferentes que um cliente nativo como o Outlook.

Quando digo que você precisa voltar aos velhos tempos, eu não estou brincando. O que funciona perfeitamente em todos os clientes de email são as tabelas. São elas que irão estruturar seu layout. Nada de float. Float não funciona no Outlook. Nada de usar background-image, ele não funciona no Outlook também. E se você já está achando que o Outlook é o problema, espere até saber que o Gmail simplesmente remove qualquer tag `<style>` que estiver no documento e só aceita estilos inline, com o atributo style direto na tag. Nesse cenário, não tem quem é pior ou melhor, só tem o pior.

Com as tabelas, você poderá usar a propriedades font e text, com todos os seus respectivos valores. Logo, você já consegue formatar a tipografia do seu email, contanto que use apenas fonts do sistema, por que a propriedades font-face funciona apenas em aparelhos que rodam iOS e no Apple Mail.

E os seletores do CSS? Sem seletores a gente não consegue fazer muita coisa, né? Pois é... Vamos continuar sem fazer muita coisa. O selector mais básico, que chamamos de "selector encadeado", feito assim: "div p", pode não funcionar no Gmail. Em todos os outros clientes este seletor funciona perfeitamente.

A propriedade width funciona em tudo. Height só não funciona no Outlook 2007&#47;2010 e 2013. Já o padding e margin, podem ser usadas à vontade. Contanto que sejam em tabelas, porque em divs não vai funcionar no Outlook.

Perceba que as principais propriedades do CSS, as que usamos todos os dias não são aceitas perfeitamente nos clientes de email conhecidos. Na verdade até podem, mas você vai precisar abrir mão de algum cliente de email.

De acordo com o a Litmus, que é um serviço para testar email marketing e websites e diversos browsers, o cliente de email do iPhone é o mais popular. Outlook vem em segundo lugar. Depois vem o cliente de email do Android, seguido pelo do iPad. Aí vem o cliente da Apple, o Apple Mail, seguido do Yahoo! Mail e Gmail. [Você pode ver os números aqui][1].

Se quiser saber também quais propriedades do CSS funcionam, [o Campaign Monitor mantém uma tabela, sempre atualizada][2].

Lembre-se: neste ambiente incerto dos emails, teste exaustivamente. Não acredite apenas em serviços online para testar seus emails. Envie emails para você mesmo, teste pessoalmente em todos os clientes de email que puder. É a melhor forma para você obter um resultado decente.

 [1]: https://emailclientmarketshare.com
 [2]: https://www.campaignmonitor.com/css/