---
title: Email bom é TXT
author: Elcio Ferreira
type: post
date: 2007-12-06
url: /email-bom-e-txt/
tweetbackscheck:
  - 1356379689
shorturls:
  - 'a:3:{s:9:"permalink";s:39:"http://tableless.com.br/email-bom-e-txt";s:7:"tinyurl";s:26:"http://tinyurl.com/3zyvngh";s:4:"isgd";s:19:"http://is.gd/dZbrbC";}'
twittercomments:
  - 'a:1:{i:19742181963071489;s:6:"136504";}'
tweetcount:
  - 1
dsq_thread_id: 503037773
categories:
  - Artigos
  - Técnicas e Práticas
tags:
  - CSS
  - desenvolvimento web
  - email
  - html
  - implementacao
  - txt
  - xhtml

---
Você é um sujeito antenado e sabe disso. Mas talvez seu chefe não saiba. Talvez seu cliente não saiba. (Talvez você mesmo não saiba.) Ou por qualquer outro motivo, você pode se ver obrigado a enviar uma newsletter em HTML. E agora, o que você faz? Chuta o pau da barraca, abre o Dreamwaver e prepara &#8220;aquele&#8221; layout?

Você ainda pode, mesmo enviando emails em HTML, se preocupar em tornar melhor a experiência de seu usuário. <!--more-->Vejamos:

1. Layout simples. Cada leitor de emails exibe de um jeito diferente. Webmails então, destróem qualquer layout. Muitos desabilitam seu CSS. Então, se preciso monte o layout com tabelas, não coloque DIVs flutuantes (layers), javascripts e outros bichos.

2. Ofereça o conteúdo em TXT. Não sei como o Outlook faz, mas a maioria dos mailers (e componentes de envio de email server-side) permite definir o conteúdo para HTML e para texto no mesmo email. Se alguém usa o Kmail (eu uso!), o webmail da Locaweb (também uso!), ou qualquer outro leitor de emails que não exiba HTML promiscuamente, vai ver o conteúdo TXT que você enviou. Se você não fizer isso o coitado vai ver código HTML listado na tela.3. Pense em quem vai ler offline. Coloque o CSS no corpo do email, não em um arquivo externo. Imagens, coloque no servidor pra deixar o email menor, mas coloque atributo ALT no seu HTML e cuide de que as imagens não sejam essenciais ao entendimento da mensagem. Muitos programas de email exibem HTML mas não exibem imagens dentro dele (meu Kmail está configurado pra isso.)

4. Nunca, nunca, nunca, em hipótese alguma, coloque javascript em sua newsletter. Você não faz a menor de idéia de como seu javascript vai se comportar no sistema do cliente. E alguns antivírus vão reclamar do seu email, causando uma má impressão em seus clientes.

5. Idem para Flash, Java, Shockwave, iPix, MP3, ActiveX.

6. Pense em contingência. Imagine que você prepara seu email com letras brancas sobre fundo preto. E o webmail, no intuito de preservar o layout deles, desabilita seu background.

Além disso, claro, não preciso dizer que newsletter de verdade é opt-in, que os emails que seus usuários enviarem clicando em &#8220;responder&#8221; na newsletter precisam ser lidos e respondidos e que se alguém pedir para não receber mais seus emails isso precisa acontecer imediatamente.