---
title: Criando seu próprio servidor HTTP do zero (ou quase) – Parte Final
author: thiguetta
type: post
date: 2015-10-27
excerpt: Na última parte deste tutorial, aprenda sobre threads e como transformar seu servidor para receber múltiplas conexões.
url: /criando-seu-proprio-servidor-http-do-zero-ou-quase-parte-final/
categories:
  - Back-end
  - Browsers
  - Código
  - Geral
  - HTML
  - HTML5
  - Java
tags:
  - http
  - java
  - server

---
Os servidores HTTP são parte fundamental da Web como conhecemos, sendo responsáveis por fornecer todo o conteúdo que acessamos através de nossos navegadores. Durante esse tutorial, entenderemos como funciona a comunicação entre o navegador e o servidor e como a informação é entregue ao usuário.

Caso não tenha acompanhado os últimos posts, recomendo que leia as Partes [um][1], [dois][2] e [três][3] antes de prosseguir a leitura deste post.

Essa é a última parte do tutorial, mas antes de prosseguir vamos recapitular o que vimos até agora então: Nós conhecemos o protocolo HTTP/1.1, qual o padrão de requisição e resposta, entendemos um pouco de _sockets_ e por fim montamos um mini servidor que recebe requisições HTTP, e devolve a página solicitada.

É claro que nosso servidor não é perfeito, além da função _main_ ter ficado gigante, nosso servidor só responde a uma requisição e para! O ideal é que o servidor permaneça em execução para receber novas requisições e também possa receber várias requisições simultâneas, afinal de contas é para isso que um servidor web serve =D

## Organizando o código

Pra ficar simples, vamos separar a requisição da resposta em duas classes diferentes que vou chamar de RequisicaoHTTP e RespostaHTTP

RequisicaoHTTP.java

<pre>import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStream;
import java.io.InputStreamReader;
import java.util.Arrays;
import java.util.List;
import java.util.Map;
import java.util.TreeMap;

public class RequisicaoHTTP {

    private String protocolo;
    private String recurso;
    private String metodo;
    private boolean manterViva = true;
    private long tempoLimite = 3000;
    private Map&lt;String, List&gt; cabecalhos;

    public static RequisicaoHTTP lerRequisicao(InputStream entrada) throws IOException {
        RequisicaoHTTP requisicao = new RequisicaoHTTP();
        BufferedReader buffer = new BufferedReader(new InputStreamReader(entrada));
        System.out.println("Requisição: ");
        /* Lê a primeira linha
         contem as informaçoes da requisição
         */
        String linhaRequisicao = buffer.readLine();
        //quebra a string pelo espaço em branco
        String[] dadosReq = linhaRequisicao.split(" ");
        //pega o metodo
        requisicao.setMetodo(dadosReq[0]);
        //paga o caminho do arquivo
        requisicao.setRecurso(dadosReq[1]);
        //pega o protocolo
        requisicao.setProtocolo(dadosReq[2]);
        String dadosHeader = buffer.readLine();
        //Enquanto a linha nao for nula e nao for vazia
        while (dadosHeader != null && !dadosHeader.isEmpty()) {
            System.out.println(dadosHeader);
            String[] linhaCabecalho = dadosHeader.split(":");
            requisicao.setCabecalho(linhaCabecalho[0], linhaCabecalho[1].trim().split(","));
            dadosHeader = buffer.readLine();
        }
        //se existir a chave Connection no cabeçalho
        if (requisicao.getCabecalhos().containsKey("Connection")) {
            //seta o manterviva a conexao se o connection for keep-alive
            requisicao.setManterViva(requisicao.getCabecalhos().get("Connection").get(0).equals("keep-alive"));
        }
        return requisicao;
    }

    public void setCabecalho(String chave, String... valores) {
        if (cabecalhos == null) {
            cabecalhos = new TreeMap&lt;&gt;();
        }
        cabecalhos.put(chave, Arrays.asList(valores));
    }

    //getters e setters vão aqui
}
</pre>

Veja que simplesmente copiei a parte onde liamos a requisição e imprimíamos na tela, dentro de um método estático lerRequisicao() que retorna um objeto RequisicaoHTTP. Perceba ainda que esse método recebe o InputStream de onde iremos ler a requisição como parâmetro. Além do mais iremos colocar os dados do cabeçalho em um Mapa<chave,valor> para facilitar o manuseio desses dados posteriormente caso seja necessário.

Até o momento os únicos dados que utilizávamos da requisição era a primeira linha que contém o caminho do arquivo, a partir de agora vamos usar o Connection (se existir) para saber se manteremos a conexão viva ou não, veja que há uma propriedade tempoLimite que por padrão é 3000 milissegundos (3 segundos), que vamos utilizar para controlar quanto tempo uma conexão deve permanecer ativa. O resto é só você implementar (os métodos _getters_ e _setters_ eu omiti).

RespostaHTTP.java

<pre>import java.io.IOException;
import java.io.OutputStream;
import java.util.Arrays;
import java.util.List;
import java.util.Map;
import java.util.TreeMap;

public class RespostaHTTP {

    private String protocolo;
    private int codigoResposta;
    private String mensagem;
    private byte[] conteudoResposta;
    private Map&lt;String, List&gt; cabecalhos;
    private OutputStream saida;

    public RespostaHTTP() {

    }

    public RespostaHTTP(String protocolo, int codigoResposta, String mensagem) {
        this.protocolo = protocolo;
        this.codigoResposta = codigoResposta;
        this.mensagem = mensagem;
    }

    /**
     * Envia os dados da resposta ao cliente.
     *
     * @throws IOException
     */
    public void enviar() throws IOException {
        //escreve o headers em bytes
        saida.write(montaCabecalho());
        //escreve o conteudo em bytes
        saida.write(conteudoResposta);
        //encerra a resposta
        saida.flush();
    }

    /**
     * Insere um item de cabeçalho no mapa
     *
     * @param chave
     * @param valores lista com um ou mais valores para esta chave
     */
    public void setCabecalho(String chave, String... valores) {
        if (cabecalhos == null) {
            cabecalhos = new TreeMap&lt;&gt;();
        }
        cabecalhos.put(chave, Arrays.asList(valores));
    }

    /**
     * pega o tamanho da resposta em bytes
     *
     * @return retorna o valor em bytes do tamanho do conteudo da resposta
     * convertido em string
     */
    public String getTamanhoResposta() {
        return getConteudoResposta().length + "";
    }

    /**
     * converte o cabecalho em string.
     *
     * @return retorna o cabecalho em bytes
     */
    private byte[] montaCabecalho() {
        return this.toString().getBytes();
    }

    @Override
    public String toString() {
        StringBuilder str = new StringBuilder();
        str.append(protocolo).append(" ").append(codigoResposta).append(" ").append(mensagem).append("\r\n");
        for (Map.Entry&lt;String, List&gt; entry : cabecalhos.entrySet()) {
            str.append(entry.getKey());
            String stringCorrigida = Arrays.toString(entry.getValue().toArray()).replace("[", "").replace("]", "");
            str.append(": ").append(stringCorrigida).append("\r\n");
        }
        str.append("\r\n");
        return str.toString();
    }
}
</pre>

Veja que para a resposta utilizamos o mesmo conceito, estamos montando o cabeçalho na requisição em um Mapa<chave, valor>, criei também outros métodos para auxiliar na geração dos dados pertinentes ao cabeçalho, e sobrescrevi o método toString() para converter o mapa no formato padrão da resposta HTTP, e por fim, o método enviar para enviar a requisição ao servidor.

Servidor.java

<pre>import java.io.File;
import java.io.IOException;
import java.net.ServerSocket;
import java.net.Socket;
import java.nio.file.Files;
import java.util.Date;

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
            System.out.println(socket.getInetAddress());
            //cria um BufferedReader a partir do InputStream do cliente

            RequisicaoHTTP requisicao = RequisicaoHTTP.lerRequisicao(socket.getInputStream());

            //se o caminho foi igual a / entao deve pegar o /index.html
            if (requisicao.getRecurso().equals("/")) {
                requisicao.setRecurso("index.html");
            }
            //abre o arquivo pelo caminho
            File arquivo = new File(requisicao.getRecurso().replaceFirst("/", ""));

            RespostaHTTP resposta;

            //se o arquivo existir então criamos a reposta de sucesso, com status 200
            if (arquivo.exists()) {
                resposta = new RespostaHTTP(requisicao.getProtocolo(), 200, "OK");
            } else { 
                //se o arquivo não existe então criamos a reposta de erro, com status 404
                resposta = new RespostaHTTP(requisicao.getProtocolo(), 404, "Not Found");
            }
            //lê todo o conteúdo do arquivo para bytes e gera o conteudo de resposta
            resposta.setConteudoResposta(Files.readAllBytes(arquivo.toPath()));
            //converte o formato para o GMT espeficicado pelo protocolo HTTP
            String dataFormatada = Util.formatarDataGMT(new Date());
            //cabeçalho padrão da resposta HTTP/1.1
            resposta.setCabecalho("Location", "http://localhost:8000/");
            resposta.setCabecalho("Date", dataFormatada);
            resposta.setCabecalho("Server", "MeuServidor/1.0");
            resposta.setCabecalho("Content-Type", "text/html");
            resposta.setCabecalho("Content-Length",resposta.getTamanhoResposta());
            //cria o canal de resposta utilizando o outputStream
            resposta.setSaida(socket.getOutputStream());
            resposta.enviar();

        }
    }
}

</pre>

Agora o código do nosso servidor está pequeno mas ainda não é o suficiente &#8211; continua recebendo uma requisição e respondendo apenas uma vez. Vamos ver mais um conceito:

## Threads

As _threads_, de maneira geral, são segmentos de código que são executados &#8220;paralelamente&#8221; (ou pelo menos quase) dentro de um mesmo programa. Para exemplificar melhor, pense nisso: imagine que ao abrir um software de grandes proporções, ele tenha que carregar todas as bibliotecas necessárias, mas ao mesmo tempo tem que mostrar ao usuário o progresso do carregamento. A ideia que temos é que esses dois trechos de código são executados paralelamente. Isso é possível graças às _threads._ Neste exemplo, temos duas _threads_ executando: uma que carrega as bibliotecas e outra que mostra o progresso para o usuário. Dentro de um programa, pode-se ter quantas threads quisermos, e enquanto o programa estiver executando, essas _threads_ podem ser criadas, executadas, terminadas, permitir que novas _threads_ e outros. Quem faz esse controle é a máquina virtual (JVM).

Olha que legal, um servidor recebe várias conexões simultâneas, onde por essas conexões passarão as requisições. Praticamente, todas essas requisições são processadas da mesma maneira, logo, para cada conexão que esse servidor recebe, ele cria uma nova _thread_, permitindo tratar as requisições de um cliente. Veja só, se temos 5 computadores solicitando uma página, então teremos 5 threads processando essas requisições, e por aí vai.

Agora fica fácil analisar qual segmento do código queremos executar paralelamente. A partir desse segmento iremos montar uma estrutura de Thread, da seguinte maneira:

ThreadConexao.java

<pre>import java.io.File;
import java.io.IOException;
import java.net.Socket;
import java.net.SocketTimeoutException;
import java.nio.file.Files;
import java.util.Date;
import java.util.logging.Level;
import java.util.logging.Logger;

public class ThreadConexao implements Runnable {

    private final Socket socket;
    private boolean conectado;

    public ThreadConexao(Socket socket) {
        this.socket = socket;
    }

    @Override
    public void run() {
        conectado = true;
        //imprime na tela o IP do cliente
        System.out.println(socket.getInetAddress());
        while (conectado) {
            try {
                //cria uma requisicao a partir do InputStream do cliente
                RequisicaoHTTP requisicao = RequisicaoHTTP.lerRequisicao(socket.getInputStream());
                //se a conexao esta marcada para se mantar viva entao seta keepalive e o timeout
                if (requisicao.isManterViva()) {
                    socket.setKeepAlive(true);
                    socket.setSoTimeout(requisicao.getTempoLimite());
                } else {
                    //se nao seta um valor menor suficiente para uma requisicao
                    socket.setSoTimeout(300);
                }

                //se o caminho foi igual a / entao deve pegar o /index.html
                if (requisicao.getRecurso().equals("/")) {
                    requisicao.setRecurso("index.html");
                }
                //abre o arquivo pelo caminho
                File arquivo = new File(requisicao.getRecurso().replaceFirst("/", ""));

                RespostaHTTP resposta;

                //se o arquivo existir então criamos a reposta de sucesso, com status 200
                if (arquivo.exists()) {
                    resposta = new RespostaHTTP(requisicao.getProtocolo(), 200, "OK");
                } else {
                    //se o arquivo não existe então criamos a reposta de erro, com status 404
                    resposta = new RespostaHTTP(requisicao.getProtocolo(), 404, "Not Found");
                    arquivo = new File("404.html");
                }
                //lê todo o conteúdo do arquivo para bytes e gera o conteudo de resposta
                resposta.setConteudoResposta(Files.readAllBytes(arquivo.toPath()));
                //converte o formato para o GMT espeficicado pelo protocolo HTTP
                String dataFormatada = Util.formatarDataGMT(new Date());
                //cabeçalho padrão da resposta HTTP/1.1
                resposta.setCabecalho("Location", "http://localhost:8000/");
                resposta.setCabecalho("Date", dataFormatada);
                resposta.setCabecalho("Server", "MeuServidor/1.0");
                resposta.setCabecalho("Content-Type", "text/html");
                resposta.setCabecalho("Content-Length", resposta.getTamanhoResposta());
                //cria o canal de resposta utilizando o outputStream
                resposta.setSaida(socket.getOutputStream());
                resposta.enviar();
            } catch (IOException ex) {
                //quando o tempo limite terminar encerra a thread
                if (ex instanceof SocketTimeoutException) {
                    try {
                        conectado = false;
                        socket.close();
                    } catch (IOException ex1) {
                        Logger.getLogger(ThreadConexao.class.getName()).log(Level.SEVERE, null, ex1);
                    }
                }
            }

        }
    }

}
</pre>

A estrutura de uma _thread_ é bem simples: uma classe que implementa a interface Runnable. Essa interface possui um único método a ser implementado, o método run(). Esse método é o nosso segmento de código que queremos que seja executado em paralelo. Veja que nele temos o código que tínhamos na _main_ com apenas algumas modificações para controlar o tempo máximo de conexão (o tempo que a conexão deve se manter ativa).

## ThreadPools

Por fim, temos que falar um pouco sobre as Thread Pools, que tem o trabalho de controlar a criação de _threads_. Claro que podemos criar quantas _threads_ quisermos, mas, às vezes, a situação requer um certo controle, ainda mais quando um servidor web pode receber milhares ou até milhões de requisições por segundo. Por isso, precisamos gerenciar essas _threads_ de maneira eficiente, para que nosso servidor não sobrecarregue. Para isso, o Java tem os Executors, que criam um ambiente de execução de múltiplas _threads_. Existem diversos tipos de ExecutorService. No nosso caso, iremos utilizar o fixo, que significa limitarmos a criação de _threads_ a um número fixo. Se o número de _threads_ criadas exceder o limite, essas novas _threads_ deverão aguardar até que as outras _threads_ terminem para começar a executar. Com isso, nossa classe Servidor passa a ficar da seguinte forma:

Servidor.java

<pre>import java.io.IOException;
import java.net.ServerSocket;
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;

public class Servidor {

    public static void main(String[] args) throws IOException {
        /* cria um socket "servidor" associado a porta 8000
         já aguardando conexões
         */
        ServerSocket servidor = new ServerSocket(8000);
        //executor que limita a criação de threads a 20
        ExecutorService pool = Executors.newFixedThreadPool(20);
        
        while (true) {
            //cria uma nova thread para cada nova solicitacao de conexao
            pool.execute(new ThreadConexao(servidor.accept()));
        }
    }
}
</pre>

Veja que agora colocamos a criação de novas _threads_ while(true). Isso impede que nosso servidor pare de executar após a primeira requisição, permitindo que ele aceite múltiplas conexões. Você deve estar a se perguntar &#8211; mas um _while true_ não gera um laço infinito? &#8211; de certa forma sim, mas para a nossa situação esta é a ideia, já que não queremos que o servidor pare, e que o servidor só finalize quando o usuário enviar o comando CTRL+C no prompt/terminal. De qualquer forma, o método accept() é bloqueado até que receba uma nova conexão, e esse laço sé será executado quando houver uma solicitação, caso contrário, ficará parado num estado de bloqueio =D

Pronto. Agora temos um servidor funcional que aceita conexões múltiplas e responde a muitas requisições.

## Considerações finais

Nosso servidor está longe de ser uma versão completa para competir com o Apache e outros servidores HTTP, até por que nosso servidor só envia documentos HTML. Vale lembrar que, quando o navegador recebe um HTML como resposta, ele tem que renderizá-lo, e ao fazer isto, ele encontra tags de arquivos de imagem, áudio, scripts ou estilos, o que gera outras requisições para o servidor, para que ele envie também esses arquivos. O código ainda pode ser melhorado, teríamos que fazer com que o servidor forneça o Content-Type correto para cada tipo de arquivo (o que não é difícil, fica como exercício). Também seria necessário implementar uma camada de segurança (o que hoje em dia é fundamental, pois sem ela nosso servidor está completamente vulnerável a ataques), e por aí vai.

Além do mais, nosso servidor responde ao padrão HTTP/1.1, mas recentemente foi lançado o protocolo HTTP2, que veio para tornar o antigo padrão ainda mais rápido. Embora tenha sofrido alterações internas (o que significa que os servidores HTTP terão que se &#8220;adaptar&#8221; para seguirem esse novo padrão), o conceito continua o mesmo. Você pode ler um pouco mais sobre HTTP2 nesse post [&#8220;HTTP/2 – Atualização do protocolo base da internet&#8221;][4] e nesse [&#8220;HTTP2 para Desenvolvedores de Web&#8221;][5].

Espero ter despertado em vocês a vontade de conhecer mais a fundo como as coisas funcionam, para criarem suas próprias contribuições e compartilharem com a galera, afinal, esse é o espirito do Tableless.

Por favor, deixem comentários, se gostaram ou não, erros, dúvidas. O feedback de vocês é importante.

Até a próxima =D

&nbsp;

## Referências:

**Lições sobre socket (em inglês):** <a title="http://www.oracle.com/technetwork/java/socket-140484.html" href="http://www.oracle.com/technetwork/java/socket-140484.html" target="_blank">http://www.oracle.com/technetwork/java/socket-140484.html</a>

**Java Tutorial Tudo sobre sockets (em inglês):** <a title="http://docs.oracle.com/javase/tutorial/networking/sockets/" href="http://docs.oracle.com/javase/tutorial/networking/sockets/" target="_blank">http://docs.oracle.com/javase/tutorial/networking/sockets/</a>

**RFC2616 (em inglês):** <a title="http://www.w3.org/Protocols/rfc2616/rfc2616.html" href="http://www.w3.org/Protocols/rfc2616/rfc2616.html" target="_blank">http://www.w3.org/Protocols/rfc2616/rfc2616.html</a>

**Código**** Fonte Completo:** <a title="Repo MeuServidorHTTP" href="https://github.com/thiguetta/MeuServidorHTTP" target="_blank">https://github.com/thiguetta/MeuServidorHTTP</a>

**Versão alternativa que fornece arquivos de imagem, javascript e css também:** <a title="Repo SimpleHTTPServer" href="https://github.com/thiguetta/SimpleHTTPServer" target="_blank">https://github.com/thiguetta/SimpleHTTPServer</a>

 [1]: http://tableless.com.br/criando-seu-proprio-servidor-http-do-zero-ou-quase-parte-i/
 [2]: http://tableless.com.br/criando-seu-proprio-servidor-http-do-zero-ou-quase-parte-ii/
 [3]: http://tableless.com.br/criando-seu-proprio-servidor-http-do-zero-ou-quase-parte-iii/
 [4]: http://tableless.com.br/http2-atualizacao-do-protocolo-base-da-internet/
 [5]: http://tableless.com.br/http2-para-desenvolvedores-de-web/