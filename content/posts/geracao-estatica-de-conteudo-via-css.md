---
title: Geração de conteúdo estático via CSS
authors: Diego Eis
type: post
date: 2013-12-02
excerpt: Entenda como funciona a geração de conteúdo automática via CSS usando a propriedade content.
url: /geracao-estatica-de-conteudo-via-css/
dsq_thread_id: 2016960956
categories:
  - CSS
  - CSS3
tags:
  - content
  - CSS
  - CSS3

---
A Propriedade `content` cria um conteúdo estático utilizando os pseudo-elementos `::after` e `::before`.

Só para esclarecer: o W3C determinou que pseudo-elementos usem sempre **::** em vez de apenas dois pontos **:** que é para diferenciar das pseudo-classes. Por isso não fique intrigado caso os exemplos usarem **::**.

### Relembrando

No CSS existe a possibilidade de você inserir um elemento de mentira (pseudo-elemento) em objetos no HTML. Estes elementos pode te auxiliar em diversos momentos do desenvolvimento, prevenindo a criação de elementos HTML vazios para produzir algum detalhe do layout que possa se misturar com o conteúdo real.

Quem nunca teve que criar um span vazio no começo ou no final de um elemento para produzir uma seta, um background decorativo ou qualquer outro detalhe? Usar os pseudo-elementos funciona como um span vazio, só que melhor, por que não é gerado lixo no HTML.

Abaixo você vê alguns exemplos de como podemos melhorar a utilização dessa vantagem.

### Valores da propriedade

A propriedade `content` pode ter os seguintes valores:

**none, normal**
  
O conteúdo não vai ser gerado.

**<string>**
  
Uma string de texto normal.

**url()**
  
Aqui ela te permite inserir imagens de fontes externas.

**counter()**
  
Aqui inserimos contadores.

**attr(attribute)**
  
Aqui permitimos pegar o valor de um determinado atributo do elemento.

**open-quote, close-quote, no-open-quote, no-close-quote**
  
Gera automaticamente marcações de aspas.

Lembrando que a propriedade **content** só pode ser usada nos pseudo-elementos `::after` ou `::before`. 

### String

Vamos gerar um texto simples no início ou no fim do elemento.<pre class="lang-html&quot> <h1>T&iacute;tulo</h1> </pre> 

Até aqui sem segredo, fizemos um título em HTML. YEAH!
  
Imagine agora que você queira inserir neste título algum conteúdo no início ou no final dele. Imagine que você queira inserir no começo de todos os títulos, algum conteúdo&#8230; Por exemplo, todos os títulos devem começar com a palavra &#8220;Seção: &#8220;. Em vez de colocar direto no HTML, podemos colocar via CSS, assim:



Claro que se esse fosse um caso real, muito provavelmente eu colocaria a palavra direto no HTML. Mas vai que você precise usar este texto em vários lugares, e em algum destes lugares é necessário incluir um prefixo nos títulos? Esta é A solução para este problema (e outros). 

Mas suponha que não vai ser usado em tantos lugares assim e você precisa inserir um traço, por exemplo, no início dos títulos. 

<pre class="lang-css">h1::before {
	content: "- ";
}
</pre>

Esse traço não seria muito interessante se fosse colocado direto no HTML. Os leitores de tela o leriam, os sistemas de busca indexariam o título com o traço e etc&#8230; Ele não é um conteúdo que agrega informação, é puramente para organizar visualmente os títulos.

### url()

Agora, imagine que você queira inserir uma imagem, como uma seta, nos ítens de uma lista, por exemplo.



### counter()

Este é um dos meus prediletos. Você pode inserir contadores automáticos nos elementos. Imagine que você queira colocar no final de cada título o número do título. Como abaixo:



As propriedades usadas ali são as `counter-increment` e a `counter()`.

Elas funcionam assim: coloquei a propriedade **counter-increment** com o valor **numero-do-titulo**. Esse valor é como se fosse uma variável em todos os elementos `h1`. Toda vez que o browser renderizar um H1, ele pegará essa variável (**numero-do-titulo**) que eu defini e incrementará o valor dela.

No pseudo-elemento `:after` de cada título, eu exibi o valor de contador daquela variável com o **counter(numero-do-titulo)**.
  
Muito simples, hein?

Dá para fazer um post inteiro com essa propriedade, mostrando suas variações e propriedades que funcionam conjuntamente com ela. 

### attr(attribute)

Usando o valor `attr(attribute)` eu consigo exibir o valor de algum atributo do elemento nos pseudo-elementos ::before e ::after. Muito simples também. Suponha que você queira mostrar ao lado de cada link o endereço do próprio link. O resultado é este:



### Formatando com CSS

O mais legal é que você pode formatar com CSS os elementos ::after e ::before como se fossem elementos do HTML, usando as propriedades normais que já usamos diariamente. Veja o exemplo acima com os endereços dos links formatados: