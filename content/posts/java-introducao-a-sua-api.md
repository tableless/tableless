---
title: JAVA – Introdução a sua API
author: Fellipe Filgueiras
type: post
date: 2015-05-18
url: /java-introducao-a-sua-api/
categories:
  - Geral
  - Java
tags:
  - java

---
A API do Java é composta por dois tipos de recursos distintos: classes e interfaces. Ela é como um bloco dividido em duas grandes partes, são centenas de Interfaces e milhares de classes que acompanham o kit de desenvolvimento do Java e que podem ser empregadas para a realização de diversos tipos de tarefas durante a construção de um programa.

Na API do Java, não existem métodos ou quaisquer tipos de dados desgarrados. O seu caráter fortemente orientado a objetos obriga a declaração de todos os métodos dentro de uma classe ou de uma interface. Do mesmo modo, não é possível declarar uma variável ou constante fora do escopo de uma classe ou de uma interface. A representação de dados deve ser feita, necessariamente, através de atributos que pertencem a uma classe ou interface específica.

As classes formam uma hierarquia dentro da API do Java, e a classe java.lang.Object é a raiz dessa hierarquia. Direta ou indiretamente, toda classe tem Object como a sua superclasse, assim, todos os métodos por ela implementados são herdados por todas as demais classes.

**Organização**

As classes e interfaces que compõem a API do Java estão divididas em pacotes, e cada pacote agrupa um conjunto de classes e interfaces que possuem propósitos comuns. Lembre-se de que um pacote também pode conter outros pacotes, de modo que eles acabam formando uma estrutura complexa de compartimentos.

A estrutura dos pacotes que abriga as classes e interfaces de Java reflete apenas a estrutura de diretórios onde os seus arquivos compilados estão dispostos. Mas, na verdade, as classes e interfaces do JDK não estão armazenadas em uma estrutura de diretórios que tenha sido criada efetivamente. Elas se encontram em um arquivo compactado chamado rt.jar, que se encontra no diretório: \jre\lib.

Assim como a localização de um arquivo no disco rígido compõe-se da identificação de todos os diretórios e subdiretórios e de seu nome, a localização de uma classe ou interface compõe-se da identificação do pacote raiz, de todos os sub pacotes e de seu nome. A classe String, por exemplo, está localizada no pacote lang e este pacote está contido no pacote java. Desse modo, a localização da classe String é escrita do seguinte modo: java.lang.String.

**O pacote java**

O pacote que fora chamado de java contém os recursos fundamentais do Java. É nele que estão contidas as classes e interfaces essenciais à consecução dos seus desígnios enquanto linguagem de programação, e também recursos indispensáveis para a realização de tarefas extremamente importantes para a construção de quaisquer programas.

O pacote java divide-se em 13 pacotes, e cada um deles contém classes e interfaces distribuídas em diversos sub pacotes. Conhecer cada um dos milhares de componentes contidos nesse pacote é uma meta que exigira muito tempo e esforço, e não se justifica. O que importa não é dominar todos os recursos disponíveis nesse e nos outros pacotes, mas tão somente saber utilizar aquelas classes e interfaces que precisam ser aplicadas para construir determinado tipo de aplicação que você deseja desenvolver.

**Conteúdo do pacote java:**

<table>
  <tr>
    <td width="64">
      <strong>Pacote</strong>
    </td>
    
    <td width="512">
      <strong>Descrição</strong>
    </td>
  </tr>
  
  <tr>
    <td width="64">
      applet
    </td>
    
    <td width="512">
      Provê as classes necessárias para criar um applet e as classes que um applet usa para se comunicar com seu contexto.
    </td>
  </tr>
  
  <tr>
    <td width="64">
      awt
    </td>
    
    <td width="512">
      Contém classes e interfaces utilizadas para desenhar gráficos e imagens e construir GUIs.
    </td>
  </tr>
  
  <tr>
    <td width="64">
      beans
    </td>
    
    <td width="512">
      Contém classes relacionadas ao desenvolvimento de componentes beans baseados na arquitetura denominada como JavaBean.
    </td>
  </tr>
  
  <tr>
    <td width="64">
      io
    </td>
    
    <td width="512">
      Provê entrada e saída para o sistema através de fluxo, serialização e arquivos de sistema.
    </td>
  </tr>
  
  <tr>
    <td width="64">
      lang
    </td>
    
    <td width="512">
      Provê classes que são fundamentais ao desígnio de Java enquanto linguagem de programação.
    </td>
  </tr>
  
  <tr>
    <td width="64">
      math
    </td>
    
    <td width="512">
      Provê classes para executar aritmética de inteiros de precisão arbitrária e aritmética decimal de precisão.
    </td>
  </tr>
  
  <tr>
    <td width="64">
      net
    </td>
    
    <td width="512">
      Provê classes para implementação de aplicações de redes.
    </td>
  </tr>
  
  <tr>
    <td width="64">
      nio
    </td>
    
    <td width="512">
      Define “buffers”, que são recipientes para dados e proveem uma prévia dos outros pacotes NIO.
    </td>
  </tr>
  
  <tr>
    <td width="64">
      rmi
    </td>
    
    <td width="512">
      Provê classes e interfaces para implementar aplicativos que utilizem invocação remota de métodos (RMI – Remot Method Invocation.)
    </td>
  </tr>
  
  <tr>
    <td width="64">
      security
    </td>
    
    <td width="512">
      Provê classes e interfaces para implementar procedimentos de segurança de informações.
    </td>
  </tr>
  
  <tr>
    <td width="64">
      sql
    </td>
    
    <td width="512">
      Provê classes e interfaces para acessar a processar dados armazenados em uma fonte de dados, normalmente um banco de dados relacional.
    </td>
  </tr>
  
  <tr>
    <td width="64">
      text
    </td>
    
    <td width="512">
      Provê classes e interfaces para controlar texto, datas, números e mensagens de modo independente de idiomas naturais.
    </td>
  </tr>
  
  <tr>
    <td width="64">
      util
    </td>
    
    <td width="512">
      Contém a estrutura de coleções, modelo de eventos, facilidades com data e hora, internacionalização e classes de utilidades diversas.
    </td>
  </tr>
</table>

** **

**O pacote javax**

O pacote javax contém várias classes e interfaces que complementam aquelas dispostas no pacote java e outras que oferecem recursos totalmente novos. Em conjunto, esses dois pacotes são os recipientes onde se encontra a base de recursos da API do Java a ser utilizada para o desenvolvimento de uma enorme diversidade de programas.

**Parte do conteúdo do pacote javax:**

** **

<table>
  <tr>
    <td width="92">
      <strong>Pacote</strong>
    </td>
    
    <td width="484">
      <strong>Descrição</strong>
    </td>
  </tr>
  
  <tr>
    <td width="92">
      acessibility
    </td>
    
    <td width="484">
      Define um contrato entre componentes de interface do usuário e uma tecnologia que provê acesso a esses componentes.
    </td>
  </tr>
  
  <tr>
    <td width="92">
      imageio
    </td>
    
    <td width="484">
      Pacote principal de entrada e saída de imagem.
    </td>
  </tr>
  
  <tr>
    <td width="92">
      naming
    </td>
    
    <td width="484">
      Contém classes e interfaces para nomear acesso a serviços.
    </td>
  </tr>
  
  <tr>
    <td width="92">
      print
    </td>
    
    <td width="484">
      Contém as classes e interfaces principais para o serviço de impressão do Java.
    </td>
  </tr>
  
  <tr>
    <td width="92">
      rmi
    </td>
    
    <td width="484">
      Contém classes e interfaces adicionais para a implementação de invocação remota de métodos.
    </td>
  </tr>
  
  <tr>
    <td width="92">
      security
    </td>
    
    <td width="484">
      Provê uma estrutura para autenticação e autorização através de certificados e chaves públicas.
    </td>
  </tr>
  
  <tr>
    <td width="92">
      sound
    </td>
    
    <td width="484">
      Provê classes e interfaces para capturar, processamento e reprodução de áudio.
    </td>
  </tr>
  
  <tr>
    <td width="92">
      sql
    </td>
    
    <td width="484">
      Provê acesso a fonte de dados do lado do servidor.
    </td>
  </tr>
  
  <tr>
    <td width="92">
      swing
    </td>
    
    <td width="484">
      Provê um conjunto de componentes “leves” para a construção de GUIs que funcionam do mesmo modo em todas as plataformas.
    </td>
  </tr>
  
  <tr>
    <td width="92">
      transaction
    </td>
    
    <td width="484">
      Contém classes de exceção lançadas pelo Object Request Broker (ORB).
    </td>
  </tr>
  
  <tr>
    <td width="92">
      xml
    </td>
    
    <td width="484">
      Provê classes que permitem o processamento de documentos XML.
    </td>
  </tr>
</table>

&nbsp;

É claro que novos pacotes tendem a ser adicionados ao pacote javax no futuro, assim como podem ser adicionados ao pacote java ou os outros pacotes que definem a organização da API do Java. O próprio pacote javax não existia na primeira versão do Java, tendo sido desenvolvido e agregado posteriormente.

Nestes momentos, é preciso apenas ter em mente que a API do Java compõe-se de classes e interfaces organizadas em uma estrutura de pacotes. A descrição superficial dessas estruturas é suficiente, por enquanto, tendo em vista que recursos específicos serão analisados com maior riqueza de detalhes em momento oportuno.

**Recursos Essenciais**

Os recursos essenciais aos desígnios do Java estão contidos no pacote java.lang. É aí que se encontram os recursos necessários para a implementação de diversas das operações fundamentais que são realizadas para a construção de grandes diversidade de aplicações.

**Operações com Textos: A classe String**

Texto é qualquer expressão composta por um conjunto de caracteres, incluindo as letras do alfabeto, os números, sinais de pontuação e todos os demais caracteres reconhecidos pelo padrão Unicode. Qualquer sequência de caracteres é, pois, um texto.

São diversos os tipos de operações que precisam ser realizadas com textos durante a execução de programas. A captação, comparação, validação, manipulação e exibição de textos são exemplos de operações que precisam ser realizadas com uma frequência enorme. Isso faz com que a representação de textos seja fundamental para a construção dos mais diversos tipos de programas.

**Principais construtores da classe String:**

<table>
  <tr>
    <td width="149">
      <strong>Assinatura</strong>
    </td>
    
    <td width="427">
      <strong>Descrição</strong>
    </td>
  </tr>
  
  <tr>
    <td width="149">
      String()
    </td>
    
    <td width="427">
      Cria uma string vazia.
    </td>
  </tr>
  
  <tr>
    <td width="149">
      String(char[] value)
    </td>
    
    <td width="427">
      Cria uma string a partir de um vetor de caracteres representado pelo parâmetro chamado value.
    </td>
  </tr>
  
  <tr>
    <td width="149">
      String(byte[] bytes)
    </td>
    
    <td width="427">
      Cria uma string a partir de um vetor de bytes  representado pelo parâmetro chamado byte.
    </td>
  </tr>
  
  <tr>
    <td width="149">
      String(String original)
    </td>
    
    <td width="427">
      Cria uma string contendo a mesma sequência de caracteres de parâmetro chamado original.
    </td>
  </tr>
</table>

**Alguns métodos da classe String:**

<table>
  <tr>
    <td width="300">
      <strong>Assinatura</strong>
    </td>
    
    <td width="276">
      <strong>Descrição</strong>
    </td>
  </tr>
  
  <tr>
    <td width="300">
      char charAt(int index)
    </td>
    
    <td width="276">
      Retorna o caractere contido na posição especificada pelo parâmetro index.
    </td>
  </tr>
  
  <tr>
    <td width="300">
      int compareTo(String anotherString)
    </td>
    
    <td width="276">
      Compara o texto de duas strings e retorna um número inteiro que define a ordem destes textos. (zero significa que são iguais).
    </td>
  </tr>
  
  <tr>
    <td width="300">
      int compareToIgnoreCase(String anotherString)
    </td>
    
    <td width="276">
      Realiza a mesma tarefa que a anterior, porém ignorando a diferença entre caracteres maiúsculos e minúsculos.
    </td>
  </tr>
  
  <tr>
    <td width="300">
      boolean endWith(String suffix)
    </td>
    
    <td width="276">
      Testa se a string corrente termina com o sufixo especificado.
    </td>
  </tr>
  
  <tr>
    <td width="300">
      int indexOf(String str)
    </td>
    
    <td width="276">
      Retorna a posição inicial, na string corrente, da substring especificada pelo parâmetro str. Se a substring não for encontrada, o retorno é -1.
    </td>
  </tr>
  
  <tr>
    <td width="300">
      int lastIndexOf(String str)
    </td>
    
    <td width="276">
      Retorna a posição inicial, na string corrente, da última ocorrência da substring especificada pelo parâmetro str. Se a substring não for encontrada, o retorno é   -1.
    </td>
  </tr>
  
  <tr>
    <td width="300">
      int length()
    </td>
    
    <td width="276">
      Retorna o número de caracteres contidos na string corrente.
    </td>
  </tr>
  
  <tr>
    <td width="300">
      String replaceAll(String org, String replacement)
    </td>
    
    <td width="276">
      Retorna uma string resultante da substituição, na string corrente, de cada ocorrência da substring especificada no parâmetro org pela substring especificada no parâmetro replacement.
    </td>
  </tr>
  
  <tr>
    <td width="300">
      boolean startsWith(String prefix)
    </td>
    
    <td width="276">
      Testa se a string corrente começa com o prefixo especificado pelo parâmetro prefix.
    </td>
  </tr>
  
  <tr>
    <td width="300">
      String substring(int begin, int end)
    </td>
    
    <td width="276">
      Retorna uma nova string com a sequência de caracteres que se encontra entre as posições especificadas pelos parâmetros begin e end.
    </td>
  </tr>
  
  <tr>
    <td width="300">
      String toLowerCase()
    </td>
    
    <td width="276">
      Retorna uma nova string contendo todos os caracteres da string atual convertidos para minúsculo.
    </td>
  </tr>
  
  <tr>
    <td width="300">
      String toUpperCase()
    </td>
    
    <td width="276">
      Retorna uma nova string contendo todos os caracteres da string atual convertidos para maiúsculo.
    </td>
  </tr>
</table>

&nbsp;

**Operações Matemáticas**

Assim como a manipulação de textos é uma operação comum em quaisquer tipos de programas, a realização de operações matemáticas é muito frequente na grande maioria deles. Isso justifica a dedicação do tempo necessário para o estudo dos recursos disponíveis para suportar esse tipo de operação.

As operações matemáticas básicas são suportadas pela própria linguagem Java e podem ser realizadas com o uso de operadores. Soma, subtração, multiplicação e divisão são exemplos de operações matemáticas suportadas pela linguagem através de operadores.

No entanto, existem diversas operações matemáticas que não encontram suporte na linguagem. Potência, raiz quadrada, logaritmo, operações trigonométricas e até operações de arredondamento são exemplos de operações que não podem ser realizadas exclusivamente com os recursos da linguagem, para realizá-las, é preciso recorrer aos métodos da classe java.lang.Math.

**Alguns métodos da classe Math:**

<table>
  <tr>
    <td width="243">
      <strong>Assinatura</strong>
    </td>
    
    <td width="333">
      <strong>Descrição</strong>
    </td>
  </tr>
  
  <tr>
    <td width="243">
      static double cell(double a)
    </td>
    
    <td width="333">
      Retorna o próximo valor double que seja um número matemático inteiro.
    </td>
  </tr>
  
  <tr>
    <td width="243">
      static double floor(double a)
    </td>
    
    <td width="333">
      Retorna o valor double anterior que seja um número matemático inteiro.
    </td>
  </tr>
  
  <tr>
    <td width="243">
      static double rint(double a)
    </td>
    
    <td width="333">
      Arredonda o número informado e retorna-o na forma de um double.
    </td>
  </tr>
  
  <tr>
    <td width="243">
      static long round(double a)
    </td>
    
    <td width="333">
      Arredonda o número informado e retorna-0 na forma de um long.
    </td>
  </tr>
  
  <tr>
    <td width="243">
      static double pow(double a, double b)
    </td>
    
    <td width="333">
      Eleva um número à determinada potência.
    </td>
  </tr>
  
  <tr>
    <td width="243">
      static double sqrt(double a)
    </td>
    
    <td width="333">
      Calcula a raiz quadrada de um número.
    </td>
  </tr>
  
  <tr>
    <td width="243">
      static double random()
    </td>
    
    <td width="333">
      Retorna um número aleatório entre 0 e 1.
    </td>
  </tr>
</table>

&nbsp;

Perceba que todos os métodos listados são estáticos, por conterem o qualificador static em suas assinaturas. Isso significa que não é preciso instanciar um objeto da classe Math para fazer uso desses métodos, basta invocá-los a partir da própria classe, do mesmo modo como se faz com seus atributos.

**Valores Aleatórios**

Objetos da classe java.util.Random podem ser utilizados para gerar um fluxo de dados aleatório. Enquanto o método random() da classe Math somente é capaz de gerar números aleatórios entre zero e um, um objeto da classe Random pode ser usado para gerar diferentes tipos de dados aleatórios e em diferentes intervalos.

**Alguns métodos da classe java.util.Random.**

<table>
  <tr>
    <td width="158">
      <strong>Assinatura</strong>
    </td>
    
    <td width="418">
      <strong>Descrição</strong>
    </td>
  </tr>
  
  <tr>
    <td width="158">
      boolean nextBoolean()
    </td>
    
    <td width="418">
      Retorna um valor booleano aleatório.
    </td>
  </tr>
  
  <tr>
    <td width="158">
      double nextDouble()
    </td>
    
    <td width="418">
      Retorna um valor aleatório entre 0,0 e 0,9 como um tipo double.
    </td>
  </tr>
  
  <tr>
    <td width="158">
      float nextFloat()
    </td>
    
    <td width="418">
      Retorna um valor aleatório entre 0,0 e 0,9 como um tipo float.
    </td>
  </tr>
  
  <tr>
    <td width="158">
      int nextInt()
    </td>
    
    <td width="418">
      Retorna um número inteiro aleatório.
    </td>
  </tr>
  
  <tr>
    <td width="158">
      int nextInt(int n)
    </td>
    
    <td width="418">
      Retorna um número inteiro aleatório entre 0 e o valor especificado através do parâmetro n.
    </td>
  </tr>
  
  <tr>
    <td width="158">
      long nextLong()
    </td>
    
    <td width="418">
      Retorna um número inteiro longo aleatório.
    </td>
  </tr>
</table>

&nbsp;