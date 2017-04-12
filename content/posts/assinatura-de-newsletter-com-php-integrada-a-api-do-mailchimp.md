---
title: Assinatura de newsletter com PHP integrada à API do Mailchimp
author: Gustavo Straube
type: post
date: 2015-02-10
excerpt: O Mailchimp é um serviço bem bacana para gerenciar newsletters — e tem uma versão gratuita que atende muito bem quem tem até 2 mil assinantes. Vou dar uma ideia, através de um exemplo básico, do que é possível fazer com a API do serviço, usando PHP.
url: /assinatura-de-newsletter-com-php-integrada-a-api-do-mailchimp/
categories:
  - PHP
tags:
  - api
  - desenvolvimento
  - desenvolvimento web
  - E-mail Marketing
  - mailchimp
  - Na Prática
  - php

---
O Mailchimp tem uma <a href="https://apidocs.mailchimp.com/" target="_blank">API bem completa</a>. Arrisco dizer que é possível fazer uma interface com muitas das funcionalidades de gerenciamento de listas, envios, etc usando a API — fica a dica para quem quiser desenvolver uma aplicação explorando alguma lacuna que o painel do Mailchimp deixa a desejar.

Eu sabia da existência da API faz algum tempo, mas usava uma função simples de exportação de CSV em alguns projetos. Mas dependendo da frequência de disparo das newsletters, exportar um arquivo e importar no Mailchimp começa a ser um tanto trabalhoso. Então esse é o meu caso de uso: um formulário de newsletter.

Aí alguém diz: “Mas você está reinventando a roda! O Mailchimp te dá um formulário pronto, você não precisa integrar com a API, basta gerar o código, copiar e colar.” E eu respondo: “Sim, existe essa possibilidade, mas e se além de enviar para o Mailchimp você precisa gravar na sua base de dados esses e-mails? E se a opção de assinatura da newsletter é um checkbox (opt-in) em um formulário de cadastro?” Acho que assim temos uma ideia melhor de quando usar a API para a captação de e-mails.

Então, vamos botar a mão no código:

## 1. Chave da API

Mas, ops! Antes de ir para a programação, toda integração com a API precisa de uma chave para autenticação. Para gerar essa chave você precisa entrar na sua conta do Mailcimp (se você não tem uma conta, criar uma nova é bem simples e não tem custo), e seguir o seguinte caminho:

  1. no menu do usuário (canto direito superior), ir em **“Account”**;
  2. na aba **“Extras”**, selecionar **“API keys”**;
  3. nessa tela você pode criar uma chave (**“Create API key”**).

A chave gerada é sua forma de autenticação na API, então deve ser mantida em segurança.

## 2 Instalação

Existe um <a href="https://bitbucket.org/mailchimp/mailchimp-api-php" target="_blank">SDK PHP oficial do Mailchimp</a>. Você pode instalar <a href="http://tableless.com.br/composer-para-iniciantes/" target="_blank">usando o Composer</a>, incluindo a seguinte dependência no seu arquivo **composer.json**:

<pre>"mailchimp/mailchimp": "2.0.*"</pre>

E executando o **composer install** (ou **update** se for um projeto já existente).

Mas se você não está usando o Composer (está desenvolvendo um tema ou plugin de WordPress, por exemplo) pode baixar o <a href="https://bitbucket.org/mailchimp/mailchimp-api-php/get/master.zip" target="_blank">pacote com o SDK</a>. Caso opte por esse tipo de instalação, provavelmente vai ser necessário incluir no seu código um **require** para a classe principal: **src/Mailchimp.php**.

## 3 Integrando

Vamos começar usando um formulário HTML simples, com apenas dois inputs: e-mail e cidade. Estou optando por usar esses dados, porque quero mostrar como usar campos personalizados com a API. O arquivo **newsletter.php** deve ser algo assim:

<pre>&lt;form action="mailchimp.php" method="post"&gt;
  &lt;h1&gt;Newsletter&lt;/h1&gt;
  &lt;label&gt;E-mail&lt;/label&gt;
  &lt;input type="email" name="email"&gt;&lt;br&gt;
  &lt;label&gt;Cidade&lt;/label&gt;
  &lt;input type="text" name="city"&gt;&lt;br&gt;
  &lt;button type="submit"&gt;Assinar!&lt;/button&gt;
&lt;/form&gt;</pre>

Obs.: Como o foco é o uso da API, não estou me preocupando com a estética do formulário, ok? 😉

Seguindo vamos para o arquivo **mailchimp.php**, que receberá os dados enviados pele formulário:

Primeiro começamos definindo algumas configurações, usando constantes:

<pre>define('MAILCHIMP_API_KEY',  ''); // Sua chave da API
define('MAILCHIMP_LIST_ID',  ''); // O ID da sua lista
define('MAILCHIMP_CITY_TAG', ''); // A tag do campo personalizado que usaremos</pre>

Tem duas informações novas aqui: o **ID da lista** e a **tag do campo** personalizado. Conseguimos esses dados no painel do Mailchimp, assim:

### ID da lista

Na lista para qual você quer adicionar as assinaturas (se você não tem nenhuma lista na sua conta, precisará criar uma antes de continuar), no menu **“Settings”** vá até **“List name and defaults”**. Nessa tela, do lado direto, existe uma pequena sessão com o título **“List ID”**, dali você vai copiar um código, tipicamente formado por letras e números.

### Tag do campo

Ainda na lista e novamente no menu **“Settings”** você vai até o link **“List fields and \*|MERGE|\* tags”**. Ali você vai copiar a tag correspondente ao campo usado no form, que no nosso exemplo é o **“Cidade”**. O que você precisa é o valor que está no input, algo parecido com **“MMERGE3”** — esse número no final muda de um campo para outro.

Caso você ainda não tenha criado nenhum campo personalizado, você pode criar um agora.

**Continuando com o código&#8230;**

Para usar um nome mais claro no código (e evitar usar as globais do PHP), vou repassar o conteúdo recebido do form para uma nova variável:

<pre>$form = $_POST;</pre>

Na sequência vou fazer uma validação bem básica dos dados, apenas verificando se os campos foram preenchidos. Provavelmente você vai querer fazer algo mais eficaz, como verificar se o formato do e-mail é válido ou se o nome da cidade tem um mínimo de caracteres, por exemplo.

<pre>if (!empty($form['email']) && !empty($form['city'])) {
  $mailchimp = new Mailchimp(MAILCHIMP_API_KEY);
  $lists = new Mailchimp_Lists($mailchimp);
  $email = [
    'email' =&gt; $form['email'],
  ];
  $merge = [
    MAILCHIMP_CITY_TAG =&gt; $form['city'],
  ];
  $lists-&gt;subscribe(
    MAILCHIMP_LIST_ID, // ID da lista
    $email,            // O e-mail do assinante
    $merge,            // Campos personalizados
    'html',            // Tipo de e-mail recebido
    false              // Confirmar assinatura por e-mail (opt-in duplo)?
  );
  echo 'Newsletter assinada!';
} else {
  echo 'Por favor preencha os campos. &lt;a href="newsletter.php"&gt;Voltar&lt;/a&gt;';
}</pre>

Se você usou um e-mail que ainda não está na lista para testar o formulário, vai ver que ele funciona a primeira vez, mas nos envios seguintes o PHP indica uma exceção. Se o teste foi feito com um e-mail já cadastrado, nem o primeiro envio funcionou.

Isso acontece porque o SDK do Mailchimp usa exceções para indicar qualquer coisa que impeça a chamada à API de ser executada com sucesso, incluindo a tentativa de assinatura com um e-mail já cadastrado. Para tratar esses casos, vamos fazer a seguinte alteração no código que está dentro do **if**:

<pre>try {
    $mailchimp = …

    ...

    echo 'Newsletter assinada!';
  } catch (Mailchimp_List_AlreadySubscribed $e) {
    echo 'Você já assinou a newsletter.';
  } catch (Mailchimp_Email_AlreadySubscribed $e) {
    echo 'Você já assinou a newsletter.';
  } catch (Mailchimp_Email_NotExists $e) {
    echo 'O e-mail informado não existe.';
  } catch (Mailchimp_Invalid_Email $e) {
    echo 'O e-mail informado é inválido.';
  } catch (Mailchimp_List_InvalidImport $e) {
    echo 'Dados inválidos, provavelmente seu e-mail.';
  } catch (Exception $e) {
    echo $e-&gt;getMessage(); // Não mostre isso para o usuário
  }</pre>

Dessa forma conseguimos tratar algumas exceções mais comuns que o SDK pode lançar e devolver um feedback para o usuário, assim ele é capaz de corrigir as informações e tentar novamente.

Para os outros casos, fazemos um tratamento genérico apenas exibindo a mensagem da exceção. Isso é o suficiente para um exemplo como esse aqui, mas não é o ideal para um código real que vai para produção, porque pode expôr bugs e informações sensíveis da sua aplicação. Então recomendo fazer um tratamento mais adequado, como gravar em um arquivo de log ou <a href="http://tableless.com.br/rastreando-excecoes-no-php-com-o-airbrake/" target="_blank">usar um rastreador de bugs</a>.

Agora quando você submeter o formulário com um e-mail já cadastrado, verá a mensagem: **“Você já assinou a newsletter.”**

## Conclusão

Essa integração é bem básica, mas dá uma ideia do que é possível fazer com a API do Mailchimp. Como falei no início, você pode ir muito mais além do que um formulário de captação de e-mails. E mesmo em se tratando da assinatura de listas, você pode refinar o código que apresentei e integrar em um formulário de cadastro do seu site, e até adicionar novos campos.

Caso tenha alguma dúvida ou encontre algum erro, fique a vontade para usar os comentários.

Ah! O código completo está disponível no GitHub: <a href="https://github.com/straube/mailchimp-sample-form" target="_blank">https://github.com/straube/mailchimp-sample-form</a>