---
title: Formulário de e-mail e envio com PHP
author: Filipe Teixeira
type: post
date: 2015-08-18
excerpt: Como abandonar um script pronto em Perl e criar um formulário de envio de e-mail simples com PHP.
url: /formulario-de-e-mail-e-envio-com-php/
categories:
  - Código
  - O Básico
  - PHP
tags:
  - php

---
Há anos atrás, quando queríamos colocar um formulário de e-mail em nosso site, simplesmente pegávamos um script em Perl que funcionava, mas não fazíamos ideia de como as coisas aconteciam por trás. Neste post demonstrarei que é muito simples fazer a mesma coisa em PHP. Perceba que o foco é principalmente no PHP, e não necessariamente na validação do formulário ou CSS, embora usaremos algumas boas práticas de validação.

**Aviso:** O script apenas enviará o e-mail se estiver em um servidor. Você não conseguirá mandar o e-mail do localhost (No Wamp ou Xampp por exemplo).

### Criando os arquivos

Criaremos quatro arquivos que irão conter nosso script.

`O index.php`, para que a pasta sempre abra no nosso arquivo de contato (você pode renomear depois para contato.php se quiser). O arquivo `mail_ok.php`, para exibir a mensagem que o e-mail foi enviado, e o `mail_error.php`, contendo a mensagem de erro. Finalmente, o `mail_send.php`, contendo o script que envia o e-mail propriamente dito.

### index.php

No `index.php` vamos fazer o nosso formulário:

<pre class="lang-html prettyprint linenums">&lt;!DOCTYPE html&gt;
&lt;html lang="pt-br"&gt;
    &lt;head&gt;
        &lt;meta charset="utf8"&gt;
        &lt;title&gt;Contato&lt;/title&gt;
    &lt;/head&gt;
    &lt;body&gt;
        &lt;form action="mail_send.php" method="post"&gt;
            &lt;fieldset&gt;
                &lt;label for="email"&gt;E-mail: &lt;/label&gt;
                &lt;input required name="email" type="email"&gt;
            &lt;/fieldset&gt;
            &lt;fieldset&gt;
                &lt;label for="mensagem"&gt;Mensagem: &lt;/label&gt;
                &lt;textarea required name="mensagem"&gt;&lt;/textarea&gt;
            &lt;/fieldset&gt;
            &lt;fieldset&gt;
                &lt;button type="submit"&gt;Enviar&lt;/button&gt;
            &lt;/fieldset&gt;
        &lt;/form&gt;
    &lt;/body&gt;
&lt;/html&gt;</pre>

Esse formulário contém os campos `e-mail` e `mensagem`, ambos campos obrigatórios.

Vamos agora fazer o `mail_ok.php` e `mail_error.php`:

### mail_ok.php

<pre class="lang-html prettyprint linenums"> &lt;!DOCTYPE html&gt;
&lt;html lang="pt-br"&gt;
    &lt;head&gt;
        &lt;meta charset="utf8"&gt;
        &lt;title&gt;Sucesso&lt;/title&gt;
    &lt;/head&gt;
    &lt;body&gt;
        &lt;h1&gt;Sucesso&lt;/h1&gt;
        
        &lt;hr&gt;
        
        &lt;p&gt;O e-mail foi enviado com sucesso.&lt;/p&gt;
    &lt;/body&gt;
&lt;/html&gt;</pre>

### ``mail_error.php

<pre class="lang-html prettyprint linenums"> &lt;!DOCTYPE html&gt;
&lt;html lang="pt-br"&gt;
    &lt;head&gt;
        &lt;meta charset="utf8"&gt;
        &lt;title&gt;Erro&lt;/title&gt;
    &lt;/head&gt;
    &lt;body&gt;
        &lt;h1&gt;Erro&lt;/h1&gt;
        
        &lt;hr&gt;
        
        &lt;p&gt;Houve um erro no envio do e-mail. &lt;a href="index.php"&gt;Tentar novamente&lt;/a&gt;.&lt;/p&gt;
    &lt;/body&gt;
&lt;/html&gt;</pre>

Os arquivos anteriores mostram mensagens se o e-mail foi enviado. O seguinte script PHP irá redirecionar para eles:

### mail_send.php

<pre class="lang_php prettyprint linenums">&lt;?php

function pegaValor($valor) {
    return isset($_POST[$valor]) ? $_POST[$valor] : '';
}

function validaEmail($email) {
    return filter_var($email, FILTER_VALIDATE_EMAIL);
}

function enviaEmail($de, $assunto, $mensagem, $para, $email_servidor) {
    $headers = "From: $email_servidor\r\n" .
               "Reply-To: $de\r\n" .
               "X-Mailer: PHP/" . phpversion() . "\r\n";
    $headers .= "MIME-Version: 1.0\r\n";
    $headers .= "Content-Type: text/html; charset=ISO-8859-1\r\n";
  
  mail($para, $assunto, nl2br($mensagem), $headers);
}

$email_servidor = "email@servidor.com";
$para = "seu@email.com";
$de = pegaValor("email");
$mensagem = pegaValor("mensagem");
$assunto = "Assunto da mensagem";

?&gt;</pre>

Este último script define três funções:

  * `pegaValor`: se existir, pega a váriavel enviada via &#8216;post&#8217;, senão, retorna uma string vazia;
  * `validaEmail: `retorna se o e-mail é válido;
  * `enviaEmail` : chama a função _mail_ do PHP com as variáveis que definimos.

As variáveis `$de` e `$mensagem` irão pegar os valores enviados pelo formulário. Nas variáveis `$email_servidor` e `$para` você deverá colocar seu e-mail do servidor e o e-mail para o qual será enviado o formulário, respectivamente. A variável `$assunto` será, obviamente, o assunto da mensagem.

### Corpo do script

<pre class="lang_php prettyprint linenums">if ($nome && validaEmail($de) && $mensagem) {
    enviaEmail($de, $assunto, $mensagem, $para, $email_servidor);
    $pagina = "mail_ok.php";
} else {
    $pagina = "mail_error.php";
}

header("location:$pagina");</pre>

Esta parte do script é o controle de fluxo. Se as variáveis não forem vazias e o e-mail for válido, enviará o e-mail e atribuirá a variável `$pagina` para `mail_ok.php`. Caso contrário, a variável `$pagina` será `mail_error.php. `E finalmente, redirecionaremos a página com a função `header`.

**Aviso:** É de suma importância verificar no seu editor de texto se a codificação é **UTF-8 sem BOM**. Se não for, o script irá enviar um espaço em branco antes do cabeçalho de redirecionamente, e irá aparecer o seguinte erro:

`Cannot modify header information - headers already sent`

Com isso nosso script PHP está pronto. Adeus Perl!