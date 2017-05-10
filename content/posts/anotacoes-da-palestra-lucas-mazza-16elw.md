---
title: 'Anotações palestra: Manutenção e Refatoração de CSS'
author: Diego Eis
type: post
date: 2014-05-20
excerpt: Anotações sobre a palestra sobre Refatoração e Manutenção de CSS em projetos, feito pelo Lucas Mazza.
url: /anotacoes-da-palestra-lucas-mazza-16elw/
dsq_thread_id: 2700165593
categories:
  - Eventos e Workshops
  - Slides e Apresentações
tags:
  - anotacoes
  - palestras

---
Esse ano estive em todos os Encontros Locaweb pelo país. O Tableless organizou a sala sobre desenvolvimento, convidando uma série de palestrantes durante o ano. O Lucas Mazza foi o palestrante convidado aqui de SP. 

O Lucas fez uma palestra sensacional sobre refatoração e manutenção de código CSS no projeto. De cara parece um assunto bastante sem graça para alguns, e é aí que mora o problema.



  * Manutenção de software é complicado. Existem legados e você precisa lidar com isso.
  * CSS não é muito prático quando se trata de legados. É difícil chegar a ter uma alta qualidade no código CSS.
  * Semântica é algo importante para manter o legado de código e assim facilitar a manutenção.
  * Semântica, Modularidade, Performance e Produtividade são pontos focais para ter um código decente.
  * Quando há diversas mãos mexendo no código, problemas cruéis podem acontecer.
  * A equipe inteira deve mexer no código. O código é do projeto, não da pessoa.
  * Qualquer desenvolvedor pode ajudar no código, mesmo que não seja dev front-end. Cuidado, back-end, código HTML precisa ser bem escrito.
  * Use PULL REQUESTS. Coding review é bom e faz bem para os dentes.
  * Você precisa passar por esses pontos no pull request: código, contexto, discussão de equipe.
  * Usando uma interface como o GitHub, você consegue trabalhar com Markdown, usar screenshots e gifs.
  * Disseminação de conhecimento é feito quando a equipe discute o código do Pull Request.
  * Quebre a ideia do paternalismo: todo mundo tem que falar do seu código e mexer nele.
  * Evite silos de conhecimento.
  * Sua equipe precisa de um padrão para escrever código, ou tudo vira bagunça. [Guideline da Plataformatec][1]
  * OOCSS-ish/FCSS-ish são formas de escrever CSS.
  * Tente usar classes e não heranças de pais. [Artigo do Otto][2]
  * Tenha uma Nomenclatura Ubíqua. Isso faz com que o nome do componente seja comum por todos da equipe.
  * Ter uma nomenclatura ubíqua também ajuda a separar as responsabilidades do código. Cada parte é independente da outra.
  * Nesting é coisa séria. Use com cuidado. Um padrão mais ou menos comum em todo mundo front-end é a utilização de nesting até 3 níveis.
  * Pré-processadores são apenas ferramentas. Eles nunca deixarão seu código ruim em um código bom.
  * Código isolado/componentizado faz com que mudanças fiquem previsíveis.
  * Cuidado com as peças móveis. Com muitos componentes seu código fica complexo e burocrático.
  * Para quem é novato no projeto, entender a relação entre as modularizações é difícil.
  * Comece a modularizar aos poucos. Deixe crescer naturalmente de acordo com o desenvolvimento do produto.
  * **NÃO EDITE CÓDIGOS DE TERCEIROS**, TIPO BOOTSTRAP E ETC.
  * Escolha dependências do tamanho que você precisa. Pode ser que uma dependência seja muito grande atrapalhe mais do ajude.
  * Use dependências com moderação e de acordo com as suas necessidades.
  * Sisteminha de criação de sprites que o Lucas usou para substituir o do Compass. <http://github.com/lucasmazza/spriteful>
  * Não modifique código de terceiros, estenda.
  * Documentação decente é amor. Você precisa ter carinho pela documentação do código.
  * Documentação de código é uma forma de comunicação entre os desenvolvedores do projeto e para pessoas fora da equipe.
  * Documentação é uma outra abstração do seu código.
  * Tente documentar bem cada módulo do CSS e Javascript. Comentários no código são bem vindos.
  * Crie um styleguide dos componentes do seu software.
  * Ler sobre KSS &#8211; [Knyle Style Sheet][3]
  * O código nunca vai mentir para você. Ele é sincero. Ele diz o que está acontecendo no seu projeto.
  * Mostre para outros times e desenvolvedores o seu código.
  * Maintainability comes from shared understanding. &#8211; **Kyle Neath**

 [1]: http://guidelines.plataformatec.com.br/css
 [2]: http://markdotto.com/2013/10/09/css-and-noparents/
 [3]: http://warpspire.com/posts/kss/