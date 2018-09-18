---
title: Vídeos mais acessíveis com HTML5 – parte II
authors: Talita Pagani
type: post
date: 2011-03-15
url: /videos-mais-acessiveis-com-html5-parte-ii/
categories:
  - html5
tags:
  - Acessibilidade
  - Tecnologia e Tendências
  - acessibilidade
---

Na [primeira parte do artigo][1], vimos as principais características do DFXP, uma especificação do W3C para trabalhar com legendas em vídeos do HTML5. Agora iremos conhecer a estrutura de um arquivo DFXP e detalhar o conceito de regions.

### Estrutura básica de um arquivo DFXP

Um arquivo DFXP é um arquivo baseado em XML que utiliza a linguagem _Timed Text Markup Language_ (TTML). A TTML estabelece tags e propriedades específicas para atribuir uma informação textual a um intervalo de tempo, posicionar esta informação em uma determinada região do vídeo e formatar a apresentação desta informação. Um documento TTML começa com a tag `tt` e sua estrutura básica é composta por um cabeçalho e corpo de conteúdo. O cabeçalho apresenta informações como metadata, definições de estilo e layout, enquanto o corpo de conteúdo contém as especificações dos textos associados a tempo e referenciando estilos e informações de layout.

<pre lang="xml" class="1"><tt xml:lang="" xmlns="https://www.w3.org/ns/ttml">
	
	
</tt>
</pre>

_Estrutura básica de um document TTML._

### Metadados

A seção de metadata pode conter informações como título do documento, descrição e informações de _copyright_. As tags que representam estes metadados são especificadas através do _namespace_ `ttm` (timed text metadata).

<pre lang="xml" class="1">&lt;metadata xmlns:ttm="https://www.w3.org/ns/ttml#metadata">
	&lt;ttm:title>Exemplo de documento TTML&lt;/ttm:title>
	&lt;ttm:copyright>The Authors (c) 2011&lt;/ttm:copyright>
&lt;/metadata>
</pre>

O endereço do _namespace_ `ttm` definido na tag metadata assim como o _namespace_ para estilos (`tts`), podem ser definidos logo na tag `tt`, deixando o código um pouco mais limpo e organizado.

<pre lang="xml" class="1">&lt;tt xml:lang="en"
	xmlns="https://www.w3.org/ns/ttml"
	xmlns:tts="https://www.w3.org/ns/ttml#styling"
	xmlns:ttm="https://www.w3.org/ns/ttml#metadata">
...
&lt;/tt>
</pre>

### Criando estilos para legendas

Infelizmente a TTML não trabalha em conjunto com linguagens para definição de estilos como o XSLT ou o próprio CSS, mas ela possui tags e propriedades para definir e aplicar informações de estilo de modo consistente e similar à forma como fazemos com CSS. As propriedades de estilo pertencem ao namespace `tts` e podem também ser utilizadas nas tags de texto da legenda e na tag `region`. Um estilo (semelhante a uma classe CSS), é criado a partir da tag style e deve conter um id que irá utilizado para associar este estilo a outros elementos.

<pre lang="xml" class="1">&lt;styling xmlns:tts="https://www.w3.org/ns/ttml#styling">
	<!-- o estilo1 especifica o padrão para cor, fonte e alinhamento de texto -->
	&lt;style xml:id="estilo1"
		tts:color="white"
		tts:fontFamily="proportionalSansSerif"
		tts:fontSize="22px"
		tts:textAlign="center"
	/>
	

<!-- Estilo alternativo baseado no estilo1, ou seja, utilizando as mesmas propriedades mas mudando a cor para amarelo -->
	

<style xml:id="estilo2" style="estilo1" tts:color="yellow" />

<!-- Outro estilo baseado no estilo1, mas alterando o alinhamento do texto para a direita -->
	

<style xml:id="estilo1Direita" style="estilo1" tts:textAlign="end" />

<!-- Estilo baseado em estilo2 mas alterando o alinhamento do texto para a esquerda -->
	

<style xml:id="estilo2Esquerda" style="estilo2" tts:textAlign="start" />
&lt;/styling>
</pre>

As opções de alinhamento de texto são um pouco diferentes do convencional. Com exceção do center, o alinhamento à esquerda é definido como _start_ e à direita como _end_. Outras propriedades de formatação:

  * **tts:backgroundColor:** aceita valores hexadecimais, RGB e cores por nome
  * **tts:displayAlign:** aplicável somente à `region`, define o alinhamento do bloco de conteúdo de forma semelhante ao _float_ em CSS, porém tem como valores `before` (esquerda), `center`, `after` (direita)
  * **tts:extent:** aplicável somente à raiz do documento DFXP (`tt`) e à `region`, é utilizado para especificar largura e altura de uma region
  * **tts:fontStyle:** aceita valores como `italic<em> </em>`e `oblique`
  * **tts:fontWeight:** define o peso da fonte, aceita os valores ``Na [primeira parte do artigo][1], vimos as principais características do DFXP, uma especificação do W3C para trabalhar com legendas em vídeos do HTML5. Agora iremos conhecer a estrutura de um arquivo DFXP e detalhar o conceito de regions.

### Estrutura básica de um arquivo DFXP

Um arquivo DFXP é um arquivo baseado em XML que utiliza a linguagem _Timed Text Markup Language_ (TTML). A TTML estabelece tags e propriedades específicas para atribuir uma informação textual a um intervalo de tempo, posicionar esta informação em uma determinada região do vídeo e formatar a apresentação desta informação. Um documento TTML começa com a tag `tt` e sua estrutura básica é composta por um cabeçalho e corpo de conteúdo. O cabeçalho apresenta informações como metadata, definições de estilo e layout, enquanto o corpo de conteúdo contém as especificações dos textos associados a tempo e referenciando estilos e informações de layout.

<pre lang="xml" class="1"><tt xml:lang="" xmlns="https://www.w3.org/ns/ttml">
	
	
</tt>
</pre>

_Estrutura básica de um document TTML._

### Metadados

A seção de metadata pode conter informações como título do documento, descrição e informações de _copyright_. As tags que representam estes metadados são especificadas através do _namespace_ `ttm` (timed text metadata).

<pre lang="xml" class="1">&lt;metadata xmlns:ttm="https://www.w3.org/ns/ttml#metadata">
	&lt;ttm:title>Exemplo de documento TTML&lt;/ttm:title>
	&lt;ttm:copyright>The Authors (c) 2011&lt;/ttm:copyright>
&lt;/metadata>
</pre>

O endereço do _namespace_ `ttm` definido na tag metadata assim como o _namespace_ para estilos (`tts`), podem ser definidos logo na tag `tt`, deixando o código um pouco mais limpo e organizado.

<pre lang="xml" class="1">&lt;tt xml:lang="en"
	xmlns="https://www.w3.org/ns/ttml"
	xmlns:tts="https://www.w3.org/ns/ttml#styling"
	xmlns:ttm="https://www.w3.org/ns/ttml#metadata">
...
&lt;/tt>
</pre>

### Criando estilos para legendas

Infelizmente a TTML não trabalha em conjunto com linguagens para definição de estilos como o XSLT ou o próprio CSS, mas ela possui tags e propriedades para definir e aplicar informações de estilo de modo consistente e similar à forma como fazemos com CSS. As propriedades de estilo pertencem ao namespace `tts` e podem também ser utilizadas nas tags de texto da legenda e na tag `region`. Um estilo (semelhante a uma classe CSS), é criado a partir da tag style e deve conter um id que irá utilizado para associar este estilo a outros elementos.

<pre lang="xml" class="1">&lt;styling xmlns:tts="https://www.w3.org/ns/ttml#styling">
	<!-- o estilo1 especifica o padrão para cor, fonte e alinhamento de texto -->
	&lt;style xml:id="estilo1"
		tts:color="white"
		tts:fontFamily="proportionalSansSerif"
		tts:fontSize="22px"
		tts:textAlign="center"
	/>
	

<!-- Estilo alternativo baseado no estilo1, ou seja, utilizando as mesmas propriedades mas mudando a cor para amarelo -->
	

<style xml:id="estilo2" style="estilo1" tts:color="yellow" />

<!-- Outro estilo baseado no estilo1, mas alterando o alinhamento do texto para a direita -->
	

<style xml:id="estilo1Direita" style="estilo1" tts:textAlign="end" />

<!-- Estilo baseado em estilo2 mas alterando o alinhamento do texto para a esquerda -->
	

<style xml:id="estilo2Esquerda" style="estilo2" tts:textAlign="start" />
&lt;/styling>
</pre>

As opções de alinhamento de texto são um pouco diferentes do convencional. Com exceção do center, o alinhamento à esquerda é definido como _start_ e à direita como _end_. Outras propriedades de formatação:

  * **tts:backgroundColor:** aceita valores hexadecimais, RGB e cores por nome
  * **tts:displayAlign:** aplicável somente à `region`, define o alinhamento do bloco de conteúdo de forma semelhante ao _float_ em CSS, porém tem como valores `before` (esquerda), `center`, `after` (direita)
  * **tts:extent:** aplicável somente à raiz do documento DFXP (`tt`) e à `region`, é utilizado para especificar largura e altura de uma region
  * **tts:fontStyle:** aceita valores como `italic<em> </em>`e `oblique`
  * **tts:fontWeight:** define o peso da fonte, aceita os valores`` e `bold`
  * **tts:lineHeight:** altura da linha, aceita os valores normal ou uma altura especificada em uma unidade de medida
  * **tts:opacity:** aplicável somente à tag `region`, define transparência
  * **tts:origin:** especifica as coordenadas x e y de origem de uma `region`
  * **tts:overflow:** define o comportamento de uma `region` quando o conteúdo estoura o espaço disponível. Aceita os valores `visible` e `hidden`
  * **tts:padding:** espaçamento interno de uma `region`, aceita valores da mesma forma que a propriedade ```Na [primeira parte do artigo][1], vimos as principais características do DFXP, uma especificação do W3C para trabalhar com legendas em vídeos do HTML5. Agora iremos conhecer a estrutura de um arquivo DFXP e detalhar o conceito de regions.

### Estrutura básica de um arquivo DFXP

Um arquivo DFXP é um arquivo baseado em XML que utiliza a linguagem _Timed Text Markup Language_ (TTML). A TTML estabelece tags e propriedades específicas para atribuir uma informação textual a um intervalo de tempo, posicionar esta informação em uma determinada região do vídeo e formatar a apresentação desta informação. Um documento TTML começa com a tag `tt` e sua estrutura básica é composta por um cabeçalho e corpo de conteúdo. O cabeçalho apresenta informações como metadata, definições de estilo e layout, enquanto o corpo de conteúdo contém as especificações dos textos associados a tempo e referenciando estilos e informações de layout.

<pre lang="xml" class="1"><tt xml:lang="" xmlns="https://www.w3.org/ns/ttml">
	
	
</tt>
</pre>

_Estrutura básica de um document TTML._

### Metadados

A seção de metadata pode conter informações como título do documento, descrição e informações de _copyright_. As tags que representam estes metadados são especificadas através do _namespace_ `ttm` (timed text metadata).

<pre lang="xml" class="1">&lt;metadata xmlns:ttm="https://www.w3.org/ns/ttml#metadata">
	&lt;ttm:title>Exemplo de documento TTML&lt;/ttm:title>
	&lt;ttm:copyright>The Authors (c) 2011&lt;/ttm:copyright>
&lt;/metadata>
</pre>

O endereço do _namespace_ `ttm` definido na tag metadata assim como o _namespace_ para estilos (`tts`), podem ser definidos logo na tag `tt`, deixando o código um pouco mais limpo e organizado.

<pre lang="xml" class="1">&lt;tt xml:lang="en"
	xmlns="https://www.w3.org/ns/ttml"
	xmlns:tts="https://www.w3.org/ns/ttml#styling"
	xmlns:ttm="https://www.w3.org/ns/ttml#metadata">
...
&lt;/tt>
</pre>

### Criando estilos para legendas

Infelizmente a TTML não trabalha em conjunto com linguagens para definição de estilos como o XSLT ou o próprio CSS, mas ela possui tags e propriedades para definir e aplicar informações de estilo de modo consistente e similar à forma como fazemos com CSS. As propriedades de estilo pertencem ao namespace `tts` e podem também ser utilizadas nas tags de texto da legenda e na tag `region`. Um estilo (semelhante a uma classe CSS), é criado a partir da tag style e deve conter um id que irá utilizado para associar este estilo a outros elementos.

<pre lang="xml" class="1">&lt;styling xmlns:tts="https://www.w3.org/ns/ttml#styling">
	<!-- o estilo1 especifica o padrão para cor, fonte e alinhamento de texto -->
	&lt;style xml:id="estilo1"
		tts:color="white"
		tts:fontFamily="proportionalSansSerif"
		tts:fontSize="22px"
		tts:textAlign="center"
	/>
	

<!-- Estilo alternativo baseado no estilo1, ou seja, utilizando as mesmas propriedades mas mudando a cor para amarelo -->
	

<style xml:id="estilo2" style="estilo1" tts:color="yellow" />

<!-- Outro estilo baseado no estilo1, mas alterando o alinhamento do texto para a direita -->
	

<style xml:id="estilo1Direita" style="estilo1" tts:textAlign="end" />

<!-- Estilo baseado em estilo2 mas alterando o alinhamento do texto para a esquerda -->
	

<style xml:id="estilo2Esquerda" style="estilo2" tts:textAlign="start" />
&lt;/styling>
</pre>

As opções de alinhamento de texto são um pouco diferentes do convencional. Com exceção do center, o alinhamento à esquerda é definido como _start_ e à direita como _end_. Outras propriedades de formatação:

  * **tts:backgroundColor:** aceita valores hexadecimais, RGB e cores por nome
  * **tts:displayAlign:** aplicável somente à `region`, define o alinhamento do bloco de conteúdo de forma semelhante ao _float_ em CSS, porém tem como valores `before` (esquerda), `center`, `after` (direita)
  * **tts:extent:** aplicável somente à raiz do documento DFXP (`tt`) e à `region`, é utilizado para especificar largura e altura de uma region
  * **tts:fontStyle:** aceita valores como `italic<em> </em>`e `oblique`
  * **tts:fontWeight:** define o peso da fonte, aceita os valores ``Na [primeira parte do artigo][1], vimos as principais características do DFXP, uma especificação do W3C para trabalhar com legendas em vídeos do HTML5. Agora iremos conhecer a estrutura de um arquivo DFXP e detalhar o conceito de regions.

### Estrutura básica de um arquivo DFXP

Um arquivo DFXP é um arquivo baseado em XML que utiliza a linguagem _Timed Text Markup Language_ (TTML). A TTML estabelece tags e propriedades específicas para atribuir uma informação textual a um intervalo de tempo, posicionar esta informação em uma determinada região do vídeo e formatar a apresentação desta informação. Um documento TTML começa com a tag `tt` e sua estrutura básica é composta por um cabeçalho e corpo de conteúdo. O cabeçalho apresenta informações como metadata, definições de estilo e layout, enquanto o corpo de conteúdo contém as especificações dos textos associados a tempo e referenciando estilos e informações de layout.

<pre lang="xml" class="1"><tt xml:lang="" xmlns="https://www.w3.org/ns/ttml">
	
	
</tt>
</pre>

_Estrutura básica de um document TTML._

### Metadados

A seção de metadata pode conter informações como título do documento, descrição e informações de _copyright_. As tags que representam estes metadados são especificadas através do _namespace_ `ttm` (timed text metadata).

<pre lang="xml" class="1">&lt;metadata xmlns:ttm="https://www.w3.org/ns/ttml#metadata">
	&lt;ttm:title>Exemplo de documento TTML&lt;/ttm:title>
	&lt;ttm:copyright>The Authors (c) 2011&lt;/ttm:copyright>
&lt;/metadata>
</pre>

O endereço do _namespace_ `ttm` definido na tag metadata assim como o _namespace_ para estilos (`tts`), podem ser definidos logo na tag `tt`, deixando o código um pouco mais limpo e organizado.

<pre lang="xml" class="1">&lt;tt xml:lang="en"
	xmlns="https://www.w3.org/ns/ttml"
	xmlns:tts="https://www.w3.org/ns/ttml#styling"
	xmlns:ttm="https://www.w3.org/ns/ttml#metadata">
...
&lt;/tt>
</pre>

### Criando estilos para legendas

Infelizmente a TTML não trabalha em conjunto com linguagens para definição de estilos como o XSLT ou o próprio CSS, mas ela possui tags e propriedades para definir e aplicar informações de estilo de modo consistente e similar à forma como fazemos com CSS. As propriedades de estilo pertencem ao namespace `tts` e podem também ser utilizadas nas tags de texto da legenda e na tag `region`. Um estilo (semelhante a uma classe CSS), é criado a partir da tag style e deve conter um id que irá utilizado para associar este estilo a outros elementos.

<pre lang="xml" class="1">&lt;styling xmlns:tts="https://www.w3.org/ns/ttml#styling">
	<!-- o estilo1 especifica o padrão para cor, fonte e alinhamento de texto -->
	&lt;style xml:id="estilo1"
		tts:color="white"
		tts:fontFamily="proportionalSansSerif"
		tts:fontSize="22px"
		tts:textAlign="center"
	/>
	

<!-- Estilo alternativo baseado no estilo1, ou seja, utilizando as mesmas propriedades mas mudando a cor para amarelo -->
	

<style xml:id="estilo2" style="estilo1" tts:color="yellow" />

<!-- Outro estilo baseado no estilo1, mas alterando o alinhamento do texto para a direita -->
	

<style xml:id="estilo1Direita" style="estilo1" tts:textAlign="end" />

<!-- Estilo baseado em estilo2 mas alterando o alinhamento do texto para a esquerda -->
	

<style xml:id="estilo2Esquerda" style="estilo2" tts:textAlign="start" />
&lt;/styling>
</pre>

As opções de alinhamento de texto são um pouco diferentes do convencional. Com exceção do center, o alinhamento à esquerda é definido como _start_ e à direita como _end_. Outras propriedades de formatação:

  * **tts:backgroundColor:** aceita valores hexadecimais, RGB e cores por nome
  * **tts:displayAlign:** aplicável somente à `region`, define o alinhamento do bloco de conteúdo de forma semelhante ao _float_ em CSS, porém tem como valores `before` (esquerda), `center`, `after` (direita)
  * **tts:extent:** aplicável somente à raiz do documento DFXP (`tt`) e à `region`, é utilizado para especificar largura e altura de uma region
  * **tts:fontStyle:** aceita valores como `italic<em> </em>`e `oblique`
  * **tts:fontWeight:** define o peso da fonte, aceita os valores`` e `bold`
  * **tts:lineHeight:** altura da linha, aceita os valores normal ou uma altura especificada em uma unidade de medida
  * **tts:opacity:** aplicável somente à tag `region`, define transparência
  * **tts:origin:** especifica as coordenadas x e y de origem de uma `region`
  * **tts:overflow:** define o comportamento de uma `region` quando o conteúdo estoura o espaço disponível. Aceita os valores `visible` e `hidden`
  * **tts:padding:** espaçamento interno de uma `region`, aceita valores da mesma forma que a propriedade``` do CSS
  * **tts:showBackground:** define quando o plano de fundo de uma ````Na [primeira parte do artigo][1], vimos as principais características do DFXP, uma especificação do W3C para trabalhar com legendas em vídeos do HTML5. Agora iremos conhecer a estrutura de um arquivo DFXP e detalhar o conceito de regions.

### Estrutura básica de um arquivo DFXP

Um arquivo DFXP é um arquivo baseado em XML que utiliza a linguagem _Timed Text Markup Language_ (TTML). A TTML estabelece tags e propriedades específicas para atribuir uma informação textual a um intervalo de tempo, posicionar esta informação em uma determinada região do vídeo e formatar a apresentação desta informação. Um documento TTML começa com a tag `tt` e sua estrutura básica é composta por um cabeçalho e corpo de conteúdo. O cabeçalho apresenta informações como metadata, definições de estilo e layout, enquanto o corpo de conteúdo contém as especificações dos textos associados a tempo e referenciando estilos e informações de layout.

<pre lang="xml" class="1"><tt xml:lang="" xmlns="https://www.w3.org/ns/ttml">
	
	
</tt>
</pre>

_Estrutura básica de um document TTML._

### Metadados

A seção de metadata pode conter informações como título do documento, descrição e informações de _copyright_. As tags que representam estes metadados são especificadas através do _namespace_ `ttm` (timed text metadata).

<pre lang="xml" class="1">&lt;metadata xmlns:ttm="https://www.w3.org/ns/ttml#metadata">
	&lt;ttm:title>Exemplo de documento TTML&lt;/ttm:title>
	&lt;ttm:copyright>The Authors (c) 2011&lt;/ttm:copyright>
&lt;/metadata>
</pre>

O endereço do _namespace_ `ttm` definido na tag metadata assim como o _namespace_ para estilos (`tts`), podem ser definidos logo na tag `tt`, deixando o código um pouco mais limpo e organizado.

<pre lang="xml" class="1">&lt;tt xml:lang="en"
	xmlns="https://www.w3.org/ns/ttml"
	xmlns:tts="https://www.w3.org/ns/ttml#styling"
	xmlns:ttm="https://www.w3.org/ns/ttml#metadata">
...
&lt;/tt>
</pre>

### Criando estilos para legendas

Infelizmente a TTML não trabalha em conjunto com linguagens para definição de estilos como o XSLT ou o próprio CSS, mas ela possui tags e propriedades para definir e aplicar informações de estilo de modo consistente e similar à forma como fazemos com CSS. As propriedades de estilo pertencem ao namespace `tts` e podem também ser utilizadas nas tags de texto da legenda e na tag `region`. Um estilo (semelhante a uma classe CSS), é criado a partir da tag style e deve conter um id que irá utilizado para associar este estilo a outros elementos.

<pre lang="xml" class="1">&lt;styling xmlns:tts="https://www.w3.org/ns/ttml#styling">
	<!-- o estilo1 especifica o padrão para cor, fonte e alinhamento de texto -->
	&lt;style xml:id="estilo1"
		tts:color="white"
		tts:fontFamily="proportionalSansSerif"
		tts:fontSize="22px"
		tts:textAlign="center"
	/>
	

<!-- Estilo alternativo baseado no estilo1, ou seja, utilizando as mesmas propriedades mas mudando a cor para amarelo -->
	

<style xml:id="estilo2" style="estilo1" tts:color="yellow" />

<!-- Outro estilo baseado no estilo1, mas alterando o alinhamento do texto para a direita -->
	

<style xml:id="estilo1Direita" style="estilo1" tts:textAlign="end" />

<!-- Estilo baseado em estilo2 mas alterando o alinhamento do texto para a esquerda -->
	

<style xml:id="estilo2Esquerda" style="estilo2" tts:textAlign="start" />
&lt;/styling>
</pre>

As opções de alinhamento de texto são um pouco diferentes do convencional. Com exceção do center, o alinhamento à esquerda é definido como _start_ e à direita como _end_. Outras propriedades de formatação:

  * **tts:backgroundColor:** aceita valores hexadecimais, RGB e cores por nome
  * **tts:displayAlign:** aplicável somente à `region`, define o alinhamento do bloco de conteúdo de forma semelhante ao _float_ em CSS, porém tem como valores `before` (esquerda), `center`, `after` (direita)
  * **tts:extent:** aplicável somente à raiz do documento DFXP (`tt`) e à `region`, é utilizado para especificar largura e altura de uma region
  * **tts:fontStyle:** aceita valores como `italic<em> </em>`e `oblique`
  * **tts:fontWeight:** define o peso da fonte, aceita os valores ``Na [primeira parte do artigo][1], vimos as principais características do DFXP, uma especificação do W3C para trabalhar com legendas em vídeos do HTML5. Agora iremos conhecer a estrutura de um arquivo DFXP e detalhar o conceito de regions.

### Estrutura básica de um arquivo DFXP

Um arquivo DFXP é um arquivo baseado em XML que utiliza a linguagem _Timed Text Markup Language_ (TTML). A TTML estabelece tags e propriedades específicas para atribuir uma informação textual a um intervalo de tempo, posicionar esta informação em uma determinada região do vídeo e formatar a apresentação desta informação. Um documento TTML começa com a tag `tt` e sua estrutura básica é composta por um cabeçalho e corpo de conteúdo. O cabeçalho apresenta informações como metadata, definições de estilo e layout, enquanto o corpo de conteúdo contém as especificações dos textos associados a tempo e referenciando estilos e informações de layout.

<pre lang="xml" class="1"><tt xml:lang="" xmlns="https://www.w3.org/ns/ttml">
	
	
</tt>
</pre>

_Estrutura básica de um document TTML._

### Metadados

A seção de metadata pode conter informações como título do documento, descrição e informações de _copyright_. As tags que representam estes metadados são especificadas através do _namespace_ `ttm` (timed text metadata).

<pre lang="xml" class="1">&lt;metadata xmlns:ttm="https://www.w3.org/ns/ttml#metadata">
	&lt;ttm:title>Exemplo de documento TTML&lt;/ttm:title>
	&lt;ttm:copyright>The Authors (c) 2011&lt;/ttm:copyright>
&lt;/metadata>
</pre>

O endereço do _namespace_ `ttm` definido na tag metadata assim como o _namespace_ para estilos (`tts`), podem ser definidos logo na tag `tt`, deixando o código um pouco mais limpo e organizado.

<pre lang="xml" class="1">&lt;tt xml:lang="en"
	xmlns="https://www.w3.org/ns/ttml"
	xmlns:tts="https://www.w3.org/ns/ttml#styling"
	xmlns:ttm="https://www.w3.org/ns/ttml#metadata">
...
&lt;/tt>
</pre>

### Criando estilos para legendas

Infelizmente a TTML não trabalha em conjunto com linguagens para definição de estilos como o XSLT ou o próprio CSS, mas ela possui tags e propriedades para definir e aplicar informações de estilo de modo consistente e similar à forma como fazemos com CSS. As propriedades de estilo pertencem ao namespace `tts` e podem também ser utilizadas nas tags de texto da legenda e na tag `region`. Um estilo (semelhante a uma classe CSS), é criado a partir da tag style e deve conter um id que irá utilizado para associar este estilo a outros elementos.

<pre lang="xml" class="1">&lt;styling xmlns:tts="https://www.w3.org/ns/ttml#styling">
	<!-- o estilo1 especifica o padrão para cor, fonte e alinhamento de texto -->
	&lt;style xml:id="estilo1"
		tts:color="white"
		tts:fontFamily="proportionalSansSerif"
		tts:fontSize="22px"
		tts:textAlign="center"
	/>
	

<!-- Estilo alternativo baseado no estilo1, ou seja, utilizando as mesmas propriedades mas mudando a cor para amarelo -->
	

<style xml:id="estilo2" style="estilo1" tts:color="yellow" />

<!-- Outro estilo baseado no estilo1, mas alterando o alinhamento do texto para a direita -->
	

<style xml:id="estilo1Direita" style="estilo1" tts:textAlign="end" />

<!-- Estilo baseado em estilo2 mas alterando o alinhamento do texto para a esquerda -->
	

<style xml:id="estilo2Esquerda" style="estilo2" tts:textAlign="start" />
&lt;/styling>
</pre>

As opções de alinhamento de texto são um pouco diferentes do convencional. Com exceção do center, o alinhamento à esquerda é definido como _start_ e à direita como _end_. Outras propriedades de formatação:

  * **tts:backgroundColor:** aceita valores hexadecimais, RGB e cores por nome
  * **tts:displayAlign:** aplicável somente à `region`, define o alinhamento do bloco de conteúdo de forma semelhante ao _float_ em CSS, porém tem como valores `before` (esquerda), `center`, `after` (direita)
  * **tts:extent:** aplicável somente à raiz do documento DFXP (`tt`) e à `region`, é utilizado para especificar largura e altura de uma region
  * **tts:fontStyle:** aceita valores como `italic<em> </em>`e `oblique`
  * **tts:fontWeight:** define o peso da fonte, aceita os valores`` e `bold`
  * **tts:lineHeight:** altura da linha, aceita os valores normal ou uma altura especificada em uma unidade de medida
  * **tts:opacity:** aplicável somente à tag `region`, define transparência
  * **tts:origin:** especifica as coordenadas x e y de origem de uma `region`
  * **tts:overflow:** define o comportamento de uma `region` quando o conteúdo estoura o espaço disponível. Aceita os valores `visible` e `hidden`
  * **tts:padding:** espaçamento interno de uma `region`, aceita valores da mesma forma que a propriedade ```Na [primeira parte do artigo][1], vimos as principais características do DFXP, uma especificação do W3C para trabalhar com legendas em vídeos do HTML5. Agora iremos conhecer a estrutura de um arquivo DFXP e detalhar o conceito de regions.

### Estrutura básica de um arquivo DFXP

Um arquivo DFXP é um arquivo baseado em XML que utiliza a linguagem _Timed Text Markup Language_ (TTML). A TTML estabelece tags e propriedades específicas para atribuir uma informação textual a um intervalo de tempo, posicionar esta informação em uma determinada região do vídeo e formatar a apresentação desta informação. Um documento TTML começa com a tag `tt` e sua estrutura básica é composta por um cabeçalho e corpo de conteúdo. O cabeçalho apresenta informações como metadata, definições de estilo e layout, enquanto o corpo de conteúdo contém as especificações dos textos associados a tempo e referenciando estilos e informações de layout.

<pre lang="xml" class="1"><tt xml:lang="" xmlns="https://www.w3.org/ns/ttml">
	
	
</tt>
</pre>

_Estrutura básica de um document TTML._

### Metadados

A seção de metadata pode conter informações como título do documento, descrição e informações de _copyright_. As tags que representam estes metadados são especificadas através do _namespace_ `ttm` (timed text metadata).

<pre lang="xml" class="1">&lt;metadata xmlns:ttm="https://www.w3.org/ns/ttml#metadata">
	&lt;ttm:title>Exemplo de documento TTML&lt;/ttm:title>
	&lt;ttm:copyright>The Authors (c) 2011&lt;/ttm:copyright>
&lt;/metadata>
</pre>

O endereço do _namespace_ `ttm` definido na tag metadata assim como o _namespace_ para estilos (`tts`), podem ser definidos logo na tag `tt`, deixando o código um pouco mais limpo e organizado.

<pre lang="xml" class="1">&lt;tt xml:lang="en"
	xmlns="https://www.w3.org/ns/ttml"
	xmlns:tts="https://www.w3.org/ns/ttml#styling"
	xmlns:ttm="https://www.w3.org/ns/ttml#metadata">
...
&lt;/tt>
</pre>

### Criando estilos para legendas

Infelizmente a TTML não trabalha em conjunto com linguagens para definição de estilos como o XSLT ou o próprio CSS, mas ela possui tags e propriedades para definir e aplicar informações de estilo de modo consistente e similar à forma como fazemos com CSS. As propriedades de estilo pertencem ao namespace `tts` e podem também ser utilizadas nas tags de texto da legenda e na tag `region`. Um estilo (semelhante a uma classe CSS), é criado a partir da tag style e deve conter um id que irá utilizado para associar este estilo a outros elementos.

<pre lang="xml" class="1">&lt;styling xmlns:tts="https://www.w3.org/ns/ttml#styling">
	<!-- o estilo1 especifica o padrão para cor, fonte e alinhamento de texto -->
	&lt;style xml:id="estilo1"
		tts:color="white"
		tts:fontFamily="proportionalSansSerif"
		tts:fontSize="22px"
		tts:textAlign="center"
	/>
	

<!-- Estilo alternativo baseado no estilo1, ou seja, utilizando as mesmas propriedades mas mudando a cor para amarelo -->
	

<style xml:id="estilo2" style="estilo1" tts:color="yellow" />

<!-- Outro estilo baseado no estilo1, mas alterando o alinhamento do texto para a direita -->
	

<style xml:id="estilo1Direita" style="estilo1" tts:textAlign="end" />

<!-- Estilo baseado em estilo2 mas alterando o alinhamento do texto para a esquerda -->
	

<style xml:id="estilo2Esquerda" style="estilo2" tts:textAlign="start" />
&lt;/styling>
</pre>

As opções de alinhamento de texto são um pouco diferentes do convencional. Com exceção do center, o alinhamento à esquerda é definido como _start_ e à direita como _end_. Outras propriedades de formatação:

  * **tts:backgroundColor:** aceita valores hexadecimais, RGB e cores por nome
  * **tts:displayAlign:** aplicável somente à `region`, define o alinhamento do bloco de conteúdo de forma semelhante ao _float_ em CSS, porém tem como valores `before` (esquerda), `center`, `after` (direita)
  * **tts:extent:** aplicável somente à raiz do documento DFXP (`tt`) e à `region`, é utilizado para especificar largura e altura de uma region
  * **tts:fontStyle:** aceita valores como `italic<em> </em>`e `oblique`
  * **tts:fontWeight:** define o peso da fonte, aceita os valores ``Na [primeira parte do artigo][1], vimos as principais características do DFXP, uma especificação do W3C para trabalhar com legendas em vídeos do HTML5. Agora iremos conhecer a estrutura de um arquivo DFXP e detalhar o conceito de regions.

### Estrutura básica de um arquivo DFXP

Um arquivo DFXP é um arquivo baseado em XML que utiliza a linguagem _Timed Text Markup Language_ (TTML). A TTML estabelece tags e propriedades específicas para atribuir uma informação textual a um intervalo de tempo, posicionar esta informação em uma determinada região do vídeo e formatar a apresentação desta informação. Um documento TTML começa com a tag `tt` e sua estrutura básica é composta por um cabeçalho e corpo de conteúdo. O cabeçalho apresenta informações como metadata, definições de estilo e layout, enquanto o corpo de conteúdo contém as especificações dos textos associados a tempo e referenciando estilos e informações de layout.

<pre lang="xml" class="1"><tt xml:lang="" xmlns="https://www.w3.org/ns/ttml">
	
	
</tt>
</pre>

_Estrutura básica de um document TTML._

### Metadados

A seção de metadata pode conter informações como título do documento, descrição e informações de _copyright_. As tags que representam estes metadados são especificadas através do _namespace_ `ttm` (timed text metadata).

<pre lang="xml" class="1">&lt;metadata xmlns:ttm="https://www.w3.org/ns/ttml#metadata">
	&lt;ttm:title>Exemplo de documento TTML&lt;/ttm:title>
	&lt;ttm:copyright>The Authors (c) 2011&lt;/ttm:copyright>
&lt;/metadata>
</pre>

O endereço do _namespace_ `ttm` definido na tag metadata assim como o _namespace_ para estilos (`tts`), podem ser definidos logo na tag `tt`, deixando o código um pouco mais limpo e organizado.

<pre lang="xml" class="1">&lt;tt xml:lang="en"
	xmlns="https://www.w3.org/ns/ttml"
	xmlns:tts="https://www.w3.org/ns/ttml#styling"
	xmlns:ttm="https://www.w3.org/ns/ttml#metadata">
...
&lt;/tt>
</pre>

### Criando estilos para legendas

Infelizmente a TTML não trabalha em conjunto com linguagens para definição de estilos como o XSLT ou o próprio CSS, mas ela possui tags e propriedades para definir e aplicar informações de estilo de modo consistente e similar à forma como fazemos com CSS. As propriedades de estilo pertencem ao namespace `tts` e podem também ser utilizadas nas tags de texto da legenda e na tag `region`. Um estilo (semelhante a uma classe CSS), é criado a partir da tag style e deve conter um id que irá utilizado para associar este estilo a outros elementos.

<pre lang="xml" class="1">&lt;styling xmlns:tts="https://www.w3.org/ns/ttml#styling">
	<!-- o estilo1 especifica o padrão para cor, fonte e alinhamento de texto -->
	&lt;style xml:id="estilo1"
		tts:color="white"
		tts:fontFamily="proportionalSansSerif"
		tts:fontSize="22px"
		tts:textAlign="center"
	/>
	

<!-- Estilo alternativo baseado no estilo1, ou seja, utilizando as mesmas propriedades mas mudando a cor para amarelo -->
	

<style xml:id="estilo2" style="estilo1" tts:color="yellow" />

<!-- Outro estilo baseado no estilo1, mas alterando o alinhamento do texto para a direita -->
	

<style xml:id="estilo1Direita" style="estilo1" tts:textAlign="end" />

<!-- Estilo baseado em estilo2 mas alterando o alinhamento do texto para a esquerda -->
	

<style xml:id="estilo2Esquerda" style="estilo2" tts:textAlign="start" />
&lt;/styling>
</pre>

As opções de alinhamento de texto são um pouco diferentes do convencional. Com exceção do center, o alinhamento à esquerda é definido como _start_ e à direita como _end_. Outras propriedades de formatação:

  * **tts:backgroundColor:** aceita valores hexadecimais, RGB e cores por nome
  * **tts:displayAlign:** aplicável somente à `region`, define o alinhamento do bloco de conteúdo de forma semelhante ao _float_ em CSS, porém tem como valores `before` (esquerda), `center`, `after` (direita)
  * **tts:extent:** aplicável somente à raiz do documento DFXP (`tt`) e à `region`, é utilizado para especificar largura e altura de uma region
  * **tts:fontStyle:** aceita valores como `italic<em> </em>`e `oblique`
  * **tts:fontWeight:** define o peso da fonte, aceita os valores`` e `bold`
  * **tts:lineHeight:** altura da linha, aceita os valores normal ou uma altura especificada em uma unidade de medida
  * **tts:opacity:** aplicável somente à tag `region`, define transparência
  * **tts:origin:** especifica as coordenadas x e y de origem de uma `region`
  * **tts:overflow:** define o comportamento de uma `region` quando o conteúdo estoura o espaço disponível. Aceita os valores `visible` e `hidden`
  * **tts:padding:** espaçamento interno de uma `region`, aceita valores da mesma forma que a propriedade``` do CSS
  * **tts:showBackground:** define quando o plano de fundo de uma```` deve ser exibido. Aceita valores `always` e `whenActive`
  * **tts:textOutline:** aplica uma borda no texto. Deve conter a cor da borda, a espessura e o raio do desfoque (quanto maior, mais desfocada será a borda)

### Layout: definindo regions

Uma `region`, conforme visto anteriormente, é um espaço para a apresentação de legenda. As _regions_ do documento TTML são declararadas na tag `layout`. Uma region pode ter um estilo associado (definido previamente na tag `styling`) como também podem ter propriedades de estilo aplicadas diretamente à tag `region`.

<pre lang="xml" class="1">&lt;layout xmlns:tts="https://www.w3.org/ns/ttml#styling">
	&lt;region xml:id="legenda"
	style="estilo1"
	tts:extent="560px 62px"
	tts:padding="5px 3px"
	tts:backgroundColor="black"
	tts:displayAlign="after"
	/>
&lt;/layout>
</pre>

Exemplo de uma region com id "legenda" que utiliza o _estilo1_ e aplica outras propriedades de formatação.
  
A tag layout também precisa especificar o _namespace_ para estilos, mas se já foi declarado na tag `tt`, não há necessidade.
  
Ao contrário do que comentei no post anterior, não há obrigatoriedade de ter _regions_ com id _default_ e _overlay_, porém ao menos uma `region` deve ser especificada no documento. Caso haja apenas uma `region`, esta será considerada _default_, independente do id atribuído.
  
No [exemplo oficial do W3C][2], o documento TTML possui 7 _regions_:

  * _default:_ a região padrão, abaixo do vídeo, para a exibição das legendas;
  * _overlay:_ região que ocupa toda a área útil do vídeo e é utilizada apenas para exibir o texto que apresenta o título do vídeo;
  * _tick1_, _tick2_, _tick3_, _tick4_, _ploc_: regions menores, sem background, que são posicionadas em diferentes lugares do vídeo e são utilizadas para descrever o barulho do relógio de da torneira.

<pre lang="xml" class="1">&lt;layout>
	&lt;region xml:id="default" tts:textAlign='center' tts:backgroundColor="black" tts:color="white" tts:padding='2px' />
	&lt;region xml:id="overlay" tts:textAlign='center' tts:origin="0px 0px" tts:extent="320px 240px" tts:opacity='0.9'
		tts:backgroundColor="white" tts:color='black' tts:fontSize='150%'/>
	&lt;region xml:id="tick1" style='s1' tts:origin="100px 150px" tts:fontSize='24pt'
		tts:color="red" />
	&lt;region xml:id="tick2" style='s1' tts:origin="200px 100px" tts:fontSize='20pt'
		tts:color="yellow" />
	&lt;region xml:id="tick3" style='s1' tts:origin="130px 140px" tts:fontSize='30pt'
		tts:color="cyan" />
	&lt;region xml:id="tick4" style='s1' tts:origin="50px 50px" tts:fontSize='40pt'
		tts:color="lime" />
	&lt;region xml:id="plop" style='s1' tts:origin="100px 120px" tts:fontSize='20pt'
		tts:color="magenta" />
&lt;/layout>
</pre>

### O corpo do documento TTML

O corpo do documento tem como raiz a tag `body`, um elemento de estruturação temporal que tem a função de armazenar as sequências de conteúdo textual. Dentro do `body` são aceitas as tags:

  * **div:** uma divisão para as legendas em um agrupamento lógico. Não é obrigatório o uso de `div`, apenas se você tem vários tipos de legendas de deseja separá-las em grupos distintos. Uma `div` pode conter outras `div`s;
  * **p:** tem a mesma função da tag `p` do HTML, um paragráfo de conteúdo. É o _container_ principal para o texto de legenda;
  * **span:** tem a mesma função da tag `span` do HTML, é um elemento de linha. Pode ser utilizada para estilizar parte de um texto contido em um `p`, por exemplo, aplicar negrito, itálico, cor diferenciada, etc;
  * **br:** quebra de linha.

Todas estas tags aceitam, além dos atributos de estilo, os seguintes atributos:

  * **begin:** especifica o início do intervalo de tempo em que o elemento será exibido;
  * **dur:** especifica a duração do intervalo de tempo;
  * **end:** especifica o término do intervalo de tempo. A documentação do W3C não clarifica se é necessário ter um `begin` quando se utiliza o `end`;
  * **region**: associa o elemento a uma `region` onde será alocado o elemento;
  * **timeContainer:** especifica um contexto temporal onde os nós filhos do elemento estarão temporalmente situados. Este atributo aceita dois valores: `par` e `seq`. Se o `timeContainer` for `par`, o intervalo temporal dos nós filhos é aplicado em pararelo, ou seja, de forma simultânea no tempo. Além disso, o intervalo de tempo dos nós filhos é relativo ao intervalo de tempo do elemento pai. Se o `timeContainer` for `seq`, o intervalo temporal dos nós filhos é aplicado de forma sequencial no tempo e o intervalo de tempo dos nós filhos é relativos aos seus nós irmãos. Caso seja o primeiro nó filho, o intervalo de tempo é relatrivo ao tempo do elemento pai. Se um _container_ de elementos de tempo (ex.: uma `div` que é container para vários `p`) não especificar `timeContainer`, será considerado que o `timeContainer` é `par`;

O W3C tem uma definição específica de expressão de tempo, que pode ser _clock-time_ (hora:minuto:segundo[.frame]) ou _offset-time_ (valor ou fração seguido de unidade de medida de tempo, ex.: 1h, 15m, 10s, 0.6s).

Para exemplificar, vamos observar alguns trechos de código do exemplo do W3C:

<pre lang="xml" class="1">&lt;body timeContainer="par">
</pre>

O corpo do documento TTML define o `timeContainer` como `par`, portanto, os nós filhos serão exibidos simultaneamente e o intervalo de tempo é relativo ao `body`.

<pre lang="xml" class="1">&lt;div region="plop" begin="00:00:08.263" dur="00:00:07.639" timeContainer="seq" tts:fontFamily='Balloon, Arial Black'>
    &lt;p dur="0.4s">Plop!&lt;/p>
    &lt;p begin="0.5s" dur="0.4s">Plop!&lt;/p>
    &lt;p begin="0.5s" dur="0.4s">Plop!&lt;/p>
    &lt;p begin="0.5s" dur="0.4s">Plop!&lt;/p>
    &lt;p begin="0.5s" dur="0.4s">Plop!&lt;/p>
    &lt;p begin="0.5s" dur="0.4s">Plop!&lt;/p>
    &lt;p begin="0.5s" dur="0.4s">Plop!&lt;/p>
    &lt;p begin="0.5s" dur="0.4s">Plop!&lt;/p>
    &lt;p begin="0.5s" dur="0.4s">Plop!&lt;/p>
    &lt;p begin="0.5s" dur="0.4s">Plop!&lt;/p>
&lt;/div>
</pre>

Esta `div` agrupa uma série de legendas que serão exibidas na `region "plop"`, sendo que elas começam a ser exibidas a partir de 8s do vídeo e duram 7s, de acordo com os atributos `begin` e `dur`. Nesta `div`, o `timeContainer` é definido como `seq` e aqui valem algumas observações importantes que vocês podem reparar no vídeo. O primeiro `p`, nó filho da `div`, não possui o atributo `begin` pois nesse caso o intervalo de tempo é relativo ao elemento pai. Ele tem duração de 0.4s. Reparem que os próximos `p`s começam aos 0.5s (relativo ao `p` anterior) e também têm a duração de 0.4s, sendo exibidos sequencialmente, ou seja, em nenhum momento eles coexistem na cena. Se o atributo `begin` não estivesse especificado, elas seriam exibidas sequencialmente considerando somente o atributo `dur` sem uma definição de intervalo para ser exibida após o elemento anterior.

<pre lang="xml" class="1">&lt;div begin="00:00:16.002" dur="00:00:07.383" timeContainer="par"  tts:fontFamily='Balloon, Impact'>
      &lt;p region="tick1">Tick!&lt;/p>
      &lt;p region="tick2" begin="1s">Tick!&lt;/p>
      &lt;p region="tick3" begin="2s">Plop!&lt;/p>
      &lt;p region="plop" begin="3s" end='6s' tts:color='white'>Plop!&lt;/p>
      &lt;p region="tick4" begin="4s" end='5s'>Tick!&lt;/p>
      &lt;p region="tick4" begin="5s" tts:color='blue' tts:fontSize='50pt'>Tick!&lt;/p>
      &lt;p region="plop" begin="6s" tts:color='fuchsia' tts:fontSize='60pt'>Plop!&lt;/p>
&lt;/div>
</pre>

Esta outra `div` não possui uma associação com `region`, ela apenas agrupa os `p`s e define o intervalo inicial do tempo e a duração. Diferentemente do trecho anterior, a associação à `region` é definida em cada `p`. O `timeContainer` é definido como `par`, neste caso o atributo `begin` de cada `p` é relativo ao intervalo de tempo da `div` e podem ser exibidos simultaneamente.

E um exemplo que não utiliza o `timeContainer` (assumindo o valor `par` como _default_) e define os intervalos de tempo de início e duração diretamente nos `p`s utilizando o formato _clock-time_:

<pre lang="xml" class="1"><div region='default'>
  &lt;p begin="00:00:00.902" dur="00:00:07.104">[Clock ticking]<br />
       [<span tts:fontStyle='italic' tts:color='lime'>tick, tick, tick</span>]&lt;/p>
        &lt;p begin="00:00:08.263" dur="00:00:07.639">[Water dropping]<br />
       [<span tts:fontStyle='italic' tts:color='lime'>plop, plop, plop</span>]&lt;/p>
        &lt;p begin="00:00:16.002" dur="00:00:07.383">[Water dropping and clock ticking]<br />
       [<span tts:fontStyle='italic' tts:color='lime'>plop, plop, plop</span>]<br />
       [<span tts:fontStyle='italic' tts:color='red'>tick, tick, tick</span>]&lt;/p>
        &lt;p begin="00:00:23.485" dur="00:00:08.659">[Clock ringing]<br />
       [<span tts:fontStyle='italic' tts:fontWeight='bold' tts:color='red'>LOUD RING</span>]&lt;/p>
  ...
  
</div>
</pre>

Este é o trecho de código referente às legendas exibidas na `region "default"`. Neste exemplo também há o uso de `span</span> demonstrando trechos de legenda em um mesmo <code>p` que possui uma estilização diferenciada.

### Associando um documento DFXP a um vídeo

As legendas são associadas a um vídeo através da tag `text`. É especificado a linguagem no atributo `lang`, o que permite que a associação de múltiplos arquivos de legenda, o atributo `type="application/ttaf+xml"` e o `src` apontando o caminho do arquivo.

<pre lang="xml" class="1">&lt;text lang='en' type="application/ttaf+xml" src="ThisIsCoffee61_captions.xml">&lt;/text>
</pre>

No exemplo do W3C, também é utilizada uma API em JavaScript para permitir que todos ou a maioria dos navegadores exibam o _player_ de vídeo e as legendas. Navegadores mais recentes possuem o player nativo, mas a API garante que outros navegadores sejam capazes de executar as mesmas funções, inclusive, a exibição de legendas.

<pre lang="html" class="1"> 
   
   
  	&lt;video controls="true" width="320px" height='240px' style='margin-right: 5%;'> 
            &lt;source src="https://media.w3.org/2009/02/ThisisCo1961_tiny.ogv" type="video/ogg; codecs=&quot;theora, vorbis&quot;" /> 
            &lt;source src="https://media.w3.org/2009/02/ThisisCo1961_tiny.mp4" type="video/mp4; codecs=&quot;avc1.42E01E, mp4a.40.2&quot;" />
            &lt;text lang='en' type="application/ttaf+xml" src="ThisIsCoffee61_captions.xml">&lt;/text> 
	&lt;/video> 
	 
  

</pre>

## Para saber mais

O conteúdo deste artigo e os os exemplos foram baseados na <a title="Timed Text Authoring Format - Distributed Format Exchange Profile" href="https://www.w3.org/TR/ttaf1-dfxp/" target="_blank">documentação do W3C para a TTML e o TTAF-DFXP</a>.

 [1]: https://tableless.com.br/videos-mais-acessiveis-com-html5-parte-i
 [2]: https://www.w3.org/2009/02/ThisIsCoffee.html