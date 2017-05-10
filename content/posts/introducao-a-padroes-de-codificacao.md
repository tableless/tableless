---
title: Introdução aos padrões de codificação
author: Diego Eis
type: post
date: 2012-01-23
excerpt: 'É mais importante para o time concordar em um único estilo de código do que encontrar o estilo perfeito. '
url: /introducao-a-padroes-de-codificacao/
tweetbackscheck:
  - 1356379056
shorturls:
  - 'a:3:{s:9:"permalink";s:60:"http://tableless.com.br/introducao-a-padroes-de-codificacao/";s:7:"tinyurl";s:26:"http://tinyurl.com/74r5hox";s:4:"isgd";s:19:"http://is.gd/FBcnIN";}'
twittercomments:
  - 'a:38:{i:161784593467445248;s:7:"retweet";i:161544030117826561;s:7:"retweet";i:161435142232084480;s:7:"retweet";i:161433995601653760;s:7:"retweet";i:161421336588197888;s:7:"retweet";i:161420979434831873;s:7:"retweet";i:161420185138511872;s:7:"retweet";i:161419111132434432;s:7:"retweet";i:161414965562048512;s:7:"retweet";i:161413111625166848;s:7:"retweet";i:161412378410487809;s:7:"retweet";i:161412212118917120;s:7:"retweet";i:165055849402875904;s:7:"retweet";i:165055332614279168;s:7:"retweet";i:165055157883764738;s:7:"retweet";i:165055153664303104;s:7:"retweet";i:169485557410443264;s:7:"retweet";i:169475711676055552;s:7:"retweet";i:169452380235120642;s:7:"retweet";i:169436687020208128;s:7:"retweet";i:169436303807623168;s:7:"retweet";i:169435824054730752;s:7:"retweet";i:167212330818600962;s:7:"retweet";i:180697788504485888;s:7:"retweet";i:190802402482470913;s:7:"retweet";i:195895713324994560;s:7:"retweet";i:195880521476214784;s:7:"retweet";i:195875159566057472;s:7:"retweet";i:202776573236084736;s:7:"retweet";i:202768235781824512;s:7:"retweet";i:202760951261446144;s:7:"retweet";i:202760477405749248;s:7:"retweet";i:202760465980456961;s:7:"retweet";i:212219386461818880;s:7:"retweet";i:212212987887493120;s:7:"retweet";i:209679843728691200;s:7:"retweet";i:209678208344403969;s:7:"retweet";i:209676394500866049;s:7:"retweet";}'
tweetcount:
  - 104
dsq_thread_id: 549554299
categories:
  - Código
  - CSS
  - HTML
  - JavaScript
tags:
  - 2012
  - cotidiano
  - desenvolvimento
  - desenvolvimento web
  - JavaScript
  - Na Prática
  - web standards

---
Como os idiomas reais, cada linguagem de programação tem suas respectivas regras, individualidades, pontuações, pausas e pontos em comum com outras linguagens. Você precisa conhecer essas peculiaridades para falar fluentemente ou no mínimo ser entendido. Nas linguagens de para web ou qualquer outra linguagem de programação, precisamos seguir algumas regras básicas para que o código não vire uma língua estrangeira no meio do projeto.

Definir padrões é normal para que a equipe inteira escreva o código da mesma maneira. Esse assunto é longo e muito importante para todas as equipes de desenvolvimento. Programadores já quiseram me matar várias vezes porque eu uso TABS em vez de ESPAÇOS em arquivos Python/PHP. Programadores gostam de espaços. Eu não. Mas não é o nosso gosto que vai definir quais os padrões de código que devemos seguir.

Quando definimos padrões e boas práticas, garantimos que todos da equipe conseguirão ter o mínimo de entendimento do código daquele projeto que está na empresa a tempos. Se alguém da equipe adoecer ou precisar ir para o Canadá, outro integrante pode assumir o seu lugar sem precisar se preocupar em aprender novas regras, porque elas devem ser as mesmas do projeto anterior.

É importante que os integrantes da equipe sejam sempre fiéis aos acordos firmados no momento em que combinam esses padrões. É importante também que, caso eles encontrem um integrante fora da lei, que eles forcem o meliante a seguir as regras. Já vi gente perdendo o trabalho de uma semana por que estava trabalhando diretamente pelo FTP e o projeto não estava no GIT. O programador simplesmente APAGOU o projeto da pessoa. Nunca mais ela resolveu editar os arquivos fora do controle de versão. Esse tipo de atitude é perigosa mas muito necessárias às vezes. Devemos forçar as regras num ambiente onde todos devem quem, quando e como as linhas de código do projeto foram escritas.

Alguns pontos para se pensar e combinar:

###### Identação

Como devemos identar o código? Com espaços ou tabs? Se for com espaços quantos? 

###### Espaços em brancos (Whitespaces)

Espaços devem ser incluídos depois de uma operação condicional? Espaços devem ser colocados entre o seletor e as chaves? E no final de cada linha, precisa?

###### Nomenclatura

Como as classes, ids e variáveis devem ser nomeadas? E as funções? Vamos usar [CamelCase][1]?

###### Comentários

Como faremos com os comentários? Como serão os delimitadores do comentário? O comentário deve ser completo ou precisa ser algo mais resumido?

###### Arquivos

Como os arquivos, que não fazem parte da estrutura padrão do CMS, Framework e etc deverão ser chamados? E o nome das pastas? Como as páginas serão chamadas?

###### Chaves e ponto/vírgula

As chaves deverão ser abertas na mesma linha ou devemos quebrar linhas? Vamos sempre usar ponto/vírgula? Vamos usar o padrão [K&R ou Allman][2]?

Quando definimos estas pequenas coisas, diminuímos muitos percalços no meio do caminho. Já vi projetos atrasarem meses por que um palerma abriu e salvou arquivos com o charset diferente do que já tinha sido combinado no início.

&#8220;It&#8217;s more important for people on a team to agree to a single coding style than it is to find the perfect style.&#8221; [Building Scalable Web Sites: Building, Scaling, and Optimizing the Next Generation of Web Applications][3]
  
Indico este livro sobre esse e outros assuntos sobre a construção, desenvolvimento e manutenção de websites

 [1]: http://en.wikipedia.org/wiki/CamelCase
 [2]: http://en.wikipedia.org/wiki/Indent_style#K.26R_style
 [3]: http://www.amazon.com/gp/product/0596102356/ref=as_li_ss_tl?ie=UTF8&tag=tableless-20&linkCode=as2&camp=1789&creative=390957&creativeASIN=0596102356