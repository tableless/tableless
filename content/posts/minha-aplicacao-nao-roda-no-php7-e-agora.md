+++
authors = "Felipe Braz"
canonical = ""
sponsor = "kinghost"
categories = ["back-end,publieditorial"]
date = "2019-01-08T10:13:10-02:00"
excerpt = "Rodando sistemas legados de PHP usando o PHP5 Compatibility Layer via Composer."
image = "https://i.imgur.com/kh64ggK.jpg"
publishdate = "2019-01-08T10:13:10-02:00"
tags = ["php"]
title = "Minha aplicação não roda no PHP7, e agora?"
type = "post"
+++

Creio que quase todo os desenvolvedores com um certo tempo de profissão têm que lidar com aplicações legadas. Para esta situação, temos dois cenários. 

O primeiro é manter sistemas escritos em linguagens erroneamente consideradas obsoletas, tais como perl, cobol e afins.

Este cenário não é necessariamente ruim, pois código não é algo perecível que vai se deteriorar com o tempo. Enquanto as regras de negócio não mudarem, um código de décadas atrás é perfeitamente utilizável! Mesmo mudanças pequenas podem ser implementadas sem muito custo de desenvolvimento.

Talvez o maior exemplo disso seja a quantidade de sistemas escritos e mantidos em cobol, existindo até eventos de nível global exclusivamente sobre esta linguagem.

O segundo cenário são sistemas escritos e mantidos em versões descontinuadas de linguagens de programação. Este é o caso que deve, ou ao menos deveria, gerar grande preocupação, pois além de perder as melhorias de código provenientes da atualização, existem ainda questões como segurança e performance.

O mais alarmante é que trabalhando há mais de 10 anos com ambiente de hospedagem, noto que para aplicações escritas em PHP o segundo caso é, infelizmente, o mais comum. Estes dados são embasados por respeitadas empresas de estatísticas de aplicações web, que demonstram que [quase 75% das aplicações em PHP](https://w3techs.com/technologies/details/pl-php/all/all) ainda rodam sob a já descontinuada versão 5!

A performance do PHP7 chega a ser [8 vezes melhor](https://www.phoronix.com/scan.php?page=news_item&px=PHP-7.3-Performance-Benchmarks) do que o PHP5, sendo que a própria redução de custo com servidores já deveria ser suficiente para justificar o tempo dispensado na mudança.

Sendo que recentemente tive a experiência de migrar aplicações críticas do PHP 5.3 para o PHP7, gostaria de compartilhar alguns aprendizados e soluções encontradas.

Primeiramente tive que passar na página oficial do PHP para verificar o que mudou entre cada versão minoritária. A lista é grande, e inclui muitos novos recursos, porém o que potencialmente pode quebrar uma aplicação são as funções descontinuadas.

Abaixo um resumo do que foi removido do PHP 5.3 até o 7.X

- [funções para Regex POSIX](http://php.net/manual/pt_BR/ref.regex.php);
- [session_register](http://php.net/session_register);
- [session_unregister](http://php.net/session_unregister);
- [funções de banco MySQL](http://php.net/manual/pt_BR/ref.mysql.php);
- [funções de banco Microsoft SQL Server](http://php.net/manual/pt_BR/ref.mssql.php);

Em um cenário ideal, seria necessário substituir em todo o código da aplicação para funções compatíveis, como usar preg_match no lugar de ereg, ou [PDO](http://php.net/pdo) para as funções de mysql ou mssql.

Porém o tempo necessário para esta alteração tende a ser elevado, sem contar o alto risco de algo parar de funcionar.

Tendo isso em mente, pensei em uma solução que pudesse ser implementada de forma genérica, algum tipo de camada de compatibilidade que permitiria que as funções descontinuadas pudessem ser utilizadas nas últimas versões do PHP, isso permitiria aplicar a solução rapidamente em diversas aplicações.

Desta ideia nasceu a biblioteca [PHP5 Compatibility Layer](https://github.com/fbraz3/php5-compatibility-layer), ao qual disponibilizo para quem necessitar migrar de versão ou mesmo efetuar benchmarkings com a aplicação com php7.

Para instalar a biblioteca, pode ser utilizado o [composer](https://getcomposer.org/).

```bash
composer require fbraz3/php5-compatibility-layer
```

A estrutura de diretórios ficará parecida com esta abaixo:

![](https://i.imgur.com/dQ7dKy1.png)

```php
echo 'Versão Atual do PHP: '.phpversion().PHP_EOL;

if(!function_exists('ereg')){
  echo 'ereg não disponível!'.PHP_EOL;
}

require_once(__DIR__.'/vendor/autoload.php');

$res = ereg('ma(c|ç)(a|ã)', 'maçã');
var_dump($res);
```

Ao rodar o arquivo, temos o resultado.

![](https://i.imgur.com/zILVqkf.png)

Vamos agora, para um exemplo mais complexo, envolvendo conexão a banco de dados.

Para começar, criei uma tabela com alguns registros de exemplo

![](https://i.imgur.com/1vfHUga.png)

Depois criei o arquivo mysql.php para utilizar as funções de banco legadas.

```php
echo 'Versão Atual do PHP: ' . phpversion() . PHP_EOL;

if(!function_exists('mysql_connect')){
    echo 'mysql_connect não disponível!'.PHP_EOL;
}

require_once(__DIR__.'/vendor/autoload.php');

$conn = mysql_connect('127.0.0.1', 'root', *********);
if (!$conn) {
    echo "Unable to connect to DB: " . mysql_error();
    exit;
}

if (!mysql_select_db("teste")) {
    echo "Unable to select database teste: " . mysql_error();
    exit;
}

$sql = "SELECT * FROM teste";

$result = mysql_query($sql);

if (!$result) {
    echo "Could not successfully run query ($sql) from DB: " . mysql_error();
    exit;
}

while ($row = mysql_fetch_assoc($result)) {
    echo $row['id'] . ' -> ' . $row['cor'] . PHP_EOL;
}

mysql_free_result($result);
```

Ao rodar o código via linha de comando, nota-se que ele é executado de forma totalmente transparente.

![](https://i.imgur.com/Nj90zpc.png)

Tudo funcionando corretamente, mas e a performance?

Como em qualquer camada de compatibilidade, não há como negar que haverá uma pequena perda de performance se comparar com um código rodando 100% escrito com as funções nativas do PHP7. Porém deve-se levar em consideração que as próprias otimizações desta última versão devem compensar, e até mesmo superar, o pequeno decréscimo do uso desta camada de compatibilidade.

E você, já necessitou migrar versões de aplicações legadas? compartilhe sua experiência com a gente!
