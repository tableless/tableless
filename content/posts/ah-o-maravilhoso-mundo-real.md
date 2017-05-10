---
title: Ah, o maravilhoso mundo real
author: Elcio Ferreira
type: post
date: 2009-09-10
excerpt: O que é mais importante, RDF ou bordas arredondadas? O novo formato de especificações modulares do W3C vai ajudar os desenvolvedores, agilizando os releases de navegador, ou vai tornar nossa vida uma bagunça?
url: /ah-o-maravilhoso-mundo-real/
aktt_notify_twitter:
  - yes
aktt_tweeted:
  - 1
tweetbackscheck:
  - 1356448033
shorturls:
  - 'a:3:{s:9:"permalink";s:51:"http://tableless.com.br/ah-o-maravilhoso-mundo-real";s:7:"tinyurl";s:26:"http://tinyurl.com/3aoveed";s:4:"isgd";s:19:"http://is.gd/MiKPrU";}'
twittercomments:
  - 'a:4:{i:57528246580948992;s:7:"retweet";i:57528113998991360;s:7:"retweet";i:57517009356865536;s:7:"retweet";i:57516309340102656;s:7:"retweet";}'
tweetcount:
  - 10
dsq_thread_id: 503039229
categories:
  - Artigos
  - Browsers
  - CSS
  - HTML
  - Tecnologia e Tendências
tags:
  - Browsers
  - CSS
  - CSS3
  - desenvolvimento
  - desenvolvimento web
  - firefox
  - html
  - html5
  - padroes web
  - Semântica
  - tableless
  - tableless.com.br
  - web standards
  - xhtml
  - xml

---
O Diego publicou, há mais de uma semana, um [artigo sobre o impacto da mudança de estratégia do W3C][1] em relação ao ciclo de vida de seus padrões. O artigo gerou algumas opiniões contrárias nos comentários, em relação ao fato de ele ter dito que bordas arredondadas são mais importantes que a web semântica e em relação à estratégia de especificações modulares do W3C. Vou compartilhar minha opinião sobre os dois pontos.

Em primeiro lugar, é importante distinguir o ideal daquilo que é possível fazer. Li um bocado sobre RDF e ontologias há uns dez anos. Li &#8220;A Revolução Inacabada&#8221;, vi o RSS nascer e se tornar popular, vi as primeiras aplicações entenderem o formato. RDF falhou. Dez anos se passaram e continuamos escrevendo HTML para ser lido por navegadores e só. Há poucos exemplos de aplicações semânticas na vida real, e a maioria seria desenvolvida de uma forma ou de outra.

Há muita gente, por exemplo, definindo seu próprio padrão de XML para trocar dados com sistemas parceiros. Quantos desses estão usando RDF, com uma ontologia interpretada automaticamente por sistemas que &#8220;descobrem&#8221; os serviços um do outro? Ou seja, não há novidades nisso nos últimos dez anos.

Escrever HTML bom é importante, porque vai ajudar o Google a indexar seu site e vai facilitar a vida de quem tentar HTML parsing nele. Mas, seja sincero, você tem mesmo esperanças de que alguém vá lê-lo como XML? Vê alguma vantagem real em validar seu código como XHTML, além de provar a si próprio que fez tudo direito? E onde está a promessa dos microformats? Microformats só fazem diferença se forem usados por muita gente. Ninguém vai fazer um parser de um formato usado em apenas um site. Você consegue citar, de cabeça, cinco sites que usem microformats e não foram feitos por você? Ah, claro, não vale incluir na lista o microformats.org.

Nem RSS é um bom exemplo de aplicação de semântica XML. Existem pelo menos dois formatos populares do padrão, além do padrão Atom, que serve para a mesma coisa. E não sei de nenhum leitor de RSS de sucesso que faça parsing dos feeds como XML. O que todos fazem é ler e interpretar a string. É isso mesmo que você entendeu, quase tão bom quanto um CSV! Outro exemplo digno de nota é o SOAP, que foi criado para fornecer aos webservices a capacidade de &#8220;autodescoberta&#8221;. Você conhece alguém que use isso de verdade? Já viu algum robô que varre a web em busca de serviços e entende sozinho como usá-los? SOAP só tem a vantagem de oferecer tooltips para ajudar os programadores .Net que usam Visual Studio. Enquanto isso, lá fora, XMLRPC e REST (com JSON) estão mudando o mundo.

Por que essas tecnologias falharam, embora pareçam todas boas idéias? Meu palpite é que elas exigiam um raciocínio de longo prazo, um tipo de aposta, que é muito difícil de conseguir. Embora XHTML, Microformats ou SOAP sejam idéias muito boas, aplicá-las em seu site só vai ter valor se muito mais gente o fizer. Se você aplicar o formato sozinho vai perder seu tempo.

O que é muito diferente de, por exemplo, deixar de usar tabelas para layout, escrever bom HTML ou usar jQuery. Essas coisas lhe devolvem um benefício imediato. Se deixar de usar tabelas para layout vai ter um site mais leve e vai perder muito menos tempo quando tiver que mudar o layout, se escrever HTML bom vai ter menos trabalho para escrever CSS, para fazer o CSS mobile e o de impressão, e se usar jQuery vai escrever javascript em um terço do tempo.

Note que esses três exemplos também tiram benefícios do fato de muita gente estar usando. Há muitos bons lugares para se aprender HTML e CSS, há muitos sistemas Open Source que já trabalham gerando código bom e os buscadores entendem a semântica do bom HTML. Mas você não depende desses benefícios para tomar a decisão de uso. Quando começamos, há dez anos, a fazer layouts tableless, não aparecíamos melhor no Google e praticamente não havia sistemas gerando HTML direito. Mas o fizemos assim mesmo porque os benefícios imediatos compensavam o esforço.

É por isso que eu temo que nunca teremos uma web semântica de verdade, e estamos condenados a fazer HTML parsing para sempre.

Há exceções. RSS, por exemplo. RSS é uma sombra do que poderia, mas é um padrão de sucesso, amplamente adotado. E não pode ser explicado com minha teoria do benefício individual imediato. Se você estiver usando RSS sozinho no mundo, não terá nenhum benefício. Talvez o sucesso do RSS se deva ao fato de precisar de uma pequena rede de usuários para oferecer um grande benefício.

Você já se perguntou como foram vendidos os primeiros aparelhos de FAX? Ter um FAX só faz sentido se mais gente tiver. Foram vendidos aos pares. As empresas o compravam para trocar documentos entre a matriz e as filiais. O fato de poder trocar documentos com o resto do mundo era, no início, um &#8220;benefício adicional&#8221;. Se você precisa trocar conteúdo com um site parceiro e vocês forem os únicos usuários de RSS no mundo, terá valido a pena. Conforme a comunidade de usuários aumentava, o valor de ter RSS crescia. Muita gente começou a usar Bloglines e todo mundo queria entrar na festa.

Há alguns anos eu percorri o país com o pessoal da Locaweb comparando o modelo de adoção do RSS com o que eu imaginava que seriam os microformats. Eu estava errado. Pense um segundo no formato de reviews dos microformats. Qual o real benefício de usá-lo? Há alguma aplicação indispensável, onde você realmente quer estar, baseada em hReview? Para que você vai perder seu tempo?

Será que não estamos resolvendo o problema errado? Quando o Diego diz que bordas arredondadas são mais importantes que RDF, será que ele não tem razão? Para meus clientes, hoje, bordas arredondadas com CSS significam um site mais rápido, mais barato (menos tempo gasto recortando imagens) e, para os sites muito visitados, economia de banda. É uma diferença pequena, mas é uma vantagem. E RDF? Além de oferecer RSS, que nem vai ser lido como XML, o que eu posso fazer de real hoje com RDF para meus clientes?

Desculpe se meu raciocínio parece mesquinho. Ele é. Estou tentando ser realista. Uma das principais influências sobre as decisões humanas é a inércia, e não acredito que o mundo vá, num futuro próximo, adotar de maneira revolucionária o RDF ou mesmo o XHTML. Ainda acho essas idéias fantásticas, só não sei se são possíveis.

O realismo também me faz crer que a nova estratégia de especificações modulares do W3C é uma coisa boa. Sofremos décadas com implementações parciais do HTML 4 e do CSS 2. Agora vamos assumir a realidade inevitável. Os desenvolvedores de navegador se sentirão mais à vontade para dizer a você o que funciona ou não. E não precisamos esperar anos para a definição de um padrão. Podemos usar os recursos com os quais o consórcio já concordou hoje. Leva mesmo alguns anos para o W3C bater o martelo sobre determinado padrão, e as especificações modulares representam um ciclo de releases muito mais dinâmico.

Já temos um acordo sobre CSS Transform, bordas arredondadas, múltiplos backgrounds, repetição no DOM, validadores de formulários, SVG, DOM Storage, querySelectors e uma série de outros recursos legais. Por que esperar até a próxima Olimpíada para dizer aos desenvolvedores de browsers: &#8220;Ok, pessoal, fechamos tudo, HTML 5 e CSS 3 já são padrões, podem implementar&#8221;? De qualquer maneira, a adoção modular das especificações do W3C é inevitável. Embora a especificação tenha saído inteira, a adoção foi modular no HTML 3, no HTML 4, no CSS 2. Sabendo que não vai ser diferente mesmo, não é melhor que tenhamos bonitas tabelas de compatibilidade entre o que existe e o que cada navegador suporta?

Dá uma olhada na [lista de módulos do CSS3][2]. Você não quer esperar isso tudo ficar pronto para ter bordas arredondadas.

 [1]: http://tableless.com.br/se-prepare-para-a-revolucao
 [2]: http://www.w3.org/Style/CSS/current-work