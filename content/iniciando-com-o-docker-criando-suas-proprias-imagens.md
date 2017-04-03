---
title: 'Iniciando com o Docker: Criando suas próprias imagens'
author: André Kiffer
type: post
date: 2016-04-28
url: /iniciando-com-o-docker-criando-suas-proprias-imagens/
categories:
  - Tecnologia e Tendências
tags:
  - build
  - Criar imagem no docker
  - docker
  - go

---
No artigo <a href="http://tableless.com.br/iniciando-com-o-docker-dicas-praticas-para-comecar-usar-agora-mesmo/" target="_blank">anterior</a>, eu descrevi alguns comandos básicos e como iniciar com o pé direito no mundo do **Docker**, trazendo de forma direta alguns conceitos que com o passar do tempo se tornaram fundamentais no meu fluxo de desenvolvimento.

Hoje eu quero partir um pouco mais para o lado prático da coisa, vamos construir uma imagem para encapsular uma pequena aplicação em **GO**.

## Primeiros passos

O arquivo de manifesto do Docker é o Dockerfile, nele você coloca as instruções de como você quer que sua imagem seja construída. Você pode na construção da imagem setar outro arquivo com o parâmetro -f.

Abaixo temos um exemplo de Dockerfile, esse é um exemplo de um app em go já compilado para ubuntu então eu só preciso copiar o arquivo executável elasticpush para dentro do docker:

<pre class="lang-bash">FROM debian:jessie
RUN mkdir /app
ENV ACCESS_TOKEN abc
ENV SECRET_TOKEN xyz
COPY ./bin/elasticpush /app/elasticpush
ENTRYPOINT [“/app/elasticpush”]
</pre>

Detalhando os comandos utilizados:

**FROM**: Este é o comando mais importante, pois ele especifica a imagem base para a construção de uma nova. Na maioria das vezes a imagem especificada vai ser uma distribuição linux, se essa imagem não for encontrada na máquina local, o docker tentará buscar em algum repository. Caso queira, por exemplo, fazer a build do seu app em GO dentro do container, você vai precisar de uma imagem que tenha o GO instalado e configurado. Outra forma também seria criar diversas instruções com o comando _RUN_ para fazer essa instalação.

**RUN**: Esse comando serve para executar outros comandos que a versão do sistema operacional permite. Por exemplo, se for debian vc pode instalar pacotes com apt-get, se for CentOS você pode utilizar o yum para pegar as dependências que seu serviço precisa para rodar. Com o RUN você também pode criar arquivos, pastas, enfim acho que deu pra entender que ele executa os mesmo comando do que você executaria na sua máquina, logo você consegue fazer praticamente tudo, e deixar a sequência de comandos versionada aqui dentro.

**ENV**: Serve para você setar variáveis de ambiente, você pode tanto deixar essas variáveis setadas de forma fixa dentro do Dockerfile quanto passá-las dinamicamente na hora que você instanciar o container. Para passar essas variáveis de ambiente na instanciação do container basta usar o parâmetro -e.
  
Exemplo: _docker run -e ACCESS_TOKEN=abcd [nome da imagem]_.

**COPY**: O COPY serve para você poder copiar arquivos e pastas para dentro da imagem do Docker, nesse exemplo eu copiei o arquivo elasticpush que estava dentro da pasta bin na minha máquina local para dentro da pasta /app na imagem do docker.

**ENTRYPOINT**: Com esse parâmetro você pode setar se quer que algo seja executado na hora da instanciação do container. Então, quando você der um _docker run_ nessa imagem, ela já vai instanciar e executar o programa que está no caminho que você colocar entre colchetes. No nosso caso queremos que essa imagem execute nossa aplicação do Elasticpush, o mesmo vale para quaisquer outros serviços como Redis, Elasticsearch, Nodejs, etc&#8230;

## Build &#8211; Construíndo a imagem

A essa altura provavelmente você já tem o Docker instalado na sua máquina, caso contrário ensinamos a fazer isso nesse <a href="http://elasticpush.com/blog/iniciando-com-o-docker-dicas-praticas-para-comecar-a-usar-agora-mesmo/" target="_blank">artigo</a>.

Para construir a imagem você precisa executar o seguinte comando, na mesma pasta que está o **Dockerfile**:

<pre><em>sudo docker build -t app/elasticpush .</em></pre>

Eu escolhi que o nome da minha imagem fosse app/elasticpush, mas isso fica a seu critério, escolha o nome que melhor se adéque ao seu serviço.

Executado o comando, se tudo correr bem terá uma saída semelhante a essa:

<pre class="lang-bash">Sending build context to Docker daemon 45.03 MB
 Sending build context to Docker daemon
 Step 0 : FROM debian:jessie
 — &gt; a582cd499e0f
 Step 1 : RUN mkdir /app
 — &gt; Using cache
 — &gt; 3763257cc26e
 Step 2 : COPY ./bin/elasticpush /app/elasticpush
 — &gt; cc4b56f3fd8e
 Removing intermediate container 0bb2091ca437
 Step 3 : ENTRYPOINT /app/elasticpush
 —&gt; Running in ad99734cd065
 — &gt; 3ffec68d5499
 Removing intermediate container ad99734cd065
 Successfully built 3ffec68d5499
 </pre>

Agora você já tem uma imagem construída. Execute o seguinte comando:

`sudo docker images`

A imagem com a tag que você escolheu vai estar listada. A partir dessa imagem você pode iniciar o container com o seguinte comando:

`sudo docker run -d [nome da imagem]`

Observe que utilizei o parâmetro -d que serve para jogar em segundo plano a inicialização do container, o que é opcional. Após isso será entregue um token que identifica o container, tipo esse:

`19895b08f19d7a4436afa1cb8af8f815939000d5468c7db10c4498317fd81cc3`

Para navegar dentro do container utilize o seguinte comando:

`sudo docker exec -it 19895b08f19d7a4436afa1cb8af8f815939000d5468c7db10c4498317fd81cc3 bash`

Com isso você estará dentro do container para caso precise fazer alguma coisa específica. Para sair é só digitar **exit**.

Bom pessoal, por enquanto é isso, uma dica que dou é tentar criar imagens mais complexas do que a que eu exemplifiquei, caso tenham alguma dúvida é só deixar um comentário.

Até a próxima!