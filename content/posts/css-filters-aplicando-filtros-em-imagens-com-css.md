---
title: CSS Filters – Aplicando filtros em imagens com CSS
author: Diego Eis
type: post
date: 2014-07-10
excerpt: Veja como aplicar filtros em imagens e elementos apenas com CSS.
url: /css-filters-aplicando-filtros-em-imagens-com-css/
dsq_thread_id: 2825769516
categories:
  - CSS
  - Técnicas e Práticas
tags:
  - CSS
  - CSS3
  - filtro
  - w3c

---
A cada dia que passa o CSS tem virado de fato uma linguagem visual, para formatar como os elementos, imagens e qualquer outro tipo de informação aparece nos browsers, celulares e etc. Um bom exemplo disso são os CSS Filters, que permite aplicar filtros, antes vistos apenas em programas como Photoshop, diretamente no browser com CSS.

> A filter effect is a graphical operation that is applied to an element as it is drawn into the document. It is an image-based effect, in that it takes zero or more images as input, a number of parameters specific to the effect, and then produces an image as output.

A possibilidade de aplicar filtros com CSS já é possível desde algo em torno de 2011, mas apenas para o motor WebKit. Agora essa possibilidade se transformou de fato em [rascunho do W3C][1] para que um dia vire uma recomendação. O [suporte ainda não é muito bom][2], mas, dependendo do seu público, você já pode usar agora. 

A sintaxe é simples e bem fácil de entender:

<pre class="lang-css">seletor {
  filter: funcao(valor) | none
}
</pre>

Os valores possíveis por enquanto são:

  * blur()
  * brightness()
  * contrast()
  * drop-shadow()
  * grayscale()
  * sepia()
  * hue-rotate()
  * invert()
  * opacity()

A imagem abaixo já está com contrast() aplicado e passando o mouse, fica com efeito blur():
  


Você pode passar uma ou várias funções em uma mesma propriedade `filter`:

<pre class="lang-css">p {
  filter: blur(50px);
}

img {
  filter: blur(50px) contrast(5);
}
</pre>

Abaixo você pode ver alguns exemplos:
  


Existem algumas observações interessantes sobre a aplicação dos filtros. Por exemplo, se você quiser combinar os filtros sepia() e grayscale(), certifique-se de adicionar sepia() antes do grayscale(), caso contrário o resultado será apenas grayscale(). 

Você pode não entender o efeito de hue-rotate(), sugiro que [leia mais sobre HUE aqui][3]. Leia mais sobre [cores na web aqui][4].

 [1]: http://www.w3.org/TR/filter-effects/
 [2]: http://caniuse.com/#feat=css-filters
 [3]: http://en.wikipedia.org/wiki/Hue
 [4]: http://tableless.com.br/sobre-cor-e-webdesign/