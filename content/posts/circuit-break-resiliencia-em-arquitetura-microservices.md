---
title: Circuit break - Resiliência em arquitetura microservices
authors: Evandro Passos
type: post
image: https://i.imgur.com/ildGxn7.jpg
date: 2018-04-15
excerpt: Adotar uma arquitetura Microservices traz muitos benefícios, mas você precisa estar preparado para lidar com falhas nos serviços. No artigo explico como tratar problemas de Timeout utilizando Circuit Break Pattern.
categories:
  - Artigos
  - back-end
  - Ruby
tags:
  - Microservices
  - Circuit Break
  - Ruby
  - Resiliencia
---

Quando entrei no [iCasei](https://www.icasei.com.br), lá em 2016, a palavra que mais se ouvia falar no escritório era: [MicroServices](https://en.wikipedia.org/wiki/Microservices), como se fosse a solução para os problemas da empresa. 

Sim, adotar essa arquitetura para todos os nossos novos serviços trouxe muitos benefícios para nossa área de desenvolvimento, mas cara, como deu trabalho manter tudo trabalhando em conjunto e operando numa boa, sem gargalos. Ta bom, você ainda não esta ligado no que significa MicroServices? Vou dar um resumão então:

MicroServices
-------------

É uma forma de desenvolver software onde você tenta quebrar sua aplicação em N serviços que teoricamente precisam ter apenas uma responsabilidade e que quando requisitados, grande parte das vezes através de chamadas utilizando o padrão Restful, forneçam as informações necessária para todos consigam se comunicar.

Benefícios
----------

A galera vem adotando esse modelo de desenvolvimento por esses motivos:

### Escalabilidade

Com serviços espalhados, você consegue, por exemplo, escalar horizontalmente apenas da API que cuida do upload de fotos para o album, uma vez que chegaram a conclusão que ela é a que mais consome recursos em determinado momento do dia.

### Deploys menos traumáticos

Como sua aplicação esta toda quebrada em pequenos pedaços, a equipe consegue realizar pequenos deploys sem afetar todas funcionalidades do sistema

### Entrega contínua

As equipes conseguem trabalhar em paralelo uma vez que você não tem serviços e projetos muito dependentes.

### Manutenção mais fácil

Quem nunca ficou com medo do _cA$@%#$@_ de alterar uma linha de código e quebrar várias funcionalidades de um legadão brabo? Se você tem várias aplicações bem pequenas o impacto sempre vai ser menor.

Resiliência, cada segundo é muito tempo
---------------------------------------

Daora, são muitos os benefícios de se adotar essa arquitetura, né? Se você está afim de encarar a brincadeira e começar a criar seus serviços, não se esqueça de uma coisa: Você pode e vai sofrer com problemas de rede(tempo de resposta). 

Como 1, 2 segundos a mais no tempo de resposta de uma API fazem uma diferença absurda no teu eco-sistema, chegando ao ponto de ficar tão instável que muitos serviços não conseguem parar de pé devido ao empilhamento de processos que ficam esperando, esperando, esperando...até tudo cair. 

É ai que entram a tal da tática **Resiliência**! 

Quando um serviço sair do ar ou demorar demais para responder, tua aplicação precisa de uma alternativa para tratar esse erro até que tudo volte ao normal, senão, ela também pode cair. Como já é de se esperar, outras pessoas já passaram pelo mesmo problema e criaram um padrão para que todos possam utilizar em seus projetos.

Circuit Break
-------------

[Martin Fowler](https://martinfowler.com/) já escreveu um pouco sobre o assunto em seu blog e a ideia consiste em ficar monitorando um bloco de código esperando possíveis falhas. Quando o número de falhas chegar no limite configurado pelo desenvolvedor o circuito é aberto e as próximas requisições da fila não irão executar o bloco por um tempo também pre-definido. 

Para fazer a decisão de quando executar ou não o bloco o Pattern Circuit Break utiliza 3 propriedades que devem ser sempre configuradas:

#### failure_threshold

Quantas falhas devem ocorrer para que o circuito seja aberto?

#### duration

Por quanto tempo as requisições não irão executar o bloco com falha?

#### timeout

Qual o tempo de resposta limite que um bloco pode demorar para então explodir a Exception?

Exemplo prático
---------------

Para quem trabalha com Rails, existe um Gem chamada [circuit_breakage](https://github.com/djspinmonkey/circuit_breakage) que já tem toda uma implementação do Pattern e vou utiliza-la para mostrar como tudo funciona, beleza? 

No [Clube do Código](https://www.clubedocodigo.com.br) como realizamos algumas requisições em APIs externas também trabalhamos ela e até agora vem trazendo ótimos resultados. **No final do artigo tem o link do repositório no Github para quem quiser brincar um pouco.** No _**GemFile**_ adicionei a chamada da para a circuit_breakage

```ruby
gem 'circuit_breakage'
```

Criei uma classe na minha API chamada _**list_posts.rb**_  que vai ser responsável por realizar o Request para buscar os posts.

```ruby
class ListPosts 
  include Singleton 
  
  API_POSTS_URL = 'https://jsonplaceholder.typicode.com/posts' ....
```

Aproveito para instanciar meu Circuit Break no construtor da classe e configurar o limite de falhas, duração e timeout.

```ruby
def initialize 
  @circuit_breaker = CircuitBreakage::Breaker.new 
  @circuit_breaker.failure_threshold = 2 
  @circuit_breaker.duration = 3 
  @circuit_breaker.timeout = 3 
end
```

Feito isso, crio um método chamado _**request_posts**_ que realiza uma requisição HTTP e faz o parse da resposta:

```ruby
def request_posts 
  response = RestClient.get API_POSTS_URL 
  JSON.parse response.body, symbolize_names: true 
end
```

E crio dois métodos para salvar resultado em uma chave no cache do Rails:

```ruby
def to_cache(posts) 
  Rails.cache.write('posts', posts) 
end 

def posts_cached 
  Rails.cache.read('posts') 
end
```

Para orquestrar tudo isso crio o método _**execute**_:

```ruby
def execute 
  posts = [] 
  begin @circuit_breaker.call do 
    posts = request_posts 
    to_cache posts 
   end 
  end 
  rescue CircuitBreakage::CircuitOpen
      posts = posts_cached 
  rescue CircuitBreakage::CircuitTimeout 
    posts = posts_cached 
  end 
  posts 
end
```

Como vocês podem perceber, realizei a chamada do método _**request_posts**_ em um bloco dentro do meu Circuit Break, ou seja, caso o Request ultrapasse o limite de timeout que informei lá na instancia, o circuito vai alterar a sua propriedade state para Open e todas as requisições vão buscar a informação no cache fornecido pelo método _**posts_cached.**_ 

Na Controller, não tem nenhum mistério, apenas utilizo minha instancia do ListPosts para pegar os posts e repassar via JSON.

```ruby
def index 
  posts = ListPosts.instance.execute 
  render json: posts 
end
```

Fiz um teste unitário para provar que o negócio funciona:

```ruby
describe 'list_posts' do
  it "when execute success" do
    posts = ListPosts.instance.execute
    expect(posts.length).to_not eq(0)
  end

  it "when to_cache received" do
    expect(ListPosts.instance).to receive(:to_cache)
    ListPosts.instance.execute
  end

  it "when circuit is open" do
    ListPosts.instance.circuit_breaker.timeout = 0.1
    ListPosts.instance.execute

    expect(ListPosts.instance.circuit_breaker.state).to eq('open')
  end
end
```

O que eu fiz foi diminuir muito limite de tempo de resposta induzindo o erro e assim consigo validar se o circuito realmente mudou seu estado para **Open.** 

Bom, é isso, espero que gostem, é uma prática que me ajuda e pode te ajudar muito nos projetos que vier enfrentar pela frente. 
O source completo esta lá no meu Github, beleza? Para acessar, [clique aqui](https://github.com/evandropassos/circuit-break-example).
