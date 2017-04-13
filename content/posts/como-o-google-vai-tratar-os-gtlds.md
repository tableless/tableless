---
title: Como o Google vai tratar os gTLDs?
author: Rodrigo Fávaro
type: post
date: 2015-08-11
excerpt: Esclarecimentos sobre as novas opções de domínios e suas relações com a busca.
url: /como-o-google-vai-tratar-os-gtlds/
categories:
  - Semântica
  - SEO
tags:
  - google
  - gtld
  - SEO

---
O Google lançou no Webmaster Central Blog uma sessão de perguntas e respostas sobre como será feita a manipulação dos <a href="https://en.wikipedia.org/wiki/Generic_top-level_domain" target="_blank">gTLDs</a> (_generic top level domains_), em português, domínios de alto nível. Se ainda não entendeu o que são domínios de alto nível, são aquelas novas extensões que vão facilitar a vida de quem tem um segmento mas nunca encontrou um domínio legal em .com ou .com.br, como por exemplo, .CASA, .CAFE, .BAR, .GURU e assim por diante. Neste <a href="https://en.wikipedia.org/wiki/List_of_Internet_top-level_domains#ICANN-era_generic_top-level_domains" target="_blank">link</a> você encontra a lista completa dos gTLDs.

<!--more-->

<img class="alignnone wp-image-50314 size-full" src="http://tableless.com.br/uploads/2015/07/gtld.jpg" alt="Exemplos de gTLD" width="940" height="492" />

Como até pouco tempo atrás o domínio em si tinha uma boa relevância nos resultados de busca, é de se pensar que um domínio .CAFE, por exemplo, exerceria maior influência no resultado quando alguém buscasse por alguma cafeteria que tivesse como seu site principal um domínio terminado em .CAFE. Mas será que isso realmente vai acontecer? Vamos então ver as perguntas mais frequentes em relação a este tema.

**Como que os novos gTLDs vão afetar a busca? O Google mudará o algoritmo de busca para favorecer esses domínios? Quão importantes eles serão nos resultados de busca?**

Em geral, os sistemas do Google tratam os novos gTLDs assim com os outros gTLDs (como .com e .org). Ter uma palavra-chave no domínio, seja com um novo ou antigo TLD não vai ter nenhuma vantagem ou desvantagem na busca.

**E sobre os nome de domínios internacionalizados (<a href="https://en.wikipedia.org/wiki/Internationalized_domain_name" target="_blank">IDN</a>), assim como .みんな? O Googlebot poderá rastreá-los e indexá-los de modo que possam ser utilizados nas buscas?**

Sim. Você poderá utilizar estes e qualquer outro TLD (pode verificar digitando no Google [site:みんな]). O Google trata a versão Punycode de um nome de _host_ como sendo equivalente à versão não codificada. Sendo assim, você não precisa redirecionar ou canonizar eles separadamente. Para o resto das URLs, lembre-se de utilizar o UTF-8 para o _path_ (caminho) e _query strings_ quando utilizar caracteres não-ASCII.

**Um TLD .BRAND terá qualquer peso a mais ou a menos em relação a um .COM?**

Não. Os TDLs serão tratados da mesma forma como qualquer outro gTLDs. Eles vão exigir as mesmas configurações de geolocalização, dentre outras mais, e eles não terão peso ou influência maiores na forma como o Google irá rastreá-los, indexar ou classificar as URLs.

**Como são manipulados os TLDs de cidade ou região (ex. .LONDON, .RIO)?**

Mesmo que esses domínios tenham especificado sua região geográfica, o Google irá tratá-los como gTLDs. Isso vai de acordo com a forma de manipulação de TDL regionais do Google, como .EU, e .ASIA, por exemplo. Para mais informações, o Google oferece detalhes sobre locais de <a href="https://support.google.com/webmasters/answer/182192" target="_blank">multi-regiões e multilinguagens</a>, além de informações sobre a <a href="https://support.google.com/webmasters/answer/62399" target="_blank">Segmentação Geográfica por País</a>.

**E sobre <a href="http://en.wikipedia.org/wiki/Country_code_top-level_domain" target="_blank">ccTLDs</a> (_country code top-level domains_): o Google vai favorecer ccTLDs (como .UK, .AE, etc.) como um domínio local para pessoas realizando buscas nestes países?**

Por padrão, a maioria dos ccTLDs (com <a href="https://support.google.com/webmasters/answer/1347922" target="_blank">exceções</a>) tem resultados no Google utilizando estes ccTLDs para &#8220;geotarget&#8221;, ou seja, ele diz que o site é provavelmente mais relevante no país apropriado. Ainda confuso? Veja o centro de ajuda para obter mais informações sobre <a href="https://support.google.com/webmasters/answer/182192" target="_blank">locais de multi-regiões e multilinguagens</a>.

**O Google vai apoiar os meus esforços de SEO para mover meu domínio de .com ou .com.br, por exemplo, para um novo TLD? Como posso mover meu site sem perder qualquer ranking ou histórico de busca?**

O Google possui uma <a href="https://support.google.com/webmasters/answer/6033049" target="_blank">vasta documentação</a> sobre mover sites em seu centro de ajuda. O Google trata esses casos da mesma forma que qualquer outra alteração de domínio, como por exemplo, mudar &#8220;minhaempresa.com&#8221; para &#8220;empresa.com&#8221;. Desta forma, mudanças de domínio podem levar algum tempo para serem processadas para a busca, por isso é importante escolher um domínio que vá atender suas necessidades a longo prazo.

* * *

Quando o assunto é domínio, geralmente poucos dão a importância devida, além de não tratar questões relacionadas a alteração. Futuramente escreverei sobre a melhor forma de fazer isso, seja mudando um site e mantendo o domínio, ou mudando o site e também o domínio, e como isso pode impactar nos resultados de busca para quem possui muitas páginas indexadas.

Sugiro olhar os preços do site  <a href="http://www.whois.com/" target="_blank">Whois.com</a> para registar seus gTLDs. Atualmente há uma promoção para domínios .SITE por apenas US$ 5,88.