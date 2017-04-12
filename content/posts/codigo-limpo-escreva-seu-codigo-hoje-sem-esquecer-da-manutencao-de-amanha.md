---
title: Código Limpo – Escreva seu código hoje sem esquecer da manutenção de amanhã
author: tableless
type: post
date: 2017-01-13
excerpt: Seu código é legível e fácil de dar manutenção? Veja neste post porque escrever código limpo é importante e como equilibrar isso com os prazos dos projetos.
url: /codigo-limpo-escreva-seu-codigo-hoje-sem-esquecer-da-manutencao-de-amanha/
categories:
  - PHP
  - Técnicas e Práticas
tags:
  - boas praticas
  - código limpo
  - desenvolvimento
  - Técnicas e Práticas

---
Você provavelmente já precisou entender o código de outra pessoa. Seja para realizar uma alteração, corrigir um _bug_ ou até mesmo para procurar um comportamento específico.
  
Talvez você até tenha feito isso no seu próprio código!

Agora pense por alguns segundos: O código foi **fácil** de entender?

Você, **só pela leitura**, conseguiu identificar o método exato que precisava alterar?

Se a resposta for positiva: ótimo! O programador fez a sua parte e conseguiu deixar o código limpo (ou pelo menos fez um código simples o suficiente para ser entendido).

Mas se a resposta for &#8220;mais ou menos&#8221;, ou &#8220;nem um pouco&#8221;, é aí que mora o problema.

E essa é a explicação para o título deste post.

## Mas por que isso acontece?

Quando aprendemos a programar, estamos mais preocupados em aprender a lógica de programação e fazer as coisas funcionarem do que com a estrutura e leitura do código. E isso é totalmente normal, afinal, estamos iniciando.

Porém, na minha opinião, o problema começa quando evoluímos em nossa carreira (começamos a trabalhar em projetos maiores e ter mais responsabilidades) e **não evoluímos o nosso código na mesma medida**.

Aí começam a aparecer os famosos &#8220;códigos espaguete&#8221; ou mesmo aquele monte de variáveis que não ajudam em nada a entender o código.

Leia o código abaixo e responda:

  * Consegue identificar qual método você precisa chamar primeiro pra cadastrar um novo cliente?
  * Percebe como os métodos estão sem ordem nenhuma e um chama o outro internamente, formando um &#8220;espaguete&#8221;? 

<pre class="lang-php">class CadastroCliente
{
    public function enviarEmail()
    {
        $mailer = new Mailer();
        $mailer-&gt;send();
    } 
    
    public function gerarSenha()
    {
        // codigo para gerar senha
        
        return $senha;
    }
    
    public function atualizar($cliente)
    {
        $model = new ClienteModel();
        $model-&gt;confirmar($cliente);
    }

    public function criar($cliente)
    {
        $senha = $this-&gt;gerarSenha();
        
        $model = new ClienteModel();
        $model-&gt;add($cliente, $senha);

        $this-&gt;enviarEmail();
    }
    
    public function confirmarCadastro($cliente)
    {
        $this-&gt;enviarEmail();
        $this-&gt;atualizar($cliente);
    }
}
</pre>

O problema dessa evolução tardia é que somente depois de muito tempo o desenvolvedor vai descobrir que poderia ter feito melhor. Note que começar escrevendo códigos confusos não é o problema, mas sim o tempo necessário para entender que essa evolução é importante.

E então, ao perceber que o código não está dos melhores, o desenvolvedor pode escolher entre:

1 &#8211; Deixar pra lá, por que o seu código sempre funciona
  
2 &#8211; Começar a melhorar o seu código pensando na qualidade do software

## Código funcionando! Next!

A sensação de ver nosso código funcionando é ótima! Quem não gosta?

Só que muita gente para por aí, nem lembra que por trás daquele comportamento existem classes, métodos, variáveis, etc.

Mas será que esse código está legível? As classes possuem responsabilidades definidas? Os métodos estão coerentes?

Pois é, existem vários pontos que precisamos estar atentos para que nosso código seja limpo.

Mas apesar de parecer muito complicado, na verdade podemos começar da forma mais simples possível: comece aos poucos e vá sempre buscando deixá-lo mais legível. Não tem como você fazer o melhor código de primeira.

Para exemplificar essa transformação de um código difícil de ser lido em um código limpo, veja o trecho abaixo:

<pre class="lang-php">class Carrinho
{
    private $vl;
    private $prods;

    public function adic($prods)
    {
        foreach ($prods as $prod) {
            if ($prod-&gt;getCat() == 'P') {
                $vl = $prod-&gt;getVl() * 0.75;
                $this-&gt;vl += $vl;
                $this-&gt;prods[] = $prod;
            } elseif ($prod-&gt;getCat() == 'B') {
                $vl = 0;
                $this-&gt;vl += $vl;
                $this-&gt;prods[] = $prod;
            } elseif ($prod-&gt;getCat() == '') {
                $vl = $prod-&gt;getVl();
                $this-&gt;vl += $vl;
                $this-&gt;prods[] = $prod;
            }
        }
    } 
}
</pre>

Você consegue identificar o que são aqueles valores (P e B) ou até mesmo entender rapidamente o que o método faz?

Vamos deixá-lo um pouco mais claro:

<pre class="lang-php">class Carrinho
{
    private $valorTotal;
    private $produtos;

    public function adicionarProduto($produtos)
    {
        foreach ($produtos as $produto) {
            if ($produto-&gt;getCategoria() == 'PROMOCAO') {
                $valor = $produto-&gt;getValor() * 0.75;
                $this-&gt;valorTotal += $valor;
                $this-&gt;produtos[] = $produto;
            } elseif ($produto-&gt;getCategoria() == 'BRINDE') {
                $valor = 0;
                $this-&gt;valorTotal += $valor;
                $this-&gt;produtos[] = $produto;
            } elseif ($produto-&gt;getCategoria() == '') {
                $valor = $produto-&gt;getValor();
                $this-&gt;valorTotal += $valor;
                $this-&gt;produtos[] = $produto;
            }
        }
    } 
}
</pre>

Agora já dá pra entender mais rápido o que o método faz: adicionar um produto no carrinho e acrescenta o valor do produto no valor total.

Mas dá pra melhorar ainda mais:

<pre class="lang-php">class Carrinho
{
    private $valorTotal;
    private $produtos;

    public function adicionarProduto($produtos)
    {   
        foreach ($produtos as $produto) {
            $valor = $produto-&gt;getValor();
            
            if ($produto-&gt;getCategoria() == 'PROMOCAO') {
                $valor = $produto-&gt;getValor() * 0.75;
            } elseif ($produto-&gt;getCategoria() == 'BRINDE') {
                $valor = 0;
            }

            $this-&gt;valorTotal += $valor;
            $this-&gt;produtos[] = $produto;
        }
    } 
}
</pre>

Notou que as linhas que atualizam o valor total e os produtos internos da classe se repetiam a cada `if`?

Já que se repetem, podemos tirar de dentro dos `ifs`, pois ele sempre será executado independente da condição.

Além disso, podemos inicializar a variável `$valor` com o valor do produto, e de acordo com a categoria do produto atualizamos essa variável. Assim conseguimos eliminar a utilização de um `if` desnecessário verificando se o produto não tem categoria.

Agora o toque final:

<pre class="lang-php">class Carrinho
{
    private $valorTotal;
    private $produtos;

    public function adicionarProduto($produtos = [])
    {   
        foreach ($produtos as $produto) {
            $this-&gt;valorTotal += $this-&gt;calcularValorProduto($produto);
            $this-&gt;produtos[] = $produto;
        }
    }

    private function calcularValorProduto(Produto $produto)
    {
        if ($produto-&gt;getCategoria() == Produto::CATEGORIA_BRINDE) {
            return 0;
        }

        if ($produto-&gt;getCategoria() == Produto::CATEGORIA_PROMOCAO) {
            return $produto-&gt;getValor() * 0.75;
        }

        return $produto-&gt;getValor();
    }
}
</pre>

Pronto, o código agora ficou mais simples e os métodos com uma únicaresponsabilidade definida.

Veja as alterações realizadas:

  * Agora o cálculo do valor fica em um método privado da classe, para não ficar tudo no método `adicionarProduto`
  * Foi adicionado um _Type Hint_ no método `calcularValorProduto` para garantir que a variável `$produto` seja um objeto da classe `Produto`
  * No método de cálculo, trocamos o `elseif` por dois `ifs` separados: isso facilita a separação por blocos de código, e consequentemente a leitura 
  * Ainda no método de cálculo, ao invés de inicializar a variável `$valor` com o valor do produto, foram adicionados `returns` em cada condição: isso possibilita o método retornar o valor mais rapidamente, já que não é mais necessário executar o método inteiro
  * Foram trocados os valores fixos das categorias por constantes da classe `Produto`

Objetivo alcançado: conseguimos deixar o código mais descritivo, separar os métodos e manter o mesmo funcionamento. E o mais importante: tudo isso foi feito de forma incremental.

Talvez depois de um tempo outras melhorias possam sem aplicadas, mas o código já melhorou o suficiente por enquanto.

Aliás, isso é o que todos nós deveríamos fazer: ao invés de você tentar abraçar o mundo e deixar seu código perfeito, tente deixá-lo o mais simples possível (e que atenda os requisitos, claro), e vá aperfeiçoando com o tempo.

Até por que provavelmente você terá que realizar alterações nele depois, e aí você pode &#8220;aparar as arestas&#8221; e ir deixando cada vez melhor.

Só não deixe seu código para trás sem revisá-lo antes, isso com certeza vai deixar alterações futuras muito mais custosas de serem feitas.

## Certo, mas e se o prazo estiver apertado?

No ciclo de desenvolvimento de software, sempre existem os casos em que o prazo é bem apertado.

Apesar de entender que precisamos de tempo suficiente para sempre testar nosso código e escrevê-lo bem, algumas vezes realmente não há saída: precisamos entregar e ponto.

Nestes casos, precisamos sempre colocar na balança se vale a pena gastar mais tempo para projetar melhor a arquitetura, testar todas as nossas classes e revisar o código.

O que não pode acontecer é utilizar estes argumentos como desculpas para não entregar a solução.

Se há espaço para refinar o código e testá-lo, então eu recomendo que faça. Você vai agradecer um dia por ter feito isso.

Caso a entrega seja de muita urgência, desenvolva de uma forma que conseguirá entregar no prazo. Mas também não use isso como desculpa para escrever qualquer código!

Fique atento a boas práticas durante o desenvolvimento acelerado, seja nomeando suas variáveis e métodos melhor, quebrando os comportamento em classes menores, etc.

Observe uma alteração pequena usando o exemplo anterior, mas que vai ajudar a tornar o código muito mais simples:

<pre class="lang-php">class Carrinho
{
    private $vl;
    private $prods;

    // Adiciona um produto no carrinho
    // Passar um array de produtos
    public function adic($prods)
    {
        foreach ($prods as $prod) {
            // Categoria do produto -&gt; P = Promocao
            if ($prod-&gt;getCat() == 'P') {
                $vl = $prod-&gt;getVl() * 0.75;
                $this-&gt;vl += $vl;
                $this-&gt;prods[] = $prod;
                
            // Categoria do produto -&gt; B = Brinde
            } elseif ($prod-&gt;getCat() == 'B') {
                $vl = 0;
                $this-&gt;vl += $vl;
                $this-&gt;prods[] = $prod;
            
            // Sem categoria, utilizar o valor do produto
            } elseif ($prod-&gt;getCat() == '') {
                $vl = $prod-&gt;getVl();
                $this-&gt;vl += $vl;
                $this-&gt;prods[] = $prod;
            }
        }
    } 
}
</pre>

Você acha que esses comentários são importantes para o código? E se um dia algum outro desenvolvedor alterar as siglas das categorias, você acha que os comentários serão atualizados?

E se ao invés de adicionar comentários, você deixasse explícito o que cada variável e método faz por meio do nome deles?

<pre class="lang-php">class Carrinho
{
    private $valorTotal;
    private $produtos;

    public function adicionarProduto($produtos)
    {
        foreach ($produtos as $produto) {
            if ($produto-&gt;getCategoria() == 'PROMOCAO') {
                $valor = $produto-&gt;getValor() * 0.75;
                $this-&gt;valorTotal += $valor;
                $this-&gt;produtos[] = $produto;
            } elseif ($produto-&gt;getCategoria() == 'BRINDE') {
                $valor = 0;
                $this-&gt;valorTotal += $valor;
                $this-&gt;produtos[] = $produto;
            } elseif ($produto-&gt;getCategoria() == '') {
                $valor = $produto-&gt;getValor();
                $this-&gt;valorTotal += $valor;
                $this-&gt;produtos[] = $produto;
            }
        }
    } 
}
</pre>

Veja que todos os comentários foram removidos. Ao invés de escrever o comportamento da classe nos comentários, os métodos e variáveis já dizem o que fazem e para o que servem.

Por isso, por mais que o prazo seja apertado, sempre há um jeito de deixar o código mais limpo.

Só não deixe de entregar o seu trabalho no prazo tentando fazer o código perfeito, isso talvez não valha tanto a pena no final.

## Conclusão

Você provavelmente percebeu o valor de escrever código limpo.

Isso no longo prazo faz uma enorme diferença, e é uma responsabilidade que todos nós programadores precisamos estar cientes. Não basta apenas escrever código, você tem que sempre pensar que outras pessoas também irão trabalhar nele.

Por isso sempre procure aperfeiçoar suas habilidades não só para aprender outras linguagens, mas para melhorar o seu código em si, independente da linguagem que você trabalhe.

E se você quer aprender como escrever código limpo, existem alguns livros que irão explicar os principais conceitos e técnicas.

Um deles que eu recomendo é o <a href="https://www.amazon.com.br/C%C3%B3digo-Limpo-Habilidades-Pr%C3%A1ticas-Softwar/dp/8576082675/ref=sr_1_1?ie=UTF8&qid=1467162877&sr=8-1&keywords=c%C3%B3digo+limpo" target="_blank">Código Limpo, do Robert C. Martin (Uncle Bob)</a>.

Além disso, existem algumas práticas para auxiliar no projeto de classes e na implementação dos métodos, como _SOLID_ e _Object Calisthenics_.

Por fim, esta é a minha visão sobre qualidade de código, se você tiver outro ponto de vista ou algum complemento, escreva nos comentários!