---
title: 'Web Semântica na Prática Parte 1: A Web do futuro (ou quase isso)'
author: James Miranda
type: post
date: 2016-10-18
excerpt: Aprenda um pouco sobre como criar aplicações Web que podem ser utilizadas por humanos e computadores
url: /web-semantica-na-pratica-parte-1-web-do-futuro-ou-quase-isso/
titulo_personalizado:
  - 'Parte1: Web Semântica <strong>na prática</strong>'
categories:
  - Artigos
  - Destaques
  - Semântica
  - Tecnologia e Tendências
  - Web Semântica
tags:
  - aprenda
  - padroes web

---
É possível conferir aqui mesmo no Tableless alguns bons artigos introdutórios sobre Web Semântica (veja [aqui][1] e [aqui][2]), os quais eu recomendo a leitura caso você nunca tenha ouvido falar sobre o assunto.

A intenção dessa sequência de posts que nomeei como “Web Semântica na Prática” é destrinchar esse assunto de modo aprofundado, apresentando os conceitos e exemplificando-os na prática. O tutorial completo será composto de 9 posts que irão reunir, ao final, um guia bastante abrangente sobre os conceitos, padrões, tecnologias, linguagens e ferramentas utilizadas na criação de aplicações para Web Semântica. Preparados?

## Apresentando a Web do Futuro

Caso você já tenha lido os textos introdutórios linkados no inicio desse texto, você tem uma noção do que é a Web Semântica (carinhosamente chamada de SemWeb pelos íntimos e também reconhecida pela alcunha de Web 3.0, mas você pode usar a buzzword que mais lhe agradar), mas independente de ter lido ou não, vamos apresentar rapidamente o que é esse conjunto de conceitos, pelas palavras de seus próprios criadores, Tim Berners-Lee, James Hendler e Ora Lassila:

> “A Web Semântica não é uma Web separada mas sim uma extensão da Web atual onde a informação possui significado, permitindo que computadores e pessoas trabalhem em cooperação&#8221;
> 
> — Tradução livre a partir do artigo &#8220;[The Semantic Web&#8221;][3]* publicado em 2001 na Scientific American

É praticamente de sabedoria popular que a Web está inundada de dados e que esse volume só cresce a cada dia que passa, mas também é fato que esses dados não possuem um significado claro e estabelecido, impossibilitando sua utilização de modo integrado sem conflitos. Determinar esse significado e converter esses dados em informação aproveitável por qualquer agente (humano ou computadorizado) é o objetivo maior da Web Semântica.

De certa forma, a Web Semântica é uma visão do que a Web será no futuro, onde agentes computadorizados poderão enfim compreender o significado dos dados da mesma maneira que nós compreendemos e atuar sobre eles, executando tarefas repetitivas e auxiliando os usuários das mais diversas maneiras.

É importante notar que, sendo uma “previsão”, a Web Semântica não é um padrão de mercado ainda, logo é bom estar ciente de que todos os padrões, formatos e linguagens utilizadas para criar aplicações nesse ambiente hoje em dia talvez não sejam nunca usados em larga escala no &#8220;mundo real&#8221;. De forma sucinta, **a** **Web Semântica é o futuro da Web, mas o modo como vemos a implementação dela hoje pode não ser a mesma quando este futuro chegar**.

Você pode estar se perguntando: Porque então estudar esses conceitos se eles podem nem chegar a ser utilizados?

O motivo é simples: embora não seja possível afirmar de forma categórica que a Web Semântica será implementada desse modo, isso é extremamente provável.

Veja, o termo foi cunhado em 2000/2001 juntamente com as possíveis tecnologias e padrões para sua implementação. As ideias iniciais foram revisadas em 2006 e em 2011 (veja “[The Semantic Web Revisited][4]”* e &#8220;[The Semantic Web 10th year update][5]&#8220;*) e a base tecnológica para Web Semântica é composta por padrões que estão por aí desde sempre e são bem conhecidas por todos: basicamente XML, URI e Unicode.

Soma-se a isso o amadurecimento desses conceitos nos 15 anos que separam sua criação da Web atual, e então é possível notar de forma clara que a Web está evoluindo e precisando dar seu próximo passo para algo ao menos próximo daquilo foi proposto como sendo a Web Semântica.

Resumindo, apesar de ser uma previsão, as tecnologias estão aí, já estão sendo usadas e, mesmo não sendo um padrão de mercado, elas funcionam e podem guiar o desenvolvimento de aplicações Web em alguns anos. É bom estar preparado.

Se isso não bastar para te convencer a continuar lendo essa série de posts, creio que possa ser interessante conhecer todos os conceitos por trás dessa proposta pois, sendo eles baseados em conceitos sólidos, aplicá-los na prática pode ser útil para uma completa compreensão da Web como um todo, seja para usá-los hoje ou em qualquer momento no futuro.

## As camadas da Web Semântica

O primeiro passo para estudar a Web Semântica é ter uma visão abrangente de como uma aplicação é arquitetada nesse contexto, incluindo os padrões e tecnologias utilizados. Para este fim, nada melhor que um desenho. ;-P

A “Pirâmide da Web Semântica” foi descrita ainda em 2001 e segue sendo um dos diagramas mais utilizados para explicar este universo de forma sucinta. Vale notar que esse diagrama possui diversas versões e modificações realizadas por profissionais de diferentes áreas (Ciência da Computação, Ciência da Informação,Biblioteconomia, ente outros), pois existem diversas propostas sobre a organização da Web Semântica, mas a versão que você vê abaixo é uma adaptação (traduzida) da figura original de 2001 que é inclusive a versão utilizada pelo W3C atualmente, com apenas um ou dois adendos que achei necessários.

<img class="wp-image-56086 size-full" src="http://tableless.com.br/uploads/2016/10/camadasWebSem.png" alt="camadas_web_semantica" width="484" height="334" />

A ideia desta estrutura é definir como implementar a Web Semântica, sendo que cada camada é complementar a camada imediatamente inferior, definindo as linguagens e conceitos chave que devem ser utilizados em tal implementação.

É muito importante ressaltar que o termo Web Semântica é como “guarda-chuva” de conceitos, técnicas e padrões, conforme pode ser observado na figura, e não uma conjunto indissociável de linguagens e frameworks que devem ser utilizados de modo obrigatório. Exatamente por esse motivo que a maior parte das aplicações existentes hoje em dia não utiliza todas as camadas, mas sim apenas uma parte delas.

Embora não tenha nada de realmente prático nesse primeiro post, imagino que para um texto introdutório chegamos a um ponto interessante e espero que tenha atiçado a curiosidade de cada um para investir um pouco de tempo estudando o que foi apresentado aqui (e também o que será apresentado nos próximos posts) para contribuir para a Web do futuro ou pelo menos chegar perto disso.

No próximo capítulo: “IRI, URI, URL, URN e como identificar TUDO na Web”.

 [1]: http://tableless.com.br/a-web-semantica/
 [2]: http://tableless.com.br/semantica-padroes-e-o-que-voce-tem-a-ver-com-isto/
 [3]: http://www.scientificamerican.com/article/the-semantic-web/
 [4]: http://ieeexplore.ieee.org/abstract/document/1637364/?reload=true
 [5]: http://dl.acm.org/citation.cfm?id=1988690