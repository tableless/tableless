---
title: Gantry 5 – Desenvolvimento de templates para Joomla e WordPress
author: Léo WG
type: post
date: 2015-08-17
excerpt: O Gantry é um framework de template Open Source e gratuito para o desenvolvimento de templates em Joomla e Wordpress.
url: /gantry-5-desenvolvimento-de-templates-para-joomla-e-wordpress/
categories:
  - CMS
  - Design
  - Joomla
  - Wordpress
tags:
  - cms
  - gantry
  - joomla
  - Wordpress

---
&nbsp;

Com o surgimento dos Gerenciadores de Conteúdo como o <a href="http://www.joomla.org/" target="_blank">Joomla </a>e <a href="https://wordpress.org/" target="_blank">WordPress</a>, os desenvolvedores de sites começaram a aproveitar mais o tempo e entregar projetos mais rápido. Quando surgem os frameworks de templates, que se integram aos CMSs para gerenciar e facilitar o desenvolvimento dos layouts das páginas, as coisas ficam mais interessantes. E é justamente nesse ponto que vamos chegar. Farei uma breve abordagem sobre o novo Framework de Template Gantry 5.

## **O Gantry**

O Gantry é um framework de template Open Source and Free, desenvolvido pela <a href="http://www.rockettheme.com/" target="_blank">RocketTheme </a>(um dos melhores clubes de extensões e templates para Joomla e WordPress) que tem a finalidade de gerenciar e customizar os layouts das páginas.

Na versão mais estável, a 4, o framework já atendia muito bem aos desenvolvedores de template, mas havia alguns problemas de semântica, layout adaptativo em vez de responsivo, poucas possibilidades de _override_ e o peso excessivo das páginas. Era uma luta para conseguir enxugar o máximo e aumentar o desempenho. Outros frameworks como <a href="http://www.t3-framework.org/" target="_blank">T3</a>, <a href="http://www.joomshaper.com/helix" target="_blank">Helix</a>, e <a href="https://yootheme.com/themes/warp-framework" target="_blank">Warp</a>, tinham uma curva de aprendizagem muito lenta, o que me frustrava. Foi quando surge o <a href="http://gantry.org/" target="_blank">Gantry 5</a>.

## **A versão 5**

Se você já conhecia a versão anterior, esqueça, a versão 5 é totalmente diferente e não tem nada a ver com as antigas. O lado bom é que consertaram e melhoraram tudo que citei de ruim acima, o lado não tão bom é que você terá que reaprender a trabalhar com o framework, mas aprender coisa nova nunca é demais.

Vamos apresentar as possibilidades que a versão 5 pode trazer a respeito do **desenvolvimento de templates em Joomla e WordPress**.

### **Crie várias páginas com configurações e layouts independentes**

<div id="attachment_50481" style="width: 610px" class="wp-caption alignnone">
  <a href="http://tableless.com.br/uploads/2015/07/img12.jpg"><img class="wp-image-50481 size-full" src="http://tableless.com.br/uploads/2015/07/img12.jpg" alt="Painel Outline" width="600" height="300" /></a>
  
  <p class="wp-caption-text">
    Painel Outline
  </p>
</div>

O Gantry 5 trouxe um nível de abstração de páginas muito superior aos outros frameworks do mercado. Chamados de **Outlines** é onde tudo se inicia no framework. Os Outlines são páginas que podem ser criadas e editadas de forma independente, dando ao layout do projeto uma flexibilidade na administração de diferentes elementos. E tudo isso é possível sem que o desenvolvedor escreva linhas e linhas de código, é tudo no arrastar e soltar.

Ao instalar o Gantry 5 e o tema padrão Hydrogen, pode-se observar 1 outline base, 2 outlines de página padrão e 3 outlines essenciais usadas para a exibição de conteúdo, página de erro e página off-line. Essas não podem ser excluídas, somente editadas, pois são outlines fundamentais para o template.

### **Faça override do core**

Esta é uma das possibilidades mais legais do Gantry 5, pois você consegue fazer substituições de quase tudo no framework. E o interessante é que ele utiliza tecnologias recentes da Web como o <a href="http://yaml.org/" target="_blank">YAML</a> para trabalhar com campos de formulário e o <a href="http://twig.sensiolabs.org/" target="_blank">Twig Template</a> para facilitar a estruturação dos arquivos de substituição.

### **Estilização mais fácil e completa**

<div id="attachment_50482" style="width: 610px" class="wp-caption alignnone">
  <a href="http://tableless.com.br/uploads/2015/07/img2.jpg"><img class="wp-image-50482 size-full" src="http://tableless.com.br/uploads/2015/07/img2.jpg" alt="Painel Style" width="600" height="300" /></a>
  
  <p class="wp-caption-text">
    Painel Style
  </p>
</div>

O painel **Style** agora tem mais possibilidades de customização e ficou ainda mais fácil trocar as cores principais do template. Com ajuda das tecnologias **YAML** e **Twig Template** você consegue fazer estilizações através de overrides onde o céu é o limite, basta abusar bastante da criatividade. E como não bastasse, agora é possível controlar os Breakpoints nos mais variados formatos de unidades: px, em ou rem.

### **Micro módulos personalizáveis**

<div id="attachment_50483" style="width: 610px" class="wp-caption alignnone">
  <a href="http://tableless.com.br/uploads/2015/07/img3.jpg"><img class="wp-image-50483 size-full" src="http://tableless.com.br/uploads/2015/07/img3.jpg" alt="Painel Settings" width="600" height="300" /></a>
  
  <p class="wp-caption-text">
    Painel Settings
  </p>
</div>

O **Particle System** como é chamado, é um sistema de módulos já pré-formatados para utilização direta no painel de layout. Você consegue customizá-lo de forma independente dos outlines, ou seja, o mesmo particle utilizado em uma página poderá ser utilizado em outra sem que haja conflito de configurações. E o mais legal é que você consegue customizar, habilitar ou desabilitar um particle e/ou criar um novo de acordo com sua necessidade ou criatividade. Mais uma vez o céu é o limite.

Existem alguns particles especiais chamados de **Atom**, que possibilitam a entrada do UA Code do Google Analytics e a chamada de dependências CSS e JS externas, evitando que o desenvolvedor mexa diretamente no código do template.

### **Infinitas possibilidades de customização**

<div id="attachment_50484" style="width: 610px" class="wp-caption alignnone">
  <a href="http://tableless.com.br/uploads/2015/07/img4.jpg"><img class="wp-image-50484 size-full" src="http://tableless.com.br/uploads/2015/07/img4.jpg" alt="Painel Layout" width="600" height="300" /></a>
  
  <p class="wp-caption-text">
    Painel Layout
  </p>
</div>

Com o P**ainel de Layout** do Gantry 5, você consegue montar inúmeras variações de grid. No canto esquerdo fica disponível vários módulos prontos para arrastar e soltar no painel. Ainda pode escolher através do botão “Load” qual o Preset (Estrutura de posições da página) deseja utilizar.

Toda a estrutura do template criado no painel de layout é renderizado no browser através da propriedade <a href="http://tableless.com.br/flexbox-organizando-seu-layout/" target="_blank">Flexbox do CSS3</a>.

### **O editor de Menu**

<div id="attachment_50485" style="width: 610px" class="wp-caption alignnone">
  <a href="http://tableless.com.br/uploads/2015/07/img5.jpg"><img class="wp-image-50485 size-full" src="http://tableless.com.br/uploads/2015/07/img5.jpg" alt="Editor de Menu" width="600" height="300" /></a>
  
  <p class="wp-caption-text">
    Editor de Menu
  </p>
</div>

Em minha opinião, a mais fantástica possibilidade do framework é o poder de flexibilidade que o editor de menu tem. Após a criação dos itens de menu no CMS, o editor de menu renderiza os itens e a partir daí você consegue realizar várias customizações, como inserir ícones, particles, módulos ou plug-ins, definir classes, reorganizar os itens, inserir subtítulo, inserir imagem, inserir submenus e organizar os elementos em um grid. Eu acho que podem melhorar ainda mais, com a possibilidade de customizar as cores e eventos.

### **Estilize usando SCSS**

Uma inovação do Gantry 5 também foi a possibilidade de trabalhar com o <a href="http://sass-lang.com/" target="_blank">SCSS</a>, que na minha opinião é extremamente produtivo, e a manutenção do código fica muito mais prático e rápido, mas quem não se familiariza com **SCSS** pode ficar tranquilo, pois ele suporta <a href="http://lesscss.loopinfinito.com.br/" target="_blank">Less </a>e também pode trabalhar diretamente com o CSS.

E para facilitar ainda mais, o framework utiliza o <a href="http://bourbon.io/" target="_blank">Bourbon</a>, uma biblioteca de mixin para SASS que ajuda, principalmente quando se trata de compatibilidade entre navegadores. É uma biblioteca fantástica, vale a pena estudá-la para utilizar da forma mais adequada em seus templates.

## **O Suporte**

O Gantry 5 tem uma comunidade bem ativa e colaborativa, e por isso conseguiram chegar em um **framework tão completo**.

A <a href="http://docs.gantry.org/" target="_blank">documentação </a>é sem dúvida uma das mais claras e fáceis de entender. Nela tem tutoriais completos de como instalar, usar, configurar e estender ainda mais o framework.

Vale a pena também seguir o <a href="http://gantry.org/blog" target="_blank">blog</a>, com artigos sobre os releases e alguns tutoriais interessantes que não estão presentes na documentação.

E tem também o <a href="https://gitter.im/gantry/gantry5" target="_blank">Gitter</a>, que funciona como um chat da comunidade. Fiquei maravilhado com o suporte dos caras; algumas vezes resolveram alguns problemas que tive na mesma hora. É um lugar também para reportar bugs do framework.

## **Considerações finais**

Por ser um framework lançado recentemente (menos de 5 meses), há muitas coisas a descobrir e melhorar. Por isso é importante, se for utilizar o framework, estar engajado na comunidade do Gantry 5 para aprender cada vez mais e também poder colaborar com o projeto.

Acredito muito no potencial desta ferramenta para desenvolvimento de templates para Joomla e WordPress, pois nestes últimos 3 anos trabalhando com CMS consegui pela primeira vez reduzir o tempo de desenvolvimento de forma considerável.

Se tiver alguma sugestão ou crítica sobre o artigo, comentem.