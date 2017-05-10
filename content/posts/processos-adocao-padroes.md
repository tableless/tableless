---
title: Processos e Adoção de Padrões
author: Diego Eis
type: post
date: 2010-03-03
excerpt: Um pouco sobre o processo de aprovação e adoção de recomendações do W3C.
url: /processos-adocao-padroes/
aktt_notify_twitter:
  - no
tweetbackscheck:
  - 1356421316
shorturls:
  - 'a:3:{s:9:"permalink";s:48:"http://tableless.com.br/processos-adocao-padroes";s:7:"tinyurl";s:26:"http://tinyurl.com/44s2pnn";s:4:"isgd";s:19:"http://is.gd/PVKIMc";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 503039377
categories:
  - Artigos
  - Código
  - Tecnologia e Tendências
tags:
  - aprenda
  - CSS
  - html
  - html5
  - navegadores
  - padroes
  - w3c
  - web standards

---
HTML 5 ou CSS 3 já podem ser usados? Quando o HTML 5 será lançado?
  
Estou ouvindo demais essas perguntas. A resposta que darei, vai servir para as duas perguntas e para perguntas futuras sobre outras recomendações do W3C. 

Para termos uma visão melhor, você precisa entender como o W3C funciona.

### Padrões e Recomendações

O W3C é um órgão que regulamenta, cria e desenvolve linguagens para publicação de conteúdo na internet. Há uma diferença muito grande entre padrão e recomendação. O W3C não faz padrões, ele recomenda métodos e linguagens. Uma recomendação se torna padrão porque há a aderência da comunidade. Normalmente uma recomendação do W3C vira padrão, porque o W3C está lá para isso, eles trabalham para que seja assim. Entretanto, você pode criar uma linguagem como o HTML, e submeter para a aprovação do W3C ou fazer o &#8220;marketing&#8221; dela sozinho e torcer para que a comunidade de desenvolvedores e fabricantes de browsers o apóiem. Isso é difícil de fazer, mas não impossível. Aconteceu com o pessoal do WHATWG com o HTML 5. Um grupo de desenvolvedores estavam descontentes com o caminho que o W3C estava tomando em relação ao XHTML 2 e ao HTML. Então resolveram criar um grupo para escrever um novo padrão da linguagem HTML. O W3C se convenceu e adotou o padrão do HTML 5 que eles estavam escrevendo.
  
Claro que esse grupo foi inspirado por desenvolvedores da Apple, Mozilla e Opera, mas isso foi só um detalhe. 😉

### Processo de adoção

O W3C recomenda métodos e linguagens, o mercado acata e vira um padrão. Uma idéia do W3C, assim que nasce, não é já indicada para uso. Para que isso aconteça há um processo de aprovação e testes. Esse processo é dividido por passos:

1. Working Draft
  
2. Last Call
  
3. Candidate Recommendation (CR)
  
4. Proposed Recommendation (PR)
  
5. W3C Recommendation (REC)

No Working Draft o W3C publica um documento para a comunidade e grupos de membros do W3C. Trate isso como uma ideia rascunhada no papel, onde eles estão perguntando para todos os interessados se é interessante e vale a pena continuar.

No Last Call, o W3C publica os deadlines do projeto, e pede para que todos os grupos de trabalho que de alguma forma estão envolvidos naquele projeto, enviem seus reviews. Há uma fase dentro do Last Call onde o W3C pede para o público, que somos nós, enviar reviews e idéias sobre o assunto.

No Cadidate Recommendation, o W3C já acredita na tecnologia proposta. Ela foi largamente revista por técnicos de dentro e fora do W3C e por todos os grupos de trabalho envolvidos no processo. Nesse ponto, há o começo da experiência de implementação dessa nova tecnologia. Normalmente alguns browsers já implementam essa ideia para que possa ser utilizada por desenvolvedores mundo afora.

Depois dessa fase, entramos na Proposed Recommendation. Nessa fase a recomendação é enviada para o W3C Advisory Committee para que eles aprovem a adoção final que será um novo padrão no mercado. Entenda que nesse meio tempo, há um processo de testes, implementação e desenvolvimento muito criterioso. É o mundo inteiro testando e sugerindo revisões para que a tecnologia seja realmente interessante e inteligente o suficiente para suprir as expectativas.

Quando essa especificação é aprovada, chegamos ao último estágio, onde a idéia inicial vira uma Recomendação. Aí sim os fabricantes de browsers e desenvolvedores poderão utilizar em seus projetos.

Para ficar mais fácil imaginar, tente pensar em um calhamaço de papel. Nesse calhamaço contém um manual de instruções de uso, implementação e detalhes técnicos de como os browsers devem renderizar as instruções, instruções de como os desenvolvedores devem aplicar e escrever o código.
  
Engraçado que tudo isso gira em torno de ideias escritas, revisadas e reescritas. Claro que eles fazem testes reais em browsers reais durante todo o processo. Por isso há integrantes de todos os browsers nas equipes para representar cada um dos browsers do mercado. É um trabalho conjunto. 

### Mas e aí, podemos ou não usar?

Durante muito tempo o CSS foi lançado em versões. Hoje temos 2 versões completas (CSS 1 e 2) e uma revisão (CSS 2.1). O time de desenvolvimento do W3C lançavam atualizações fechadas, ou seja, para haver um lançamento oficial, a especificação do CSS teria de ser totalmente desenvolvida, testada e aprovada. O CSS e o HTML passavam inteiros por todos os processos acima. Por isso, os lançamentos de atualizações no HTML e no CSS eram tão demorados.
  
Hoje, a aprovação do CSS3 está sendo feito por módulos, assim como o HTML5. Há uma equipe para cada uma das principais propriedades do CSS. Por exemplo, há uma equipe que trabalha exclusivamente para o desenvolvimento do background no CSS3. Quando essa equipe acha que já fez um bom avanço, a propriedade de background, separada do resto da linguagem, passa por todo aquele processo que conhecemos no começo do artigo. Isso facilita a adoção dos browsers e dos desenvolvedores. 

Por isso que hoje, mais do que nunca, é necessário que os desenvolvedores pratiquem o Graceful Degradation e do Progressive Enhancement. Pode ser que um browser não suporte uma determinada propriedade porque deu foco para outra propriedade. Isso faz com que a taxa de incompatibilidade de browsers aumente. Se levarmos em conta que os browsers estão mais espertos e suas atualizações estão sendo mais breves, isso não será grande problema. Nosso problema atual é exatamente browsers antigos que não recebem mais atualização. O IE6 está deixando de ser esse caso. A taxa de utilização do IE6 já está bem abaixo do IE7. Claro que em alguns casos isso não é motivador porque trata-se de público específico ou cliente interno. Mas a grande maioria do mercado já está sem essa sombra.

Querendo ou não, essa nova forma de o W3C lançar atualizações em módulos, mexe com a dinâmica do mercado. Não apenas os browsers precisam de atualizações rápidas, mas o desenvolvedor também. Cada uma das atualizações lançadas, minimizam o tempo de trabalho, melhoram o processo de desenvolvimento e priorizam a qualidade de código. Outro passo importante para o desenvolvedor é entender que o site que ele escreve, é portável para qualquer tipo de dispositivo. O desenvolvedor é uma espécie de mensageiro. O conteúdo precisa entregue em diversos meios, e é o desenvolvedor que possibilita isso.

Alguns links para que você conheça mais sobre o processo estão abaixo. Isso tudo pode ser encontrado no site do W3C. Basta ler.

  * [About W3C][1]
  * [Níveis de aprovação][2]
  * [Current Work do CSS][3]

 [1]: http://www.w3.org/Consortium/ "Sobre o W3C"
 [2]: http://www.w3.org/2005/10/Process-20051014/tr#maturity-levels "Níveis de aprovação"
 [3]: http://www.w3.org/Style/CSS/current-work#test "Projeto actual do CSS"