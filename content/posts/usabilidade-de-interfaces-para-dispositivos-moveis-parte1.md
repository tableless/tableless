---
title: Usabilidade de interfaces para dispositivos móveis – parte I
author: Talita Pagani
type: post
date: 2011-11-21
excerpt: O que muda nas questões de usabilidade quando estamos falando em dispositivos móveis?
url: /usabilidade-de-interfaces-para-dispositivos-moveis-parte1/
tweetbackscheck:
  - 1356390591
shorturls:
  - 'a:3:{s:9:"permalink";s:82:"http://tableless.com.br/usabilidade-de-interfaces-para-dispositivos-moveis-parte1/";s:7:"tinyurl";s:26:"http://tinyurl.com/cmvg7x8";s:4:"isgd";s:19:"http://is.gd/EdGNj5";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 503040448
categories:
  - Acessibilidade
  - Mobile
  - UX
tags:
  - desenvolvimento web
  - dispositivos moveis
  - qualidade em uso
  - usabilidade

---
Já escrevemos aqui no Tableless sobre melhores práticas de front-end / usabilidade para dispositivos móveis. Um questionamento comum a estas diretrizes é o quanto elas são específicas ao contexto mobile, pois muitas delas não se distinguem das diretrizes que vêm sendo difundidas há 20 anos.

É fato que grande parte das diretrizes são semelhantes, mas o que muda é a criticidade quando tratamos de mobile. Algumas recomendações tornam-se mais graves e imperdoáveis quando não são seguidas no projeto de interfaces para dispositivos móveis.

Como exemplo, podemos usar a questão da densidade informacional. Em aplicações que serão visualizadas em dispositivos móveis, os textos devem ser concisos, eliminando informações secundárias que podem ser irrelevantes. &#8220;_Ora, mas isso também vale para aplicações visualizadas em desktop!_&#8220;, você pensa. Porém, para mobile, a concisão deve ser ainda maior e informações que seriam aceitáveis nas aplicações web/desktop convencionais devem ser removidas de aplicações mobile. A diretriz base é a mesma: reduzir informação secundária. O que diferencia é o grau de severidade que isto representa neste outro cenário.

## Recomendações críticas para o projeto de interfaces mobile

Desenvolver sites e aplicações para mobile requer atenção para alguns critérios que tem um grande impacto na forma com que as pessoas interagem com estes dispositivos.

### Reduzir clicks

Ok, esta parece ser uma recomendação óbvia para ambiente mobile. Porém, quem já desenvolveu para mobile ou utiliza aplicações nestes dispositivos, pense: você já deve ter visto algum site que apresenta uma informação bem limitada na primeira tela com um link de “leia mais”, onde você tem o esforço de clicar e esperar o carregamento do restante do conteúdo que você necessita, que às vezes poderia ser resumido em apenas uma tela.

Se em um projeto usual de interface as melhores práticas indicam que seria mais adequado disponibilizar toda a informação necessária em uma única tela e poupar cliques do usuário, porque esta diferença em mobile? Por isso, deixar o conteúdo mais conciso é crucial para que a informação possa ser apresentada de modo objetivo e o menos fragmentada possível.

### Reduzir funcionalidades

Restringir a quantidade de funcionalidades, mantendo as que são necessárias ao ambiente mobile, diminui a chance dos usuários se confundirem diante de todas as possibilidades e opções oferecidas.

### Reduzir conteúdo

Devido ao tamanho das telas, o conteúdo para mobile exige uma carga cognitiva maior e, portanto, pode ser até duas vezes mais difícil de compreender. Como a memória de curto prazo é fraca, quanto mais os usuários tiverem que rolar para se lembrar de um conteúdo, menos eles o farão.

### Dar escolhas ao usuário

Textos mais concisos e funcionalidades mais restritas são necessários. Mas é importante manter um link para a versão convencional do site, caso o usuário precise acessar algum recurso que não esteja na versão mobile. O usuário deve ter o direito de escolha sobre como ele deseja visualizar o site.

## Outras práticas importantes que herdamos da usabilidade convencional

### Integridade estética

O quanto o design da sua aplicação se integra com a função da mesma. É o casamento entre forma e função, interface com boa qualidade estética e funcional.

### Consistência

A consistência de interface permite que o usuário transfira seus conhecimentos e habilidades de uso de uma aplicação para outra. É preciso frisar que uma aplicação consistente não é aquela que copia outras aplicações. Pelo contrário, é uma aplicação que tira proveito dos padrões e paradigmas de interface com os quais as pessoas se sentem mais confortáveis durante a interação.

### Metáforas

Fácil reconhecimento e memorização de palavras, símbolos e imagens.

### Contexto do Usuário

Especificação do ambiente do usuário, incluindo também a modelagem de e análise de tarefa e objetivos de negócio.

### Modelo Mental

Organização apropriada de dados, funções, tarefas, papéis e pessoas de acordo com o modo com que o usuário compreende e reconhece estes elementos.

### Navegação

Navegação adequada considerando o modelo mental através de janelas, menus, caixas de diálogos e painéis de controle em formato compreensível.

### Interação e Feedback

Input efetivo e feedback do output de informações para assegurar ao usuário que uma ação está em processamento.

### Aparência e Design

Qualidade visual e atenção ao design com relação à escala, proporção, ritmo, simetria e balanceamento de componentes.

### Visualização de Informações

Apresentação de informações por tabelas, gráficos, mapas e diagramas. Uma vez que a tela destes dispositivos ainda é pequena em comparação aos computadores comuns (mesmo se tratando de tablets), é preciso se valer de componentes coringas que são capazes de apresentar uma boa quantidade de informação de modo compacto, conciso, de fácil visualização e acessível.

Além dessas questões relativas à interface, temos fatores externos que têm grande influência na interação dentro destes ambientes. É o que veremos na parte II deste artigo.

[Leia a parte 2 deste artigo aqui.][1]

## Referências

Marcus, A. “Mobile User Interface Design: For Work, Home, and On the Way”. In ACM SIGCHI 2004. ACM, Viena, Austria, 2004.

Apple. iOS Human Interface Guidelines. Disponível em <span style="text-decoration: underline"><a href="http://developer.apple.com/library/ios/documentation/userexperience/conceptual/mobilehig/MobileHIG.pdf">http://developer.apple.com/library/ios/documentation/userexperience/conceptual/mobilehig/MobileHIG.pdf</a></span>.

IHC 2006. Workshop de Usabilidade de Aplicações e Tecnologias Emergentes: a Necessidade de uma “Nova Usabilidade”?. Disponível em: <http://www.dimap.ufrn.br/ihc2006/workshop.php>

Peter Thomas and Robert D. Macredie. 2002. Introduction to the new usability. ACM Trans. Comput.-Hum. Interact. 9, 2 (June 2002), 69-73. <http://doi.acm.org/10.1145/513665.513666>

Peter Thomas and Harold Thimbleby. 2002. The new usability: the challenge of designing for pervasive computing. In Proceedings of the 15th international conference on Computer communication (ICCC &#8217;02), S. V. Raghavan and Sudhir P. Mudur (Eds.). International Council for Computer Communication, Washington, DC, USA, 382-388.

Kelma Madeira et al. Uma Avaliação do Orkut utilizando Personas sob a ótica da Nova Usabilidade. In: VIII Simpósio Brasileiro de Fatores Humanos em Sistemas Computacionais (IHC 2008), Porto Alegre, 2008.

 [1]: http://tableless.com.br/usabilidade-interfaces-dispositivos-moveis-parte2/