---
title: Bower na prática
author: Diogo Beato
type: post
date: 2014-01-15
excerpt: Um dos grandes problemas encontrados no desenvolvimento de software é o gerenciamento de dependências. Saiba como o Bower pode ajudar.
url: /bower-na-pratica/
categories:
  - Código
  - Técnicas e Práticas
tags:
  - assets
  - bower
  - CSS
  - html
  - js
  - ruby

---
A maioria das linguagens já possuem ferramentas para automatizar e facilitar esse tipo de tarefa.
  
Por exemplo: Java &#8211; (Maven e Ivy), Ruby &#8211; (Rubygems), Python &#8211; (pip), entre outras.

No desenvolvimento front-end, uma ferramenta que vem ganhando bastante espaço nessa área é o <a title="bower.io" href="http://bower.io/" target="_blank">Bower</a>.

Como o bower é para gerenciar componentes de front-end, pode ser adicionado em qualquer projeto, independente do seu back-end ser Java, Ruby, Python, Node, PHP, etc.

Andei pesquisando a respeito dessa ferramenta e senti a falta de artigos em português que ensinem o passo-a-passo de como incorpora-lo em nossas aplicações, por isso resolvi escrever esse tutorial, ajudar com que todos possam dar seus primeiros passos com o <a title="bower.io" href="http://bower.io/" target="_blank">Bower</a> e melhorar o gerenciamento de dependências dos seus respectivos front-ends.

## Instalação

Inicialmente é necessário primeiro que você tenha o [Node][1] junto com o [NPM][2] instalado na sua máquina. Caso contrário, basta acessar o [nodejs.org][1], fazer download e instalar. Bem simples!

Feito isso, vamos para o terminal/cmd e instalar o bower com o seguinte comando:

<pre class="sh">npm install -g bower</pre>

Para quem ainda não conhece, o [NPM][2]  é um gerenciador de pacotes de programas que rodam com o Node. Aqui estamos basicamente mandando ele instalar o bower no nosso computador, uma coisa que gostaria de ressaltar é a opção `-g` que está dizendo para o npm instalar o bower globalmente em nossa máquina, assim ele já fica nas nossas variáveis de ambiente e podemos utiliza-lo facilmente em outros projetos.

## Adicionando o Bower ao projeto

Nesse exemplo, vamos ilustrar um projeto web simples, sem back-end, mas garanto que vai ficar fácil de entender como incorpora-lo ao seu projeto, independente da linguagem. Caso vocês tenham alguma dúvida, perguntem nos comentários que vou me esforçar para ajudar.

Nosso projeto vai se chamar **&#8220;zombie-striker&#8221;** e terá a seguinte estrutura:

<pre>|zombie-striker/
|--assets/
|----scripts/
|----styles/
|----images/
|--index.html</pre>

Para adicionarmos o bower, vamos até a pasta do projeto &#8220;/zombie-striker&#8221; e digitar o comando:

<pre>bower init</pre>

O bower irá iniciar um wizard para gerar o arquivo &#8220;bower.json&#8221; pedindo pra você completar as seguintes informações:

<pre># nome do projeto
name:zombie-striker 

# versão do projeto
version:0.0.1

# descrição do projeto
description: app to strike zombies with bower

# arquivo principal do seu projeto
main file: assets/scripts/main.js

# palavras-chaves 
keywords: zombie striker

# autores do projeto
authors: "Diogo Vecchiati http://divecch.com"

# tipo de licença
license: MIT

#homepage do projeto
homepage: "https://github.com/diRex/zombie-striker"

# se você gostaria que o bower adicionasse os components já instalados, como dependências no arquivo json.
set currently installed components as dependencies?(y/n) n

# se você gostaria de adicionar o ignore list default do bower
add commonly ignored files to ignore list?(y/n) y

# se você gostaria de tornar esse pacote privado para que não seja acidentalmente publicado no registro de pacotes do bower.
would you like to mark this package as private which prevents it from beig accidentally published to the registry?(y/n) y</pre>

**Observação**: Algumas das opções acimas são válidas apenas para pacotes que vão ser distribuídos como novos componentes, por exemplo: caso você esteja criando um novo framework e queira disponibilizar aos demais através do bower .Porém, não é nosso caso, então podemos utilizar o &#8220;bower.json&#8221; gerado pelo wizard e modificar de acordo com a nossa necessidade. Caso você queira, pode pular a etapa de wizard do `bower init` e  criar o &#8220;bower.json&#8221; na mão com as opções que você queira.

Ao terminar o wizard, você terá um &#8220;bower.json&#8221; parecido com esse:

<pre>{
	"name": "zombie-striker",
	"version": "0.0.1",
	"authors": [
		"Diogo Vecchiati &lt;http://divecch.com&gt;"
	],
	"description": "app to strike zombies with bower",
	"main": "assets/scripts/main.js",
	"keywords": [
		"zombie"
	],
	"license": "MIT",
	"homepage": "https://github.com/diRex/zombie-striker",
	"private": true,
	"ignore": [
		"**/.*",
		"node_modules",
		"bower_components",
		"test",
		"tests"
	]
}</pre>

## Adicionando dependências

Como de costume na maioria dos projetos front-end, vamos utilizar o JQuery como dependência. Vou mostrar duas maneiras de fazer isso.

#### Editando o arquivo &#8220;bower.json&#8221;

Você pode editar o seu arquivo &#8220;bower.json&#8221; e adicionar

<pre>...
	"ignore": [
		"**/.*",
		"node_modules",
		"bower_components",
		"test",
		"tests"
	]
        "dependencies": {
                "jquery": "~2.0.3"
        }
}</pre>

e em seguida executar:

<pre>bower install</pre>

Toda vez que você executa o `bower install`, ele verifica quais as dependências existentes no seu arquivo &#8220;bower.json&#8221; e caso elas não estejam presentes na pasta de componentes serão instaladas.

#### Executando o comando bower install

Outra maneira é executando o camando `bower install <package>`

<pre>bower install jquery --save</pre>

A opção `--save` serve para adicionar o componente no &#8220;dependencies&#8221; do &#8220;bower.json&#8221;.

Por padrão, o diretório que o bower utiliza pra salvar os componentes instalados é &#8220;bower_components/&#8221;, caso você queira modificar, basta criar um arquivo chamado &#8220;.bowerrc&#8221; com o seguinte conteúdo:

<pre>{
	"directory":"assets/components"
}</pre>

Depois de alterar o diretório dos componentes, o ideal é que você remova o diretório anterior, &#8220;bower_componentes&#8221; e execute o `bower install`, pra ele fazer download das dependências novamente. Ou simplesmente renomeie 😛

Para importar o jquery no nosso projeto é o mesmo &#8220;arroz com feijão&#8221;, só adicionar a tag script no html:

<pre>&lt;script src="assets/components/jquery/jquery.min.js"</pre>

## Pesquisando componentes

Caso você queira pesquisar mais componentes para adicionar ao seu projeto, é só utilizar o `bower search`. Por exemplo, quero adicionar o bootstrap ao meu projeto, mas não sei o nome correto do pacote.

<pre>bower search bootstrap</pre>

Assim você consegue listar todos os pacotes que tenham relação com o bootstrap, é bem confuso de ver no terminal,como acontece na pesquisa de qualquer gerenciador de pacotes, mas da pra encontrar.

## Dicas

#### Não versione o diretório de componentes

Não versione a pasta que vc estiver utilizando pra salvar os componentes gerenciados pelo bower, se a sua pasta for a padrão(&#8220;bower_components/&#8221;), coloque no seu .gitignore, assim você deixa seu repositório mais leve e evita conflitos de libs que foram adicionadas por diferentes desenvolvedores.

#### Atenção com as dependências

Mantenham todas as dependências configuradas no &#8220;bower.json&#8221; algumas vezes pode acontecer de você executar um `bower install jquery`, esquecer da opção `--save` ou esquecer de adicionar manualmente no &#8220;bower.json&#8221; Quando outro desenvolvedor for participar do seu projeto e executar um `bower install`, o jquery não vai estar lá.

#### Ferramenta visual para pesquisa de pacotes

Outra forma de visualizar os componentes registrados no bower de maneira mais agradável é através do site: <http://sindresorhus.com/bower-components/>.

**That&#8217;s all folks**, espero que tenham gostado, que passem a utilizar o bower em seus projetos, pois facilita muito controlar quais dependências existentes no projeto. Se quiserem pesquisar mais sobre as possibilidades que o bower oferece, basta acessar o site oficial: <http://bower.io/>.

Qualquer dúvida, critica ou sugestões comentem aqui em baixo.
  
[]&#8217;s !!!

 [1]: http://nodejs.org/
 [2]: https://npmjs.org/ "npmjs.org"