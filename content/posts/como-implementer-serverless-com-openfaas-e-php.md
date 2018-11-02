+++
authors = "KingHost"
canonical = "https://king.host/blog/2018/09/serverless-com-openfaas-e-php/"
categories = ["PHP"]
date = "2018-11-02T01:26:28-03:00"
excerpt = "Entenda como implementar serverless usando uma solução open source, o OpenFaaS."
image = "https://i.imgur.com/rxfTgrd.png"
publishdate = "2018-11-02T00:00:00-03:00"
tags = ["OpenFaas", "ServerLess"]
title = "Como implementer Serverless com OpenFaas e PHP"
type = "post"

+++
As arquiteturas sem servidor (serverless) são **projetos de aplicações que incorporam serviços “Backend as a Service” (BaaS)** de terceiros e/ou que incluem execução de código personalizado em contêineres efêmeros gerenciados em uma plataforma **“Functions as a Service” (FaaS)**.

Ao usar essas ideias e outras relacionadas, como aplicações single-page, **estas arquiteturas removem grande parte da necessidade de um componente tradicional de servidor**. As arquiteturas serverless podem se beneficiar de um custo operacional, **complexidade** e **lead time de engenharia significativamente reduzidos**, a um custo de maior dependência de fornecedores e serviços de suporte.

## Como implementar funções PHP Serverless com OpenFaaS

**Serverless computing**, ou simplesmente serverless, é um tema quente no mundo da arquitetura de software. Os fornecedores de nuvem “Big Three” – [**Amazon**](https://www.amazon.com.br/), [**Google**](https://www.google.com.br/) e [**Microsoft**](https://www.microsoft.com/pt-br) – investem pesado em Serverless, e vimos muitos livros, projetos de código aberto, conferências e fornecedores de software dedicados ao assunto.

Neste artigo, vamos ver **como podemos implementar serverless utilizando uma solução open source, o** [**OpenFaaS**](https://www.openfaas.com/).

## O que é o OpenFaas?

O **OpenFaaS** é uma **estrutura para criar funções serverless em contêineres** (com o Docker e o Kubernetes).

Com a ajuda de FaaS abertas, é fácil transformar qualquer coisa em uma função **sem servidor** que seja executada no **Linux ou no Windows**, por meio do **Docker ou do Kubernetes**. Ele fornece uma **funcionalidade integrada**, como infraestrutura de auto-recuperação, dimensionamento automático e a capacidade de controlar todos os aspectos do cluster.

Então, basicamente, o OpenFaaS **é um conceito de decompor nossas aplicações em uma pequena unidade de trabalho**. Um dos principais benefícios é o fato de não precisarmos gerenciar a infraestrutura de aplicações, possibilitando aos desenvolvedores se concentrarem em fornecer valor de negócios. Vale reforçar que o **serverless é perfeito para dispositivos IoT, arquitetura de microsserviços ou qualquer outro tipo de aplicação que precise ser eficiente**.

Além disso, o **OpenFaaS permite criar e distribuir funções “serverless”** em um ambiente de computação em nuvem.

A “function” pode ser uma lógica simples que você programa ou a execução de um binário para realizar uma ação.

Abro aqui um parêntese para comentar que o termo “serverless” é um pouco inadequado, pois você ainda **precisa de um servidor ou de muitos servidores**, mas ao implantar sua função na nuvem, **não precisa se preocupar em escalar ou gerenciar recursos** de servidor físico por conta própria.

Voltando ao OpenFaas, ele tem em destaque algumas funcionalidades como:

* **Facilidade de uso** através do portal de interface do usuário e instalação com um clique;
* Escrever funções em **qualquer linguagem para Linux ou Windows** e empacotar no formato de imagem Docker / OCI;
* Portátil – **executado em hardware existente ou nuvem pública/privada** – Kubernetes e Docker Swarm nativos;
* **CLI disponível** com formato YAML para modelar e definir funções;
* **Escala automática** à medida que a demanda aumenta.

## Visão geral do OpenFaaS

![](https://king.host/blog/wp-content/uploads/2018/09/texto-1.png)

### Function Watchdog

Você pode **transformar qualquer imagem do Docker em uma função sem servidor**, adicionando o **Function Watchdog** (um minúsculo servidor HTTP Golang).  
O Watchdog é o **ponto de entrada** que permite que as solicitações HTTP sejam encaminhadas para o processo de destino via STDIN. A resposta é enviada de volta ao requisitor escrevendo para STDOUT a partir do seu aplicativo.

### API Gateway / UI Portal

O **API Gateway fornece uma rota externa para suas funções** e coleta métricas do **Native Cloud** por meio do **Prometheus**.  
Seu API gateway escalará as funções de acordo com a demanda, alterando a contagem de réplicas de serviço no Docker Swarm ou na API do Kubernetes.  
Uma interface do usuário é preparada para permitir que você invoque funções em seu navegador e crie novas, conforme necessário.

### Prometheus / Grafana

O prometheus é utilizado para **monitorar os serviços**, mostrando o **dimensionamento automático ao vivo em ação**. Exemplo de um painel Grafana vinculado ao OpenFaaS:

![](https://king.host/blog/wp-content/uploads/2018/09/image2-780x390.png)

### CLI

Qualquer container ou processo em um container Docker pode ser uma **função sem servidor no FaaS**. Usando a FaaS CLI, você pode implantar suas funções ou criar rapidamente novas funções a partir de modelos como o Node.js, Python ou PHP.

## Configurando o OpenFaaS

Supondo que você **já tenha o Docker instalado**, a primeira coisa que você precisa fazer é inicializar o **Docker Swarm** e implantar a stack do OpenFaaS.

    docker swarm init --advertise-addr $(hostname -i)

Mude para uma pasta de trabalho adequada e **instale a stack do OpenFaaS** clonando o repositório do github e executando o script de implementação.

    git clone https://github.com/openfaas/faas &amp;&amp; \\  cd faas &amp;&amp; \\  ./deploy_stack.sh

Neste momento é gerado um **username e password** para acesso a UI e CLI do OpenFaaS, **guarde estes dados**.

Teste se a stack está funcionando invocando a função de exemplo **echoit** que faz echo de todos os dados de entrada enviados.

    curl 127.0.0.1:8080/function/func_echoit -d 'hello world'

Agora que o **OpenFaaS está funcionando**, você precisa **instalar a estrutura cli do OpenFaaS (faas-cli)** que permite construir, implementar e invocar suas próprias funções facilmente a partir da linha de comando.

    curl -sL https://cli.openfaas.com \| sudo sh

Em seguida, **instale o modelo PHP do OpenFaaS**:

    faas-cli template pull https://github.com/itscaro/openfaas-template-php

Agora vamos criar uma nova função e dizer qual linguagem usar.

## Construindo e implementando uma função PHP no OpenFaaS

Uma vez instalado o template, podemos testá-lo **criando nossa primeira função PHP**.

A sintaxe da linha de comando do OpenFaaS para criar uma nova função é a **faas-cli new functionname –lang languagename.**

O template PHP usa o nome da linguagem php para funções **PHP7,** e **php5 para funções PHP5**. Vamos criar uma função PHP7 chamada func-ping-php usando o código do template.

    faas-cli new func-ping-php --lang php |

Você observará um novo arquivo **func-ping-php.yml** e a **pasta da função será criada**.  
Dentro de **./func-ping-php** há um diretório src que contém uma classe **Handler.php**. Abra isso e você verá:

![](https://king.host/blog/wp-content/uploads/2018/09/image1-780x414.png)

Então, por padrão, ela apenas retorna os dados que você envia para ele.  
Agora temos a configuração do projeto, podemos construí-lo!

### Construindo nossa função

Para construir uma função, usaremos novamente o faas-cli:

    faas-cli build -f ./func-ping-php.yml |

Isso criará o container docker que executará nossa função.  
Uma vez que é construído, podemos implantá-lo!

### Implantando nossa função

    faas-cli deploy -f ./func-ping-php.yml |

Depois de executar esta função, você deverá ver:

![](https://king.host/blog/wp-content/uploads/2018/09/image5-780x299.png)

Isso nos diz que está tudo bem, assim como a URL com a qual podemos invocar a função.

### Executando nossa função

Agora, podemos acessar nossa função enviando uma solicitação POST para o URL especificada:

    curl -XPOST http://127.0.0.1:8080/function/func-ping-php

No entanto, não veremos nada, pois a função apenas retorna o que você envia para ela, e nós não enviamos nada para ela!

Agora, se enviarmos dados para ele, devemos ter os dados retornados. Então executamos:

    curl -XPOST -d "olá blog" http://127.0.0.1:8080/function/func-ping-php

Nos dará uma saída:  
_olá blog_

Agora, vamos atualizar nossa função para responder com o timestamp atual, já que é uma função “ping”.

### Atualizando nossa função

Vamos atualizar nossa função para retornar algum json, então, de volta em **./func-ping-php/src/Handler.php**, vamos alterá-lo para:

![](https://king.host/blog/wp-content/uploads/2018/09/image2-1-780x414.png)

Podemos verificar executando:

    curl -XPOST -H "Content-Type: application/json" http://127.0.0.1:8080/function/func-ping-php --head

O que nos mostrará que a resposta também retorna o **application/json**:

![](https://king.host/blog/wp-content/uploads/2018/09/8-1-780x328.png)

Agora então vamos reconstruir nossa função e reimplanta-lá de acordo com as etapas acima:

#### Construir

    faas-cli build -f ./func-ping-php.yml

#### Implantar

    faas-cli deploy -f ./func-ping-php.yml

Agora, se executarmos nossa função, veremos que recuperamos o JSON especificado:

    curl -XPOST http://127.0.0.1:8080/function/func-ping-php {"pong": 1532176701}

## Conclusão

Neste artigo/tutorial vimos que é simples **criarmos funções serverless** utilizando o projeto open source **OpenFaaS**, uma alternativa aos principais players do mercado que fornecem este serviço.

Para isso nós usamos basicamente a ferramenta **CLI do OpenFaaS (faas-cli)**, mas você também pode utilizar a interface do usuário, que facilita e permite que invoque funções em seu navegador e crie novas, conforme necessário.

![](https://king.host/blog/wp-content/uploads/2018/09/9-780x501.png)

E você, já conhecia o projeto OpenFaaS e qual a sua opinião sobre Serverless, já está utilizando?

Quer saber mais sobre o assunto? Confira no blog da KingHost em [http://kingho.st/kw8d](http://kingho.st/kw8d).