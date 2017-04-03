---
title: API de cotações de Bolsa de Valores, Dólar e Euro
author: Henrique Schreiner
type: post
date: 2014-12-29
excerpt: Aprenda a utilizar uma API para consulta de cotações com PHP.
url: /api-de-cotacoes-de-bolsa-de-valores-dolar-e-euro/
categories:
  - Back-end
  - PHP

---
Hoje em dia é muito comum os sites terem um widget ou uma barra lateral com informações de cotações do dólar, euro e os principais mercados financeiros do mundo.

Como o mercado oscila muito, essas informações são atualizadas constantemente, de minuto a minuto. Se você está pensando em mostrar essas informações em seu site, com certeza vai precisar de uma API para consultar estes dados em tempo real.

O pessoal da <a href="http://agenciaideias.com.br" target="_blank">Agência Ideias</a> criou uma <a href="http://developers.agenciaideias.com.br/cotacoes" target="_blank">API</a> bem legal para consulta de cotações em tempo real, sendo o valor do euro e do dólar referentes aos valores de compra dessas moedas. O formato do retorno da consulta pode ser <a href="http://developers.agenciaideias.com.br/cotacoes/json" target="_blank">JSON</a> ou <a href="http://developers.agenciaideias.com.br/cotacoes/xml" target="_blank">XML</a>, dependendo da necessidade de sua aplicação. Para a nossa classe em PHP, vamos utilizar o formato de retorno em JSON.

Vamos criar um novo arquivo em PHP com o nome **Quotation.php**. Nele vamos criar a classe **Quotation**. Logo no início da classe, vamos declarar duas variáves estáticas que serão usadas por nossa classe. Uma delas é o endereço da API e a outra é o conteúdo que será retornado por ela.

<pre class="lang-php">class Quotation {

  private static $apiUrl = "http://developers.agenciaideias.com.br/cotacoes/json";
  private static $content;

}
</pre>

Em seguida, vamos criar um método estático para preparar nossa classe para a interação com a API:

<pre class="prettyprint php">public static function init() {

  self::$content = file_get_contents(self::$apiUrl);
  self::$content = json_decode(self::$content);
}
</pre>

O conteúdo do retorno da API é semelhante a este:

<pre class="lang-javascript">{
  "bovespa":{
    "cotacao":"46955",
    "variacao":"-0.14"
  },
  "dolar": {
    "cotacao":"2.7500",
    "variacao":"+2.34"
  },
  "euro":{
    "cotacao":"3.4427",
    "variacao":"+2.65"
  },
  "atualizacao":"16\/12\/14   - 14:08"
}
</pre>

Para que possamos organizar melhor as informações, vamos criar um método para cada tipo de cotação:

<pre class="lang-php">public static function dolar() {

        self::init();
        return array(
            "quotation" =&gt; self::$content-&gt;dolar-&gt;cotacao,
            "variation" =&gt; self::$content-&gt;dolar-&gt;variacao,
            "status" =&gt; self::getVariation(self::$content-&gt;dolar-&gt;variacao)
        );
    }

    public static function bovespa() {

        self::init();
        return array(
            "quotation" =&gt; self::$content-&gt;bovespa-&gt;cotacao,
            "variation" =&gt; self::$content-&gt;bovespa-&gt;variacao,
            "status" =&gt; self::getVariation(self::$content-&gt;bovespa-&gt;variacao)
        );
    }

    public static function euro() {

        self::init();
        return array(
            "quotation" =&gt; self::$content-&gt;euro-&gt;cotacao,
            "variation" =&gt; self::$content-&gt;euro-&gt;variacao,
            "status" =&gt; self::getVariation(self::$content-&gt;euro-&gt;variacao)
        );
    }

</pre>

Cada um destes métodos utiliza o método **init()** que inicializa a interação da nossa classe com a API e guarda o retorno na variável estática de classe **self::$content**.

Por último, vamos criar um último método apenas para verificar se a variação teve uma alta ou uma baixa:

<pre class="lang-php">public static function getVariation($variation) {
        if (strpos($variation, "+")) {
            return "+";
        } else {
            return "-";
        }
  }
</pre>

Como exemplo, vamos verificar a cotação do dólar:

<pre class="lang-php">$dolar = Quotation::dolar();
  echo "Cotação do Dólar:\n";
  echo "Valor: R$" . number_format($dolar['quotation'], 2, ',', '.') . "\n";
  echo "Variação: {$dolar['variation']}";
</pre>

A classe pode ser baixada na íntegra <a title="QuotationAPI" href="https://github.com/hmschreiner/QuotationAPI" target="_blank">aqui</a>.

Espero que tenham gostado do post. **Não deixem de comentar e deixar suas dúvidas.**