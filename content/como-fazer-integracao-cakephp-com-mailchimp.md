---
title: Como fazer integração do CakePHP com Mailchimp
author: Gustavo Henrique Prado Reis
type: post
date: 2015-03-26
excerpt: Aprenda como fazer integração do Mailchimp com o framework CakePHP
url: /como-fazer-integracao-cakephp-com-mailchimp/
categories:
  - Back-end
  - PHP

---
Em um projeto que trabalhei, o cliente tinha um espaço no site para cadastro de newsletter, dessa forma ele gostaria de fazer automaticamente esse cadastro em suas listas no Mailchimp para não ter que ficar importando uma lista nova de e-mails sempre.

Dai surgiu a necessidade de pesquisar um pouco e encontrar diversas maneiras de fazer isso, algumas que até já não funcionam mais devido a versões.. Vou mostrar aqui como funcionou pra mim.

Optei por usar um plugin do <a href="https://github.com/dereuromark" rel="noreferrer">Mark S</a>. Existe uma pequena documentação junto ao repositório do github, porém achei bastante confuso.. Vamos lá!

### Instalação

Primeiramente temos que fazer a instalação do plugin no CakePHP e a geração da chave para acesso a API do Mailchimp.

Para instalar o plugin no cake é possível fazer com Composer, ou fazer o <a href="https://github.com/dereuromark/cakephp-mailchimp" rel="noreferrer">clone do repositório</a> e manualmente colocar na pasta app/vendor. Com composer basta entrar na pasta app, abrir o terminal e executar o comando:

<pre class="lang-html">composer require dereuromark/cakephp-mailchimp:1.0.*</pre>

Após feito isso o plugin já vai estar instalado (da uma conferida na pasta app/vendor). Com o plugin instalado vamos gerar a Key.

<ul class="task-list">
  <li>
    Acesse o <a href="http://mailchimp.com/" rel="noreferrer">Mailchimp</a>
  </li>
  <li>
    No menu do usuário, clique em Account
  </li>
  <li>
    Na aba Extras, selecione API KEYS
  </li>
  <li>
    Nessa tela um pouco abaixo vai ter uma tabela com suas keys, e um botão logo abaixo CREATE API KEY
  </li>
  <li>
    Após clicar neste botão sua chave será gerada, guarde este valor
  </li>
</ul>

### <a class="anchor" href="https://gist.github.com/gustavopradoreis/d0e003c8d72b76c396de#estrutura" rel="noreferrer" name="user-content-estrutura"></a>Estrutura

Pra galera mais iniciante em cake, segue uma estrutura básica com a localização dos arquivos e pastas que vamos utilizar,

<pre class="lang-html">app
--- Config
------ bootstrap.php (arquivo de configuração)
--- Console
--- Controller
------ FormularioController.php (o formulário que for utilizar)
--- Lib
--- Locale
--- Model
--- Plugin
------ Mailchimp (pasta do plugin)
--- Test
--- Vendor
--- View
------ Formulario
--------- formulario.ctp (view onde ficará a estrutura html de seu formulário)
--- Webroot
</pre>

### <a class="anchor" href="https://gist.github.com/gustavopradoreis/d0e003c8d72b76c396de#configura%C3%A7%C3%A3o" rel="noreferrer" name="user-content-configura%C3%A7%C3%A3o"></a>Configuração

Para carregar o plugin no arquivo app/config/boostrap.php você pode optar por duas opções:

<pre class="lang-html">CakePlugin::loadAll();
</pre>

Carregando todos os plugins que estiverem na pasta (app/Plugin), ou pode carregar plugins específicos da seguinte forma:

<pre class="lang-html">Plugin::load('Mailchimp');
</pre>

Após isso, coloque as seguintes configurações (ainda no arquivo bootstrap.php):

<pre class="lang-html">Configure::write('Mailchimp.defaultListId', 'ID DA SUA LISTA');
Configure::write('Mailchimp.apiKey', 'CHAVE QUE GERAMOS ANTERIORMENTE');
Configure::write('Mailchimp.defaultCampaignId', 'ID DA SUA CAMPANHA');
</pre>

Só um lembrete: o ID da lista é o que aparece na pagina &#8220;Settings -> List name and defaults&#8221;. E não o id que aparece na url quando acessamos a lista. (No site do Mailchimp esse lembrete)

### <a class="anchor" href="https://gist.github.com/gustavopradoreis/d0e003c8d72b76c396de#utiliza%C3%A7%C3%A3o" rel="noreferrer" name="user-content-utiliza%C3%A7%C3%A3o">Utilização</a>

Existem alguns métodos nesse plugin para utilização, vou mostrar como faz para incluir novos e-mails na lista. Caso queira outras operações, fique a vontade para consultar a documentação <a href="https://github.com/dereuromark/cakephp-mailchimp/blob/master/docs/Mailchimp.md" rel="noreferrer">aqui</a>!

##### <a class="anchor" href="https://gist.github.com/gustavopradoreis/d0e003c8d72b76c396de#inserir-novos-e-mails" rel="noreferrer" name="user-content-inserir-novos-e-mails"></a>INSERIR NOVOS E-MAILS

Para inserir novos e-mails, faça da seguinte forma:

_Formulário_

<pre class="lang-html">&lt;form action="&lt;?$this-&gt;webroot?&gt;newsletters/add" method="post" id="newsletterForm"&gt;
        &lt;label&gt;Recebe novidades!&lt;/label&gt;
        &lt;input type="email" placeholder="Digite seu E-mail" name="data[email]" class="email"&gt;
        &lt;input type="submit" value="Assinar" class="send"&gt;
    &lt;/form&gt;
</pre>

_Controller_

<pre class="lang-html">$MailchimpSubscriber = ClassRegistry::init('Mailchimp.MailchimpSubscriber');
$data = $this-&gt;data;
$data['source'] = 'newsletterForm';
$options = array('doubleOptin' =&gt; false, 'updateExisting' =&gt; false);
$response = $MailchimpSubscriber-&gt;subscribe($data, $options);
</pre>

Primeiro estamos inicializando o plugin. Após isso, atribuímos a variável $data, todos os valores do formulário (lembrando que ele pega o campo com name &#8220;email&#8221; do formulário) e também criamos uma posição no array com o nome do formulário.

Criamos então um array com algumas opções que o Mailchimp nos oferece em sua API, aqui utilizei duas opções mas fique livre para dar uma olhada na <a href="https://apidocs.mailchimp.com/api/1.3/listsubscribe.func.php" rel="noreferrer">documentação do mailchimp</a>. Essas duas opções servem para:

<pre class="lang-html">doubleOptin: essa opção faz com que não seja necessário enviar um e-mail solicitando o usuário a confirmar sua inscrição na lista. Por padrão é TRUE
updateExisting: simplesmente faz a atualização no e-mail se existir ao invés de inserir e-mails repetidos.
</pre>

Pronto, por final chamamos o método subscribe que faz a inserção na lista. Caso queira, pode utilizar a variável $response para manipular o retorno.
  
**_Lembrete: a inserção não ocorre de forma instantânea, demora entre 5 e 10 minutos para aparecer o e-mail na lista (no site do mailchimp)._**

Existem vários outros métodos que fazem coisas bem interessante como remover o e-mail da lista, retornar todos e-mails cadastrados e também manipulação das campanhas, veja <a href="https://github.com/dereuromark/cakephp-mailchimp/blob/master/docs/Mailchimp.md" rel="noreferrer">aqui</a>.