---
title: "GraphQL: a nova era das APIs Web"
authors: Cleber Campomori
type: post
publishdate: 2018-03-19
date: 2018-03-15
excerpt: "Uma nova categoria de ferramentas tem ganhado mercado quando falamos sobre a construção de APIs Web: estamos falando do GraphQL."
categories:
  - javascript
tags:
  - graphql
  - nodejs
image: https://i.imgur.com/2JQG3Df.png
---

Nós do [TreinaWeb](https://www.treinaweb.com.br/?utm_source=tableless&utm_medium=artigo_graphql_top&utm_campaign=parceiro) temos visto ultimamente em nossos cursos e conversas com os alunos que muitas dúvidas vêm aparecendo com relação ao **GraphQL**. Dúvidas como "mas, o que exatamente vem a ser o **GraphQL**?" ou "qual o motivo pelo qual ele vem ficando tão famoso?", entre várias outros questionamentos.

Para tentar ajudar a esclarecer esta nova tendência, vamos discutir estes e mais alguns pontos neste artigo. :)

## Afinal, o que é o GraphQL?

Será que estamos falando de mais um framework JavaScript?

Calma! Não estamos falando de uma nova biblioteca ou framework JavaScript, embora muitas pessoas façam essa associação. O GraphQL é na verdade uma **linguagem de consulta** criada pelo Facebook. Você poderia, a grosso modo, colocá-la ao lado do SQL. Só que, enquanto o SQL é utilizado para consulta e manipulação de bancos de dados relacionais, o GraphQL é utilizado para **consulta e manipulação de APIs Web**. Isso quer dizer que você, assim como pode utilizar o SQL em conjunto com qualquer outra linguagem (como PHP, C\#, Java e outras), você também pode utilizar o GraphQL em conjunto com qualquer outra linguagem para consumir uma API.

Além da linguagem em si, também costumamos nos referir ao back-end que fornece informações no formato do GraphQL como "GraphQL" também.

O GraphQL é muito relacionado ao JavaScript porque sua implementação mais comum é justamente utilizando ferramentas JavaScript (principalmente Node.js). Porém, mais uma vez: você pode utilizar o GraphQL com qualquer linguagem. Já existem bibliotecas e frameworks para implementação do GraphQL para a grande maioria das linguagens, quer seja essa implementação do lado do servidor (quem vai fornecer os dados no formato do GraphQL) como do lado do cliente (quem vai enviar as consultas e consumir os dados no formato do GraphQL).

## Os princípios básicos do GraphQL

![](https://i.imgur.com/yGKgR2E.png)

O GraphQL, de modo geral, possui três estruturas principais: as *queries*, as *mutations* e as *subscriptions*.

Antes de discutirmos sobre cada uma destas estruturas, vamos imaginar os recursos abaixo, que são expostos por uma API GraphQL hipotética.

| Cachorro     | Pessoa             |
|--------------|--------------------|
| Id: Int      | Id: Int            |
| Nome: String | Nome: String       |
| Raça: String | Idade: Int         |
| Dono: Pessoa | Cachorro: Cachorro |

Para expormos estas estruturas através de uma API GraphQL, precisamos as representar através de *types* (nesse caso específico, teríamos *object types*). Os *types*, na verdade, servem para representar recursos em geral em uma API GraphQL.

Se fôssemos definir os *types* para os recursos acima, poderíamos defini-los da seguinte maneira:

```
type Pessoa {
  id: ID
  nome: String!
  idade: Integer
  cachorros: \[Cachorro\]
}

type Cachorro {
  id: ID
  nome: String!
  raca: String
  dono: Pessoa!
}
```

Veja como é interessante a maneira como representamos as relações entre nossos recursos: como uma pessoa pode ter mais de um cachorro, veja que informamos que o atributo "cachorros" é um conjunto do *type* Cachorro, já que o colocamos entre colchetes. O mesmo não acontece no atributo "dono" do *type* Cachorro, já que um cachorro só pode pertencer a um único dono por vez.

As exclamações na frente dos atributos de nossos *types* indicam que aqueles atributos em questão são obrigatórios e, por decorrência, não podem possuir valores nulos. Veja que não colocamos a exclamação na frente do atributo "cachorros" do *type* Pessoa: não fizemos isso porque nem toda pessoa possui um ou mais cachorros. Mas, colocamos a exclamação para o atributo *dono* do type *Pessoa*, pois todo cachorro deve possuir um dono.

Por fim, veja que os ids estão definidos com o tipo ID do GraphQL. Com isso, nós informamos que aquele atributo é um identificador único para cada um dos recursos que são expostos pela API. Agora, não entenda que algo que seja definido como um ID seja necessariamente um número. Pode ser um GUID, por exemplo. O tipo aqui não influencia. O que é importante é que realmente se trate de um identificador único.

Com isso, por hora, temos um *schema* com a definição dos *types* Pessoa e Cachorro, *types* estes que possuem *fields* -- o equivalente aos atributos. Um *schema* define a estrutura, entre outras coisas, dos *object types*. Nossos *types* Pessoa e Cachorro são *object types*.

As *queries* são utilizadas quando desejamos recuperar recursos do servidor GraphQL. Como o próprio nome entrega, se trata de uma operação de consulta. Além disso, as *queries* são como *types* especiais para o GraphQL, já que elas definem operações.

Por exemplo: se quiséssemos que nossa API GraphQL expusesse uma consulta dos donos e seus respectivos cachorros através do id do dono, teríamos algo similar ao trecho de *schema* abaixo:

```
type Query {

  dono(id: String): Pessoa

}
```

Perceba que estamos definindo uma consulta que estamos chamando de *dono* dentro das *queries* expostas pela nossa API GraphQL. Você pode entender isso como se fosse um possível *endpoint* de nossa API. Nós ainda podemos receber um parâmetro em nossa consulta: o id do dono a ser pesquisado. Por fim, essa consulta promete nos retornar um objeto do tipo *Pessoa*.

Se fôssemos invocar uma consulta para nossa API querendo recuperar as informações do dono e seus respectivos cachorros com o id 1, poderíamos ter a consulta abaixo:

```
query DonoPorId($id: String){

  dono(id: $id){

    id

    nome

    idade

    cachorros {

      id

      nome

      raca

    }

  }

}

// Variáveis

{

  "id": 1

}
```

Veja que estamos criando uma consulta nomeada chamada *DonoPorId*, que recebe um parâmetro chamado *id*. Sabemos que *id* é um parâmetro por causa do *$* à frente dele -- o *$* é indicador de variável para o GraphQL. Internamente, essa consulta nomeada chamará a *query* *dono* em nossa API, repassando o valor da variável *id* como valor para o parâmetro *id* que a *query* espera em nosso serviço. Nós nomeamos essa consulta para que seu significado fique mais claro no cliente -- essa é considerada uma boa prática quando estamos lidando com o GraphQL.

Perceba ainda na consulta acima que nós queremos recuperar o dono cujo id é 1. Note também que estamos especificando os campos que desejamos como resposta: o id, o nome, a idade e os cachorros do dono com o id repassado. Ainda especificamos as informações dos cachorros que desejamos: o id, o nome e a raça.

Poderíamos ter a resposta abaixo para essa consulta:

```
{

  "data": {

    "dono": {

      "id": 1,

      "nome": "João"

      "idade": 20,

      "cachorros": [{

        "id": 1,

        "nome": "Manu",

        "raca": "Poodle"

      }]
    }

  }

}
```

Se não quiséssemos todos estes campos, poderíamos especificar isso no *payload* da nossa consulta (esse é um dos pontos mais interessantes do GraphQL, pois nós não precisaríamos fazer nenhuma modificação em nossa API para que ela ganhe essa habilidade de "filtragem" de informações a serem retornadas).

```
query DonoPorIdSoNomes($id: String){

  dono(id: $id){

    nome

    cachorros {

      nome

    }

  }

}

// Variáveis

{

  id: 1

}
```

Pela consulta acima, nós só desejamos o nome do dono e os nomes dos cachorros vinculados a este dono. Sendo assim, teríamos a seguinte resposta:

```
{

  "data": {

  "dono": {

    "nome": "João"

    "cachorros": [{

        "nome": "Manu",

     }]
  }

  }

}
```

Já as *mutations* são utilizadas quando desejamos alterar dados em nossa API. Uma inserção, por exemplo, deveria ser uma *mutation* em uma API GraphQL.

A definição de uma *mutation* é feita de maneira muito similar a de uma *query*, com exceção de que elas são definidas em um objeto especial chamado *mutation* (ao invés de ser definido no objeto *query*).

Por exemplo: poderíamos especificar a ação de inserção em uma API GraphQL a partir do seguinte fragmento de *schema*:

```
type Mutation {

  criarDono(dono: Pessoa!): Pessoa

}
```

Nesse caso, temos uma *mutation* que, pelo nome, promete inserir uma nova pessoa em nossa API. Além disso, ela nos promete retornar um objeto *Pessoa*: provavelmente, a pessoa que acabou de ser inserida na API GraphQL.

Se fôssemos invocar esta ação de nossa API GraphQL, poderíamos ter a seguinte requisição:

```
mutation NovoDono($dono: Pessoa){

  criarDono(dono: $dono){

    id

  }

}

// Variáveis

{

  "nome": "Maria",

  "idade": 30

}
```

Acima, estamos criando novamente uma operação nomeada, que se chamará *NovoDono*. Esta operação, que recebe um objeto *Pessoa* como parâmetro, irá na verdade invocar o método *criarDono* de nossa API GraphQL, repassando o objeto *Pessoa* que foi recebido pelo parâmetro *dono*. No final, nós ainda queremos simplesmente o id do novo dono que foi inserido como resposta para essa *mutation*. No final, teríamos por exemplo a resposta abaixo:

```
{

  "data": {

    "criarDono": {
      "id": "05e3b4d7-ed80-4aa2-b7e5-4d020849cbd1"\
    }

  }

}
```

Já as *subscriptions* constituem um recurso interessantíssimo do GraphQL. Elas tornam possível reagir a modificações de informações no servidor dentro dos clientes de uma API GraphQL em tempo real através de uma conexão geralmente baseada em WebSockets. Sendo assim, é perfeitamente possível com GraphQL notificar os clientes quando determinados eventos acontecem no servidor. Um exemplo interessante: as notificações do Facebook. Quando um amigo seu faz um post em um grupo do Facebook do qual você faz parte, você recebe uma notificação quase que instantaneamente... Você conseguiria um efeito muito similar através das *subscriptions* do GraphQL. Você teria uma operação de inserção de um post, operação essa a qual seu cliente poderia reagir através de uma *subscription*. O mais legal é que isso é intrínseco ao GraphQL, o que com certeza facilita muito para nós como desenvolvedores.

Por fim, é importante entendermos como o servidor GraphQL saberia de onde ele iria obter os donos e cachorros para consulta e aonde os novos donos e cachorros seriam inseridos. Isso é feito através de uma estrutura chamada *resolver*. Para uma mesma API GraphQL, você poderia ter diferentes *resolvers* -- um para MongoDB, outro para MySQL e outro para arquivos físicos, por exemplo. Isso mostra um outro aspecto importante do GraphQL: ele não é acoplado com nenhuma tecnologia de armazenamento de dados. Na verdade, o GraphQL não é acoplado a nenhuma tecnologia específica.

## Mas isso está parecendo com... REST!

![](https://i.imgur.com/AvXp2Ue.png)

E você não está errado em pensar isso... Na verdade, podemos dizer de certa forma que o GraphQL meio que compete com o REST. Mas por que poderíamos precisar de uma alternativa ao já tão popular REST?

Alguns pontos podem complicar a implementação de uma API REST. Vamos imaginar o seguinte cenário: sua aplicação precisa de um *endpoint* que retorne um dono de cachorro e seus respectivos cachorros por um id, igual vimos anteriormente.... Provavelmente, se sua API implementa o REST, você terá um *endpoint* que responde por GET e retorne aquela mesma lista que vimos anteriormente. Seu *endpoint*, se estivermos falando de uma API local, poderia ser este:

`https://localhost:8080/api/v1/pessoas/1`

Enquanto sua resposta poderia ser a mesma obtida anteriormente:

```
{

  "data": {

    "dono": {

    "id": 1,

    "nome": "João"

    "idade": 20,

    "cachorros": \[{

        "id": 1,

        "nome": "Manu",

        "raca": "Poodle"

      }\]\
    }

  }

}
```

Agora, imagine que você precise de um *endpoint* que também precise retornar o dono e seus cachorros pelo id do dono, porém, você agora não precisa retornar todas as informações vistas anteriormente: você precisa somente do nome do dono e do nome dos cachorros... Em uma API REST, como poderíamos proceder nessa situação?

Bom, nós teríamos duas possibilidades: a primeira, mais simples, é utilizar exatamente o mesmo *endpoint* anterior e desprezar as informações adicionais no cliente que fez a requisição. A segunda, mais complexa, seria a criação de um *endpoint* específico que responda somente com as informações necessárias.

A primeira hipótese (utilização do mesmo *endpoint*) seria a solução que a maioria das pessoas adotaria, já que não há prejuízo de performance perceptível do lado do servidor desta API. Mas e o lado do cliente? Desta maneira, nós estaríamos forçando o cliente a *parsear* informações que nós nem precisamos... Isso sem falar da questão do tráfego: nós teríamos um *response* que seria bem maior e mais pesado por conter informações que em tese seriam inúteis para aquela situação, o que implicaria em maior tráfego de dados e tempo de resposta por parte do cliente. O maior problema nem seria o tempo de resposta do cliente ser maior por ter mais informações para *parsear*, mas sim você penalizar o cliente com um tráfego maior simplesmente porque, em tese, você está com preguiça de criar um novo *endpoint* adequado, haha. E, se você pensar que o acesso à internet no Brasil é um problema considerável ainda (quer seja pela velocidade baixa em algumas regiões, quer seja porque muitas pessoas contam com alguma limitação de acesso à internet -- como os pacotes de dados dos planos de celular), isso pode significar um grande problema para sua aplicação.

A segunda hipótese (criação de um *endpoint* que responda somente com as informações necessárias) seria a mais correta tecnicamente. Nós poderíamos ter o seguinte *endpoint*...

`https://localhost:8080/api/v1/pessoas/somenteNomes/1`

Que forneceria a seguinte resposta:

```
{

  "data": {

    "dono": {

    "nome": "João"

    "cachorros": \[{

      "nome": "Manu",

      }\]\
    }

  }

}
```

O problema de tráfego estaria resolvido, mas você precisaria criar um *endpoint* que aplicasse exatamente as regras do *endpoint* original, só que retornando somente os nomes dos donos e dos cachorros. Além de isso remeter a duplicação de recursos, isso pode ficar insustentável à medida que sua API precisar crescer.

Isso acontece porque o REST, por implementar as regras que o protocolo HTTP propõe, é orientado a recursos. Sendo assim, um *response* que traga todas as informações poderia ser encarado como um recurso diferente do que é exposto em um *endpoint* que nos traga somente os nomes dos donos e dos cachorros. Outro ponto que acontece é que o servidor é responsável por definir o que é entregável para o cliente, sendo o cliente praticamente um mero "escravo" do servidor no que diz respeito às informações que devem ser trafegadas.

O GraphQL mitiga este ponto. Anteriormente, nós vimos que o próprio cliente, ao disparar uma *query* por exemplo, pode especificar que tipo de informação deve ser retornada a partir do servidor. E isso é natural ao GraphQL: nós não precisamos criar uma *query* específica para retornar as informações que o cliente precisa em uma determinada situação, pois o GraphQL já está preparado para realizar essa filtragem do que deve ser retornado ou não.

```
query DonoPorIdSoNomes($id: String){
  dono(id: $id){
    nome
    cachorros {
      nome
    }
  }
}

// Variáveis

{
  id: 1
}
```

Na *query* acima, por exemplo, já deixamos claro que só desejamos que o nome do dono e o nome de seus respectivos cachorros sejam retornados. O fluxo foi invertido: não é o servidor que define o que deve ser enviado para o cliente; é o cliente que diz o que ele precisa do servidor. E o melhor: nós não precisamos fazer nenhuma alteração no servidor para que ele passe a entender essa inversão de fluxo.

Veja, não estou dizendo que isso é algo exclusivo do GraphQL e que seja impossível implementar em uma API REST... Sim, poderíamos aplicar algo assim também em uma API REST. Mas isso demandaria trabalho adicional, enquanto no GraphQL, isso já está pronto.

A questão das *subscriptions* também é fantástica. Em uma API REST, nós precisaríamos meio que implementar algo com WebSockets "na mão", enquanto esse recurso já está disponível praticamente de maneira natural no GraphQL.

Temos mais uma diferença palpável entre APIs REST e APIs GraphQL: no final, em uma API REST, os *endpoints* acabam meio que agindo como identificadores de recursos. Por exemplo: se temos o *endpoint* abaixo:

`https://localhost:8080/api/v1/pessoas`

Podemos tranquilamente deduzir que ele irá devolver dados de pessoas. Já o GraphQL é orientado aos *schemas* que nós vimos anteriormente. O que é excelente, pois podemos mudar a forma como expomos nossos recursos sem que isso impacte em novos *endpoints* ou em versionamentos de API, mitigando uma possível quebra entre o servidor da API e seus clientes.

## Mas então por que estou usando REST ainda? Vou migrar tudo para GraphQL!

![Vamos declarar guerra ao REST!](https://i.imgur.com/iiw8QUa.png)

Também não é bem assim... Primeiro por causa do próprio trabalho de migração do REST para o modelo do GraphQL. Esse não é um trabalho trivial, tanto da parte do cliente como da parte do servidor.

APIs baseadas em GraphQL também podem trazer alguns problemas: elas não são, por exemplo, versionadas, não pelo menos de maneira natural. Em alguns cenários, o versionamento de APIs pode ser muito interessante: por exemplo, se estamos com sistemas novos e legados que consomem os mesmos recursos. Muitas vezes, pode vir a ser interessante separarmos o acesso de sistemas legados de sistemas que são mais recentes. Com REST, uma das maneiras de se fazer isso é através do versionamento. O versionamento de APIs também nos ajuda a identificar as alterações que uma API teve no decorrer do tempo, o que fica completamente transparente com o GraphQL. Dependendo da situação, isso pode vir a causar alguns problemas, principalmente a longo prazo ou em ambientes completamente heterogêneos, com várias aplicações de várias versões consumindo a mesma API.

Outro ponto interessante que pode pesar contra o GraphQL: ele não esconde informações por padrão, já que é o cliente quem decide o que o servidor deve retornar ou não. Por causa disso, o cliente também é obrigado a entender o nome de todos os *fields* e integrações entre os diferentes *object types* para fazer estas requisições de maneira correta. Isso pode não ser interessante em alguns momentos, principalmente quando falamos de integrações com softwares de terceiros, onde por vezes gostaríamos que algumas informações fossem ocultadas. O versionamento poderia auxiliar neste ponto, mas como vimos, o GraphQL não provê por hora um suporte para este recurso. Então, podemos ter um problema complexo de ser resolvido nessa situação, o que pode criar um grande quebra-cabeça entre os desenvolvedores da API (que precisam tomar muito cuidado com o que é exposto) e os consumidores dessa API (que acabam precisando de alguma maneira conhecer o *schema* da API para que possam se comunicar com esta).

Veja que aqui vale o velho mantra de qualquer tecnologia: existem situações onde o GraphQL é muito bem-vindo, enquanto em outras o bom e velho REST (ou até mesmo o "vovô" SOAP) pode ser a melhor saída. Cabe a nós como desenvolvedores analisar cada situação e tomar a melhor decisão nesse sentido.

## Frameworks e bibliotecas que podem ajudar a implementar o GraphQL

Alguns frameworks e bibliotecas podem ajudar bastante a implementar o padrão GraphQL, tanto no lado do cliente, como do lado do servidor. Algumas destas bibliotecas e alguns destes frameworks são:

-   [GraphQL-JS][https://github.com/graphql/graphql-js]: implementação para servidores GraphQL baseada no Node.js. Essa é, inclusive, a implementação original do GraphQL. Você pode utilizar esta biblioteca em conjunto com o Express, por exemplo, para expor uma API GraphQL;
-   [GraphQL-Server][https://dev.apollodata.com/tools/graphql-server/]: é a implementação para servidores do principal framework GraphQL atualmente, o Apollo. Trata-se da implementação mais popular atualmente. Abordamos esta implementação para servidores em nosso [curso de GraphQL](https://www.treinaweb.com.br/curso/graphql-criando-apis-modernas-com-graphcool-e-apollo);
-   [Apollo-Client][https://www.apollodata.com/]: é a implementação do Apollo para clientes GraphQL. É também a implementação para clientes abordada em nosso curso;
-   [Relay][https://facebook.github.io/relay/]: uma implementação do próprio Facebook para clientes React.

## Concluindo...

O GraphQL pode trazer uma série de benefícios com relação ao desenvolvimento de APIs modernas, seja através do conceito no qual o cliente pode definir o que o servidor deve retornar como resposta ou através de todo o seu ferramental, como as *subscriptions*. Porém, como quase tudo nessa vida, ele não é uma "bala de prata": se você precisa de uma API versionada ou de um controle maior sobre o que é exposto para seus clientes, talvez o REST ou até mesmo o SOAP possam resolver melhor a situação.

Porém, trata-se de um padrão que já teve uma grande aceitação na comunidade, inclusive com grandes *cases* de sucesso (o próprio Facebook pode ser considerado um caso de sucesso do GraphQL). Por isso, já fica claro que o GraphQL veio para ficar, o que torna importante que nós como desenvolvedores conheçamos mais esta nova especificação (por mais que talvez não gostemos de alguns de seus conceitos ou talvez da sua ligeira verbosidade).

Caso queira, você pode acompanhar o repositório oficial do GraphQL no GitHub por esse [link](https://github.com/facebook/graphql).

Se você também se interessar, temos um [curso bem legal de GraphQL e Graphcool no TreinaWeb](https://www.treinaweb.com.br/curso/graphql-criando-apis-modernas-com-graphcool-e-apollo?utm_source=tableless&utm_medium=artigo_graphql_bottom&utm_campaign=parceiro).

Até a próxima! ;)

 