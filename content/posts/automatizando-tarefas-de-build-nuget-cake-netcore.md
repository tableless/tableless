---
title: Automatizando tarefas com Cake
excerpt: Saiba como automatizar tarefas de build, teste e deploy de pacotes Nuget com Cake e .Net Core.
authors: Wellington Nascimento
image: https://i.imgur.com/6gIyUPo.jpg
type: post
date: 2017-11-29
categories:
  - back-end
  - Na prática
tags:
  - asp.net
  - NetCore
  - task-runner
  - Cake
  - Nuget
---

É muito chato ter que fazer o build, rodar testes, executar a análise de 
qualidade do código, entre outras tarefas, de forma manual em nossas aplicações,
e o assunto se complica ainda mais quando temos que executar essas mesmas
tarefas em ferramentas de CI como é o caso do VSTS, GoCD, Jenkins, entre outros.

Já trabalhei com automação de pipelines de CI/CD com scripts PowerShell e Rake,
e além dessas, ainda existem diversas outras ferramentas de automatização de
tarefas como o Gulp, Fake, Psake, etc, e para nossa felicidade o Cake.

O [Cake](https://cakebuild.net/) é um automatizador de tarefas cross-platform
que roda em cima do compilador do C#, o Roslyn, sendo assim podemos escrever
nossos scripts de automação em C#. Com ele podemos criar tarefas de build,
execução de testes de unidade e cobertura de código, criação de pacotes Nuget,
deploy, entre diversas outras tarefas que podem facilitar a vida de todo bom
desenvolvedor preguiçoso… :)

Vamos começar nosso trabalho com uma aplicação bem simples de exemplo escrita em
.Net Core. Ela é bem pequena, possui apenas alguns métodos de extensão que
iremos disponibilizar na forma de pacote Nuget para aproveitar em outras
aplicações, afinal somos preguiçosos e não queremos reinventar a roda a cada
nova aplicação desenvolvida certo?!

> Ela já foi criada e está disponível no [meu Github](https://github.com/wellingtonjhn/csharp-extensions). Não esqueça de instalar o [.Net Core 2.0 SDK](https://www.microsoft.com/net/download) em seu computador.

## Instalando o [Cake](https://cakebuild.net/)

O primeiro passo para usar o [Cake ](https://cakebuild.net/)é obter seus scripts
de bootstrap, **build.ps1** (para windows) e **build.sh** (para linux/osx).

Para isso podemos usar os comandos de terminal na raiz do nosso repositório,
conforme a
[documentação](https://cakebuild.net/docs/tutorials/setting-up-a-new-project),
ou copiá-los do [repositório oficial do
Cake](https://github.com/cake-build/example).

Esses scripts são responsáveis por baixar todas as dependências necessárias para
usar o Cake em nosso projeto.

Caso esteja usando o Visual Studio Code, também é possível utilizar [este
plugin](https://marketplace.visualstudio.com/items?itemName=cake-build.cake-vscode)
do Cake para instalar os scripts necessários, conforme sua documentação

*****

## Script de tasks do Cake

O script que irá conter as tarefas também deve ficar na raiz do repositório e
ter o nome **build.cake**. Esse script será chamado automaticamente durante a
execução dos scripts *build.ps1* ou *build.sh.*

> O script completo está no repositório da aplicação de exemplo. Você pode clicar
> [aqui
](https://github.com/wellingtonjhn/csharp-extensions/blob/master/build.cake)para
acessá-lo diretamente. Neste artigo vamos passar por cada task separadamente
para melhor entendimento de cada passo do script.

## Aliases do Cake

O Cake usa um sistema de aliases que são métodos pré-definidos que você pode
usar em suas Tasks, como no exemplo abaixo. Neste caso o alias **Information**
escreve uma mensagem de log na saída do terminal, e faz parte dos aliases de
Logging do Cake:

    Task("Default")
    .Does(() => {
       Information("Hello World!");
    });

Dessa forma podemos usar os aliases já definidos no Cake ou usar algum
[Addin](https://cakebuild.net/addins) para métodos out-of-box. Também podemos
extendê-lo e criar nossos próprios Addins, mas fica para um outro artigo.

> Você pode encontrar uma listagem completa dos aliases suportados na
> [documentação ](https://cakebuild.net/dsl)do Cake.

Durante a primeira execução do script correspondente ao seu ambiente será criada
a pasta **tools **na raiz do projeto com todas as dependências de que o Cake
precisa. Adicione essa pasta no arquivo **.gitignore** do repositório para não
ser versionada, você não quer um repositório pesado não é mesmo?!

A estrutura do nosso projeto nesse momento ficará assim:

![](https://cdn-images-1.medium.com/max/1600/1*D4I9WUK07aZHsFigdojalA.png)
<span class="figcaption_hack">Estrutura do projeto com os arquivos build.ps1, build.sh e build.cake</span>

## Pipeline de execução

Antes de iniciar a criação das nossas tarefas, vamos entender o pipeline de
execução do nosso script. As tasks do Cake obedecem uma sequência onde devemos
definir um ponto de entrada para o script e então encadeamos a execução de uma
task na outra, por exemplo, para executar os testes, primeiramente é necessário
fazer o build, já para gerar os pacotes Nuget é necessário primeiramente rodar
os testes, e assim por diante.

![](https://cdn-images-1.medium.com/max/1600/1*AF9tObV1MVUcdeG-7bbQDg.png)

## Configuração inicial do script

Vamos definir algumas variáveis iniciais para nosso script, e seu ponto de
entrada, dessa forma:

<script src="https://gist.github.com/wellingtonjhn/f18ec0dc89c2f8566c2acd1c2352a34e.js"></script>

A variável **target** é um argumento que define a task default que o Cake deve
chamar quando este for executado. Já a variável **configuration **é um parâmetro
que deverá ser informado para o compilador do C#, de modo que ele compile o
código em modo Release. A variável **artifactsDirectory **diz respeito ao
diretório em que iremos gerar os artefatos após a execução do nosso script. Esse
diretório será criado na raiz do repositório.

A task **Default** é o ponto de entrada de nosso script. Ela será atualizada em
breve para que as demais tasks sejam disparadas automaticamente.

No terminal usamos os comandos **dotnet build, dotnet test **e** dotnet pack**
para fazer o build, executar os testes de unidade e criar pacotes Nuget
respectivamente em uma aplicação .Net Core. Mas em nosso script usaremos os
aliases do Cake.

## Tarefa de build

<script src="https://gist.github.com/wellingtonjhn/fdbfbe2dee00d510a0504cf0fab1c7d0.js"></script>

A task **Build** irá percorrer o diretório **src **(source) e seus
sub-diretórios em busca de arquivos de projeto para então executar o alias
**DotNetCoreBuild**, que é responsável por fazer o build em aplicações .Net
Core. Ele é equivalente ao comando de terminal **dotnet build**.

> No Cake, as funcionalidades correspondentes ao [.Net Core CLI](https://github.com/dotnet/cli) estão definidas na [documentação](https://cakebuild.net/api/Cake.Common.Tools.DotNetCore/DotNetCoreAliases).

## Tarefa de testes

<script src="https://gist.github.com/wellingtonjhn/f27bdcd4613287d6de037a3e792b41b8.js"></script>

Note que a task **Test**, é dependente da task **Build**, ou seja, essa task só
pode ser executada após a execução do **Build**, dessa forma começamos a montar
nosso pipeline de execução.

A task **Test**, irá percorrer o diretório **tests**, incluindo seus
sub-diretórios, assim como aconteceu com a task de build, mas nesse caso, temos
apenas projetos de teste. Caso algum teste falhe, a execução do script será
interrompida.

## Tarefa de criação de pacotes nuget

<script src="https://gist.github.com/wellingtonjhn/fa25eee20fe8566c3ae1200277d13cf7.js"></script>

Assim como a task **Test** é dependente de **Build**, a task de criação de
pacotes Nuget só pode ser executada após a task Test.

Aqui novamente percorremos a pasta **src** em busca dos arquivos de projeto, ou
seja, será criado um pacote para cada projeto em nossa aplicação. Nossa
aplicação de exemplo contém apenas um projeto nesta pasta, então teremos apenas
um único pacote Nuget gerado na pasta de artefatos do nosso script.

## Deploy do pacote nuget

<script src="https://gist.github.com/wellingtonjhn/e443dde26ffa87278b9dd5136f8662c1.js"></script>

Aqui também não tem segredo. A task **Push-Nuget-Package** irá buscar por
arquivos com a extensão **nupkg **(Nuget Package) dentro da pasta de artefatos
do nosso script. Ao encontrar qualquer arquivo será usado o alias **NugetPush
**para subir o pacote no [nuget.org](https://www.nuget.org/). Você vai precisar
de uma conta para poder fazer a publicação, e uma chave de api. Veja que neste
exemplo eu deixei a chave aberta no script, mas o ideal é que ela esteja em uma
variável de ambiente para que não fique exposta dessa forma. Não se preocupe, a
chave neste exemplo tinha o tempo de expiração de 1 dia e já não é mais válida.

Abaixo você pode ver o [pacote publicado](https://www.nuget.org/packages/CSharpExtensions.Core) no meu feed
pessoal.


![](https://cdn-images-1.medium.com/max/1600/1*MEPbjSuYtxKUQ_oGGS_0OQ.png)
<span class="figcaption_hack">Pacote Nuget publicado no Nuget.Org</span>


## Corrigindo a task default

Nossa task **Default **por si só não faz nada, e já que ela é o ponto de entrada
do script devemos fazer ela depender da última task no pipeline, no caso a task
**Push-Nuget-Package**, com isso criamos uma cadeia de dependências entre as
tasks. O Cake irá executar primeiramente a dependência de cada task formando
assim nosso pipeline.

Para corrigir é simples, basta adicionar a dependência da task Default, dessa
forma:

    Task("Default").IsDependentOn("Push-Nuget-Package");

## Executando o script

Para rodar nosso script, basta usar os scripts **build.ps1** ou **build.sh**, de
acordo com seu ambiente de execução, Windows ou Unix respectivamente.

![](https://cdn-images-1.medium.com/max/1600/1*g4daIO3MaUbVPN8e9NrXgw.png)
<span class="figcaption_hack">Inicio da execução do script</span>

![](https://cdn-images-1.medium.com/max/1600/1*t4ox6Q3_MgteNbw93agXkQ.png)
<span class="figcaption_hack">Task de build</span>

![](https://cdn-images-1.medium.com/max/1600/1*mbvoj6aTINQ11fSnd0D3lw.png)
<span class="figcaption_hack">Task de testes</span>

![](https://cdn-images-1.medium.com/max/1600/1*yNpVhqKCVX_X9lLpjlJ4tQ.png)
<span class="figcaption_hack">Task de geração de pacote nuget</span>

![](https://cdn-images-1.medium.com/max/1600/1*5mSekmtUd6fbMGtoJM2fpg.png)
<span class="figcaption_hack">Task de deploy de pacote nuget no nuget.org</span>

## Pontos de melhoria

Podemos melhorar nosso script Cake das seguintes formas:

* Definir tasks de [Setup e
TearDown](https://cakebuild.net/docs/fundamentals/setup-and-teardown) em nosso
script. No Setup podemos fazer a limpeza da pasta de artefatos, dessa forma
teremos um ambiente limpo a cada nova execução do script.
* Quebrando as tasks e parâmetros de entrada em mais de um arquivo Cake para
melhor organização;
* Adicionando cobertura de testes de unidade com
[OpenCover](https://github.com/OpenCover/opencover),
[Coveralls](https://coveralls.io/),
[ReportGenerator](https://danielpalme.github.io/ReportGenerator), etc;
* Adicionando análise sintática de código, que irá verificar itens como
duplicidade de código, complexidade, segurança, etc, usando o
[SonarQube](https://www.sonarqube.org/) ou [Codacy](https://www.codacy.com/);
* Integrando com ferramentas de CI (Travis, AppVeyor, VSTS, GoCD, Jenkins);
* Criar variável de ambiente para guardar a chave de Api do Nuget.

As possibilidades são inúmeras, e agora podemos deixar essas tarefas chatas com
o Cake e ir tomar um café sossegado enquanto ele faz o trabalho repetitivo para
nós! :D

No próximo artigo pretendo implementar algumas dessas melhorias. ;)

Bom, é isso pessoal. Espero que tenham gostado e qualquer dúvida ou sugestão
fiquem a vontade para entrar em contato.

Abraços!
