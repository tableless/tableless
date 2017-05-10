---
title: 3 parâmetros de HTML que você deve usar em um futuro próximo
author: Dani Guerrato
type: post
date: 2013-05-14
excerpt: Imagens responsivas, downloads automáticos e logos em vetor sempre atualizados. Não é sonho. Conheça algumas novidades que nos esperam em um futuro próximo.
url: /3-parametros-de-html-que-voce-dev-usar-em-um-futuro-proximo/
dsq_thread_id: 1287604903
categories:
  - Artigos
  - HTML
  - HTML5
tags:
  - 2013
  - design responsivo
  - download em HTML5
  - html
  - imagens responsivas
  - rel logo

---
Neste artigo vamos conhecer alguns parâmetros que ainda não são largamente utilizados por algum motivo ou outro, mas que merecem ser conhecidos por serem práticos, úteis e interessantes. Alguns não foram aprovados oficialmente por orgãos como W3C, outros já receberam o ok da instituição mas não são compatíveis com a maioria dos browsers&#8230; De qualquer maneira valem a pena serem conhecidos pois todos tem o poder de facilitar nosso dia-a-dia de alguma forma.

É impossível prever com exatidão quais propostas vieram para ficar e quais vão se perder no limbo dos browsers, mas vale a pena ficar de olho nestas aqui&#8230;

## Imagens responsivas

### Picture

Esta proposta pode tornar realidade um sonho de muitos desenvolvedores: imagens responsivas. Esqueça soluções server side complexas ou javascripts pesados. Utilizando você pode servir imagens em diferentes resoluções e / ou densidade de pixels diretamente no HTML. E o melhor, através de Media Queries apenas a imagem correta para cada situação é baixada pelo navegador!

As possibilidades de uso são imensas. É possível utilizar imagens adequadas para cada ponto de quebra do layout em diferentes dispositivos, servir imagens coloridas ou em preto e branco de acordo com a capacidade da tela ou até mesmo mostrar imagens diferentes de acordo com a orientação do dispositivo (retrato ou paisagem).

Na prática a tag picture poderia ser aplicada da seguinte maneira:

<pre class="lang-HTML">&lt;picture&gt;
  &lt;source media="(min-width: 40em)" srcset="fotogrande.jpg 1x, fotogrande-hd.jpg 2x"&gt;
  &lt;source srcset="fotopequena.jpg 1x, fotopequena-hd.jpg 2x"&gt;
  &lt;img src="fotofallback.jpg" alt=""&gt;
&lt;/picture&gt;</pre>

Em dispositivos cuja largura minima é maior do que 40 EM o arquivo &#8220;fotogrande.jpg&#8221; seria exibido, enquanto para larguras menores o arquivo &#8220;fotopequena.jpg&#8221; seria o escolhido. Os atributos &#8220;1x&#8221; e &#8220;2x&#8221; referem-se a densidade de pixels. Ou seja, versões em HD seriam servidas para monitores de alta resolução como o retina display. No caso de não compatibilidade do atributo com o browser uma  <img alt="" />normal serviria como fallback.

Infelizmente, por enquanto, nenhum browser suporta o atributo. Mas isto deve mudar em breve. Pelo menos no que depender do [Responsive Images Community][1], o grupo de desenvolvedores empenhado em discutir, refinar e divulgar o atributo. Eles até construíram um novo build do Chromium só para demonstrar como tudo funcionaria ao vivo. Já existe um [rascunho não-oficial][2] do projeto para a W3C com a documentação completa. Na [página do grupo no Github][3] também é possível acompanhar as discussões.

### Srcset

Existe ainda uma proposta diferente apoiada pelo mesmo grupo. Incrementar o bom e velho img através do atributo srcset.

<pre class="lang-HTML">&lt;img src="fallback.jpg" alt="" srcset="fotopequena.jpg 640w 1x, fotopequena-hd.jpg 640w 2x, fotogrande.jpg 1x, fotogrande-hd.jpg 2x "&gt;</pre>

Esta sintaxe é mais concisa e já existe como um [rascunho oficial na W3C][4]. O conceito ainda está em um estágio bem inicial de desenvolvimento, mas de qualquer forma esta é uma discussão que vale a pena ser acompanhada.

## Rel=&#8221;logo&#8221;

Buscar por logotipos na internet pode ser uma tarefa difícil. Serviços como Google imagens acabam retornando arquivos de baixa qualidade, rasterizados e pequenos demais. Alguns sites como [Brands of the World][5] tentam fazer um apanhado geral de alguns logotipos, mas acabam não dando conta do trabalho. Sem contar que é impossível garantir que o arquivo é uma cópia real e de boa qualidade do logotipo original.

A proposta do [rel=&#8221;logo&#8221;][6] é criar um padrão para a publicação de logotipos em vetor na internet que possa ser reutilizado por outros sites, aplicativos, leitores, etc. Desta maneira os usuários poderiam facilmente ter acesso a um arquivo escalável e aprovado pelo dono. E isto facilitaria para que as aplicações sempre tivessem a versão mais atualizada do logo, mantendo a consistência da identidade visual de uma marca.

O padrão foi [rejeitado pelo Microformats][7] por ser parecido com rel=&#8221;icon&#8221;. (Aparentemente eles não sabem distinguir entre ícones e logotipos). Mas isto não desestimulou o uso já que é algo simples de ser aplicado e que não depende muito de atributos como compatibilidade do browser, etc. Alguns serviços grandes como Foursquare e Github já utilizam rel=&#8221;logo&#8221;.

Basta uma linha de HTML para utilizar rel=&#8221;logo&#8221; em seu site. O processo é bem similar ao de implementação de um favicon ou um apple touch icon. Para utilizar basta realizar o upload do arquivo SVG em um servidor qualquer e adicionar o seguinte código entre as tags head (obviamente substituindo &#8220;seudominio.com.br&#8221; pelo endereço do seu arquivo).

<pre class="lang-HTML">&lt;link rel="logo"   type="image/svg"  href="http://www.seudominio.com.br/logo.svg"/&gt;</pre>

E pronto! Você pode testar o funcionamento utilizando a [API do serviço][8].

Para o futuro existem ainda projetos para ampliar este conceito. A idéia é incluir formatos diferentes (horizontal, vertical, quadrado), variações de cores (mococromático, colorido, etc) e até mesmo link para um manual da marca em PDF.

Quer gritar para os quatro cantos da web que qualquer um pode baixar seu logo? Você pode implementar uma solução como a do plugin [Logo Downloadtip][9] para facilitar o acesso ao arquivo.

## a[download]

Colocar um link direto para um arquivo pesado &#8211; como um PDF por exemplo &#8211; pode ser um desastre. O usuário pode clicar acidentalmente e o navegador travar ao tentar renderizar o arquivo utilizando um plugin&#8230; Pedir para &#8220;clicar com o botão direito e salvar&#8221; também não é uma solução efetiva do ponto de vista da experiência do usuário. Mas através do atributo a[download] você pode forçar o browser a realizar automaticamente o download do arquivo. Existem algumas soluções em PHP para este problema, mas seria muito mais simples se isto pudesse ser resolvido em HTML mesmo, certo?

Existe uma preocupação grande quanto a segurança deste tipo de funcionalidade. É provável que arquivos executáveis não sejam compatíveis com o formato.

Bem, o parâmetro a[download] já existe e está presente nas especificações do HTML5. O problema é a compatibilidade com os navegadores. Por enquanto só o Google Chrome 4+ e o Firefox 20+ aceitam&#8230; Mas se você quiser utilizar mesmo assim é bem simples.

<pre class="lang-HTML">&lt;a href="nomedoarquivogigante.pdf" download&gt;Download do Arquivo Gigante&lt;/a&gt;</pre>

Você também pode especificar um nome através do atributo &#8220;download&#8221;. Isto é especialmente útil no caso de arquivos com o nome gerado automaticamente, já que o arquivo sera salvo com o nome que você especificou. Não se esqueça de incluir a extensão do arquivo já que o Firefox não coloca ela automaticamente.

<pre class="lang-HTML">&lt;a href="4816162342.pdf" download="arquivogigante.pdf"&gt;Download do Arquivo Gigante&lt;/a&gt;</pre>

Quer testar como funciona? Esta [demo do atributo][10] é bem interessante.

Além de baixar automáticamente ao clicar no link, no Google Chrome também é possível arrastar e soltar o arquivo para a área de trabalho.

## Seja a mudança que você quer ver no mundo.

Este pensamento aplica-se perfeitamente ao desenvolvimento web. As vezes dependemos muito de padrões, consórcios e associações fechadas para determinar o futuro e esquecemos que nós, desenvolvedores, também temos o poder para criarmos nossos próprios caminhos e fazermos a diferença na comunidade. Iniciativas como rel=&#8221;logo&#8221; e Responsive Images Community Group são a prova disto.

 [1]: http://responsiveimages.org/ "Responsive Images Community Group"
 [2]: http://picture.responsiveimages.org/ "Responsive Images - Picture"
 [3]: https://github.com/responsiveimagescg "Responsive Images CG "
 [4]: http://www.w3.org/html/wg/drafts/srcset/w3c-srcset/ "W3C - Srcset "
 [5]: http://www.brandsoftheworld.com/ "Brands of the World"
 [6]: http://relogo.org "relogo"
 [7]: http://microformats.org/wiki/rel-logo "Rel Logo"
 [8]: http://relogo.org/api/ "Relogo API"
 [9]: http://demo.jarnesjo.net/jquery-logo-downloadtip/ "jQuery Logo Downloadtip"
 [10]: http://html5-demos.appspot.com/static/a.download.html "A-download Demo"