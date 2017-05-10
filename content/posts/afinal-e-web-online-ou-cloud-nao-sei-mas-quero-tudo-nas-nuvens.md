---
title: Afinal é web, online ou cloud? Não sei mas quero tudo nas nuvens!
author: Carlos Renato Gaddini
type: post
date: 2014-05-29
excerpt: Desde 2004 venho acompanhando bem de perto o mundo web. Muitas empresas vem ano após ano investindo pesado para tirar as informações de dentro da empresa, literalmente. Várias vertentes tem sido abordadas por empresas de software que precisam determinantemente exteriorizar  os dados de seus clientes, afinal tudo cada dia está mais conectado.
url: /afinal-e-web-online-ou-cloud-nao-sei-mas-quero-tudo-nas-nuvens/
dsq_thread_id: 2719827266
categories:
  - Mercado e Comportamento

---
Felizmente vem pouco a pouco entrando nas pautas de desenvolvimento um conceito que já é adotado mundialmente principalmente encabeçado pelas desenvolvedoras de software livre: _O conceito de intercomunicação entre aplicações e intercomunicação entre ecossistemas diferentes_, como softwares online com desktop, desktop para desktop e online para online. E isso certamente é um grande progresso a nível de Brasil.

O grande “canal” que está possibilitando conectar tudo que é informático no mundo é a internet. Internet que para milhões de pessoas é uma espécie de “linha de telefone” para ligar computadores uns aos outros diretamente a serviços como o Facebook, Twitter ou email de uma maneira simples: o computador A manda uma mensagem por um aplicativo e esse por pulsos elétricos é recebido no computador B como se fosse um SMS. Pois é esse é o conceito do senso comum por aqui.

As pessoas não fazem idéia da _parafernalha_ necessária por trás da tela para fazer tudo isso funcionar. E funcionar rápido e eficazmente. Não imaginam por quantas camadas as informações passam, são convertidas em bytes, depois empacotadas, divididas em inúmeras partes, viajam pelo protocolo IP até um servidor que recebe, processa, remonta e armazena a informação que depois é retransmitida a outros _n_ servidores depois redivididas, retransmitidas, para serem recompostas e recebidas pelo software cliente e então é vista instantâneamente de mídias n para n. Isso sem falar em APIs de diversos aplicativos. Se analisarmos tecnicamente podemos dizer que, por exemplo no Facebook uma simples mensagem de 32kb de tamanho pode gerar 500, 600 ou mais kb em diferentes servidores e máquinas como desktop ou celulares.

Geramos muita informação e queremos que ela seja não só 100% confiável, mas 100% acessível de qualquer lugar a qualquer hora e que também que fique guardada eternamente.

Redes de computadores não são exatamente uma novidade assim como a utilização de computadores para comunicação e a internet. Mas o que mudou que fez nós também mudarmos nosso comportamento social, econômico e comercial?

> A incrível possibilidade de ter nossos dados acessíveis instantaneamente de qualquer lugar do mundo.

E isso foi parar nos sistemas das empresas. Para mim, que sou das “antigas” gosto de chamar de **netserver**, mas esse termo está meio impopular. Aqui no Brasil, os primeiros sistemas “fora de casa” não poderiam serem chamados de “aplicação em um servidor externo” porque deixaria os clientes um pouco confusos e não soaria comercial. E também porque não estava sendo contratado um servidor dedicado para cada cliente. Foi então que se popularizou o termo **online** que embora tecnicamente não quer dizer absolutamente nada além de estar “ligado” em uma tradução livre, foi bem aceito. Foi aí que entrei na onda de fazer sistemas online, termo que uso até hoje em algumas aplicações da qual participo.

Certa vez, há uns 4 anos, um cliente me ligou desesperado em uma segunda-feira marcando uma reunião em sua empresa. Prontamente atendi ao pedido do cliente e na reunião, o seu responsável de TI foi enfático em afirmar que o sistema que eles haviam adquirido recentemente estava tecnologicamente defasado, que deveria ser urgentemente atualizado. Fique espantado. Na ocasião estávamos “up-to-date” em relação a tecnologia disponível para web na época. Então indaguei qual seria a tecnologia que seu sistema deveria ser feito para não estar mais defasado e então ele disse com uma única palavra que me deixou perplexo e quase atônito: &#8220;Cloud! Quero que meu sistema seja Cloud!&#8221;
  
Depois de uns 20s para reiniciar meu sistema, comecei a pensar naquilo que ele havia me solicitado. E&#8230; fiquei sem resposta. Apenas disse que voltaria para meu QG e que iria pesquisar junto à minha equipe de desenvolvimento e em breve lhe daria uma resposta.

Até então, o conceito que eu sabia sobre Cloud era simples: que estava em mais de um lugar na internet ou computação distribuída &#8211; termo que eu havia conhecido no mundo Linux &#8211; e que não representaria substancialmente alguma mudança no comportamento da aplicação, seria transparente para o cliente.

Mas como sabemos, o Brasil é muito inventivo &#8211;  também gosto de chamar de “terra das oportunidades” &#8211; porque as vezes tenho a impressão que algumas empresas ficam o dia todo pesquisando coisas na internet “gringa” e transformam isso em negócios &#8211; mas isso fica para um outro artigo quem sabe…

Abri minha página de busca e pesquisei **cloud** para ver o que aparecia. Para minha surpresa, 3 empresas estava oferendo cloud aqui no Brasil. Me surpreendi, afinal porque serviço cloud separado? O que estava sendo oferecido?

Bom, como eu já falei _cloud_ ou _cloud computing_ significa apenas disponibilizar vários servidores em redes e/ou locais diferentes mas que se comportem como um só. Sim é isso! Mas… o que ví foi o oferecimento de hospedagem escalável &#8211; que é possível mudar capacidades separadas de componentes virtuais como memória, processadores ou espaço em disco &#8211; sem precisar adotar pacotes para mudar de categoria de hospedagem.

Bom, em qualquer uma das duas situações &#8211; a original ou a nacional &#8211; não traria qualquer diferença para esse cliente com seu volume de dados. Marquei nova reunião para _tentar_ explicar isso e após alguns minutos o cliente disse o seguinte: _Não quero saber se é online ou cloud, quero meu sistema nas nuvens!_

Como estamos em uma “terra de coronéis” e que a sua palavra é a que vale, sorteei uma das 3 empresas e encaminhei a contratação para o cliente. Transferi para lá e ele tá usando até hoje feliz da vida…

Não vou citar nomes, nem falar dessa ou daquela empresa provedora dessas tecnologias, mas tenho sentido o Brasil um pouco sem opções. Vejo inúmeras empresas oferecendo serviços, mas quando faço uma investigação, caio nas seguintes situações: a) A empresa em si não tem tecnologia nenhuma, apenas revende serviços dos datacenters nacionais como a Embratel, Telefonica e Terra Empresas; b) Ficam fora do país (Índia, China ou EUA) o que acarreta em dificuldade de suporte, latência alta (acima de 50ms) e problemas crônicos de roteamento.

Mas então, o que fazer?

Simples! Ter seu próprio server.

Hoje tenho tido bons resultados nessa idéia e vale a pena experimentar. Uma coisa deve ser falada: hospedagem é boa para sites, não para sistemas.

Quais são as vantagens e desvantagens de alugar um Server dedicado?

Desvantagens:

  * Custo (ainda) elevado
  * Exige mais conhecimento técnico do administrador
  * Ter critério maior nas atualizações
  * Dificuldade de expansão

Vantagens:

  * Maior segurança
  * Facilidade de backup
  * Atualizações específicas
  * Expansão facilitada
  * Direcionamento para o Plano de Negócios

Hoje algumas empresas estão se especializando no fornecimento de servidores dedicados a preços bem acessíveis e com uma configuração razoável. O mundo está em constante mudança, não é mesmo?