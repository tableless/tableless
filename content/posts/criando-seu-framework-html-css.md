---
title: Criando seu próprio Framework HTML CSS
author: Bernard De Luna
type: post
date: 2013-01-07
excerpt: 'Um Framework pode ser o responsável pelo sucesso da sua aplicação e lhe poupar milhares de dólares, assim como pode representar o gargalo do desenvolvimento do seu produto e levar o seu projeto ao fracasso. '
url: /criando-seu-framework-html-css/
dsq_thread_id: 995672744
categories:
  - Código
  - CSS
  - HTML
tags:
  - bernard de luna
  - bootstrap
  - button
  - form
  - formee
  - foundation
  - framework
  - grid
  - smacss
  - twitter

---
Em 2011, principalmente em 2012, dezenas de pessoas vinham e voltavam com o assunto &#8220;Qual o melhor Framework?&#8221;, fora os bootstrap fanboys de plantão que falavam tão cegamente do Twitter Bootstrap que se somasse todos os amores da internet teriamos um &#8220;cupcake de gato dançando Gangnam Style após tentar beber 1 litro de absolute&#8221; bootstrape. Eu sempre falo isso no meio das minhas palestras e começo dizendo no início desse post: Sejamos menos emotivos e mais analistas em Front-end, explico a seguir:

Nossa função é analisar as possibilidades, testar as inovações, medir os riscos e otimizar os resultados. Testar frameworks como Twitter Bootstrap, Foundation, &#8230; é parte do nosso trabalho, onde em muitos casos a pessoa esquece a melhor parte: **Criar o seu próprio Framework Front-end**.

## Por que você deseja criar seu próprio Framework?

  * Nenhum dos frameworks tem o objeto que eu preciso
  * Eu quero total controle sobre o código
  * Eu preciso de algo mais simples ou menos objetos do que os outros possuem
  * Aprender a criar um Framework por diversão e aprendizado

## Por que você não deve criar o seu próprio Framework?

  * Você não tem tempo disponível para criá-lo
  * É mais vantajoso utilizar um já pronto do que criar um do zero
  * Maior produtividade por utilizar algo já criado e documentado

Se você teve mais afinidade a primeira lista, ou é apenas curioso, vamos começar com alguns tópicos que o levarão a criar o &#8220;defina o nome a sua escolha&#8221; bootstrap.

## Tudo depende da nomeclatura e organização

Para componentizar sua página de maneira sustentável você precisa explorar ao máximo a organização e padronização do projeto. Quando eu analiso código de alguns profissionais ou empresas, sempre começo olhando pelos nomes utilizados em classes, pois me diz muito sobre a política da empresa na hora da criação das páginas, por exemplo:

<pre class="prettify lang-html">Botão = .button, .botao, .btn, .bt</pre>

A partir da escolha do padrão, você precisa mantê-lo nas variações

<pre class="prettify lang-html">.btn-enviar, .btn-cancelar, .btn-salvar, .btn-pesquisar, ...</pre>

Então geramos uma redundância no prefixo, que é uma coisa boa quando falamos em padrão e organização

<pre class="prettify lang-html">&lt;a href="#" title="salvar" class="btn btn-salvar"&gt;Salvar&lt;/a&gt;</pre>

A partir daí você vai seguir a mesma linha para demais diferenciações e se são diferenciais específicas do componente de botão ou se é uma variação genérica, como visto abaixo:

<pre class="lang-html">/* classe full específica */
&lt;a href="#" title="salvar" class="btn btn-salvar btn-full"&gt;Salvar&lt;/a&gt;

/* classe full generica */
&lt;a href="#" title="salvar" class="btn btn-salvar full"&gt;Salvar&lt;/a&gt;
</pre>

Assim, podemos contextualizar para outros artefatos e seus devidos prefixos:

<pre class="lang-html">Botão = .button, .botao, .btn, .bt
Tabela = .table, .tabela, .tbl, .tb
listas = .list, .lista, .group
widgets = .widgets, .wid
títulos = .title, .tit, .tt, .header, .h
</pre>

e algumas devidas personalizações

<pre class="lang-html">Botão = .btn-primary, .btn-secondary, .btn-small, .btn-medium, .btn-loading, .btn-disabled
Tabela = .tbl-roles, .tbl-full, .tbl-small
Tooltip = .tooltip, .tooltip-pin-up, .tooltip-pin-down, .tooltip-small, .tooltip-warning
</pre>

**OBS: É óbvio que estou dando exemplos e você deve construir seus padrões com a sua equipe e profissionais envolvidos no processo.**

### Revisando

  * A parte mais primordial para a construção de um Framework sustentável é o trabalho de nomeclaturas e seu emprego no código
  * O nome dado ao componente deve vir como prefixo das suas diversificações
  * Caso uma das variações seja utilizada em outros componentes, ela pode ser utilizada sem prefixo como &#8220;full, clear, left, right, error&#8221;
  * Mapeie a nomeclatura e as possibilidades com sua equipe, nunca sozinho

## Coloque todos seus padrões em um único local

Um bom framework é reconhecido pela reutilização de seu código, sendo assim, você não pode contar que seus elementos caibam, se alinhem e harmonizem apenas no local pre desenhado, por isso, você precisa criar uma página que apresente todos os elementos padronizados, a fim de testá-los e documentá-los. Repare nas duas páginas abaixo:

  * Twitter Bootstrap: <a href="http://twitter.github.com/bootstrap/components.html" title="http://twitter.github.com/bootstrap/components.html" target="_blank">http://twitter.github.com/bootstrap/components.html</a>
  * Foundation: <a href="http://foundation.zurb.com/docs/elements.php" title="http://foundation.zurb.com/docs/elements.php" target="_blank">http://foundation.zurb.com/docs/elements.php</a>

Agora que está convencido, você precisa criar essa página de apresentação onde você listará os componentes padronizados. Em um primeiro momento você pode inserir os componentes na página, agrupando (Veja os links acima para inspirar-se) da maneira que achar mais organizada. Essa etapa lhe dará mais segurança, pois a cada componente finalizado, você e sua equipe comemorará pelo padrão criado. Lembre-se que mais do que criar os componentes é preciso sempre dar 360 nos seus artefatos, identificando pontos de melhoria ou bugs, tratando e atualizando-os nessa página de padrões.

### Adendo para projetos responsivos

Caso você tenha variações padronizadas para projetos responsivos, não os considere na mesma página, por mais que a mudança possa ser percebida na mudança do viewport, crie uma página &#8220;padrao-mobile.html&#8221; ou algo do tipo com o local útil já reduzido simulando a largura do device pretendido, pois os padrões precisam ser facilmente visualizados, nenhuma equipe ficaria contente toda hora tendo que redimensionar navegador para ver o elemento normal e para mobile né?

### Revisando

  * Todos os componentes padronizados precisam ser incluídos em uma página separada da aplicação para documentação e validação
  * Se o elemento estará pronto quando puder ser reutilizado em outros locais sem quebrar (geralmente por má herança CSS)
  * Agrupe os elementos (form, títulos, botões, grid, etc) para manter a organização do seu projeto
  * Planeje e organize os padrões com sua equipe, nunca sozinho

## Módulos, produtos, componentes e(ou) artefatos

Os nomes são variados, pode chamar como achar mais fofo, mas o importante é saber que qualquer framework utiliza itens comuns, então comece por eles e, a partir daí, desenvolva em cima das suas necessidades menos comuns. Os componentes comuns são:

  * Grid
  * Tipografia
  * Botões
  * Formulários

Claro que cada projeto pedirá necessidades especiais, cabendo a você e sua equipe serem flexíveis e espertos. Vamos conversar rapidamente sobre cada um desses 4 componentes?

### Grid

Lembro de quando eu criei o <a href="http://formee.org" title="formee framework" target="_blank">Formee framework</a> e penava com cálculos e mais cálculos para chegar ao Grid flexível perfeito, foram muitas páginas de caderno rabiscadas com contas e mais contas. O Grid é uma parte perigosa do projeto, principalmente por exigirem algumas escolhas desde o começo, como:

  * Usarei float para diagramação?
  * Usarei algum pre processador como Less, Sass ou Stylus?
  * Usarei colunas em pixels ou colunas flexíveis?
  * Minhas colunas serão responsivas?

A partir daí, você tem uma série de Grids famosos para você estudar e basear o seu projeto, alguns fugindo do float, gerando projetos mais interessantes, porém menos seguros para browsers não atuais (não, não me refiro apenas a IE); alguns utilizando contas dos pre processadores, gerando larguras e espaçamentos automáticos de acordo com o container; alguns utilizando colunas flexíveis (exemplo do Formee) que podem ser muito interessantes para muitos projetos, mas começa a gerar desconforto em containers muito pequenos e alguns utilizando colunas responsivas, que podem refazer todo o pensamento dos 3 primeiros itens dessa lista.

Uma dica para quem está estudando o desenvolvimento de GRIDs é pesquisar sobre o atributo CSS **`box-sizing`** que é responsável por mudar o display do box model, passando a considerar o padding e border na hora de aparecer na largura/altura final, o box-model convencional não os considera na largura e altura, somando no resultado os valores, ou seja, 300px de largura acaba se tornando 300px + 2px de borda + 10px de padding = 312px total.

Outro ponto mais avançado que vocês precisarão trabalhar em cima é a parte da criação do grid. Atualmente você tem duas formas de fazê-lo:

<pre class="lang-html">&lt;div class="grid-6-12"&gt;&lt;/div&gt;
&lt;div class="grid-6-12"&gt;&lt;/div&gt;
</pre>

ou

<pre class="lang-html">&lt;div class="row"&gt;
&lt;div class="col-6"&gt;&lt;/div&gt;
&lt;div class="col-6"&gt;&lt;/div&gt;
&lt;/div&gt;
</pre>

Conseguem entender a diferença? O primeiro é comum em projetos onde você não tem controle sobre a quantidade de divs, assim você cria algo e vai administrando, do outro lado, você controla a diagramação linha por linha. O problema da primeira é o famoso bug de float, que quando um dos elementos rouba mais altura e impacta no elemento da linha de baixo, ele gera um buraco, desorientando os demais irmãos, o problema da segunda é que com isso você engessa totalmente o seu código, prejudicando inclusive a liberdade de uma diagramação criativa para mobiles.

Rabisque para chegar numa largura confortável do seu grid, conte com um espaçamento confortável entre as colunas, teste, teste, teste e teste.

### Tipografia

Precisamos definir os elementos textuais da aplicação, geralmente são títulos, listas, parágrafos e links. É bastante importante você simular todas as combinações possíveis na etapa de testes, pois sempre pode gerar algum incomodo pro usuário, por exemplo, você ter um título grande, um parágrafo de 2 linhas e outro título grande não é a mesma coisa que 1 título grande e 5 parágrafos grandes, tudo isso precisa ser testado. 

Para você conhecer um pouco mais sobre tipografia na parte de Front-end, recomendo a <a href="https://github.com/necolas/normalize.css/wiki" title="https://github.com/necolas/normalize.css/wiki" target="_blank">wiki do Normalize.css criado pelo Nicolas Gallagher</a> que retrata a falta de padronização na mostragem dos elementos textuais entre os browsers. Eu tenho algumas considerações sobre essa filosofia, mas quem sabe isso fica para um outro post 🙂

### Botões

Creio que a melhor forma de começar a criar seus padrões é pelo grupo de botões, pois é bastante simples e gostoso de criar. Geralmente em um aplicativo existem 2 tipos de botões, primário e genérico. O botão primário(`.btn-primary`, `.btn-cta`) é o botão das funções principais da página, é o botão de ação final e por isso mais importante, enquanto o botão genérico é utilizado para funções variadas que não sejam a função principal do usuário, a relação primário/genérico é a mesma de salvar/cancelar, avançar/upload photo, etc.

Alguns projetos acabam necessitando de outros padrões no botão como, por exemplo, `.btn-secondary` para botão de importância secundário, mas ainda sim não genérico, e `.btn-error.btn-no.btn-delete` para botões que tenham uma carga negativa (vermelho talvez) clara neles para o usuário saber que pode ser perigosa tal opção.

Geralmente, os botões possuim algumas particularidades comuns em todos os projetos como o .small para uma versão mais minimalista, .full para uma versão de ocupar toda a largura do container. Uma possibilidade é botões com ícones, assim sendo, primeiro é necessário criar um agrupamento de padrões chamados ícones, depois você precisa estudar se o elemento botão precisa sofrer alguma mudança por ter o ícone dentro, caso sim, seria interessante pensar em um padrão focado no &#8220;estado&#8221; do botão, podendo ser `.btn-icon`, seguindo o padrão de `.btn-disabled`, `.btn-loading`, ou até mesmo criar um prefixo que indica as chamadas **&#8220;state rules&#8221;**, mais difundida atualmente pelo <a href="http://smacss.com/book/type-state" title="http://smacss.com/book/type-state" target="_blank">SMACSS</a>, segue um exemplo:

<pre class="lang-css">a.is-disabled { 
  color: gray;
}
.btn.is-disabled { 
  background: gray;
}
</pre>

Assim, o `"is-"` passa a ser um padrão que pode ser reutilizado em diversos componentes, trazendo formatações diferentes. Então você pode criar dois &#8220;states&#8221; se achar interessante no seu projeto, um seria o `"is-"` para `.is-loading`, `.is-active`, `.is-disabled`, e criar outro chamado `"has-"` como `.has-icon`, `.has-photo`, `.has-offer`, etc.

### Formulários

Formulário, assim como o Grid é um elemento bastante complexo, pois exige muito estudo e testes. Você deve estar pensando &#8220;Ah! Estilizar um input é muito simples&#8221;, e estilizar uma lista de checkbox, radio? E personalizar um select para ele ficar mais interessante no Chrome (atualmente é horrível), e você considerar os novos inputs HTML5 como tel, search, range, e MUITOS outros e tratar de uma forma bacana pro seu app, por isso é bom você realizar testes e padrões.

O **`box-sizing`** citado no Grid é um bom amigo para elementos de formulário também, pois você consegue controlar a largura dele de forma segura, visto que elemento como input não ocupará a linha toda só por ser display: block, você precisará definir largura 100%, daí ele somará o padding e a borda e quebrará seu grid. Mudando o box-sizing, você consegue dizer que o padding e a borda fará parte do 100% de largura, ficando bem mais fácil, não acha?

Não se esqueça que mensagens de erro, sucesso, atenção, inputs com erros, labels, precisam ser padronizados e também colocados na página com os padrões no agrupamento de formulário. É bastante importante que esse arquivo seja visto pelos desenvolvedores back-end também, para que eles possam até já utilizar os padrões na hora de fazerem testes ou qualquer prototipagem, facilitando na hora da manipulação.

## Javascript não é um plus

Melhor do que a padronização visual, a padronização de classes, html e css, é ter também a padronização do funcionamento e manipulação desses componentes. Assim, o desenvolvedor front-end deve se arriscar a padronizar também o javascript, permitindo a reutilização do mesmo e manipulando dentro do padrão perseguido. Tanto o Foundation quanto o Bootstrap são excelentes Frameworks, pois além de seus módulos prontos, possuem interações bem implementadas como modais, tooltips, slideshow, accordion, dropdown, e muitos outros que agregam diretamente no projeto.

## Conclusão

Nesses 8 anos de experiência específicos de desenvolvimento de aplicativos online, percebi que quanto mais padrões forem definidos em equipe, aumentamos mais a produtividade, diminuimos os erros no projeto, nos comunicamos melhor entre setores, perdas e ganhos de pessoas no time não gera uma grande perda de velocidade do time, e que a empresa fica sempre com um legado. A criação de um framework não é fácil, mas é bastante possível e, acredite, divertida. 

### Turbinando seu Framework

Separei 3 coisas não comentadas acima que eu faço quando desenvolvo meus frameworks atualmente:

  * Separo meu CSS em arquivos LESS como: reset, base, theme, responsive. Tenho um style.less que compila todos num único CSS, mas mantendo a organização do projeto, o que é muito difícil de fazer depois que se passa das 3 mil linhas.
  * De tanto em tanto tempo dou um 360 em uma dos padrões criados
  * Apresento meu rascunho de planejamento do padrão para o Designer responsável (se houver) para que o mesmo possa alinhar os agrupamentos na hora de criar o <a href="http://www.onextrapixel.com/2012/09/28/30-handy-and-free-ui-kits-for-web-and-mobile/" title="http://www.onextrapixel.com/2012/09/28/30-handy-and-free-ui-kits-for-web-and-mobile/" target="_blank">UI kit</a>.

**E você já criou o seu próprio Framework?** Conte aqui sua experiência 🙂