---
title: Workflow para cuidar dos seus assets
author: Jean Carlo Emer
type: post
date: 2013-10-31
excerpt: O termo assets é utilizado na economia para caracterizar todo recurso que se poderá tirar proveito no futuro. Mas não se preocupe, nosso assunto aqui é sobre desenvolvimento web.
url: /workflow-para-cuidar-dos-seus-assets/
dsq_thread_id: 1922824496
categories:
  - Artigos
  - Código
  - HTML
  - JavaScript
  - Técnicas e Práticas

---
No desenvolvimento web, o termo assets é utilizado para designar tudo o que complementa o conteúdo dos websites. Em outras palavras, assets são nossos recursos de folhas de estilo, scripts, fontes e imagens.

Em uma primeira análise, os assets parecem algo simples de se gerenciar. Porém, o que passa muitas vezes por desapercebido é que a falta de alguns cuidados podem impactar significativamente na performance do projeto notada pelo usuário.

Apesar dos sintomas da baixa performance serem muito mais notados no front-end, uma estratégia adequada de gerência deve iniciar já no back-end das aplicações. Muito por isto, programadores Ruby criaram a biblioteca Sprockets que tem como função compilar e servir assets da melhor maneira possível. Seu principal uso se dá através do Asset Pipeline, parte integrante do framework de desenvolvimento Ruby on Rails.

O que segue é uma análise detalhada das principais funcionalidades do workflow do Asset Pipeline destacando quais os impactos positivos que são refletidos para os projetos que o utilizam.

## Asset Pipeline

As principais funcionalidades do framework são: pré-compilar, concatenar, minificar e ajudar para que o navegador faça o cache dos arquivos adequadamente.

### Pré-compilação

Linguagens como [CoffeeScript][1] e [Sass][2] têm se tornado cada vez mais maduras e utilizadas no processo de desenvolvimento. Este texto não tem o caráter de defender quais os benefícios de uso de cada uma delas. Mas é importante que, se você optar ou precisar utilizar alguma delas, seu workflow suporte o seu uso.

O Asset Pipeline e outros frameworks similares provêm uma maneira bastante simples de indicar por quais linguagens e engines o arquivo precisa ser avaliado. Eles fazem isto através da extensão do arquivo. Assim, é só nomear o arquivo com a extensão `.coffee` para indicar que seu conteúdo está escrito em CoffeeScript.

Mais do que indicar uma linguagem, é possível fazer com que um mesmo arquivo seja avaliado por mais de uma liguagem ou engine através do uso de outros indicadores no nome do arquivo. Um arquivo de nome `main.js.coffee.erb`, seria avaliado pela engine de template Erb e posteriormente interpretado como CoffeeScript. Nestes casos, o resultado de cada avaliação, que são iniciadas pela extensão mais a direita, é então utilizado como insumo para a próxima avaliação.

### Concatenação

Apesar de folhas de estilo e código JavaScript ainda não possuírem construções nativas de módulos, a simples tarefa de separação do código em diferentes arquivos já garante maior legibilidade e facilidade de manutenção.

Por outro lado, queremos continuar entregando a menor quantidade possível de assets no front-end da aplicação. Para tal, precisamos concatenar os arquivos. A maneira de concatenar os arquivos de JavaScript no Asset Pipeline é a seguinte:

<pre class="prettyprint lang-javascript linenums">//= require jquery
//= require jquery.ui
//= require main</pre>

E para concatenar folhas de estilo:

<pre class="prettyprint lang-ruby linenums">/*
*= require normalize 
*= require layout
*= require header
*/</pre>

Vale lembrar que depois de concatenados os arquivos, a referência da linha em que determinado código foi declarado é perdida, o que pode dificultar o _debugging_. O Asset Pipeline, quando em ambiente de desenvolvimento, inclui todos os arquivos no HTML sem concatenar através de diferentes `<script>` e `<link>`. Desta forma, é muito mais fácil identificar qual o arquivo e linha de cada diretiva.

A partir disto, notamos que o workflow que cuida dos assets **precisa necessariamente ter acesso** à aplicação para poder, como neste caso, flexibilizar o uso de diferentes arquivos com base no ambiente.

Vale ressaltar que soluções de workflow escritas nos dias atuais podem utilizar [Source Maps][3], o que também é possível no Asset Pipeline, para chegar a um resultado semelhante.

### Minificação

Último passo do seu workflow, minificar os arquivos garante aquela economia esperta da banda larga do usuário. E, assim como na concatenação, você **não** vai querer que os arquivos estejam minificados em seu ambiente de desenvolvimento.

Novamente, o Asset Pipeline não minifica seus arquivos quando em ambiente de desenvolvimento. As ferramentas geralmente utilizadas para a tarefa em ambiente de produção são: minificador do Sass para as folhas de estilos e [UglifyJS][4] para JavaScript.

### Cache

O ponto mais importante relacionado aos assets é a configuração adequada do tempo de expiração de cada arquivo. Porque, no pior dos casos, em decorrência disto o usuário será obrigado a baixar todas as imagens e demais recursos a cada acesso a uma diferente página do seu website.

Pegando como exemplo a configuração de tempo de expiração dos arquivos do [HTML5 Boilerplate][5], é possível notar que os assets possuem em geral um tempo de expiração de um mês. Grosseiramente, isto significa que o usuário irá baixar determinado arquivo novamente apenas daqui um mês.

Os benefícios são óbvios, os malefícios talvez nem tanto. Se o projeto sofrer manutenção e aquela imagem importante for alterada, o usuário não necessariamente terá a nova versão. A solução é renomear os arquivos (e não apenas a [querystring][6]) a cada alteração para que assim o usuário seja obrigado  a baixar a nova versão.

O Asset Pipeline viabiliza esta estratégia adicionando um código ao nome de todos os arquivos, o `main.css` é renomeado para algo como `main-dc409308c085b71ae34d793cedb384a1.css`. O código é relacionado ao conteúdo do arquivo, o que significa que se eu alterar qualquer caractere, este código muda e o nome do meu arquivo também.

Por fim, o Asset Pipeline provê o método `asset_path` para que eu possa saber o nome do meu arquivo já com o código. Basta utilizar a pré-compilação, e o arquivo de folha de estilo `main.css.erb` será avaliado pela engine de template que irá traduzir `<%= asset_path('logo.png') %>` para o nome da imagem já com o código.

Mesmo não sendo um processo tão simples, não existe melhor estratégia na atualidade para garantir que os usuários possam manter arquivos no cache e ao mesmo tempo baixar imediatamente apenas os arquivos que tenham sido alterados em uma manutenção da sua aplicação. Antes que alguém comente, renomear a pasta de todos os assets não garante que apenas os arquivos alterados necessitem ser baixados, todos serão.

## Outros frameworks

Entendi, você achou as funcionalidades do Asset Pipeline fantásticas e compreendeu na teoria e prática a importância de cada uma delas. Mas se a sua aplicação não é escrita em Ruby on Rails, é possível utilizar [somente o Sprockets][7]. De qualquer maneira, você vai precisar de Ruby e perderá alguns recursos.

Vale ressaltar que qualquer linguagem de back-end pode implementar um workflow igual a este. E com certeza ele deve ser copiado e aprimorado. Já existem inclusive plugins em desenvolvimento para o [Grunt][8]. Quem sabe você não possa colaborar com algum deles.

 [1]: http://tableless.com.br/javascript-com-cafe
 [2]: http://tableless.com.br/sass-um-outro-metodo-de-escrever-css
 [3]: http://www.html5rocks.com/en/tutorials/developertools/sourcemaps
 [4]: https://github.com/mishoo/UglifyJS
 [5]: https://github.com/h5bp/html5-boilerplate/blob/9518d22de739a1b03bdbfcde2149e1fd994c280a/.htaccess#L445
 [6]: http://www.stevesouders.com/blog/2008/08/23/revving-filenames-dont-use-querystring
 [7]: https://github.com/DanielHeath/sprockets-sample
 [8]: http://tableless.com.br/grunt-voce-deveria-estar-usando