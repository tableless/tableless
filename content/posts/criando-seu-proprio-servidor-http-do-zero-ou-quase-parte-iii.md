---
title: Criando seu próprio servidor HTTP do zero (ou quase) – Parte III
author: thiguetta
type: post
date: 2015-10-05
url: /criando-seu-proprio-servidor-http-do-zero-ou-quase-parte-iii/
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
Estamos entrando na terceira parte do tutorial, e quem está acompanhando até aqui já sabe então como funciona a comunicação entre cliente e servidor, envio de requisição pelo cliente e recebimento de resposta (na duvida só voltar e releia a [Parte I][1] e/ou [Parte II][2]), porém o que a gente quer é criar o servidor, receber as requisições e enviar a resposta ao cliente.

## O Servidor

A idéia do servidor é bem simples e estende a do cliente, como assim? Fácil, fácil. no post anterior vimos como criar um socket, no caso, nos criamos um socket já conectado ao site do google, mas o que internamente acontece é, criamos um socket, associamos esse socket a uma porta (lembrando que no caso do cliente a porta aberta é aleatória, so para que o servidor saiba onde deve retornar a resposta) e conectamos ao socket do servidor na porta especifica.

<p style="text-align: justify">
  Agora vamos pensar um pouco, no caso do servidor, temos que criar um socket, associar (bind) a uma porta especifica(para que todos os clientes saibam exatamente onde conectar) e ficamos aguardando alguém solicitar uma conexão (listen), se alguém solicitar conexão nós aceitamos (accept), resumindo o processo, temos como na imagem abaixo:
</p>

<div style="width: 369px" class="wp-caption aligncenter">
  <a href="http://3.bp.blogspot.com/_Gt5b2CU22sM/S4iS4lbeU5I/AAAAAAAAAUU/DBmariOce1o/s400/rzab6503.gif"><img src="http://3.bp.blogspot.com/_Gt5b2CU22sM/S4iS4lbeU5I/AAAAAAAAAUU/DBmariOce1o/s400/rzab6503.gif" alt="" width="359" height="324" /></a>
  
  <p class="wp-caption-text">
    Diagrama Cliente/Servidor
  </p>
</div>

Em Java já temos uma classe pronta que faz isso, que é o ServerSocket, que já cria um socket que está aguardando conexões, o que torna nossa vida bem mais simples, então vamos parar de teoria e ir pro código, para isso criamos uma classe chamada Servidor e nela faremos o seguinte:

<pre>import java.io.IOException;
import java.net.ServerSocket;
import java.net.Socket;

public class Servidor {

    public static void main(String[] args) throws IOException {
        /* cria um socket "servidor" associado a porta 8000
          já aguardando conexões
        */
        ServerSocket servidor = new ServerSocket(8000);
        //aceita a primeita conexao que vier
        Socket socket = servidor.accept();
        //verifica se esta conectado  
        if (socket.isConnected()) {
            //imprime na tela o IP do cliente
            System.out.println("O computador "+ socket.getInetAddress() + " se conectou ao servidor.");
        }
    }
}
</pre>

Veja que estamos abrindo a porta 8000 e não a 80, isso por que embora essa seja a porta &#8220;destinada/utilizada&#8221; para servidores HTTP, ela é gerenciada pelo sistema operacional então não poderemos abri-la por enquanto (o SO não permitiria até por que em alguns sistemas linux já existe um servidor HTTP utilizando essa porta, em outros a porta está bloqueada pelo firewall, e teremos que abri-la manualmente mas veremos isso em breve), por isso vamos utilizar outra porta para testes, vamos compilar esse código e coloca-lo em execução, veja que ele permanecerá em execução até que ele receba pelo menos uma solicitação de conexão, que é o que vamos fazer, assim basta abrir o navegador e digitar o endereço http://localhost:8000 e ir para a página, veja que ao fazer isso sua linha de comando aparecerá a frase:

<pre>java Server
O computador /0:0:0:0:0:0:0:1 se conectou ao servidor.</pre>

Veja  que este é o endereço IP do seu computador já no formato IPv6.  Note  que logo em seguida o programa foi finalizado, isso porque nosso servidor não está configurado para múltiplas conexões/requisições, porém vamos fazer isso já já, agora vamos ver qual foi a requisição que nosso navegador fez ao servidor, e para ler a entrada o conceito é o mesmo de ontem, vamos usar o InputStream para ler os dados enviados pelo cliente, então vamos adicionar o seguinte código logo após imprimir o IP:

<pre>[...]
            //cria um BufferedReader a partir do InputStream do cliente
            BufferedReader buffer = new BufferedReader(new InputStreamReader(socket.getInputStream()));
            System.out.println("Requisição: ");
            //Lê a primeira linha
            String linha = buffer.readLine();
            //Enquanto a linha não for vazia
            while (!linha.isEmpty()) {
                //imprime a linha
                System.out.println(linha);
                //lê a proxima linha
                linha = buffer.readLine();
            }
[...]
</pre>

Veja que agora utilizamos um BufferedReader ao invés do Scanner, isto por que o Scanner mesmo após ter terminado de ler a requisição ele espera que a a conexão seja encerrada, a fim de aguardar novas entradas, mas como não é interessante para gente esperar,  vamos usar o Buffer pois podemos verificar se a linha for vazia, se for, simplesmente encerra o programa sem ter que aguardar que a conexão seja encerrada. (Caso seja necessário continuar lendo a entrada antes da conexão encerras é so pegar o InputReader novamente e continuar lendo. Agora ao executarmos nosso servidor,  e acessar a página localhost:8000 no navegador teremos a seguinte saída na linha de comando:

<pre>java Server
O computador /0:0:0:0:0:0:0:1 se conectou ao servidor.
Requisição: 
GET / HTTP/1.1
Host: localhost:8000
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10.9; rv:29.0) Gecko/20100101 Firefox/29.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: pt-BR,pt;q=0.8,en-US;q=0.5,en;q=0.3
Accept-Encoding: gzip, deflate
DNT: 1
Connection: keep-alive</pre>

Veja que minha requisição foi originada de um navegador Firefox e que o formato da requisição é muito semelhante do que vimos na primeira parte do tutorial =D. Agora é so fazer o servidor tratar essas informações e devolver uma resposta ao cliente, nesse caso vamos devolver uma página HTML que é o que o navegador espera. Vamos criar duas páginas uma chamada índex.html e outra 404.html, e vamos armazena-las na mesma pasta que está colocando o código fonte do servidor com os seguintes códigos:

Arquivo index.html

# Funcionou!!!!

Arquivo 404.html

<pre>Erro 404</pre>

# A página que você procura não foi encontrada

Por convenção quando alguém solicita o arquivo &#8220;/&#8221; está solicitando a pagina inicial que geralmente é o índex.html, dependendo da configuração do servidor, no nosso caso queremos que nosso servidor retorne o índex.html, se o usuário pedir por qualquer coisa no formato &#8220;/{nome da pagina}.html&#8221; retornaremos esse arquivo, caso o arquivo não exista, retornaremos o erro 404 e a página de erro correspondente.

Sabemos que a primeira linha da requisição contem o método, o arquivo solicitado e o protocolo separados por um espaço em branco, para o nosso servidor o método não importa, então assumiremos sempre o GET, e o protocolo será sempre o HTTP/1.1, então o que nos importa é o arquivo solicitado. Vamos alterar o nosso código que deve ficar assim:

<pre>[...]
            /* Lê a primeira linha
             contem as informaçoes da requisição
             */
            String linha = buffer.readLine();
            //quebra a string pelo espaço em branco
            String[] dadosReq = linha.split(" ");
            //pega o metodo
            String metodo = dadosReq[0];
            //paga o caminho do arquivo
            String caminhoArquivo = dadosReq[1];
            //pega o protocolo
            String protocolo = dadosReq[2];
            //Enquanto a linha não for vazia
            while (!linha.isEmpty()) {
                //imprime a linha
                System.out.println(linha);
                //lê a proxima linha
                linha = buffer.readLine();
            }
            //se o caminho foi igual a / entao deve pegar o /index.html
            if (caminhoArquivo.equals("/")) {
                caminhoArquivo = "/index.html";
            }
            //abre o arquivo pelo caminho
            File arquivo = new File(caminhoArquivo);
            byte[] conteudo;
            //status de sucesso - HTTP/1.1 200 OK
            String status = protocolo + " 200 OK\r\n";
            //se o arquivo não existe então abrimos o arquivo de erro, e mudamos o status para 404
            if (!arquivo.exists()) {
                status = protocolo + " 404 Not Found\r\n";
                arquivo = new File("/404.html");
            }
            conteudo = Files.readAllBytes(arquivo.toPath());
[...]
</pre>

Veja que ainda não respondemos ao navegados com os dados, apenas montamos uma parte da resposta, para enviar a resposta precisaremos do OutputStream e montar uma string com a estrutura básica da resposta, dai vamos escrever esses dados no stream, semelhante ao que fizemos na parte II do nosso tutorial:

<pre>//cria um formato para o GMT espeficicado pelo HTTP
            SimpleDateFormat formatador = new SimpleDateFormat("E, dd MMM yyyy hh:mm:ss", Locale.ENGLISH);
            formatador.setTimeZone(TimeZone.getTimeZone("GMT"));
            Date data = new Date();
            //Formata a dara para o padrao
            String dataFormatada = formatador.format(data) + " GMT";
            //cabeçalho padrão da resposta HTTP
            String header = status
                    + "Location: http://localhost:8000/\r\n"
                    + "Date: " + dataFormatada + "\r\n"
                    + "Server: MeuServidor/1.0\r\n"
                    + "Content-Type: text/html\r\n"
                    + "Content-Length: " + conteudo.length + "\r\n"
                    + "Connection: close\r\n"
                    + "\r\n";
            //cria o canal de resposta utilizando o outputStream
            OutputStream resposta = socket.getOutputStream();
            //escreve o headers em bytes
            resposta.write(header.getBytes());
            //escreve o conteudo em bytes
            resposta.write(conteudo);
            //encerra a resposta
            resposta.flush();
</pre>

Agora é só compilar, rodar e ver o resultado =D

No caso de sucesso deve aparecer como na figura abaixo:

[<img class="alignnone size-full wp-image-51391" src="http://tableless.com.br/uploads/2015/09/sucesso.png" alt="200 - Sucesso" width="1279" height="707" />][3]

Caso a página não existe, deve aparecer assim:

[<img class="alignnone size-full wp-image-51392" src="http://tableless.com.br/uploads/2015/09/erro404.png" alt="Erro 404" width="1280" height="709" />][4]

Temos um servidor funcional capaz de fornecer as páginas HTML para os clientes que solicitarem, mas perceba que nosso servidor atende a apenas uma requisição e se encerra logo em seguida, sem contar que nosso método main ficou gigante, mas fique tranquilo, isso será assunto para a próxima e ultima parte do tutorial, onde vamos organizar melhor nosso código, tratar alguns comandos do servidor importantes como manter a conexão viva e trabalhar com múltiplas requisições, conexões simultâneas e afins. Por hora fica o exercício, tente organizar o código a sua maneira, altere como desejar, crie mais páginas HTML e teste e veja se está sendo exibida corretamente, todo código feito até aqui está no final da página e está todo comentado para facilitar o entendimento.

Espero que estejam gostando e por favor deixem comentários com seu feedback: o que achou, dúvidas, se funcionou ou não, se a abordagem não estiver adequada ou mesmo erros que posso ter cometido pelo caminho.

Até o próximo post.

Download do código fonte: <a href="https://github.com/thiguetta/ServidorHTTP" target="_blank">https://github.com/thiguetta/ServidorHTTP</a>

 [1]: http://tableless.com.br/criando-seu-proprio-servidor-http-do-zero-ou-quase-parte-i/ "Criando seu próprio servidor HTTP do zero (ou quase) – Parte I"
 [2]: http://tableless.com.br/criando-seu-proprio-servidor-http-do-zero-ou-quase-parte-ii/ "Criando seu próprio servidor HTTP do zero (ou quase) – Parte II"
 [3]: http://tableless.com.br/uploads/2015/09/sucesso.png
 [4]: http://tableless.com.br/uploads/2015/09/erro404.png