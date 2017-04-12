---
title: Mozilla libera primeira compilação do Servo, o seu motor de renderização
author: tableless
type: post
date: 2016-07-03
url: /mozilla-libera-primeira-compilacao-do-servo-o-seu-motor-de-renderizacao/
titulo_personalizado:
  - 'Conheça o novo motor de renderização da <strong>Mozilla</strong>'
categories:
  - Destaques
  - Notícias
tags:
  - firefox
  - mozilla

---
A [lançou][1] a primeira compilação de [Servo][2], seu novo engine. Esta é a primeira demonstração que Jack Moffitt, líder do projeto na Mozilla, descreveu como &#8220;um mecanismo de navegação de última geração com foco no desempenho e robustez.&#8221;

Pacotes para o MacOS e Linux estão disponíveis para download aqui: [Servo Developer Preview downloads][3]. A Mozilla promete que os pacotes para Windows e Android estarão disponíveis &#8220;em breve&#8221; e você pode verificar todo o código fonte no [GitHub][4]. Viu por que eu gosto da Mozilla?

Para tentar facilitar a interação, a Mozilla fez este novo motor com uma interface totalmente HTML. Ele ainda não está totalmente compatível (tentei escrever este post, usando WordPress, pelo Servo, mas as telas ficam &#8220;meio&#8221; quebradas). A interface, por enquanto, está totalmente pelada. Não tem abas visíveis, não tem barra de endereço, não há sidebar, rodapé ou algo assim.

Moffitt disse que esta interface é &#8220;inteiramente escrita em HTML, CSS e JavaScript&#8221; e que &#8220;inclui muitas animações e interações ricas que você encontraria em aplicações nativas, mas que nem sempre funcionam bem em navegadores atuais.&#8221;

<span class="embed-youtube" style="text-align:center; display: block;"></p> 

<p>
</p>

<p>
  </span>
</p>

<p>
  Em abril de 2013, a Mozilla e a Samsung anunciaram planos para desenvolver um engine da &#8220;próxima geração&#8221; usando a linguagem de programação <a href="https://www.rust-lang.org/">Rust</a>. Eles queriam reconstruir o navegador a partir do zero em hardware moderno, ignorando velhos pressupostos que tiveram que ser feitas antes multicore e hardware paralelo. O objetivo final na época era trazer a tecnologia para Android e ARM, mas que evoluiu desde então para um motor que está sendo desenvolvido para Windows, Mac OS X, Linux e Android. Como Moffitt falou antes, &#8220;Servo re-imagina a arquitetura do navegador no mercado moderna de computadores multi-core, GPUs e linguagens de programação mais seguras.&#8221;
</p>

<p>
  Ainda assim, esta é apenas uma demo técnica destina-se a dar aos desenvolvedores uma chance de experimentar o Servo. Eventualmente, a Mozilla espera que o motor Servo &#8220;irá definir um novo padrão para de desempenho para engine web&#8221;.
</p>

<p>
  Desde 2014 (sim, faz tempo) o <a href="https://blog.mozilla.org/research/2014/04/17/another-big-milestone-for-servo-acid2/">motor Servo já passa no teste Acid2</a>.
</p>

<p>
  Eu tenho dúvidas, mas torço muito pela Mozilla. Meu browser principal é o Firefox e quero muito continuar contando com a privacidade e as facilidades que a Mozilla oferece. Mesmo assim, fico em dúvida sobre a performance do browser por conta da construção em JS e CSS. O <a href="http://tableless.com.br/atom-o-novo-editor-github/">Atom</a>, editor de texto do GitHub, é feito usando JS, e é lerdo pra caramba. Mesma coisa para o <a href="http://tableless.com.br/o-editor-de-textos-open-source-da-adobe-o-brackets/">Brackets da Adobe</a> que é uma carroça. Vamos ver como ele vai se sair.
</p>

<p>
  <small><a href="http://venturebeat.com/2016/07/01/mozilla-releases-first-nightly-build-of-servo-its-next-generation-browser-engine/">fonte: VentureBeat</a></strong></p>

 [1]: https://blog.servo.org/2016/06/30/servo-nightlies/
 [2]: https://servo.org/
 [3]: https://servo-builds.s3.amazonaws.com/index.html
 [4]: https://github.com/servo/servo/