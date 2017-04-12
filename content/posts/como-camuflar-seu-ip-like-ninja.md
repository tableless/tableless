---
title: Como camuflar seu ip like a ninja
author: Júlio Carneiro
type: post
date: 2016-12-04
url: /como-camuflar-seu-ip-like-ninja/
categories:
  - Artigos
  - Código
  - Técnicas e Práticas

---
Temos algumas formas de camuflar ip, alguns programas que nos auxiliam a fazer isso de forma fácil. A um tempo atrás eu estava usando o sistema operacional <strong class="markup--strong markup--p-strong">WHONIX</strong> para poder fazer esse tunelamento pra mim, ele é realmente eficaz e eu não precisei me preocupar muito com detalhes, porém eu testei algumas outras opções e tiveram duas que eu realmente gostei, uma é o <strong class="markup--strong markup--p-strong">PROXYCHAINS</strong> e a outra o <strong class="markup--strong markup--p-strong">JONDO</strong>:

> <https://anonymous-proxy-servers.net/en/jondo.html>
> 
> <http://proxychains.sourceforge.net>

&nbsp;

Ambas tem seus prós e contras obviamente, achei o **proxychains** com mais liberdade para trabalhar em diversas áreas e o **jondo mais eficaz no que se propõe a fazer, **porém um pouco mais limitado.

Vou ensinar as duas formas ok? Deste modo você pode fazer testes com as duas e escolher qual é a melhor para **o seu propósito**, vamos lá:

### ProxyChains

O **proxychains** é um programa que faz o roteamento de suas requisições através de **proxys** que você escolhe por uma lista **que você mesmo faz**, porém vamos fazer um pouco diferente usando o **tor router** para direcionar as requisições diretamente para porta do tor, fazendo com que tudo passe pelo router do tor antes de ir para web.

Eu não uso o **kali linux**, porém baixei todos os repositórios dele para o ubuntu com o “**KATOOLIN**” ( <a href="https://github.com/LionSec/katoolin" rel="nofollow"><strong>https://github.com/LionSec/katoolin</strong></a> ), á partir daí instalei o **proxychains** na minha maquina, caso você use o kali, os repositórios que vamos usar já vem na distro por default então é só instalar.

Vamos instalar o **tor** e o **proxychains** para que eles trabalhem juntos:

<pre>sudo apt-get install tor
sudo apt-get install proxychains</pre>

Feito a instalação a configuração é muito fácil, vamos precisar abrir o arquivo de configurações do proxychains, que é o “/etc/proxychains.conf”. Vamos abrir ele com o nano:

<pre>sudo nano /etc/proxychains.conf</pre>

Com o arquivo aberto vamos comentar a linha “strict\_chain” e descomentar a linha “dynamic\_chain”, e no final do arquivo vamos adicionar a seguinte linha:

<pre>socks5 127.0.0.1 9050</pre>

Vamos salvar o arquivo e podemos iniciar o services do Tor para depois podermos começar com o proxychains:

<pre>sudo service tor start</pre>

Agora para fazermos com que o tunelamento funcione com o proxychains é só adicionar o comando “proxychains” antes do programa que você quer utilizar, exemplo:

<pre>sudo proxychains firefox</pre>

Entre em algum site de consulta de ip e veja seu ip camuflado com sucesso utilizando o tor e o proxychains ;D

### JonDo

Você pode usar JonDonym para navegar anônimo, e-mail anônimo, chats e outros fins. **JonDo** , anteriormente JAP, é uma ferramenta de proxy IP Changer. Ele atua como um proxy e irá encaminhar o tráfego de suas aplicações de internet criptografadas, e por isso vai esconder o seu endereço IP. É uma aplicação Java, open source e você pode baixá-lo gratuitamente.

Com o **JonDo** é o mesmo esquema, caso tenha o **kali linux** você só vai precisar instalar pelo repositório, caso use outra distro recomendo o **KATOOLIN** para baixar os repositórios do kali e assim instalar as aplicações dele.

Para instalação do **JonDo** e do **JonDoFox** ( que é um **firefox modificado **para não termos risco de sermos descobertos, ele desabilita o javascript e muitas coisas que podem dar informações sobre nossa navegação ) vamos precisar instalar o **java jre e algumas ****dependências**, e claro o jondo e jondofox que baixamos no site oficial indicado acima:

<pre class="lang-bash">sudo aptitude install default-jre java-wrappers firefox
sudo dpkg -i jondo_all.deb
sudo dpkg -i jondofox-en_all.deb</pre>

Com o **JonDo** e o **JonDoFox** instalados na minha maquina vou entrar no terminal e dar um “**sudo jondo**” assim, vamos inicializar a aplicação do **JonDo**, lá podemos ver algumas opções de configuração e tudo que o programa oferece, veja:<figure>

![][1]</figure> 

&nbsp;

Com o **JonDo** rodando, podemos agora inicializar o **JonDoFox**, que vai ser nosso **navegador anonimo** trabalhando junto ao **JonDo**, vamos inicializar e entrar em algum site de consulta de ip para nos localizarmos, veja:<figure>

![][2]</figure> 

&nbsp;

Por aí já da para vermos que estamos utilizando o **JonDo** corretamente, o site de status deles nos da essa resposta assim que entramos para fazer o teste.<figure>

![][3]</figure> 

&nbsp;

É bem legal o jeito que ele dá o **status completo do seu anonimato**, este site é próprio do **JonDo** para testar seu anonimato. Acho importante ser a **primeira coisa que você deve fazer** ao iniciar o serviço.

Espero que tenham curtido o post, qualquer dúvida só comentar ai em baixo! Abraços e até o próximo post.

 [1]: https://cdn-images-1.medium.com/max/800/1*ThtPBRe1tD7aqjiFMEWvlQ.png
 [2]: https://cdn-images-1.medium.com/max/800/1*4cjyOlP2MnoNHbnyuEhsbA.png
 [3]: https://cdn-images-1.medium.com/max/800/1*1qhJ-OTxjcv2ritD_DKjSg.png