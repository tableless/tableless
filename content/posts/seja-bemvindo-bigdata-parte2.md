---
title: Seja bem-vindo ao Big Data e Eu serei seu guia — Parte 2 - Enfrentando um Problema
authors: Allan Sene
type: post
date: 2017-07-30
excerpt: Grandes desafios por traz da contrução de sistemas de bancos de dados de alta disponibilidade e escaláveis.
categories:
  - Big Data
  - Semântica
tags:
  - Big Data
  - Semântica
image: https://cdn-images-1.medium.com/max/2000/1*WAxsCkb61Pf3NteZqXwPJQ.jpeg
---

Você gosta é de solução né... [Not today](https://media.makeameme.org/created/but-it-is.jpg)! Como um bom
computeiro, vou te dar é um quebra-cabeça. Continuando [a
série](https://medium.com/@allansenne/seja-bem-vindo-ao-big-data-e-eu-serei-seu-guia-parte-1-cursos-6b6f25cfa3fe)
de maneira bem pragmática, vamos analisar hoje uma parte importante do problema
de processamento de dados massivos.

### O Maior Acoplamento de Todos

Antes de 1905, não havia nada mais absoluto que o **Tempo**. Até que Einstein
tirasse do chapéu a bela interpretação da
[invariância](https://pt.wikipedia.org/wiki/InvariÃ¢ncia) da velocidade da luz
em detrimento do Tempo, este reinava absoluto nos reinos da Ciência,
[Filosofia](https://pt.wikipedia.org/wiki/Causalidade) e até longe dos
[racionalistas](https://pt.wikipedia.org/wiki/AdÃ¡gio_(mÃºsica)).

Talvez um pouco distante desse círculo, quem sabe rebuscado demais, nós
desenvolvedores, além dos prazos de entrega incabíveis, enfrentamos o **Tempo**
todo santo dia. Regras de negócio, transações em bancos de dados, chamadas
assíncronas, gerenciamento de dependências, integração contínua e paralelismo.
Metade das nossas decisões de arquitetura e implementação estão intimamente
ligadas ao **Tempo**.

Mesmo os mais jovens programadores já ouviram falar de acoplamento de código,
aquele código que dá preguiça até de ler... macarrônico... famoso [big ball of
mud](https://www.laputan.org/mud/)... arghhh ;p

Mas um acoplamento que muita gente negligencia é justamente de **Tempo!
**Quantas vezes seu sistema em produção -e não importa qual tecnologia você use
ou tão perfeita seja sua infra- insiste em ficar lento, em diminuir tempo de
resposta e criar gargalos mais tensos que a pia de um banheiro copo-sujo?
**Maldito Tempo**!

Apesar de ele estar presente em todos esses assuntos relacionados a software e a
computação, aqui trataremos especialmente dele em um contexto:
[Dados](https://www.google.com.br/search?q=dados&safe=off&source=lnms&tbm=isch&sa=X&ved=0ahUKEwjQifCyt_3TAhXGEpAKHRXMCCsQ_AUIBigB&biw=1366&bih=602#imgrc=_)!

### Bonés e Ácidos

aQuem estudou [Introdução a Bancos de
Dados](https://lagunita.stanford.edu/courses/Engineering/db/2014_1/about) vai se
lembrar muito bem das garantias que um **banco de dados
**[transacional](https://www.quora.com/What-is-a-database-transaction) deve nos
dar, resumidos na inesquecível sigla:

## ACID

* **Atomicidade**: todas transações são atômicas, ou seja, sem fragmentação
nenhuma. Ou ela acontece como um **todo**, ou **nada** dela acontece. Famoso
“*ou dá ou desce*”: ou dá [commit](https://pt.wikipedia.org/wiki/Commit), ou dá
[rollback](https://pt.wikipedia.org/wiki/Rollback).
* **Consistência:** toda transação termina com um **estado válido** do banco de
dados. Conceitualmente, podemos dizer que é uma [máquina de
estados](https://pt.wikipedia.org/wiki/MÃ¡quina_de_estados_finita): toda
operação leva a algum estado válido em todo o sistema, mesmo que seja o mesmo
estado anterior à operação -como no *rollback*, por exemplo.
* **Isolamento:** toda transação, mesmo que hipoteticamente seja executada no
mesmo momento para um mesmo conjunto de dados, segue uma [ordem de
execução](https://en.wikipedia.org/wiki/Call_stack)* *e executa *isoladamente*
da outra. Não há operações simultâneas, concorrentes ou paralelas e elas nem
precisam/devem trocar informações entre si.
* **Durabilidade:** toda transação gera um estado final confiável. Se ela foi
completa, pode *crashar, *cair a força ou desligar da tomada, seu resultado foi
gravado em disco permanentemente, -*até que outra transação venha e altere o
estado novamente, claro*.

Tudo isso funciona muito bem no mundo tradicional, mas [como eu já disse
anteriormente](https://medium.com/@allansenne/destrua-seu-data-warehouse-f362ae6e4460),
no mundo distribuído, meu amigo... as coisas que podem dar errado, **darão
errado**, quer você queira, quer não.

Como [lidar com Big
Data](https://medium.com/@allansenne/as-verdades-que-o-mercado-brasileiro-e-vocÃª-precisam-ouvir-sobre-big-data-9fb6f8d5b9d3)
só nos foi possível graças as imensas evoluções que tivemos na área de
[computação distribuída](https://en.wikipedia.org/wiki/Distributed_computing),
temos que transpor um desafio novo, modelado num teorema bem desafiador...

## [The CAP Theorem](https://en.wikipedia.org/wiki/CAP_theorem)

Os bancos de dados transacionais nos dão várias garantias que nos ajudam a
modelar inúmeros problemas. O **ACID** nos blinda de muitas dificuldades que
poderíamos — e **iremos** — sentir ao lidar com Concorrência. E Concorrência é
justamente nossa aliada para bater nosso inimigo inicial: [The
Time](https://www.youtube.com/watch?v=JwYX52BP2Sk)! Somente com ela -por
enquanto- conseguimos bater o rival quando precisamos processar **imensas
quantidades de dados todos os dias.**

É justamente tentando transpor as dificuldades de processar quantidades massivas
de dados, que resolvemos um dia a juntar **concorrência** e bancos de dados em
uma coisa só, criando um problema BEM desafiador, porém necessário de enfrentar:
o **CAP Theorem**. Este teorema atesta que, em um banco distribuído**,** **só
conseguimos manter duas coisas** da seguinte tríplice:

* **Consistência (Consistency):** surge do mesmo conceito explicado acima, mas
veremos de outra maneira: Toda leitura recebe ou o dado **mais recentemente
escrito** (último estado válido) ou uma mensagem de erro — já que alguma
transação deve estar ocorrendo.
* **Disponibilidade (Availability):** Toda transação ou leitura dá garantia de
execução, mesmo que demore: ou seja, não vai receber uma mensagem de erro como
anteriormente.
* **Tolerância à Partição (Partitioning):** O sistema continua funcionando
**normalmente **mesmo que parte dele esteja indisponível.

[https://robertgreiner.com/2014/08/cap-theorem-revisited/](https://robertgreiner.com/2014/08/cap-theorem-revisited/)</span>

Lembre-se que estamos falando de sistemas de bancos de dados **distribuídos** e
é sempre bom repetir que sistemas distribuídos [são o demônio na
terra](https://en.wikipedia.org/wiki/Fallacies_of_distributed_computing)**!
**Dessa forma, meio que somos forçados a admitir que **Tolerância à partição **é
um fato, é **inerente** a qualquer sistema distribuído. Portanto, segundo o
[Teorema de
Brewer](https://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.67.6951&rep=rep1&type=pdf),
ou escolhemos **Consistência** ou **Disponibilidade**.

Analise o seguinte exemplo, visualizando o desenho acima com somente 2 nós num
cluster, para facilitar o entendimento:

**Há falha na rede e estamos fazendo uma escrita: **o sistema de banco de dados
ou lhe retorna um erro, garantindo **Consistência**, ou ele escreve em um nó
somente, e lhe retorna Ok, garantindo **Disponibilidade.**

Estes dilemas são **muito** comuns em bancos de dados em *cluster,
*principalmente em bancos* NoSQL *mais modernos, que tentam se adequar melhor à
diversidade de tipos de dados, à falta de estruturação e, principalmente, ao
volume e velocidade que tais dados chegam.


Admitir um banco de dados transacional nessa realidade é algo bem **delicado**
do ponto de vista arquitetural, exigindo muito planejamento, já que o **ACID nos
atrela ao acoplamento de Tempo. **Usar da** Concorrência, **por sua vez, é
também difícil, pois essa escolha, além dos dilemas que o **CAP** nos traz,
implica em um **aumento grande na complexidade da arquitetura,** exigindo mais
profissionais e alta capacitação destes.

Tendo em vista estes conceitos, vemos que tomar decisões com base em **dados**,
**benchmarks***, *e, claro, bastante **teoria** é **essencial** para equilibrar
esse *trade-off *inevitável entre os entraves do **Tempo** e da
**Concorrência**.

*****

Mas e aí? Você tem uma idéia de como resolvemos esse problema? Temos tecnologias
que já bateram a conjectura que Brewer cunhou? Se você acha que sim, ou que não
comente aí! Se você não sabe ou não quer opinar, disque 2... quer dizer... recomende
e compartilhe esse texto com seus amigos! :D

*****

No próximo post, já adianto, trataremos de conceitos muito valiosos para o
desenvolvimento de sistemas de alto desempenho, escalabilidade e
disponibilidade. Abraços e até mais!

* [Big Data](https://medium.com/tag/big-data?source=post)
* [Software Development](https://medium.com/tag/software-development?source=post)
* [Data](https://medium.com/tag/data?source=post)
* [Coding](https://medium.com/tag/coding?source=post)
* [Back End](https://medium.com/tag/backend?source=post)

### [Publicado originalmente no canal do Tableless no Medium](https://medium.com/tableless?source=footer_card)

Um lugar para ler e discutir sobre desenvolvimento, design, web semântica,
back-end e outros assuntos relacionados a web. Se você quiser publicar artigos
conosco, envie um email: medium[at]tableless.com.br ou *clique no link*
[https://bit.ly/escreva-tableless-medium](https://bit.ly/escreva-tableless-medium)
