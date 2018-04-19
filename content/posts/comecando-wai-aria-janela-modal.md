---
title: Começando com WAI ARIA em uma janela modal
authors: Alura
type: post
sponsor: alura
publishdate: 2018-04-25
date: 2018-04-25
excerpt: Como melhorar a acessibilidade em modais.
image: https://i.imgur.com/Mlw5SRI.jpg
categories:
  - acessibilidade
  - wai-aria
  - html
  - publieditorial
---

Depois de fazer esse [post com dicas de acessibilidade](http://blog.caelum.com.br/melhorando-a-acessibilidade-em-suas-interfaces/), resolvi fazer mais este para que você conheça um pouco de um recurso muito interessante: a **WAI ARIA**. Vamos?

* * *

Um elemento visual que hora ou outra precisamos fazer em nossos projetos é aquela janelinha _modal_ ou _dialog_. Sabe? Aquela que aparece sempre para te <del>irritar</del> informar sobre algo importante ou confirmar alguma ação? Como essa da imagem abaixo: ![Exemplo de janela modal pedindo email](http://blog.caelum.com.br/wp-content/uploads/2042/04/exemplo-janela-modal-dialog.jpg) Como normalmente você faria essa janela? O novo elemento `<dialog>` pode ser uma boa, mas o [suporte atualmente ainda não é muito bom.](https://caniuse.com/#search=dialog). Poderíamos ir com uma singela `<div>`, como essa:

See the Pen [Modal 1.0](https://codepen.io/designernatan/pen/vRzLBr/) by Natan Souza ([@designernatan](https://codepen.io/designernatan)) on [CodePen](https://codepen.io).

Agora, como será que o usuário de leitor de tela ouviria isso? Para demonstrar isso sem que você tenha que baixar um desses softwares (o que recomendo, sua percepção como profissional e pessoa vai mudar bastante), dá uma olhada no GIF abaixo que mostra o exibidor de fala de um deles, o NVDA: ![Modal que nao avisa no NVDA que foi aberta](http://blog.caelum.com.br/wp-content/uploads/2018/04/modal-que-nao-parece-modal.gif) Sem aviso nenhum, o usuário se perderá quando essa janela surgir. Idealmente, o leitor de tela deveria informar que uma janela foi aberta. Como fazer isso? Podemos fazer uso de um recurso super bacana chamado WAI ARIA.

## WAI ARIA?

Pense na [WAI ARIA](https://www.w3.org/TR/aria-in-html/) como vários pacotes de expansão do <del>The Sims</del> HTML. Com ela podemos simplesmente colocar um atributo em um elemento e assim mudar totalmente seu valor semântico. Um botão poderia virar um link, um link poderia virar um título, e por aí vai. Inclusive em um futuro post mostrarei como deixar uma `<div>` com “cara” de checkbox. Para falarmos que a `<div>` que representa nossa modal é na verdade uma janela modal, devemos mudar a função que ela tem em nosso HTML, alterar seu papel, com o atributo `role`. Mas qual valor colocar? Dialog, modal, popup? Para isso que temos a [documentação da WAI ARIA](https://www.w3.org/TR/wai-aria-1.1/#usage_intro) e nela podemos ver que tem justamente o que precisamos: o valor “dialog”. Colocando o atributo `role=”dialog”` e chegamos nesse resultado:

See the Pen [Modal 1.2](https://codepen.io/designernatan/pen/MVqpzm/) by Natan Souza ([@designernatan](https://codepen.io/designernatan)) on [CodePen](https://codepen.io).

Agora veja como o NVDA interpreta isso: ![NVDA falando sobre uma janela de diálogo por conta do role=dialog](http://blog.caelum.com.br/wp-content/uploads/2018/04/nvda-modal-com-role.jpg)

## Só isso para uma modal acessível?

Não, mas é um começo! Alguns pontos interessantes para tomarmos cuidado quando fazemos uma modal:

*   Com a modal aberta, o foco nunca deve ir para os elementos do fundo;
*   Botão de fechar não pode falar apenas “X”, deveria falar “Fechar modal”;
*   Ao fechar, foco volto pro botão que abriu a modal;
*   Descrição sobre o que se trata a modal com o atributo [“aria-labelledby”](https://developer.mozilla.org/pt-BR/docs/Web/Accessibility/ARIA/ARIA_Techniques/Usando_o_atributo_aria-labelledby);
*   Cores com contraste decente ([ferramenta que ajuda nisso](https://contrastchecker.com/));
*   Informações textuais sempre bem escritas, sem figuras de linguagem (já viu a [série Atypical?](https://pt.wikipedia.org/wiki/Atypical)).

## Modal, dialog ou pop-up?

Também tinha essa dúvida! Fiz uma rápida enquete no meu Twitter, e apesar do correto ser o termo "dialog", galera aqui no BR fala "modal" mesmo:

> Como você chama aquela janelinha que surge no meio da tela em uns sites? RT para ajudar pls :)
> 
> — Natan Souza (@designernatan) [30 de janeiro de 2018](https://twitter.com/designernatan/status/958324690891821056?ref_src=twsrc%5Etfw)

## Resumo

Tente usar os elementos nativos do HTML5 que não tem muito erro. Se por algum motivo você não puder ou for algo que ainda não foi criado, use a WAI ARIA para te ajudar a deixar seu projeto um pouco mais acessível. Se tiver interesse em se aprofundar em acessibilidade, tanto na parte de design/layouts quanto na parte de front-end, recomendo a dar uma olhada nesse [post com dicas de acessibilidade](http://blog.caelum.com.br/melhorando-a-acessibilidade-em-suas-interfaces/) e nos meus [cursos de acessibilidade](https://www.alura.com.br/busca?query=acessibilidade) na Alura, em que mostro como deixar seu site mais inclusivo para todos.