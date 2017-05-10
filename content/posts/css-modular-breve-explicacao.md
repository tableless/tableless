---
title: CSS Modular – Breve explicação
author: Diego Eis
type: post
date: 2006-07-11
url: /css-modular-breve-explicacao/
tweetbackscheck:
  - 1356460976
shorturls:
  - 'a:3:{s:9:"permalink";s:52:"http://tableless.com.br/css-modular-breve-explicacao";s:7:"tinyurl";s:26:"http://tinyurl.com/3dqwr9v";s:4:"isgd";s:19:"http://is.gd/ba04ud";}'
twittercomments:
  - 'a:1:{i:35056021730758657;s:7:"retweet";}'
tweetcount:
  - 1
dsq_thread_id: 503035671
categories:
  - Artigos
  - Geral
tags:
  - acessibilidade
  - Na Prática

---
Há um [artigo com mais detalhes aqui][1].

Se você faz sites grandes usando CSS, já deve ter notado que chega uma etapa do trabalho que se não prestar a atenção devida, podemos nos perder em mundo de propriedades, classes e ids. O CSS ajuda muito no desenvolvimento, isso é fato e ninguém duvida. Acontece que se você não tiver o mínimo de organização, pode ficar tão bagunçado quanto desenvolver sites usando tabelas.

Há uma maneira de organizar melhor seu CSS e deixá-lo organizado para que a manutenção seja rápida e transparente. Isso é possível quando modulamos o CSS.

### Separando as seções

Os sites costumam ser dividos em vários pedaços. Um site simples, por exemplo, pode ser divido em 5 pedaços principais: Topo, Coluna da esquerda (onde normalmente vai um menu lateral), Coluna do meio (onde geralmente vai o conteúdo do site), Coluna da direita (publicidade, busca, etc) e Rodapé.

<img width="530" height="504" alt="Exemplo de estrutura" id="image733" src="http://tableless.com.br/uploads/2006/07/exemplo.jpg" />

Você pode dividir seu CSS de acordo com este padrão. Ou seja, criar um arquivo CSS para cada pedaço do site, e depois importá-los em apenas um arquivo CSS principal, que será linkado na home.

No caso deste nosso sites simples, com 5 pedaços, você teria um arquivo CSS para o topo, onde você formataria tudo que pode estar no cabeçalho do site: Logo, menu, busca, data, etc&#8230; Outro CSS que formataria a coluna da esquerda, outro arquivo para coluna do meio, e assim por diante.

Você teria 5 arquivos CSS que conteriam a formatação de cada pedaço do site unicamente. Isso evitaria ter apenas um arquivo de CSS com centenas de linhas. Onde é um tanto custoso fazer alguma alteração. Separando seu CSS em pequenos módulos, você consegue ser mais rápido na hora de executar manutenções, porque você sabe onde exatamente encontrar a formatação de cada área do site. Se o problema é na lateral esquerda, você vai direto no arquivo responsável pela formatação da coluna da esquerda. Poupa trabalho de ficar procurando onde fazer a alteração.

### Importando

Para importar todos os arquivos CSS em apenas um, usaremos o comando @import:

`@import url(topo.css); /** CSS do cabecalho **/<br />
@import url(colunaesquerda.css); /** Coluna da esquerda **/<br />
@import url(conteudo.css); /** Conteúdo do site **/<br />
@import url(colunadireita.css); /** Coluna da direita **/<br />
@import url(rodape.css); /** Rodapé **/`Os nomes que eu usei para os arquivos são apenas para explicação. Não é bom usar nomes tão específicos por falta de semântica. Isso é papo para outro post.
  
Você pode ainda ir mais além, e criar arquivos individuais para seções específicas do site, como por exemplo telas que usem formulários: Telas de cadastro, contatos, logins, etc.

Use o bom senso. Não exagere. Não adianta você criar dezenas de arquivos CSS, em vez de facilitar a vida, você vai piorar. Já vi muito desenvolvedor criar um arquivo CSS para formatar apenas duas ou três propriedades de um objeto. Isso é contraproducente. Não vale a pena criar um arquivo para tão pouco código.

### Planejando

Um bom planejamento antes de começar a estrutura seu CSS é muito bem vindo. Analise o layout e defina as seções principais. Mapeie as páginas que terão formulários, elas costumam ser mais complicadas que o geral, é bom que elas tenham um arquivo CSS individual.

Crie uma pasta CSS onde você irá colocar toda a formatação do site. Nesta pasta se encontrarão apenas os arquivos CSS e a pasta de imagens que estes arquivos irão utilizar.

Não crie nomes complicados para os arquivos CSS. Tente manter a simplicidade e objetividade nos nomes para que não haja problemas posteriores de conflito. Já vi muita gente colocar nomes como: cabecalho\_interna\_sistema_logado.css
  
É muito fácil cometer erros com uma nomeclatura desta maneira. Seja sucinto na hora da escolha dos nomes.
  
Fazendo todo este planejamento, é simples de controlar toda a estrutura de formatação do site.
  
A maneira que eu apresentei aqui é muito básica. Você com certeza fará sites bem maiores e complexos do que nosso exemplo. Mas a idéia continua a mesma. Adapte esta técnica de acordo com as necessidades do projeto. Invente maneiras novas&#8230; lembre-se que padrões web vieram para libertar.

 [1]: http://tableless.com.br/modulando-o-css "Modulando o CSS"