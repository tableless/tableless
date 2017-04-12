---
title: Formulário sem Model no CakePHP 3.x
author: Eduardo Abreu
type: post
date: 2015-06-16
url: /formulario-sem-model-no-cakephp-3-x/
categories:
  - Back-end
  - Código
  - PHP
tags:
  - cakephp
  - cakephp3
  - frameworks
  - php

---
Requisitos do artigos:
  
&#8211; Ter o CakePHP 3 instalado ( <a href="https://medium.com/@eabreusantos/instalando-o-cakephp-3-0-2f2a155cb8b1" target="_blank">Artigo de como instalar o Cakephp 3.x</a>)

O que aprenderemos:

  * Como trabalhar com formulários que não necessitam de um Model.
  * Criar uma página de contato.

### Formulários

Na maioria das vezes, trabalhamos com formulários relacionados a um Model para persistir dados. Outras vezes precisamos validar os dados de um formulário onde não há persistência, como é no caso de um Formulário de Contato. Para tal tarefa, o CakePHP 3.x nos disponibiliza o que chamamos de **Modelless Forms**.

Para começar, precisamos criar uma pasta chamada &#8216;Forms&#8217; dentro do diretório &#8216;app\src&#8217;. Para exemplificar vamos assumir que iremos criar um formulário de contato básico com nome, email e mensagem.

Na pasta Forms, crie um arquivo chamado &#8216;ContactForm.php&#8217; com o seguinte conteúdo:

<pre class="lang-php">namespace App\Form;
use Cake\Form\Form;
use Cake\Form\Schema;
use Cake\Validation\Validator;
class ContactForm extends Form
{
 /*
 * Cria schema do formulário
 * @param Schema object
 * @return Schema object
 */
 protected function _buildSchema(Schema $schema)
{
 return $schema-&gt;addField('name', 'string')
 -&gt;addField('email', ['type' =&gt; 'string'])
 -&gt;addField('body', ['type' =&gt; 'text']);
}
/*
*Add regras de validação aos campos do formulário
* @param Validator object
* @return Validator object
*/
protected function _buildValidator(Validator $validator)
{
 return $validator-&gt;add('name', 'length', [
 'rule' =&gt; ['minLength', 10],
 'message' =&gt; 'Campo nome é obrigatório'
 ])-&gt;add('email', 'format', [
 'rule' =&gt; 'email',
 'message' =&gt; 'Endereço de e-mail inválido',
 ]);
}
/*
* Envia e-mail com os dados do contato
* @param array $data dados da requisição
* @return bool true caso tenha enviado o e-mail com sucesso
*/
protected function _execute(array $data)e
{
// Send an email.
return true;
}
}</pre>

Linha 1:4 — Declaramos o namespace e importamos classes que iremos utilizar.

Linha 5 — Declaração da classe, obrigatório o sufixo Form tanto na declaração da classe como no nome do arquivo, Modelless Forms devem obrigatoriamente estender da classe Form.

Linha 12:17 — Método &#8216;**_buildSchema**&#8216;, recebe como parâmetro um objeto do tipo Schema. É usado para definir o esquema de dados que será utilizado pelo FormHelper para criar o formulário html. É possível definir o tipo do campo, tamanho do campo e precisão. Este método deve retornar o próprio objeto Schema.

Linha 23:32 — Método **&#8216;_buildValidator**&#8216;, recebe como parâmetro um objeto do tipo Validator. É usado para definir o esquema de validação do formulário quando processado. É possível definir várias regras de validação para mesmo campo. Este método deve retornar o próprio objeto Validator. Veja mais regras e opções em: <a href="http://book.cakephp.org/3.0/en/core-libraries/validation.html" target="_blank">http://book.cakephp.org/3.0/en/core-libraries/validation.html</a>. Em breve irei publicar um artigo sobre Validação de dados.

Linha 38:~ — Método &#8216;**_execute**&#8216;, recebe como parâmetro um array contendo os dados da requisição ou no caso os dados do formulário que o usuário preencheu. O retorno deste método é de acordo com a implementação.

### Processando o Formulário

Uma vez definida a classe do formulário, temos agora de processa-lo, para isto podemos utilizar um Controller. Na pasta &#8216;app\src\Controller&#8217; crie um arquivo chamado &#8216;ContactController.php&#8217; com o seguinte conteúdo.

<pre class="lang-php">namespace App\Controller;
use App\Controller\AppController;
use App\Form\ContactForm;
class ContactController extends AppController
{
  /*
  * Exibe e processa o formulário de contato caso seja uma requisição post
  * @return void\Response
  */
public function index()
{
 $contact = new ContactForm();
 if ($this-&gt;request-&gt;is('post')) {
 if ($contact-&gt;execute($this-&gt;request-&gt;data)) {
 $this-&gt;Flash-&gt;success('Mensagem enviado, aguarde nosso retorno.');
} else {
 $this-&gt;Flash-&gt;error('Ocorreu um problema ao enviar sua mensagem.');
}
}
 $this-&gt;set('contact', $contact);
}
}</pre>

Linha 13 — Verificamos se a requisição é do tipo &#8216;POST&#8217;.

Linha 14 — Caso seja, tentamos processar o formulário executando o método &#8216;execute()&#8217; que recebe como parâmetro os dados da requisição que estará disponível no método &#8216;\_execute&#8217; do Form. Ao executar o método &#8216;execute&#8217;, automaticamente o formulário irá tentar validar os dados de acordo com sua implementação do método &#8216;\_buildValidator&#8217;, se a validação passar, só então o método &#8216;_execute&#8217; é chamado.

Linha 20 — Envia o objeto do formulário à view para ser utilizado no FormHelper.

### Capturando erros de validação

Para capturar os erros de validação, utilize o método &#8216;errors()&#8217; do objeto do formulário, veja abaixo um exemplo:

<pre class="lang-php ">// Na action do controller
public function index()
{
 $contact = new ContactForm();
 $erros = [];
 if ($this-&gt;request-&gt;is('post')) {
 if ($contact-&gt;execute($this-&gt;request-&gt;data)) {
 $this-&gt;Flash-&gt;success('Mensagem enviado, aguarde nosso retorno.');
} else {
//Captura <span class="hiddenGrammarError">erros
 $erros</span> = $contact-&gt;errors();
 $this-&gt;Flash-&gt;error('Ocorreu um problema ao enviar sua mensagem.');
}
}
 $this-&gt;set('contact', $contact);
 $this-&gt;set('erros',$erros);
}</pre>

O método &#8216;errors&#8217; retorna um array com a listagem de campos que não estão válidos, sendo os índices os nomes dos campos e os valores as mensagens de erro.

### Exibição do Formulário

Para que o formulário seja exibido para usuário, crie uma view no diretório &#8216;app\src\View\Template\Contact&#8217; com o nome &#8216;index.ctp&#8217; e o seguinte conteúdo:

Por enquanto é só galera, em breve irei publicar como enviar os dados do formulário para um e-mail.

Qualquer dúvida, estou a disposição para ajudar.

Abraços!