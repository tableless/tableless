---
title: Consumo eficiente de recursos computacionais de servidores de aplicação web com Node.js
author: Jamerson Bernardo
type: post
date: 2016-04-28
excerpt: 'Este  artigo  é  o  resultado  de  uma  análise  da  plataforma  Node.js, especificamente quando submetida a um alto número de acessos simultâneos, comparando os números dos indicadores de serviço e eficiência obtidos em testes de performance.'
url: /consumo-eficiente-de-recursos-computacionais-de-servidores-de-aplicacao-web-com-node-js/
titulo_personalizado:
  - 'Análise de consumo de recursos de servidores <strong>com Node.js</strong>'
categories:
  - Artigos
  - Back-end
  - Destaques
  - JavaScript
tags:
  - back-end
  - JavaScript
  - node.js

---
## INTRODUÇÃO

Nos últimos anos, houve um considerável crescimento do número de usuários e volume de dados na Internet. Em 2014, cerca de 3 bilhões de pessoas no mundo usavam a internet e 43.6% das residências em todo mundo possuíam algum forma de acesso a grande rede. Os sites de redes sociais têm registrado, ao longo dos anos, um crescimento exponencial, o Facebook, por exemplo, possuía no final de 2013, 1,3 bilhões de usuários ativos, enquanto o Twitter, maior _microblog_ internacional, registrava, na mesma época, 646 milhões de usuários ativos, responsáveis por 58 milhões de _tweets_ postados diariamente (ITU, 2014). Nesse cenário, as aplicações necessitam atender esse grande número de acesso simultâneo mantendo estabilidade e desempenho satisfatório.

Duas possíveis soluções podem ser utilizadas para resolução de problemas de picos de acessos simultâneos: 1) a substituição da máquina antiga por uma mais robusta, com maior capacidade de processamento; e 2) incorporar novas máquinas, a fim de atender o aumento da demanda dos clientes. Não obstante, as aplicações – _software_ – necessitam utilizar mecanismos e paradigmas capazes de extrair a capacidade máxima de processamento do _hardware_, ou seja, atender um maior número de requisições com o mínimo possível de recursos computacionais.

Por conseguinte, Node.js pode ser uma alternativa eficiente em aplicações com um alto número de requisições simultâneas por ter em seu modelo de programação as estratégias já mencionadas.

Para verificar a eficiência do Node.js foi montado um ambiente controlado para execução de testes de performance, simulando um alto número de acessos simultâneos a uma aplicação de “Hello World”, que tem como saída uma mensagem de “Hello World” e a hora de execução do _script_. Na execução dos testes foi analisado o consumo de recursos computacionais da plataforma Node.js em relação a outras tecnologias.

## METODOLOGIA

Foi considerado como universo desta pesquisa, servidores de aplicações web que necessitam atender um grande número de requisições simultâneas. Para amostragem foram selecionadas plataformas que utilizam entradas e saídas não bloqueantes como estratégia para melhoramento de desempenho: a) Node.js; b) Thin; c) Twistted; e d) Tornado.

A coleta dos dados foi realizada durante a execução de testes de performance, em um ambiente controlado, utilizando a ferramenta Apache JMeter. Antes do teste, o plugin ServerAgent, do Apache JMeter, foi configurado no sistema operacional da aplicação servidora, para permitir a coleta dos dados referentes ao uso de memória e CPU. Foram utilizadas 05 (cinco) máquinas virtuais, com sistema operacional Debian 7.5 e em cada uma dessas máquinas foi instalado uma plataforma da amostragem. Acessos simultâneos de 100, 500 e 1.000 usuários, foram originados do Apache JMeter e direcionados a cada um dos hosts da amostragem, que executavam um código de “Hello, World!”.

Os dados obtidos por ocasião da execução do teste de carga objetivaram trazer subsídios para interpretar a eficiência e consumo de recursos da plataforma Node.js em relação as demais plataformas da amostra. A análise dos dados levou em consideração 04 (quatro) indicadores de desempenho, dividido em dois grupos: a) indicadores de serviço: disponibilidade e tempo de resposta; e b) indicadores de eficiência: consumo de recursos e throughput (vazão).

## RESULTADOS

Com base nos testes realizados percebeu-se que, Node.js demonstrou ter maior desempenho que todas as outras plataformas. Sendo capaz de atender quase o dobro de requisições por segundo, em relação à Thin, tecnologia que demonstrou desempenho mais próximo ao Node.js.

<div id="attachment_53919" style="width: 574px" class="wp-caption alignnone">
  <img class="wp-image-53919 size-full" src="http://tableless.com.br/uploads/2016/04/tempo_resposta.png" alt="Resultado do tempo médio de resposta" width="564" height="332" />
  
  <p class="wp-caption-text">
    Figura 1 &#8211; Resultado do tempo médio de resposta (em milissegundos)
  </p>
</div>

No aspecto tempo de resposta, como pode ser observado na figura acima, o Node.js teve o melhor tempo, gastando metade do tempo utilizado pela plataforma Thin, que ficou em segundo lugar.

Salienta-se que, em todas as plataformas, o tempo médio de resposta quando 1.000 (um mil) requisições concorrentes estavam sendo executadas não foi um tempo aceitável para ambientes de produção, justificado pela pouca capacidade dos recursos computacionais dos servidores em que as aplicações estavam sendo executadas. Todavia, os aspectos aqui analisados são as diferenças dos resultados apresentados entre as plataformas analisadas, uma vez que todas aplicações foram executadas nas mesmas condições de infraestrutura e hardware.

<div id="attachment_53918" style="width: 574px" class="wp-caption alignnone">
  <img class="wp-image-53918 size-full" src="http://tableless.com.br/uploads/2016/04/req_por_segundo.png" alt="Resultado do throughput (vazão)" width="564" height="332" />
  
  <p class="wp-caption-text">
    Figura 2 &#8211; Resultado do throughput (vazão)
  </p>
</div>

Este é um indicador do grupo dos indicadores orientados a eficiência, e um dos principais fatores a ser analisado no teste, pois expressa a capacidade do servidor em atender requisições durante um determinado período. No gráfico da figura 2, está exposto o número de requisições executadas por segundo e é notável que das plataformas analisadas, Node.js apresentou o melhor índice de requisições, chegando a obter mais de 500 requisições por segundo para os testes de 1.000 requisições concorrentes, enquanto a plataforma que obteve o segundo melhor índice alcançou, no melhor caso, um valor acima de 400 requisições por segundo, sendo com apenas 100 requisições simultâneas. É visível a grande diferença entre as plataformas, chegando a ter um aumento de desempenho de quase 50% utilizando os mesmo recursos de hardware.

<div id="attachment_53917" style="width: 488px" class="wp-caption alignnone">
  <img class="wp-image-53917 size-full" src="http://tableless.com.br/uploads/2016/04/erros.png" alt="Porcentagem de erros durante os testes" width="478" height="164" />
  
  <p class="wp-caption-text">
    Tabela 1 &#8211; Porcentagem de erros durante os testes
  </p>
</div>

Quanto ao consumo dos recursos computacionais, todas as tecnologias tiveram um consumo bastante alto nas avaliações com mais 100 requisições concorrentes. Thin, não conseguiu completar com sucesso todas as requisições, nos testes de 500 requisições teve uma taxa de erro de 0,44%. Já nas avaliações com 1.000 requisições, essa taxa aumentou para 2,32%, conforme a tabela 1.

<div id="attachment_53921" style="width: 574px" class="wp-caption alignnone">
  <img class="wp-image-53921 size-full" src="http://tableless.com.br/uploads/2016/04/uso_memoria.png" alt="Resultado do consumo de memória RAM" width="564" height="332" />
  
  <p class="wp-caption-text">
    Figura 3 &#8211; Resultado do consumo de memória RAM
  </p>
</div>

No indicador consumo de memória RAM, figura 3, praticamente todas as plataformas tiveram consumo constante e estável. Das plataformas que conseguiram atender todas as requisições com taxas de erro “zero”, Node.js foi a que teve o menor consumo, enquanto o Twisted foi a que obteve o maior consumo de memória, porém essa diferença entre as plataformas, em geral, foi baixa.

<div id="attachment_53920" style="width: 574px" class="wp-caption alignnone">
  <img class="wp-image-53920 size-full" src="http://tableless.com.br/uploads/2016/04/uso_cpu.png" alt="Resultado consumo de CPU" width="564" height="332" />
  
  <p class="wp-caption-text">
    Figura 4 &#8211; Resultado consumo de CPU
  </p>
</div>

Quanto ao uso da CPU, em geral, todas as tecnologias avaliadas tiveram um alto consumo. Das plataformas que completaram todas as requisições sem erros, em média, a Twisted foi a que apresentou o menor consumo de CPU e Tornado a que apresentou o maior índice de consumo. Node.js só ficou abaixo das demais plataformas nos testes de 100 requisições simultâneas, nas avaliações com 500 e 1000 requisições concorrentes, Node.js teve o segundo maior consumo de CPU.

Cabe ressaltar que apesar do consumo de memória e CPU ter sido similar entre todas as plataformas, Node.js foi superior nas questões de tempo de resposta e número de requisições por segundo, ou seja, foi capaz de atender, com sucesso, um número muito maior de requisições por segundo, com um tempo relativamente menor para atender cada requisição, utilizando a mesma capacidade de recursos de hardware das demais tecnologias.

## CONSIDERAÇÕES FINAIS

Analisando os resultados nos testes é possível concluir que Node.js é realmente uma alternativa para consumo eficiente dos recursos computacionais, e demonstrou ser um servidor de aplicação web de alto desempenho, tendo uma performance até 50% maior que as demais arquiteturas exploradas nos testes. Isto se deve ao fato de essa plataforma ter sido construída com esse propósito, de alto desempenho.

Foi possível comprovar que a performance de Node.js é bem superior a dos servidores web “event-based” comparados nesta pesquisa, permitindo que aplicações que exigem um alto de número de conexões concorrentes sejam mantidas com menos recursos computacionais, reduzindo o custo de infraestrutura dos servidores. Contudo, Node.js não é uma plataforma para todo tipo de aplicação. Em algumas situações, ela não poderá ser utilizada sozinha, mas como um suplemento em aplicações de grande porte, cabendo aos gestores e engenheiros avaliar os requisitos da aplicação e verificar se Node.js é a solução ideal para o desenvolvimento do projeto.

## REFERÊNCIAS

Basso, Fernando Luis. (2014) “Um estudo experimentativo e comparativo da plataforma Node.js”, http://painel.passofundo.ifsul.edu.br/uploads/arq/201505221046071866349516.pdf.

Bonfim, F. L., Liang, M. (2014) “Aplicações escaláveis com mean stack”, http://www.inf.ufpr.br/ml09/TG/monografia.pdf.

Gros-Dubois, J. (2014) “Process-based vs Thread-based concurrency (Node.js)”, https://ncombo.wordpress.com/2014/07/11/process-based-vs-thread-basedconcurrency-node-js.

ITU, International Telecommunication Union. (2014) “Measuring the Information Society Report 2014”, Geneva Switzerland.

Junior, F. A. R. (2012) “Programação Orientada a Eventos no lado do servidor utilizando Node.js”, http://www.infobrasil.inf.br/userfiles/16-S3-3-97136-Programa%C3%A7%C3%A3o%20Orientada\___.pdf.

Molyneaux, I. (2014) “The Art of Application Performance Testing: From Strategy to Tools”, Gravenstein Highway North: O’Reilly, 2ª Edição.

Moreira, R. H. (2013) “O que é Node.js?”, http://nodebr.com/o-que-e-node-js.

Node.js. (2015) “About Node.js”, https://nodejs.org.

Teixeira, P. (2013) “Professional Node.Js: BUILDING Javascript-Based Scalable Software.”, Indianapolis: John Wiley & Sons.

Opher, E., Niblett, P. (2011) “Event Processing in Action”. Stamford: Manning.

Pereira, C. R. (2011) “Aplicações web real-time com Node.Js”, Stamford: Casa do Código.

Ribeiro, C. (2013) “Destilando JMeter I: Introdução e Conceitos”, http://www.bugbang.com.br/destilando-jmeter-i-introducao-e-conceitos.