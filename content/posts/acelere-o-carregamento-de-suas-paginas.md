---
title: Acelere o carregamento de suas páginas
author: Jean Carlo Emer
type: post
date: 2014-03-25
excerpt: Também conhecido como o Santo Graal das páginas de internet, encontrar o carregamento perfeito não é tarefa fácil.
url: /acelere-o-carregamento-de-suas-paginas/
dsq_thread_id: 2503344883
categories:
  - JavaScript
  - Técnicas e Práticas

---
Muita coisa já foi escrita sobre este assunto, originalmente em português temos o renomado guia [Como perder peso no browser][1] cujos autores são feras e a série intitulada [Performance front-end][2] aqui mesmo no Tableless. As iniciativas gringas são muitas com destaque ao [YSlow][3] e às [práticas do Yahoo! para melhorar performance][4].

Neste ponto, se ainda continua nesta leitura, você deve estar se perguntando se existe alguma técnica que não é coberta por alguma destas referências. Há sim. Porém já deixo o aviso, o que veremos a seguir não substitui outras técnicas voltadas a ganho de performance, assim como muitas outras, é apenas uma técnica complementar.

## Carregamento especulativo

Uma tentativa de acelerar o carregamento já foi vendida no Brasil como uma funcionalidade incrível creditada a discadores de internet. Sim, discadores. Os pacotes de _software_ incluíam um navegador especial. A função deste era identificar os _hiperlinks_ já no carregamento da página e requisitar por eles sem que o usuário tomasse conhecimento. Assim, quando o usuário seguisse algum _hiperlink_, o seu conteúdo já estava disponível.

O resultado desta técnica é um tanto desastroso por duas perspectivas. Muito do conteúdo requisitado nunca era utilizado desperdiçando banda de internet e processamento do cliente e servidor. E em segundo, porque já naquele tempo as páginas [faziam mal uso de _hiperlinks_][5] para operar manipulação e exclusão de recursos.

Esta técnica já não é mais utilizada, provando que requisitar mais do que se precisa não é uma solução inteligente.

## Carregando apenas conteúdo

Nas aplicações tradicionais, o carregamento de JavaScript e CSS, nossos _assets_, despendem **até metade do tempo** total de carregamento da página. Se considerarmos que, para tirar proveito do _cache_, estes _assets_ serão os mesmos em diferentes páginas. O próximo passo é reaproveitar uma única página durante a navegação.

A técnica consiste em alterar o comportamento padrão dos _hyperlinks_ fazendo com que o endereço indicado no atributo `href` seja requisitado assincronamente. O resultado da requisição é analisado e apenas o conteúdo de interesse é substituído. O principal ganho de performance se deve ao fato das folhas de estilo e _scripts_ não serem requisitados durante a navegação.

### Bibliotecas

#### jQuery PJAX

Criada por um dos fundadores do GitHub, a biblioteca [PJAX][6] implementa a técnica utilizando jQuery. Para testar seu funcionamento, basta navegar por um repositório no próprio GitHub.

A biblioteca permite indicar quais _hyperlinks_ terão seu comportamento modificado e qual o _container_ que deve ser utilizado para depositar o conteúdo retornado pela requisição. O conteúdo retornado pela requisição deve ser tratado no _back-end_ para retornar estritamente o que precisa ser depositado no _container_. Isto é possível graças a um cabeçalho adicionado a requisição que garante sua identificação no _back-end_. Mesmo que a intenção seja substituir o `<body>`, é aconselhado remover o `<head>` mantendo apenas a _tag_ `<title>`. Isto garante um ganho de performance ainda mais significativo.

#### Turbolinks

O Turbolinks é um misto de biblioteca JavaScript e código _back-end_ que implementa a  técnica de carregamento de conteúdo no Ruby on Rails sem depender de jQuery. A _gem_, como são chamados os pacotes de Ruby, é padrão a partir da versão 4.0 do _framework_.

A biblioteca foi desenvolvida pela 37Signals para ser utilizada na versão _mobile_ do seu principal produto, o Campfire. O que atesta que a técnica é praticável em dispositivos móveis modernos.

Diferente da biblioteca PJAX, o Turbolinks não permite que seja configurado o _container_ de destino do conteúdo, todo o conteúdo do `<body>` é substituído. Por causa disto, a aplicação não precisa sofrer nenhuma modificação no seu _back-end_ para utilizar a _gem_: o conteúdo esperado é o mesmo de uma requisição tradicional de página. Como veremos a seguir, os desafios para se utilizar o Turbolinks e mesmo a PJAX, residem no _front-end_ da aplicação

### Como a técnica é possível

Requisições assíncronas já são usadas frequentemente e enfrentam praticamente nenhum problema de suporte. Nos primórdios, _iframes_ e API de `ActiveXObject` eram usados para possibilitar este tipo de requisição. Atualmente, grande parte dos navegadores suportam a API de `XMLHttpRequest` apesar da [especificação estar em rascunho desde 2006][7].

Note que a técnica é fundamentalmente calcada na mudança da barra de endereço sem que resulte no carregamento de uma nova página. A barra de endereço está intimamente ligada com a seção de histórico onde os navegadores armazenam as páginas acessadas. Antigamente, este histórico podia apenas ser retrocedido e avançado através da interface JavaScript `window.history`.

Uma nova especificação, associada com o [HTML5][8], permite manipular o histórico e consequentemente a barra de endereço. Como se trata de uma funcionalidade nova, seu [suporte é restrito a navegadores modernos][9]. As bibliotecas PJAX e Turbolinks fazem uma **detecção da funcionalidade** e operam no modelo de navegação tradicional caso esta não esteja disponível.

A nova API de _history_ permite adicionar novas entradas com a função `window.history.pushState`. A função recebe os parâmetros `data` e `title`, utilizados para referenciar esta entrada no histórico. O último parâmetro `url` se trata do endereço a ser mostrado na barra de endereço. A API também define um evento `popstate` que permite identificar quando o usuário navega por entradas adicionadas ao histórico. Vejamos o funcionamento com um exemplo:

    window.addEventListener('popstate', function(event) {
      console.log(event.state);
    }, false
    
    window.history.pushState({ tableless: 'sample' }, 'Fake Post', 'http://tableless.com.br/fake-post');
    

Como já observamos, a execução da função `pushState` irá adicionar uma entrada no histórico de navegação e alterar a barra de endereço para _http://tableless.com.br/fake-post_. Na ocasião de o usuário retroceder o histórico de navegação, a barra de endereço será alterada para seu endereço inicial e o evento `popstate` será disparado. O valor da propriedade `state` do evento é aquele definido pelo parâmetro `data` na chamada de `pushState`. O _console_ será preenchido com `Object {tableless: "sample"}`.

Dependendo da implementação da API no navegador, o evento `popstate` será disparado logo no carregamento da página. Neste caso, o _console_ será preenchido com `undefined`.

### Dicas importantes

Fazendo uso das bibliotecas, seu projeto ser tornará uma aplicação que carrega suas páginas assincronamente. Um pré requisito para o que discutiremos a seguir é compreender o comportamento dos _scripts_. Sempre que um _script_ não é disponibilizado no documento, a única maneira de executá-lo é através da API do DOM. Nestes casos, o seu carregamento será assíncrono e sua execução é condicionada ao término do _download_. Note, **não há garantia de ordem de execução quando temos mais de um script**.

#### jQuery PJAX

A biblioteca analisa o conteúdo retornado pela requisição a procura de _scripts_. Caso o arquivo indicado pelo `src` ainda não faça parte da aplicação, o _script_ é adicionado ao `<head>`. **Apenas estes serão executados sem garantia de ordem**.

O ideal é incluir os _scripts_ no `<head>` e assistir aos eventos `pjax:start` e `pjax:end`, disparados imediatamente antes e depois de alterar o conteúdo,  para atribuir e remover comportamentos. Entenda que a biblioteca mantém em _cache_ todos os conteúdos requisitados para agilizar a navegação pelo histórico. Isto matém ativos os comportamentos atribuídos. O impacto é ainda maior se o conteúdo assiste a eventos do `<body>` ou outros objetos globais. A remoção dos comportamentos passa a ser de extrema importância para evitar _memory leaks_.

#### Turbolinks

A biblioteca **executa todos os _scripts_ contidos no `<body>`** sem garantia de ordem. Um dos problemas mais comuns se dá quando a biblioteca é ativada em aplicações que seguem a boa prática de inserir os _scripts_ antes do `</body>`. Os _scripts_ que tenham alguma dependência, _plugins_ jQuery, por exemplo, passam a depender da sorte para funcionar. A solução é mover os _scripts_ para o `<head>` ou marcar aqueles que não devem ser executados com o atributo `data-turbolinks-eval` igual a `false`.

Uma prática comum quando posicionamos _scripts_ no `<head>` é acessar o DOM utilizando funções como `jQuery.ready `para garantir que já esteja acessível. O maior impacto no uso do Turbolinks é que eventos de _load_ não serão mais disparados durante a navegação, `jQuery.ready `não irá funcionar. A biblioteca dispara os eventos `page:receive` e `page:load` antes e depois de alterar o conteúdo. Os comportamentos precisam ser atribuídos com base nestes eventos.

A biblioteca ainda permite que os _assets_ que contenham o atributo `data-turbolinks-track` sejam analisados a cada requisição. Caso uma mudanças seja identificada, a página é completamente recarregada.

Assim como a PJAX, o Turbolinks também implementa uma estratégia de _cache_. O conteúdo, quando trazido imediatamente do _cache_, dispara o evento `page:restore`. Em seguida, para atualizar o conteúdo, a requisição é refeita. Todas as mudanças de conteúdo, que sempre serão duas nestes casos, são seguidas dos eventos `page:change` e `page:update`.

Gerenciar todos estes eventos pode ser complicado, ainda mais se já estiver acostumado a utilizar `jQuery.ready`. A solução é adotar o _plugin_ [jQuery Turbolinks][10]. Mas não se esqueça, a mesma dica de remoção dos comportamentos mencionada na seção a respeito da PJAX são válidas aqui para evitar _memory leaks_.

Um último desafio é fazer com que outras bibliotecas JavaScript sejam compatíveis com o Turbolinks. Serviços comuns como Google Analytics e _widgets_ do Facebook e Twitter podem não funcionar adequadamente. Um projeto muito interessante chamado [Turbolinks Compatibility][11] apresenta estratégias para tornar compatível uma série de bibliotecas.

### Futuro das bibliotecas

Formulários ainda são um problema, o Turbolinks não endereça este caso de uso e o PJAX apenas o faz de maneira experimental. O agravante é maior quando o formulário inclui envio de arquivos.

A especificação em rascunho do XMLHttpRequest Level 2 permite o envio de arquivos com informação de progresso através de requisições assíncronas. Esta é uma funcionalidade muito interessante para aplicações que fazem _upload_ de muitos arquivos em série, por exemplo. O [suporte da API][12] já é muito bom em navegadores modernos.

## Conclusão

A biblioteca PJAX é uma alternativa muito boa por permitir atualizar seções específicas da página. Ao mesmo tempo, para uma implementação inicial, a biblioteca permite também o carregamento total do conteúdo da página.

Turbolinks é uma ótima alternativa para implementar a técnica de carregamento de conteúdo em aplicações Ruby on Rails. Se você quiser ir um pouco além, podendo inclusive enviar formulários, a biblioteca [Wiselinks][13] pode ser uma ótima tentativa.

### Evoluindo ainda mais a sua aplicação

Talvez não pareça tão natural, mas o próximo passo é utilizar uma biblioteca como o Backbone.js. Através dela é possível gerenciar cada um dos _containers_ que podem sofrer atualização de conteúdo através do construtor `Backbone.View`.

Os endereços serão gerenciados pelo `Backbone.Router` que inclusive utiliza `window.history.pushState`. Note a semelhança, todas as páginas que o roteador conhece devem ser implementadas no _back-end_ para quando o usuário acessar o endereço diretamente. O Backbone.js ainda disponibiliza os construtores de `Model` e `Collection` para gerenciar os dados da sua aplicação.

### Por fim

Os ganhos em rapidez de carregamento podem ser bastante significativos, mas a aplicação precisa ser repensada e adequada. É preciso testar constantemente a aplicação em busca de _memory leaks_.  Apenas adicionar uma das bibliotecas de carregamento de conteúdo assíncrono e esperar que tudo funcione não é uma alternativa. Mas não deixe de tentar, o usuário agradece.

 [1]: http://browserdiet.com/pt
 [2]: http://tableless.com.br/performance-frontend-parte1
 [3]: http://developer.yahoo.com/yslow
 [4]: http://developer.yahoo.com/performance/rules.html
 [5]: http://tableless.com.br/o-grande-desencontro-http-com-o-html
 [6]: https://github.com/defunkt/jquery-pjax
 [7]: http://www.w3.org/TR/XMLHttpRequest
 [8]: http://www.w3.org/TR/2011/WD-html5-20110113/history.html
 [9]: http://caniuse.com/#feat=history
 [10]: https://github.com/kossnocorp/jquery.turbolinks
 [11]: http://reed.github.io/turbolinks-compatibility
 [12]: http://caniuse.com/xhr2
 [13]: https://github.com/igor-alexandrov/wiselinks