---
title: Páginas acessíveis com o HaTeMiLe
author: Carlson Santana Cruz
type: post
image: http://imgh.us/dog-41431_1280.png
date: 2017-05-07
excerpt: O HaTeMiLe é uma biblioteca que utiliza os Padrões Web para resolver problemas de acessibilidade. Entenda melhor como ela funciona.
categories:
  - Acessibilidade
  - HTML
  - JavaScript
---

A acessibilidade finalmente esta se tornando uma das metas no desenvolvimento web, mesmo assim ela enfrenta um conjunto de problemas:

 1. nas aulas, apostilas e tutoriais sobre desenvolvimento web dificilmente abordam a acessibilidade;
 2. mesmo conhecendo os Padrões Web (HTML, CSS e JavaScript) o desenvolvedor pode acabar desenvolvendo páginas web inacessíveis;
 3. frameworks e temas utilizados no desenvolvimento podem contribuir com páginas inacessíveis.

Baseando-se nos [polyfills](https://remysharp.com/2010/10/08/what-is-a-polyfill), que permitem prover um recurso não suportado pelo browser, foi desenvolvido o [HaTeMiLe](https://github.com/carlsonsantana/HaTeMiLe-for-JavaScript) (anagrama para HTML Accessible, removendo as consoantes de Accessible), uma biblioteca que utiliza os Padrões Web para tentar resolver alguns problemas de acessibilidade.

## Instalação da biblioteca

É possível [baixar a biblioteca através do GitHub](https://github.com/carlsonsantana/HaTeMiLe-for-JavaScript) ou instalá-la no projeto do seu site através do bower:

```shell
bower install hatemile
```

Dentro da tag `<head>`, antes de qualquer CSS e JavaScript, cole o código-fonte abaixo, substituindo o **/path/to** pelo caminho relativo ou absoluto para a biblioteca ser acessada através navegador.

```html
<head>
	[...]
	<!-- Esconde as mudanças visuais da biblioteca. -->
	<link rel="stylesheet" type="text/css" href="/path/to/css/hide_changes.css" />
	<!-- Faz com que seja possível armazenar todos os event listener da página. -->
	<script type="text/javascript" src="/path/to/js/common.js"></script>
	<script type="text/javascript" src="/path/to/js/eventlistener.js"></script>
	[...]
</head>
```

No final da tag `<body>`, cole o código-fonte abaixo.

```html
<body>
	[...]
	<!-- Arquivos de idiomas -->
	<script type="text/javascript" src="/path/to/_locales/en_US/js/configurations.js"></script>
	<script type="text/javascript" src="/path/to/_locales/en_US/js/skippers.js"></script>
	<script type="text/javascript" src="/path/to/_locales/en_US/js/symbols.js"></script>
	<!-- Dependências -->
	<script type="text/javascript" src="/path/to/js/hatemile/util/CommonFunctions.js"></script>
	<script type="text/javascript" src="/path/to/js/hatemile/util/Configure.js"></script>
	<script type="text/javascript" src="/path/to/js/hatemile/util/html/vanilla/VanillaHTMLDOMParser.js"></script>
	<script type="text/javascript" src="/path/to/js/hatemile/util/html/vanilla/VanillaHTMLDOMElement.js"></script>
	<script type="text/javascript" src="/path/to/js/hatemile/util/html/vanilla/VanillaHTMLDOMTextNode.js"></script> 
	<script type="text/javascript" src="/path/to/js/cssParser.js"></script>
	<script type="text/javascript" src="/path/to/js/hatemile/util/css/jscssp/JSCSSPParser.js"></script>
	<script type="text/javascript" src="/path/to/js/hatemile/util/css/jscssp/JSCSSPRule.js"></script>
	<script type="text/javascript" src="/path/to/js/hatemile/util/css/jscssp/JSCSSPDeclaration.js"></script>
	<!-- Classes de soluções -->
	<script type="text/javascript" src="/path/to/js/hatemile/implementation/AccessibleCSSImplementation.js"></script>
	<script type="text/javascript" src="/path/to/js/hatemile/implementation/AccessibleEventImplementation.js"></script> 
	<script type="text/javascript" src="/path/to/js/hatemile/implementation/AccessibleFormImplementation.js"></script>
	<script type="text/javascript" src="/path/to/js/hatemile/implementation/AccessibleDisplayScreenReaderImplementation.js"></script>
	<script type="text/javascript" src="/path/to/js/hatemile/implementation/AccessibleNavigationImplementation.js"></script>
	<script type="text/javascript" src="/path/to/js/hatemile/implementation/AccessibleAssociationImplementation.js"></script>
</body>
```

Após esses scripts crie um arquivo JavaScript, nos exemplos a seguir iremos utilizar o arquivo *execute_hatemile.js*, para executar a biblioteca cole o código-fonte abaixo.

```javascript
//Carrega as configurações do HaTeMiLee
var configuration = new hatemile.util.Configure(hatemile_configuration); 
//Instancia os parsers HTML e CSS, necessários para executar as correções
var htmlParser = new hatemile.util.html.vanilla.VanillaHTMLDOMParser(document); 
var cssParser = new hatemile.util.css.jscssp.JSCSSPParser(document, location.href);
```

## Recursos da biblioteca

### Prover ao leitor de tela o suporte as propriedades CSS speak, speak-as e speak-header

Os navegadores mais populares *Internet Explorer*, *Microsoft Edge*, *Mozilla Firefox*, *Google Chrome*, *Opera* e *Safari* não possuem suporte as propriedades do [CSS Speech](https://www.w3.org/TR/css3-speech/). A biblioteca nesse caso funciona como um polyfill que provê ao navegador suporte a essa tecnologia, para isso basta adicionar o seguinte código no arquivo *execute_hatemile.js*.

```javascript
[...]
//Instancia a classe de soluções para os problemas de acessibilidade do CSS.
var accessibleCSS = new hatemile.implementation.AccessibleCSSImplementation(htmlParser, cssParser, hatemile_configuration_symbols);
//Provê o recurso aos leitores de tela as propriedades CSS speak, speak-as, speak-header, funcionando como um polyfill.
accessibleCSS.provideAllSpeakProperties();
```

### Disponibiliza todas as funções da página via teclado

No JavaScript existem eventos que só são disparados com ações do mouse ou dispositivos de entrada correspondentes, como o touchpad ou a tela touch: mousedown, mouseup, click, dblclick, mouseover, mouseout, drag, dragstart, dragend, dragenter, dragover, dragleave e drop.

A pessoas que possuem deficiência visual ou problemas na coordenação motora não utilizam o mouse como dispositivo de entrada, assim se faz necessário disponibilizar todas as funcionalidades da página através do teclado para tornar uma página acessível.

Para resolver esse problema de acessibilidade a biblioteca utiliza eventos do teclado equivalentes para executar os eventos do mouse, para isso basta adicionar o seguinte código no arquivo *execute_hatemile.js*.

```javascript
[...]
//Instancia a classe de soluções para os problemas de acessibilidade referentes aos eventos JavaScript inacessíveis via teclado.
var accessibleEvent = new hatemile.implementation.AccessibleEventImplementation(htmlParser);
//Faz com que os eventos de Drag-and-Drop possam ser utilizados através do teclado, utilizando espaço para selecionar o elemento, Enter para soltar o elemento selecionado sobre outro elemento e Esc para soltar o elemento selecionado.
accessibleEvent.makeAccessibleAllDragandDropEvents();
//Faz com que os eventos de passar o mouse sobre os elementos se tornem acessíveis pelo teclado.
accessibleEvent.makeAccessibleAllHoverEvents();
//Faz com que os eventos de click do mouse possam ser utilizados através do teclado selecionando o elemento e pressionando Enter.
accessibleEvent.makeAccessibleAllClickEvents();
```

### Fornecer instruções para a entrada de dados

O HTML possui atributos para restringir a entrada de dados do usuário, porém nem todos os navegadores e leitores de tela possuem a capacidade de informar essas restrições para o usuário. A biblioteca possuí a capacidade de fornecer essas instruções para os usuários, sendo necessário adicionar o seguinte código no arquivo *execute_hatemile.js*.

```javascript
[...]
//Instância a classe de soluções para elementos de formulários da biblioteca.
var accessibleForm = new hatemile.implementation.AccessibleFormImplementation(htmlParser, configuration);
//Utiliza o atributo aria-required para informar ao usuário quando um campo é obrigatório, pesquisando pelos elementos que possuem o atributo required.
accessibleForm.markAllRequiredFields();
//Utiliza os atributos aria-valuemin e aria-valuemax para informar ao usuário o valor mínimo e máximo de um campo, pesquisando pelos elementos que possuem os atributos min ou max.
accessibleForm.markAllRangeFields();
//Utiliza o atributo aria-autocomplete para informar ao usuário quando um campo possuí o recurso de autocompletar, pesquisando pelos elementos que possuem o atributo autocomplete.
accessibleForm.markAllAutoCompleteFields();
//Realiza validações nos campos e utiliza o atributo aria-invalid para informar ao usuário se um campo está com um valor inválido ou não.
accessibleForm.markAllInvalidFields();
```

### Facilidades de navegação para o usuário

As pessoas que possuem deficiência visual navegam de forma linear na web, devido as tecnologias utilizadas, sendo que dificilmente uma página possibilita a esse tipo de usuário ir para a área desejada diretamente. Nesse sentido a biblioteca provê duas formas de navegação que podem ser utilizadas de forma concomitante: a navegação através dos saltadores de conteúdo no início da página e através dos cabeçalhos da página (`<h1>`, `<h2>`, `<h3>`, `<h4>`, `<h5>` e `<h6>`).

Além disso o recurso de navegação para que o usuário possa ir para a descrição longa da imagem não é suportado por uma boa parte dos navegadores e quando esse recurso esta disponível é possível que só esteja disponível através do mouse.
Para resolver esses problemas de acessibilidade adicione o seguinte código no arquivo *execute_hatemile.js*.

```javascript
[...]
//Instancia a classe de soluções de navegação da biblioteca.
var accessibleNavigation = new hatemile.implementation.AccessibleNavigationImplementation(htmlParser, configuration, hatemile_configuration_skippers);
//Permite que o usuário possa navegar entre os cabeçalhos da página.
accessibleNavigation.provideNavigationByAllHeadings();
//Permite que o usuário possa saltar conteúdos da página pré-definidos pelo desenvolvedor.
accessibleNavigation.provideNavigationByAllSkippers();
//Permite que o usuário possa navegar para as descrições longas das imagens.
accessibleNavigation.provideNavigationToAllLongDescriptions();
```

### Associar elementos a outros elementos

Os leitores de tela muitas vezes possuem recursos interessantes como mostrar o conteúdo de um `<label>` quando um campo é selecionado ou ler o conteúdo de um cabeçalho de uma célula da tabela. Porém é possível que esse `<label>` não esteja associado ao campo utilizando o atributo `for` ~~(sim, ainda há pessoas que fazem com que o campo seja um elemento descendente de um label)~~ ou mesmo o leitor de tela só leia os cabeçalhos das células de dados apenas quando estes tiverem determinados metadados, para resolver esses problemas adicione o seguinte código no arquivo *execute_hatemile.js*.

```javascript
[...]
//Instancia a classe de soluções de problemas de associação
var accessibleAssociation = new hatemile.implementation.AccessibleAssociationImplementation(htmlParser, configuration);
//Associa as células de dados das tabelas sejam associadas com as células de cabeçalho 
accessibleAssociation.associateAllDataCellsWithHeaderCells();
//Associa os rótulos aos seus respectivos campos, caso já não estejam associados
accessibleAssociation.associateAllLabelsWithFields();
```

### Disponibilizar informações não suportadas pelo agente de usuário

Mesmo com o desenvolvedor utilizando corretamente os padrões WEB e [WAI-ARIA](https://www.w3.org/WAI/intro/aria), é possível que o leitor de tela não suporte tal recurso ou mesmo o navegador não passe essa informação para o leitor de tela.

Até mesmo os usuário que não possuem deficiência visual podem desconhecer recursos interessantes implementados na página devido a falta dessa informação fornecida pelo navegador, como por exemplo as teclas de atalho que podem ser utilizadas para facilitar na navegação da página.

Para resolver esse tipo de problema adicione o seguinte código no arquivo *execute_hatemile.js*.

```javascript
[...]
//Instancia a classe para forçar o leitor de tela a disponibilizar informações sobre a página.
var accessibleScreenReader = new hatemile.implementation.AccessibleDisplayScreenReaderImplementation(htmlParser, configuration, navigator.userAgent);
//Força o leitor de tela a mostrar para o usuário o atributo “role” utilizado nos elementos.
accessibleScreenReader.displayAllRoles();
//Força o leitor de tela a mostrar para o usuário os cabeçalhos das células de dados das tabelas.
accessibleScreenReader.displayAllCellHeaders();
//Força o leitor de tela a mostrar para o usuário todos os atalhos da página, definidos pelo atributo “accesskey”.
accessibleScreenReader.displayAllShortcuts();
//Força o leitor de tela a mostrar para o usuário os valores do WAI-ARIA.
accessibleScreenReader.displayAllWAIARIAStates();
//Força o leitor de tela a mostrar para o usuário alguns atributos dos links.
accessibleScreenReader.displayAllLinksAttributes();
//Força o leitor de tela a mostrar para o usuário o conteúdo dos títulos dos elementos.
accessibleScreenReader.displayAllTitles();
//Força o leitor de tela a mostrar para o usuário quando um elemento pode ser arrastado, onde pode ser solto e qual a ação que será executada.
accessibleScreenReader.displayAllDragsAndDrops();
//Força o leitor de tela a mostrar para o usuário qual o idioma do elemento.
accessibleScreenReader.displayAllLanguages();
```

## Conclusão

A acessibilidade na web apesar do seu crescimento ainda não é o suficiente para atender a demanda das pessoas com necessidades especiais e apesar de não ser um assunto novo, apenas recentemente ela vem ganhando a devida atenção, surgindo várias iniciativas para aumentar a acessibilidade na web.

Mesmo assim ainda estamos carentes de ferramentas que possam resolver de forma automática os problemas de acessibilidade e essa biblioteca foi desenvolvida tanto para tentar mudar um pouco a situação atual como também para instigar o desenvolvimento de novas soluções.
