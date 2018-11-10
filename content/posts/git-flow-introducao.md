---
title: Gerenciando seus branches com o Git Flow
authors: Breno Panzolini
type: post
date: 2018-11-10
excerpt: Explicação dos conceitos básicos e fundamentais do Git Flow.
categories:
  - GIT
  - Técnicas e Práticas
tags:
  - Técnicas e Práticas
  - GIT
image: https://git-scm.com/images/branching-illustration@2x.png
---

# O que é o Git Flow?

Quando estamos trabalhando em times pequenos, é comum adotarmos pouco controle (às vezes até nenhum) sobre o fluxo de *branches* dos nosso repositórios, porém conforme a complexidade do projeto e equipe vão aumentando coisas que antes eram simples, como um *hotfix*, começam a se tornar difíceis de controlar.

O **Git Flow** é um modelo de conjunto de diretrizes que equipes de desenvolvimento podem seguir para organizar as *branches*.

É importante ressaltar que o Git Flow são **diretrizes** e **não regras**, ou seja, você não precisa seguir 100% ao pé da letra o que ele fala, acho legal e até saudável que haja uma adaptação de acordo com a equipe de desenvolvimento.

Uma outra observação importante, é que o Git Flow não é o único modelo que podemos seguir para organizar as nossas *branches* (existem até pessoas que criticam esse modelo), porém na minha experiência até hoje, ele foi o que mais se mostrou efetivo quando estamos trabalhando em conjunto com outros times de desenvolvimento.

# Como Funciona

Como mencionei, o Git Flow são diretrizes para a organização dos nossos *branches*, e por esse motivo ele estabelece **padrões de nomes** e **funções** para cada tipo de *branch*, são eles:

- **master**: contém o nosso código de produção, todo o código que estamos desenvolvendo, em algum momento será "juntado" com essa branch
- **develop**: contém o código do nosso próximo deploy, isso significa que conforme as features vão sendo finalizadas elas vão sendo juntadas nessa *branch* para posteriormente passarem por mais uma etapa antes de ser juntada com a **master**
- __feature/\*__: são *branches* para o desenvolvimento de uma funcionalidade específica, por convenção elas tem o nome iniciado por **feature/**, por exemplo: feature/cadastro-usuarios. Importante ressaltar que essas *branches* são criadas **sempre** à partir da **branch develop**
- __hotfix/\*__: são *branches* responsáveis pela realização de alguma correção crítica encontrada em produção e por isso são criadas à partir da **master**. Importante ressaltar que essa *branch* deve ser juntada tanto com a **master** quanto com a **develop**
- __release/\*__: tem uma confiança maior que a branch **develop** e que se encontra em nível de preparação para ser juntada com a **master** e com a **develop** (caso alguma coisa tenha sido modificada na branch em questão)

É importante ressaltar, que sempre que uma branch **hotfix/** ou **release/** é mesclada com a **master** o Git Flow gera automaticamente **tags** facilitando assim uma eventual necessidade de mudarmos para uma versão mais antiga.

# Exemplo Prático

Nada melhor do que executarmos um exemplo prático para fixar os conceitos do **Git Flow**. Existe um plugin do Git que nos ajuda a executar todos os comandos de criação de branches, tags, etc, facilitando assim todo o processo.

## 1. Instalando o plugin

O **Git Flow** não é uma ferramenta padrão do **Git**, e por esse motivo precisamos antes de tudo realizar a instalação do plugin.

No github tem o [passo a passo](https://github.com/nvie/gitflow/wiki/Installation) de como instalar em todos os ambientes.

## 2. Criando um repositório Git

Primeiramente vamos iniciar um repositório Git "normal", para isso executar os seguintes comandos:

```sh
$ mkdir teste-gitflow
$ cd teste-gitflow
$ git init
```

Apenas criamos um novo diretório chamado `teste-gitflow` e inicializamos o git com o comando `git init`.

## 3. Inicializando o Git Flow

Vamos inicializar o Git Flow no nosso repositório:

```sh
$ git flow init
```

Algumas perguntas referentes à nomenclatura serão feitas, recomendo apenas apertar ENTER e não alterar nenhuma configuração aqui.

![git flow init](https://i.imgur.com/1UHlify.png)

Interessante observar que apenas executando o comando acima já foi criado e feito o *checkout* para a **branch develop**.

## 4. Iniciando uma feature branch

Vamos simular a criação de uma feature para cadastro de usuários:

```sh
$ git flow feature start cadastro-usuarios
```

![feature start](https://i.imgur.com/ftbi1nA.png)

Após executado o comando acima, vou criar um arquivo `usuarios.js` (apenas para simular o desenvolvimento de uma feature). E após isso vou realizar o `commit`.

```sh
$ touch usuarios.js
$ git add .
$ git commit -m "Criado cadastro de usuarios"
```

## 5. Finalizando a feature branch

Agora que já temos nossa feature criada, podemos finalizar a *branch* e mesclá-la com a **develop**.

```sh
$ git flow feature finish cadastro-usuarios
```

![feature finish](https://i.imgur.com/odkaNpS.png)

## 6. Iniciando o release

Agora que já temos a nossa funcionalidade de usuários na **branch develop** vamos iniciar o **release**

```sh
$ git flow release start 1.0.0
```

![release start](https://i.imgur.com/Dqnx0k1.png)

Lembrando que mudanças podem acontecer na **release** antes de ser mesclada para **master**, porém em muitos cenários essa branch é imediatamente já juntada com a **master**.

## 7. Finalizando o release

Agora vamos finalizar o **release**

```sh
$ git flow release finish 1.0.0
```

![release finish](https://i.imgur.com/yCodYvm.png)

Se você está seguindo o passo a passo, irá notar que o Git Flow abre o editor de texto para que possamos editar algumas coisas:

- Primeira para editar o texto do merge commit relacionado ao merge entre a release branch 1.0.0 e master (texto opcional)
- Segunda para a descrição da tag 1.0.0, que será criada pelo Git Flow para facilitar mudanças de versão (texto obrigatório)

Feito isso seu código está na **master** pronto para ir para produção e sem maiores problemas de versionamento.

# Conclusão

O objetivo desse post foi mostrar o básico do que o Git Flow é capaz de fornecer, maiores informações podem ser encontradas no [repositório do GitHub](https://github.com/nvie/gitflow).

Na minha visão esse modelo para organizar as nossas *branches* é bem legal de ser seguido para times de desenvolvimento, pois permite tanto o desenvolvimento "paralelo" de features quanto a correção de bugs críticos encontrados em produção.
