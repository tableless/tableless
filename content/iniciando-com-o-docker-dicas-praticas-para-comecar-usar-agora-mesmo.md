---
title: 'Iniciando com o Docker: dicas práticas para começar a usar agora mesmo'
author: André Kiffer
type: post
date: 2016-04-19
excerpt: Informações introdutórias para começar com Docker.
url: /iniciando-com-o-docker-dicas-praticas-para-comecar-usar-agora-mesmo/
titulo_personalizado:
  - 'O básico sobre <strong>Docker</strong>'
categories:
  - Destaques
tags:
  - docker

---
Nós no [Elasticpush][1] utilizamos Docker para criar nossos ambientes de desenvolvimento, não que o Docker seja somente para isso, aliás, a sua principal vantagem é poder ter a mesma imagem da sua máquina e em produção.

Mas enquanto não reestruturamos as coisas para rodar o Docker em produção utilizamos suas vantagens no ambiente de desenvolvimento o que já nos trás uma série de benefícios como:

  * Facilidade de configuração do ambiente de novos membros da equipe
  * Ter diversas versões da mesma biblioteca rodando sem conflito para testes pontuais
  * Poder trabalhar em outros projetos sem comprometer os recursos da máquina e sem a necessidade de levantar uma Máquina Virtual inteira somente para isso.
  * Acabar com a história do &#8220;Na minha máquina funcionava&#8221; (Caso rode em produção também)
  * Versionar a configuração necessária para certo serviço rodar. Para que outros desenvolvedores não precisarem fazer tudo novamente. 

No inicio não foi tão simples ver essas vantagens e nem entender como as coisas realmente funcionavam por trás do Docker, por isso, gostaria de compartilhar alguns dos principais comandos para você poder brincar e ir se familiarizando com a ideia de usar essa plataforma. 

## O que é o Docker

**Docker** é uma plataforma open-source escrita em **GO** cuja finalidade é criar ambientes isolados para aplicações e serviços. Com esse isolamento o docker garante que cada container tenha tudo que um serviço precisa para ser executado. 

Uma das vantagens dessa abordagem é você poder iniciar esse serviço em qualquer máquina que sempre irá rodar da forma esperada, com bibliotecas, dependências e permissões configuradas da forma correta, sem surpresas.

Quem trabalha com DevOps sabe o quanto isso facilita o dia a dia, ao invés de você criar um snapshot da máquina inteira, você pode ter vários containers docker rodando na mesma máquina podendo substituí-los ou adicionar novos a medida que for achando necessário. Sem contar na facilidade de reuso, pois você pode usar serviços idênticos em diferentes projeto como por exemplo: Nginx, Elasticsearch, Kafka, PHP-FPM, entre outros. 

## Instalando o Docker

Para distribuições Linux é muito simples de se instalar o Docker, já quem usa OSX ou Windows precisa rodar o docker dentro de uma Máquina Virtual.

<pre class="lang-shell">root@ubuntu:~$ apt-get install docker.io</pre>

## Comandos Básicos

Agora que você já tem o Docker instalado em sua máquina, vamos ver os principais comandos que você precisa para poder baixar imagens e executar containers.

Para o docker poder baixar uma imagem é necessário que ela esteja no Docker Hub ou em algum outro registry. Por padrão se nenhum outro registry for especificado a imagem será baixada do [Docker Hub][2].

No [Docker Hub][2], existem milhares de imagens disponíveis que a comunidade foi contribuindo e que facilitam muito a vida do desenvolvedor. Você pode montar um ambiente completo em questão de minutos baixando as imagens que precisar e ir linkando umas com as outras. Em um outro post explicarei uma forma de versionar essa linkagem de containers usando Docker Compose.

<pre class="lang-shell">rroot@ubuntu:~$ docker pull [nome da imagem]; #Baixa a imagem.</pre>

Quando você executa o comando acima, o docker irá baixar a imagem e deixar salva em sua máquina. Ela ainda não estará rodando, pois é só a imagem o que vai ser executado é um container, você pode executar vários containers da mesma imagem.

<pre class="lang-shell">rroot@ubuntu:~$ docker images; #Lista todas as imagens baixadas

root@ubuntu:~$ docker run [nome da imagem]; #Inicia um container da imagem que você escolheu.</pre>

O comando **docker run** tem diversos parâmetros que você pode passar como: volume (**-v**) para você mapear uma pasta da máquina pra dentro do container, qual porta (**-p**) você quer externar para que a máquina consiga fazer requisições dentro do container, enfim são várias configurações possíveis. 

É interessante você pegar alguns exemplos práticos nas próprias descrições das imagens para entender o funcionamento geral e ver a documentação oficial para entender a utilidade de cada parâmetro.

<pre class="lang-shell">rroot@ubuntu:~$ docker ps; # Lista os containers em execução

root@ubuntu:~$ docker exec [container id] [comando]; #Executa comandos dentro do container

root@ubuntu:~$ docker stop $(docker ps -aq); #Para a execução de todos dos containers

root@ubuntu:~$ docker rm $(docker ps -aq); #Exclui todos os containers criados</pre>

## Docker na prática**
  
** 

Aqui vai um comando prontinho pra você executar um script em uma linguagem que não tem na sua máquina. Eu escolhi o ruby:

<pre class="lang-shell">rroot@ubuntu:~$ echo puts 'Tableless' &gt; 'hello_ruby.rb' #Criando um arquivo .rb que imprime no console a frase "Tableless".

root@ubuntu:~$ docker run -v "$(pwd)":/var/ruby -w /var/ruby google/ruby sh -c 'ruby hello_ruby.rb'</pre>

Executando esse docker run, caso você não tenha a imagem **google/ruby** baixada na sua máquina o próprio docker vai se encarregar disso, fazendo o download e iniciando o container. 

A opção **-v** seguida do valor **&#8220;$(pwd)&#8221;:/var/ruby** mapeia a pasta atual (que você está executando o comando no terminal) onde criei o arquivo **hello_ruby.rb** para a pasta **/var/ruby** dentro container do docker. 

A opção **-w** seta de qual path vai partir a execução do comando no nosso caso parte de **/var/ruby**, o **google/ruby** é o nome da imagem do ruby que vamos usar e o **sh -c** do unix para executar o seguinte comando &#8216;**ruby hello_ruby.rb**&#8216;. 

Façam o teste na máquina de vocês e vejam como é simples rodar um script em uma linguagem que não estava configurada em seu ambiente.

Note que por traz de toda simplicidade do Docker existe uma ferramenta poderosa que está mudando a forma com o que as aplicações são distribuídas hoje em dia, além de ser um grande aliado para configuração do seu ambiente de desenvolvimento. 

Em um outro post, irei mostrar passo a passo o desenvolvimento de um app para mostrar como que seria a aplicação do docker em um ambiente real, nele mostrarei como criar suas próprias imagens usando o arquivo manifesto Dockerfile e também, um pouco de **Docker compose**.

Hoje mudei a forma de como eu instalo serviços na minha máquina, sempre que vejo uma ferramenta interessante busco primeiro no **Docker hub**, baixo executo e se for relevante deixo ali para quando for usar, caso contrário removo, já se tornou parte do meu dia a dia e tenho certeza que pra você também fará diferença.

Caso tenha alguma dúvida, ou queira compartilhar sua experiência com docker, fique à vontade para deixar um comentário.

 [1]: http://elasticpush.com
 [2]: http://hub.docker.com/