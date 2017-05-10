---
title: PHP na linha de comando
author: Gustavo Straube
type: post
date: 2014-07-24
excerpt: O PHP, assim como outras linguagens de programação, oferece a opção de execução via linha de comando. Aprenda nesse passo a passo básico como usar o terminal para executar seus scripts.
url: /php-na-linha-de-comando/
dsq_thread_id: 2865448494
categories:
  - PHP
tags:
  - desenvolvimento
  - Na Prática
  - tutorial

---
Quem conhece um pouco de alguma linguagem de programação, acaba se acostumando a escrever trechos de código para automatizar tarefas simples ou resolver problemas. Para aqueles mais íntimos do PHP, se torna habitual escrever aplicações com uma interface simples em HTML, mas com isso deixamos de aproveitar algumas vantagens da linha de comando em conjunto com o nosso script para resolver essas questões triviais (ou nem tanto). Também existe benefício de não depender de um servidor web e um navegador.

## 1. Hello terminal!

Para dar os primeiros passos na execução de scripts a partir do interpretador é interessante começar entendendo como funciona a chamada. Então, que tal um “Hello terminal!”? Segue o código do nosso primeiro script:

<pre>&lt;?php
echo "Hello terminal!\n";</pre>

A partir da linha de comando, no diretório onde você salvou o seu script, execute (considerando que você salvou o arquivo como **script.php**):

<pre>$ php script.php
Hello terminal!</pre>

No Windows, você deverá usar o executável do PHP — **php.exe script.php** —, mas tenha certeza de que ele está no PATH do sistema.

Isso deverá imprimir a frase “**Hello terminal!**” na saída padrão do terminal, como mostrado acima. Você vai ver que se não incluir a quebra de linha no final da string (\n), o seu prompt vai ficar na mesma linha que a saída do script. Isso não prejudica a execucão do script e nem dos próximos comandos, mas pode dificultar a leitura do resultado.

## 2. Usando parâmetros

Quando usamos o navegador para executar um script PHP e precisamos passar algum parâmetro para ele, incluímos uma query no final da URL, por exemplo: **?param1=abc&param2=123**. Usando a linha de comando é possível fazer algo semelhante, passando argumentos na chamada do interpretador, logo em seguida ao nome do script, assim:

<pre>$ php script.php abc 123</pre>

Nesse exemplo estamos passando dois argumentos: “**abc**” e “**123**”. O seu script pode lidar com esses dados através das variáveis **$argc** e **$argv**. A primeira contém um número inteiro com a quantidade de argumentos passados para o interpretador. Atenção: o nome do script é o primeiro parâmetro, então **$argc** sempre vai ser no mínimo 1, no nosso exemplo ele teria o valor 3. A segunda variável contém um array com os valores dos argumentos. Assim como acontece para a **$argc**, o primeiro valor é o nome do script.

Se imprimirmos, usando a função **var_dump**, o conteúdo das variáveis **$argc** e **$argv**, do último exemplo, teríamos:

<pre>int(3)
array(3) {
  [0]=&gt;
  string(10) "script.php"
  [1]=&gt;
  string(3) "abc"
  [2]=&gt;
  string(3) "123"
}</pre>

Você vai notar que **$argc** sempre carrega o mesmo valor que o resultado da chamada **count($argv)**, em todo caso **$argc** é o padrão usado e é alguns milisegundos mais rápido por já estar na memória (se isso fizer alguma diferença na performance do seu script).

Sabendo disso, como exemplo, podemos escrever um utilitário simples para ajudar em redações: listar as palavras de um texto em ordem alfabética seguidas de sua posição no texto, assim podemos verificar como as palavras se repetem no texto e ajustar o vocabulário, se for o caso. Vamos lá!

Esperamos que o nome do arquivo (para simplificar vamos usar um TXT simples) seja passado como argumento para o script.

<pre>&lt;?php

/*
 * Esperamos 1 parâmetro (lembrando que o nome do script
 * também conta) com o nome do TXT.
 */
if ($argc &lt; 2) {
  echo "O nome do arquivo TXT deve ser passado para o script.\n";

  /*
   * Passamos um código de erro (qualquer número inteiro
   * entre 1 e 254) para indicar que o programa encerrou com erro.
   */
  exit(1);
}
$file = $argv[1];

/*
 * Verificamos se a extensão do arquivo é txt.
 */
if (".txt" !== strtolower(substr($file, -4)) {
  echo "O script aceita somente arquivos TXT.\n";
  exit(1);
}

// Pegamos o conteúdo do arquivo.
$contents = file_get_contents($file);

// Separamos as palavras em um array.
$words = preg_split("/[\s+,\.!\?\(\):]/", $contents, null, PREG_SPLIT_NO_EMPTY);

// Ordenamos alfabeticamente.
natcasesort($words);

foreach ($words as $position =&gt; $word) {

  /*
   * Imprimimos cada palavra e sua respectiva posição
   * dentro do texto.
   */
  echo "{$word} ({$position})\n";

}</pre>

Feito!

Agora se criarmos um TXT chamado **sobre.txt**, no mesmo diretório que nosso script, contendo a primeira frase do artigo da Wikipédia sobre o PHP, teremos o resultado abaixo:

<pre>$ php script.php sobre.txt
acrônimo (2)
apenas (19)
aplicações (24)
atuantes (27)
capazes (32)
[...]
usada (17)
Web (40)
Wide (39)
World (38)
é (12)</pre>

## 3. Mesclando o uso com outros comandos

Falando um pouco das utilidades que o terminal oferece e que podemos combinar com o nosso script, temos, por exemplo, o **grep**, que executa buscas através de expressões regulares (alternativamente, no Windows você pode usar o **findstr**: <a title="http://technet.microsoft.com/en-us/library/bb490907.aspx" href="http://technet.microsoft.com/en-us/library/bb490907.aspx" target="_blank">http://technet.microsoft.com/en-us/library/bb490907.aspx</a>). Se quisermos filtrar o resultado do nosso script para exibir apenas uma palavra específica, sem alterar o código, poderíamos executá-lo assim:

<pre>$ php script.php sobre.txt | grep originalmente
originalmente (18)
originalmente (8)</pre>

O grep é apenas um dos comandos disponíveis que podem ser agregados a execução do seu script, mas a idéia é apresentar apenas o básico sobre a execução de programas PHP via linha de comando.

Ficou com alguma dúvida? Fique a vontade para usar o espaço de comentários.