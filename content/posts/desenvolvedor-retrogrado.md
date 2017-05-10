---
title: Desenvolvedor Retrógrado
author: Diego Eis
type: post
date: 2007-07-01
url: /desenvolvedor-retrogrado/
aktt_notify_twitter:
  - no
tweetbackscheck:
  - 1356140464
shorturls:
  - 'a:3:{s:9:"permalink";s:48:"http://tableless.com.br/desenvolvedor-retrogrado";s:7:"tinyurl";s:26:"http://tinyurl.com/3nv58jk";s:4:"isgd";s:19:"http://is.gd/FxEx9E";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 503037355
categories:
  - Artigos
  - Tecnologia e Tendências
tags:
  - cotidiano
  - Na Prática

---
[Neste post que o Ronaldo publicou][1], me (assustou) chamou muito a atenção [o comentário que um dos leitores fez][2].

### Tableless é mais dificil de implementar

Não sei o que ele quis dizer com isso, mas em todos os clientes que eu prestei consultoria, presenciei de perto resultados contrários a esta afirmação. Lembro-me de quando atendemos o Terra. No final do curso, eles já tinham a home do site feita em Tableless e já pronta para publicar.

Muitas vezes a demora da implementação de HTML+CSS em sites se deve a curva de aprendizagem dos desenvolvedores. Isso é normalíssimo. Você implementa sites durante anos. De repente chega um bando de pessoas dizendo que a maneira que você usa é errada, lerda e totalmente ultrapassada. Logo você se dispõe a aprender a nova maneira que andam falando. Lê, se interessa e aprende. Na hora da prática você terá dúvidas e procuraráa prender novas soluções para velhos problemas, que você resolveria em dois segundos do modo que estava acostumado. Você precisa se familiarizar com a nova maneira. Isso leva tempo e depende de muito esforço. Como disse, isso é normal e acontece todo tempo que o reaprendizado é necessário.

Novos desenvolvedores que aprendem a construir sites com padrões web, sem passar pelo método antigo, se tornam mais proficientes. O motivo é óbvio: eles não precisam mudar nenhum tipo de conceito enraizado por causa de anos de costume. Já nós que passamos por esta transição, precisamos mudar toda nossa forma de pensar. É custoso.

Equipes que se dispõe a estudar e praticar novas metodologias de trabalho têm tido ótimos resultados, não apenas em aspectos de velocidade de implementação, mas também em novas metodologias de trabalho que antes eram impossíveis com a maneira antiga.

Quando dizemos que a guerra entre Designers e Programadores acaba e todos vivem felizes para sempre, não estamos brincando. Isso se tornou realidade em equipes de todos os tamanhos.

### Leva mais tempo pra testar

Não me lembro exatamente o tempo que eu levava testando projetos feitos com tabelas. Mesmo não tendo esse parâmetro, sites feitos com Padrões Web são fáceis de testar e e alguns fatores dependem de seu público alvo e as medias em que seu site será exibido.

Já cansei de dizer que antigamente eu testava todos sites em pelo menos 6 browsers: Internet Explorer 5.5 e 6. Opera (neste tempo o Opera lançava uma versão por semana, era incrível. Por isso era comum testar em 2 ou 3 versões do Opera). Firefox (que no tempo chamava-se Phoenix e posteriormente Firebird).

Atualmente essa lista diminuiu para 2 (ou 3) browsers: Internet Explorer 6 e Firefox. E agora (só agora) estou colocando o IE7 na lista.

Browsers como Firefox e Opera tem a renderização muito próxima. Por isso posso descartar um deles, no caso o Opera. O Firefox é o segundo browser mais usado e por isso merece mais atenção.
  
Ainda é necessário testar no Internet Explorer 6, porque ele é o brower mais utilizado (ainda até mais que o IE7), portanto&#8230;

Se você quiser que seu site seja bem acessado por Smartphones e cia, você precisa testar em aparelhos de verdade, assim você sabe se a experiência do usuário está sendo satisfatória e percebe mais fácil melhorias que podem ser feitas.

Hoje, se você quer ter um site de sucesso, uma bateria enorme de testes deve ser feita. Não importa em quantas medias você vai publicar. Sem trabalho não há recompensa.

### Mais dificil para outros darem suporte

Como o [Ronaldo disse no post dele][1]:

> Atualmente, a consciência em torno de padrões Web e especialmente da prática conhecida como tableless é tão grande que mesmo clientes corporativos mais alheios a essas questões estão começando a pedir que seus sites e sistemas sejam feitos desta forma.

Se os clientes que são os que menos sabem sobre detalhes técnicos, estão exigindo que seus sites sejam feitos com Padrões, o desenvolvedor tem obrigação de saber construir, implementar e conhecer os Padrões Web.
  
Sabendo que os Padrões Web estão tão difundidos e ganhando grandes massas, como podemos dizer que um código separando informação (HTML) da formatação (CSS) é mais dificil de dar manutenção?

Uma das principais características de se construir sites utilizando os Padrões Web é ter o código mais enxuto possível. Fazendo isso, você tem conseqüentemente um código mais simples.

Como dou cursos sobre Padrões Web, tenho muito contato com códigos desenvolvidos por várias pessoas. Até os piores códigos que vejo são simplérridos comparados com os horrendos códigos feitos em sites usando Tabelas.

Uma das premissas dos Padrões é: quanto mais simples melhor. Se está achando que está complicado, é porque provavelmente algo (ou tudo) está errado.
  
Sempre digo aos alunos tentarem resolver os problemas com o uso mínimo de elementos. Tente usar um elemento para resolver os problemas no layout. Só depois de esgotar todas as possibilidades, pense em adicionar um segundo elemento.

Usando Padrões, todos os desenvolvedores sabem por exemplo que o H1 é um título de primeira instância. Tanto o profissional daqui de São Paulo quanto o profissional lá da ponta do Brasil no Rio Grande do Sul sabe o que isso significa. É pra isso que existe os Padrões: ter controle.
  
Logo, o suporte se torna fácil, quase fluente. O que precisará ser entendido nos códigos de terceiros são as nomenclaturas dadas para os elementos, porque as tags/elementos já são conhecidos por todos.

### Inclua entre 20 a 40% sobre o orçamento inicial

Isso poderia ser feito a uns anos atrás. Hoje em dia, desenvolver com Padrões Web está começando a deixar de ser diferencial, logo, essa &#8220;taxa&#8221; vai se tornar abusiva.
  
É a mesma coisa quando um desenvolvedor pede mais no salário por saber ler inglês. Isso é essencial hoje em dia para quem trabalha com tecnologia.

Você vai cobrar mais caro do cliente, por causa da gama de possibilidades que poderão ser implementadas no site posteriormente e que serão interessantes para oferecer ao cliente. Aí sim você tem um diferencial.

Um serviço seria ter um site onde ele poderá gerenciar todo conteúdo por um CMS e que poderá mudar o layout a hora que quiser. Isso justificará esses 20% ou 40% a mais.
  
Pro desenvolvedor, esse trabalho é fácil de resolver implementando o WordPress como CMS e criando layouts se baseando pelo código HTML criado pelo WP.

Infelizmente ainda temos desenvolvedores que pensam para trás.
  
Para esses, temos que desejar boa sorte para mudar de pensamento e estudar melhor as possibilidades.

Ficar acomodado é muito bom, mas só para você (as vezes nem pra você).

 [1]: http://logbr.reflectivesurface.com/2007/06/29/tableless-vs-mundo-real/
 [2]: http://logbr.reflectivesurface.com/2007/06/29/tableless-vs-mundo-real/#comment-3942