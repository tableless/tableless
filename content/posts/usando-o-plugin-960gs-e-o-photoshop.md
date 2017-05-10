---
title: Usando o plugin 960gs e o Photoshop
author: Flavio Santana
type: post
date: 2013-06-25
excerpt: Entenda como funciona o Grid 960. Ideal para iniciantes.
url: /usando-o-plugin-960gs-e-o-photoshop/
dsq_thread_id: 1404571107
categories:
  - Código
  - Design
  - HTML
  - O Básico
tags:
  - 2013
  - grid

---
Grids tem como base no Design Gráfico como forma não só de organização, mas de proporção e distribuição dos elementos dentro do layout. Seja de um livro, uma revista ou um web site, usamos grids para estruturar as informações e alinhamentos.

Especialmente no Design para Web, usamos, na maioria das vezes o sistema de grid de 960 pixels que é um padrão para monitores antigos com resolução de 1024×768 mostrem o site corretamente sem que se crie a barra de rolagem horizontal.

No sistema de grid de 960px podemos dividir em 12, 16 ou 24 colunas e criar a estrutura do site nessas proporções facilitando para que se torne responsivo e adaptativo para telas de dispositivos móveis.

Neste tutorial eu vou mostrar como funciona um layout de um site responsivo usando o 960gs no Photoshop

## Instalando o plugin

Um recurso muito interessante para criarmos grids rapidamente em softwares como o Photoshop e o Fireworks é o plugin 960gs. Este plugin pode ser encontrado no site <a href="http://960.gs" target="_blank">http://960.gs/</a>

[<img class="alignnone size-medium wp-image-37700" alt="960gs-btn" src="http://tableless.com.br/uploads/2013/06/960gs-btn-465x310.jpg" width="465" height="310" srcset="uploads/2013/06/960gs-btn-465x310.jpg 465w, uploads/2013/06/960gs-btn-252x168.jpg 252w, uploads/2013/06/960gs-btn.jpg 600w" sizes="(max-width: 465px) 100vw, 465px" />][1]

No site, encontramos o botão de download &#8211; **Big ol’ DOWNLOAD button** . A pasta vem com um nome **“nathansmith-960-Grid-System-231ee0c“** que contém códigos html e css e vários tipos de templates do grid para diversos tipos de aplicações.

[<img class="alignnone size-medium wp-image-37702" alt="plugin" src="http://tableless.com.br/uploads/2013/06/plugin-465x310.jpg" width="465" height="310" srcset="uploads/2013/06/plugin-465x310.jpg 465w, uploads/2013/06/plugin-252x168.jpg 252w, uploads/2013/06/plugin.jpg 600w" sizes="(max-width: 465px) 100vw, 465px" />][2]

Baixando o arquivo e descompactando temos a pasta **app_plugin** e temos a Actions para Photoshop e a extensão do Fireworks. Execute a Action ele abrirá o Photoshop automaticamente com os padrões de grid no painel de Actions. **Window > Action ou Alt + F9**

[<img class="alignnone size-medium wp-image-37701" alt="actions" src="http://tableless.com.br/uploads/2013/06/actions-465x310.jpg" width="465" height="310" srcset="uploads/2013/06/actions-465x310.jpg 465w, uploads/2013/06/actions-252x168.jpg 252w, uploads/2013/06/actions.jpg 600w" sizes="(max-width: 465px) 100vw, 465px" />][3]

## Definindo o layout

Vamos trabalhar no padrão de 12 colunas apenas. Executando a Action no botão “Play” ele cria um documento padrão com o tamanho de **1020x700px** e com o nome **12 Column Grid**. *As definições do grid podem ser alteradas caso seja necessário.

[<img class="alignnone size-medium wp-image-37703" alt="grid-1" src="http://tableless.com.br/uploads/2013/06/grid-1-465x310.jpg" width="465" height="310" srcset="uploads/2013/06/grid-1-465x310.jpg 465w, uploads/2013/06/grid-1-252x168.jpg 252w, uploads/2013/06/grid-1.jpg 600w" sizes="(max-width: 465px) 100vw, 465px" />][4]

Vamos ajustar nosso documento para o tamanho inicial de **1440x900px**. A altura do layout pode variar com o andamento do wireframe. Para isso vamos em **Image > Canvas Size ou Alt+Ctrl+C**

[<img class="alignnone size-medium wp-image-37704" alt="canvas" src="http://tableless.com.br/uploads/2013/06/canvas-465x310.jpg" width="465" height="310" srcset="uploads/2013/06/canvas-465x310.jpg 465w, uploads/2013/06/canvas-252x168.jpg 252w, uploads/2013/06/canvas.jpg 600w" sizes="(max-width: 465px) 100vw, 465px" />][5]

**Nota:** É importante ressaltar que o grid vêm com **10px** de margem direita e esquerda. O nosso layout responsivo vai se basear nessas h2.
  
<img class="alignnone size-medium wp-image-37705" alt="grid-2" src="http://tableless.com.br/uploads/2013/06/grid-2-465x310.jpg" width="465" height="310" srcset="uploads/2013/06/grid-2-465x310.jpg 465w, uploads/2013/06/grid-2-252x168.jpg 252w, uploads/2013/06/grid-2.jpg 600w" sizes="(max-width: 465px) 100vw, 465px" />

Salve o seu documento **File > Save** ou **Ctrl + S** com um nome que você quiser. Eu salvei o meu documento como uma empresa fictícia chamada **Covey.**

## Criando a interface

Se você está criando uma interface do zero, pense no seu contexto e conteúdo. Quando se cria sites responsivos, é crucial pensarmos como exibiremos o seu conteúdo e como ele vai se comportar em dispositivos com telas menores. Tablets no geral tem resolução em posição de paisagem de **1024&#215;768**, logo, sites criados em padrões **960px** funcionam perfeitamente nessa resolução.

Quando escolhemos o sistema de grid de **12**, **16** ou **24** colunas, seguimos um padrão de uso de colunas. Abaixo eu apliquei em um wireframe usando o sistema de **12 colunas**.

Ele tem um tamanho de **940px** de área útil, ou seja, de conteúdo e elementos. Deixei **10px** padrão de cada lado do layout como folga, assim ele não ficará colado na borda da tela.

Aqui, tenho um cabeçalho com menu e um banner principal com texto e um rodapé com links. Meu conteúdo é dividido em 3 blocos, então eu usei 4 colunas para cada bloco. Se eu tivesse 4 blocos de conteúdo, usaria 3 colunas e assim sucessivamente. No meu caso, eu usarei o grid da seguinte forma:

[<img class="alignnone size-medium wp-image-37706" alt="desktop_01_01" src="http://tableless.com.br/uploads/2013/06/desktop_01_01-401x310.jpg" width="401" height="310" srcset="uploads/2013/06/desktop_01_01-401x310.jpg 401w, uploads/2013/06/desktop_01_01-217x168.jpg 217w, uploads/2013/06/desktop_01_01.jpg 600w" sizes="(max-width: 401px) 100vw, 401px" />][6]

No formato retrato **(768px)** do  **tablet**, eu usei 9 colunas e redimensionei o conteúdo para utilizar os mesmo blocos de conteúdo em 3 colunas.

[<img class="alignnone size-medium wp-image-37708" alt="tablet_01" src="http://tableless.com.br/uploads/2013/06/tablet_01-401x310.jpg" width="401" height="310" srcset="uploads/2013/06/tablet_01-401x310.jpg 401w, uploads/2013/06/tablet_01-217x168.jpg 217w, uploads/2013/06/tablet_01.jpg 600w" sizes="(max-width: 401px) 100vw, 401px" />][7]

E no **celular** **(240px)** o uso de 3 colunas para cada bloco de conteúdo é o mesmo, o que muda é a posição dos elementos que passam a ficar um em cima do outro.

[<img class="alignnone size-full wp-image-37800" alt="58df1f37-5a47-4696-8197-216d3ff6836c" src="http://tableless.com.br/uploads/2013/06/58df1f37-5a47-4696-8197-216d3ff6836c.png" width="600" height="947" srcset="uploads/2013/06/58df1f37-5a47-4696-8197-216d3ff6836c.png 600w, uploads/2013/06/58df1f37-5a47-4696-8197-216d3ff6836c-106x168.png 106w, uploads/2013/06/58df1f37-5a47-4696-8197-216d3ff6836c-196x310.png 196w" sizes="(max-width: 600px) 100vw, 600px" />][8]

Eu não vou entrar a fundo no assunto de **CSS**. Eu exemplifiquei para mostrar como eu resolvi a questão do redimensionamento.

<pre class="lang-css">body{
	margin:0 10px;
	background:#f1f1f1;
}

#geral{
	width:100%;
	max-width:940px;
	min-width:220px;
	margin:0 auto;
}

header{
	height:80px;
	background:#323232;
}

#banner{
	height:260px;
	background:#FFF;
	margin:15px 0 15px;
}

footer{
	height:190px;
	background:#CCC;
	margin:15px 0;
	clear:both;
}

article{
	height:260px;
	background:#5f65b3;
	width:31.25%;
	float:left;
}

article.middle{
	margin:0 3.125% 15px;
}

@media only screen and (max-width:600px){
	article{
		width:100%;
		margin-bottom:15px;
	}

	article.middle{
		margin:0px;
		margin-bottom:15px;
	}
}</pre>

No site fictício, eu criei em cima do wireframe pensando como as informações ficariam dispostas, então temos a interface web. Nesta parte não detalhei detalhes visuais ou de formatação, apenas no conceito de grids.

[<img class="alignnone size-medium wp-image-37707" alt="covey-960gs-example" src="http://tableless.com.br/uploads/2013/06/covey-960gs-example-496x310.png" width="496" height="310" srcset="uploads/2013/06/covey-960gs-example-496x310.png 496w, uploads/2013/06/covey-960gs-example-268x168.png 268w, uploads/2013/06/covey-960gs-example.png 1440w" sizes="(max-width: 496px) 100vw, 496px" />][9]

Se colocarmos como se fossem camadas, a ideia do uso do grid para 3 diferentes tipos de tela, temos esse resultado:

[<img class="alignnone size-medium wp-image-37710" alt="camads_01" src="http://tableless.com.br/uploads/2013/06/camads_01-490x310.jpg" width="490" height="310" srcset="uploads/2013/06/camads_01-490x310.jpg 490w, uploads/2013/06/camads_01-265x168.jpg 265w, uploads/2013/06/camads_01.jpg 600w" sizes="(max-width: 490px) 100vw, 490px" />][10]

## Resultado Final

Em sua versão desktop, temos o layout padrão em grid **960px**. O resultado final ficaria assim:

[<img class="alignnone size-medium wp-image-37711" alt="pc_01_01" src="http://tableless.com.br/uploads/2013/06/pc_01_01-463x310.jpg" width="463" height="310" srcset="uploads/2013/06/pc_01_01-463x310.jpg 463w, uploads/2013/06/pc_01_01-251x168.jpg 251w, uploads/2013/06/pc_01_01.jpg 600w" sizes="(max-width: 463px) 100vw, 463px" />][11]
  
Na versão  **tablet**, o CSS diminui as imagens, o texto do banner e o tamanho do corpo de cada bloco de conteúdo.
  
[<img class="alignnone size-medium wp-image-37712" alt="0000_01_01" src="http://tableless.com.br/uploads/2013/06/0000_01_01-328x310.jpg" width="328" height="310" srcset="uploads/2013/06/0000_01_01-328x310.jpg 328w, uploads/2013/06/0000_01_01-178x168.jpg 178w, uploads/2013/06/0000_01_01.jpg 600w" sizes="(max-width: 328px) 100vw, 328px" />][12]
  
Na versão de **celular**, o layout se adapta até o tamanho de **240px**. Com ajuda do CSS, eu otimizei o menu para o estilo **dropdown**, otimizando a experiência de navegação.

[<img class="alignnone size-medium wp-image-37713" alt="celular_01" src="http://tableless.com.br/uploads/2013/06/celular_01-432x310.jpg" width="432" height="310" srcset="uploads/2013/06/celular_01-432x310.jpg 432w, uploads/2013/06/celular_01-234x168.jpg 234w, uploads/2013/06/celular_01.jpg 600w" sizes="(max-width: 432px) 100vw, 432px" />][13]

## Conclusão

Vários artigos sobre **Design Responsivo** ou **RWD** (Responsive Web Design) estão disponíveis na Web. Este artigo é apenas uma das formas que conseguimos otimizar o site para dispositivos móveis. Lembrando, como disse anteriormente, temos que pensar como o conteúdo será exibido e como podemos moldar ao nosso projeto e como trabalhar ele de diferentes formas.

Eu disponibilizei esse exemplo de layout neste <a href="http://bit.ly/12kNheE" target="_blank">http://bit.ly/12kNheE</a> para melhor visualização e entendimento. Espero que tenha ajudado a gerar conhecimento. Gostou, quer comentar ou criticar? Vamos conversar

 [1]: http://tableless.com.br/uploads/2013/06/960gs-btn.jpg
 [2]: http://tableless.com.br/uploads/2013/06/plugin.jpg
 [3]: http://tableless.com.br/uploads/2013/06/actions.jpg
 [4]: http://tableless.com.br/uploads/2013/06/grid-1.jpg
 [5]: http://tableless.com.br/uploads/2013/06/canvas.jpg
 [6]: http://tableless.com.br/uploads/2013/06/desktop_01_01.jpg
 [7]: http://tableless.com.br/uploads/2013/06/tablet_01.jpg
 [8]: http://tableless.com.br/uploads/2013/06/58df1f37-5a47-4696-8197-216d3ff6836c.png
 [9]: http://tableless.com.br/uploads/2013/06/covey-960gs-example.png
 [10]: http://tableless.com.br/uploads/2013/06/camads_01.jpg
 [11]: http://tableless.com.br/uploads/2013/06/pc_01_01.jpg
 [12]: http://tableless.com.br/uploads/2013/06/0000_01_01.jpg
 [13]: http://tableless.com.br/uploads/2013/06/celular_01.jpg