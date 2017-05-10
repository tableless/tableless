---
title: CSS e acessibilidade na web
author: Reinaldo Ferraz
type: post
date: 2013-03-12
excerpt: Entenda como o uso do CSS influencia a acessibilidade dos seus projetos web.
url: /css-e-acessibilidade-na-web/
dsq_thread_id: 1132699458
categories:
  - Acessibilidade
  - CSS
tags:
  - acessibilidade
  - html
  - internet para todos
  - w3c

---
<img src="http://blog.w3c.br/uploads/2013/03/css31-213x300.png" alt="logo CSS3" style="float: left; margin-right:15px; " width="213" height="300" />

Temos abordado bastante a importância da acessibilidade na web na estrutura e semântica do código HTML: cabeçalhos, tabelas, textos alternativos e outros recursos para deixar o _markup_ robusto e acessível. Mas todos são elementos que podem ser manipulados pelo CSS e por isso devemos ter certos cuidados com a acessibilidade deles.

Softwares leitores de tela já são capazes de identificar elementos de formatação visual das páginas que não foram declaradas no HTML e sim no CSS, como tipo e cor de fonte por exemplo. Por esse motivo existem questões relacionadas a acessibilidade que estão diretamente ligadas ao CSS da sua página e vão muito além do uso de cores nas suas páginas Web. 

Gostaria de elencar aqui alguns pontos importantes para a criação de páginas web acessíveis voltados diretamente ao uso do CSS, mas antes de começar vale lembrar da máxima de sempre separar as camadas de estrutura (HTML) da apresentação (CSS) da sua página web. Faça toda a formatação visual/layout dentro do CSS e deixe o HTML para a estrutura do seu documento.

### Contraste

Sua paleta de cores deve prever o contraste adequado entre os elementos da página, e tudo isso deve ser considerado no seu CSS. Fundos e elementos devem um contraste de pelo menos 4,5:1 para uma visualização adequada. O E-mag publica em sua última página uma [tabela de referência para textos em preto ou branco com fundos coloridos][1] que auxilia muito essa tarefa.

### Pseudo elementos :before e :after

Servem para inserir conteúdo adicional antes e depois de determinados elementos em sua página web via CSS. Esse recurso deve ser utilizado com cuidado pois nem todas as tecnologias assistivas/leitores de tela conseguem ler os conteúdos inseridos antes ou depois do texto. O ideal é utilizar pseudo-elementos apenas para uso estético e design e não para inserir conteúdo importante da sua página web. Existe um ótimo [artigo da Lucica Ibanescu explicando e mostrando como os leitores de tela interagem com pseudo-elementos][2].

> Faça toda a formatação visual/layout dentro do CSS e deixe o HTML para a estrutura do seu documento.

### Links

É importante que o seu usuário saiba que aquele texto em destaque é um link e não precise ficar vasculhando a página para procurar um texto com link para outra página. [Jacob Nielsen publicou em 2004 um artigo com orientações para a criação e customização de links em sua página][3], como por exemplo não sublinhar textos que não são links e usar cores diferentes para links visitados.

### Convulsões

O WCAG 2.0 deixa bem claro que devemos ter [cuidado para não criar conteúdos que possam causar convulsões em usuários com fotossensibilidade][4], como telas que piscam muito rápido ou efeitos luminosos estroboscópicos. Com a possibilidade de fazer animações em CSS3, essa recomendação também serve para a criação de efeitos nas folhas de estilo. 

### Conteúdo invisível

[Existem diversas formas de esconder o conteúdo de uma página web][5]. Alguns deles podem ser acessados por tecnologias assistivas por isso vale a pena verificar se o que você quer esconder em sua página deve ou não ser lido por softwares leitores de tela. [Este artigo de Jonathan Snook explica bem cada uma das técnicas][6].

> Softwares leitores de tela já são capazes de identificar elementos de formatação visual das páginas que não foram declaradas no HTML e sim no CSS

### Foco nos elementos

Localizar onde está o foco em uma navegação via teclado de uma página cheia de links é uma tarefa complicada quando o foco não dá destaque para o elemento selecionado. Destacar o foco dos elementos beneficia não só pessoas que navegam por links mas auxilia o preenchimento de formulários, facilitando a localização do foco em determinados campos.

Viu como acessibilidade no CSS vai muito além de questões com cores? Posicionamento de elementos, tamanho de fontes e linhas também devem ser considerados no seu projeto web. Vale lembrar que hoje desenvolvemos pensando em uma plataforma da web, a _Open Web Platform_ e não somente no HTML5 ou no CSS3. A Web de hoje vai muito além do código HTML e sua acessibilidade deve ser ampliada para toda a sua plataforma para que a web seja efetivamente para todos.

 [1]: http://emag.governoeletronico.gov.br/emag/#s7
 [2]: http://cssgallery.info/testing-the-accessibility-of-the-css-generated-content/
 [3]: http://www.nngroup.com/articles/guidelines-for-visualizing-links/
 [4]: http://www.w3.org/TR/WCAG/#seizure
 [5]: http://webaim.org/techniques/css/invisiblecontent/
 [6]: http://snook.ca/archives/html_and_css/hiding-content-for-accessibility