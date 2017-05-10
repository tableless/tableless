---
title: 'ePub: Aprenda a criar um livro digital'
author: Dani Guerrato
type: post
date: 2012-02-01
excerpt: |
  |
    Conheça as vantagens do formato, aprenda a criar um livro do zero, descubra as melhores práticas e porquê você deve correr dos geradores automáticos.
url: /epub-aprenda-a-criar-um-livro-digital/
tweetbackscheck:
  - 1356388838
shorturls:
  - 'a:3:{s:9:"permalink";s:31:"http://tableless.com.br/?p=5346";s:7:"tinyurl";s:26:"http://tinyurl.com/7h7b62q";s:4:"isgd";s:19:"http://is.gd/5AZaDk";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 560144937
categories:
  - Artigos
  - Código
  - Mercado e Comportamento
  - Técnicas e Práticas
  - Tecnologia e Tendências
tags:
  - 2012
  - acessibilidade
  - CSS
  - CSS3
  - desenvolvimento web
  - design
  - ebook
  - ePub
  - Na Prática
  - web standards

---
## Introdução

Com a crescente popularização de tablets e leitores digitais não há dúvida de que os livros eletrônicos vieram para ficar. O formato ePub vem cada vez mais se consolidando como o padrão definitivo para eBooks. As editoras procuram profissionais especializados, mas, aqui no Brasil não existem muitos que de fato possuem o know-how necessário para desenvolver livros no padrão. Na verdade o que acontece é que as editoras estão alocando o tipo de profissional errado para a função. Um diagramador padrão, acostumado com editoração impressa via softwares visuais como Indesign vai ter problemas ao tentar lidar com linhas de código. Já um desenvolvedor front-end vai se sentir em casa já que criar e editar um livro digital é basicamente lidar com XHTML e folhas de estilo em CSS. Neste artigo vou comentar sobre as vantagens (e desvantagens) deste padrão e como com algumas poucas dicas você poderá editar um livro digital.

## Por que não usar PDF?

O PDF tem muitas vantagens. Até a sua tia que te liga toda semana para perguntar de novo como faz para ler o resultado da Megasena na internet sabe como abrir um PDF. E do ponto de vista do design é ótimo. Hey, você tem muito mais controle do layout! Você pode colocar imagens e textos como quiser sem se preocupar com nada. Exceto… Você já tentou ler um PDF em um smartphone? É simplesmente agonizante. É necessário dar zoom in e out a cada frase diferente. Ou tentar ler tudo em um tamanho de letra absurdamente pequeno…

Isto acontece por que o PDF é baseado no suporte físico de uma folha, o que simplesmente não faz sentido no mundo digital. Vou explicar: um artista que pretende pintar uma nova obra de arte precisa saber o tamanho da tela. Da mesma maneira, ao editar um livro, ou qualquer outro tipo de documento para a impressão, é necessário saber o tamanho da folha para aí então fazermos toda a diagramação. O problema é que em um ambiente digital não existe uma folha. Existe um viewport (ou seja, área de visualização) que pode ser, bem, do tamanho que o usuário quiser! Se ele for ler o seu livro no browser pode aumentar e diminuir o tamanho da janela até a resolução máxima do monitor. Ou pode optar por ler em um tablet, smartphone, eReader… Enfim, a questão é que não temos como determinar a medida de altura e largura da mesma maneira que fazíamos com o papel. E o PDF, como foi pensado para ser impresso, precisa desta medida fixa.

## Sobre o ePub

ePub é abreviação de Eletronic Publication, ou seja, Publicação Eletrônica. É um formato de livro aberto e gratuito criado pelo [IDPF][1], um fórum internacional de publicação digital. Os livros deste formato são fluidos, o que permite que a experiência de leitura seja legal em qualquer tamanho da tela, sistema operacional ou dispositivo que você escolher. Desde que você tenha um app para isto, é claro. Mas isto não é muita preocupação. Existem leitores gratuitos para quase todos os aparelhos e sistemas operacionais (se você não conhece nenhum dê uma olhadinha no final do texto). Outro aspecto bacana do ePub é o controle que ele dá ao usuário. É possível realizar buscas, navegar através de links, aumentar e diminuir o tamanho da letra, trocar as fontes, a paleta de cores, etc. Sim, isto significa que se o cara quiser ler o livro inteiro em Comics Sans ele pode! Mas se isto deixar o usuário feliz quem somos nós para dizer não?

## Como editar

Bem, agora que você já sabe como ler e por que usar, vamos descobrir como é um livro digital por dentro! Criei um livro de exemplo para utilizar neste tutorial. [Você pode baixa-lo aqui][2]. Mas qualquer outro livro que você tiver neste formato vai servir para o nosso experimento.

A extensão ePub é um formato de livros compactado. Faça um teste: renomeie o arquivo deste tutorial de meulivro.epub para meulivro.zip ou meulivro.rar que você poderá ver o conteúdo do pacote. No entanto, uma coisa importante de se ter em mente é que não são todos os softwares editores que estão preparados para salvar neste formato. Até dá para ler os arquivos XHTML separados, mas você teria que abrir manualmente, editar e recompactar a cada mudança de volta para ePub o que não seria nada prático. Felizmente existem alguns softwares como [Sigil][3] que são específicos para a edição de código de ePubs. Eles não tem um visual muito bonito mas cumprem com a função direitinho. Bem, vamos explorar os arquivos…

**Obs.** Existem outras especificações opcionais, mas vou me manter dentro do fundamental.
  
**Obs.2** Os nomes dos arquivos são case sensitive.

## A Estrutura

Vamos voltar ao nosso ePub! Ao descompactar a pasta você vai ter o seguinte:

arquivo mimetype
  
pasta META-INF

  * container.xml

pasta OEBPS

  * content.opf
  * toc.ncx
  * style.css
  * titulo.html
  * capitulo1.html
  * capitulo2.html

## Para que serve tudo isso e como eu crio sozinho?

#### Mimetype

A função do mimetype é informar ao sistema operacional qual é o tipo do arquivo. O mimetype é um simples arquivo de texto ASCII.  Para criar um mimetype basta abrir qualquer editor (ou até mesmo o bloco de notas) e escrever esta linha de código:

`application/epub+zip`

Salve como mimetype (sem nenhuma extensão) e pronto. Está feito! O mimetype é igual para qualquer ePub. Então copiar de um outro ePub da certo também.

#### Container.xml

Deve ficar dentro da pasta  META-INF. A função deste arquivo é agregar todos os outros. Bora criar um!

[cc escaped=&#8221;true&#8221;  lang=&#8221;xml&#8221;]

<?xml version=&#8221;1.0&#8243; encoding=&#8221;UTF-8&#8243;?>
  
<container xmlns=&#8221;urn:oasis:names:tc:opendocument:xmlns:container&#8221; version=&#8221;1.0&#8243;>
  
<rootfiles>
  
<rootfile full-path=&#8221;OEBPS/content.opf&#8221; media-type=&#8221;application/oebps-package+xml&#8221;/>
  
</rootfiles>
  
</container>
  
[/cc]

#### Content.opf

Descreve o conteúdo de todos os arquivos. Apesar da extensão esquisita é só criar um xml e depois salvar como .opf É composto das seguintes partes: metadata, manifest e spine. O esqueleto dele é assim:

[cc escaped=&#8221;true&#8221;  lang=&#8221;xml&#8221;]
  
<?xml version=&#8221;1.0&#8243; encoding=&#8221;UTF-8&#8243;?>
  
<package xmlns=&#8221;http://www.idpf.org/2007/opf&#8221; unique-identifier=&#8221;EPB-UUID&#8221; version=&#8221;2.0&#8243;>
  
<!&#8211; insira os parâmetros aqui &#8211;>
  
</package>
  
[/cc]

#### Metadata

Não tem muito segredo aqui. São as informações do seu livro.

**Itens obrigatórios:**

  * **title** &#8211; O título do seu livro.
  * **language** &#8211; A Lingua utilizada. Como o livro está em português eu escolhi pt-br.
  * **identifier** &#8211; Um código único para o seu livro. Pode ser o ISBN, por exemplo.

**Itens opcionais:**

  * **creator** &#8211; O criador. No caso, você.
  * **contributor** &#8211; Contribuidor
  * **publisher** &#8211; Editora
  * **subject** &#8211; Assunto
  * **description** &#8211; Descrição do livro
  * **date** &#8211; Data
  * **type** &#8211; Tipo
  * **format** &#8211; Formato
  * **source** &#8211; Fonte
  * **relation** &#8211; Relação
  * **coverage** &#8211; Cobertura
  * **rights** &#8211; O tipo de licença. Creative Commons, por exemplo.

Bem, vamos preencher nossas metadatas. Eu inseri o seguinte entre as tags package:

[cc escaped=&#8221;true&#8221;  lang=&#8221;xml&#8221;]

<metadata xmlns:opf=&#8221;http://www.idpf.org/2007/opf&#8221;
  
xmlns:dc=&#8221;http://purl.org/dc/elements/1.1/&#8221;>
  
<dc:title>Saga do primeiro ePub</dc:title>
  
<dc:creator opf:role=&#8221;aut&#8221; opf:file-as=&#8221;Dani&#8221;>Dani</dc:creator>
  
<dc:date opf:event=&#8221;original-publication&#8221;>2012</dc:date>
  
<dc:publisher>Tableless</dc:publisher>
  
<dc:date opf:event=&#8221;epub-publication&#8221;>2012-01-30</dc:date>
  
<dc:subject>Primeiro ePub</dc:subject>
  
<dc:subject>Estudos</dc:subject>
  
<dc:source>Tableless</dc:source>
  
<dc:rights>Pode copiar galera!</dc:rights>
  
<dc:identifier id=&#8221;EPB-UUID&#8221;>minhaid</dc:identifier>
  
<dc:language>pt-br</dc:language>
  
</metadata>

[/cc]

#### Manifest

É um manifesto mesmo. Deve conter (em qualquer ordem) a lista de todos os arquivos da sua publicação. Exceto mimetype, container.xml e content.opf É necessário especificar uma ID única para cada arquivo. Você pode nserir estas informações antes ou depois da metadata. O importante é que esteja também dentro da tag package. No caso do nosso livro-tutorial ficou assim:

[cc escaped=&#8221;true&#8221;  lang=&#8221;xml&#8221;]

<manifest>
  
<!&#8211; Documentos &#8211;>
  
<item id=&#8221;titulo&#8221; href=&#8221;titulo.html&#8221; media-type=&#8221;application/xhtml+xml&#8221; />
  
<item id=&#8221;capitulo1&#8243; href=&#8221;capitulo1.html&#8221; media-type=&#8221;application/xhtml+xml&#8221; />
  
<item id=&#8221;capitulo2&#8243; href=&#8221;capitulo2.html&#8221; media-type=&#8221;application/xhtml+xml&#8221; />

<!&#8211; CSS Style Sheets &#8211;>
  
<item id=&#8221;main-css&#8221; href=&#8221;style.css&#8221; media-type=&#8221;text/css&#8221;/>

<!&#8211; NCX &#8211;>
  
<item id=&#8221;ncx&#8221; href=&#8221;toc.ncx&#8221; media-type=&#8221;application/x-dtbncx+xml&#8221;/>
  
</manifest>

[/cc]

#### Spine

A espinha do livro, ou seja, a ordem de leitura. Aqui você deve colocar apenas os arquivos tipo HTML na ordem que você deseja que apareça no livro, chamando cada um pelo ID que você definiu no manifesto. Tome cuidado para não duplicar nenhum arquivo ou ID. Como você já adivinhou, deve ser inserido entre as tags package também.

[cc escaped=&#8221;true&#8221;  lang=&#8221;xml&#8221;]

<spine toc=&#8221;ncx&#8221;>
  
<itemref idref=&#8221;titulo&#8221; linear=&#8221;yes&#8221;/>
  
<itemref idref=&#8221;capitulo1&#8243; linear=&#8221;yes&#8221;/>
  
<itemref idref=&#8221;capitulo2&#8243; linear=&#8221;yes&#8221;/>
  
</spine>

[/cc]

#### toc.ncx

TOC é uma sigla para Table of Contents, ou seja, o indice do livro. Também é um arquivo xml salvo com a terminação .ncx Possui a seguinte estrutura:

**#head**

  * uid — o identificador único em content.opf
  * depth — níveis do sumário >= 1
  * totalPageCount — to 0
  * maxPageNumber — to 0

**#navMap**

O sumário em si

**#navPoint**

  * id — único do arquivo
  * playOrder —ordem de navegação (iniciando em 1)

O nosso índice ficou assim então:

[cc escaped=&#8221;true&#8221;  lang=&#8221;xml&#8221;]

<?xml version=&#8221;1.0&#8243; encoding=&#8221;UTF-8&#8243;?>
  
<!DOCTYPE ncx
  
PUBLIC &#8220;-//NISO//DTD ncx 2005-1//EN&#8221; &#8220;http://www.daisy.org/z3986/2005/ncx-2005-1.dtd&#8221;>
  
<ncx xmlns=&#8221;http://www.daisy.org/z3986/2005/ncx/&#8221; version=&#8221;2005-1&#8243;>
  
<head>
  
<meta name=&#8221;dtb:uid&#8221; content=&#8221;idtest&#8221;/>
  
<meta name=&#8221;dtb:depth&#8221; content=&#8221;3&#8243;/>
  
<meta name=&#8221;dtb:totalPageCount&#8221; content=&#8221;0&#8243;/>
  
<meta name=&#8221;dtb:maxPageNumber&#8221; content=&#8221;0&#8243;/>
  
</head>
  
<docTitle>
  
<text>Saga do primeiro ePub</text>
  
</docTitle>
  
<docAuthor>
  
<text>Dani</text>
  
</docAuthor>
  
<navMap>
  
<navPoint id=&#8221;titulo&#8221; playOrder=&#8221;1&#8243;>
  
<navLabel>
  
<text>Titulo</text>
  
</navLabel>
  
<content src=&#8221;titulo.html&#8221;/>
  
</navPoint>
  
<navPoint id=&#8221;capitulo1&#8243; playOrder=&#8221;2&#8243;>
  
<navLabel>
  
<text>Capitulo 1</text>
  
</navLabel>
  
<content src=&#8221;capitulo1.html&#8221;/>
  
</navPoint>
  
<navPoint id=&#8221;capitulo2&#8243; playOrder=&#8221;2&#8243;>
  
<navLabel>
  
<text>Capitulo 2</text>
  
</navLabel>
  
<content src=&#8221;capitulo2.html&#8221;/>
  
</navPoint>
  
</navMap>
  
</ncx>

[/cc]

&nbsp;

#### Os capítulos

É aqui que entra o livro em si. Cada capitulo deve ficar em um HTML separado. Estes arquivos não são nada diferentes de HTMLs comuns:

&nbsp;

[cc escaped=&#8221;true&#8221;  lang=&#8221;xml&#8221;]

<html xmlns=&#8221;http://www.w3.org/1999/xhtml&#8221; xml:lang=&#8221;pt&#8221;>
  
<head>
  
<meta http-equiv=&#8221;Content-Type&#8221; content=&#8221;application/xhtml+xml; charset=utf-8&#8243; />
  
<title>Capítulo 1</title>
  
<link href=&#8221;style.css&#8221; rel=&#8221;stylesheet&#8221; type=&#8221;text/css&#8221; />
  
</head>
  
<body>
  
<div>
  
<h3>Capítulo 1</h3>

<p>Hello World! Este é o primeiro capítulo do nosso livro. Yey!</p>
  
<p>Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum</p>
  
</div>
  
</body>
  
</html>

[/cc]

#### Outros tipos de arquivos:

**CSS** &#8211; Uma folha de estilos normal.
  
**Pasta images** &#8211; Aqui devem ficar as imagens do livro. Formatos permitidos: jpeg, png, gif e svg+xml
  
**Pasta fonts** &#8211; Utilize esta pasta se você quiser embedar algum arquivo de fonte no seu documento. Lembre-se de utilizar sempre o formato Open Type pois alguns aplicativos de leitura não suportam True Type.

#### E agora basta compactar!

Selecione todos os arquivos e crie um arquivo compactado (pode ser .zip ou .rar). Depois é só renomear para .epub e ler no seu dispositivo favorito. Pronto! Você tem um livro digital! 🙂

## Dicas importantes para editar um ePub

#### Semântica é sua amiga

Bem, se você é leitor do Tableless provavelmente não preciso dizer isso, mas vou dizer mesmo assim! É muito importante utilizar uma estrutura semântica aqui. Tags h1 a h6 para títulos, p para parágrafos… O que você já está mais do que cansado de saber a esta altura. Evite usar br para quebrar a linhas por que sem ter o tamanho de um container é difícil determinar quando de fato vai ser necessário quebrar a linha.

#### Evite seletores complexos

Leitores digitais não são tão sofisticados quanto browsers. Mantenha o seu CSS o mais simples possível.

#### Use tamanhos relativos

Como as &#8220;páginas&#8221; do seu livro vão aumentar e diminuir de acordo com o tamanho da tela do dispositivo não utilize pixels como medida para nada. Lembre-se: EM para texto e margens, porcentagens para figura. Isto vai garantir que o seu livro continue proporcional e escalável. E o seu leitor feliz!

#### Tamanho é Documento

Não use apenas um documento XHTML para o livro todo. A recomendação é que os capítulos tenham menos de 300k cada. Mais do que isto pode deixar alguns leitores, como o iBooks por exemplo, muito lentos! A razão é que estes apps consideram cada capítulo como um bloco de texto diferente. Se você colocar tudo em um documento só o aplicativo vai carregar tudo de uma vez a cada acesso.

Outra dica é tentar usar sempre imagens otimizadas para a web e com uma resolução não maior do que 1200 x 1600px.

#### Não pire muito na escolha de fontes

Evite usar fontes fora do padrão websafe. Você pode embedar fontes Open Type utilizando a propriedade @font-face mas isto não significa que voce deve. Para começar não são todos os leitores que aceitam isto e no final o seu arquivo pode ficar pesado demais e travar. E muitas vezes pode ser um trabalho extra inútil já que o seu usuário pode muito facilmente trocar de fonte. Se mesmo assim você quiser usar não escolha mais do que dois ou três tipos.

## Edição visual

Sim. Existem alguns softwares que podem gerar o livro para você. O Adobe InDesign faz isto, o Pages do Mac… Mas falando sério: não vale a pena. O código vai ficar sujo e no final você vai ter que corrigir vários bugs. É como se você estivesse utilizando um editor &#8220;What you see is what you get&#8221; para fazer um site. Acho que vocês entendem o drama. Mas… se você for realmente caminhar por esta estrada escura tenha algumas coisas em mente:

  * Se você está acostumado com editoração nestes programas é preciso mudar alguns paradigmas. Esqueça páginas mestras, hifenização, numeração, pé de página… você não precisa se preocupar mais com estas coisas em um formato digital.
  * Crie estilos específicos para o que é título, parágrafo, etc e não esqueça de importa-los na hora de salvar o arquivo.
  * Cuidado ao gerar o TOC (table of contents, ou seja, o índice). Se você colocar mais de dois subniveis pode dar problemas de compatibilidade com alguns programas e o seu livro simplesmente não abrir.
  * Lembre-se que todas as imagens precisam estar ancoradas para que fluam juntamente com o texto.
  * Determine quebras de capítulos. No caso do InDesign, salve cada parte do livro em um arquivo diferente. Depois junte todos os arquivos em um formato &#8220;book&#8221;.

## E quanto ao formato iBook da Apple?

A Apple lançou recentemente um software gratuito chamado iBooks Autor para a criação visual de livros digitais. Os livros no formato iBook são bem interativos, permitindo a implementação de elementos multimidia como videos (coisa que ainda está engatinhando no formato ePub). Com um &#8220;pequeno&#8221; porém. Sem muito alarde nos termos de serviço a Apple colocou uma clausula de exclusividade para livros comerciais. Ou seja, se você utilizar o software e vender o seu livro através da iBook Store não poderá vender em mais nenhum lugar. Sem contar que o programa é exclusivo para Mac.

## Fique longe dos conversores automáticos!

Existem alguns softwares ainda que prometem converter de PDF para ePub. Fique longe deles! Sério. Eles são ainda piores que os editores visuais. Um software não consegue interpretar um livro da mesma maneira que um ser humano a menos que você diga a ele o que fazer. Se você não determinar &#8220;ei, isto é um título&#8221; ele não tem como fazer este tipo de decisão por você.

Os PDFs estão presos a um tamanho fixo, lembra? O que significa que as palavras precisam ser hifenizadas. Se você converter automaticamente (além do seu código ser a coisa menos semântica desde os sites feitos em tabelas) os hífens vão continuar lá, criando divisões no me-io das pala-vras on-de não pre-cisava! Pense nos números das páginas… se o texto flui isso significa que um mesmo livro pode (e vai) ter uma numeração diferente de acordo com o aparelho utilizado. Mas no caso da conversão automática os números no pdf vão continuar lá. Os títulos provavelmente vão estar errados também. Fora que muitos deixam marcas como &#8220;convertido pelo programa XYZ&#8221; em todas as páginas do livro.

## Links úteis

  * [## Introdução

Com a crescente popularização de tablets e leitores digitais não há dúvida de que os livros eletrônicos vieram para ficar. O formato ePub vem cada vez mais se consolidando como o padrão definitivo para eBooks. As editoras procuram profissionais especializados, mas, aqui no Brasil não existem muitos que de fato possuem o know-how necessário para desenvolver livros no padrão. Na verdade o que acontece é que as editoras estão alocando o tipo de profissional errado para a função. Um diagramador padrão, acostumado com editoração impressa via softwares visuais como Indesign vai ter problemas ao tentar lidar com linhas de código. Já um desenvolvedor front-end vai se sentir em casa já que criar e editar um livro digital é basicamente lidar com XHTML e folhas de estilo em CSS. Neste artigo vou comentar sobre as vantagens (e desvantagens) deste padrão e como com algumas poucas dicas você poderá editar um livro digital.

## Por que não usar PDF?

O PDF tem muitas vantagens. Até a sua tia que te liga toda semana para perguntar de novo como faz para ler o resultado da Megasena na internet sabe como abrir um PDF. E do ponto de vista do design é ótimo. Hey, você tem muito mais controle do layout! Você pode colocar imagens e textos como quiser sem se preocupar com nada. Exceto… Você já tentou ler um PDF em um smartphone? É simplesmente agonizante. É necessário dar zoom in e out a cada frase diferente. Ou tentar ler tudo em um tamanho de letra absurdamente pequeno…

Isto acontece por que o PDF é baseado no suporte físico de uma folha, o que simplesmente não faz sentido no mundo digital. Vou explicar: um artista que pretende pintar uma nova obra de arte precisa saber o tamanho da tela. Da mesma maneira, ao editar um livro, ou qualquer outro tipo de documento para a impressão, é necessário saber o tamanho da folha para aí então fazermos toda a diagramação. O problema é que em um ambiente digital não existe uma folha. Existe um viewport (ou seja, área de visualização) que pode ser, bem, do tamanho que o usuário quiser! Se ele for ler o seu livro no browser pode aumentar e diminuir o tamanho da janela até a resolução máxima do monitor. Ou pode optar por ler em um tablet, smartphone, eReader… Enfim, a questão é que não temos como determinar a medida de altura e largura da mesma maneira que fazíamos com o papel. E o PDF, como foi pensado para ser impresso, precisa desta medida fixa.

## Sobre o ePub

ePub é abreviação de Eletronic Publication, ou seja, Publicação Eletrônica. É um formato de livro aberto e gratuito criado pelo [IDPF][1], um fórum internacional de publicação digital. Os livros deste formato são fluidos, o que permite que a experiência de leitura seja legal em qualquer tamanho da tela, sistema operacional ou dispositivo que você escolher. Desde que você tenha um app para isto, é claro. Mas isto não é muita preocupação. Existem leitores gratuitos para quase todos os aparelhos e sistemas operacionais (se você não conhece nenhum dê uma olhadinha no final do texto). Outro aspecto bacana do ePub é o controle que ele dá ao usuário. É possível realizar buscas, navegar através de links, aumentar e diminuir o tamanho da letra, trocar as fontes, a paleta de cores, etc. Sim, isto significa que se o cara quiser ler o livro inteiro em Comics Sans ele pode! Mas se isto deixar o usuário feliz quem somos nós para dizer não?

## Como editar

Bem, agora que você já sabe como ler e por que usar, vamos descobrir como é um livro digital por dentro! Criei um livro de exemplo para utilizar neste tutorial. [Você pode baixa-lo aqui][2]. Mas qualquer outro livro que você tiver neste formato vai servir para o nosso experimento.

A extensão ePub é um formato de livros compactado. Faça um teste: renomeie o arquivo deste tutorial de meulivro.epub para meulivro.zip ou meulivro.rar que você poderá ver o conteúdo do pacote. No entanto, uma coisa importante de se ter em mente é que não são todos os softwares editores que estão preparados para salvar neste formato. Até dá para ler os arquivos XHTML separados, mas você teria que abrir manualmente, editar e recompactar a cada mudança de volta para ePub o que não seria nada prático. Felizmente existem alguns softwares como [Sigil][3] que são específicos para a edição de código de ePubs. Eles não tem um visual muito bonito mas cumprem com a função direitinho. Bem, vamos explorar os arquivos…

**Obs.** Existem outras especificações opcionais, mas vou me manter dentro do fundamental.
  
**Obs.2** Os nomes dos arquivos são case sensitive.

## A Estrutura

Vamos voltar ao nosso ePub! Ao descompactar a pasta você vai ter o seguinte:

arquivo mimetype
  
pasta META-INF

  * container.xml

pasta OEBPS

  * content.opf
  * toc.ncx
  * style.css
  * titulo.html
  * capitulo1.html
  * capitulo2.html

## Para que serve tudo isso e como eu crio sozinho?

#### Mimetype

A função do mimetype é informar ao sistema operacional qual é o tipo do arquivo. O mimetype é um simples arquivo de texto ASCII.  Para criar um mimetype basta abrir qualquer editor (ou até mesmo o bloco de notas) e escrever esta linha de código:

`application/epub+zip`

Salve como mimetype (sem nenhuma extensão) e pronto. Está feito! O mimetype é igual para qualquer ePub. Então copiar de um outro ePub da certo também.

#### Container.xml

Deve ficar dentro da pasta  META-INF. A função deste arquivo é agregar todos os outros. Bora criar um!

[cc escaped=&#8221;true&#8221;  lang=&#8221;xml&#8221;]

<?xml version=&#8221;1.0&#8243; encoding=&#8221;UTF-8&#8243;?>
  
<container xmlns=&#8221;urn:oasis:names:tc:opendocument:xmlns:container&#8221; version=&#8221;1.0&#8243;>
  
<rootfiles>
  
<rootfile full-path=&#8221;OEBPS/content.opf&#8221; media-type=&#8221;application/oebps-package+xml&#8221;/>
  
</rootfiles>
  
</container>
  
[/cc]

#### Content.opf

Descreve o conteúdo de todos os arquivos. Apesar da extensão esquisita é só criar um xml e depois salvar como .opf É composto das seguintes partes: metadata, manifest e spine. O esqueleto dele é assim:

[cc escaped=&#8221;true&#8221;  lang=&#8221;xml&#8221;]
  
<?xml version=&#8221;1.0&#8243; encoding=&#8221;UTF-8&#8243;?>
  
<package xmlns=&#8221;http://www.idpf.org/2007/opf&#8221; unique-identifier=&#8221;EPB-UUID&#8221; version=&#8221;2.0&#8243;>
  
<!&#8211; insira os parâmetros aqui &#8211;>
  
</package>
  
[/cc]

#### Metadata

Não tem muito segredo aqui. São as informações do seu livro.

**Itens obrigatórios:**

  * **title** &#8211; O título do seu livro.
  * **language** &#8211; A Lingua utilizada. Como o livro está em português eu escolhi pt-br.
  * **identifier** &#8211; Um código único para o seu livro. Pode ser o ISBN, por exemplo.

**Itens opcionais:**

  * **creator** &#8211; O criador. No caso, você.
  * **contributor** &#8211; Contribuidor
  * **publisher** &#8211; Editora
  * **subject** &#8211; Assunto
  * **description** &#8211; Descrição do livro
  * **date** &#8211; Data
  * **type** &#8211; Tipo
  * **format** &#8211; Formato
  * **source** &#8211; Fonte
  * **relation** &#8211; Relação
  * **coverage** &#8211; Cobertura
  * **rights** &#8211; O tipo de licença. Creative Commons, por exemplo.

Bem, vamos preencher nossas metadatas. Eu inseri o seguinte entre as tags package:

[cc escaped=&#8221;true&#8221;  lang=&#8221;xml&#8221;]

<metadata xmlns:opf=&#8221;http://www.idpf.org/2007/opf&#8221;
  
xmlns:dc=&#8221;http://purl.org/dc/elements/1.1/&#8221;>
  
<dc:title>Saga do primeiro ePub</dc:title>
  
<dc:creator opf:role=&#8221;aut&#8221; opf:file-as=&#8221;Dani&#8221;>Dani</dc:creator>
  
<dc:date opf:event=&#8221;original-publication&#8221;>2012</dc:date>
  
<dc:publisher>Tableless</dc:publisher>
  
<dc:date opf:event=&#8221;epub-publication&#8221;>2012-01-30</dc:date>
  
<dc:subject>Primeiro ePub</dc:subject>
  
<dc:subject>Estudos</dc:subject>
  
<dc:source>Tableless</dc:source>
  
<dc:rights>Pode copiar galera!</dc:rights>
  
<dc:identifier id=&#8221;EPB-UUID&#8221;>minhaid</dc:identifier>
  
<dc:language>pt-br</dc:language>
  
</metadata>

[/cc]

#### Manifest

É um manifesto mesmo. Deve conter (em qualquer ordem) a lista de todos os arquivos da sua publicação. Exceto mimetype, container.xml e content.opf É necessário especificar uma ID única para cada arquivo. Você pode nserir estas informações antes ou depois da metadata. O importante é que esteja também dentro da tag package. No caso do nosso livro-tutorial ficou assim:

[cc escaped=&#8221;true&#8221;  lang=&#8221;xml&#8221;]

<manifest>
  
<!&#8211; Documentos &#8211;>
  
<item id=&#8221;titulo&#8221; href=&#8221;titulo.html&#8221; media-type=&#8221;application/xhtml+xml&#8221; />
  
<item id=&#8221;capitulo1&#8243; href=&#8221;capitulo1.html&#8221; media-type=&#8221;application/xhtml+xml&#8221; />
  
<item id=&#8221;capitulo2&#8243; href=&#8221;capitulo2.html&#8221; media-type=&#8221;application/xhtml+xml&#8221; />

<!&#8211; CSS Style Sheets &#8211;>
  
<item id=&#8221;main-css&#8221; href=&#8221;style.css&#8221; media-type=&#8221;text/css&#8221;/>

<!&#8211; NCX &#8211;>
  
<item id=&#8221;ncx&#8221; href=&#8221;toc.ncx&#8221; media-type=&#8221;application/x-dtbncx+xml&#8221;/>
  
</manifest>

[/cc]

#### Spine

A espinha do livro, ou seja, a ordem de leitura. Aqui você deve colocar apenas os arquivos tipo HTML na ordem que você deseja que apareça no livro, chamando cada um pelo ID que você definiu no manifesto. Tome cuidado para não duplicar nenhum arquivo ou ID. Como você já adivinhou, deve ser inserido entre as tags package também.

[cc escaped=&#8221;true&#8221;  lang=&#8221;xml&#8221;]

<spine toc=&#8221;ncx&#8221;>
  
<itemref idref=&#8221;titulo&#8221; linear=&#8221;yes&#8221;/>
  
<itemref idref=&#8221;capitulo1&#8243; linear=&#8221;yes&#8221;/>
  
<itemref idref=&#8221;capitulo2&#8243; linear=&#8221;yes&#8221;/>
  
</spine>

[/cc]

#### toc.ncx

TOC é uma sigla para Table of Contents, ou seja, o indice do livro. Também é um arquivo xml salvo com a terminação .ncx Possui a seguinte estrutura:

**#head**

  * uid — o identificador único em content.opf
  * depth — níveis do sumário >= 1
  * totalPageCount — to 0
  * maxPageNumber — to 0

**#navMap**

O sumário em si

**#navPoint**

  * id — único do arquivo
  * playOrder —ordem de navegação (iniciando em 1)

O nosso índice ficou assim então:

[cc escaped=&#8221;true&#8221;  lang=&#8221;xml&#8221;]

<?xml version=&#8221;1.0&#8243; encoding=&#8221;UTF-8&#8243;?>
  
<!DOCTYPE ncx
  
PUBLIC &#8220;-//NISO//DTD ncx 2005-1//EN&#8221; &#8220;http://www.daisy.org/z3986/2005/ncx-2005-1.dtd&#8221;>
  
<ncx xmlns=&#8221;http://www.daisy.org/z3986/2005/ncx/&#8221; version=&#8221;2005-1&#8243;>
  
<head>
  
<meta name=&#8221;dtb:uid&#8221; content=&#8221;idtest&#8221;/>
  
<meta name=&#8221;dtb:depth&#8221; content=&#8221;3&#8243;/>
  
<meta name=&#8221;dtb:totalPageCount&#8221; content=&#8221;0&#8243;/>
  
<meta name=&#8221;dtb:maxPageNumber&#8221; content=&#8221;0&#8243;/>
  
</head>
  
<docTitle>
  
<text>Saga do primeiro ePub</text>
  
</docTitle>
  
<docAuthor>
  
<text>Dani</text>
  
</docAuthor>
  
<navMap>
  
<navPoint id=&#8221;titulo&#8221; playOrder=&#8221;1&#8243;>
  
<navLabel>
  
<text>Titulo</text>
  
</navLabel>
  
<content src=&#8221;titulo.html&#8221;/>
  
</navPoint>
  
<navPoint id=&#8221;capitulo1&#8243; playOrder=&#8221;2&#8243;>
  
<navLabel>
  
<text>Capitulo 1</text>
  
</navLabel>
  
<content src=&#8221;capitulo1.html&#8221;/>
  
</navPoint>
  
<navPoint id=&#8221;capitulo2&#8243; playOrder=&#8221;2&#8243;>
  
<navLabel>
  
<text>Capitulo 2</text>
  
</navLabel>
  
<content src=&#8221;capitulo2.html&#8221;/>
  
</navPoint>
  
</navMap>
  
</ncx>

[/cc]

&nbsp;

#### Os capítulos

É aqui que entra o livro em si. Cada capitulo deve ficar em um HTML separado. Estes arquivos não são nada diferentes de HTMLs comuns:

&nbsp;

[cc escaped=&#8221;true&#8221;  lang=&#8221;xml&#8221;]

<html xmlns=&#8221;http://www.w3.org/1999/xhtml&#8221; xml:lang=&#8221;pt&#8221;>
  
<head>
  
<meta http-equiv=&#8221;Content-Type&#8221; content=&#8221;application/xhtml+xml; charset=utf-8&#8243; />
  
<title>Capítulo 1</title>
  
<link href=&#8221;style.css&#8221; rel=&#8221;stylesheet&#8221; type=&#8221;text/css&#8221; />
  
</head>
  
<body>
  
<div>
  
<h3>Capítulo 1</h3>

<p>Hello World! Este é o primeiro capítulo do nosso livro. Yey!</p>
  
<p>Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum</p>
  
</div>
  
</body>
  
</html>

[/cc]

#### Outros tipos de arquivos:

**CSS** &#8211; Uma folha de estilos normal.
  
**Pasta images** &#8211; Aqui devem ficar as imagens do livro. Formatos permitidos: jpeg, png, gif e svg+xml
  
**Pasta fonts** &#8211; Utilize esta pasta se você quiser embedar algum arquivo de fonte no seu documento. Lembre-se de utilizar sempre o formato Open Type pois alguns aplicativos de leitura não suportam True Type.

#### E agora basta compactar!

Selecione todos os arquivos e crie um arquivo compactado (pode ser .zip ou .rar). Depois é só renomear para .epub e ler no seu dispositivo favorito. Pronto! Você tem um livro digital! 🙂

## Dicas importantes para editar um ePub

#### Semântica é sua amiga

Bem, se você é leitor do Tableless provavelmente não preciso dizer isso, mas vou dizer mesmo assim! É muito importante utilizar uma estrutura semântica aqui. Tags h1 a h6 para títulos, p para parágrafos… O que você já está mais do que cansado de saber a esta altura. Evite usar br para quebrar a linhas por que sem ter o tamanho de um container é difícil determinar quando de fato vai ser necessário quebrar a linha.

#### Evite seletores complexos

Leitores digitais não são tão sofisticados quanto browsers. Mantenha o seu CSS o mais simples possível.

#### Use tamanhos relativos

Como as &#8220;páginas&#8221; do seu livro vão aumentar e diminuir de acordo com o tamanho da tela do dispositivo não utilize pixels como medida para nada. Lembre-se: EM para texto e margens, porcentagens para figura. Isto vai garantir que o seu livro continue proporcional e escalável. E o seu leitor feliz!

#### Tamanho é Documento

Não use apenas um documento XHTML para o livro todo. A recomendação é que os capítulos tenham menos de 300k cada. Mais do que isto pode deixar alguns leitores, como o iBooks por exemplo, muito lentos! A razão é que estes apps consideram cada capítulo como um bloco de texto diferente. Se você colocar tudo em um documento só o aplicativo vai carregar tudo de uma vez a cada acesso.

Outra dica é tentar usar sempre imagens otimizadas para a web e com uma resolução não maior do que 1200 x 1600px.

#### Não pire muito na escolha de fontes

Evite usar fontes fora do padrão websafe. Você pode embedar fontes Open Type utilizando a propriedade @font-face mas isto não significa que voce deve. Para começar não são todos os leitores que aceitam isto e no final o seu arquivo pode ficar pesado demais e travar. E muitas vezes pode ser um trabalho extra inútil já que o seu usuário pode muito facilmente trocar de fonte. Se mesmo assim você quiser usar não escolha mais do que dois ou três tipos.

## Edição visual

Sim. Existem alguns softwares que podem gerar o livro para você. O Adobe InDesign faz isto, o Pages do Mac… Mas falando sério: não vale a pena. O código vai ficar sujo e no final você vai ter que corrigir vários bugs. É como se você estivesse utilizando um editor &#8220;What you see is what you get&#8221; para fazer um site. Acho que vocês entendem o drama. Mas… se você for realmente caminhar por esta estrada escura tenha algumas coisas em mente:

  * Se você está acostumado com editoração nestes programas é preciso mudar alguns paradigmas. Esqueça páginas mestras, hifenização, numeração, pé de página… você não precisa se preocupar mais com estas coisas em um formato digital.
  * Crie estilos específicos para o que é título, parágrafo, etc e não esqueça de importa-los na hora de salvar o arquivo.
  * Cuidado ao gerar o TOC (table of contents, ou seja, o índice). Se você colocar mais de dois subniveis pode dar problemas de compatibilidade com alguns programas e o seu livro simplesmente não abrir.
  * Lembre-se que todas as imagens precisam estar ancoradas para que fluam juntamente com o texto.
  * Determine quebras de capítulos. No caso do InDesign, salve cada parte do livro em um arquivo diferente. Depois junte todos os arquivos em um formato &#8220;book&#8221;.

## E quanto ao formato iBook da Apple?

A Apple lançou recentemente um software gratuito chamado iBooks Autor para a criação visual de livros digitais. Os livros no formato iBook são bem interativos, permitindo a implementação de elementos multimidia como videos (coisa que ainda está engatinhando no formato ePub). Com um &#8220;pequeno&#8221; porém. Sem muito alarde nos termos de serviço a Apple colocou uma clausula de exclusividade para livros comerciais. Ou seja, se você utilizar o software e vender o seu livro através da iBook Store não poderá vender em mais nenhum lugar. Sem contar que o programa é exclusivo para Mac.

## Fique longe dos conversores automáticos!

Existem alguns softwares ainda que prometem converter de PDF para ePub. Fique longe deles! Sério. Eles são ainda piores que os editores visuais. Um software não consegue interpretar um livro da mesma maneira que um ser humano a menos que você diga a ele o que fazer. Se você não determinar &#8220;ei, isto é um título&#8221; ele não tem como fazer este tipo de decisão por você.

Os PDFs estão presos a um tamanho fixo, lembra? O que significa que as palavras precisam ser hifenizadas. Se você converter automaticamente (além do seu código ser a coisa menos semântica desde os sites feitos em tabelas) os hífens vão continuar lá, criando divisões no me-io das pala-vras on-de não pre-cisava! Pense nos números das páginas… se o texto flui isso significa que um mesmo livro pode (e vai) ter uma numeração diferente de acordo com o aparelho utilizado. Mas no caso da conversão automática os números no pdf vão continuar lá. Os títulos provavelmente vão estar errados também. Fora que muitos deixam marcas como &#8220;convertido pelo programa XYZ&#8221; em todas as páginas do livro.

## Links úteis

  *][4] &#8211; A organização responsável pela criação do ePub. O site deles é meio confuso, mas contém bastante informação a respeito do formato.
  * [ePub Chech][5] &#8211; Validação de ePub
  * [Epub Format Construction Guide][6] &#8211; Um meta-livro bem completo sobre o assunto.

## Bibliotecas gratuitas

  * [Google Books][7]
  * [ePub Bud][8]

## Aplicativos para a Leitura

#### Mac & PC

  * [Adobe Digital Editions][9]
  * [Nook][10]

#### Linux

  * [FB Reader][11]

#### iOS

  * [iBooks][12]
  * [Stanza][13]

#### Android

  * [Aldiko][14]

#### Leitura no Browser

  * [## Introdução

Com a crescente popularização de tablets e leitores digitais não há dúvida de que os livros eletrônicos vieram para ficar. O formato ePub vem cada vez mais se consolidando como o padrão definitivo para eBooks. As editoras procuram profissionais especializados, mas, aqui no Brasil não existem muitos que de fato possuem o know-how necessário para desenvolver livros no padrão. Na verdade o que acontece é que as editoras estão alocando o tipo de profissional errado para a função. Um diagramador padrão, acostumado com editoração impressa via softwares visuais como Indesign vai ter problemas ao tentar lidar com linhas de código. Já um desenvolvedor front-end vai se sentir em casa já que criar e editar um livro digital é basicamente lidar com XHTML e folhas de estilo em CSS. Neste artigo vou comentar sobre as vantagens (e desvantagens) deste padrão e como com algumas poucas dicas você poderá editar um livro digital.

## Por que não usar PDF?

O PDF tem muitas vantagens. Até a sua tia que te liga toda semana para perguntar de novo como faz para ler o resultado da Megasena na internet sabe como abrir um PDF. E do ponto de vista do design é ótimo. Hey, você tem muito mais controle do layout! Você pode colocar imagens e textos como quiser sem se preocupar com nada. Exceto… Você já tentou ler um PDF em um smartphone? É simplesmente agonizante. É necessário dar zoom in e out a cada frase diferente. Ou tentar ler tudo em um tamanho de letra absurdamente pequeno…

Isto acontece por que o PDF é baseado no suporte físico de uma folha, o que simplesmente não faz sentido no mundo digital. Vou explicar: um artista que pretende pintar uma nova obra de arte precisa saber o tamanho da tela. Da mesma maneira, ao editar um livro, ou qualquer outro tipo de documento para a impressão, é necessário saber o tamanho da folha para aí então fazermos toda a diagramação. O problema é que em um ambiente digital não existe uma folha. Existe um viewport (ou seja, área de visualização) que pode ser, bem, do tamanho que o usuário quiser! Se ele for ler o seu livro no browser pode aumentar e diminuir o tamanho da janela até a resolução máxima do monitor. Ou pode optar por ler em um tablet, smartphone, eReader… Enfim, a questão é que não temos como determinar a medida de altura e largura da mesma maneira que fazíamos com o papel. E o PDF, como foi pensado para ser impresso, precisa desta medida fixa.

## Sobre o ePub

ePub é abreviação de Eletronic Publication, ou seja, Publicação Eletrônica. É um formato de livro aberto e gratuito criado pelo [IDPF][1], um fórum internacional de publicação digital. Os livros deste formato são fluidos, o que permite que a experiência de leitura seja legal em qualquer tamanho da tela, sistema operacional ou dispositivo que você escolher. Desde que você tenha um app para isto, é claro. Mas isto não é muita preocupação. Existem leitores gratuitos para quase todos os aparelhos e sistemas operacionais (se você não conhece nenhum dê uma olhadinha no final do texto). Outro aspecto bacana do ePub é o controle que ele dá ao usuário. É possível realizar buscas, navegar através de links, aumentar e diminuir o tamanho da letra, trocar as fontes, a paleta de cores, etc. Sim, isto significa que se o cara quiser ler o livro inteiro em Comics Sans ele pode! Mas se isto deixar o usuário feliz quem somos nós para dizer não?

## Como editar

Bem, agora que você já sabe como ler e por que usar, vamos descobrir como é um livro digital por dentro! Criei um livro de exemplo para utilizar neste tutorial. [Você pode baixa-lo aqui][2]. Mas qualquer outro livro que você tiver neste formato vai servir para o nosso experimento.

A extensão ePub é um formato de livros compactado. Faça um teste: renomeie o arquivo deste tutorial de meulivro.epub para meulivro.zip ou meulivro.rar que você poderá ver o conteúdo do pacote. No entanto, uma coisa importante de se ter em mente é que não são todos os softwares editores que estão preparados para salvar neste formato. Até dá para ler os arquivos XHTML separados, mas você teria que abrir manualmente, editar e recompactar a cada mudança de volta para ePub o que não seria nada prático. Felizmente existem alguns softwares como [Sigil][3] que são específicos para a edição de código de ePubs. Eles não tem um visual muito bonito mas cumprem com a função direitinho. Bem, vamos explorar os arquivos…

**Obs.** Existem outras especificações opcionais, mas vou me manter dentro do fundamental.
  
**Obs.2** Os nomes dos arquivos são case sensitive.

## A Estrutura

Vamos voltar ao nosso ePub! Ao descompactar a pasta você vai ter o seguinte:

arquivo mimetype
  
pasta META-INF

  * container.xml

pasta OEBPS

  * content.opf
  * toc.ncx
  * style.css
  * titulo.html
  * capitulo1.html
  * capitulo2.html

## Para que serve tudo isso e como eu crio sozinho?

#### Mimetype

A função do mimetype é informar ao sistema operacional qual é o tipo do arquivo. O mimetype é um simples arquivo de texto ASCII.  Para criar um mimetype basta abrir qualquer editor (ou até mesmo o bloco de notas) e escrever esta linha de código:

`application/epub+zip`

Salve como mimetype (sem nenhuma extensão) e pronto. Está feito! O mimetype é igual para qualquer ePub. Então copiar de um outro ePub da certo também.

#### Container.xml

Deve ficar dentro da pasta  META-INF. A função deste arquivo é agregar todos os outros. Bora criar um!

[cc escaped=&#8221;true&#8221;  lang=&#8221;xml&#8221;]

<?xml version=&#8221;1.0&#8243; encoding=&#8221;UTF-8&#8243;?>
  
<container xmlns=&#8221;urn:oasis:names:tc:opendocument:xmlns:container&#8221; version=&#8221;1.0&#8243;>
  
<rootfiles>
  
<rootfile full-path=&#8221;OEBPS/content.opf&#8221; media-type=&#8221;application/oebps-package+xml&#8221;/>
  
</rootfiles>
  
</container>
  
[/cc]

#### Content.opf

Descreve o conteúdo de todos os arquivos. Apesar da extensão esquisita é só criar um xml e depois salvar como .opf É composto das seguintes partes: metadata, manifest e spine. O esqueleto dele é assim:

[cc escaped=&#8221;true&#8221;  lang=&#8221;xml&#8221;]
  
<?xml version=&#8221;1.0&#8243; encoding=&#8221;UTF-8&#8243;?>
  
<package xmlns=&#8221;http://www.idpf.org/2007/opf&#8221; unique-identifier=&#8221;EPB-UUID&#8221; version=&#8221;2.0&#8243;>
  
<!&#8211; insira os parâmetros aqui &#8211;>
  
</package>
  
[/cc]

#### Metadata

Não tem muito segredo aqui. São as informações do seu livro.

**Itens obrigatórios:**

  * **title** &#8211; O título do seu livro.
  * **language** &#8211; A Lingua utilizada. Como o livro está em português eu escolhi pt-br.
  * **identifier** &#8211; Um código único para o seu livro. Pode ser o ISBN, por exemplo.

**Itens opcionais:**

  * **creator** &#8211; O criador. No caso, você.
  * **contributor** &#8211; Contribuidor
  * **publisher** &#8211; Editora
  * **subject** &#8211; Assunto
  * **description** &#8211; Descrição do livro
  * **date** &#8211; Data
  * **type** &#8211; Tipo
  * **format** &#8211; Formato
  * **source** &#8211; Fonte
  * **relation** &#8211; Relação
  * **coverage** &#8211; Cobertura
  * **rights** &#8211; O tipo de licença. Creative Commons, por exemplo.

Bem, vamos preencher nossas metadatas. Eu inseri o seguinte entre as tags package:

[cc escaped=&#8221;true&#8221;  lang=&#8221;xml&#8221;]

<metadata xmlns:opf=&#8221;http://www.idpf.org/2007/opf&#8221;
  
xmlns:dc=&#8221;http://purl.org/dc/elements/1.1/&#8221;>
  
<dc:title>Saga do primeiro ePub</dc:title>
  
<dc:creator opf:role=&#8221;aut&#8221; opf:file-as=&#8221;Dani&#8221;>Dani</dc:creator>
  
<dc:date opf:event=&#8221;original-publication&#8221;>2012</dc:date>
  
<dc:publisher>Tableless</dc:publisher>
  
<dc:date opf:event=&#8221;epub-publication&#8221;>2012-01-30</dc:date>
  
<dc:subject>Primeiro ePub</dc:subject>
  
<dc:subject>Estudos</dc:subject>
  
<dc:source>Tableless</dc:source>
  
<dc:rights>Pode copiar galera!</dc:rights>
  
<dc:identifier id=&#8221;EPB-UUID&#8221;>minhaid</dc:identifier>
  
<dc:language>pt-br</dc:language>
  
</metadata>

[/cc]

#### Manifest

É um manifesto mesmo. Deve conter (em qualquer ordem) a lista de todos os arquivos da sua publicação. Exceto mimetype, container.xml e content.opf É necessário especificar uma ID única para cada arquivo. Você pode nserir estas informações antes ou depois da metadata. O importante é que esteja também dentro da tag package. No caso do nosso livro-tutorial ficou assim:

[cc escaped=&#8221;true&#8221;  lang=&#8221;xml&#8221;]

<manifest>
  
<!&#8211; Documentos &#8211;>
  
<item id=&#8221;titulo&#8221; href=&#8221;titulo.html&#8221; media-type=&#8221;application/xhtml+xml&#8221; />
  
<item id=&#8221;capitulo1&#8243; href=&#8221;capitulo1.html&#8221; media-type=&#8221;application/xhtml+xml&#8221; />
  
<item id=&#8221;capitulo2&#8243; href=&#8221;capitulo2.html&#8221; media-type=&#8221;application/xhtml+xml&#8221; />

<!&#8211; CSS Style Sheets &#8211;>
  
<item id=&#8221;main-css&#8221; href=&#8221;style.css&#8221; media-type=&#8221;text/css&#8221;/>

<!&#8211; NCX &#8211;>
  
<item id=&#8221;ncx&#8221; href=&#8221;toc.ncx&#8221; media-type=&#8221;application/x-dtbncx+xml&#8221;/>
  
</manifest>

[/cc]

#### Spine

A espinha do livro, ou seja, a ordem de leitura. Aqui você deve colocar apenas os arquivos tipo HTML na ordem que você deseja que apareça no livro, chamando cada um pelo ID que você definiu no manifesto. Tome cuidado para não duplicar nenhum arquivo ou ID. Como você já adivinhou, deve ser inserido entre as tags package também.

[cc escaped=&#8221;true&#8221;  lang=&#8221;xml&#8221;]

<spine toc=&#8221;ncx&#8221;>
  
<itemref idref=&#8221;titulo&#8221; linear=&#8221;yes&#8221;/>
  
<itemref idref=&#8221;capitulo1&#8243; linear=&#8221;yes&#8221;/>
  
<itemref idref=&#8221;capitulo2&#8243; linear=&#8221;yes&#8221;/>
  
</spine>

[/cc]

#### toc.ncx

TOC é uma sigla para Table of Contents, ou seja, o indice do livro. Também é um arquivo xml salvo com a terminação .ncx Possui a seguinte estrutura:

**#head**

  * uid — o identificador único em content.opf
  * depth — níveis do sumário >= 1
  * totalPageCount — to 0
  * maxPageNumber — to 0

**#navMap**

O sumário em si

**#navPoint**

  * id — único do arquivo
  * playOrder —ordem de navegação (iniciando em 1)

O nosso índice ficou assim então:

[cc escaped=&#8221;true&#8221;  lang=&#8221;xml&#8221;]

<?xml version=&#8221;1.0&#8243; encoding=&#8221;UTF-8&#8243;?>
  
<!DOCTYPE ncx
  
PUBLIC &#8220;-//NISO//DTD ncx 2005-1//EN&#8221; &#8220;http://www.daisy.org/z3986/2005/ncx-2005-1.dtd&#8221;>
  
<ncx xmlns=&#8221;http://www.daisy.org/z3986/2005/ncx/&#8221; version=&#8221;2005-1&#8243;>
  
<head>
  
<meta name=&#8221;dtb:uid&#8221; content=&#8221;idtest&#8221;/>
  
<meta name=&#8221;dtb:depth&#8221; content=&#8221;3&#8243;/>
  
<meta name=&#8221;dtb:totalPageCount&#8221; content=&#8221;0&#8243;/>
  
<meta name=&#8221;dtb:maxPageNumber&#8221; content=&#8221;0&#8243;/>
  
</head>
  
<docTitle>
  
<text>Saga do primeiro ePub</text>
  
</docTitle>
  
<docAuthor>
  
<text>Dani</text>
  
</docAuthor>
  
<navMap>
  
<navPoint id=&#8221;titulo&#8221; playOrder=&#8221;1&#8243;>
  
<navLabel>
  
<text>Titulo</text>
  
</navLabel>
  
<content src=&#8221;titulo.html&#8221;/>
  
</navPoint>
  
<navPoint id=&#8221;capitulo1&#8243; playOrder=&#8221;2&#8243;>
  
<navLabel>
  
<text>Capitulo 1</text>
  
</navLabel>
  
<content src=&#8221;capitulo1.html&#8221;/>
  
</navPoint>
  
<navPoint id=&#8221;capitulo2&#8243; playOrder=&#8221;2&#8243;>
  
<navLabel>
  
<text>Capitulo 2</text>
  
</navLabel>
  
<content src=&#8221;capitulo2.html&#8221;/>
  
</navPoint>
  
</navMap>
  
</ncx>

[/cc]

&nbsp;

#### Os capítulos

É aqui que entra o livro em si. Cada capitulo deve ficar em um HTML separado. Estes arquivos não são nada diferentes de HTMLs comuns:

&nbsp;

[cc escaped=&#8221;true&#8221;  lang=&#8221;xml&#8221;]

<html xmlns=&#8221;http://www.w3.org/1999/xhtml&#8221; xml:lang=&#8221;pt&#8221;>
  
<head>
  
<meta http-equiv=&#8221;Content-Type&#8221; content=&#8221;application/xhtml+xml; charset=utf-8&#8243; />
  
<title>Capítulo 1</title>
  
<link href=&#8221;style.css&#8221; rel=&#8221;stylesheet&#8221; type=&#8221;text/css&#8221; />
  
</head>
  
<body>
  
<div>
  
<h3>Capítulo 1</h3>

<p>Hello World! Este é o primeiro capítulo do nosso livro. Yey!</p>
  
<p>Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum</p>
  
</div>
  
</body>
  
</html>

[/cc]

#### Outros tipos de arquivos:

**CSS** &#8211; Uma folha de estilos normal.
  
**Pasta images** &#8211; Aqui devem ficar as imagens do livro. Formatos permitidos: jpeg, png, gif e svg+xml
  
**Pasta fonts** &#8211; Utilize esta pasta se você quiser embedar algum arquivo de fonte no seu documento. Lembre-se de utilizar sempre o formato Open Type pois alguns aplicativos de leitura não suportam True Type.

#### E agora basta compactar!

Selecione todos os arquivos e crie um arquivo compactado (pode ser .zip ou .rar). Depois é só renomear para .epub e ler no seu dispositivo favorito. Pronto! Você tem um livro digital! 🙂

## Dicas importantes para editar um ePub

#### Semântica é sua amiga

Bem, se você é leitor do Tableless provavelmente não preciso dizer isso, mas vou dizer mesmo assim! É muito importante utilizar uma estrutura semântica aqui. Tags h1 a h6 para títulos, p para parágrafos… O que você já está mais do que cansado de saber a esta altura. Evite usar br para quebrar a linhas por que sem ter o tamanho de um container é difícil determinar quando de fato vai ser necessário quebrar a linha.

#### Evite seletores complexos

Leitores digitais não são tão sofisticados quanto browsers. Mantenha o seu CSS o mais simples possível.

#### Use tamanhos relativos

Como as &#8220;páginas&#8221; do seu livro vão aumentar e diminuir de acordo com o tamanho da tela do dispositivo não utilize pixels como medida para nada. Lembre-se: EM para texto e margens, porcentagens para figura. Isto vai garantir que o seu livro continue proporcional e escalável. E o seu leitor feliz!

#### Tamanho é Documento

Não use apenas um documento XHTML para o livro todo. A recomendação é que os capítulos tenham menos de 300k cada. Mais do que isto pode deixar alguns leitores, como o iBooks por exemplo, muito lentos! A razão é que estes apps consideram cada capítulo como um bloco de texto diferente. Se você colocar tudo em um documento só o aplicativo vai carregar tudo de uma vez a cada acesso.

Outra dica é tentar usar sempre imagens otimizadas para a web e com uma resolução não maior do que 1200 x 1600px.

#### Não pire muito na escolha de fontes

Evite usar fontes fora do padrão websafe. Você pode embedar fontes Open Type utilizando a propriedade @font-face mas isto não significa que voce deve. Para começar não são todos os leitores que aceitam isto e no final o seu arquivo pode ficar pesado demais e travar. E muitas vezes pode ser um trabalho extra inútil já que o seu usuário pode muito facilmente trocar de fonte. Se mesmo assim você quiser usar não escolha mais do que dois ou três tipos.

## Edição visual

Sim. Existem alguns softwares que podem gerar o livro para você. O Adobe InDesign faz isto, o Pages do Mac… Mas falando sério: não vale a pena. O código vai ficar sujo e no final você vai ter que corrigir vários bugs. É como se você estivesse utilizando um editor &#8220;What you see is what you get&#8221; para fazer um site. Acho que vocês entendem o drama. Mas… se você for realmente caminhar por esta estrada escura tenha algumas coisas em mente:

  * Se você está acostumado com editoração nestes programas é preciso mudar alguns paradigmas. Esqueça páginas mestras, hifenização, numeração, pé de página… você não precisa se preocupar mais com estas coisas em um formato digital.
  * Crie estilos específicos para o que é título, parágrafo, etc e não esqueça de importa-los na hora de salvar o arquivo.
  * Cuidado ao gerar o TOC (table of contents, ou seja, o índice). Se você colocar mais de dois subniveis pode dar problemas de compatibilidade com alguns programas e o seu livro simplesmente não abrir.
  * Lembre-se que todas as imagens precisam estar ancoradas para que fluam juntamente com o texto.
  * Determine quebras de capítulos. No caso do InDesign, salve cada parte do livro em um arquivo diferente. Depois junte todos os arquivos em um formato &#8220;book&#8221;.

## E quanto ao formato iBook da Apple?

A Apple lançou recentemente um software gratuito chamado iBooks Autor para a criação visual de livros digitais. Os livros no formato iBook são bem interativos, permitindo a implementação de elementos multimidia como videos (coisa que ainda está engatinhando no formato ePub). Com um &#8220;pequeno&#8221; porém. Sem muito alarde nos termos de serviço a Apple colocou uma clausula de exclusividade para livros comerciais. Ou seja, se você utilizar o software e vender o seu livro através da iBook Store não poderá vender em mais nenhum lugar. Sem contar que o programa é exclusivo para Mac.

## Fique longe dos conversores automáticos!

Existem alguns softwares ainda que prometem converter de PDF para ePub. Fique longe deles! Sério. Eles são ainda piores que os editores visuais. Um software não consegue interpretar um livro da mesma maneira que um ser humano a menos que você diga a ele o que fazer. Se você não determinar &#8220;ei, isto é um título&#8221; ele não tem como fazer este tipo de decisão por você.

Os PDFs estão presos a um tamanho fixo, lembra? O que significa que as palavras precisam ser hifenizadas. Se você converter automaticamente (além do seu código ser a coisa menos semântica desde os sites feitos em tabelas) os hífens vão continuar lá, criando divisões no me-io das pala-vras on-de não pre-cisava! Pense nos números das páginas… se o texto flui isso significa que um mesmo livro pode (e vai) ter uma numeração diferente de acordo com o aparelho utilizado. Mas no caso da conversão automática os números no pdf vão continuar lá. Os títulos provavelmente vão estar errados também. Fora que muitos deixam marcas como &#8220;convertido pelo programa XYZ&#8221; em todas as páginas do livro.

## Links úteis

  * [## Introdução

Com a crescente popularização de tablets e leitores digitais não há dúvida de que os livros eletrônicos vieram para ficar. O formato ePub vem cada vez mais se consolidando como o padrão definitivo para eBooks. As editoras procuram profissionais especializados, mas, aqui no Brasil não existem muitos que de fato possuem o know-how necessário para desenvolver livros no padrão. Na verdade o que acontece é que as editoras estão alocando o tipo de profissional errado para a função. Um diagramador padrão, acostumado com editoração impressa via softwares visuais como Indesign vai ter problemas ao tentar lidar com linhas de código. Já um desenvolvedor front-end vai se sentir em casa já que criar e editar um livro digital é basicamente lidar com XHTML e folhas de estilo em CSS. Neste artigo vou comentar sobre as vantagens (e desvantagens) deste padrão e como com algumas poucas dicas você poderá editar um livro digital.

## Por que não usar PDF?

O PDF tem muitas vantagens. Até a sua tia que te liga toda semana para perguntar de novo como faz para ler o resultado da Megasena na internet sabe como abrir um PDF. E do ponto de vista do design é ótimo. Hey, você tem muito mais controle do layout! Você pode colocar imagens e textos como quiser sem se preocupar com nada. Exceto… Você já tentou ler um PDF em um smartphone? É simplesmente agonizante. É necessário dar zoom in e out a cada frase diferente. Ou tentar ler tudo em um tamanho de letra absurdamente pequeno…

Isto acontece por que o PDF é baseado no suporte físico de uma folha, o que simplesmente não faz sentido no mundo digital. Vou explicar: um artista que pretende pintar uma nova obra de arte precisa saber o tamanho da tela. Da mesma maneira, ao editar um livro, ou qualquer outro tipo de documento para a impressão, é necessário saber o tamanho da folha para aí então fazermos toda a diagramação. O problema é que em um ambiente digital não existe uma folha. Existe um viewport (ou seja, área de visualização) que pode ser, bem, do tamanho que o usuário quiser! Se ele for ler o seu livro no browser pode aumentar e diminuir o tamanho da janela até a resolução máxima do monitor. Ou pode optar por ler em um tablet, smartphone, eReader… Enfim, a questão é que não temos como determinar a medida de altura e largura da mesma maneira que fazíamos com o papel. E o PDF, como foi pensado para ser impresso, precisa desta medida fixa.

## Sobre o ePub

ePub é abreviação de Eletronic Publication, ou seja, Publicação Eletrônica. É um formato de livro aberto e gratuito criado pelo [IDPF][1], um fórum internacional de publicação digital. Os livros deste formato são fluidos, o que permite que a experiência de leitura seja legal em qualquer tamanho da tela, sistema operacional ou dispositivo que você escolher. Desde que você tenha um app para isto, é claro. Mas isto não é muita preocupação. Existem leitores gratuitos para quase todos os aparelhos e sistemas operacionais (se você não conhece nenhum dê uma olhadinha no final do texto). Outro aspecto bacana do ePub é o controle que ele dá ao usuário. É possível realizar buscas, navegar através de links, aumentar e diminuir o tamanho da letra, trocar as fontes, a paleta de cores, etc. Sim, isto significa que se o cara quiser ler o livro inteiro em Comics Sans ele pode! Mas se isto deixar o usuário feliz quem somos nós para dizer não?

## Como editar

Bem, agora que você já sabe como ler e por que usar, vamos descobrir como é um livro digital por dentro! Criei um livro de exemplo para utilizar neste tutorial. [Você pode baixa-lo aqui][2]. Mas qualquer outro livro que você tiver neste formato vai servir para o nosso experimento.

A extensão ePub é um formato de livros compactado. Faça um teste: renomeie o arquivo deste tutorial de meulivro.epub para meulivro.zip ou meulivro.rar que você poderá ver o conteúdo do pacote. No entanto, uma coisa importante de se ter em mente é que não são todos os softwares editores que estão preparados para salvar neste formato. Até dá para ler os arquivos XHTML separados, mas você teria que abrir manualmente, editar e recompactar a cada mudança de volta para ePub o que não seria nada prático. Felizmente existem alguns softwares como [Sigil][3] que são específicos para a edição de código de ePubs. Eles não tem um visual muito bonito mas cumprem com a função direitinho. Bem, vamos explorar os arquivos…

**Obs.** Existem outras especificações opcionais, mas vou me manter dentro do fundamental.
  
**Obs.2** Os nomes dos arquivos são case sensitive.

## A Estrutura

Vamos voltar ao nosso ePub! Ao descompactar a pasta você vai ter o seguinte:

arquivo mimetype
  
pasta META-INF

  * container.xml

pasta OEBPS

  * content.opf
  * toc.ncx
  * style.css
  * titulo.html
  * capitulo1.html
  * capitulo2.html

## Para que serve tudo isso e como eu crio sozinho?

#### Mimetype

A função do mimetype é informar ao sistema operacional qual é o tipo do arquivo. O mimetype é um simples arquivo de texto ASCII.  Para criar um mimetype basta abrir qualquer editor (ou até mesmo o bloco de notas) e escrever esta linha de código:

`application/epub+zip`

Salve como mimetype (sem nenhuma extensão) e pronto. Está feito! O mimetype é igual para qualquer ePub. Então copiar de um outro ePub da certo também.

#### Container.xml

Deve ficar dentro da pasta  META-INF. A função deste arquivo é agregar todos os outros. Bora criar um!

[cc escaped=&#8221;true&#8221;  lang=&#8221;xml&#8221;]

<?xml version=&#8221;1.0&#8243; encoding=&#8221;UTF-8&#8243;?>
  
<container xmlns=&#8221;urn:oasis:names:tc:opendocument:xmlns:container&#8221; version=&#8221;1.0&#8243;>
  
<rootfiles>
  
<rootfile full-path=&#8221;OEBPS/content.opf&#8221; media-type=&#8221;application/oebps-package+xml&#8221;/>
  
</rootfiles>
  
</container>
  
[/cc]

#### Content.opf

Descreve o conteúdo de todos os arquivos. Apesar da extensão esquisita é só criar um xml e depois salvar como .opf É composto das seguintes partes: metadata, manifest e spine. O esqueleto dele é assim:

[cc escaped=&#8221;true&#8221;  lang=&#8221;xml&#8221;]
  
<?xml version=&#8221;1.0&#8243; encoding=&#8221;UTF-8&#8243;?>
  
<package xmlns=&#8221;http://www.idpf.org/2007/opf&#8221; unique-identifier=&#8221;EPB-UUID&#8221; version=&#8221;2.0&#8243;>
  
<!&#8211; insira os parâmetros aqui &#8211;>
  
</package>
  
[/cc]

#### Metadata

Não tem muito segredo aqui. São as informações do seu livro.

**Itens obrigatórios:**

  * **title** &#8211; O título do seu livro.
  * **language** &#8211; A Lingua utilizada. Como o livro está em português eu escolhi pt-br.
  * **identifier** &#8211; Um código único para o seu livro. Pode ser o ISBN, por exemplo.

**Itens opcionais:**

  * **creator** &#8211; O criador. No caso, você.
  * **contributor** &#8211; Contribuidor
  * **publisher** &#8211; Editora
  * **subject** &#8211; Assunto
  * **description** &#8211; Descrição do livro
  * **date** &#8211; Data
  * **type** &#8211; Tipo
  * **format** &#8211; Formato
  * **source** &#8211; Fonte
  * **relation** &#8211; Relação
  * **coverage** &#8211; Cobertura
  * **rights** &#8211; O tipo de licença. Creative Commons, por exemplo.

Bem, vamos preencher nossas metadatas. Eu inseri o seguinte entre as tags package:

[cc escaped=&#8221;true&#8221;  lang=&#8221;xml&#8221;]

<metadata xmlns:opf=&#8221;http://www.idpf.org/2007/opf&#8221;
  
xmlns:dc=&#8221;http://purl.org/dc/elements/1.1/&#8221;>
  
<dc:title>Saga do primeiro ePub</dc:title>
  
<dc:creator opf:role=&#8221;aut&#8221; opf:file-as=&#8221;Dani&#8221;>Dani</dc:creator>
  
<dc:date opf:event=&#8221;original-publication&#8221;>2012</dc:date>
  
<dc:publisher>Tableless</dc:publisher>
  
<dc:date opf:event=&#8221;epub-publication&#8221;>2012-01-30</dc:date>
  
<dc:subject>Primeiro ePub</dc:subject>
  
<dc:subject>Estudos</dc:subject>
  
<dc:source>Tableless</dc:source>
  
<dc:rights>Pode copiar galera!</dc:rights>
  
<dc:identifier id=&#8221;EPB-UUID&#8221;>minhaid</dc:identifier>
  
<dc:language>pt-br</dc:language>
  
</metadata>

[/cc]

#### Manifest

É um manifesto mesmo. Deve conter (em qualquer ordem) a lista de todos os arquivos da sua publicação. Exceto mimetype, container.xml e content.opf É necessário especificar uma ID única para cada arquivo. Você pode nserir estas informações antes ou depois da metadata. O importante é que esteja também dentro da tag package. No caso do nosso livro-tutorial ficou assim:

[cc escaped=&#8221;true&#8221;  lang=&#8221;xml&#8221;]

<manifest>
  
<!&#8211; Documentos &#8211;>
  
<item id=&#8221;titulo&#8221; href=&#8221;titulo.html&#8221; media-type=&#8221;application/xhtml+xml&#8221; />
  
<item id=&#8221;capitulo1&#8243; href=&#8221;capitulo1.html&#8221; media-type=&#8221;application/xhtml+xml&#8221; />
  
<item id=&#8221;capitulo2&#8243; href=&#8221;capitulo2.html&#8221; media-type=&#8221;application/xhtml+xml&#8221; />

<!&#8211; CSS Style Sheets &#8211;>
  
<item id=&#8221;main-css&#8221; href=&#8221;style.css&#8221; media-type=&#8221;text/css&#8221;/>

<!&#8211; NCX &#8211;>
  
<item id=&#8221;ncx&#8221; href=&#8221;toc.ncx&#8221; media-type=&#8221;application/x-dtbncx+xml&#8221;/>
  
</manifest>

[/cc]

#### Spine

A espinha do livro, ou seja, a ordem de leitura. Aqui você deve colocar apenas os arquivos tipo HTML na ordem que você deseja que apareça no livro, chamando cada um pelo ID que você definiu no manifesto. Tome cuidado para não duplicar nenhum arquivo ou ID. Como você já adivinhou, deve ser inserido entre as tags package também.

[cc escaped=&#8221;true&#8221;  lang=&#8221;xml&#8221;]

<spine toc=&#8221;ncx&#8221;>
  
<itemref idref=&#8221;titulo&#8221; linear=&#8221;yes&#8221;/>
  
<itemref idref=&#8221;capitulo1&#8243; linear=&#8221;yes&#8221;/>
  
<itemref idref=&#8221;capitulo2&#8243; linear=&#8221;yes&#8221;/>
  
</spine>

[/cc]

#### toc.ncx

TOC é uma sigla para Table of Contents, ou seja, o indice do livro. Também é um arquivo xml salvo com a terminação .ncx Possui a seguinte estrutura:

**#head**

  * uid — o identificador único em content.opf
  * depth — níveis do sumário >= 1
  * totalPageCount — to 0
  * maxPageNumber — to 0

**#navMap**

O sumário em si

**#navPoint**

  * id — único do arquivo
  * playOrder —ordem de navegação (iniciando em 1)

O nosso índice ficou assim então:

[cc escaped=&#8221;true&#8221;  lang=&#8221;xml&#8221;]

<?xml version=&#8221;1.0&#8243; encoding=&#8221;UTF-8&#8243;?>
  
<!DOCTYPE ncx
  
PUBLIC &#8220;-//NISO//DTD ncx 2005-1//EN&#8221; &#8220;http://www.daisy.org/z3986/2005/ncx-2005-1.dtd&#8221;>
  
<ncx xmlns=&#8221;http://www.daisy.org/z3986/2005/ncx/&#8221; version=&#8221;2005-1&#8243;>
  
<head>
  
<meta name=&#8221;dtb:uid&#8221; content=&#8221;idtest&#8221;/>
  
<meta name=&#8221;dtb:depth&#8221; content=&#8221;3&#8243;/>
  
<meta name=&#8221;dtb:totalPageCount&#8221; content=&#8221;0&#8243;/>
  
<meta name=&#8221;dtb:maxPageNumber&#8221; content=&#8221;0&#8243;/>
  
</head>
  
<docTitle>
  
<text>Saga do primeiro ePub</text>
  
</docTitle>
  
<docAuthor>
  
<text>Dani</text>
  
</docAuthor>
  
<navMap>
  
<navPoint id=&#8221;titulo&#8221; playOrder=&#8221;1&#8243;>
  
<navLabel>
  
<text>Titulo</text>
  
</navLabel>
  
<content src=&#8221;titulo.html&#8221;/>
  
</navPoint>
  
<navPoint id=&#8221;capitulo1&#8243; playOrder=&#8221;2&#8243;>
  
<navLabel>
  
<text>Capitulo 1</text>
  
</navLabel>
  
<content src=&#8221;capitulo1.html&#8221;/>
  
</navPoint>
  
<navPoint id=&#8221;capitulo2&#8243; playOrder=&#8221;2&#8243;>
  
<navLabel>
  
<text>Capitulo 2</text>
  
</navLabel>
  
<content src=&#8221;capitulo2.html&#8221;/>
  
</navPoint>
  
</navMap>
  
</ncx>

[/cc]

&nbsp;

#### Os capítulos

É aqui que entra o livro em si. Cada capitulo deve ficar em um HTML separado. Estes arquivos não são nada diferentes de HTMLs comuns:

&nbsp;

[cc escaped=&#8221;true&#8221;  lang=&#8221;xml&#8221;]

<html xmlns=&#8221;http://www.w3.org/1999/xhtml&#8221; xml:lang=&#8221;pt&#8221;>
  
<head>
  
<meta http-equiv=&#8221;Content-Type&#8221; content=&#8221;application/xhtml+xml; charset=utf-8&#8243; />
  
<title>Capítulo 1</title>
  
<link href=&#8221;style.css&#8221; rel=&#8221;stylesheet&#8221; type=&#8221;text/css&#8221; />
  
</head>
  
<body>
  
<div>
  
<h3>Capítulo 1</h3>

<p>Hello World! Este é o primeiro capítulo do nosso livro. Yey!</p>
  
<p>Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum</p>
  
</div>
  
</body>
  
</html>

[/cc]

#### Outros tipos de arquivos:

**CSS** &#8211; Uma folha de estilos normal.
  
**Pasta images** &#8211; Aqui devem ficar as imagens do livro. Formatos permitidos: jpeg, png, gif e svg+xml
  
**Pasta fonts** &#8211; Utilize esta pasta se você quiser embedar algum arquivo de fonte no seu documento. Lembre-se de utilizar sempre o formato Open Type pois alguns aplicativos de leitura não suportam True Type.

#### E agora basta compactar!

Selecione todos os arquivos e crie um arquivo compactado (pode ser .zip ou .rar). Depois é só renomear para .epub e ler no seu dispositivo favorito. Pronto! Você tem um livro digital! 🙂

## Dicas importantes para editar um ePub

#### Semântica é sua amiga

Bem, se você é leitor do Tableless provavelmente não preciso dizer isso, mas vou dizer mesmo assim! É muito importante utilizar uma estrutura semântica aqui. Tags h1 a h6 para títulos, p para parágrafos… O que você já está mais do que cansado de saber a esta altura. Evite usar br para quebrar a linhas por que sem ter o tamanho de um container é difícil determinar quando de fato vai ser necessário quebrar a linha.

#### Evite seletores complexos

Leitores digitais não são tão sofisticados quanto browsers. Mantenha o seu CSS o mais simples possível.

#### Use tamanhos relativos

Como as &#8220;páginas&#8221; do seu livro vão aumentar e diminuir de acordo com o tamanho da tela do dispositivo não utilize pixels como medida para nada. Lembre-se: EM para texto e margens, porcentagens para figura. Isto vai garantir que o seu livro continue proporcional e escalável. E o seu leitor feliz!

#### Tamanho é Documento

Não use apenas um documento XHTML para o livro todo. A recomendação é que os capítulos tenham menos de 300k cada. Mais do que isto pode deixar alguns leitores, como o iBooks por exemplo, muito lentos! A razão é que estes apps consideram cada capítulo como um bloco de texto diferente. Se você colocar tudo em um documento só o aplicativo vai carregar tudo de uma vez a cada acesso.

Outra dica é tentar usar sempre imagens otimizadas para a web e com uma resolução não maior do que 1200 x 1600px.

#### Não pire muito na escolha de fontes

Evite usar fontes fora do padrão websafe. Você pode embedar fontes Open Type utilizando a propriedade @font-face mas isto não significa que voce deve. Para começar não são todos os leitores que aceitam isto e no final o seu arquivo pode ficar pesado demais e travar. E muitas vezes pode ser um trabalho extra inútil já que o seu usuário pode muito facilmente trocar de fonte. Se mesmo assim você quiser usar não escolha mais do que dois ou três tipos.

## Edição visual

Sim. Existem alguns softwares que podem gerar o livro para você. O Adobe InDesign faz isto, o Pages do Mac… Mas falando sério: não vale a pena. O código vai ficar sujo e no final você vai ter que corrigir vários bugs. É como se você estivesse utilizando um editor &#8220;What you see is what you get&#8221; para fazer um site. Acho que vocês entendem o drama. Mas… se você for realmente caminhar por esta estrada escura tenha algumas coisas em mente:

  * Se você está acostumado com editoração nestes programas é preciso mudar alguns paradigmas. Esqueça páginas mestras, hifenização, numeração, pé de página… você não precisa se preocupar mais com estas coisas em um formato digital.
  * Crie estilos específicos para o que é título, parágrafo, etc e não esqueça de importa-los na hora de salvar o arquivo.
  * Cuidado ao gerar o TOC (table of contents, ou seja, o índice). Se você colocar mais de dois subniveis pode dar problemas de compatibilidade com alguns programas e o seu livro simplesmente não abrir.
  * Lembre-se que todas as imagens precisam estar ancoradas para que fluam juntamente com o texto.
  * Determine quebras de capítulos. No caso do InDesign, salve cada parte do livro em um arquivo diferente. Depois junte todos os arquivos em um formato &#8220;book&#8221;.

## E quanto ao formato iBook da Apple?

A Apple lançou recentemente um software gratuito chamado iBooks Autor para a criação visual de livros digitais. Os livros no formato iBook são bem interativos, permitindo a implementação de elementos multimidia como videos (coisa que ainda está engatinhando no formato ePub). Com um &#8220;pequeno&#8221; porém. Sem muito alarde nos termos de serviço a Apple colocou uma clausula de exclusividade para livros comerciais. Ou seja, se você utilizar o software e vender o seu livro através da iBook Store não poderá vender em mais nenhum lugar. Sem contar que o programa é exclusivo para Mac.

## Fique longe dos conversores automáticos!

Existem alguns softwares ainda que prometem converter de PDF para ePub. Fique longe deles! Sério. Eles são ainda piores que os editores visuais. Um software não consegue interpretar um livro da mesma maneira que um ser humano a menos que você diga a ele o que fazer. Se você não determinar &#8220;ei, isto é um título&#8221; ele não tem como fazer este tipo de decisão por você.

Os PDFs estão presos a um tamanho fixo, lembra? O que significa que as palavras precisam ser hifenizadas. Se você converter automaticamente (além do seu código ser a coisa menos semântica desde os sites feitos em tabelas) os hífens vão continuar lá, criando divisões no me-io das pala-vras on-de não pre-cisava! Pense nos números das páginas… se o texto flui isso significa que um mesmo livro pode (e vai) ter uma numeração diferente de acordo com o aparelho utilizado. Mas no caso da conversão automática os números no pdf vão continuar lá. Os títulos provavelmente vão estar errados também. Fora que muitos deixam marcas como &#8220;convertido pelo programa XYZ&#8221; em todas as páginas do livro.

## Links úteis

  *][4] &#8211; A organização responsável pela criação do ePub. O site deles é meio confuso, mas contém bastante informação a respeito do formato.
  * [ePub Chech][5] &#8211; Validação de ePub
  * [Epub Format Construction Guide][6] &#8211; Um meta-livro bem completo sobre o assunto.

## Bibliotecas gratuitas

  * [Google Books][7]
  * [ePub Bud][8]

## Aplicativos para a Leitura

#### Mac & PC

  * [Adobe Digital Editions][9]
  * [Nook][10]

#### Linux

  * [FB Reader][11]

#### iOS

  * [iBooks][12]
  * [Stanza][13]

#### Android

  * [Aldiko][14]

#### Leitura no Browser

  *][15] &#8211; Google Chrome
  * [ePub Read][16] &#8211; Firefox

 [1]: http://idpf.org/ "IDPF"
 [2]: http://tableless.com.br/uploads/2012/01/meulivro.epub_.zip
 [3]: http://code.google.com/p/sigil/ "Sigil"
 [4]: http://idpf.org/epub "IDPF"
 [5]: http://code.google.com/p/epubcheck/ "ePub Check"
 [6]: http://www.hxa.name/articles/content/epub-guide_hxa7241_2007.html "Epub Format Construction Guide"
 [7]: http://books.google.com.br/ "Google Books"
 [8]: http://www.epubbud.com/ "ePub Bud"
 [9]: http://www.adobe.com/products/digitaleditions/ "Adobe Digital Editions "
 [10]: http://www.barnesandnoble.com/u/free-nook-apps/379002321/ "Nook"
 [11]: http://www.fbreader.org/ "FB Reader"
 [12]: http://www.apple.com/br/ipad/built-in-apps/ibooks.html "iBooks"
 [13]: http://itunes.apple.com/br/app/stanza/id284956128?mt=8 "Stanza"
 [14]: http://www.aldiko.com/ "Aldiko"
 [15]: https://chrome.google.com/webstore/detail/ghgnmgfdoiplfmhgghbmlphanpfmjble "Magic Scroll "
 [16]: http://www.epubread.com/ "ePub Read"