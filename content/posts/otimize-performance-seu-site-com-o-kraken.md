---
title: Otimize a performance do seu site com o Kraken
author: FelipeMartinin
type: post
date: 2015-04-14
excerpt: Usando Kraken para otimizar suas imagens.
url: /otimize-performance-seu-site-com-o-kraken/
categories:
  - Artigos
  - Browsers
  - Técnicas e Práticas
tags:
  - Browsers
  - imagens
  - otimização
  - otimização de imagens
  - performance
  - Técnicas e Práticas

---
Quando o assunto é performance, você ainda pode ter muita dor de cabeça. É comum muitos sites e aplicações web terem a sua experiência deformada por problemas na performance. Há tempos procuramos métodos para otimizar nossos sites, tais como concatenação de arquivos para diminuir as requisições HTTP, minificar CSS, JavaScript e até mesmo HTML. Entre várias outras técnicas. Porém, cada vez mais essas técnicas não conseguem acompanhar os novos recursos que sempre estão surgindo para deixar nossos sites cada vez mais impressionantes. E pesados.

Quando o assunto é front-end, um dos grandes vilões para uma boa performance ainda são as imagens, já que a maior parte do tráfego de seu site vem delas. Não é difícil ver uma única imagem com o tamanho superior à todo código que é carregado em uma determinada página. Tentamos contornar esse dilema usando SVG nas iconografias, fazer gradientes e elementos de interface complexos usando apenas CSS. Mas isso ainda não nos deixam isentos do uso de imagens em jpeg, gif e png, e do peso delas.

### Conheça o Kraken

Como é impossível ter um site sem imagens, o que podemos fazer é amenizar o impacto delas na performance. Então aí que eu lhes apresento o Kraken.

O Kraken é uma ferramenta poderosa que conta com um motor de compressão de imagens super eficiente. Eu por exemplo já tive imagens com 99% do seu tamanho reduzido. E o melhor de tudo, sem nenhum impacto na qualidade visual.

E é exatamente isso que o Kraken promete, e onde ele se destaca. Não uma mera diminuição no tamanho do arquivo, mas sim que isso aconteça garantindo que não haverá perdas na qualidade visual da imagem. Como no exemplo abaixo:

<div style="width: 766px" class="wp-caption alignnone">
  <img class="" src="http://s29.postimg.org/kh32i0mg7/kraken_before_and_after.jpg" alt="Kraken" width="756" height="205" />
  
  <p class="wp-caption-text">
    Kraken antes e depois
  </p>
</div>

### Minha experiência com o Kraken

Sempre usei o plugin imagemin do grunt. Mas nunca tive resultados expressivos. Até que, por recomendação de um amigo, eu conheci o Kraken e realmente fiquei impressionado com os seus resultados. Mas além de contar histórias, vou demonstrar o uso prático da aplicação.

No meu site pessoal, na página portfolio, há uma listagem dos meus projetos e suas respectivas capas. 90% dessa página é composta por imagens e notei que estava levando muito tempo para carregar por conta dessas imagens. Então eu testei otimizar cada uma delas para ver o resultado. Antes vale lembrar que eu fiz essas imagens pelo Photoshop, e elas foram salvas no formato png no modo smallest/slow, que garante uma compressão maior. Mas será que é o suficiente? Vamos ver logo abaixo:

<div style="width: 760px" class="wp-caption alignnone">
  <img class="" src="http://s12.postimg.org/j3s0bu43h/compress_o.png" alt="compressão" width="750" height="305" />
  
  <p class="wp-caption-text">
    compressão
  </p>
</div>

Nessa brincadeira, eu poupei 1.84MB de carregamento em minha página, isso remete a 85.39% a menos do tamanho total de todas as imagens juntas. É um ganho e tanto, não?

Agora vamos ver o impacto disso na página em questão:

Antes:

<div style="width: 557px" class="wp-caption alignnone">
  <img class="" src="http://s30.postimg.org/6l234x6cx/kraken_antes.jpg" alt="Antes" width="547" height="52" />
  
  <p class="wp-caption-text">
    Antes
  </p>
</div>

Depois

<div style="width: 562px" class="wp-caption alignnone">
  <img class="" src="http://s30.postimg.org/wun5npsa9/kraken_depois.jpg" alt="depois" width="552" height="51" />
  
  <p class="wp-caption-text">
    depois
  </p>
</div>

Lembrando que em ambos os carregamentos o cache foi limpo.

E sobre a qualidade. Gostaria que você mesmo fizesse esse teste com a imagem de sua preferência.

### Ok, quero usar!

Infelizmente nada que funciona tão bem é de graça. O Kraken possui vários tipos de planos, com pagamento mensal ou anual.

Mas também há também o modo gratuito, com algumas limitações, é claro. No modo gratuito você não terá acesso a recursos como a API deles, Plugin para WordPress entre outros. Mas talvez o que vá mais lhe incomodar é o limite de 1MB por imagem.

Eu pessoalmente, uso apenas o modo gratuito e não tenho muitos problemas. Geralmente quando eu lido com imagens acima de 1MB, eu recorro a uma outra alternativa que citarei logo abaixo.

### Uma alternativa interessante

Também há uma ferramenta chamada Compressor.io, ela tem a mesma finalidade do Kraken mas é 100% gratuito. Ela se demonstra tão eficiente quanto, e eu já até tive imagens que a compressão foi maior no Compressor.io do que no Kraken, como podem ver abaixo:

No Kraken:

<div style="width: 898px" class="wp-caption alignnone">
  <img class="" src="http://s10.postimg.org/okddqy9gp/compressao_no_kraken.png" alt="Kraken" width="888" height="93" />
  
  <p class="wp-caption-text">
    Kraken
  </p>
</div>

No Compressor:

<div style="width: 838px" class="wp-caption alignnone">
  <img class="" src="http://s10.postimg.org/h346bqjxl/compressao_no_compressor.png" alt="Compressor" width="828" height="57" />
  
  <p class="wp-caption-text">
    Compressor
  </p>
</div>

Tudo bem que nesse exemplo não se tratou de uma imagem grande. Nesse caso eu usei a imagem que se tornou a capa desse artigo. Mas demonstra que mesmo tratando-se de uma aplicação gratuita, se mostra tão competente quanto. (Não me perguntem o por que em cada ferramenta a imagem foi identificada com o tamanho original diferente. Mas é a mesma imagem, eu juro! )

O único problema é que o Compressor.io só permite você otimizar uma imagem por vez, e isso pode tornar as coisas meio trabalhosas dependendo da quantidade de imagens que você precisa tratar. Também não há tantos recursos quanto o Kraken tem caso você esteja disposto a pagar pelo serviço.

Caso você tenha várias imagens com menos de 1MB e algumas imagens com mais, você poderá usar o melhor de cada ferramenta para conseguir atingir a otimização de performance que você deseja para seu site, gratuitamente!

<a title="Kraken" href="http://kraken.io" target="_blank">http://kraken.io</a>

<a title="Compressor" href="http://compressor.io" target="_blank">http://compressor.io</a>

Agora é com vocês!

Não esqueça de deixar seu comentário abaixo! Já conhecia o Kraken? Começou a usar depois desse artigo? Conhece outras alternativas? Compartilhe conosco!