---
title: "GIT: Tenho que voltar para uma versão antiga, e agora?"
authors: Jaime Neves
type: post
date: 2018-10-21
excerpt: Voltando o código para uma versão anterior.
image: https://i.imgur.com/dGlU52F.png
categories:
  - Técnicas e Práticas
tags:
  - GIT
---

Em um belo dia, estávamos trabalhando na versão *v2.20.0*, sucessora da versão
*v2.19.0* da nossa aplicação. Chegou pra gente uma requisição na qual teríamos
que corrigir um **bug** na versão v2.19.0, pois era a versão que estava em
produção. De acordo com nossa semântica de versionamento, essa correção iria
gerar uma nova versão a partir da *v2.19.0,* que seria a versão **v2.19.1.**. Após o término, teríamos que adicionar essas alterações para a versão *v2.20.0* que era a nossa linha principal de desenvolvimento.

O sistema de versão usado pela nossa equipe é o Git.

Partindo desse cenário, irei mostrar os comandos usados para chegarmos até a
versão antiga e depois adicionar as alterações na linha principal de
desenvolvimento.

**IMPORTANTE**: Existem muitos fatores envolvidos nessa retomada de versão.
Dependendo do tamanho da sua equipe, cada membro poderia estar trabalhando em
branchs diferentes para a versão *v2.20.0, v*ocê já poderia ter PR (*pull
request*) para ser aprovado, você já poderia estar resolvendo algum conflito de
alguma feature… enfim, vários cenários. Mas o objetivo principal aqui é mostrar
como faremos essa retomada de versão. Dependendo de como você gerencia e em qual
área da aplicação será feito a correção, isso tudo que falei pode não ser um
problema pra você.

### Voltando Para Versão Antiga

Vamos imaginar que você está na sua linha de comando dentro da branch
**develop.**

## 1. Liste Todas as Versões.

Comando para listar as versões: `git tag`.

Por exemplo:

```
$[develop]
```

se a quantidade de versões é grande, você pode digitar `git tag -l "v2.*"` para
listar apenas as versões 2.x.

## 2. Faça o checkout para a versão desejada, no nosso caso, a versão v2.19.0.

```
$[develop] 
```

Sua tela se parecerá com essa:

Nesse momento, todos os arquivos da sua aplicação, voltaram ao estado antigo.
Todas as modificações e outros arquivos adicionados a partir da versão v2.19.0
não existem.

Você está dentro da versão [**v2.19.0**].

Para as etapas posteriores, podem existir várias maneiras de fazer, vou mostrar
a que usamos.

## 3. Criando Uma Nova Branch.

Criamos uma **branch** chamada `feature-bugfix` a partir da versão *v2.19.0*.
Pois com isso, vamos manter os **commits **separados, para um maior controle.

Por exemplo:

```
$[v2.19.0] 
```


ficará dessa maneira.

```
$[feature-bugfix]
```


## 4. Gerando uma Nova Versão.

Após a correção dos bugs, **adicione** e **comite** suas alterações.

Para adicionar, eu gosto sempre de usar o `git add .` .

```
$[feature-bugfix] 
```


comitando as alterações.

```
$[feature-bugfix] 
```


Vamos gerar a versão **v2.19.1**.

Podemos gerar através da linha de comando, ou se você usa o GitHub como
repositório, você pode também gerar a versão por lá. Particularmente eu gosto
quando a gente gera versões no GitHub, pois podemos escrever um *markdown* sobre
a versão.

Gerando pela linha de comando.

```
$[feature-bugfix] 
```


### Fazendo o Merge na Linha Principal de Desenvolvimento.

Após a correção dos bugs e a geração da nova versão, colocamos as alterações na
linha principal de desenvolvimento. Fizemos da seguinte forma:

Com a versão v2.19.1, sem nenhuma pendência de modificações, realizamos o
checkout para a branch **develop**.

```
$[v2.19.1] 
```


Realizamos o merge, na linha de comando.

```
$[develop] 
```


Na hora do merge tivemos alguns conflitos em alguns arquivos, resolvemos os
mesmos, e depois realizamos o commit das alterações.

