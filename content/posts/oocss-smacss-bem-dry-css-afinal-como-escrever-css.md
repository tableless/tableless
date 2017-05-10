---
title: 'OOCSS, SMACSS, BEM, DRY CSS: afinal, como escrever CSS?'
author: Jean Carlo Emer
type: post
date: 2014-06-23
excerpt: Conheça os principais estilos de escrita de CSS e aprenda o que você pode extrair deste mar de siglas para escrever código melhor.
url: /oocss-smacss-bem-dry-css-afinal-como-escrever-css/
dsq_thread_id: 2789992839
titulo_personalizado:
  - 'OOCSS, SMACSS, BEM, DRY CSS: afinal, <strong>como escrever CSS?</strong>'
categories:
  - Artigos
  - CSS
  - Técnicas e Práticas

---
Já sabemos que se tratando de CSS, apesar da escrita ser muito simples, há uma série de armadilhas. Começamos não utilizando `!important` ou `tags` para estilização, [considerando o peso dos seletores][1] e adotando um _code standard_. Mas ainda não damos tanta atenção para a arquitetura que está intimamente ligada a futuros conflitos. Um conflito de CSS é fruto de código mal escrito que cancela regras ou as aplicada em porções inadequadas do _layout_.

Saiba que não se trata de aprender algumas técnicas a mais, antes que alguém deixe um dos muito comentários infelizes que figuram em outros textos do assunto, trata-se essencialmente de reconhecer soluções para um problema pertinente e comum. **É preciso pensar como organizar nosso código CSS**. Melhor ainda, devemos planejar qual será a **o estilo de arquitetura** da nossa folha de estilo.

## Conceitos básicos

A experiência nos mostra aquilo que Phil Karlton já dizia: uma das tarefas mais árduas da computação é a de nomear coisas. E isto é o que fazemos o tempo todo quando escrevemos CSS, definir quais serão nossos seletores. Esta tarefa envolve organização, padronização, planejar reutilização e uma série de outras disciplinas.

Um ponto pertinente é compreendermos o significado de semântica, que define a relação entre símbolos e seu significado, neste contexto. Nicolas Gallagher escreveu um texto sensacional sobre [semântica no HTML e sua não relação com semântica da arquitetura do front-end][2]. A semântica das _tags_ do HTML e Microdata está muito bem definida nas especificações e deve ser respeitada. Através dela é possível para humanos e máquinas melhor interpretar as informações contidas em um documento.

Por outro lado, ao contrário daquilo que muitos pensam, não há nenhuma semântica a ser seguida quando atribuímos classes a um elemento. **Não existe classe não semântica**, já que seu significado deve ser estabelecido em cada projeto.

## Object Oriented CSS

O conteúdo de um website geralmente é bem específico em cada uma das páginas. É pouco comum que o mesmo conteúdo se manifeste em diferentes seções de um projeto. Portanto, **classes nomeadas com base no conteúdo são bastante difíceis de serem reusadas**.

Segundo o OOCSS, um _objeto de CSS_ é todo **padrão visual** que pode se repetir no projeto e é identificado através de uma classe. O estilo enfatiza a separação de propriedades de estrutura e de _skin_. Propriedades como `background`, `color` e `border`, quando fizerem parte da identidade visual do projeto, são consideras parte do _skin_ e devem ser agrupadas em classes próprias. Observe a classe de _skin_ `anchor-icon`, que define um `background`, utilizada juntamente com duas classes de estrutura: `<button class="button anchor-icon">Abrir</button>` e `<a class="link anchor-icon">Tableless</a>`.

O uso dos objetos ao longo do projeto não deve causar surpresas, o que significa que sua localização não deve interferir na sua apresentação. Isto significa não utilizar _nesting_ de seletores. Caso sejam necessárias variações, objetos podem estender outros diretamente no HTML: `<div class="graph graph-big">`.

Classes como `.wrapper`, `.image-replacement` e `.clearfix` aparecem em alguns exemplos que aplicam este sistema. O argumento é que se tratam de classes de estrutura com um padrão que pode ser reusado. Um exemplo: `<div class="graph graph-big clearfix wrapper">`.

O maior ensinamento é o de utilizar classes baseadas na aparência ao invés de conteúdo ou até mesmo funcionalidade, que até pouco eu acreditava ser o ideal. Apesar dos demais conceitos serem interessantes, a documentação é vaga e não há um padrão de nomenclatura que diferencie classes de estruturação e de _skins_.

## SMACSS

O sistema estabelece e é bastante baseado em cinco categorias de regras de CSS: _base_, _layout_, _module_, _state_ e a pouco importante _theme_. As regras de _base_ são as do tipo que não utilizam seletores com classes ou ids, as encontramos em um _CSS Reset_ ou _normalize.css_. O sistema alerta sobre a [agressividade dos _CSS Resets_][3] mas não alerta sobre as regras deste tipo definidas no próprio projeto, ainda mais quando aplicadas a _divs_, _spans_ ou _headings_. **Regras cujos seletores não utilizam classes são globais e qualquer decisão tomada neste nível irá perpetuar por todo o projeto, cuidado**.

As categorias de _layout_ e _module_ são bastante semelhantes. Pense no _layout_ como elementos agregadores e geralmente únicos como _header_, _footer_ e _sidebar_. O sistema propõe que regras de _layout_ tenham ids ou classes com o prefixo `.l-` como seletores.

As regras da categoria _module_ englobam os demais componentes da página. O sistema não encoraja o uso de elementos nos seletores, preferindo `.box .title` ao invés de `.box h2`. Ainda, o seletores como `.box-title` são defendidos para facilitar a leitura do HTML.

Assim como o OOCSS, o sistema repudia regras do tipo `#sidebar .media` onde a localização do elemento passa a ser relevante para sua apresentação. O SMACSS reforça que seja adicionada uma classe para abrigar as variações. O elemento da _sidebar_ passa a ter a classe do módulo e também a do sub-módulo: `<div class="media media-sidebar">`.

A categoria de _state_ engloba regras responsáveis por gerenciar estado de componentes enquanto o usuário estiver navegando. Regras desta categorias são as únicas que podem e talvez precisem utilizar `!important`. O padrão indica que as classes possuam o prefixo `.is-`. Com certeza, algum dos seus projetos já precisou de uma classe como `.is-active`, `.is-collapsed` ou `is-current`.

O SMACSS é mais uma série de tutoriais de como escrever um bom código que propriamente um sistema de CSS. Contra os padrões, **não concordo com qualquer aparição de #id em folhas de estilos** por ir contra os preceitos de reuso. O atributo id na realidade serve mais como um destino de navegação, por isto a necessidade de ser único. Considero um pouco estranho também o prefixo `l-` para as classes de _layout_, o que me atreve a desconsiderar totalmente a categoria e a gerir suas regras como se pertencessem a categoria _module_. Não existe necessidade desta distinção nos seletores, apenas separar as regras em um arquivo `layout.css` já é suficiente.

A categoria de _state_ é a mais interessante, o padrão fica muito conveniente para ser utilizado em código JavaScript. Quando o estado de um componente demanda regras muito específicas, o SMACSS sugere o seletor `.is-tab-active`. Desta maneira, o JavaScript perde um tanto da sua modularidade, seletores aninhados como `.tab.is-active` podem ser uma melhor jogada.

Por fim, mesmo sendo [bastante válido][4], o SMACSS não soluciona alguns desafios típicos do _design_ de componentes de médio porte pois em nenhum momento endereça como nomear adequadamente elementos descendentes.

## BEM

O BEM &#8211; sigla para _block_, _element_, _modifier_ &#8211; é uma metodologia com várias versões cujo o preceito de esclarecer o desenvolvedor mais sobre o _markup_ através de suas classes. **Este sistema permite escrever sites de maneira rápida, auto-explicativa e com manutenção descomplicada**. Esqueça seus preconceitos com os caracteres duplos de hifen, eu já deixei o meu de lado, e reflita a seguir o quanto mais de informação a classe `.report-graph__bar_size_big` oferece em relação as tradicionais `.bar`, `.report-graph-bar` ou `.graph-bar`.

O _block_ é uma entidade independente da aplicação, podendo ser o mais alto nível de abstração (_header_, _footer_) ou componente (_graph_, _tabs_). O _element_ é um descendente dependente de um _block_ que possui uma certa função. Para permitir nomes compostos e evitar ambiguidades, o padrão estabelece o controverso `__` como separador. Desmembrando a classe `report-graph__bar`, identificamos _bar_ como _element_ e sabemos da existência do elemento pai _report-graph_, que é o _block_.

O estilo define o _modifier_ como uma propriedade de um _block_ ou _element_ que altera sua aparência. Desta maneira, o _block_ `.menu` poderia ser acrescido da classe `.menu_size_big`, note o uso de `_`.

A fim de deixar o padrão um pouco mais claro, veja um exemplo:

      <div class="report-graph">
        <div class="report-graph__bar">...</div>
        <div class="report-graph__bar report-graph__bar_size_big">...</div>
      </div>
    

As classes `.report-graph`, `report-graph__bar` e `report-graph__bar_size_big` são, respectivamente, _block_, _element_ e _modifier_. Neste ponto você já deve ter refletido e concluído que sim, há muito mais informação numa classes nomeada neste padrão.

Uma das falhas do estilo é não possuir categorias como as do SMACSS. Segundo o padrão, o estado de um componente deve ser endereçado como um _modifier_, não há uma categoria de _state_. Conforme citei anteriormente, classes _modifier_ como `.menu__item_state_current` tiram a modularidade do JavaScript fazendo com que o código dependa do componente. Alguns desenvolvedores também podem sentir falta do estilo não versar nada sobre regras aplicadas diretamente a elementos (categoria _base_ do SMACSS) e boas práticas de CSS.

O grande trunfo do padrão é mesmo sugerir uma nomenclatura adequada para elementos descendentes. Outro aspecto interessante é o padrão de [organização de arquivos][5].

## DRY CSS

O princípio consiste em não repetir propriedades com mesmos valores em seu código. De maneira simples, a todo momento que isto for necessário, estas propriedades devem ser agrupadas e endereçadas por vários seletores. O sistema define que o agrupamento seja nomeado através de um primeiro seletor, algo como `#MEDIUM-WHITE-BACKGROUND` para um agrupamento de `background` e `border` brancas. As custas deste primeiro seletor, muitos desenvolvedores confundem que o _pattern_ sugere que este seletor seja usado no HTML, o que não é verdade.

A técnica, assim como outros sistemas, sugere que seu código seja pensando em termos de padrões de aparência. O problema está no fato da técnica não sugerir melhor uso das classes de CSS. Segundo o sistema, sempre que a aparência de um elemento mudar, sua classe precisará ser movida para outros agrupamentos nas folhas de estilo. Sistemas como SMACSS e BEM endereçam mudanças de aparência com a criação de um submódulo ou modificador que será adicionado ao HTML evidenciando a alteração e permitindo manter a antiga aparência.

Não entenda mal, os conceitos por trás do DRY CSS são válidos. Inclusive, já [sugeri uma variação da técnica em conjunto com _placeholders_ do SASS][6] para nomear propriedades que definem um elemento da aparência do seu projeto. Os _placeholders_ carregam os conceitos de DRY CSS e ainda permitem basear sua arquitetura em outros sistemas mais poderosos.

## Afinal, como escrever CSS

Como você deve ter reparado, todas os sistemas possuem conceitos e abordagens para escrever código melhor e acredito um pouco em cada um deles. Não vai adiantar muito pular para esta conclusão em busca de repostas, os conceitos já foram todos explorados.

Saiba também que não é por nada que _Atomic CSS_ não aparece no texto, sem levar em conta a metodologia e apesar das [tentativas em convencer][7], não enxergo valor em classes como `.mt-20` e códigos como o do site [My Yahoo!][8].

Voltando ao ponto, por incrível que pareça, o ideal é mesmo misturar os sistemas. Uma boa referência é a [convenção do projeto SUIT CSS][9]. O projeto convenciona três categorias de classes: utilitárias, componentes e estado; cada uma seguindo um sistema. Classes utilitárias (OCSS) são estruturais, de baixo nível e possuem prefixo `.u-`: `.u-clearfix`, `u-row`, `u-span2`. Os componentes definem uma variação de BEM que introduz os sinais `--` para designar os `modifiers`. Vale a nota que este uso dos hifens é erroneamente atribuído ao BEM, que na realidade define unicamente _underscores_. Por fim, o sistema define classes de estado dos componentes seguindo o padrão do SMACSS.

O projeto [SUIT CSS][10], mantido por ninguém menos que Nicolas Gallagher, criador do normalize.css, é uma fonte incrível para se observar como definir classes seguindo esta mistura mágica de _pattenrs_. Um pequeno ponto contra a nomenclatura do projeto é o uso de classes em `CamelCase`. Portanto, deixarei logo abaixo uma pequena variação em `lowercase` para facilitar o entendimento e servir como um guia simples:

    /* Utility */
    .u-utility-name {}
    
    /* Component */
    .block-name {}
    .block-name__element-name {}
    .block-name--modifier-name {}
    
    /* State */
    .is-global-state {}
    
    /* Component state (scoped to component) */
    .block-name.is-state-of-component {}
    

Acima de tudo, é essencial evoluirmos nosso entendimento sobre a importância da busca por um sistema para evitar conflitos de código e facilitar reuso até mesmo entre diferentes projetos. A adoção de um sistema abstrai o raciocínio repetitivo de buscar nomes para as classes e permite escrever CSS com um pouco menos de culpa.

 [1]: http://josh.github.io/css-explain
 [2]: http://nicolasgallagher.com/about-html-semantics-front-end-architecture
 [3]: http://stackoverflow.com/a/8357635
 [4]: http://www.smashingmagazine.com/2012/04/20/decoupling-html-from-css
 [5]: http://bem.info/method/filesystem
 [6]: http://tableless.com.br/css-steroids
 [7]: http://www.smashingmagazine.com/2013/10/21/challenging-css-best-practices-atomic-approach
 [8]: https://my.yahoo.com
 [9]: https://github.com/suitcss/suit/blob/master/doc/naming-conventions.md
 [10]: https://github.com/suitcss