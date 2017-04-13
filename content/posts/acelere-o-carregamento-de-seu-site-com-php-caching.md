---
title: Acelere o carregamento de seu site com PHP Caching
author: Felipe Torretto
type: post
date: 2016-07-07
url: /acelere-o-carregamento-de-seu-site-com-php-caching/
categories:
  - PHP
tags:
  - cache
  - desempenho
  - performance
  - php

---
<span style="font-weight: 400">Criar um site dinâmico, de fácil manutenção e que carregue rápido é o desejo de todo desenvolvedor, mas para isso não existe uma fórmula mágica, é necessário conciliar diferentes ferramentas e técnicas. </span>

<span style="font-weight: 400">Mas muitos desenvolvedores iniciantes em PHP não conhecem as soluções existentes ou tem medo da curva de aprendizado que os frameworks exigem.</span>

<span style="font-weight: 400">O foco desse artigo é mostrar para esses desenvolvedores como uma técnica simples, utilizando apenas comandos básicos do PHP, pode acelerar o carregamento de seu site e evitar que ele fique caindo.</span>

### O problema a ser resolvido, processamento desnecessário

<span style="font-weight: 400">Para cada acesso a um site dinâmico, o servidor geralmente realiza consultas no banco de dados, executa blocos de códigos e entrega uma página pronta para exibição.</span>

<span style="font-weight: 400">Mesmo que os acessos a uma página ocorram com poucos segundos de diferença e nada no conteúdo tenha sido alterado, o servidor irá fazer o mesmo processo para cada solicitação, quantas vezes for preciso.</span>

<span style="font-weight: 400">Isto é um trabalho desnecessário e que exige muito processamento do servidor, principalmente em momentos de tráfego intenso, e se o servidor não der conta, o seu site ficará temporariamente fora do ar.</span>

### A solução, PHP Caching

<span style="font-weight: 400">Também conhecido como Cache de Objetos, essa técnica executa uma página PHP e armazena o conteúdo gerado em um arquivo HTML, e para os próximos acessos, durante um certo período, o servidor irá entregar esse HTML gerado.</span>

<span style="font-weight: 400">Sem a necessidade de consultar o banco de dados ou executar algum tipo de programação para montar a página, o servidor além de conseguir entregar uma página mais rapidamente, também suportará um número maior de acessos concorrentes.</span>

### **Qual o ganho na performance?**

<span style="font-weight: 400">Vai depender muito da programação do site, mas quanto mais ações forem realizadas no backend, maior será o ganho. Veja abaixo os resultados obtidos durante um teste:</span>

 <img class="aligncenter wp-image-55365 size-full" src="http://tableless.com.br/uploads/2016/07/phpcaching-benchmarks.jpg" width="1180" height="393" />A versão dinâmica foi entregue em 318 ms e a versão cacheada em 14 ms, 23 vezes mais rápido.

## Desenvolvimento

<span style="font-weight: 400">Chega de teoria e vamos para a prática, criaremos juntos um exemplo que seja o mais simples possível.</span>

<span style="font-weight: 400">Primeiro crie uma pasta no seu ambiente de desenvolvimento chamada <code>phpcaching</code>, dentro dela crie outras duas pastas, uma chamada <code>paginas</code> onde iremos armazenar as páginas dinâmicas em PHP e outra chamada <code>cache</code> que irá armazenar os arquivos HTML.</span>

<span style="font-weight: 400">Dentro da pasta <code>paginas</code> crie um arquivo chamado <code>index.php</code>, com o código:</span>

<pre><span style="font-weight: 400">&lt;!DOCTYPE html&gt;</span>
<span style="font-weight: 400">&lt;html&gt;</span>
<span style="font-weight: 400">&lt;head&gt;</span>
<span style="font-weight: 400">    &lt;meta charset="utf-8"&gt;</span>
<span style="font-weight: 400">    &lt;title&gt;PHP Caching&lt;/title&gt;</span>
<span style="font-weight: 400">&lt;/head&gt;</span>
<span style="font-weight: 400">&lt;body&gt;</span>
<span style="font-weight: 400">    &lt;p&gt;Página gerada em: &lt;?php echo date('H:i:s') ?&gt;&lt;/p&gt;</span>
<span style="font-weight: 400">&lt;/body&gt;</span>
<span style="font-weight: 400">&lt;/html&gt;</span>
</pre>

<span style="font-weight: 400">Teste a página que acabamos de criar, acessando ela pelo navegador, no meu caso o endereço é: <code>http://localhost/phpcaching/paginas/index.php</code></span>

<span style="font-weight: 400">Você verá uma página simples, que apenas mostra o horário atual toda vez que é acessada.</span>

<span style="font-weight: 400">Agora vamos criar o nosso controlador de cache, que irá funcionar da seguinte maneira:</span>

<img class="aligncenter wp-image-55366 " src="http://tableless.com.br/uploads/2016/07/phpcaching-diagrama-de-atividades.jpg" width="551" height="551" />
  
<span style="font-weight: 400">Sabendo a lógica de funcionamento, fica mais fácil programar nosso controlador. Crie na raiz do projeto um arquivo chamado <code>index.php</code> com o seguinte código:</span>

<pre class="lang-php">&lt;?php
// Configurações
$validadeEmSegundos = 60;
$arquivoCache = 'cache/index.html';
$urlDinamica = 'http://localhost/phpcaching/paginas/index.php';

// Verifica se o arquivo cache existe e se ainda é válido
if (file_exists($arquivoCache) && (filemtime($arquivoCache) &gt; time() - $validadeEmSegundos)) {

    // Lê o arquivo cacheado
    $conteudo = file_get_contents($arquivoCache);
} else {

    // Acessa a versão dinâmica
    $conteudo = file_get_contents($urlDinamica);

    // Cria o cache
    file_put_contents($arquivoCache, $conteudo);
}

// Exibe o conteúdo da página
echo $conteudo;
</pre>

<span style="font-weight: 400">Vou explicar as funções utilizadas para caso você não conheça alguma delas:</span>
  
<span style="font-weight: 400"><code>file_exists</code>: verifica se um arquivo existe</span>
  
<span style="font-weight: 400"><code>file_get_contents</code>: lê o conteúdo de um arquivo</span>
  
<span style="font-weight: 400"><code>file_put_contents</code>: escreve o conteúdo em um arquivo</span>
  
<span style="font-weight: 400"><code>filemtime</code>: retorna o horário que o arquivo foi modificado</span>
  
<span style="font-weight: 400"><code>time</code>: retorna o horário atual</span>

<span style="font-weight: 400">Agora acesse o site através do controlador de cache, no meu caso <code>http://localhost/phpcaching/</code></span>

<span style="font-weight: 400">Repare que o horário aparece como anteriormente, mas se atualizarmos a página o horário não muda. Isto acontece porque a página exibida é a versão cacheada, que foi armazenada na pasta <code>cache</code> com o nome <code>index.html</code>.</span>

Pronto, nossa solução para cachear páginas está criada.

## Conclusão

<span style="font-weight: 400">Esta técnica é uma maneira eficaz de aumentar a performance de seu site, sem precisar instalar algo no servidor ou algum framework no seu projeto e é recomendada para quem está iniciando no assunto.</span>

<span style="font-weight: 400">O código apresentado não é uma solução definitiva, mas uma base que podemos expandir de acordo com as necessidades de cada projeto, crie sua versão melhorada, faça um teste com um projeto que você já possua e analise a diferença no tempo de carregamento do site.</span>

<span style="font-weight: 400">Eu utilizo essa técnica em um portal de notícias da minha região, e apesar do site já ter sido migrado de servidor algumas vezes, o código nunca precisou de alteração, essa é a vantagem de utilizar apenas comandos básicos do PHP.</span>

<span style="font-weight: 400">Continuem os estudos e que a performance esteja com você.</span>