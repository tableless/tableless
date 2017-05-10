---
title: Criando listras com CSS3
author: Jhonathan Souza Soares
type: post
date: 2014-05-15
excerpt: |
  |
    Já parou pra pensar que aquele background que você utilizava ‘repeat’ que sobrecarregava seu site e nunca ficava perfeito?
    Vamos ver como podemos criar fundos listrados sem a utilização de imagens!
url: /criando-listras-com-css3/
dsq_thread_id: 2648259341
categories:
  - CSS
  - CSS3

---
Cada vez mais, com o passar do tempo as ferramentas CSS3 aos poucos vem ganhando seu devido destaque. Com a constante atualização dos navegadores, a morte declarada do Windows XP, e novos dispositivos a cada dia, podemos finalmente colocar em projetos reais as funcionalidades, pelo menos algumas do CSS3.

Anteriormente sempre que queríamos algo assim, era necessário a utilização de imagens, texturas ou dependendo do caso nem era possível. Agora com a criação de listras em CSS você poderá fazer de maneira fácil, simples e melhorar o desempenho do carregamento do seu código no browser.

O início de tudo vem com a utilização CSS Gradientes quando foi falado inicialmente há 4 anos atrás sobre <a title="http://tableless.com.br/gradientes-em-css/" href="http://tableless.com.br/gradientes-em-css/" target="_blank">Gradientes em CSS</a> e foi apresentado um guia de <a title="http://tableless.com.br/como-usar-gradient-no-css-de-forma-consciente/" href="http://tableless.com.br/como-usar-gradient-no-css-de-forma-consciente/" target="_blank">Como usar linear-gradient de maneira consciente </a>fornecendo uma base para o que precisamos saber agora.

Primeiro precisamos saber quais são os tipos de gradientes que podemos utilizar :

<div id="attachment_42329" style="width: 845px" class="wp-caption aligncenter">
  <img class="wp-image-42329 size-full" src="http://tableless.com.br/uploads/2014/04/propriedade.jpg" alt="propriedades " width="835" height="260" srcset="uploads/2014/04/propriedade.jpg 835w, uploads/2014/04/propriedade-400x124.jpg 400w" sizes="(max-width: 835px) 100vw, 835px" />
  
  <p class="wp-caption-text">
    Tabela explicativa das propriedades gradiente com CSS3
  </p>
</div>

O [Bernard de Luna escreveu um arquivo completo aqui no Tableless][1] mostrando como usar o linear-gradient de forma consciente, vale a pena dar uma olhada para se familiarizar com cada tipo de gradiente. Neste post vamos utilizar basicamente a propriedade repeating-linear-gratient. Bom, chega de conversa e vamos entender inicialmente como podemos montar nosso fundo CSS.

### Listras Diagonais simples

Veja o seguinte exemplo :

<img class="alignnone size-full wp-image-42362" src="http://tableless.com.br/uploads/2014/04/1-90g.jpg" alt="listra-css" width="295" height="252" />

Veja o código:

<pre class="lang-css">.listra {
background: repeating-linear-gradient(
90deg,
#FCFF7C,
#FCFF7C 10px,
#FFE13A 10px,
#FFE13A 20px
);
</pre>

A propriedade contém as seguintes informações o nível de inclinação ( em graus ) de qual será as listras, as cores que você deseja colocar e a largura das mesmas. Veja a mesma imagem só que com o nível de inclinação em 45 graus :

<img class="alignnone size-full wp-image-42361" src="http://tableless.com.br/uploads/2014/04/1-45g.jpg" alt="fundo-listras-css" width="264" height="249" />

Vamos analisar a imagem com um pouco mais de atenção :

<img class="alignnone size-full wp-image-42360" src="http://tableless.com.br/uploads/2014/04/1-45b.jpg" alt="listra-css-analise" width="416" height="416" srcset="uploads/2014/04/1-45b.jpg 416w, uploads/2014/04/1-45b-400x400.jpg 400w" sizes="(max-width: 416px) 100vw, 416px" />

Podemos ver as dimensões de 10px em vermelho, a segunda lista iniciando com 20px e o grau de inclinação de 45º.

### Listras diagonais Gradiente

Se você fizer o background com uma listra padrão , e depois fazer metade das listras totalmente transparente ao invés de utilizar cores,você poderá implementar o efeito de gradiente na sua propriedade e fazer isso único elemento:

<img class="alignnone size-full wp-image-42364" src="http://tableless.com.br/uploads/2014/04/2-45g.jpg" alt="listra-css-gradiente" width="178" height="162" />

Veja seu código:

<pre class="lang-css">.listra {
background:
repeating-linear-gradient(
45deg,
transparent,
transparent 10px,
#ccc 10px,
#ccc 20px),
linear-gradient(
to bottom,
#fff,
#000
);}
</pre>

&nbsp;

Neste exemplo estou fazendo um fundo listrado com transparente e cinza, e utilizando a propriedade linear-gradient do branco ao preto cobrindo todas as listras. Viu como fica interessante?

### Listras sobre uma imagem

Sim, isto mesmo! Podemos utilizar texturas, imagens que acabam dando um maior efeito ao nosso background, veja como é fácil fazer :

Vamos analisar a seguinte imagem :

<img class="alignnone size-full wp-image-42365" src="http://tableless.com.br/uploads/2014/04/3-45g.jpg" alt="listra-css-com-imagem" width="298" height="162" />

Veja o código equivalente :

<pre class="lang-css">.listra {
background: repeating-linear-gradient(
45deg,
rgba(0, 0, 0, 0.2),
rgba(0, 0, 0, 0.2) 10px,
rgba(0, 0, 0, 0.3) 10px,
rgba(0, 0, 0, 0.3) 20px
),
url(textura.jpg);
}
);
</pre>

&nbsp;

Diante desta propriedade podemos analisar que inicialmente possuímos 45º de inclinação e desta vez, ao invés de utilizarmos cores no formado hexadecimal, utilizamos cores em modo rgba pois assim podemos colocar transparência (0.2 e 0.3) nas listras para que a mesma dê visibilidade a textura que foi colocada mais ao fundo da propriedade.

### Listras radiais

Bom, o CSS3 é uma ferramenta poderosa, não temos como duvidar disto, imagine criar o seguinte efeito:

<img class="alignnone size-full wp-image-42363" src="http://tableless.com.br/uploads/2014/04/1-360g.jpg" alt="listra-imagem-radial" width="274" height="161" />

Bom, isto é possível, veja só que simples:

<pre class="lang-css">.listra {
background: repeating-radial-gradient(
  circle,
  blue,
  blue 10px,
  #87A9FF 10px,
  #87A9FF 20px
);}

</pre>

A única diferença que ao invés de colocarmos a rotatividade em graus, adicionamos um círculo e o próprio CSS3 fez o resto!

Bom, acaba por aqui? Claro que não, ainda tem muito o que se pode fazer apenas com estas propriedades, a autora deste blog por exemplo, criou um tabuleiro de xadrez só com estas propriedades, veja só : <http://lea.verou.me/2010/12/checkered-stripes-other-background-patterns-with-css3-gradients/>

Ficamos por aqui, espero que tenham gostado!

 [1]: http://tableless.com.br/como-usar-gradient-no-css-de-forma-consciente/ "Como usar linear-gradient em CSS de forma consciente?"