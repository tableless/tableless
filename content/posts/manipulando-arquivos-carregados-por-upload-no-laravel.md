---
title: Manipulando arquivos carregados por upload no Laravel
author: Gustavo Straube
image: uploads/2017/03/ivars-krutainis-153526_.jpg
type: post
date: 2017-04-07
excerpt: Arquivos grandes carregados por upload no Laravel
categories:
  - Laravel
---


<a href="https://laravel.com/" target="_blank">Laravel</a> é um <em>framework</em> que tem se tornado bastante popular no mundo do PHP. Uma das vantagens dele sobre outros <em>frameworks</em> é que ele permite que seu código fique limpo e fluído, especialmente pela forma como ele trata as dependências e outras ajudas. Mas isso é assunto para outro momento. Agora, queria falar um pouco sobre a manipulação de arquivos carregados via upload.

Para começar, queria compartilhar uma situação hipotética: por causa da lógica de negócio por trás do projeto que você está trabalhando, é necessário garantir que arquivos duplicados não sejam carregados via <em>upload</em>. Usar o nome do arquivo nem sempre é a melhor forma de fazer isso porque o usuário pode simplesmente usar outro nome. Então quero compartilhar uma forma de fazer isso usando Laravel.

A documentação do <em>framework</em> não é muito clara a respeito da classe que representa um arquivo carregado. Procurando no código-fonte, porém, é possível encontrar evidências de que o objeto retornado pelo método <code>$request-&gt;file()</code> é uma instância da classe <code>SplFileInfo</code>. Isso significa que é possível manipular o arquivo sem grandes complicações. E o melhor: é possível fazer isso antes mesmo de gravar o arquivo no destino final.

Você pode encontrar essa evidência da <code>SplFileInfo</code> na classe <a href="https://github.com/symfony/symfony/blob/master/src/Symfony/Component/HttpFoundation/File/File.php" target="_blank">File</a>:

<pre>class File extends \SplFileInfo 
{</pre>

Essa referência a uma classe do <a href="http://symfony.com/" target="_blank">Symfony</a> pode parecer estranha se você não tem familiriadade com a arquitetura do Laravel, mas ele usa vários componentes do Symfony internamente.

Bom, vamos ver como é possível fazer a manipulação na prática!


## Resolvendo um upload


Uma <em>action</em> (método de um <em>controller</em>) simples para <em>upload</em> de arquivo geralmente pega a instância do arquivo do <em>request</em>, verifica se um arquivo foi enviado e grava ele no destino final. Provavelmente algo parecido com isso:

<pre class="php">&lt;?php

namespace App\Http\Controllers;

use Illuminate\Http\Request; 
use Symfony\Component\HttpFoundation\Response;

class FileController extends Controller 
{

    /**
    * Resolve o envio do arquivo.
    *
    * @param Request $request A instância do request.
    * @return Response A instância da response.
    */
    public function upload(Request $request)
    {

        /*
        * O campo do form com o arquivo tinha o atributo name="file".
        */
        $file = $request-&gt;file('file');

        if (empty($file)) {
            abort(400, 'Nenhum arquivo foi enviado.');
        }

        $path = $file-&gt;store('uploads');

        // Faça qualquer coisa com o arquivo enviado...

    }
}</pre>


## Lendo e comparando o arquivo em partes

Usando aquela instância do arquivo que pegamos do <em>request</em>, podemos escrever um método que compara ela com uma outra instância da classe <code>SplFileInfo</code>. Para agilizar o processamento, você não precisa comparar os arquivos inteiros. Ir por partes é a melhor estratégia. Você pode ler um pedaço do mesmo tamanho de ambos os arquivos e compará-los. Assim que uma diferença for encontrada, pare a execução do método.

<pre>/**
 * Compara o conteúdo de dois arquivos para verificar se há diferenças.
 *
 * Não verifica qual exatamente é a diferença entre os arquivos. Dessa 
 * forma, uma diferenção é encontrada, a função para de ler os arquivos.
 *
 * @param SplFileInfo $a O primeiro arquivo para comparar.
 * @param SplFileInfo $b O segundo arquivo para comparar.
 * @return bool Indica se há qualquer diferença entre os arquivos.
 */
private function fileDiff($a, $b) 
{
    $diff = false;
    $fa = $a-&gt;openFile();
    $fb = $b-&gt;openFile();

    /*
     * Lê o mesmo número de bytes de cada arquivo. Quebra (break) o loop 
     * assim que uma diferença for encontrada.
     */
    while (!$fa-&gt;eof() &amp;&amp; !$fb-&gt;eof()) {
        if ($fa-&gt;fread(4096) !== $fb-&gt;fread(4096)) {
            $diff = true;
            break;
        }
    }

    /*
     * Apenas um dos arquivos chegou ao fim.
     */
    if ($fa-&gt;eof() !== $fb-&gt;eof()) {
        $diff = true;
    }

    /*
     * Closing handlers.
     */
    $fa = null;
    $fb = null;

    return $diff;
}</pre>


## Melhorando a performance

A função que escrevemos acima é uma ótima maneira de comparar dois arquivos. Porém, abrir, ler e comparar o conteúdo de cada arquivo enviado anteriormente para a aplicação pode consumir muitos recursos (tempo, I/O, processamento). Podemos reduzir significamente esse consumo comparando o tamanho dos arquivos primeiro, e então apenas abrir e comparar o conteúdo dos arquivos que tiverem o mesmo tamanho. Isso ficaria assim:

<pre>/**
 * Verifica se o arquivo passado já foi enviado antes.
 *
 * Passa de arquivo em arquivo no diretório de uploads, conferindo se algum 
 * pode ser igual ao arquivo sendo enviado.
 *
 * @param SplFileInfo $file O arquivo para verificar.
 * @return bool Indica se arquivo já foi enviando antes.
 */
private function isAlreadyUploaded($file) 
{
    $size = $file-&gt;getSize();

    /*
     * O arquivo onde os arquivos são gravados.
     */
    $path = storage_path('app/uploads/');

    if (!is_dir($path)) {
        return false;
    }

    $files = scandir($path);
    foreach ($files as $f) {
        $filePath = $path . $f;
        if (!is_file($filePath)) {
            continue;
        }

        /*
         * Se ambos os arquivos tiverem o mesmo tamanho, compara o conteúdo.
         */
        if (filesize($filePath) === $size) {

            /*
             * Verifica se há alguma diferença, usando a função que escrevemos 
             * acima.
             */
            $diff = $this-&gt;fileDiff(new \SplFileInfo($filePath), $file);

            /*
             * Retorna se os arquivos **não** são diferentes, ou seja, iguais. 
             * Isso significa que já foi enviado antes.
             */
            return !$diff;
        }
    }
    return false;
}</pre>


## Gravando o arquivo

Voltando à <em>action</em> que definimos no começo e usando esse último método que escrevemos, podemos finalmente gravar o arquivo. É importante lembrar de chamar o método de gravação (<code>store</code>) apenas depois de ter verificado se o arquivo já não existe.

<pre>&lt;?php

namespace App\Http\Controllers;

use Illuminate\Http\Request; 
use Symfony\Component\HttpFoundation\Response;

class FileController extends Controller 
{

    /**
     * Resolve o envio do arquivo.
     *
     * @param Request $request A instância do request.
     * @return Response A instância da response.
     */
    public function upload(Request $request)
    {

        /*
         * O campo do form com o arquivo tinha o atributo name="file".
         */
        $file = $request-&gt;file('file');

        if (empty($file)) {
            abort(400, 'Nenhum arquivo foi enviado.');
        }

        /*
         * Já existe um arquivo igual ao que está sendo enviado?
         */
        if ($this-&gt;isAlreadyUploaded($file)) {
            abort(400, 'Esse mesmo arquivo já foi enviado antes.');
        }

        /*
         * Apenas grava o arquivo depois da verificação.
         */
        $path = $file-&gt;store('uploads');

        // Faça qualquer coisa com o arquivo enviado...

    }
}</pre>


## Conclusão

Essa é apenas uma maneira de trabalhar com o arquivo retornado pelo <em>request</em>, pensando no que ele é internamente. Existem provavelmente outras mil maneiras de utilizar isso para resolver outros problemas ou ao menos tornar seu código mais fluído.

Também é importante entender que essa é apenas uma forma de fazer isso usando o <em>framework</em>. Você provavelmente pode usar outras táticas para resolver o mesmo problema. Por exemplo, seria possível armazenar o arquivo enviado em um diretório temporário e então fazer as comparações necessárias. Ou você pode aproveitar a lógica descrita aqui e usar as funções nativas do PHP para <em>upload</em> ao invés das funções do Laravel.