---
title: Você conhece AMP?
author: Thaiana Poplade
type: post
date: 2016-07-13
excerpt: 'O projeto AMP - Accelerated Mobile Pages, é uma iniciativa Google em conjunto com alguns publishers como Chartbeat, Vox, Wordpress.com, Twitter, The Washington Post, UOL, etc; de trabalhar uma estrutura de rápido carregamento de conteúdos em Smartphones.'
url: /voce-conhece-amp/
titulo_personalizado:
  - 'Você conhece <strong>AMP?</strong>'
categories:
  - CMS
  - CSS
  - Destaques
  - Mobile
  - Técnicas e Práticas
tags:
  - amp
  - Conteúdo
  - Wordpress

---
O projeto <a href="https://www.ampproject.org/" target="_blank">AMP &#8211; Accelerated Mobile Pages</a>, é uma iniciativa Google em conjunto com alguns publishers como Chartbeat, Vox, WordPress.com, Twitter, The Washington Post, UOL, etc; de trabalhar uma estrutura de rápido carregamento de conteúdos em Smartphones. Afinal, apesar da navegação mobile crescer dia-a-dia as soluções para uma entrega com mais velocidade ainda andam a passos lentos. Nossa conexão de internet em celulares ainda não tem a devida capacidade e nos obriga a, em alguns casos, buscar tamanha versatilidade em nosso desenvolvimento web a ponto de, em um site responsivo, ter que oferecer uma &#8220;cidade completa e bem elaborada&#8221; em sua versão desktop e uma &#8220;ilha&#8221; em sua versão mobile para não correr o risco de prejudicar nosso usuário.

Em busca de reduzir os índices de frustração e oferecer uma solução mais rápida essa iniciativa tomou forma e o projeto vem sendo adotado e atualizado constantemente por outros publishers pelo mundo. Aqui você pode acompanhar quem esta aplicando versões AMP em seus CMS’s: <a href="https://www.ampproject.org/who/" target="_blank">https://www.ampproject.org/who/</a>

OK! Tudo bacana, mas o que tem a ver com Front/Dev? Eu te respondo: tudo!

O formato AMP é totalmente focado em performance e para esse resultado a estrutura exige mudanças na entrega HTML, JS e CSS das páginas web que desenvolvemos tradicionalmente. Um conteúdo deve ser estruturado de maneira que tags AMP sejam lidas e artifícios JS sejam aplicados apenas em caso de necessidade real.
  
<span style="line-height: 1.5">Tecnicamente não é difícil transformar seu conteúdo em formato AMP, mas certamente, será trabalhoso caso sua estrutura seja robusta ou antiga ou os dois.</p> 

<h2>
  Entendendo um pouco o AMP
</h2>

<p>
  A estrutura é simplificada: em geral, boa parte das tags devem conter o prefixo <strong>&#8220;amp-&#8220;&#8221;</strong> para serem lidas. Esse é o começo dos começos:
</p>

<pre class="lang-html">&lt;iframe src="" /&gt;</pre>

<p>
  em AMP
</p>

<pre class="lang-html">&lt;amp-iframe src="" /&gt;</pre>

<p>
  O detalhe mais trabalhoso dessa modificação fica por conta das especificações que esses novos prefixos exigem. No exemplo acima, se nosso conteúdo for um trecho hospedado em um protocolo HTTP, provavelmente não funcionaria.
</p>

<p>
  <strong>Páginas AMP exigem que os conteúdos para iframes sejam HTTPs.</strong>
</p>

<p>
  Além deste ponto, as imagens devem conter medidas de altura e largura, assim como qualquer outro bloco que contém algo, como trechos do Twitter ou Facebook.
</p>

<p>
  O JS, da forma que utilizamos também é excluído. Aquele <i>pluggin </i>de galeria ou aquele <i>slider </i>em Jquery, possivelmente não vão funcionar e aí você deve estar pensando:
</p>

<p>
  <img class="alignnone" src="https://media.giphy.com/media/fd1TSJqq3b4GI/giphy.gif" width="600" height="338" />
</p>

<p>
  Calma!<br /> Eu também reagi assim no primeiro momento mas, Google &#8220;é pai e não é padastro&#8221;&#8221; e criou uma biblioteca de alternativas para substituirmos o tradicional pela versão AMP.
</p>

<p>
  Você pode dar uma conferida aqui: <a href="https://www.ampproject.org/docs/reference/extended.html" target="_blank"><span style="line-height: 1.5">https://www.ampproject.org/docs/reference/extended.html</a></p> 
  
  <h2>
    E como eu sei que meu formato AMP esta funcionando?
  </h2>
  
  <p>
    Tem 2 maneiras de verificar se seu código esta de acordo com a validação AMP.
  </p>
  
  <p>
    A primeira delas é através das ferramentas de Web Developer (F12) dos navegadores no item &#8220;Console&#8221;&#8221;. Lá você deve ser avisado dos erros encontrados.
  </p>
  
  <p>
    <img class="alignnone size-full wp-image-55207" src="http://tableless.com.br/uploads/2016/07/console.jpg" alt="console" width="466" height="337" />
  </p>
  
  <p>
    Para Chrome tem uma extensão que fica no cantinho de sua tela avisando o número de erros e &#8220;warnings&#8221;&#8221; que ele encontrou para ajustar:
  </p>
  
  <p>
    <img class="alignnone size-full wp-image-55208" src="http://tableless.com.br/uploads/2016/07/extensaoamp.jpg" alt="extensaoamp" width="50" height="38" />
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p>
    AMP válido e publicado, teste a busca de seus conteúdo no Google e veja como ele se apresenta. Dever algo desta forma:
  </p>
  
  <p>
    <img class="alignnone wp-image-55209" src="http://tableless.com.br/uploads/2016/07/Google-AMP-news.jpg" alt="Google-AMP-news" width="800" height="516" />
  </p>
  
  <p>
    A documentação completa você pode ler aqui:
  </p>
  
  <p>
    <a href="https://www.ampproject.org/docs/get_started/about-amp.html" target="_blank">https://www.ampproject.org/docs/get_started/about-amp.html</a>
  </p>
  
  <p>
    Eles explicam tudo diretinho e você tem a chance de colaborar para uma entrega mais veloz de conteúdo na internet mobile.
  </p>
  
  <p>
    Até a próxima! 😉
  </p>