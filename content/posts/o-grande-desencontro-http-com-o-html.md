---
title: O grande desencontro do HTTP com o HTML
author: Jean Carlo Emer
type: post
date: 2014-01-06
excerpt: Duas tecnologias criadas sob o mesmo projeto que possuem uma falha de compatibilidade. Vamos conhecer um pouco da história do HTTP e HTML, boas práticas e como manter interações coerentes entre cliente e servidor.
url: /o-grande-desencontro-http-com-o-html/
dsq_thread_id: 2095314894
categories:
  - Código
  - HTML
tags:
  - html
  - http
  - json
  - rest

---
O texto irá contar a evolução e desencontro de duas tecnologias. O importante aqui é apresentar a você uma série de conceitos e raciocínios ligados à linguagem de marcação e ao protocolo de marcação mais famosos dos nossos tempos. Vê se não banca o curioso, nada de descer até o fim do texto para conhecer o desfecho desta trama.

## Prólogo

### Hypertext Transfer Protocol (HTTP)

O HTTP é um protocolo de comunicação para distribuição de objetos de hipermídia referenciados por uma URL. Este é o principal dos protocolos da Internet e com certeza, como desenvolvedores, é o que devemos melhor conhecer. A função do protocolo é bastante simples: realizar requisições e receber respostas entre um cliente e servidor.

A transmissão de informações entre um emissor e um receptor caracteriza uma comunicação. E da mesma forma que uma comunicação interpessoal, a cordialidade é essencial. O protocolo HTTP estabelece um cabeçalho para suas requisições e respostas. O cabeçalho de uma mensagem são informações complementares que são de uso do cliente e servidor. Através das informações passadas pelo cabeçalho, que são de uso exclusivo do servidor e navegador, é possível informar em uma requisição a preferência de idiomas, as codificações e os formatos de conteúdo para uma resposta. O cabeçalho da resposta, por sua vez, contém o [código de status][1], codificação, formato do conteúdo e tempo de expiração da página.

#### Métodos de requisição

O protocolo HTTP foi criado no projeto World Wide Web e designado para operar essencialmente com documentos de hipertexto. Nesta época, havia somente o método GET para requisitar as páginas, mas isto foi antes de qualquer especificação do protocolo.

O HTTP 1.1, que constitui a especificação consolidada mais recente, possui alguns outros métodos que são informados no cabeçalho da requisição. Os principais métodos que você deve conhecer são:

  * **GET**: desde sempre, solicita um objeto para o servidor. Em tempo, objetos são qualquer entidade que o servidor conheça e que o cliente esteja interessando em manipular.
  * **PUT**: escreve um objeto no servidor de maneira a respeitar a propriedade da [idempotência][2]. Em linhas gerais, este tipo de requisição pode ser chamada mais de uma vez e o resultado no servidor será o mesmo. Geralmente estas requisições carregam consigo um identificador único para o objeto e portanto são mais usadas para alterá-lo.
  * **POST**: escreve um objeto no servidor sem respeitar a propriedade da idempotência. Requisições deste tipo, quando repetidas, podem gerar resultados diferentes no servidor. O uso comum é para a criação de objetos no servidor.
  * **DELETE**: remove um objeto no servidor.

### Representational State Transfer (REST)

Graças a ubiquidade alcançada pelos navegadores, aplicações apoiadas na internet são cada vez mais comuns. REST é um estilo de arquitetura que define como aplicações devem utilizar o protocolo HTTP e URLs para representar recursos.

O estilo estabelece que o conceito de **recurso** é tudo aquilo no servidor que pode ser nomeado, tal como documentos ou imagens. Cada recurso deve possuir um identificador único, ou seja, uma **URL**. Por exemplo, uma aplicação para gerenciar produtos pode identificar um recurso de produto através da URL `products/59`.

O cliente, através dos **métodos de requisição do HTTP**, efetua ações em um recurso. Considerando a mesma aplicação, requisições com método `GET`, `PUT` e `DELETE` para a URL `products/59` irão mostrar, alterar e excluir o produto, respectivamente. Note, uma única URL para três diferentes ações.

O último conceito relacionado a REST é o de **representação**. O cliente sempre irá transferir uma representação de um recurso. Informações passadas pelo cabeçalho da requisição ou acrescentadas ao fim da URL podem informar qual o formato da representação que se espera de um recurso. Desta forma, o mesmo recurso pode ser transferido na forma de HTML, JSON e até mesmo XML.

O Ruby on Rails, _framework_ bastante usado para desenvolver aplicações _web_, prove uma série de funcionalidades para auxiliar o uso de REST. Para compreender melhor o assunto, basta conferir [o guia de rotas][3] do Ruby on Rails, que documenta como definir URLs e ações de _controller_ com base em recursos.

A bibliografia a respeito de REST é vasta. A última dica sobre o assunto é conferir a tradução de um texto que é muito bom e engraçado: [Como eu expliquei REST para a minha esposa][4].

### Hypertext Markup Language (HTML)

O desenvolvimento do HTML foi concomitante ao do HTTP, sua função é marcar os documentos do projeto World Wide Web. Você já está careca de saber que o HTML é um conjunto de _tags_ que estruturam e garantem semântica ao documento.

## Capítulo 1: A evolução das especificações

No início, o navegador tinha como função ser a interface para uma grande biblioteca distribuída. O protocolo HTTP, antes mesmo da sua especificação, tinha apenas um método GET. Não havia a intenção de se alterar as informações armazenadas em um servidor. A primeira especificação do HTTP já era mais ambiciosa e definia uma série de [métodos de requisições][5]. Com estes métodos, já era possível deixar explícito que uma alteração seria realizada no servidor.

Criada logo após a especificação do HTTP, a [primeira especificação do HTML][6] era um pouco menos ambiciosa. Tente imaginar, a especificação não continha formulários. Mesmo assim, os métodos de requisição do HTTP não foram deixados de fora. As âncoras aceitavam um atributo `methods` para indicar quais métodos poderiam ser usados ao requisitar determinado objeto. Poucos navegadores deram suporte ao atributo, o qual nunca chamou muita a atenção e na especificação atual já está obsoleto.

Manter o HTML com o único propósito de marcar conteúdo já não era a estratégia quando definida a segunda especificação da linguagem. A especificação eleva o HTML 2.0 a um _Internet Media Type_. Isto significa que os usuários podem não apenas navegar e interagir com documentos, mas também preencher e submeter formulários.

Além de um atributo `action` com a URL de destino, os formulários aceitam um atributo `method` que suporta os valores `GET` ou `POST` como método da requisição de envio. O uso de `POST`, segundo a especificação, é restrito a operações que modifiquem a base de dados ou assinem algum serviço.

## Capítulo 2: O desencontro

No estado atual da especificação, o HTML suporta âncoras que realizam requisições com o método `GET` e formulários que são enviados com método `GET` ou `POST`. Qualquer outro recurso, tais como imagens, folhas de estilo e _scripts_, são requisitados com o método `GET`. **O HTML não possui nenhum recurso para o uso dos métodos `PUT` e `DELETE`**.

O resultado é que não existe uma maneira de utilizar uma API REST unicamente através de HTML. Em outras palavras, uma página pode apenas acessar e criar novos recursos. Não é possível excluir ou alterar recursos utilizando REST e toda a sorte dos métodos de requisição do HTTP.

As discussões a respeito desta falha de compatibilidade são antigas. Existem várias propostas de soluções. A mais notável, chamada [HTML Form HTTP Extensions][7], acrescenta um atributo `method` ao formulário que aceita a maioria dos métodos do HTTP 1.1. Desta maneira, é possível disparar uma requisição com método `DELETE` através de um formulário. A proposta, que é um rascunho não oficial e não possui suporte em nenhum navegador, inclui também artifícios para adicionar informações ao cabeçalho da requisição.

## Capítulo 3: Alternativas

Antes de falar das alternativas, é importante nos voltarmos para o JavaScript. A API `XMLHttpRequest` permite o uso de todos os métodos além de manipular outros dados do cabeçalho da requisição:

    var request = new XMLHttpRequest();
    request.open('DELETE', 'products/59');
    
    request.setRequestHeader('X-Requested-With', 'XMLHttpRequest');
    request.send();
    

É importante destacar que poder disparar requisições com diferentes métodos apenas através de JavaScript não é o bastante. Em especial, requisições deste tipo são assíncronas, não sendo sempre o que precisamos.

### Formulários

Apesar do Ruby on Rails se tratar de um framework para desenvolver aplicações web para navegadores, o estilo REST é suportado e evangelizado em toda a documentação do framework.

Enquanto as especificações não evoluem, os formulários parecem ser a melhor alternativa para disparar diferentes métodos. O Ruby on Rails tem como dependência o [Rack][8], que é uma interface para desenvolver aplicações em Ruby. O Rack permite que o formulário com método `POST` possa informar um novo método através de um campo `_method`. Isto não afeta diretamente o método da requisição, apenas faz com que o Ruby on Rails interprete a requisição de maneira diferente. O formulário a seguir seria atendido por uma rota de `DELETE` de `products/59`:

    <form method="post" action="products/59">
        <input type="hidden" name="_method" value="delete">
        <button>Deletar produto</button>
    </form>
    

Caso esteja utilizando Ruby on Rails, não é recomendado possuir códigos como este nas suas `views`. Ao invés disto, utilize [Form Helpers][9], os quais já se encarregam de escrever este e outros campos necessários para o correto funcionamento do framework.

Tratando-se de outras linguagens, diferentes frameworks _full-stack_ também endereçam esta solução. O Laravel, escrito em PHP, [também suporta um campo `hidden` de nome `_method`][10].

A flexibilidade e vantagem desta solução é poder ter as mesmas rotas e ações para manipular um recurso através de formulários HTML e requisições JavaScript. Graças ao REST, as diferentes ações podem transferir uma representação do recurso em HTML ou JSON para requisições oriundas de formulários e `XMLHttpRequest`, respectivamente.

### Âncoras

Segunda a especificação, os _links_ são conexões entre dois recursos. Em especial, as âncoras permitem que o usuário navegue através de um documento ou acesse outro recurso seguindo determinada URL. Os _links_, que incluem `<a>`, `<area>` e `<link>`, sempre requisitam recursos através do método `GET` e portanto **não devem causar efeito colateral no servidor**.

#### Removendo registros

Em áreas administrativas, é bastante comum termos registros em tabelas com uma âncora de excluir. E está errado por vários motivos: não é por navegar para uma página que registros devem ser excluídos. Lembre-se que nos tempos em que conexão banda larga era rara, aceleradores praticavam acesso a todas as âncoras para agilizar a navegação. Assim, tudo seria excluído. O mínimo a se dizer é que cada um destes botões devem estar envoltos em um formulário `POST`, até mesmo se sua aplicação não respeitar REST.

Um argumento que pode surgir contra esta prática é a mudança dos elementos no HTML, por trocarmos um único `<a>` por um formulário que tem um `<button>` não tão fácil de estilizar. Se você estiver utilizando REST, existe uma alternativa que é apoiada em JavaScript: continuar usando `<a>` que quando clicado criará e enviará um formulário. O Ruby on Rails faz exatamente isto com o auxílio do `jquery_ujs` incluso na gem [jquery-rails][11] quando encontra uma âncora com `data-method` igual a esta:

    <a href="products/59" data-method="delete" rel="nofollow">Remover</a>
    

O atributo `rel` com valor `nofollow` serve para que esta âncora não seja deliberadamente seguida. Repetindo uma recomendação, caso esteja no Rails, utilize o _helper_ `link_to` ao invés de escrever diretamente o código acima.

Um detalhe importante é que através desta abordagem, caso o comportamento do JavaScript seja impedido, o usuário terá apenas acesso a uma representação do recurso. O mesmo acontece para o caso de o usuário copiar esta URL e acessar pela barra de navegação. Nestes casos, uma requisição `GET` é disparada e não haverá exclusão do recurso. A questão aqui é que a representação do recurso, ou seja, a página que é exibida ao acessar `products/59` através de `GET`, deve conter um formulário que permita excluir o produto. Este artifício muitas vezes é deixado de lado e a exclusão dos registros fica condiciona a JavaScript.

## Nota do autor

O conceito de REST é muito interessante e espero que logo possamos utilizar nativamente no HTML. Seria genial e com certeza é necessária uma evolução da especificação neste aspecto. Cá entre nós, evoluções deste tipo são muito mais úteis que mudar a semântica de `<b>`, `<em>`, `<strong>` e afins.

Antes de mais nada, não se esqueça que **acessar um _link_ não pode causar nenhum efeito colateral na sua aplicação**. Use e abuse de formulários. Mais ainda, faça que o _back-end_ da sua aplicação utilize REST. Escolha um bom _framework_ e vá em frente.

Desculpe pelo texto ter ficado extenso e talvez um tanto pesado. Espero que tenha gostado e que aproveite estas dicas para escrever aplicações melhores.

 [1]: http://httpstatus.es
 [2]: http://pt.wikipedia.org/wiki/Idempot%C3%AAncia
 [3]: http://guides.rubyonrails.org/routing.html#crud-verbs-and-actions
 [4]: http://distopico.wordpress.com/traducao-de-how-i-explained-rest-to-my-wife
 [5]: http://www.w3.org/Protocols/HTTP/Methods.html
 [6]: http://www.w3.org/MarkUp/draft-ietf-iiir-html-01.txt
 [7]: http://cameronjones.github.io/form-http-extensions/index.html#form-method-attribute
 [8]: http://rack.github.io
 [9]: http://guides.rubyonrails.org/form_helpers.html
 [10]: http://laravel.com/docs/html#opening-a-form
 [11]: https://github.com/rails/jquery-rails