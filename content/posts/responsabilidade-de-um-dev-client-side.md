---
title: Responsabilidade de um dev client-side
author: Diego Eis
type: post
date: 2010-11-10
excerpt: Designer de web tem que saber codificar HTML/CSS/Javascript? Um desenvolvedor client-side tem que saber design?
url: /responsabilidade-de-um-dev-client-side/
aktt_notify_twitter:
  - yes
tweetbackscheck:
  - 1356381343
shorturls:
  - 'a:3:{s:9:"permalink";s:62:"http://tableless.com.br/responsabilidade-de-um-dev-client-side";s:7:"tinyurl";s:26:"http://tinyurl.com/3hpq98l";s:4:"isgd";s:19:"http://is.gd/cweL0V";}'
twittercomments:
  - 'a:10:{i:9975481474486272;s:7:"retweet";i:19350013402423296;s:6:"136489";i:47669586954424323;s:7:"retweet";i:47663310987997184;s:7:"retweet";i:47659817065652224;s:7:"retweet";i:47655167943905281;s:7:"retweet";i:53828034188410880;s:6:"137492";i:53827492351451136;s:6:"137493";i:53835798407163904;s:6:"137495";i:53873791121637376;s:6:"137497";}'
tweetcount:
  - 16
dsq_thread_id: 503039743
categories:
  - Artigos
  - Código
  - Tecnologia e Tendências
tags:
  - 2010
  - cotidiano
  - desenvolvimento web
  - padroes web

---
O reconhecimento do desenvolvedor client-side está maior do que nos anos passados. Isso é importante para nós. Anteriormente nenhuma empresa levava a sério esse setor, não porque ele era menos importante, porque na verdade ele não era, mas por falta de &#8220;inteligência&#8221; das próprias empresas e dos liderantes. O ponto é que esse mercado cresceu, se estruturou, passou por uma reforma natural como todo e qualquer novo mercado que surge e é prostituído com profissionais imaturos.

Com o crescimento deste mercado as responsabilidades do desenvolvedor client-side mudou. Na verdade, não apenas as responsabilidades, mas a estrutura da equipe que ele está inserido mudou completamente. Fica mais granulada. Fica se parecendo mais com uma linha de montagem, só que mais específica e menor. Vamos entender basicamente o processo:

[<img class="alignnone size-full wp-image-2275" title="Processo de desenvolvimento simples" src="http://tableless.com.br/uploads/2010/11/organograma.gif" alt="" width="610" height="880" srcset="uploads/2010/11/organograma.gif 610w, uploads/2010/11/organograma-207x300.gif 207w" sizes="(max-width: 610px) 100vw, 610px" />][1]

Cada etapa deste processo pode ser completado por um ou mais profissionais. Podem haver processos antes do Design, como: planejamento, briefing, entrevistas, levantamento de informações e hipóteses entre outros.
  
Também podem haver processos posteriores ao server-side: testes de funcionalidades, usabilidade, SEO, otimização de banco e código, migrações etc.
  
Existem processos paralelos também, mas não vamos detalhar.

Sabemos que em Server-side, apenas um programador pode resolver o problema. Não adianta colocar um designer ou um dev client-side. Eles não sabem programar, não querem programar, não estão afim. Na parte do client-side é a mesma coisa. O programador não tem noção de design. Ele não tem noção das peculiaridades dos browsers. Não sabe quais as propriedades funcionam nos diversos browsers, não tem noção de acessibilidade, de design e outros pontos importantes. O dev de client-side tem as seguintes responsabilidades na minha opinião:

  1. Planejamento do HTML</p> 
      1. Mapeamento dos elementos do layout
      2. Estudo de SEO e semântica dos elementos
      3. Estrutura do HTML padrão
      4. Otimização do código
  2. Implementação do HTML
  3. Planejamento do CSS</p> 
      1. Estudo de escalabilidade do CSS
      2. Modularização dos arquivos
      3. Nomenclatura de classes e ids
      4. Nomenclatura e padronização código
      5. Otimização do código
  4. Comportamento dos elementos</p> 
      1. Definição do comportamento (junto ao designer)
      2. Criação e padrão de funções e aplicação
      3. Modularização dos arquivos

Veja que dividimos basicamente alguns pontos relacionados às camadas de desenvolvimento: informação, formatação e comportamento. Lembrando que na camada de comportamento o dev client-side só precisa saber a manipulação de elementos. Não precisa aprender a programar profundamente em Javascript. Basta saber um pouco de JQuery ou outra biblioteca da linguagem. Para ocasiões mais complexas há o programador client-side que é o especialista em Javascript. O cara que programa em Javascript como ninguém outro e que vai fazer funções mais complexas do que fazer um DIV aparecer e desaparecer.

Mas quem vai fazer o HTML, CSS e Javascript do projeto? Depende e é aqui que entra a polêmica: em algumas empresas é preferível que o designer seja o coder client-side. Ele já vai ter feito o design dentro dos limites das compatibilidades e possibilidades do HTML/CSS/Javascript. Ele terá a autonomia de retirar ou colocar elementos no layout.
  
Já em outras empresas o processo é separado: o designer cria o layout e depois de pronto e aprovado pelo cliente (no melhor dos mundos) o dev client-side senta e codifica o layout. Pode ser que nessa fase ainda haja uma divisão, entrando dois profissionais: um para HTML/CSS e outro para Javascript.

Eu não aconselho uma granulação maior, ou seja, um profissional para HTML, outro para CSS e outro para Javascript. Não é necessário. Quem escreveu o HTML já tem em sua cabeça toda a estrutura e já entende como o CSS poderá ser escrito e por isso o processo pode ser mais demorado se outro profissional for fazer o CSS.

É interessante que o designer conheça profundamente HTML e CSS. Uma por que ele conhecerá os limites de cada uma das linguagens e outra porque ele poderá codificar seus layouts em momentos que os projetos precisarem de um reforço. Não recomendo que ele conheça Javascript, não é necessário.
  
Já o dev que fará o HTML/CSS não precisa ser um designer excelente, mas ele precisa ter noções do belo. Ser perfeccionista em distâncias, tamanhos, cores e fontes. Entender como fazer para que um browser antigo degrade o layout harmoniosamente e assim por diante.

Com a divulgação e adoção do HTML5 e CSS3, o mercado de client-side deixa de ser restrito ao trio HTML/CSS/Javascript. Muitos especialistas em SVG, Canvas, XML e etc surgirão. O mercado cresceu e mudou muito. Quanto mais o mercado cresce, mas se torna necessário especializar-se em vez de ser um canivete suiço.

 [1]: http://tableless.com.br/uploads/2010/11/organograma.gif