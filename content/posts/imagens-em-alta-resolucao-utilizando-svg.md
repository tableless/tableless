---
title: Imagens em alta resolução utilizando SVG
author: Dani Guerrato
type: post
date: 2012-11-27
excerpt: Entenda o que são imagens SVG e como você poderá utilizá-las hoje.
url: /imagens-em-alta-resolucao-utilizando-svg/
tweetbackscheck:
  - 1356389712
shorturls:
  - 'a:3:{s:9:"permalink";s:31:"http://tableless.com.br/?p=7276";s:7:"tinyurl";s:26:"http://tinyurl.com/d7rn58q";s:4:"isgd";s:19:"http://is.gd/P6KSuR";}'
twittercomments:
  - 'a:0:{}'
categories:
  - Artigos
  - CSS
  - CSS3
  - Técnicas e Práticas
tags:
  - alta resolução
  - CSS3
  - HiDPI
  - html5
  - imagens
  - svg
  - w3c
  - xml

---
## Scalable Vector Graphics (SVG)

Uma das grandes tendências do momento quando se fala sobre desenvolvimento web é o formato SVG, principalmente com o advento do design responsivo e a consequente preocupação com dispositivos com densidade de pixel superior (HiDPI) como a tela retina da Apple, utilizada nos modelos mais recentes do iPhone, iPad e do Macbook Pro. Mas o que exatamente é um arquivo SVG? Qual é a diferença entre um vetor e um bitmap? E como e por que utilizar esta tecnologia a nosso favor?

## O que é SVG?

SVG é uma sigla para Scalable Vector Graphics ou, em português, Vetor Gráfico Redimensionável. O padrão foi proposto pelo W3C em 1999, inspirado em formatos proprietários como VML da Microsoft e PGML da Adobe. Em 2001 o SVG ganhou sua primeira versão oficial. A vantagem deste formato em relação aos anteriores é ele ser um padrão aberto (open source). Ou seja, todos podem utilizar sem ter que pagar dinheiro para nenhuma empresa&#8230;

Um arquivo SVG é basicamente um mapa em XML que descreve matematicamente uma figura gráfica bidimensional. Funciona como um conjunto de instruções numéricas para realizar um desenho, que são convertidas em imagens em um software capaz de interpreta-lo (como um browser, por exemplo). SVG é para uma imagem o que o HTML é para um texto.

## Vetor vs Bitmap

Existem dois tipos principais de arquivos de imagens. Vetores e Bitmaps. Os arquivos do tipo vetor (como AI, EPS, CDR e o nosso novo melhor amigo SVG) são linhas, curvas e formas geometricas descritas matematicamente. Já os arquivos bitmaps (como JPG, PNG, GIF etc) são compostos por um grid de pixels.

As vantagens de se utilizar gráficos em vetor são incríveis. Primeiramente por que é possível redimensiona-los infinitamente sem perder qualidade ou nitidez. Na prática isto significa que um ícone, por exemplo, terá a mesma aparência sem distorções em um smartphone ou uma televisão de 42&#8221;. Não importa qual é a quantidade de espaço que a imagem ocupa, o arquivo terá o mesmo peso. O que potencialmente economiza a quantidade de banda necessária para realizar o download, minimiza a quantidade de requisições para o servidor já que não são necessárias diversas imagens diferentes para servir todas as necessidades, etc&#8230; A possibilidade de uso de medidas relativas também faz dos gráficos em SVG o formato ideal para se trabalhar com design responsivo.

<img class="alignnone size-full wp-image-7315" alt="SVG vs PNG" src="http://tableless.com.br/uploads/2012/11/svg-versus-png.jpg" width="720" height="495" srcset="uploads/2012/11/svg-versus-png.jpg 720w, uploads/2012/11/svg-versus-png-300x206.jpg 300w" sizes="(max-width: 720px) 100vw, 720px" />

## Onde e quando aplicar

Ultimamente o formato vem sendo utilizado para ícones, mas ele é útil para qualquer elemento gráfico que precisa ser redimensionado como botões, padrões de background, etc&#8230; Uma boa dica é utilizar gráficos SVG para logotipos. Desta maneira o logo sempre ficará nítido e com uma boa qualidade em qualquer resolução ou tamanho de tela, deixando seu cliente muito mais feliz&#8230;

Existem ainda uma infinidade de outras possibilidades para este tipo de arquivo como filtros, animações, scripts e outros elementos interativos. Até alguns jogos simples, como este clone de [Tetris][1] pela Mozilla.

Mas é bom não abusar. Quanto mais complexa a imagem mais tempo levará para o browser renderiza-la. É inviável utilizar o formato para uma fotografia, por exemplo.

## Como fazer um arquivo SVG

Bem, se você gosta muito de matemática e hard coding você pode abrir um editor de texto e escrever manualmente. Se você deseja se aventurar existem alguns tutoriais bacanas nesta [wiki][2]. Existem ainda algumas bibliotecas de javascript, como a [Raphael.js][3], que facilitam bastante o trabalho.

Mas para quem não é o super-herói da matemática e deseja uma solução mais prática é possível utilizar algumas ferramentas gráficas como o Adobe Illustrator, Corel Draw, Inkscape&#8230; e simplesmente exportar outros arquivos vetoriais para o formato. Existe até um editor online chamado [SVG Edit][4]. Ele é bem simples, mas quebra um bom galho na falta de um outro software por perto.

É possível encontrar por aí até alguns programas que prometem converter automaticamente bitmap em SVG&#8230; Mas isto não é nada recomendável e cria resultados com qualidade desastrosa.

Se você não é um grande designer, sem problemas. Você pode ainda encontrar diversos pacotes de ícones no formato sob licença creative commons. Uma boa fonte para quem gosta do estilo minimalista é o site [Noum Project][5].

## Implementação

#### Uma pequena nota sobre medidas relativas

Lembrando que para esta técnica funcionar corretamente no caso específico de design responsivo é necessário a utilização de medidas relativas como EM e porcentagem. Vamos utilizar para os exemplos práticos um pequeno icone de roldana. O tamanho &#8220;padrão&#8221; do nosso ícone de exemplo seria equivalente a 32px de altura e largura. Se considerarmos que a medida padrão de texto (1em) de um browser é equivalente a 16px, o tamanho padrão do nosso icone seria portanto 2em (16&#215;2 = 32). Tomar este tipo de preocupação é fundamental para garantir a flexibilidade das imagens e dar ao desenvolvedor um controle muito maior sobre o conteúdo. Não se esqueça que esta medida será afetada de acordo com a porcentagem do font-size, ok? Para fins práticos vamos trabalhar neste artigo com a medida em 100%.

Hora de colocar a mão na massa e conhecer alguns métodos de desenvolvimento. Não existe uma solução perfeita, cada uma é boa para um tipo de situação. Vamos analisar algumas opções, juntamente com seus lados positivos e negativos.

#### 1. < object >

[cc escaped=&#8221;true&#8221; lang=&#8221;html&#8221;]
  
<object data=&#8217;icone.svg&#8217; type=&#8217;image/svg+xml&#8217;>
  
<img src=&#8217;img/icone.png&#8217;>
  
</object>

**pró:** É o metodo de aplicação mais utilizado, devido a facilidade para criar-se um fallback para as versões mais antigas do Internet Explorer.
  
**contra:** Não é a solução mais semântica, já que o W3C não recomenda a utilização desta tag para imagens. Pode gerar ainda alguns problemas de compatibilidade. A engine Safari/Webkit não renderiza corretamente elementos object com transparência, por exemplo.

#### 2. **<svg>**

<pre class="lang-html">&lt;svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink"&gt;
&lt;path fill="#231F20" d="M32,17.969v-4l-4.781-1.992c-0.133-0.375-0.273-0.737-0.445-1.094l1.93-4.805L25.875,3.25l-4.763,1.961
c-0.362-0.175-0.734-0.323-1.117-0.461L17.969,0h-4l-1.977,4.734c-0.398,0.141-0.781,0.289-1.161,0.469L6.078,3.294L3.25,6.122
l1.938,4.711C5,11.219,4.847,11.614,4.703,12.021L0,14.031v4l4.706,1.961c0.146,0.406,0.302,0.802,0.489,1.188l-1.903,4.742
L6.12,28.75l4.724-1.945c0.378,0.18,0.766,0.325,1.164,0.461L14.031,32h4l1.979-4.758c0.38-0.141,0.755-0.289,1.114-0.461
l4.797,1.922l2.828-2.828l-1.969-4.773c0.167-0.359,0.305-0.722,0.438-1.094L32,17.969z M15.969,22c-3.312,0-6-2.688-6-6
s2.688-6,6-6s6,2.688,6,6S19.281,22,15.969,22z"/&gt;
&lt;/svg&gt;</pre>

**pró:** Esta tag de HTML5 foi criada especificamente para este fim, portanto esta é a solução mais moderna e semântica. É relativamente simples: basta colar o código SVG inline.
  
**contra:** Código muito extenso dificulta a manutenção (já que é preciso editar manualmente e não apenas substituir um arquivo), baixo grau de compatibilidade com browsers antigos.

#### 3. <img><img alt="" />

<pre class="lang-html">&lt;img src='img/icone.svg'&gt;</pre>

**pró:** Aplicação simples. Melhor opção para imagem sem interação.
  
**contra:** Por motivos de segurança, alguns browsers podem desativar scripts em SVG e algumas opções interativas na tag <img>, como links.

#### 4. Background Images

**pró:** Esta opção utiliza apenas CSS. Muito útil para algumas combinações mais complexas como sprites responsivos.

**contra:** Fallback depende de javascript para funcionar corretamente (veja explicação mais detalhada abaixo).

.icone {
  
background: url(&#8220;../img/icone.svg&#8221;) no-repeat;
  
width: 2em;
  
height: 2em;
  
}

#### Suporte

Google Chrome 4+, Firefox 3+, Safari 3.2+, Opera 8+ e IE 9+.

## Métodos de Fallback

#### 

#### Background images em CSS

As versões mais antigas do Internet Explorer (8 e anteriores) possuem diversas deficiências, dentre elas a falta de suporte para background em RGBA. Mas alguns males vem para o bem. É possível se aproveitar desta falha em nosso beneficio. Basta preparar duas imagens: uma versão em SVG para os navegadores mais atuais e outra em PNG para os navegadores antigos e, na classe do CSS, declaramos dois backgrouds. Em um chamamos a imagem em SVG e declaramos uma cor para o background dela usando RGBA. Os navegadores mais antigos irão ignorar esta linha pois, para eles, o RGBA é um erro e eles não irão ler este background. Para estes navegadores, colocamos outro background com a imagem em png. O contra é não é a solução mais semântica já que o usuário será obrigado a baixar duas vezes as imagens&#8230; Mas existem algumas maneiras de contornar com a utilização de plugins que controlam a requisição de imagens HD do servidor como o [Foresight][6].

<pre class="lang-css">body {
font-size:100%;
}

.icone {
background: url("../img/icone.png") no-repeat;
background: rgba(0,0,0,0) url("../img/icone.svg") no-repeat;
width: 2em;
height: 2em;
text-indent: -6000px;
}</pre>

#### Comentário condicional para IE

<pre class="lang-html">&lt;!--[if lte IE 8]&gt;&lt;img src='img/icone.png'&gt;&lt;![endif]--&gt;
&lt;!--[if gt IE 8]&gt;&lt;img src='img/icone.svg'&gt;&lt;![endif]--&gt;
&lt;!--[if !IE]&gt; --&gt;&lt;img src='img/icone.svg'&gt;&lt;!-- &lt;![endif]--&gt;</pre>

#### Fallback utilizando Modernizr

Pode-se utilizar a biblioteca [Modernizr][7] para detectar se existe um suporte ao elemento. O script funciona da seguinte maneira: se o navegador suporta o formato a classe .svg é adicionada ao html, em caso negativo a classe anexada é .no-svg. Isto possibilita a inclusão de um css alternativo. Veja o exemplo:

<pre class="lang-css">.icone {
width: 2em;
height: 2em;
text-indent: -6000px;
}

.icone.svg {
background: url(icone.svg) no-repeat;

}

.icone.no-svg {
background: url(icone.png) no-repeat;
}</pre>

## Considerações Finais

Fácil, rápido e indolor. Até o momento não existe nenhuma contra-indicação para o formato e os problemas de retro compatibilidade podem ser facilmente contornados com um pouco de criatividade e conhecimento&#8230; Quem acha que gráficos em alta resolução são uma preocupação apenas para um futuro distante esta na hora de abrir a janela (do browser) e dizer olá para o presente.

## Saiba mais:

#### [Resolution Independence with SGV][8]

Artigo bem completo da Smashing Magazine sobre o assunto.

#### [W3C SVG][9]

O canal oficial do formato na W3C.

#### [Ways to embed a Clickable SVG-Logo into Your Website][10]

Uma lista extensiva com vantagens e desvantagens de cada método e exemplos de uso.

#### [Using SVG for flexible scalable and fun backgrounds &#8211; Part I][11]

Artigo do blog A List Apart &#8211; Parte 1

#### [Using SVG for flexible scalable and fun backgrounds &#8211; Part II][12]

Artigo do blog A List Apart &#8211; Parte 2

 [1]: http://croczilla.com/bits_and_pieces/svg/samples/svgtetris/svgtetris.svg "Mozila SVG Tetris"
 [2]: http://docs.webplatform.org/wiki/svg/tutorials
 [3]: http://raphaeljs.com/
 [4]: http://svg-edit.googlecode.com/svn/branches/2.5.1/editor/svg-editor.html
 [5]: http://thenounproject.com/
 [6]: https://github.com/adamdbradley/foresight.js
 [7]: http://modernizr.com/
 [8]: http://coding.smashingmagazine.com/2012/01/16/resolution-independence-with-svg/
 [9]: http://www.w3.org/Graphics/SVG/
 [10]: http://www.noupe.com/tutorial/svg-clickable-71346.html
 [11]: http://www.alistapart.com/articles/using-svg-for-flexible-scalable-and-fun-backgrounds-part-i/
 [12]: http://www.alistapart.com/articles/using-svg-for-flexible-scalable-and-fun-backgrounds-part-ii/