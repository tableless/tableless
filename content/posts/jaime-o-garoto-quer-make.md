---
title: O básico sobre o automatizador de tarefas Make
author: Cristiano Santos
type: post
date: 2016-04-11
excerpt: Vocês trocariam seu Gruntfile (ou semelhantes) por um Makefile?
url: /jaime-o-garoto-quer-make/
titulo_personalizado:
  - 'Vocês trocariam seu Gruntfile ou Gulpfile <strong>por um Makefile?</strong>'
categories:
  - Artigos
  - Destaques
  - Técnicas e Práticas
tags:
  - linux
  - make

---
O trabalho no client-side é cercado por tarefas pequenas e frequentes. Por causa dessas tarefas frequentes, surgiram ferramentas fantásticas como Grunt, Gulp e vários outros.

Mas se voltarmos um pouco no tempo, vamos encontrar um cara chamado **MAKE**. Quem já instalou algum programa em alguma distribuição unix-like sabe bem do quem estou falando.

Esse era o processo básico pra instalar o programa.

<pre class="lang-bash">$ ./configure
$ make
$ make install
</pre>

Mas junto com isso, você precisava resolver uma série de problemas de dependências, caminhos de arquivos, permissões, versão e em último caso, ligava ou chamava quele amigo que manjava muito de Linux e implorava por ajuda.

Muitos podem ver esses problemas como algo ruim, mas observando melhor, isso faz com que você entenda para onde os arquivos estão indo e que para um programa funcionar, ele depende de outros programas e outras bibliotecas, que podem ter uma permissão especial para serem usados.

Tá mas que diabos é o Make e qual a relação dele com o Grunt ou Glup?

## Make

Basicamente o MAKE é um atomatizador de tarefas em ambientes unix que foi e é muito usado para compilar programas.

No processo básico de instalação que falei acima o que acontecia era o seguinte:

  1. `$ ./configure` era um script que depois de executado com sucesso criava o arquivo `Makefile`
  2. `Makefile` é o arquivo que dizia ao **make** quais eram as tarefas a serem realizadas para compilar o programa, essas tarefas eram feitas numa ordem topologica respeitando as dependências dos arquivos.
  3. `$ make install` esse comando chamava uma tarefa que estava definida no makefile e que tinha como objetivo fazer a instalação do programa compilado anteriormente.

<img class="aligncenter" src="http://cristianounix.github.io/img/posts/graph.png" alt="" width="420" height="273" />
  
Veja mais sobre ordenação topologica <a href="https://en.wikipedia.org/wiki/Topological_sorting" target="_blank">aqui</a>

O Make é nativo das plataformas Linux, mas caso não tenha basta instalar o pacote `build-essential`

<pre class="lang-shell">$ apt-get install build-essential</pre>

Antes de brincarmos com o Make, seria bom criar uma pasta em qualquer lugar de sua preferência, e dentro dela vamos criar nosso arquivo `Makefile`. Neste arquivo vamos colocar esse conteúdo (respeitando as tabulações):

<pre class="lang-bash">string = "Finalizando..."

all: task_all
task_all: dep1 dep2 dep3
  @echo $(string)
  @echo "Pronto !!"
dep1:
  @echo "Dependencia 1 "
dep2:
  @echo "Dependencia 2 "
dep3:
  @echo "Dependencia 3 "
  @echo
</pre>

Agora, via terminal e dentro dessa pasta, execute o make:

<pre class="lang-bash">$ make
----------------
Dependencia 1
Dependencia 2
Dependencia 3

Finalizando...
Pronto !!
</pre>

Legal, né?

Se quiser mudar a ordem de execução só alterar a linha abaixo:

<pre class="lang-bash">task_all: dep1 dep2 dep3</pre>

Para:

<pre class="lang-bash">task_all: dep3 dep2 dep1</pre>

Execute o make e observe a saída novamente. Percebeu que a ordem mudou?!

Você também pode chamar uma tarefa especifica, assim:

<pre class="lang-bash">$ make dep2</pre>

### Vamos fazer algo útil

Agora que sabemos o básico do make, vamos pensar em como poderiamos substituir uma tarefa simples do grunt, nosso problema será esse:

  1. Compilar nossos arquivos stylus
  2. Concatenar todos os arquivos
  3. Minificar

<pre class="lang-bash"># Compila, concatena e minifica todos os arquivos de estilo
# Obs: verifica se você tem disponivel os executaveis globalmente,
#     senão terá que colocar o path deles

PATH_STYL=styl/*.styl
PATH_CSS=css
STYLUS_CMD=stylus
CONCAT_CMD=cat 
CONCAT_PATH=styl/header.css styl/body.css styl/footer.css &gt; css/style.css
UGLIFY_CMD=uglify
UGLIFY_PATH=-s ./css/style.css -o ./css/style.min.css -c

all: task_all
task_all: compile concat minify clean
  @echo "Pronto !!"
compile:
  $(STYLUS_CMD) $(PATH_STYL)
  @echo "Stylus compilado..."
concat:
  $(CONCAT_CMD) $(CONCAT_PATH)
  @echo "Concatenando..."
minify:
  $(UGLIFY_CMD) $(UGLIFY_PATH)
  @echo "Minificando..."
clean:
  rm styl/*.css
  @echo "Limpando a bagunça..."
</pre>

A saída desse cara que nós acabamos de fazer vai ser algo assim:

<img class="aligncenter" src="http://cristianounix.github.io/img/posts/gif-make-makefile-front.gif" alt="" width="550" height="321" />

#### Vamos tentar deixar um pouco mais legal. {#vamos-tentar-deixar-um-pouco-mais-legal}

<pre class="lang-bash"># Compila, concatena e minifica todos os arquivos de estilo
# Obs: verifica se você tem disponivel os executaveis globalmente,
#     senão terá que colocar o path deles

CSS_FINAL = css/style.min.css
STYLUS_FILES = styl/header.styl \
                 styl/body.styl \
                 styl/footer.styl

CSS_MIN = $(STYLUS_FILES:.styl=.min.css) 

all: $(CSS_FINAL)
 
$(CSS_FINAL): $(CSS_MIN)
  cat $^ &gt;$@
  rm -f $(CSS_MIN)

%.min.css: %.styl
  stylus --compress &lt;$&lt; &gt;$@

clean:
  rm -f $(CSS_FINAL)
</pre>

#### Existem alguns variavéis do Make que devemos saber:

`$@` &#8211; isso mostra o nome target atual:

<pre class="lang-bash">all: blabla
  @echo "Ei"
blabla:
  @echo $@
# Saída será:
# blabla
# Ei
</pre>

`$<` &#8211; isso mostra o nome da primeira dependência:

<pre class="lang-bash">all: blabla vixi
  @echo "A dependencia desse target é" $&lt;
blabla:

vixi:

# Saída será:
# A dependência desse target é blabla
</pre>

`[$^]` &#8211; isso mostra a lsita das dependências do target:

<pre class="lang-bash">all: blabla vixi
  @echo "As dependências desse target são" $^
blabla:

vixi:

# Saída será:
# As dependências desse target são blabla vixi
</pre>

`[$?]` &#8211; Lista de todos arquivos de dependências mais recentes que a regra, a lista de arquivos é separada por espaço:

Crie 2 ou mais arquivos *.txt na pasta que irá ficar esse teste do makefile e coloquei qualquer texto dentro deles.

<pre class="lang-bash">HEAD_CMD=head
FILES=$(shell find . -name '*.o')

show: $(FILES)
       $(HEAD_CMD) $?

# Saída será:
# head file1.txt file2.txt file3.txt [...]
# ==&gt; file1.txt  file2.txt &lt;==
# [CABECALHO_2]
</pre>

`[$*]` &#8211; Nome do arquivo sem a extensão:

<pre class="lang-bash">CSS_FINAL = css/style.min.css
STYLUS_FILES = styl/header.styl  \
                 styl/body.styl \
                 styl/footer.styl 
CSS_MIN = $(STYLUS_FILES:.styl=.min.css)

all: $(CSS_FINAL)

$(CSS_FINAL): $(CSS_MIN)

%.min.css: %.styl
@echo "Arquivo -&gt;" $*

# Saída será:
# Arquivo -&gt; styl/header
# Arquivo -&gt; styl/body
# Arquivo -&gt; styl/footer
</pre>

Muita coisa legal dá pra fazer com o Make.

Dá para por exemplo você se conectar via ssh ou ftp e fazer o upload ou download de arquivos, rodar um shell script com diversas rotinas, você pode criar todo o setup da sua máquina colocando o make para instalar tudo que vc usa precisa: vim, mongodb, git, nodejs, sublime, brew, ou até mesmo configurar o deploy de sua aplicação, etc etc.

Isso só foi o ponto de partida, foi o básico do básico do básico e mais um pouco básico do que o make faz.

> Vocês trocariam seu Gruntfile (ou semelhantes) por um Makefile? 

(E por favor, não estou dizendo que as outras ferramentas são ruins, ou que você não deve usá-las. Quero apenas chamar a atenção para as ferramentas que já estão aqui há muito mais tempo e não conhecemos tão bem quanto pensamos.)

Referência suprema: <a href="http://www.gnu.org/software/make/manual/make.html" target="_blank">Manual Make</a>