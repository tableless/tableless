---
title: HTTP/2 – Atualização do protocolo base da internet
author: Diego Eis
type: post
date: 2015-02-18
excerpt: O protocolo HTTP vai receber oficialmente uma grande atualização em breve. Saiba o que mudou.
url: /http2-atualizacao-do-protocolo-base-da-internet/
categories:
  - Artigos
  - Browsers
  - Técnicas e Práticas
  - Tecnologia e Tendências
tags:
  - html
  - http
  - internet

---
HTTP é o protocolo de comunicação base usado para a internet funcionar. O nome é Hypertext Transfer Protocol. Olha só a palavra Hypertext aparecendo de novo. Onde mais você encontra ela? Isso! Exato! Na sigla HTML: HyperText Markup Language. O HTTP é o protocolo que troca ou faz a transferência de hipertextos.

Eu não vou explicar aqui o que é um [Hipertexto][1] porque eu sei que você já sabe. Mas a grande novidade é que durante os últimos 16 anos nós usamos uma mesma versão desse protocolo e agora a galera do [IETF HTTP Working Group][2] soltou a atualização, chamada de HTTP/2!

O HTTP/2 não é uma reescrita completa do protocolo, tanto que os métodos e códigos de status continuam os mesmos. O foco foi em performance. Especificamente para diminuir a latência percebida pelo usuário final, redes e a melhora do uso de recursos do servidor. Eles dizem que o objetivo principal é usar uma única conexão entre o browser e o website!

O ponto principal do HTTP/1.1 era que ele permitia que o seu site fosse comprimido pelos servidores e depois descomprimidos pelos computadores. Isso resolve uma série de problemas de tamanho em uma época onde conexão era muito restrita. A versão 1.1 do protocolo permitiu que a internet continuasse crescendo, resolvendo o uso de dados em grandes quantidades pelos websites.

A versão 2 tem quase o mesmo propósito. O principal problema resolvido agora é que o browser faz várias requisições de arquivos para o servidor montar seu websitio. Todo mundo aqui usa CSS, JS, imagens, vídeos, fonts e diversas outras coisinhas para fazer websites bonitos e agradáveis. Isso carrega demais as páginas e significa mais requisições entre browser e servidor.

O ponto é que o browser só consegue fazer uma requisição por vez, por servidor. Essas requisições demoram para serem feitas, principalmente quando há CSS ou JS bloqueantes. Por isso que muita gente, principalmente grandes websites, baixam imagens, JS, CSS etc de diferentes servidores. E aqui se forma o problema. Conforme isso vai acontecendo, a carga na rede, como um todo, aumenta bastante e vários outros serviços começam a engasgar. 

O que muda então é o seguinte: enquanto hoje o browser faz uma requisição para ter uma resposta, ele vai fazer uma requisição e conseguirá ter várias respostas de uma vez. Isso quer dizer que ele pode falar com o servidor uma vez e pedir tudo o que tem direito. Isso é muito importante e um grande avanço.

Isso não quer dizer que você vai desistir da performance do seu site, pelo contrário, você vai ter tempo para melhorar a performance de outros pontos, por exemplo, o processamento do computador ao montar sua página, uso de memória etc.

O [Mark Nottingham][3], chairman do IETF, [fez um post em seu blog no dia 18 de Fevereiro][4] explicando o lançamento e dando mais detalhes.

Uma curiosidade interessante é que eles usaram o [GitHub para definir as especificações, testes etc][5]. [Veja a especificação aqui][6].

Se tiver perguntas, o pessoal do IETF [criou um FAQ bastante extenso][7] explicando uma série de perguntar pertinentes.

 [1]: http://pt.wikipedia.org/wiki/Hipertexto
 [2]: https://httpwg.github.io/
 [3]: https://www.mnot.net/blog
 [4]: https://www.mnot.net/blog/2015/02/18/http2
 [5]: https://github.com/http2
 [6]: http://http2.github.io/
 [7]: http://http2.github.io/faq/