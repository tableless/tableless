---
title: Construindo protótipos navegáveis em realidade virtual com A-Frame
authors: Bruno Castro
type: post
date: 2017-07-16
excerpt: A-Frame é um framework NODE.JS pra construção de aplicações em 360 no browser.
image: https://i.imgur.com/EWitjy4.png
categories:
  - Javascript
tags:
  - nodejs
  - aframe
---

[A-Frame](https://aframe.io/) é um framework NODE.JS pra construção de
aplicações em 360 no *browser*. Sua estrutura de *tags* é muito parecidas com as
do html e apesar de não ter como finalidade gerar protótipos, sua implementação
descomplicada o torna uma solução atraente na falta de ferramentas apropriadas
pra desenvolver protótipos em realidade virtual.

Nesse tutorial vamos construir um protótipo VR navegável baseado em um [exemplo
de loja virtual, veja online](https://conceptstore360.github.io/).

<div style="max-width: 800px; width:100%;height:0;padding-bottom:57%;position:relative;"><iframe src="https://giphy.com/embed/l1BgSQsZviwBFQa6k" width="100%" height="100%" style="max-width: 800px; position:absolute" frameBorder="0" class="giphy-embed" allowFullScreen></iframe></div><p><a href="https://giphy.com/gifs/vr-virtual-reality-360-l1BgSQsZviwBFQa6k">via GIPHY</a></p>

### Setup inicial

Lembre-se: o A-FRAME segue uma estrutura básica de html, então, todo projeto
deve ser iniciado como um html simples e as dependências do framework listadas
em scripts no head:

<script src="https://gist.github.com/brunocastro/9151dd5192370ae2a795f08218ebd3e6.js"></script>

O "aframe.min.js" é o *framework*, ele quem faz a mágica acontecer. Já o
"aframe-href-component.js" é uma dependência que permite adicionar links no
A-FRAME, aos moldes da propriedade href do HTML. Sem esta segunda linha de
script não seria possível lincar novas páginas.

#### Tags principais

Há algumas tags que você deve conhecer para iniciar todo e qualquer projeto, as
listo logo a baixo, você verá que todas fazem sentido.

![](https://cdn-images-1.medium.com/max/800/1*Rgsn-5qqCdg2vkmEaCGhnw.png)

**[&lt;a-scene&gt;](https://aframe.io/docs/0.6.0/core/scene.html)** esta tag é o cenário,
ela inicia a composição 3D para o navegador e deve envolver todas demais tags do
A-FRAME, contida no <body>. Tudo que existe na composição deve estar na tag
"a-scene" e tem suas posições X, Y e Z referenciados nela.

**[&lt;a-assets&gt;](https://aframe.io/docs/0.6.0/core/asset-management-system.html)** (não gera qualquer visualização) liste aqui todos os recursos de imagens,
audios, vídeos e modelos tridimensionais que devem ser carregados antes da
renderização. Isso impede que algo seja carregado depois da montagem da cena.

<script src="https://gist.github.com/brunocastro/2df875cac225bb784563812307cba268.js"></script>

**[&lt;-a-sky&gt;](https://aframe.io/docs/0.6.0/primitives/a-sky.html)** tag que
recebe o rótulo de Sky, ela é o céu do nosso cenário. Aqui determinamos qual
[imagem Equirectangular](https://www.flickr.com/groups/equirectangular/)
(cilíndrica equidistante) deverá ser o fundo da composição.

<script src="https://gist.github.com/brunocastro/1e0bf49a80998255dc348bf20d27f814.js"></script>

**[&lt;a-camera&gt;](https://aframe.io/docs/0.6.0/primitives/a-camera.html)** esta tag
 é fundamental** para que o usuário possa olhar ao seu entorno. Sem ela, uma
composição seria renderizada, mas não seria possível mudar o ponto de vista, o
usuário não conseguiria olhar a seu redor.

<script src="https://gist.github.com/brunocastro/85e32127f4f6025d280866361d388b90.js"></script>

**[&lt;a-cursor&gt;](https://aframe.io/docs/0.6.0/primitives/a-cursor.html)** (tag
opcional), indica o cursor (mira no centro da tela em forma de elipse). É se você
pretende adicionar navegação a composição. O cursor é a única forma no A-FRAME
de capturar o clique (lembre-se que não navegaremos com mouse, ou toque de
tela).

### Montando a composição

Até aqui, apenas montamos o cenário vazio com uma imagem de fundo, vamos agora
conhecer as tags que renderizam (geram elementos visíveis) no cenário do
A-FRAME:

#### Tags para gerar elementos

Listarei apenas as utilizadas na concept store, sugiro [conhecer outras
tags](https://aframe.io/docs/).

![](https://cdn-images-1.medium.com/max/1000/1*YpuSoi-CU63POpmnktyyhA.png)

**[&lt;a-entity
obj-model=""&gt;](https://aframe.io/docs/0.6.0/components/obj-model.html)**
Permite carregar modelos tridimensionais exportados de softwares de modelagem.
Muito útil para colocar objetos complexos em sua composição, como o Tênis em
destaque na *concept store*.

<script src="https://gist.github.com/brunocastro/57155df22d5b9962a9c5e365822d2a8a.js"></script>

**[&lt;a-image&gt;](https://aframe.io/docs/0.6.0/primitives/a-image.html)** O bom e
velho *bitmap* terá sempre o seu lugar. Com essa tag você pode carregar uma
imagem em 2D e posicioná-la onde desejar nos 3 eixos: x, y e z.

<script src="https://gist.github.com/brunocastro/7fb72f50a566dbe9223d3c4058dbfa25.js"></script>

**[&lt;a-curvedimage&gt;](https://aframe.io/docs/0.6.0/primitives/a-curvedimage.html)**
Essa talvez seja a tag mais útil se você pretende criar interfaces em 360.
Você pode carregar imagens ( de preferência bem largas, tipo landscape) e
determinar qual raio (distância do centro à borda de uma elipse) ela terá em
relação ao centro do cenário.

<script src="https://gist.github.com/brunocastro/6f2b67fd5ae4d9422c3baf59c76ef2eb.js"></script>

### Misture tudo e leve ao forno!

Agora que já conhece as principais tags e entende a composição do cenário, fica
fácil criar seus protótipos navegáveis em 360 e testá-los no celular.<br>

**!dica:** use
[SimpleHTTPServer](https://www.scottmadethis.net/interactive/simpleserver/) e
transforme seu mac em um servidor local.

Lembre-se que um protótipo deve ser simples, ou seja, você deve dedicar o menor
esforço possível pra validar uma ideia. Veja como exemplo o código completo da
*concept store*, não é diferente de tudo que vimos até agora, com menos de 40
linhas e feito de forma simples:

<script src="https://gist.github.com/brunocastro/2f2606fca0906a75db1e44f660b4946b.js"></script>

Em pouco tempo teremos soluções mais práticas para prototipar em 360º, quem sabe
uma solução pra Sketch, XD ou Axure. Mas não espere até lá pra se arriscar no
seu primeiro protótipo funcional em realidade virtual.

Caso precise, volte a consultar este texto e sinta-se a vontade para baixar os
arquivos fontes da *Concept Store 360*. Todos os materiais da são distribuídos
sobre a [licença MIT (open source)](https://pt.wikipedia.org/wiki/LicenÃ§a_MIT),
veja, remixe e colabore:

Qualquer dúvida, posta lá no Git, ou aqui, nos comentários. ;)

### Referências:
* [VR](https://medium.com/tag/vr?source=post)
* [Prototyping](https://medium.com/tag/prototyping?source=post)
* [A Frame](https://medium.com/tag/a-frame?source=post)
* [UX Design](https://medium.com/tag/ux-design?source=post)
* [Design](https://medium.com/tag/design?source=post)
