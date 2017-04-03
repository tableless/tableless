---
title: A importância de desenvolver considerando off-line first
author: Reinaldo Ferraz
type: post
date: 2015-11-18
excerpt: Uma aplicação web que funcione off-line é fundamental nos dias de hoje, tendo em vista a mobilidade, instabilidade de rede e mesmo a falta de acesso à internet.
url: /a-importancia-do-offline-first/
categories:
  - Artigos
  - Mobile
tags:
  - mobile
  - Offline
  - web storage

---
Você está em casa à noite e resolve baixar um jogo no seu smartphone. Depois de algumas horas jogando, é hora de ir dormir porque no dia seguinte você tem um voo para pegar. Logo após a decolagem você resolve passar mais uma fase daquele joguinho que instalou. Ao abrir o aplicativo, você se depara com a necessidade de conexão com a internet para jogar (e muitas vezes até para abrir o jogo). 

Isso não é &#8220;privilégio&#8221; apenas de jogos e acontece com frequência porque boa parte das aplicações dependem da conexão à internet para funcionar (mesmo aquelas que foram baixadas previamente). Muitas vezes isso é desnecessário pois a aplicação que envia pequenos pacotes de dados poderia acumular esses pacotes caso estivesse sem uma conexão disponível no momento. 

Foi com esse intuito, de promover a criação de aplicações que funcionem também _off-line_, que estão surgindo iniciativas para auxiliar o desenvolvimento de _apps_ que sobrevivam quando você estiver em um túnel, no avião ou no meio de uma trilha na floresta. Uma delas é a [_Off-line first_][1], que defende que sua aplicação deve estar pronta para cenários sem acesso a internet. Essas iniciativas fazem uso de recursos e documentação que já estamos acostumados a acompanhar, mas nem sempre com esse viés de garantir o funcionamento sem internet. 

Um dos pontos fundamentais para o funcionamento de aplicações Web rodarem _off-line_ é garantir que seja possível acessa-las em cache. Pode parecer desnecessário e redundante falar isso em pleno 2015, mas ainda existem aplicações que não armazenam dados em cache.

Dentro da [documentação do HTML5][2] existe um tópico dedicado exclusivamente para aplicações _Web off-line_. Para ilustrar essa documentação, o próprio W3C mostra um exemplo simples de uma aplicação de um relógio, e como adicionar o _manifest_ de forma adequada. [O exemplo desse relógio está disponível na página do WHATWG][3]. 

Além disso, temos em nosso favor a [Web Storage API][4], que nos possibilita armazenar dados da aplicação no _client side_.

A preocupação em garantir o funcionamento de aplicações _off-line_ não é está apenas dentro das recomendações do W3C. O [Google tem uma área interessante sobre a criação de apps][5] _off-line first_. O documento começa com algumas dicas fundamentais para a criação do aplicativos:

  * Os arquivos do aplicativo &#8211; JavaScript, CSS e fontes, além de outros recursos necessários (como imagens) já foram baixados.
  * Seu aplicativo pode salvar e sincronizar (de forma opcional) pequenas quantidades de dados.
  * Seu aplicativo pode detectar mudanças na conectividade.

Mesmo que essas dicas sejam insuficientes, o Google recomenda seguir algumas regras para isso:

  * Use dados locais sempre que possível
  * Separe UI (User Interface) dos dados da sua aplicação
  * Suponha que seu aplicativo pode ser fechado a qualquer momento.
  * Teste seu aplicativo cuidadosamente.

A [Mozilla também tem documentação muito interessante sobre a construção de aplicações desconectadas da internet][6]. Lá também estão algumas recomendações para o desenvolvimento de uma boa aplicação _off-line_. Basicamente a documentação recomenda o seguinte:

  * A aplicação deve detectar o estado “_off-line_”
  
    Já existem APIs que determinam o status de conexão do usuário, sem a necessidade de _HTTP request_.
  * Armazenamento de “_data and assets_” _off-line_
  
    Garanta que o armazenamento de dados possa ser feito no dispositivo do usuário.
  * Salve os status da aplicação periodicamente
  
    Durante o uso da aplicação, considere salvar periodicamente o status no dispositivo do usuário.
  * Sincronize com o servidor
  
    A aplicação deve enviar periodicamente os dados para o servidor. Quando não conseguir, ela pode fazer o armazenamento no dispositivo do usuário e enviar quando possível. Considere construir uma solução para organizar a fila de pacotes quando a conectividade cair.

Mesmo sabendo que a conectividade vem aumentando e melhorando de forma exponencial, vale a pena planejar o uso da sua aplicação em um cenário sem internet. Em um país com proporções continentais como o Brasil e com um percentual de 84% da população com telefone celular ([dados do Cetic.br de 2014][7]), é fundamental que a aplicação não se limite apenas a momentos em que o usuário esteja conectado (claro que isso não é possível em todas as aplicações). A Web móvel é uma realidade e a mobilidade nos deixa sujeitos a oscilações de conectividade. E nossas aplicações devem estar prontas para isso.

Boas referências para estudo:

  * HTML5 Recommendation – Offline Application &#8211; <http://www.w3.org/TR/html5/browsers.html#offline>
  * Web Storage API &#8211; <http://www.w3.org/TR/webstorage/>
  * Google Chrome Apps – Offline First &#8211; <https://developer.chrome.com/apps/offline_apps>
  * Mozzila App Center – Working Offline &#8211; <https://developer.mozilla.org/en-US/Apps/Build/Offline>
  * Designing Offline-First Web Apps &#8211; <http://alistapart.com/article/offline-first>
  * Offline First &#8211; <http://offlinefirst.org/>

 [1]: http://offlinefirst.org/
 [2]: http://www.w3.org/TR/html5/browsers.html#offline
 [3]: https://whatwg.org/demos/offline/clock/live-demo/clock.html
 [4]: http://www.w3.org/TR/webstorage/
 [5]: https://developer.chrome.com/apps/offline_apps
 [6]: https://developer.mozilla.org/en-US/Apps/Build/Offline
 [7]: http://data.cetic.br/cetic/explore?dados=%7B%22idPesquisa%22:%22TIC_DOM%22,%22idUnidadeAnalise%22:%22Usuarios%22,%22paletaCor%22:%22paleta1%22,%22aba%22:%22filtroIndicador%22,%22tpGrafico%22:%22tipo2%22,%22ano%22:%222014%22,%22idIndicador%22:%2226335%22,%22idsDimensaoN1%22:%22%22,%22idsDimensaoN2%22:%22%22,%22idsAgrupamentoN1%22:%22235088%22,%22idsAgrupamentoN2%22:%221141546%22%7D