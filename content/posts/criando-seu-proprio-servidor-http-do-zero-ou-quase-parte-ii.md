---
title: Criando seu próprio servidor HTTP do zero (ou quase) – Parte II
author: thiguetta
type: post
date: 2015-09-11
url: /criando-seu-proprio-servidor-http-do-zero-ou-quase-parte-ii/
categories:
  - Back-end
  - Browsers
  - Código
  - HTML
  - HTML5
  - Java
tags:
  - desenvolvimento web
  - java
  - Na Prática
  - navegadores
  - Técnicas e Práticas
  - w3c
  - web
  - web standards

---
Se chegou até aqui é por que você terminou de ler a primeira parte do tutorial (Caso não, leia a [Parte I][1] ), mas não desista, a parte legal vai chegar, mas antes de começar, falta mais um item de teoria &#8211;  sim eu sei que é chato, mas juro que é importante &#8211; os Sockets.

## Sockets e portas

Falamos muito de requisições e respostas no último post mas ainda não falamos de conexão e troca de informações. Bom, vamos lá, ligeiramente comentamos um pouco sobre os protocolos de rede, também disse que o protocolo web, o HTTP, está na camada mais alta do TCP/IP, a camada de aplicação, mas para este tutorial pouco importa o que acontece nas camadas inferiores  (se tiver curiosidade procure mais sobre), o que realmente importa é saber que esse tal de TCP/IP é responsável pela conexão entre dois pontos (dois computadores, ou no nosso caso, cliente e servidor).

Tanto o servidor quanto o cliente são computadores com seus respectivos sistemas operacionais (Linux, Windows, etc) e neles estão em execução diversas aplicações inclusive o navegador e o próprio servidor HTTP, mas nesse monte de aplicações em execução, como vamos saber que estamos enviando e recebendo dados da aplicação certa? precisamos de um algo que identifique cada aplicação (ou pelo menos que identifique uma aplicação que use a rede). Esses pontos de identificação, por assim dizer, são chamados de Socket (ou em português, soquete, tomada, encaixe, enfim algo que tenha uma “abertura/encaixe&#8221; para conexão), resumindo é um ponto que permite conectar alguma coisa, no nosso caso, um outro computador através da rede. Para receber uma conexão, o Socket precisa de uma abertura, essa abertura é o que chamamos de porta, sei que para alguns o conceito parece ser trivial, mas para outros, inclusive profissionais de TI, esses conceitos podem embaralhar a cabeça.

Resumindo, um Socket é o ponto final da conexão, onde uma porta é aberta para que a aplicação possa enviar ou receber dados, cada porta é identificada por um número que é única no computador, sendo que se tentar abrir uma porta que já estiver sendo usado por outra aplicação, o sistema operacional irá barrar e retornar um erro de acesso negado ou informa que a porta está em uso.

Existe uma lista de portas conhecidas  que são utilizadas por algumas aplicações, as mais comuns são:

  * 21 FTP &#8211; Transferencia de arquivo
  * 22 SSH &#8211;  Secure Shell
  * 25 SMTP &#8211; Envio de Emails
  * 80 HTTP &#8211; Web
  * 443 HTTPS &#8211; Web “Segura&#8221;

Uma porta ela é única por computador mas não é única na internet, quando você quer efetuar a conexão com uma determinada aplicação rodando em um computador remoto, a identificação do socket é composto pelo endereço de IP ou o nome canônico (domínio &#8211; endereço do site) da máquina destino e a porta que essa aplicação usando, no seguinte formato {Endereço}:{Porta}.

<pre class="lang-html">exemplo.com:80 ou
 192.168.1.224:1000     
</pre>

A maioria das aplicações que requerem conexão com algum serviço se conectam diretamente as portas especificas que cada uma delas usa, sendo necessário informar apenas o IP (ao menos que seja uma porta que a aplicação não conheça, o serviço está funcionando numa porta atípica ai será necessário informar, veremos mais na parte III). O que isso significa? isso significa que quando você digita o site <http://www.google.com.br> no seu navegador, ele sabe que os servidores HTTP estão executando na porta 80, então não é preciso identificar-la, pois o navegador irá &#8220;converter&#8221; para o formato correto, transparentemente, a mesma coisa acontece quando você acessa um site seguro utilizando https://www.seubanco.com.br o navegador sabe que a porta de conexão segura no servidor é a 443, e tentará se conectar nela.

O que acontece é seu navegador irá se conectar ao site, ele sabe que o servidor está respondendo na porta 80 no endereço tal, para isso é necessário que o navegador abre uma porta local aleatória, para que assim o servidor possa saber para quem responder:

[<img src="http://www.raywenderlich.com/uploads/2011/06/sockets.jpg" alt="" width="600" height="200" />][2]

Pronto agora que entendemos o conceito (ou pelo menos espero que tenham entendido =D) vamos colocar as mãos na massa.

Vou partir do principio que já sabem criar uma classe e compilar um programa em Java (caso não lembre-se que o Google é nosso amigo =D). Se preferir, usando o mesmo conceito pode converter a ideia para a linguagem de sua preferência (só não esqueça de compartilhar com a galera =D).

Vamos lá, vou criar uma classe em Java chamada Cliente, será uma classe simples que vai se conectar a um servidor (neste caso vamos conectar no [google.com.br][3]) e ver se ele está conectado, se sim ele imprimirá na tela o IP do servidor.

&nbsp;

<pre class="lang-javascript">import java.io.IOException;
import java.net.Socket;

public class Cliente {
    public static void main(String[] args) throws IOException {
        //cria um socket com o google na porta 80
        Socket socket = new Socket("google.com.br", 80);
        //verifica se esta conectado
        if (socket.isConnected()) { 
            //imprime o endereço de IP do servidor
            System.out.println("Conectado a " + socket.getInetAddress());
        }
    }
}
</pre>

Ao instanciar um novo objeto da classe Socket com os parâmetros domínio e porta, internamente a máquina virtual Java já abre uma porta aleatória em seu computador e em seguida conecta ao servidor google.com.br na porta 80. Veja que até então não sabemos o endereço de IP do servidor mas ao efetuar a conexão o socket já se atualiza com essa informação. Vamos compilar nossa classe e verificar o resultado que  deve ser algo desse tipo:

<pre class="lang-bash">$ javac Cliente.java
$ java Cliente
Conectado a google.com.br/173.194.118.151</pre>

Mas isso não é o suficiente queremos trocar informações com o servidor conectado, para isso nosso socket fornece 2 recursos  um para leitura dos dados recebidos (InputStream) do servidor e outro para enviar os dados que queremos para o servidor (OutputStream), é claro que para enviarmos algum dado para o servidor temos que saber como se comunicar com o servidor, como a gente já sabe, o servidor do google é um servidor HTTP que nos fornece as páginas de serviço do Google, certo? então sabemos que o servidor entende o protocolo HTTP. vamos enviar uma requisição HTTP simples a esse servidor e ver o que ele responde.

<pre class="lang-javascript">/* veja que a requisição termina com \r\n que equivale a &lt;CR&gt;&lt;LF&gt;
       para encerar a requisição tem uma linha em branco */
    String requisicao = ""
        + "GET / HTTP/1.1\r\n"
        + "Host: www.google.com.br\r\n"
        + "\r\n";
    //OutputStream para enviar a requisição
    OutputStream envioServ = socket.getOutputStream();
    //temos que mandar a requisição no formato de vetor de bytes
    byte[] b = requisicao.getBytes();
    //escreve o vetor de bytes no "recurso" de envio 
    envioServ.write(b);
    //marca a finalização da escrita
    envioServ.flush();
</pre>

É claro que apenas isso não basta pois somente estamos enviando a requisição certo?, então precisaremos ler o InputStream logo após enviar os dados para ver o que o servidor responde, vamos facilitar as coisas afinal isto não é C, para ler o que o servidor responde vamos utilizar um Scanner, que ja faz a conversão o Input de bytes para String, assim a gente não tem que tratar esses trecos.

<pre class="lang-javascript">//cria um scanner a partir do InputStream que vem do servidor
    Scanner sc = new Scanner(socket.getInputStream());
    //enquanto houver algo para ler
    while (sc.hasNext()) {
        //imprime uma linha da resposta
        System.out.println(sc.nextLine());
    }
</pre>

Agora se executarmos o programa podemos ler o que o servidor nos devolve e exibir na tela, logo teremos um resultado parecido com isso

<pre class="lang-bash">$ javac Cliente.java 
$ java Cliente
Conectado a google.com.br/173.194.118.151 
HTTP/1.1 200 OK
Date: Tue, 17 Jun 2014 23:29:57 GMT
Expires: -1
Cache-Control: private, max-age=0
Content-Type: text/html; charset=ISO-8859-1
Set-Cookie: PREF=ID=fee5bb44e3822528:FF=0:TM=1403047797:LM=1403047797:S=BpVMDbzBHKUgdlRS; expires=Thu, 16-Jun-2016 23:29:57 GMT; path=/; domain=.google.com.br
Set-Cookie: NID=67=CT9hDvtQnKCvGeox_lmn7IjB_gbZ6Z9m7YT2rM1LAw2hVDVbvas16qfTsH1Jc1TRhrynqE-j0fb3EPl_JvjttiV-kqVpJlYjmg7Qd_e8oHcnJM1L2xlHWtlKw2EcomUM; expires=Wed, 17-Dec-2014 23:29:57 GMT; path=/; domain=.google.com.br; HttpOnly
P3P: CP="This is not a P3P policy! See http://www.google.com/support/accounts/bin/answer.py?hl=en&answer=151657 for more info."
Server: gws
X-XSS-Protection: 1; mode=block
X-Frame-Options: SAMEORIGIN
Alternate-Protocol: 80:quic
Transfer-Encoding: chunked

8000
&lt;!doctype html&gt;&lt;html[...]um monte de HTML[...]

0
</pre>

Veja que o resultado é semelhante ao que vimos anteriormente sobre na nossa teoria de requisição e resposta, também há algumas outras propriedade que não vimos mas não importa para nós ao menos que queira se aprofundar no assunto. Veja também que seu programa também continua em execução, isso acontece porque o servidor do google ainda não encerrou a conexão, isso acontece porque no HTTP/1.1 a propriedade &#8220;Connection: keep-alive&#8221; é padrão mesmo que não enviamos na requisição, quem define esse tempo é o próprio servidor, por experiência própria eu sei que a conexão com o google se mantém ativa por aproximadamente 3 minutos, isso para dar tempo suficiente para que você faça todas as pesquisas sem ter que criar uma nova conexão para cada pesquisa que você faz, isso é importante no caso do google já que ele recebe milhares de requisições por segundo, sendo que varias delas são feitas pela mesma pessoa, então não convém criar uma nova conexão para cada nova requisição.

Você deve estar se perguntando, mas Thiago, isso não é o que o navegador faz?

&#8211; Sim, o que fizemos hoje foi implementar a parte mais básica de um navegados web.

Mas a proposta é fazer um servidor e não um navegador, certo?

&#8211; Certo, mas antes de avançarmos é importante entender bem qual é o trabalho do navegador antes de criar o servidor que irá responder as requisições dele, mas isso será assunto para a parte III.

Posso fazer em outra linguagem?

&#8211; Claro, socket é implementado em todas as linguagens, basta consultar a documentação da sua linguagem preferida para entender como replicar o conceito acima.

Por hoje ficamos por aqui pessoal, espero que tenham aproveitado bem nossa parte prática, no próximo começaremos definitivamente a criar nosso servidor.

Até Mais.

 [1]: http://tableless.com.br/criando-seu-proprio-servidor-http-do-zero-ou-quase-parte-i/ "Criando seu próprio servidor HTTP do zero (ou quase) – Parte I"
 [2]: http://www.raywenderlich.com/uploads/2011/06/sockets.jpg
 [3]: http://google.com.br