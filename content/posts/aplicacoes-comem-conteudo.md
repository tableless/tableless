---
title: Aplicações comem conteúdo. Só os bem tratados.
author: Diego Eis
type: post
date: 2006-05-22
url: /aplicacoes-comem-conteudo/
tweetbackscheck:
  - 1356447582
shorturls:
  - 'a:3:{s:9:"permalink";s:49:"http://tableless.com.br/aplicacoes-comem-conteudo";s:7:"tinyurl";s:26:"http://tinyurl.com/42t38t2";s:4:"isgd";s:19:"http://is.gd/H1zz4z";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 503035371
categories:
  - Artigos
  - Geral
  - Tecnologia e Tendências
tags:
  - acessibilidade
  - Técnicas e Práticas

---
Uma das perguntas mais badaladas que costumo ouvir de clientes e até mesmo pessoas que acabaram de conhecer os Padrões é: Como tal site fica sempre em primeiro no Google?
  
E a segunda pergunta que sempre ouço, vem depois da resposta da primeira pergunta: Só?

Um dos fatores (não o único) para que o Google (ou qualquer outra aplicação &#8220;um pouco inteligente&#8221;) defina se algum site aparecerá no topo de suas buscas, é a maneira com que seu conteúdo é tratado.

Veja, é muito simples o raciocínio: O que aplicações como o Google procuram quando visitam o seu site? A resposta parece clara, não? Conteúdo. Ele procura conteúdo. O que mais ele procuraria?
  
Logo, ele vai ao seu site, indexa todo o conteúdo e o guarda para quando alguém fizer uma pesquisa, este conteúdo possa ser mostrado nos resultados.

Dependendo de como a página foi construída, alguns valores importantes podem ter sido perdidos. Partes do conteúdo são mais importantes que outras e seria interessante que as aplicações (como o Google) soubessem disso para que quando o usuário fizesse uma pesquisa, ele pudesse receber resultados mais específicos e exatos. Normalmente quando usamos a maneira antiga de desenvolvimento, nós não aplicamos nenhuma técnica para definir qual conteúdo é mais importante que outro. Logo, o Google (ou outra aplicação) indexa este conteúdo sem nenhum parâmetro de qual parte do texto é ou não importante.

Quando você faz um site com sua estrutura semanticamente exata, você gera significado que pode ser usado em muitas aplicações. Quando você marca um título com sua tag correta (h1, h2, h3 &#8230;), o Google sabe que aquilo é um título e então vai dar prioridade &#8220;x&#8221; a ele. Um leitor de tela para cegos, também sabe que aquilo é um título e então mudará a entonação ou usará qualquer outro método para indicar ao ouvinte que aquela pequena frase é algo importante. Uma aplicação que surgirá daqui a algum tempo, também poderá saber que aquilo é um título.

Portanto, se você faz um site que não usa tabelas para estruturas, mas faz algo parecido:

`<div id="titulo1">Título</div>`

Você não entendeu perfeitamente a alma do negócio.

Já passou por aqui:

  * [Lições sobre Semântica #2][1]
  * [Lições sobre Semântica #1][2]
  * [Diferenças sutis na semântica][3]
  * [A Web Semântica][4]
  * [Podcast #18 &#8211; Opera 9, Wasabi, Songbird e Semântica][5]
  * [Semântica é que manda][6]
  * [Subjetividade na Semântica][7]

 [1]: http://tableless.com.br/licoes_sobre_semantica_2
 [2]: http://tableless.com.br/licoes_sobre_semantica_1
 [3]: http://tableless.com.br/diferencas-sutis-na-semantica
 [4]: http://tableless.com.br/a-web-semantica/
 [5]: http://tableless.com.br/podcast-18-opera-9-wasabi-songbird-e-semantica
 [6]: http://tableless.com.br/a-semantica-e-que-manda
 [7]: http://tableless.com.br/subjetividade-na-semantica