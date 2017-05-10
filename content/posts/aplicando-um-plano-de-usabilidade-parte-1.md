---
title: Aplicando um Plano de Usabilidade – Parte 1
author: Alysson Franklin
type: post
date: 2011-01-04
excerpt: 'Aprenda a planejar e analisar seu website antes de colocar a mão na massa - quer dizer, no código.'
url: /aplicando-um-plano-de-usabilidade-parte-1/
uwre:
  - yes
tweetbackscheck:
  - 1356447098
shorturls:
  - 'a:3:{s:9:"permalink";s:65:"http://tableless.com.br/aplicando-um-plano-de-usabilidade-parte-1";s:7:"tinyurl";s:26:"http://tinyurl.com/4x33rhn";s:4:"isgd";s:19:"http://is.gd/RUN3bc";}'
twittercomments:
  - 'a:1:{i:145213022166724608;s:7:"retweet";}'
tweetcount:
  - 1
dsq_thread_id: 503039787
categories:
  - Acessibilidade
  - Artigos
  - Browsers
  - Código
  - Geral
  - Técnicas e Práticas
tags:
  - usabilidade

---
Pensar a Usabilidade não é algo fácil. Aprendê-la também não o é. Usabilidade não é algo que um desenvolvedor aprenderá por osmose ou coisa parecida, mesmo que a experiência no desenvolvimento conte muito para este assunto. 

Apesar de ser um assunto antigo, a Usabilidade (assim como a Acessibilidade) engatinha no Brasil e, se nao fossem os _Bandeirantes da Usabilidade_ que temos aqui, ainda estaríamos aprendendo a fazer faíscas. Por causa deles, parece que 2011 será o ano que vamos começar realmente a criar a roda. Agradecimento mais do que justo a quem desde 2007 tenta mostrar que sim, é uma cadeira que vale a pena conhecer.

Criar um Plano de Usabilidade é uma atividade que não deve ser feita com olhos de desenvolvedor. Poderíamos falar que um Arquiteto de Software teria mais facilidade de trabalho que um desenvolvedor web em si, puramente por questão de perfil. A infraestrutura de um produto é algo que usualmente fica sob a responsabilidade destes profissionais. Mas quando o assunto é internet, eu defendo que o Especialista em Usabilidade seja o Desenvolvedor, e não o Arquiteto. A não ser que o Arquiteto tenha sido no passado um desenvolvedor fervoroso de aplicações para internet. Nada contra, eu mesmo planejo tirar o meu <a href="http://www.opengroup.org/itac/" title="acessar o site do Open Group sobre a Certificação IT Architect" target="_blank">ITAC*</a> este ano, mas explico a minha posição:

**O Desenvolvedor Web, com treinamento específico sobre o assunto pode oferecer mais a profissão por ter vivência na depuração de erros relativos a navegadores, agregando este valor no Plano de Usabilidade, salvando horas e barateando o custo do projeto ao longo do seu ciclo de vida. Arquitetos ou designers podem fazer Planos brilhantes, porém a possibilidade deste plano ser mais caro que um elaborado por um Desenvolvedor Web Sênior é muito maior.**

Muito da profissão de Desenvolvedor é aprendido na base da tentativa e erro, pegando artigos e referências, testando, aplicando, aprendendo. Um arquiteto que estudou para isso, sem passar pelo desenvolvimento pesado, perde uma perna fundamental de aprendizado quando o assunto é Usabilidade. A perna do desenvolvimento nos permite pensar, planejar e aplicar uma solução para um determinado fim. E depois de desenolvido, podemos **testar, entender como funcionou sua solução em cenários pre-determinados, mensurar os resultados**. Isso nos fornece material para pensamento crítico, entendendo como algumas situações de erro podem ocorrer para que no futuro elas não se repitam. Se um desginer monta um layout que o desenvolvedor percebe a necessidade de uso em demasia de float e position por exemplo, ele poderá se preocupar com problemas de renderizacao com browsers antigos como o IE6 logo de cara. Se o desenvolvedor perceber que o position:absolute será usado por exemplo, ele já saberá que para que tudo fique bonitinho no IE6, ele terá que usar o atributo clear em todas as classes aonde o position estará presente por exemplo. Isso evitará problemões la na frente, quando nos testes se perceber que o IE6 se tornaria o seu pior pesadelo por exemplo. Esse diferencial da experiência, o Arquiteto não terá. Um Designer também não, mas um Developer sim.

Mas a experiência não é nada sem conhecimento, e se um dev quer realmente enveredar pelos mares da Usabilidade, ele precisa entender as fases de um Plano de Usabildade, e, principalmente, como aplicar um Teste de Usabilidade.

## Criando um Plano de Usabilidade

Um Plano de Usabilidade é definido por 4 fases distintas: **Planejamento, Análise, Design** e **Testes e Upgrades**. Um plano como esse abraça muito mais que a Usabilidade em si, mas fala tambem sobre o projeto e o time como um todo.

O planejamento do projeto é fundamental porque ajuda a focar seus objetivos. Ele também ajuda a planejar as atividades de usabilidade que são parte do processo de desenvolvimento de um site. Você deve pensar sobre o que você quer alcançar e criar uma visão direcionada que irá beneficiar tanto os usuários quanto sua empresa. Um site usualmente está disponível para todos. Mas &#8220;todos&#8221; não é necessariamente a melhor definição da audiência do seu site. Um portal de conteúdo por exemplo estará aberto para quem quiser acessar suas notícias, mas se o portal não se preocupar em montar uma versão acessível de seu site para todos os navegadores, provavelmente usuários de regiões mais pobres (e por consequência donos de hardware mais desatualizado) vão experimentar problemas &#8211; quando conseguirem &#8211; ao acessar uma informação. Sinto falta de uma granularidade maior para defender aqui o meu ponto de vista (tenho apenas os números de versão de navegador no Brasil, e se você por favor tiver outros números, me envie a fonte, por favor) mas acredito fortemente que usuários de internet que estão no Amapá vao experimentar problemas de largura de banda, navegadores e resiliência por exemplo. Sem planejamento estes usuários ficariam no escuro e a penetração do seu produto em um mercado em potencial seria jogado no lixo. Para que isso nao aconteça, você precisa **planejar** antes de colocar a mão na massa – digo, no código.

### Planejamento:

  1. **Desenvolvimento do Plano de Usabilidade**  
    Determinar o **escopo** do projeto, identificar **audiência** do site e definir **objetivos** do site.
  2. **Montar equipe do projeto**  
    A utopia começa cedo, logo no planejamento. Em tese, uma equipe de produção web deve ter Gerente de Projetos, Especialistas em Usabilidade, Editores de Conteúdo, Arquitetos de Informação, Designers Gráficos, Developers, e Especialistas no Conteúdo do site. Obviamente que estas 7 pessoas normalmente são apenas uma, no máximo 3 pessoas, mas é assim que as coisas funcionam e mesmo sendo um exército-de-um-homem-só, você precisará produzir por 7 se quiser vencer esta batalha. 
      * **Gerente de projetos:** um profissional gabaritado para liderar e gerenciar um projeto complexo;
	  
        Especialista em Usabilidade: Deve trabalhar no processo de design centrado no usuário (o famoso UCD). Vai ser o responsável por availar o site atual (se existente), a concorrência, conduzir as análises de tarefas, desenvolver os atores, escrever os cenários de teste, definir as métricas e objetivos, analisar os protótipos para encontrar problemas de Usabilidade, conduzir a análise de cartas com usuários do website e recomendar melhorias;
      * **Editores de Conteúdo:** Os escritores responsáveis por produzir o conteúdo que será colocado no website;
      * **Arquitetos de Informação:** Organizam a informação produzida de um modo lógico para a audiência. Trabalham próximos dos Arquitetos de Usabilidade para definir a nevegação do website;
      * **Designers Gráficos:** Responsáveis pelo design do website, trabalham na criação do mesmo e também do Design Paralelo.
      * **Developers:** Responsáveis pelas características técnicas do website, são também os que programam, colocando a mão na massa fazendo acontecer o trabalho dos designers gráficos, arquitetos de informação e especialistas de usabilidade.
      * **Especialistas em Conteúdo:** Revisores ou consultores sobre o conteúdo do seu website. Trabalham próximos dos editores para garantir que o conteúdo produzido esteja alinhado com os objetivos da empresa e também com as tendências de mercado.
    
    Normalmente, este exército numeroso se resumem a 4 pessoas apenas, um gerente de projetos (que pode ser o próprio contratante), um editor de conteúdo, um desenvolvedor e um designer. Sabemos que este número é ainda menor dependendo do contexto. Não é difícil uma única pessoa (ou duas) ser(em) a(s) responsável(is) por todas as fases do projeto.</li> 
    
      * **Contratar Especialista de Usabilidade**  
        Com olhos de um developer, é fácil dizer que tirando o conteúdo e o design tudo pode ser feito por ele, afinal um gerente só se faz necessário quando temos uma equipe de trabalho com algumas pessoas. **Mas desenvolver não é pensar em Usabilidade, e vice-versa.** Um Especialista em Usabilidade deve estar preparado para: 
          * efetuar pesquisas de/com usuários, 
          * Fazer análise de tarefas e usuários, 
          * Dar assistência ao nível executivo estabelecendo métricas de avaliação dos resultados de Usabilidade alinhados com a estratégia da empresa, 
          * Escrever web services 
          * Dominar a arquitetura da informação. 
        
        Mas não é só isso, não falamos dos **Testes de Usabilidade** ainda. Um profissional destes deve estar preparado para:
        
          * Criar e aplicar os Testes de Usabilidade,
          * definir e recomendar os momentos do projeto aonde Testes de Usabilidade precisam ser feitos, 
          * definir a quantidade de usuários e métodos de recrutamento para os testes, 
          * definir os equipamentos e suas configurações para os Testes de Usabilidade (incluindo testes remotos), 
          * definir as metricas coletadas, como elas serão usadas e como as informações serão reportadas, oferecendo com uma linguagem simples explicações sobre métricas ou problemas de Usabilidade encontrados (recomendações de mudança com documentação válida, tutoriais – preferencialmente em vídeo &#8211; para recriar bugs e como consertá-los,
          * Oferecer assistência para o time de desnvolvimento para implementar as recomendações.
        
        Percebe-se que o trabalho deste profissional é mais consultoria que mão na massa, mas fica visível que um developer precisa ir mais a fundo caso queira oferecer serviços nesta área também.</li> 
        
          * **Declaração de trabalho SOW**  
            A Declaração de trabalho é uma ferramenta poderosa para o dono do negócio, e se bem montada, pode ser usada para obter estimativas de custo de fornecedores (agências web) realistas, ajudando na escolha da melhor entrega e do melhor custo. A Declaração de trabalho deve oferecer informações sobre o processo de Design Centrado no Usuario (UDC), avaliação do site atual, avaliação do usuário, arquitetura da informação e organização do conteúdo, testes interativos de usabilidade, definição do perfil de usuários para testes, definição de como a análise e testes serão feitos, definição de como a documentação deve ser produzida.
          * **Reunião de Kick-off do projeto**  
            Hora de conhecer seus colegas de trabalho, como, quando e onde o trabalho será feito.</ol> 
        
        Como vimos, nesta fase definimos o que vamos fazer, em qual período de tempo, com quais pessoas e a qual custo. Esta é uma tarefa dos gerentes de projeto, e normalmente profissionais de desenvolvimento e design estão fora desta fase, assim como os profissionais de Usabilidade. Mas é uma boa recomendação é inverter os passos 2 e 3 e ter o Profissional de Usabilidade já neste momento de montagem da equipe, pois ele pode indicar de acordo com as necessidades do projeto o melhor leque de skillsets para profissionais de design e desenvolvimento, por exemplo. Para PMEs, esta fase pode ser customizada, e mesmo desenvolvedores freelancer podem utilizá-la. 
        
        Considere um representante de auto-peças automotivas por exexmplo; o seu cliente descobriu ontem que para ter mais penetração no mercado ele precisaria de um site na internet, que vai ter um cadastro básico de clientes para relacionamento e compra de peças, além de uma área institucional para apresentar a empresa. Isso é tudo que o dono dessa representação sabe. Nesta fase de Planejamento caberia a desenvolvedor ajudar o “nivel executivo” da auto-peças que o contratou a montar o SOW, mostrando que o site a se desenvolver, deverá ser funcional tanto para a Mecânica do Zezinho ali da esquina, que provavelmente tem um K6-2 com acesso de 100kbps quanto para _as maiores lojas de mecânica do shopping_, aonde o cliente vai com a família passar a tarde enquanto mecânicos deixam o seu carro como novo. Se a representação desta auto-peças tiver estes dois tipos de cliente, a página de pedidos deverá ser extremamente leve e funcional em vários tipos de browser, garantindo que o pedido, que é o que faz a representação comercial funcionar, seja feito, independente de usuário, plataforma ou velocidade de acesso.
        
        ### Análise: 
        
        Analisar é fundamental antes de codificar, e, nesta fase, o quanto mais você coletar informações sobre seu site e seus usuários, melhor. 
        
          1. **Analisando o Site atual**  
            Analisar o site atual quando o existente nos mostra aonde estamos e aonde queremos chegar. Pesquise o log do servidor e o log de termos pesquisa, reveja emails ou ligações feitas pelos clientes sobre os problemas que eles usualmente tem no website atual, faça um Teste de Usabilidade no site atual, conduza uma pesquisa online se possível e analise no site atual as diretivas básicas de desenvolvimento web para: 
              * Processo de design;
              * Otimização da experiência do usuário;
              * Acessibilidade;
              * Página inicial;
              * Layout de páginas;
              * Navegação;
              * Scroll e paginação;
              * Cabeçalhos, títulos e labels;
              * Links;
              * Aparência do texto;
              * Listas;
              * Widgets e dispositivos de controle da tela;
              * Gráficos, imagens, ícones e multimídia;
              * Conteúdo;
              * Organização do Conteúdo;
              * Pesquisa interna;
              * Usabilidade
            
            Quando estes objetivos de Usabilidade estão definidos, podemos nesta fase documentar as métricas atuais para a famosa comparação antes-depois, que é uma das ferramentas que vai availar o seu trabalho. Caso o site não exista, recomenda-se contato com o time da empresa para responder <a href="https://docs.google.com/document/d/1se4r1CX7dtRv1gVS-xX1jE5gkSyB5lRVCVwQml19pAg/edit?hl=en" target="_blank" title="Acessar formulário com questoes de negócio para reuniões iniciais com o cliente">questões de negócio</a> que podem clarear ou direcionar o desenvolvimento do site. </li> 
            
              * **Aprendendo sobre a Audiência**  
                Para mim, a principal parte do planejamento e análise é conhecer a sua audiência. Quem é o seu usuário? O que ele espera ao acessar o seu site? Como ele pensa, agrupa e organiza a informação encontrada em seu site? Como ele trabalha com a informação que você provê a ele? O quanto sua audiência quer ler em seu website? Qual o formato desta leitura? Como ele acessa esta informação? Todas estas são perguntas que você precisa saber antes de começar a codificar o seu website. 
                Existem várias técnicas de se obter estas informações, e algumas delas são inclusive etapas do Plano de Usabilidade:
                
                  * **Teste de Usabilidade**: sim, um teste de usabilidade mostra muito sobre a sua audiência e **como o acesso ao seu site é feito**. Pode ser feito remotamente.
                  * **Entrevistas contextuais:** Um diálogo informal e presencial com um ou dois usuários por vez pode mostrar observações e principalmente, **padrões de comportamento** dos usuários ao navegar/usar seu website;
                  * **Pesquisas online:** Coleta **expectativas, experiências e opiniões** sobre o seu site com um número pré-definido de pessoas.
                  * **Entrevistas individuais:** Presencialmente ou via telefone, IM ou qualquer outro modo, **fornece uma maior quantidade de informações devido ao formato** com perguntas e respostas.
                  * **Análise de Cartas:** Aplicada individualmente com cartas ou outros métodos de análise, consiste no feedback de **como os usuários agrupam a informação disponível** no seu website, mostrando os níveis lógicos e desvios entre como o cliente quer disponibilizar a informação e como a audiência a recebe de verdade.
                  * **Entrevistas de grupo:** técnica de pesquisa de tradicional muito utilizada em marketing, produz diferentes tipos de informação das entrevistas contextuais: **Em uma entrevista de grupo, os participantes falam sobre suas atividades e você ouve-os falar sobre seu trabalho**. Em um Teste de Usabilidade típico ou entrevista contextual, os usuários falam e fazem suas atividades e você assiste e ouve-os durante o todo o processo. 
              * **Conduzindo Análises de Tarefas**  
                De forma sucinta, mostra quais os objetivos dos usuários ao acessar o seu site, o que eles fazem e como. Deve mostrar os passos efetuados para efetuar uma determinada ação e como agir diante das opções possíveis. Uma Análise de Tarefas deve oferecer para usuários únicos e grupos de usuário: 
                  * Mostrar as atividades **(o que)** os usuários fazem em seu website **e como** fazem;
                  * Mostrar **fatores pessoais, sociais e culturais** que os usuários tem ao efetuar estas atividades;
                  * Como o **ambiente físico e suas limitações** podem impactar nas atividades efetuadas pelo usuário?
                  * Como o **conhecimento prévio** do usuário sobre o assunto **influencia o modo como ele pensa** durante o período de utilização do seu website.
              * **Definindo Atores**  
                Para se mensurar as análises de tarefas, precisamos definir os tipos de usuários que acessam o seu site e o que eles fazem. Mantendo o exemplo da Representante Comercial de Auto-peças, poderíamos elencar perfis de **Mecânicos**, que pesquisariam informações técnicas sobre as peças e fariam pedidos, **Atendimento ao cliente** que pesquisam informações sobre os pedidos efetuados, **público em geral** que vai navegar pela parte institucional do site e **Administradores** que vão inputar informações sobre as peças e sobre o negócio em si. Cada um destes perfis vai executar uma determinada gama de tarefas, acessar um número autorizado de páginas e tudo isso deve ser documentado na análise feita no tópico 3. Cabe agora definirmos os atores, estes perfis hipoteticamente pensados, para depois podermos aplicá-los as Análises de Tarefas nos Cenários para Teste.
              * **Escrevendo Cenários para teste**  
                Já explicado no tópico acima, mostra em **detalhes as tarefas que devem ser feitas pelos atores para se atingir uma determinada atividade** no website.
              * **Estabelecendo Objetivos e Métricas**  
                Definir valores racionais para os cenários de teste com base em **tempo, acurácia, eficácia e satisfação do usuário**. No nosso exemplo de representante de auto-peças, poderíamos dizer que uma métrica de sucesso seria: 
                  * Fazer o usuário entender o fluxo de informação das páginas em 30 segundos para que ele possa rapidamente identificar a área de pedidos, parte principal do site;
                  * Fazer a página de pedidos renderizar em qualquer navegador e qualquer conexão em até 35 segundos;
                  * Fazer o usuário conseguir chegar a página de pedidos e fazer o seu pedido em até 2 minutos, pedindo a peça correta do fornecedor correto; 
                  * Errar no máximo um passo do cenário de teste e conseguir retornar ao fluxo correto de ações em no máximo 30 segundos, 
                  * Usuário rankear a experiência de fazer o pedido entre 4 e 5, em uma escala de 1 a 5. 
                
                Verificadas os objetivos acima, devemos ponderar sobre o tempo de navegação, entendimento e renderização além do número de escolhas erradas na navegação, pesquisas improdutivas, erros usando a aplicação e erros de entendimento de página. Somado a satisfação do usuário em todo o processo, podemos quantificar o nosso sucesso (ou falha) definidos nos objetivos primários. Alguns outros exemplos seriam de objetivos seriam:
                
                  * **Website:** 95% mínimo de usuários deve ser capaz de procurar uma peça e fazer um pedido no site;
                  * **Website:** 100% dos mecânicos deve ser capaz de ler as informações das áreas de peças automotivas e entende-las completamente antes de fazer o pedido;
                  * **Website:** O serviço de suporte ao usuário deve ser capaz de responder a perguntas por telefone dos clientes em até 3 minutos;
                  * **Cenário:** 90% dos mecânicos deve conseguir achar a página sobre o Eixo Cardã em ate 45 segundos;
                  * **Cenário:** 100% dos mecânicos deve conseguir identificar os updates em uma página, diferenciando novo conteúdo do conteúdo antigo em ate 5 segundos;
                  * **Cenário:** 80% dos usuários deve ser capaz de encontrar e clicar em um link em ate 15 segundos;
                  * **Página:** A pagina deve renderizar em ate 45 segundos em conexões discadas;
                  * **Página:** A pagina deve renderizar em ate 15 segundos em conexões de banda larga;
                  * **Widgets:** 100% dos usuários deve ser capaz de usar o filtro de range para selecionar peças em uma determinada faixa de preço;
                  * **Widgets:** 100% dos usuários deve ser capaz de usar o filtro alfabético para encontrar informações sobre uma peça específica.
                
                No próximo artigo vou falar sobre a fase de **Design** e dos **Testes e Upgrades**. **Namastê**!
                
                ### Referências
                
                  * [ITAC][1]
                  * [IE6 absolute positioning bug][2]
                  * [Browser Wars no Brasil – Navegadores por versão de 01/10 a 12/10][3]
                  * [Usability Statement of Work (DOC &#8211; 93KB)][4]
                  * [Usability and Focus Group Participant Recruitment (DOC &#8211; 36KB)][5]
                  * [Web Usability Consulting (DOC &#8211; 42KB)][6]
                  * [Web Usability Testing (DOC &#8211; 48KB)][7]

 [1]: http://www.opengroup.org/itac/
 [2]: http://it.toolbox.com/blogs/css-asylum/the-ie6-absolute-positioning-bug-15285
 [3]: http://gs.statcounter.com/#browser_version-BR-monthly-201001-201012-bar
 [4]: http://www.usability.gov/sows/SampleTaskOrdReq05.doc
 [5]: http://www.usability.gov/sows/SOWparticipantrecruit.doc
 [6]: http://www.usability.gov/sows/SOWgisusability.doc
 [7]: http://www.usability.gov/sows/SOWdataprodusab.doc