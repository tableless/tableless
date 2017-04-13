---
title: 10 Dicas Simples Para Acelerar Seu Site Até 278 Vezes
author: Roberto Beraldo
type: post
date: 2015-11-07
excerpt: É fundamental que seu site seja rápido. Isso atrai e fideliza clientes. Veja aqui 10 dicas simples que podem acelerar seu site até 278 vezes
url: /10-dicas-simples-para-acelerar-seu-site-ate-278-vezes/
categories:
  - Back-end
  - Técnicas e Práticas
tags:
  - banco de dados
  - elasticsearch
  - web performance

---
Seu site é veloz?

Você sabia que, quanto mais veloz for seu site, mais satisfeito seu visitante vai ficar?

Isso é o que apontam algumas pesquisas realizadas pela _Akamai_ e pela _Gomez.com_. Elas demonstraram que a satisfação do seu visitante com o seu site decai em 16% a cada 1 segundo a mais que ele aguarda pelo carregamento da página.

As pesquisas também concluíram que os usuários esperam que os sites carreguem em 2 segundos ou menos, sendo que eles abandonariam páginas que levassem mais de 3 segundos para carregar.

E ainda: 79% dos clientes que tiveram problemas com o desempenho de um site não voltariam a fazer negócio. E 44% deles contariam aos amigos sobre a má experiência.

Por isso, o tempo de carregamento das páginas é extremamente importante. Pode ser uma das chaves para seu negócio dar certo de verdade e atrair clientes.

Velocidade de carregamento é fundamental em qualquer site. E é o critério que mais pesa nas avaliações feitas por usuários.

Afinal, ninguém poderá avaliar o _design_ do site ou seu conteúdo antes dele carregar completamente.

O grande problema é que muitos desenvolvedores focam muito em _design_ e em conteúdo, deixando o desempenho em segundo plano. Muitas vezes, perdem alguns segundos de carregamento em prol de um efeito visual.

Pense que seu visitante é um cliente fiel, que voltará inúmeras vezes ao seu site. Mas ele só fará isso se o site for rápido e confiável.

Por isso separei aqui 10 dicas simples, focadas em banco de dados, para você otimizar o carregamento das páginas do seu site.

<div id="attachment_51733" style="width: 510px" class="wp-caption aligncenter">
  <img class="size-full wp-image-51733" src="http://tableless.com.br/uploads/2015/10/1909270-many-cars-are-driving-at-night-on-a-highway-and-create-light-trails.jpg" alt="O mundo se move rápido. Seu site deve fazer o mesmo" width="500" height="248" />
  
  <p class="wp-caption-text">
    <em>O mundo se move rápido. Seu site deve fazer o mesmo</em>
  </p>
</div>

## 1. Selecione Apenas os Campos que Realmente Vai Usar {#selecione-apenas-os-campos-que-realmente-vai-usar}

É muito comum vermos consultas como `SELECT * FROM tabela`. O asterisco (`*`) vai trazer todas as colunas da tabela. Mas nem sempre precisamos de todas elas.

Muitas vezes, temos uma tabela com 20, 50 ou até 100 ou mais colunas. Serão raros os casos em que você precisará de todas elas.

Por isso sempre defina quais campos quer selecionar.

## 2. Modele Corretamente o Banco de Dados {#modele-corretamente-o-banco-de-dados}

Esta dica parece bem óbvia, mas o fato é que a maioria dos problemas com desempenho são devido à modelagem errada dos bancos de dados.

Um simples exemplo que vejo com muita frequência é, salvar diversas informações como dados pessoais e financeiros na mesma coluna de uma tabela.

Outro exemplo é, salvar em um único campo os valores selecionados em _checkboxes_. Alguns programadores pegam todos os valores e os armazenam separados por vírgula em um único campo. Quando o usuário decide atualizar ou remover uma opção, o programador deve escrever linhas e mais linhas para separar os valores, comparar e depois unir de novo.

Modelagem errada prejudica o banco de dados, o programador, que precisará escrever mais códigos. e, principalmente, o desempenho da aplicação, que precisará processar todo esse código em excesso.

Modelagem de dados é a primeira fase do desenvolvimento. Estruture bem seu banco de dados antes mesmo de começar a escrever seus códigos.

## 3. Use a Cláusula `LIMIT` {#use-a-cláusula-limit}

Outra vez, parece uma dica óbvia. Até demais.

Porém, por incrível que pareça, tem muita gente por aí que não faz isso.

Imagine um site ou blog que exibe apenas 10 registros por página. O correto é usar `LIMIT` para trazer apenas esses 10.

Já vi códigos sem esse `LIMIT`, que buscam diversos registros e pegam, via programação, apenas os 10 primeiros.

<div id="attachment_51740" style="width: 505px" class="wp-caption aligncenter">
  <img class="size-full wp-image-51740" src="http://tableless.com.br/uploads/2015/10/usuaio-impaciente.jpg" alt="Esse cliente você já perdeu" width="495" height="309" />
  
  <p class="wp-caption-text">
    <em>Esse cliente você já perdeu</em>
  </p>
</div>

## 4. Faça _Cache_ das Consultas {#faça-cache-das-consultas}

As consultas mais rápidas são aquelas não executadas.

Explico.

Sempre que você executa uma consulta SQL, uma determinada quantidade de recursos do servidor é usada, além do tempo gasto, é claro.

Por isso, uma ótima opção para sites grandes e com muito tráfego é criar _cache_ de dados, evitando que algumas consultas SQL frequentes sejam executadas pelo SGBD.

Há diversas ferramentas para isso, como, por exemplo, AdoDB e Memcached.

## 5. Não Execute Consultas Dentro de _Loops_ {#não-execute-consultas-dentro-de-loops}

O velho <a href="http://rberaldo.com.br/o-problema-do-n-mais-1/" target="_blank"><strong>Problema do N + 1</strong></a>.

Imagine esta situação: um site de artigos, com uma tabela de usuários e outra de artigos, que possui um campo que relaciona o artigo com seu autor.

Se precisar listar os autores e os títulos de seus respectivos posts, alguns programadores fariam o seguinte:

<ol type="1">
  <li>
    Selecionar todos os usuários: <code>SELECT id, nome FROM usuarios;</code>
  </li>
  <li>
    Para cada usuário, buscar seus posts: <code>SELECT titulo FROM posts WHERE user_id = id_do_usuario;</code>
  </li>
</ol>

A segunda consulta seria executada `N` vezes, sendo `N` o número total de usuários.

Ou seja, total de consultas seria `N + 1` (`N` consultas de posts mais uma consulta para a lista de usuários).

Porém, bastariam duas consultas ou mesmo um simples `JOIN` para resolver o problema, o que pode trazer um ganho de desempenho <a href="http://rberaldo.com.br/o-problema-do-n-mais-1/" target="_blank">de até 13 Vezes</a>.

Explico o **Problema do N + 1** em mais detalhes <a href="http://rberaldo.com.br/o-problema-do-n-mais-1/" target="_blank">neste artigo</a>.

<div id="attachment_51745" style="width: 510px" class="wp-caption aligncenter">
  <img class="size-full wp-image-51745" src="http://tableless.com.br/uploads/2015/10/seo-slow-loading11.jpg" alt="De olho no relógio!" width="500" height="333" />
  
  <p class="wp-caption-text">
    <em>De olho no relógio!</em>
  </p>
</div>

## 6. Use `JOIN`s em Vez de Sub-Consultas {#use-joins-em-vez-de-sub-consultas}

Quando programamos, usar sub-consultas é algo simples, lógico e funcional, como neste exemplo:

<pre class="sourceCode sql"><code class="sourceCode sql">&lt;span class="kw">SELECT&lt;/span> usuarios.id,
       (
        &lt;span class="kw">SELECT&lt;/span> &lt;span class="fu">MAX&lt;/span>(data_criacao)
               &lt;span class="kw">FROM&lt;/span> posts
               &lt;span class="kw">WHERE&lt;/span> usuario_id = usuarios.id
       ) &lt;span class="kw">AS&lt;/span> ultimo_post
       &lt;span class="kw">FROM&lt;/span> usuarios u</code></pre>

Embora sub-consultas sejam úteis, usar `JOIN` é igualmente funcional e mais rápido.

A consulta anterior pode ser transformada nesta:

<pre class="sourceCode sql"><code class="sourceCode sql">&lt;span class="kw">SELECT&lt;/span> a.id, &lt;span class="fu">MAX&lt;/span>(p.data_criacao) &lt;span class="kw">AS&lt;/span> ultimo_post
       &lt;span class="kw">FROM&lt;/span> usuarios u
       &lt;span class="kw">INNER&lt;/span> &lt;span class="kw">JOIN&lt;/span> posts p &lt;span class="kw">ON&lt;/span> (u.id = p.usuario_id)
       &lt;span class="kw">GROUP&lt;/span> &lt;span class="kw">BY&lt;/span> u.id</code></pre>

## 7. Use `UNION`s ao invés de `OR`s {#use-unions-em-vez-de-ors}

A seguinte consulta utiliza a cláusula `OR` para filtrar os registros:

<pre class="sourceCode sql"><code class="sourceCode sql">&lt;span class="kw">SELECT&lt;/span> * 
      &lt;span class="kw">FROM&lt;/span> tabela1, tabela2
      &lt;span class="kw">WHERE&lt;/span> tabela1.p = tabela2.q 
            &lt;span class="kw">OR&lt;/span> tabela1.x = tabela2.y;</code></pre>

A cláusula `UNION` permite combinar os resultados de dois ou mais `SELECT`s.

A seguinte consulta, usando `UNION`, vai trazer os mesmos resultados que a consulta anterior, sendo mais rápida:

<pre class="sourceCode sql"><code class="sourceCode sql">&lt;span class="kw">SELECT&lt;/span> *
      &lt;span class="kw">FROM&lt;/span> tabela1, tabela2 
      &lt;span class="kw">WHERE&lt;/span> tabela1.p = tabela2.q
&lt;span class="kw">UNION&lt;/span>
&lt;span class="kw">SELECT&lt;/span> * 
      &lt;span class="kw">FROM&lt;/span> tabela1, tabela2 
      &lt;span class="kw">WHERE&lt;/span> tabela1.x = tabela2.y</code></pre>

## 8. Utilize Índices {#utilize-índices}

Índices de banco de dados são como índices de bibliotecas. Eles permitem ao banco de dados encontrar os resultados sem perder tempo olhando registro por registro. Assim como um leitor olha o índice da biblioteca e encontra um livro com mais facilidade e rapidez.

Sempre crie índices em suas tabelas, indexando os campos que são frequentemente consultados.

## 9. Otimize as Tabelas do Banco de Dados {#otimize-as-tabelas-do-banco-de-dados}

Alguns SGBDs, como o MySQL, possuem ferramentas nativas para otimização de seus dados.

Se suas tabelas são frequentemente modificadas, recebendo novos dados e removendo outros, pode ser interessante rodar uma otimização com certa frequência, para tornar as tabelas menores e mais rápidas.

A otimização toma um certo tempo para ser executada, por isso, é recomendável agendá-la para madrugadas ou para horários quando seu sistema tem pouco uso.

Para o MySQL, um simples exemplo de otimização pode ser feito com esta consulta:

<pre class="sourceCode sql"><code class="sourceCode sql">OPTIMIZE &lt;span class="kw">TABLE&lt;/span> nome_da_tabela;</code></pre>

<div id="attachment_51742" style="width: 646px" class="wp-caption aligncenter">
  <img class="size-full wp-image-51742" src="http://tableless.com.br/uploads/2015/10/foguete.jpg" alt="Site rápido como foguete: desempenho até 278 Vezes maior" width="636" height="301" />
  
  <p class="wp-caption-text">
    <em>Site rápido como foguete: desempenho até 278 Vezes maior</em>
  </p>
</div>

## 10. Use um Servidor de Busca {#use-um-servidor-de-busca}

Todas as dicas anteriores são válidas e trazem um certo ganho de desempenho.

Mas já imaginou conseguir ganhos de desempenho de <a href="http://buscasupersonica.com.br" target="_blank">Até 278 Vezes</a>?!

Esse é o ganho que podemos conseguir com um Servidor de Busca como o ElasticSearch.

O ElasticSearch permite armazenar dados de forma otimizada para buscas extremamente rápidas.

Se o seu sistema faz muitos `SELECT`s, o ElasticSearch pode trazer <a href="http://buscasupersonica.com.br" target="_blank">ganhos fenomenais em desempenho</a>.

Veja <a href="http://buscasupersonica.com.br" target="_blank">Neste Vídeo</a> algumas dicas para Acelerar o Seu Site Até 278 Vezes!