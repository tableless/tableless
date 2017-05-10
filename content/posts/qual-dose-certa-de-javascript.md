---
title: Qual a dose certa de JavaScript
author: Jean Carlo Emer
type: post
date: 2014-02-03
excerpt: Um pouco de JavaScript não obstrusivo e quais as estratégias para garantir uma boa performance e acessibilidade em aplicações ricas.
url: /qual-dose-certa-de-javascript/
dsq_thread_id: 2214033807
categories:
  - Artigos
  - JavaScript
  - Técnicas e Práticas
tags:
  - client-side
  - front-end
  - JavaScript
  - js

---
Para uma linguagem de programação que começou de maneira tão despretensiosa, o JavaScript ganhou muito espaço. É bem verdade que [alguns navegadores não dão suporte à linguagem][1], mas estes possuem propósitos particulares ou estacionaram em alguma era que não esta.

O navegador Chrome deve muito da sua popularidade pela rapidez com que interpreta JavaScript e a Mozilla há pouco removeu a opção de desabilitar a linguagem no Firefox. Os fabricantes de navegadores bem sabem, querendo ou não, a internet como conhecemos tem o JavaScript como uma de suas principais dependências.

O dilema é como melhor aplicar e o quanto tornar dependente nossa aplicação de código escrito em JavaScript. Qual a dose certa?

## Manifesto

O _The Web Standards Project_ fez bastante barulho há algum tempo e trouxe consigo o [Manifesto do JavaScript][2]. Segundo o texto, **a função do JavaScript é melhorar a usabilidade das páginas através da adição de interatividade**. O que nos leva a algumas premissas:

  * **Cliente não deve assumir o papel do servidor**. O JavaScript não deve ter a função de fazer uma série de requisições em Ajax e montar a página toda no front-end.
  * **O JavaScript deve ser não obstrusivo**. A experiência do usuário não deve depender do correto funcionamento e suporte de JavaScript. Mesmo que perdendo usabilidade, todas as funcionalidades devem sempre estar disponíveis.

## A prática

### Performance

O documento de HTML deve ser entregue para o usuário com conteúdo e o carregamento do JavaScript postergado ao máximo: para o fim do `<body>`. A não ser que você tenha ótimos motivos (por favor, liste nos comentários), reserve a função de gerar o documento para o servidor da sua aplicação. Falando em comentários, saiba até que o carregamento assíncrono deles não é algo a se orgulhar se o motivo for unicamente limitações de infra estrutura. Em defesa a nós bloqueiros, o Disqus tem uma boa pitada de rede social e isto já nos vale como desculpa para seu uso.

Voltando ao ponto, o [Twitter já aprendeu][3] na própria pele que a performance no front-end está fortemente ligado a quanto do trabalho é deixado para o navegador. Sua infra pode ter várias APIs fantásticas e dignas mas a função de consolidar as informações não é do navegador do usuário.

Só me deixe esclarecer um detalhe, nada contra bibliotecas e _frameworks_ JavaScript, eles são bastante úteis e devem entrar em ação assim que todo o conteúdo já tiver sido carregado. Interações mais complexas podem ter sua usabilidade aprimorada drasticamente se realizadas em uma única página com auxílio de JavaScript.

### JavaScript não obstrusivo

O assunto não é nenhuma novidade e caso desconheça [The seven rules of unobtrusive JavaScript][4] é um bom começo. Sejamos práticos e vamos pegar como exemplo âncoras que removem algum registro da sua base de dados. Sem JavaScript, o clique na âncora não vai resultar em uma requisição de `DELETE`, mas sim levar para uma representação do registro que obrigatoriamente deve conter um formulário que permita esta ação. Tudo bem se o usuário precisa navegar para outra página e dar alguns cliques a mais, mesmo com perda de usabilidade, a funcionalidade está lá e pode ser alcançada sem dependência de JavaScript. Caso não tenha compreendido o exemplo das âncoras e sua requisição, confira esta [postagem sobre REST][5].

Escrever seu código de maneira que não seja obstrusivo é possível na maioria das aplicações. Mas e para aplicações de tempo real, por exemplo, como é possível? Algumas funcionalidades podem não ser possíveis sem o devido suporte computacional, não tem jeito. O que nos resta são os paliativos. Uma aplicações de tempo real pode ter uma _meta refresh_ no `<head>` ou um botão para atualizar, não é o ideal, mas é o mínimo.

Mesmo assim, desculpa, mas não acho prático que por criar código exclusivamente não obstrusivo se deixe de fazer jogos e outras aplicações utilizando WebSockets e WebGL. Mas são poucas as aplicações que estão neste seleto grupo. Por fim, os conceitos por trás de JavaScript não obstrusivo são bastante relevantes e respeitá-los ao máximo continua sendo uma boa prática para tornar sua aplicação acessível a qualquer suporte computacional.

### Acessibilidade

A acessibilidade pode estar unicamente relacionada com a escrita de JavaScript não obstrusivo: a partir do momento que sua aplicação não depende exclusivamente de JavaScript, o conteúdo estará sempre acessível. Mas garantir  que sua aplicação esteja acessível apenas quando o JavaScript falhar, demorar para carregar (mais sobre este assunto em breve) ou simplesmente não ter o devido suporte, soa como plano B. Que tal então garantir acessibilidade também quando o JavaScript está sendo executado adequadamente?

A especificação WAI-ARIA permite tornar acessíveis as tão modernas aplicações ricas. Como estamos nos preocupando com aspectos práticos, vamos a este exemplo de [_modal_ do Bootstrap][6]. Repare como a _modal_ não é aberta por uma âncora e sim por um botão.  Neste exemplo, seu conteúdo não está em uma página alternativa ou seção do mesmo documento, não há razão para utilizarmos uma âncora. No elemento da _modal_, os atributos de `role` e `aria-hidden` auxiliam a indicar o tipo de conteúdo e se este está disponível. A função do JavaScript aqui, além de mostrar a _modal_, é garantir o correto valor para o atributo `aria-hidden` e assegurar que o foco seja direcionado para o elemento da _modal_ assim que ativada.

Coleções de componentes de interfaces como a jQuery UI são razoavelmente acessíveis. O calcanhar de Aquiles parece residir nas famosas _tabs._ Inclusive, existem alguns _forks_ deste _widget_ da jQuery UI tentando atingir melhores níveis de acessibilidade por manter o histórico de navegação, indicar o foco adequadamente e possibilitar melhor navegação através do teclado. Utilizar os atributos WAI-ARIA corretos nem sempre é o bastante.

#### Conteúdo que pode sofrer atualização

A especificação de boas práticas de uso de WAI-ARIA nos deixa ainda um recurso pouco comentado e, na minha opinião, de vital importância em uma aplicação rica. São atributos com a função de permitir que a aplicação seja cortês com o usuário: o atributo `aria-live`, por exemplo, permite indicar se modificações no conteúdo do elemento devem ser notificadas ao usuário.

Utilizando novamente o exemplo dos comentários, veja quanto é relevante indicar de forma acessível que novos comentários estão disponíveis. Sempre contamos com o estímulo visual que pode, por diversos motivos, não ser notado pelo usuário. Faz todo sentido em aplicações com algum tipo de comportamento assíncrono poder [indicar quais regiões podem sofrer atualizações][7].

### Modularização

Já escrevi por aqui que [modularização nos permite reduzir a complexidade, separar interesses e manter o código de maneira simples][8]. Mas ainda, digamos que sua aplicação esteja com uma grande quantidade de código a ser baixada. Caso seu código seja modularizado seguindo AMD, pacotes de módulos podem ser carregados sob demanda.

Pensando em uma _single page app_ de e-mail, nem sempre que utilizar a aplicação o usuário pode querer escrever mensagens ou gerenciar as configurações. Não há necessidade em fazer o _download_ e processamento de uma grande quantidade de código responsável por funcionalidades que são de uso esporádico na sua aplicação. Algumas heurísticas interessantes podem ser utilizadas para condicionar o carregamento dos pacotes sem onerar o usuário com o mal visto &#8220;carregando&#8221;. Por exemplo: o usuário leu mais de duas mensagens, é provável que queira escrever alguma; o usuário aproximou o _mouse_ do botão de configurações, a ação pode estar sendo considerada.

### Versione o seu produto

Claro que a web é de todos e estamos aprendendo a possibilitar que diferentes suportes computacionais possam partilhar de um mesmo documento. Mas sejamos honestos, aplicações ricas, a despeito de todos os seus esforços, podem, por culpa da banda de internet ou capacidade de processamento, ter uma experiência miserável em alguns dispositivos.

Caso não haja saída e os muitos recursos sejam o diferencial do seu produto, uma versão _fit_ da sua aplicação com uso limitado de JavaScript pode ser a solução. O Gmail já segue esta estratégia há muito tempo e até o momento não me parece uma má jogada. Nunca esqueça que o essencial é garantir uma experiência adequada para o usuário.

Note ainda que esta prática não entra em desacordo com a premissa de escrever JavaScript não obstrusivo. Pelo contrário, o que estamos oferecendo é um fluxo alternativo onde as funcionalidades principais do produto estão disponíveis mesmo que com uma usabilidade mais pobre. Uma versão alternativa da aplicação pode ainda se valer da modularização do seu código e se você for bem esperto, irá reaproveitar muita coisa.

## Palavras finais

Levando em conta qualquer aplicação, saiba que é difícil avaliar pela quantidade de linhas o quão adequado é um código JavaScript. Se você compreendeu bem os exemplos e conceitos do texto, vai notar que não há nenhuma relação entre a dose certa e esta outra medida.

Em uma única sentença, a **dose certa de JavaScript é aquela em que a experiência do usuário é glorificada**. Isto vai depender muito dos objetivos da sua aplicação e na maneira que você escreve código. Tudo isto irá afetar a acessibilidade, usabilidade e performance.

Aprenda a pensar e planejar a sua aplicação como um todo, apenas JavaScript não será sua salvação nem sua completa derrota. Saiba que as vezes a acessibilidade só pode ser alcançada com a ajuda de alguns atributos no HTML. O segredo é estudar alternativas, experimentar soluções e mensurar resultados.

 [1]: http://en.wikipedia.org/wiki/Comparison_of_web_browsers#JavaScript_support
 [2]: http://www.webstandards.org/action/dstf/manifesto
 [3]: https://blog.twitter.com/2012/improving-performance-on-twittercom
 [4]: http://dev.opera.com/articles/view/the-seven-rules-of-unobtrusive-javascrip
 [5]: http://tableless.com.br/o-grande-desencontro-http-com-o-html
 [6]: http://getbootstrap.com/javascript/#modals
 [7]: http://www.w3.org/WAI/PF/aria-practices/#liveprops
 [8]: http://tableless.com.br/modularizacao-em-javascript