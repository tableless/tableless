---
title: 'Anotações de palestra: Além do que se vê – práticas com HTML e CSS'
author: Diego Eis
type: post
date: 2014-05-21
excerpt: Minhas anotações da palestra do Jean Carlo Emer sobre práticas e truques com HTML e CSS.
url: /anotacoes-da-palestra-jean-carlo-emer-16elw/
dsq_thread_id: 2702125206
categories:
  - Eventos e Workshops
  - Slides e Apresentações
tags:
  - anotacoes
  - palestras

---
Anotações da palestra do Jean Carlo Emer no evento 16 Encontro Locaweb de 2014 chamada **Além do que se vê &#8211; Práticas com HTML e CSS**.



## História

  * Com CSS conseguimos liberdade de estilo e construção para websites.
  * Em 1995 começamos a ter alguma interação. O termo Dynamic HTML foi cunhado nesse tempo, possibilitando o uso do Javascript para criar experiências mais ricas.
  * HTML é para conteúdo. Ele surgiu no reinado de conteúdo. CSS é para estilização e JS é para interatividade, comportamento.
  * Isso não é bem verdade. O HTML na versão 2 ganha a capacidade de interagir com os recursos representados.
  * Quando inserimos conteúdo via CSS usando :before e :after, já estamos modificando conteúdo retirando a responsabilidade que o HTML tinha para isso.
  * Temos todas as tecnologias, HTML, CSS, JS e DOM para controlar conteúdo, estilo, interatividade, acessibilidade, usabilidade e performance.
  * Cada uma das tecnologia tem aptidões diferentes, mas todas podem controlar partes das responsabilidade.

## HTML

  * A tag TITLE mantém um histórico de navegação legível par ao usuário. Ele não serve apenas para motores de busca ou para deixar o título bonito na janela.
  * Títulos com atributo ID são âncoras importantes para o conteúdo da página. Isso melhora a acessibilidade e a usabilidade da página.
  * Rótulos indicam o significado de porções de formulários e campos. Rótulos como legends, label e etc ajudam a dar mais informação sobre outras informações.
  * Placeholder não substitui o label, ele só ajuda o usuário a preencher o campo, dando dicas de quais informações podem ser inseridas no campo.
  * Legendas, como o figcaption, ajudam a aumentar a descrição de elementos gráficos e visuais.
  * Âncoras possibilitam navegar, explorar conteúdo, ir de um lugar para outro.
  * Botões te ajudam a fazer ações na própria página. Não devem ser usados para navegações. Isso é responsabilidade do link.

## CSS

  * Não use display: none; para sumir com legends, labels e etc. Leitores de tela não &#8220;enxergam&#8221; o elemento com display: none;
  * Em vez de usar display: none; prefira usar técnicas de offset. Por exemplo: use position: absolute; -99999em; para posicionar o elemento para fora da página.
  * Ocutar conteúdos: image replacement é um método para usar imagens quando ícones ou grafias por vezes cumprem melhor o papel que textos
  * [Uma outra técnica para fazer Image Replacement][1]
  * Gerar conteúdo via CSS ajuda na estilização de pequenos elementos
  * Insere o endereço dos links quando a página for impressa.

<pre class="lang-css">@media print {
  a[href]::after {
   cotent: " (" attr(href)")";
  }
}
</pre>

 [1]: http://nicolasgallagher.com/another-css-image-replacement-technique