---
title: Servindo sites estáticos com Jekyll
author: Diego Eis
type: post
date: 2013-11-11
excerpt: Entenda como o Jekyll funciona e como ele pode te ajudar a fazer websites estáticos, sem banco de dados e fáceis de gerenciar.
url: /jekyll-servindo-sites-estaticos/
dsq_thread_id: 1954136445
categories:
  - Código
  - HTML
  - Técnicas e Práticas
tags:
  - html
  - jekyll
  - markdown
  - ruby
  - websites

---
O [Tableless produz código front-end][1] HTML/CSS/JAVASCRIPT para vários tipos de clientes, grandes ou pequenos. Os clientes querem ao final do projeto arquivos estáticos, em uma estrutura de arquivos decente e código bem organizado e isso não é algo tão trivial assim.

## O problema

O primeiro problema que temos quando iniciamos a produção de um site, é como resolver as partes de layout que são repetidas em todas as páginas do projeto, por exemplo: header, footer, sidebar e essas coisas. Já vi vários dos meus alunos mantendo sites com dezenas de páginas, sem nem ao menos usar um simples include de PHP. Eu os perdoo por que a maioria estava começando. Mesmo assim é algo muito amador manter um site dessa forma. No Tableless, durante algum tempo, por conveniência, usávamos simples includes do PHP para prevenir repetições. Escolhemos PHP por conveniência, [já que produzimos muitos sites em WordPress][2].

Um dos problemas estava resolvido. O segundo problema era: como entregar isso para o cliente?
  
Eu não poderia simplesmente enviar um pacote com vários arquivos **.php** para um cliente que trabalhava com ASP ou Python.
  
Logo começamos a usar o **wget** para percorrer o projeto e transformar as páginas em HTML estático. Não demorou muito para desistirmos disso. Embora seja tudo automático, não era o ideal. Precisávamos ter algo mais inteligente para isso. Foi aí que surgiu em nossas vidas algumas ferramentas para gerar sites estáticos. Conhecemos o Jekyll, Middleman e alguns outros. Hoje vamos falar um pouco do [Jekyll][3].

## Jekyll

O Jekyll é um gerador de códigos estáticos. A ideia é que você crie páginas e até mesmo um blog de forma estática, usando HTML que você já conhece, junto com alguns truques que irão ajudá-lo a converter seu site em arquivos estáticos, pronto para ser publicado. Ele é baseado em vários formatos como Markdown para formatação de textos e posts e um padrão de template chamado Liquid com um pouco de YAML para exibir e guardar os dados das variáveis. Não se preocupe com a sopa de letras, por enquanto. Mais à frente no texto você vai entender um pouco mais.

## Estrutura de diretórios

A coisa toda é muito simples: todo o arquivo que tiver **_** (underline) na frente do nome, o Jekyll vai ignorar no pacote final, quando converter seu projeto. Veja uma estrutura de um dos nossos projetos:

<img src="http://tableless.com.br/uploads/2013/11/Screen-Shot-2013-11-10-at-5.09.22-PM.png" alt="Screen Shot 2013-11-10 at 5.09.22 PM" width="265" height="277" class="alignnone size-full wp-image-39447" srcset="uploads/2013/11/Screen-Shot-2013-11-10-at-5.09.22-PM.png 265w, uploads/2013/11/Screen-Shot-2013-11-10-at-5.09.22-PM-160x168.png 160w" sizes="(max-width: 265px) 100vw, 265px" />

A pasta **_includes** guarda arquivos que serão reutilizados nas páginas do projeto, tipo o header, footer, sidebar e etc ou qualquer outra coisa de acordo com sua necessidade.

Na pasta **_layouts** você vai colocar os padrões de layout de páginas. Imagine que existam páginas com formatos de estruturas diferentes. É aí que você vai organizar essas coisas.

Para você ter um exemplo, nesse projeto fizemos apenas uma estrutura básica que usamos para home e para as páginas internas. Embora as páginas tenham estruturas diferentes, decidimos usar apenas um arquivo default para incluir por padrão em todas as páginas o header e o footer. As estruturas das páginas foram definidas de acordo com o código específico em cada uma das páginas. Veja o código do arquivo **default.html**:

<pre class="lang-yaml">{% include header.html %}

{{ content }}

{% include footer.html %}
</pre>

Ridículo, né?
  
Ah! O `{{ content }}` é uma variável que exibe o conteúdo das páginas. É como o `the_content()` do WordPress. É ali que o Jekyll vai inserir o conteúdo das páginas que você criar. No nosso caso, o código encontrado em **defail-view.html, index e results**.

A pasta **_site** é o build do seu projeto. É ali que o Jekyll coloca a versão final estática do site, pronto para ser publicado. 

Tem gente que deixa a pasta _site versionável no GIT, tem gente que bota no **.ignore**. Aí vai de você decidir o que achar melhor.

As URLs ficam assim:

<pre class="lang-bash">.
|-- _config.yml
|-- _includes/
|-- _layouts/
|-- _posts/
|-- _site/
|-- detail-view.html    # =&gt; http://projeto.com/detail-view.html
|-- index.html    # =&gt; http://projeto.com
└── results.html  # =&gt; http://projeto.com/results.html
</pre>

Se você inserir um arquivo **index.html** nas pastas, a url das páginas vão ficar assim:

<pre class="lang-bash">.
|-- _config.yml
|-- _includes/
|-- _layouts/
|-- _posts/
|-- _site/
|-- detail-view/
|---- index.html    # =&gt; http://projeto.com/detail-view/
|-- index.html    # =&gt; http://projeto.com
|-- results/
└──── index.html    # =&gt; http://projeto.com/results/
</pre>

## Estrutura de código

A estrutura de código dos arquivos é muito simples de se entender, mas para alguns pode ser um pouco estranha por não ter familiaridade com estruturas de dados como YAML. Mas isso é simples e você aprende rápido, tenho certeza. Continue lendo para você ver como é fácil.

### Sem banco de dados

Para começar, você não mantém um banco de dados e é isso que faz toda a graça. O conteúdo do seu site ficar guardado nos arquivos de cada página. Você não precisa levantar um servidor de MySQL. Todas as informações do site estarão nos arquivos que você criar para cada página. Ou seja, nada de queries, nada de templates tags do WordPress.

#### YAML e Liquid

O formato YAML é conhecido pela facilidade de leitura. Ele foi criado para ser fácil da gente entender e também escrever. Ou seja, ele é um formato simples para escrevermos manualmente, mas também para manipularmos via programação. É aqui que o Jekyll começa a ficar legal. Essa estrutura é usada também no Middleman e no DocPad. Logo, aprendendo aqui, você já vai saber mais ou menos como funciona nos outros geradores. 

Qualquer arquivo que contém um bloco YAML &#8211; que o pessoal do Jekyll chama de **front-matter** &#8211; será processado como um arquivo especial. O front-matter **precisa ser a primeira coisa do arquivo** e deve estar num formato válido de YAML. Toda página do seu site feito em Jekyll precisa começar com essa estrutura:

<pre class="lang-yaml">---
layout: default
title: Home
---
</pre>

Simples, ahn? O bloco é demarcado pelos três traços no começo e no fim. TEM que ser três traços. Nem mais, nem menos. O código YAML são as duas variáveis **layout** e **title**.

Neste bloco você pode usar variáveis predefinidas ou criar suas próprias variáveis. Essas variáveis estarão disponíveis para você acessar usando as tags do formato Liquid. Você já vai ver mais abaixo, primeiro vamos entender as duas variáveis acima.

A variável **layout** indica que você está usando a estrutura de template do **default.html**. Lembra a estrutura de arquivos e diretórios que mostramos logo no início? Os nomes que você coloca ali na variável **layout** são os nomes dos arquivos que estão dentro da pasta **_layouts**, sem a extensão **.html**. Logo, se você tiver um arquivo ali dentro chamado **no-sidebar.html**, indicando um formato de página que não vai ter sidebar, o valor da variável **layout** será **no-sidebar**. Fica assim:

<pre class="lang-yaml">---
layout: no-sidebar
title: Página Interna
---
</pre>

A segunda variável é a **title**. Aqui é uma variável criada por mim, que será usada para ser o título da página. Veja abaixo como a gente puxa o valor da variável **title** que definimos acima, usando o formato Liquid.

<pre class="lang-html">&lt;!DOCTYPE html&gt;
&lt;html lang="pt-br"&gt;
&lt;head&gt;
	&lt;title&gt; {{ page.title }} &lt;/title&gt;
	&lt;meta charset="utf-8"&gt;
&lt;/head&gt;
&lt;body&gt;
...
</pre>

O **{{ page.title }}** está dizendo que nesse local, ao renderizar o site, o Jekyll irá colocar o título da página atual. 

O formato [Liquid][4] é um formato de template muito simples. A sua sintaxe é muito parecida com outros tipos de padrões de templates, como por exemplo o [Mustache.js][5]. Logo, não tem muito segredo. Você abre duas chaves **{{**, coloca o nome da variável e depois fecha com duas chaves novamente **}}**.

#### Entendendo mais sobre as variáveis

Você usa o prefixo **page** para puxar os dados da página. Qualquer coisa que esteja ali no front-matter vai ser puxado usado o **page** antes. Se você quiser pegar o nome do site, por exemplo, ou qualquer outra coisa referente ao site inteiro, você usa o prefixo **site**. Um exemplo:

<pre class="lang-html">&lt;!DOCTYPE html&gt;
&lt;html lang="pt-br"&gt;
&lt;head&gt;
	&lt;title&gt; {{ page.title }} - {{ site.name }} &lt;/title&gt;
	&lt;meta charset="utf-8"&gt;
&lt;/head&gt;
&lt;body&gt;
...
</pre>

Nesse caso, as informações referentes ao site não estarão no **front-matter**, mas em um arquivo de configuração, que o Jekyll vai ler sempre quando for iniciado. Esse arquivo se chama **_config.yml**. Você vai escrevê-lo no mesmo formato que o front-matter. Um exemplo:

<pre class="lang-yml"><strong>name:</strong> Nome do Projeto
<strong>source:</strong>      .
<strong>destination:</strong> ./_site
<strong>plugins:</strong>     ./_plugins
<strong>layouts:</strong>     ./_layouts
<strong>css_folder:</strong>  'assets/stylesheets'
<strong>js_folder:</strong>  'assets/javascripts'
<strong>img_folder:</strong>  'assets/images'
<strong>include:</strong>     ['.htaccess']
<strong>exclude:</strong>     []
<strong>keep_files:</strong>  ['.git','.svn']
<strong>timezone:</strong>    nil

...

</pre>

Há outras variáveis globais que podem não estar aí no **_config.yml**. Por exemplo a **{{ site.pages }}** que retorna a lista de páginas do site.

Há uma série de variáveis disponíveis [aqui][6] e você pode ver as [variáveis globais aqui][7].

### Entendendo o _config.yml

O **_config.yml** guarda as configurações do seu projeto. Ele deve estar sempre no root do seu projeto. Sempre que você inicia um novo projeto Jekyll, ele cria um _config.yml. Você pode ver um exemplo abaixo:

<pre class="lang-yml">source:      .
destination: ./_site
plugins:     ./_plugins
layouts:     ./_layouts
include:     ['.htaccess']
exclude:     []
keep_files:  ['.git','.svn']
gems:        []
timezone:    nil
encoding:    nil

future:      true
show_drafts: nil
limit_posts: 0
pygments:    true

relative_permalinks: true

permalink:     date
paginate_path: 'page:num'

markdown:      maruku
markdown_ext:  markdown,mkd,mkdn,md
textile_ext:   textile

excerpt_separator: "\n\n"

safe:        false
host:        0.0.0.0
port:        4000
baseurl:     /
url:         http://localhost:4000
lsi:         false

maruku:
  use_tex:    false
  use_divs:   false
  png_engine: blahtex
  png_dir:    images/latex
  png_url:    /images/latex

rdiscount:
  extensions: []

redcarpet:
  extensions: []

kramdown:
  auto_ids: true
  footnote_nr: 1
  entity_output: as_char
  toc_levels: 1..6
  smart_quotes: lsquo,rsquo,ldquo,rdquo
  use_coderay: false

  coderay:
    coderay_wrap: div
    coderay_line_numbers: inline
    coderay_line_numbers_start: 1
    coderay_tab_width: 4
    coderay_bold_every: 10
    coderay_css: style

redcloth:
  hard_breaks: true
</pre>

Para ficar mais fácil, eu ainda adiciono uma ou outra opção personalizada no _config.yml, como por exemplo o caminho do CSS e do Javascript:

<pre class="lang-yml">css_folder:  'assets/stylesheets'
js_folder:  'assets/javascripts'
img_folder: 'assets/images'
</pre>

Assim eu chamo os assets assim:

<pre class="lang-html">&lt;!DOCTYPE html&gt;
&lt;html lang="pt-br"&gt;
&lt;head&gt;
	&lt;title&gt; {{ page.title }} - {{ site.name }} &lt;/title&gt;
	&lt;meta charset="utf-8"&gt;

	&lt;link rel="stylesheet" type="text/css" href="{{ site.css_folder }}/bootstrap.min.css"&gt;
	&lt;link rel="stylesheet" type="text/css" href="{{ site.css_folder }}/style.css"&gt;

&lt;/head&gt;
&lt;body&gt;

...

</pre>

Bem legal, né?
  
Não precisa entender todas as variáveis que eles colocam ali no **_config.yml**. Basta entender que dá para criar novas variáveis personalizadas e que você pode modificar os valores das variáveis existentes. Há muita coisa ali que você não precisa usar. Mesmo assim, se você tiver muitos outros dados para usar, você pode importar em formato YAML entro da pasta **_data**, que eu não vou detalhar sobre isso aqui, por enquanto.

### Quick start

Para iniciar um projeto e começar a fuçar nas coisas é fácil.

<pre class="lang-bash">~ $ gem install jekyll
~ $ jekyll new nome-projeto
~ $ cd nome-projeto
~/nome-projeto $ jekyll serve --w
</pre>

O parâmetro **&#8211;w** ou **&#8211;watch** serve para que a cada vez que você fizer uma modificação nos arquivos do projeto, o Jekyll faz um build automático do projeto. Aí é só fazer um refresh no site e ver as modificações.

O Jekyll vai subir seu site na porta :4000, é só seguir para: http://localhost:4000/
  
Lembre-se que você precisa ter Ruby instalado na sua máquina, já que o Jekyll é uma GEM.

Feito isso, dá uma fuçada na pasta do projeto. Você vai perceber que existe uma pasta **_posts** que eu não citei nesse artigo.
  
O Jekyll pode ser usado para criar um blog. Os posts são arquivos escritos em Markdown e que são automaticamente transformados em arquivos HTML e guardados em pastas organizadas por ordem cronológica. Coisa fina! Talvez em um próximo post eu explique melhor esse módulo.

## Conclusão

Eu, pessoalmente, prefiro Jekyll ao Middleman. Os dois são bem parecidos. Mas eu acho Jekyll bem mais simples. Eu uso Middeman em outros projetos e vou tentar preparar um post explicando o básico para vocês sobre ele.

Se você tem Windows e estiver muito afim de fazer isso tudo funcionar, leia esse post do Nando ensinando como faz para instalar [Ruby, Rails, MySQL e Git no Windows][8] ou compra um Mac.

A comunidade Ruby ajudou muito o mundo front-end com várias ferramentas que ajudam a automatizar processos de desenvolvimento. É por isso que geralmente os front-ends que trabalham em projetos com Ruby conseguem se virar melhor em determinados pontos. Mas essa é uma outra história. 😉

 [1]: http://tableless.com.br/servicos/front-end.php
 [2]: http://tableless.com.br/servicos/wordpress.php
 [3]: http://jekyllrb.com
 [4]: http://docs.shopify.com/themes/liquid-basics
 [5]: http://tableless.com.br/templates-client-side-com-mustache-js/
 [6]: http://jekyllrb.com/docs/frontmatter/
 [7]: http://jekyllrb.com/docs/variables/
 [8]: http://simplesideias.com.br/configurando-ruby-rails-mysql-e-git-no-windows