---
title: Cabeçalhos nível 1, sections e acessibilidade
author: Reinaldo Ferraz
type: post
date: 2014-09-01
excerpt: Como múltiplos H1 dentro de sections impactam a acessibilidade da sua página
url: /cabecalhos-nivel-1-e-sections/
categories:
  - Acessibilidade
  - Semântica
tags:
  - acessibilidade

---
Na semana passada li um artigo bem interessante sobre a utilização de múltiplos <h1>
  
em uma página separada por <section> e como isso impacta a acessibilidade das páginas Web. Depois de algumas conversas pelo Twitter resolvi pesquisar e escrever um pouco sobre o assunto.</section> 

Antes de mais nada, quero deixar claro que **essa é uma abordagem com relação a acessibilidade das páginas e não sobre SEO**. Essa conversa sobre como mais de um <h1> interfere no resultado de busca é antiga mas vale um novo post para o tema.

Tudo começou com o artigo do [Adrian Roselli][1] sobre esse assunto. Ele discute a questão sobre como as tecnologias assistivas acessam os cabeçalhos <h1> dentro dos elementos <section>. 

O primeiro ponto a ser considerado é como a documentação do W3C trata a questão dos múltiplos <h1> dentro de cada página web. Segundo a [documentação do próprio HTML5][2] é possível ter mais de um <h1> na página desde que estejam separados por múltiplas <section>.

Essa questão impacta na compatibilidade com tecnologias assistivas de hoje em dia. Atualmente os principais leitores de tela ([JAWS 15][3] e [NVDA 2014][4]) não conseguem identificar a diferença e a importância de um <h1> no título de uma notícia de um <h1> dentro de uma <section>. Explico.

Considere uma página com a seguinte estrutura:

<pre>&lt;!DOCTYPE html&gt;
&lt;html lang="pt-br"&gt;
&lt;head&gt;
&lt;title&gt;Teste&lt;/title&gt;
&lt;/head&gt;
&lt;body&gt;
&lt;h1&gt;Título Importante&lt;/h1&gt;
   &lt;section&gt;
   &lt;h1&gt;Título Importante&lt;/h1&gt;
      &lt;section&gt;
      &lt;h1&gt;Título Importante&lt;/h1&gt;
      &lt;/section&gt;
   &lt;/section&gt;
&lt;/body&gt;
&lt;/html&gt;
</pre>

O navegadores exibirão o código da seguinte forma:

<img src="http://tableless.com.br/uploads/2014/09/teste-titulos1.png" alt="Imagem com as palavras título importante em três tamanhos" width="265" height="141" class="aligncenter size-full wp-image-44187" srcset="uploads/2014/09/teste-titulos1.png 265w, uploads/2014/09/teste-titulos1-261x139.png 261w" sizes="(max-width: 265px) 100vw, 265px" />

Mas para os atuais leitores de tela a informação aparece da seguinte forma:

→ Título importante cabeçalho nível 1
  
→ Título importante cabeçalho nível 1
  
→ Título importante cabeçalho nível 1

A [Wiki do Grupo de HTML do W3C][5] mostra mais detalhes dessa explicação.

O documento [WCAG 2.0][6] não aborda a questão de múltiplos cabeçalhos de nível 1 e coloca como exemplo apenas os cabeçalhos estruturados entre <h1> e <h6>.

O que temos hoje é uma gama de tecnologias assistivas que navegam pelos cabeçalhos da página mas não fazem distinção de importância por estar dentro de uma <section>.

Ao passar esse pequeno trecho de código dentro do [validador de markup do W3C][7] não encontramos erros. Ele passa com validação de HTML5 mas mostra o seguinte _warning_ na página:

<img src="http://tableless.com.br/uploads/2014/09/validator-01.png" alt="Imagem com o resultado de um aviso do validador de markup referente a  cabeçalhos e leitores de tela" width="835" height="219" class="aligncenter size-full wp-image-44197" srcset="uploads/2014/09/validator-01.png 835w, uploads/2014/09/validator-01-265x69.png 265w, uploads/2014/09/validator-01-400x104.png 400w" sizes="(max-width: 835px) 100vw, 835px" />

Ou seja: para garantir que tecnologias assistivas acessem o conteúdo de cabeçalhos em sua ordem de importância adequada, não considere que elementos <h1> dentro de <section> tenha o mesmo peso de importância de <h1> que estão fora de <section>.Isso não quer dizer que não seja possível utilizar mais de um <h1> dentro de uma página. Se todos os cabeçalhos de nível 1 tem o mesmo valor semântico, eles podem e devem ser utilizados.

Os cabeçalhos de uma página tem função fundamental para a acessibilidade. Pessoas que utilizam softwares leitores de tela navegam pela estrutura de cabeçalhos e utilizam o tipo de cabeçalho para navegar entre eles. Por exemplo, nos principais leitores de tela ao pressionar a tecla &#8220;H&#8221; o software navega pelos cabeçalhos em sequência. Ao pressionar as teclas &#8220;1&#8221; a &#8220;6&#8221; a navegação é feita por níveis de cabeçalho, sendo a tecla &#8220;1&#8221; utilizada para navegar por cabeçalhos de nível 1 e assim por diante até o nível 6. Inclusive a navegação por cabeçalhos é uma das principais formas de localizar conteúdo, segundo a última [pesquisa do WebAim sobre usuários de softwares leitores de tela][8].

 [1]: http://blog.adrianroselli.com/2013/12/the-truth-about-truth-about-multiple-h1.html
 [2]: http://www.w3.org/TR/html5/sections.html#the-h1,-h2,-h3,-h4,-h5,-and-h6-elements
 [3]: http://www.freedomscientific.com/Downloads/ProductDemos/#JAWS
 [4]: http://www.nvaccess.org/download/
 [5]: https://www.w3.org/wiki/HTML/Usage/Headings/h1only
 [6]: http://www.w3.org/TR/2014/NOTE-WCAG20-TECHS-20140408/H42
 [7]: http://validator.w3.org/
 [8]: http://webaim.org/projects/screenreadersurvey5/#finding