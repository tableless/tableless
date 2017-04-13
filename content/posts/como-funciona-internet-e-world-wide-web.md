---
title: Como funciona a Internet e a World Wide Web
author: Marcel dos Santos
type: post
date: 2015-11-23
excerpt: Conhecermos alguns conceitos por trás do funcionamento da Internet e da World Wide Web é fundamental para os que entram no mundo do desenvolvimento web.
url: /como-funciona-internet-e-world-wide-web/
categories:
  - Geral
tags:
  - internet
  - World Wide Web

---
Muitas pessoas se encantaram com a **Web** e gostariam que ela fizesse parte da sua vida pessoal e/ou profissional. Comigo foi assim, com alguns amigos também e, acredito, que com você também foi assim. Afinal, quem não queria fazer parte desta história?

Acontece que muitas pessoas que entram neste mundo do **desenvolvimento web** sequer sabem, de fato, como a Web funciona. Iniciam querendo aprender a criar sites com HTML, CSS, JavaScript, PHP ou _<insira sua linguagem predileta aqui>_ sem saber seu funcionamento. Por isso, é importante conhecermos alguns conceitos por trás do funcionamento da **Internet** e da **World Wide Web**.

A **Internet** é uma rede que interconecta computadores e outros dispositivos como o seu celular em escala global para a transferência de dados entre eles. Já a **World Wide Web** é uma aplicação onde páginas são interligadas através de _links_ e que se utiliza da Internet para funcionar.

Muito sucinto, não? Então vamos ver com um pouco mais de detalhes&#8230;

## Redes de computadores

Antes de falarmos sobre a Web, precisamos conhecer um pouco sobre **rede de computadores**. Uma **rede de computadores** é a interconexão entre computadores que permite a **comunicação de dados** entre si. Esta comunicação pode ser feita através de **cabos** ou **sem fios**. Para entender melhor como os computadores se comunicam entre si, utilizarei como exemplo o _acesso a uma página da web_.

<img class="alignnone wp-image-51929 size-full" title="Redes de computadores" src="http://tableless.com.br/uploads/2015/10/computer-network.png" alt="Redes de computadores" width="760" height="400" />

Suponha que queira acessar o site do **<a href="http://www.pensandonaweb.com.br" target="_blank">Pensando na Web</a>** para ler alguns posts interessantes sobre desenvolvimento web. Daí você abre o seu navegador predileto e digita `www.pensandonaweb.com.br` na barra de endereços e, passados poucos segundos, a página inicial do blog é exibida. Como esse processo todo, aparentemente simples, ocorre?

## Endereço IP e portas

Acontece que os computadores possuem um endereço numérico único chamado **endereço IP** e, além deste endereço, possui também inúmeras **portas** por onde as _aplicações_ e _processos_ se comunicam. Para que você acesse a página desejada, de fato, o seu computador precisa antes **estabelecer uma conexão** com o computador onde a página solicitada está hospedada.

> Chamaremos, a partir de agora, o seu computador de **cliente** e o computador onde a página está hospedada de **servidor**.

Continuando com o exemplo anterior, vamos imaginar que o **cliente** de endereço IP `177.178.79.80` queira, através da porta `65000`, iniciar uma conexão com o **servidor** de endereço IP `185.186.87.88` na porta `80` para obter a página inicial do Pensando na Web.

<img class="alignnone wp-image-51930 size-full" title="Modelo cliente-servidor" src="http://tableless.com.br/uploads/2015/10/client-server-model.png" alt="Modelo cliente-servidor" width="760" height="320" />

Mas espere, como o cliente sabe o endereço IP e a porta no servidor que deve conectar para obter a página inicial do Pensando na Web se nada disso foi informado? Ou melhor, se só o que foi informado foi `www.pensandonaweb.com.br` na barra de endereços de seu navegador?

## DNS e portas conhecidas

Quando um computador está ligado em rede, ele está configurado para acessar um servidor especial chamado **servidor de nomes** ou **servidor DNS**, como é mais conhecido. Este servidor funciona como uma lista telefônica.

Quando digitamos `www.pensandonaweb.com.br` na barra de endereços, estamos informando o **endereço** ou a **URL** (_Uniform Resource Locator_) do site que desejamos acessar. Se o navegador não conhecer o endereço IP para esta URL &#8211; afinal, ele deve visitá-la várias vezes ao dia 🙂 &#8211; ele se conecta ao **servidor DNS** e pergunta: Olá, tudo bem? Tenho a URL `www.pensandonaweb.com.br`, você pode me informar o endereço IP dela? Eis que o **servidor DNS** responde: Pois não, o endereço IP desta URL é `185.186.87.88`.

Hmmm, interessante! Mas como se sabe em qual porta deve se conectar?

Imagine o seguinte, algum desconhecido passa pelo bairro onde você mora e te pergunta onde fica a padaria ou o mercadinho. E você prontamente responde, a padaria é no final desta rua e o mercadinho fica ao lado da padaria. Isso é automático para você, estes estabelecimentos sempre estiveram no mesmo lugar desde quando você era criança e dificilmente mudam de lugar. E quando mudam, os interessados são sempre informados.

O mesmo acontece com as **portas** disponíveis num computador, elas são **conhecidas** de acordo com o **serviço** que oferecem. Se precisar de um serviço de transferência de arquivos ou **FTP**, ele pode ser encontrado na _porta 21_. Se precisar de um _shell_ remoto e seguro ou **SSH**, ele estará na _porta 22_. Se precisar de um serviço de entrega de e-mail ou **SMTP**, ele estará na _porta 25_. Ou, ainda, se precisar de um serviço de entrega de páginas web, ele estará na _porta 80_.

Todos como se fossem os estabelecimentos do bairro onde você mora, muito bem conhecidos e raramente mudam de lugar.

> O **servidor DNS** funciona como uma lista telefônica para encontrar o endereço IP da URL solicitada. Já as **portas** são conhecidas de acordo com os serviços oferecidos. O serviço de entrega de páginas web encontra-se na _porta 80_ e o serviço de entrega de e-mail encontra-se na _porta 25_, por exemplo.

## TCP/IP, como os computadores se comunicam

Uma vez conhecido o **endereço IP** do destino e a **porta** na qual deseja se conectar, o cliente precisa **estabelecer uma conexão** com o servidor. A conexão é estabelecida da seguinte maneira:

**Cliente:** Boa tarde `185.186.87.88`, desejo estabelecer uma conexão na porta `80`?
  
**Servidor:** Boa tarde `177.178.79.80`. Pode realizar a conexão.
  
**Cliente:** Ok, iniciarei a conexão. _Os pacotes começam a ser enviados a partir deste momento&#8230;_

Este tipo de conexão utiliza o protocolo **TCP** ou _Transmission Control Protocol_ e é através deste protocolo que o **cliente** e o **servidor** conversam entre si. Através desta conexão ocorre o envio de **pacotes**, fragmentos menores dos dados que serão trafegados que contém informações como a _porta de origem_, a _porta de destino_ e a _sequência_ que devem ser reconstruídos ao chegar no destino.

Este é um tipo especial de conexão pois ela é **ponto-a-ponto**, ou seja, a comunicação pode ser feita em duas vias (o cliente fala com o servidor e o servidor fala com o cliente). Outra característica importante é a **garantia de entrega** onde todos os pacotes que saem da _origem_ possuem a garantia de que chegarão ao _destino_ e que serão entregues de forma **ordenada** e **sem modificações**. Outra característica importante ainda é o **controle de fluxo** que controla a quantidade de pacotes enviados ou recebidos aumentando ou diminuindo de acordo com a necessidade.

Ou, numa breve alusão ao serviço de correios de carta registrada, as suas correspondências chegarão ao destino, na ordem correta e não serão violadas ou abertas. E, se sua caixa de correio da sua casa estiver cheia, as correspondências serão entregues numa frequência menor até que sua caixa de correio tenha mais espaço!

> O **TCP** é um protocolo de rede que permite a comunicação entre computadores e uma conexão deve ser estabelecida antes do início do envio de pacotes. Ele é um protocolo **ponto-a-ponto**, possui **garantia de entrega** de pacotes de forma **ordenada** e **sem modificações** e possui **controle de fluxo**.

Certo, mas o que acontece quando a conexão é estabelecida? Existe uma aplicação conhecida como **servidor web** que **recebe e manipula** todos os pacotes que vem pela **porta 80**. Vamos ver o seu funcionamento mais adiante&#8230;

## HTTP, o idioma dos navegadores e servidores web!

Imagine o seguinte, você mora no prédio localizado no endereço IP `185.186.87.88` e o seu apartamento é o de número `80`. O seu trabalho é enviar páginas com as informações variadas para quem as solicita através do correio. Uma pessoa qualquer te envia uma carta solicitando uma página com informações sobre _futebol_, por exemplo. Você recebe esta carta, abre ela, analisa a solicitação, monta a página com a informação solicitada, coloca a página num envelope e a envia de volta para o remetente. Só que esta comunicação se dá num idioma próprio, que somente vocês entendem.

Se alguém, por engano, enviar uma carta solicitando uma página com informações sobre _viagens_ para o seu vizinho do `21`, o Sr. Fábio Teixeira Pimentel (ou FTP para os íntimos), não receberá nada de volta. Isso acontece porque ele não entenderá o idioma escrito na carta e, de qualquer forma, ele só trabalha com transferência de arquivos e não com o envio de páginas.

Esse idioma é o **HTTP** ou _Hypertext Transfer Protocol_ e é o idioma que os **navegadores** e os **servidores web** conversam. É através deste idioma que o seu navegador informa ao servidor web qual a sua **versão**, qual o seu **idioma**, se aceita **conteúdo compactado** ou não e qual **página** foi solicitada. E, da mesma forma, é através deste idioma que o servidor web informa ao seu navegador se a **página solicitada existe**, qual o seu **formato**, se a página enviada foi **compactada**, se existe algum _**cookie**_ para ser gravado no seu computador e, principalmente, o **conteúdo da página** solicitada.

Quando o navegador solicita uma página web é chamado de **requisição** e quando o servidor web envia a página web solicitada de volta para o navegador é chamado de **resposta**. Cada requisição realizada pelo navegador é independente umas das outras e, por este motivo, o HTTP é considerado um protocolo **sem estado** ou **_stateless_**. E o que isso quer dizer? Quando você realiza uma nova requisição (ao mudar de página no site, por exemplo) o servidor web não lembra que você realizou uma requisição anterior.

A **requisição** realizada pelo seu **navegador** se parece com isso:

<pre>GET / HTTP/1.1
Host: www.pensandonaweb.com.br
Connection: keep-alive
Cache-Control: no-cache
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
Pragma: no-cache
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_9_2) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/34.0.1847.116 Safari/537.36
Accept-Encoding: gzip,deflate,sdch
Accept-Language: en-US,en;q=0.8,es;q=0.6,pt;q=0.4
</pre>

E a **resposta** gerada pelo **servidor web** se parece com isso:

<pre>HTTP/1.1 200 OK
Date: Mon, 31 Mar 2014 22:01:16 GMT
Server: Apache
Content-Type: text/html
Cache-Control: no-store
Pragma: no-cache
Vary: Accept-Encoding,User-Agent
Content-Encoding: gzip
Connection: close
Transfer-Encoding: chunked

&lt;!doctype html&gt;
&lt;html lang="en"&gt;
&lt;head&gt;
&lt;meta charset="UTF-8"&gt;
&lt;title&gt;Pensando na Web&lt;/title&gt;
...
&lt;/head&gt;
&lt;body&gt;
...
&lt;/body&gt;
&lt;/html&gt;
</pre>

Este processo de _requisição_ e _resposta_ por meio do protocolo HTTP acontece através da conexão estabelecida entre o _cliente_ e o _servidor_ por meio do protocolo TCP. As **mensagens** de requisição e resposta geradas pelo navegador e servidor web são quebradas em _pacotes_ e enviadas através da rede com toda a &#8220;infraestrutura&#8221; que o TCP oferece. Esta abordagem que os sites e aplicações web utilizam é conhecida como arquitetura **cliente-servidor**.

[<img class="alignnone wp-image-51931 size-full" title="Arquitetura cliente-servidor" src="http://tableless.com.br/uploads/2015/10/client-server-approach.png" alt="Arquitetura cliente-servidor" width="760" height="560" />][1]

O HTTP tem se tornado um &#8220;idioma&#8221; amplamente falado. Outras aplicações, além de seu navegador e de servidores web, estão aprendendo a falar este idioma. Programas de linha de comando como o **curl** e o **wget** e a maior parte das linguagens de programação sabem falar o HTTP. Aqueles aplicativos marotos de listas de tarefas e redes sociais que você tem no seu _smartphone_ também utilizam o HTTP para se comunicar. Guarde este nome, que você irá ouvi-lo bastante caso decida seguir a vida de desenvolvedor web.

> O **HTTP** é o protocolo utilizado pelos **navegadores** e **servidores web** se comunicarem. Quando o navegador solicita uma página web é chamado de **requisição** e quando o servidor web envia a página solicitada de volta é chamado de **resposta**. Esta abordagem é conhecida como arquitetura **cliente-servidor**. Na requisição é informado qual o **idioma** utilizado e a **página** solicitada e na resposta é informado o **formato** e o **conteúdo** da página.

Certo, falamos de rede de computadores, endereços IP e portas, servidores DNS, protocolos TCP e HTTP mas ainda não foi falado como as páginas web de fato são exibidas.

## HTML

Voltando algumas linhas acima, vemos a resposta que o servidor web enviou ao navegador como resultado de uma requisição. Perceba que esta resposta é dividida por uma linha vazia. Acima da linha encontra-se o **cabeçalho da resposta** e abaixo o **conteúdo da resposta**. E, neste exemplo, o formato do conteúdo é um **documento HTML**, visto que solicitamos uma página web.

Uma vez que o documento HTML é obtido, o navegador **analisa** seu conteúdo e realiza outras requisições para obter os outros **recursos** que também compõe a página web como _folhas de estilo_, _scripts_ e _imagens_, por exemplo. Com o documento HTML e o restante dos outros recursos, o navegador começa a **renderizar** a página web.

Quando uma página web é acessada, o navegador, não faz apenas uma, mas diversas requisições para obter todo o conteúdo da página. Isso quer dizer que através da **requisição** pode-se obter não só _documentos HTML_, mas também recursos de diversos tipos como _imagens_, _documentos PDF_, _vídeos_ entre outros inúmeros formatos.

O **HTML** ou _Hypertext Markup Language_ é uma **linguagem de marcação** utilizada para criar páginas web. Ela foi criada por **<a href="https://pt.wikipedia.org/wiki/Tim_Berners-Lee" target="_blank">Tim Berners-Lee</a>**, o também criador do protocolo HTTP e da World Wide Web, e no início suportava apenas elementos de textos e links. Hoje o HTML encontra-se numa fase mais madura, com suporte a dezenas de funcionalidades e fazendo parte de um conjunto de tecnologias como o **CSS** e o **JavaScript**, que são a base para a web atual.

Mas o HTML é um assunto para um outro post, onde poderá ser explicado com mais detalhes a sua estrutura e o seu funcionamento.

## Finalmente, o que é a Internet e a World Wide Web?

Os conceitos abordados nas seções anteriores estão por trás do funcionamento da Internet e da World Wide Web. Como dito anteriormente, a **Internet** é uma rede que interconecta **computadores**, ou mais especificamente, uma rede que interconecta outras **redes de computadores**. A sua infraestrutura é composta por bilhões de dispositivos como servidores, roteadores, computadores, _tablets_, _smartphones_ interligados por complexas estruturas de comunicação, por meio de satélites, cabos ópticos espalhados pelo mundo ou sem fio.

Vários **serviços** funcionam sobre a infraestrutura da Internet, como os serviços de _telefonia_ (voz sobre IP), _correio eletrônico_ (e-mail), _aplicações peer-to-peer_, _transferência de arquivos_ e a _World Wide Web_.

Existe uma confusão quando as pessoas dizem que &#8220;vão acessar a Internet&#8221; quando se referem ao ato de abrir o navegador e navegar entre as páginas. Na verdade, elas estão acessando a World Wide Web. Porém, isso não torna a afirmação anterior inválida, pois se a World Wide Web funciona sobre a infraestrutura da Internet, as pessoas de fato estão acessando a Internet. Mas as pessoas poderiam seguramente dizer que &#8220;vão acessar a Internet&#8221; também quando forem fazer uma chamada no Skype, enviar uma mensagem pelo WhatsApp, enviar um e-mail ou mesmo baixar alguns arquivos através do FTP, pois todos estes serviços, assim como a World Wide Web, também rodam sobre a infraestrutura da Internet.

Já a **World Wide Web** é uma aplicação onde documentos e/ou páginas web são interligados através de _links_ e que se utiliza da Internet para funcionar. Utilizamos o **navegador** e através das **URLs** acessamos estas páginas web e, ao clicar em um link, este processo todo é repetido para a nova página que será aberta. É através dela que conseguimos acessar os **sites** e as **aplicações web**. Google, Google Maps, Twitter, Facebook, Gmail, YouTube, Netflix, Spotify, Wikipedia, WordPress, UOL, Globo.com, Dropbox e seu _bankline_ são todos exemplos de aplicações web.

A diferença entre **sites** e **aplicações web** é bastante subjetiva. Um **site web** pode ser caracterizado pelo seu _conteúdo_ enquanto uma **aplicação web** pode ser caracterizada pela _interação_ do usuário. Um site institucional de uma empresa que conta sua história, exibe seus produtos e informações de contato é um exemplo de um **site web**. Ele é composto por várias **páginas web** com foco no _conteúdo_. Já um tocador de música _online_ que permite buscar artistas e músicas, criar listas de reprodução e tocar as músicas exibindo a capa do álbum e o progresso da música é um exemplo de uma **aplicação web**. As _interações_ constantes do usuário como buscar artistas, reproduzir ou avançar entre as músicas é o seu diferencial.

As **aplicações web** possuem diversas vantagens em relação às _aplicações nativas_ como acessar os seus dados de qualquer lugar, utilizar sempre sua versão mais nova e acessar de qualquer dispositivo que possua um _navegador web_ sem se preocupar com a plataforma ou dispositivo utilizado. Utilizando uma aplicação web de e-mail, por exemplo, você acessará seus e-mails de qualquer lugar, utilizando sempre a versão mais nova e de qualquer dispositivo como um computador ou um _smartphone_.

> A **Internet** é uma rede que interconecta computadores e outras redes de computadores e é composta por bilhões de dispositivos como servidores, roteadores, computadores e dispositivos móveis. Vários **serviços** funcionam sobre a infraestrutura da Internet como a _telefonia_ (voz sobre IP) e a _World Wide Web_. A **World Wide Web** é uma aplicação onde documentos e/ou páginas são interligadas através de _links_. É através dela que, por meio de um _navegador_ e através de _URLs_, acessamos os **sites** e as **aplicações web**.

## Conclusão

O entendimento do funcionamento da Internet e da World Wide Web é importante para quem deseja seguir a carreira de desenvolvedor web. Apesar de parecer complexo, compreender o funcionamento de ambas é razoavelmente fácil e não há a necessidade de entrar em detalhes ou em tópicos mais avançados num primeiro momento.

A sua compreensão sobre o assunto te ajudará no entendimento de outros conceitos relacionados ao desenvolvimento web e facilitará o seu caminho nesta jornada. Bons estudos! 😉

 [1]: http://tableless.com.br/uploads/2015/10/client-server-approach.png