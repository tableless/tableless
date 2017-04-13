---
title: Acelere o desenvolvimento front-end com Jade
author: Harryson Guimarães
type: post
date: 2015-08-03
excerpt: Aprenda a criar mixins, recursos de include, laços de repetição for, variáveis e muito mais no HTML com Jade.
url: /acelere-o-desenvolvimento-front-end-com-jade/
categories:
  - Código
  - HTML
  - Pré-processadores
tags:
  - JADE
  - Node

---
Certos elementos em nossos sites sempre se repetem, como o menu, o cabeçalho e o rodapé. Replicar o código desses elementos em cada página é uma péssima ideia. Imagine ter um site com mais de 100 páginas HTML e para cada uma, ter que codificar o mesmo menu, o mesmo cabeçalho e o mesmo rodapé. Além de ser algo extremamente trabalhoso, dar manutenção em um código desses é uma tarefa complicada. Imagine que para uma simples alteração de ano, geralmente encontrada no rodapé de muitos sites, seria necessário alterar 100 arquivos. O risco de esquecer algum deles e deixar suas páginas com um layout inconsistente é alto.

Com o advento do HTML5, existe uma nova especificação para reutilização de HTML. São os <a href="http://www.w3.org/TR/html-imports/" target="_blank">HTML imports</a>. Porém, sua <a href="http://caniuse.com/#search=import" target="_blank">adoção pelos navegadores atuais(07/2015) </a>ainda é mínima. Outra estratégia largamente utilizada é o uso do _include_ do _PHP_, como visto em <a href="http://tableless.com.br/otimizando-e-organizando-seu-front-end-com-php/" target="_blank">outro artigo</a> aqui mesmo no Tableless. Porém, essa não é uma solução elegante, já que depende de um servidor _PHP,_ e nem todo site/sistema é criado com base nessa estrutura de _backend_.

Entra em cena o _template engine_ <a href="http://jade-lang.com" target="_blank">Jade</a>. Com recursos para fazer _include_ de HTML e muitas outras funcionalidades, sua sintaxe é extremamente limpa, baseada em indentação, como o _Python_. No exemplo a seguir (retirado e adaptado do site oficial do projeto) compare seu equivalente transformado em HTML:

<a href="http://tableless.com.br/uploads/2015/07/Captura-de-Tela-2015-07-13-às-21.12.59.png" target="_blank"><img class="alignnone" title="JADE e HTML lado a lado" src="http://tableless.com.br/uploads/2015/07/Captura-de-Tela-2015-07-13-às-21.12.59.png" alt="Jade e o HTML gerado" width="800" height="357" /></a>

Todo começo de linha é interpretado como uma tag HTML, a menos que comece com o operador &#8220;|&#8221;. Neste caso, será interpretado como innerHTML, assim como o texto após uma tag e um espaço (visto na linha 4 da imagem acima).

No Jade, os atributos das tags são definidos dentro de parênteses, separados entre si por vírgula:

<pre class="lang-haml">form(name="form", novalidate)
  textarea(name="pergunta", required, id="pergunta")
  label(for="pergunta") Digite sua pergunta
</pre>

Equivalente em HTML:

<pre class="lang-html">&lt;form name="form" novalidate&gt;
  &lt;textarea name="pergunta" required id="pergunta"&gt;&lt;/textarea&gt;
  &lt;label for="pergunta"&gt;Digite sua pergunta&lt;/label&gt;
&lt;/form&gt;
</pre>

Ids e classes podem igualmente ser definidos dentro dos parênteses ou através de atalhos, onde `#` é um atalho para id e `.` é um atalho para classes:

<pre class="lang-css">div#container
  input#titulo.validate.bordered(type="text")
</pre>

O código acima irá gerar:

<pre class="lang-html">&lt;div id="container"&gt;
  &lt;input id="titulo" class="validate bordered" type="text"&gt;
&lt;div&gt;
</pre>

O Jade é muito mais que uma sintaxe limpa para seu HTML. Um grande recurso do Jade é o uso da herança de templates e _includes_. É possível criar uma página base e então criar páginas que estendam esta página com um conteúdo específico. Assim, conseguimos criar um template com os trechos que se repetem em nosso site, como o cabeçalho, o rodapé, etc. Abaixo, um exemplo de herança de templates do Jade:

<img class="alignnone" src="http://tableless.com.br/uploads/2015/07/Captura-de-Tela-2015-07-13-às-21.29.23.png" alt="Templates e includes" width="343" height="240" />

No arquivo layout.jade acima, é definido o template que será estendido por todas as outras páginas. É possível também visualizar o recurso de includes.

  * `include head` : arquivo head.jade, onde é carregado folhas de estilo, definido o title da página, o viewport, dentre outros;
  * `include cabecalho`: arquivo cabecalho.jade onde é carregado a logo do site;
  * `include menu`: arquivo menu.jade onde é inserido o menu do site. Pode também ser colocado junto com o cabecalho, mas aqui mantivemos em um arquivo separado;
  * `block contentBlock` : esse é o trecho que será sobrescrito por cada página que extender o layout.jade;
  * `include footer`: arquivo footer.jade com o rodapé do site (simplificado para melhor entendimento):

[<img class="alignnone wp-image-50039 size-full" src="http://tableless.com.br/uploads/2015/07/Captura-de-Tela-2015-07-13-às-22.07.49.png" alt="exemplo de footer do arquivo Jade" width="599" height="120" />][1]

O Jade &#8220;inclui&#8221; o código do arquivo no lugar onde ele invocado (onde foi feito o _include_). Criado o layout.jade, basta estender esse layout para cada página do seu site como visto no código abaixo:

[<img class="alignnone wp-image-50040 size-full" src="http://tableless.com.br/uploads/2015/07/Captura-de-Tela-2015-07-13-às-22.16.40.png" alt="contentBlock foi o nome do bloco definido no arquivo layout.jade para ser sobrescrito." width="746" height="172" />][2]

O nome _contentBlock_ foi definido no arquivo layout.jade para ser sobrescrito. Com o recurso de _includes_ e _extends_ conseguimos resolver o problema sem ter que replicar código HTML para várias páginas.

Outra funcionalidade que acelera nosso processo de desenvolvimento é o uso dos **_mixins_**. _Mixins_ reusam fragmentos de código HTML, possibilitando parametrizar certos pedaços de código. Vamos tomar como exemplo o _<a href="http://getbootstrap.com/components/#panels-alternatives" target="_blank">panel</a>_ do Bootstrap. Esse é o código usado para criar um _panel_:

<a href="http://tableless.com.br/uploads/2015/07/Captura-de-Tela-2015-07-13-às-23.23.28.png" target="_blank"><img class="alignnone wp-image-50050 size-full" src="http://tableless.com.br/uploads/2015/07/Captura-de-Tela-2015-07-13-às-23.23.28.png" alt="Código para criação de um panel no Bootstrap." width="636" height="393" /></a>

Não é tanto _markup_, mas que tal usarmos a estrutura de um _panel_ com apenas uma linha? Com o uso de _mixins_ isso é possível. Criamos uma estrutura inicial com o _markup_ de um _panel_, parametrizando o que for necessário como o título, o rodapé e o estilo do _panel_. Após criada essa estrutura (_mixin_) para inserir um _panel_, basta chamá-lo com o comando _+panel()_, passando os parâmetros desejados.

[<img class="alignnone wp-image-50150 size-full" src="http://tableless.com.br/uploads/2015/07/Captura-de-Tela-2015-07-15-às-21.59.46.png" alt="Mixin e seu uso" width="612" height="441" />][3]

O seguinte código gerou os _panels_ abaixo. Perceba, que na estrutura criada, se não informarmos um título, o _panel_ ficará sem o seu título. O mesmo para o rodapé. Se não informarmos a classe para estilizar o _panel_, nosso _mixin_ aplica a classe _panel-default_:

[<img class="alignnone wp-image-50151 size-full" src="http://tableless.com.br/uploads/2015/07/Captura-de-Tela-2015-07-15-às-21.58.49.png" alt="Panels com uso de mixins" width="579" height="488" />][4]

Note que no conteúdo do _mixin_, temos um _block_. Esse será o bloco substituído pelo conteúdo definido abaixo da chamada ao _panel_. Nesse _mixin_, é apresentado também o conceito de variáveis e o comando de decisão `if`. Perceba o grande poder que os _mixins_ nos proporciona. O exemplo acima é simples, mas podemos criar qualquer &#8220;componente&#8221; mais complexo e reutilizá-lo ao longo do nosso desenvolvimento.

Se interessou pelo Jade? Quer começar a usar hoje mesmo? No <a href="http://jade-lang.com" target="_blank">site oficial do projeto</a> você encontra um passo a passo de como usá-lo, além de documentação para outros recursos não citados nesse post. A princípio, a sintaxe do Jade pode parecer um pouco intimidadora, mas sua curva de aprendizado é rápida. Em questão de alguns minutos você já está familiarizado com sua estrutura.

Com o Jade também é possível gerar o HTML preservando a indentação ou configurando-o para remover espaços e quebras de linha, gerando um HTML &#8220;minificado&#8221;.

E se você utiliza algum automatizador de tarefas, basta adicionar o Jade ao seu workflow com o <a href="https://github.com/gruntjs/grunt-contrib-jade" target="_blank">Grunt</a> ou o <a href="https://github.com/phated/gulp-jade" target="_blank">Gulp</a>.

 [1]: http://tableless.com.br/uploads/2015/07/Captura-de-Tela-2015-07-13-às-22.07.49.png
 [2]: http://tableless.com.br/uploads/2015/07/Captura-de-Tela-2015-07-13-às-22.16.40.png
 [3]: http://tableless.com.br/uploads/2015/07/Captura-de-Tela-2015-07-15-às-21.59.46.png
 [4]: http://tableless.com.br/uploads/2015/07/Captura-de-Tela-2015-07-15-às-21.58.49.png