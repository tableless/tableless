---
title: Criando seu próprio servidor HTTP do zero (ou quase) – Parte I
author: thiguetta
type: post
date: 2015-09-01
url: /criando-seu-proprio-servidor-http-do-zero-ou-quase-parte-i/
categories:
  - Back-end
  - Browsers
  - Código
  - HTML
  - HTML5
  - Java
tags:
  - desenvolvimento
  - desenvolvimento web
  - http
  - java
  - Na Prática
  - w3c
  - web standards

---
Sou apaixonado por tecnologias livres e como sou extremamente curioso, gosto de saber como as coisas funcionam. Como também sou cinestésico, não me contento em apenas em entender, tenho que criar, recriar, escrever, rescrever, inventar, reinventar, enfim sentir realmente como se faz. Nesse vai e vem de aprendizado, minha última curiosidade foi entender como os servidores HTTP funcionam e criar um do zero (ou pelo menos quase).

É claro que para fazer isso eu não fui tão lá embaixo a ponto de utilizar C, utilizei da linguagem de programação da qual me sinto mais confortável e que já oferece algumas facilidades que em C teria que sangrar pra fazer o mesmo porém não impossível, mas enfim, optei por desenvolver em Java, os passos vou contar pra vocês aqui, mas utilizando os mesmo conceitos nada impede que utilize qualquer outra linguagem de programação.

## Introdução

Vamos ao que interessa! A grosso modo, um servidor HTTP é uma aplicação (software) que fornece páginas web (geralmente escritas em HTML), ou seja, ao digitar o endereço da página (URL) e dar um ENTER no seu navegador, ele envia uma requisição no servidor destino, o servidor processa essa informação e retorna o documento HTML correspondente, por fim o navegador renderiza o documento e exibe aquela página bonita (nem sempre!).

<div style="width: 510px" class="wp-caption aligncenter">
  <a href="http://www.tankonyvtar.hu/en/tartalom/tamop425/0027_ADW1/images/ADW100.png"><img src="http://www.tankonyvtar.hu/en/tartalom/tamop425/0027_ADW1/images/ADW100.png" alt="Requisição HTTP" width="500" height="200" /></a>
  
  <p class="wp-caption-text">
    Requisição HTTP
  </p>
</div>

Para isso vamos entender como a comunicação entre seu navegador e o servidor funciona, o protocolo, depois vamos entender como é feita a conexão, tratar e enviar documentos e por fim vamos deixar nosso servidor pronto para receber múltiplas conexões.

## O Protocolo HTTP

É claro que nem so de Web a Internet é feita, existem uma serie de recursos que estão sobre a Internet, a web é uma delas, mas para que esses serviços sejam tratados como devem é necessário ter um linguagem comum que permita que o servidor entenda o que o navegador quer, e que o navegador saiba se a resposta do pedido está correta ou não, para isso estabelecem-se os protocolos, que são padrões estipulados por um órgão competente afim de uniformizar o “trafego” de informações de diferentes serviços na internet. Quem define esses padrões é a IETF (Internet Engineering Task Force, ou melhor, Força Tarefa de Engenharia da Internet). Para saber mais quem são eles, acesse <a href="http://www.ietf.org" target="_blank">aqui</a> (em Inglês)

O protocolo HTTP, ou Hyper Text Transfer Protocol, ou melhor ainda, protocolo de transferencia de hiper texto, direto e reto é o cara que define a troca de paginas HTML, pronto falei!. A versão mais atual (que é a que vamos adotar nesse tutorial por assim dizer) é a 1.1 que na minha opinião é a mais difundida também (pode ser que encontre por ai alguns utilizando a versão 1.0 ou até mesmo a 0.9), enfim , essa versão e seus padrões foram propostos no documento <a href="http://www.ietf.org/rfc/rfc2068.txt" target="_blank">RFC 2068</a> e atualizado e alterado por diversos outros RFCs, que não convém a gente falar aqui, mas se tiver curiosidade procura lá no site da IEFT acima que tem todos.

So para nos situar o HTTP está na camada mais alta do protocolo de comunicação de rede conhecido como TCP/IP (não vamos entrar em detalhes pois não é o foco), chamada camada de aplicação (Nada mais justo já que o servidor e o navegados são aplicações).

<div style="width: 430px" class="wp-caption aligncenter">
  <a href="http://static.thegeekstuff.com/uploads/2011/10/tcp-ip.png"><img src="http://static.thegeekstuff.com/uploads/2011/10/tcp-ip.png" alt="Camadas de Rede (TCP/IP)" width="420" height="470" /></a>
  
  <p class="wp-caption-text">
    Camadas de Rede (TCP/IP)
  </p>
</div>

No nosso escopo, o servidor é um software que fica aguardando solicitações, falando em nível de aplicação, o processo é simples, o navegador (vamos chamar de cliente) envia uma requisição (request), o servidor processa e devolve uma resposta(response).

## A Requisição

A requisição é um “documento” em texto plano composto por um cabeçalho (que define  a comunicação, requerido) e os dados (opcional, depende da aplicação).

O cabeçalho é bem simples, a primeira linha contém a informação principal da requisição, ou seja, qual a sua solicitação (método), o que está sendo solicitado (arquivo/página/recurso a ser acessado) e padrão de comunicação que no nosso caso é o HTTP/1.1, a segunda linha é o endereço de host do servidor que irá responder a sua solicitação, veja o exemplo:

<pre>GET /index.html HTTP/1.1
Host: <a href="http://google.com">google.com</a></pre>

As linhas seguintes são informações pertinentes a conexão e podem conter informações de quem está solicitando, o formato dessas informações é do tipo <propriedade> : <valor> o final de cada linha é encerrado por um <CR><LF> (cuidado, pois muitos confundem este comando com o ENTER, embora para windows esse comando corresponde ao ENTER, não é verdade para Linux e afins), o final da requisição deve ser uma linha em branco (ou seja apenas um <CR><LF>)veja o exemplo de uma requisição completa

<pre>GET /HTTP/1.1
Host: www.google.com.br
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10.9; rv:29.0) Gecko/20100101 Firefox/29.0
Accept: text/html,application/xhtml+xml,application/xml
Accept-Language: pt-BR,pt,en-US,en
Accept-Encoding: gzip, deflate
Connection: keep-alive</pre>

Traduzindo, queremos pegar (GET) a raiz ou página inicial ( / ) que está em “www.google.com.br”. Esta requisição está sendo enviada de um navegador (User-Agent) Firefox, que aceita (Accept) os seguintes formatos, html e xml de preferencia que estejam no idioma (Accept-Language) Português do Brasil (pt-BR) ou qualquer outro idioma a seguir (veja que é possível passar uma lista de idiomas na ordem em que gostaria que aparecessem, veja que caso o servidor não tenha nenhuma dessas páginas ou não trate essa propriedade, ele irá devolver a página no idioma padrão do html que ele encontrar correspondente a sua solicitação), o formato de compactação aceito pelo navegador  (Accept-Enconding) e por fim a persistência da conexão, ou seja se você quer que o servidor mantenha a conexão ativa, o que eu quero dizer é que para cada recurso dentro de uma pagina HTML, seja uma imagem, um estilo css, ou um javascript, que precisa ser carregado, o navegador faz uma nova requisição, não seria legal criar uma nova conexão para cada requisição ainda mais se elas acontecem em um curto espaço de tempo, então o keep-alive mantém a conexão “viva&#8221; tempo pra que esses recursos sejam carregados. É claro que o protocolo define muito mais propriedades, como pode observar no documento RFC mencionado acima, porém cada servidor deve implementar essas funcionalidades, no nosso caso vamos implementar apenas as funcionalidades na requisição de exemplo e algumas mais que mencionaremos mais adiante.

## A Resposta

A resposta segue um formato bem parecido da requisição, a primeira linha contem o protocolo, o código e mensagem de retorno como segue:

<pre>HTTP/1.1 200 OK</pre>

Esse código é esperado quando a pagina solicitada foi encontrada e seu conteúdo está enviada logo abaixo do cabeçalho (veremos a diante). Existem diversos códigos de retorno de sucesso, e de erro também, quem aqui nunca recebeu um 404 Not Found ao tentar acessar uma página que não existe?, esses e outros detalhes iremos tratar na parte de implementação. Por fim as linhas seguintes da resposta contem algumas informações pertinentes ao navegador e por fim a pagina html solicitada, veja que o conteúdo é concatenado com a resposta:

<pre>HTTP/1.1 200 OK
Date: Tue, 17 Jun 2014 01:20:13 GMT
Server: gws
Location: https://www.google.com.br/
Last-Modified: Tue, 17 Jun 2014 01:20:13 GMT
Content-Encoding: gzip
Content-Length: 234
Connection: closeContent-Type: text/html


&lt;html&gt;todo o html da página&lt;/html&gt; *</pre>

*este conteúdo pode estar compactado

Nesta resposta o servidor retorna a data da resposta (Date), qual o nome/tipo/empresa que desenvolveu/sistema operacional do servidor que gerou a resposta, a localização atual (Location) importante caso seu site use caminho relativo em hiperlinks, imagens e outros (veremos com mais detalhes na implementação) ultima vez que o arquivo foi modificado (Last-Modified), importante caso o navegador permita cache de paginas, compactacao do conteúdo (Content-Enconding), para que o navegador saiba fazer a descompactacao se necessário, tamanho em bytes do  conteúdo,o estado da conexão, que neste caso o servidor informa que a conexão foi fechado, o tipo do conteúdo(Content-Type), que é um texto contendo html e por fim, é claro, o conteúdo da resposta, ou seja, aquilo que o navegador irá exibir pra gente.

Quer testar? Então abra o navegador de sua preferência, melhor que seja o firefox =D, em seguida abra o modo de desenvolvedor (geralmente é so apertar F12), e por fim clique na aba Rede, pronto agora é so digitar um site na barra de endereço, e acompanhar as requisições pelo console, se quiser mais detalhes clique em uma requisição e peça para exibir detalhes, se estiver usando o firefox, ele aparece esses detalhes logo na lateral da lista de requisições. analise as propriedades enviadas na requisição e veja qual foi a resposta. você irá percebem que existem mais propriedades do que comentamos aqui, mas para nós neste tutorial não será necessário, se quiser pode pesquisar mais sobre eles ou ler o documento RFC que ja falamos sobre ele.

<div id="attachment_17" style="width: 310px" class="wp-caption aligncenter">
  <a href="http://euamoaweb.com.br.md-54.webhostbox.net/arquivolivre.com.br/uploads/2014/06/Screen-Shot-2014-06-17-at-12.00.06-AM.png"><img class="wp-image-17 size-medium" src="http://blog-tsg0.rhcloud.com/uploads/2014/06/Screen-Shot-2014-06-17-at-12.00.06-AM-300x165.png" alt="Requisicao" width="300" height="165" /></a>
  
  <p class="wp-caption-text">
    Requisicao
  </p>
</div>

<div id="attachment_18" style="width: 310px" class="wp-caption aligncenter">
  <a href="http://euamoaweb.com.br.md-54.webhostbox.net/arquivolivre.com.br/uploads/2014/06/Screen-Shot-2014-06-17-at-12.00.34-AM.png"><img class="wp-image-18 size-medium" src="http://blog-tsg0.rhcloud.com/uploads/2014/06/Screen-Shot-2014-06-17-at-12.00.34-AM-300x166.png" alt="Resposta" width="300" height="166" /></a>
  
  <p class="wp-caption-text">
    Resposta
  </p>
</div>

Chegamos ao fim da primeira parte do nosso tutorial, sei que teoria é chato mas se faz necessário, mas prometo que na <a href="http://tableless.com.br/criando-seu-proprio-servidor-http-do-zero-ou-quase-parte-ii/" target="_blank">Parte II</a> colocaremos as mãos a obra.

Então até a próxima.