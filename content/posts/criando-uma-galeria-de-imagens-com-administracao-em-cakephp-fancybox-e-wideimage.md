---
title: Criando uma galeria de imagens com administração em CakePHP, Fancybox e WideImage)
author: Erik Figueiredo
type: post
date: 2014-04-27
excerpt: Criando uma galeria de imagens com painel de administração e separada por álbuns de imagens com administração em CakePHP, Fancybox e WideImage.
url: /criando-uma-galeria-de-imagens-com-administracao-em-cakephp-fancybox-e-wideimage/
dsq_thread_id: 2633907916
categories:
  - Back-end
  - PHP
tags:
  - cakephp
  - images
  - php

---
Eu sou da opinião que todo bom desenvolvedor frontend tem que ter pelo menos uma noção de backend, e o contrário também tem que acontecer, é comum as pessoas virem me perguntar como que faz pra fazer o Fancybox funcionar no CakePHP, ou como que eu integro um plugin para Jquery no site, puxa, a maioria das vezes é adicionar um seletor, chamar o javascript no Html e configurar de acordo com a documentação, vamos ver se simplifico pra vocês.

A ideia é criar uma galeria de imagens com painel de administração e separada por álbuns. Iremos instalar também o DebugKit pra medir o uso de memória do CakePHP e saber se a nossa aplicação está pesada ou não.

### Para quem o CakePHP é interessante?

O CakePHP é interessante para devs backend que precisam ganhar tempo ao desenvolver ou querem entender como funciona o esquema de MVC.

Também é interessante para os devs frontend que precisam automatizar algumas tarefas, entender como é o mundo do backend e até ganhar tempo com o sistema de temas, layouts e view do CakePHP (camada V).

### O que vamos usar?

Vamos precisar de:

  * Uma cópia do CakePHP (<http://cakephp.org/>, a direita tem uma palavra grande escrito Download com o link para a versão estável mais recente.)
  * Uma cópia do Fancybox (<http://fancyapps.com/fancybox/#license>, botãozinho azul!)
  * O DebugKit (<https://github.com/cakephp/debug_kit>, na lateral direita tem um link chamado “Download ZIP”)
  * O WideImage (<http://wideimage.sourceforge.net/download/>, aonde está escrito “download it”, baixe só o lib (terceiro da lista))
  * Um desenvolvedor web
  * Água
  * Pó de café
  * Uma cafeteira

### Modo de preparo

Primeiro você pega a água, o pó de café e a cafeteira pra fazer um café esperto e acompanhar este tutorial.

**Preparando o ambiente!**

  1. Em seguida, descompacte o CakePHP no seu servidor local (eu uso o Xampp: <https://www.apachefriends.org/pt_br/index.html>) para facilitar aqui.
  2. Descompacte o DebugKit na pasta app/Plugin do CakePHP e renomeie o diretório **debug_kit-master** para **DebugKit**
  3. O FancyBox vai em _app/webroot_, mas apenas a pasta source, e renomeie para fancy.
  4. O WideImage pode ir em _app/Vendor/wideimage_ e dentro os arquivos dele de forma que o WideImage.php fique disponível em _app/Vendor/wideimage/WideImage.php_

Agora que temos todos os arquivos, vamos ativar o DebugKit pra poder ter as métricas de uso de memória, execução dos SQLs e outros dados.

  1. Abra o arquivo _app/Config/bootstrap.php_ e cole o código abaixo (cod.1) na linha 72
  2. Após isso abra o AppController.php (em _app/Controller_) e cole o bloco cod.2 na linha 35, entre as chaves ({}) da classe AppController.

**Cod.1::**

<pre>CakePlugin::load('DebugKit');</pre>

**Cod.2::**

<pre>public $components = array(
'DebugKit.Toolbar',
'Session'
);
</pre>

Se acessar sua aplicação agora vai ver que temos um pequeno botão no canto superior direito, ao clicar nele você já tem acesso aos dados da sua aplicação, em timer você vê o uso de memória.

Pra fechar, acesse o core.php em app/Config, procure e descomente a linha a seguir (aqui era a 152) removendo as barras do começo (//)

<pre>Configure::write('Routing.prefixes', array('admin'));</pre>

**Preparando a estrutura**

Pra começar vamos precisar de um banco de dados (vamos usar o MySql), execute o código abaixo (se quiser, use algo como PHPMyAdmin para ajudar) pra criar as tabelas:

**Cod.3:**

<pre>-- --------------------------------------------------------

--
-- Estrutura da tabela `albuns`
--

CREATE TABLE IF NOT EXISTS `albuns` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `titulo` varchar(255) NOT NULL,
  `created` datetime NOT NULL,
  `modified` datetime NOT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=latin1 AUTO_INCREMENT=1 ;

-- --------------------------------------------------------

--
-- Estrutura da tabela `imagens`
--

CREATE TABLE IF NOT EXISTS `imagens` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `url` varchar(250) NOT NULL,
  `titulo` varchar(250) NOT NULL,
  `descricao` text NOT NULL,
  `albun_id` int(11) NOT NULL,
  `created` datetime NOT NULL,
  `modified` datetime NOT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=latin1 AUTO_INCREMENT=1 ;

</pre>

Preencha as linhas que comentei (host, login, password e database), com isso já temos o banco de dados também conectado, para verificar, acesse a aplicação no navegador e verifique a última mensagem dos blocos coloridos.

Para finalizar esta etapa de preparação, vamos criar os arquivos da galeria:

Em app/Model crie Albun.php e Imagen.php (e sim, com n, já que o CakePHP trabalha com singular e plural em inglês, até da pra mudar isso, mas o artigo já vai ficar enorme).

Em app/Controller crie AlbunsController.php e ImagensController.php

Em app/View crie 2 pastas (Albuns e Imagens) com 3 arquivos dentro de cada:

  * admin_novo.ctp
  * admin_editar.ctp
  * admin_index.ctp

E apenas na pasta Albuns, crie mais 2 arquivos além dos dois que devem estar dentro dela e da Imagens:

  * ver.ctp
  * index.ctp

A partir deste ponto é interessante que você conheça um pouco sobre MVC. Aqui vai uma dica: [escrevi sobre isso aqui][1]. Não precisa fazer o exemplo todo, apenas entender como é.

**Relacionando as imagens com os albuns**

Em primeiro lugar precisamos entender como as imagens se relacionam com cada álbum, a própria documentação do CakePHP já fala sobre isso (<http://book.cakephp.org/2.0/en/models/associations-linking-models-together.html>), infelizmente está em inglês, vou eu mesmo mostrar como é.

Temos 4 tipos possíveis de relacionamento entre tabelas.

Um para um &#8211; hasOne
  
Um para muitos &#8211; hasMany
  
Muitos para um &#8211; belongTo
  
Muitos para muitos – hasAndBelongsToMany ou HABTM
  
Se você ler com calma já vai ver que é fácil de definir relacionamentos, no nosso caso imagens tem um álbum ou Muitos para Um, indo ao contrário, álbum te muitas imagens ou Um para Muitos, logo:

> Album hasMany Imagem
  
> Imagems belongsTo Album

Entendeu a lógica por traz de definir os relacionamentos? Então vamos informar isso nos models.

Abra os arquivos Album.php e Imagem.php que estão em app/Model e vamos configurar:

**Cod. 5:**

<pre class="lang-php">//Albun.php

class Albun extends AppModel
{
    public $hasMany = array('Imagen');
}

// Imagen .php

class Imagen extends AppModel
{
    public $belongsTo = array('Albun');
}
</pre>

Pronto, com isso sempre que buscarmos algo no banco de dados ele já vai incluir automaticamente os dados relacionados, ou seja, se eu listar o álbum, ele vai trazer todas as imagens deste determinado álbum e o contrário também vai acontecer (dizer a qual álbum a imagem pertence).

**Criando os controllers**

Os controllers vão decidir o que será feito na aplicação, ou seja, exibir o que? Pegar que infromação no banco? Que hora o upload deve ser feito? É muito simples, os dois arquivos devem ser salvos em app/Controller:

**Cod. 6:**

<pre class="lang-php">//AlbunsController.php

class AlbunsController extends AppController
{
    
}

//ImagensController.php

class ImagensController extends AppController
{
    
}
</pre>

**Configurando a criação de álbuns de imagens na administração**

No controller álbuns (AlbunsController.php) crie uma função chamada admin_novo, assim:

**Cod. 7:**

<pre class="lang-php">public function  admin_novo()
{
		if ($this-&gt;request-&gt;is('post')) {
			$this-&gt;Albun-&gt;create();
			if ($this-&gt;Albun-&gt;save($this-&gt;request-&gt;data)) {
				$this-&gt;Session-&gt;setFlash(__('Album criado.'));
				return $this-&gt;redirect(array('action' =&gt; 'index'));
			} else {
				$this-&gt;Session-&gt;setFlash(__('Erro ao criar o álbum, tente novamente.'));
			}
		}
}
</pre>

Este action (o nome dado as _functions_ de cada página nos controllers do CakePHP) vai testar se o carregamento da página foi um post, se sim, ele informa que estamos criando um registro, tenta salvar o registro e envia para a index caso tenha sucesso, com uma mensagem de “Album criado”, caso contrário, apenas informa que algo deu errado.

A view desta action, ou o cara que vai exibir os dados na tela do usuário fica assim (arquivo app/View/Albuns/admin_novo.ctp):

**Cod. 7A:**

<pre class="lang-html">&lt;div class="albuns form"&gt;
&lt;?php echo $this-&gt;Form-&gt;create('Albun'); ?&gt;
 &lt;fieldset&gt;
 &lt;legend&gt;Novo album&lt;/legend&gt;
 &lt;?php
 echo $this-&gt;Form-&gt;input('titulo');
 ?&gt;
 &lt;/fieldset&gt;
&lt;?php echo $this-&gt;Form-&gt;end(__('Submit')); ?&gt;
&lt;/div&gt;

</pre>

**Configurando a edição de álbuns de imagens na administração**

Muito parecido com add, mas dessa vez checando se o álbum especificado existe antes de salvar.

**Cod. 8:**

<pre class="lang-php">public function admin_editar($id = null) {
		if (!$this-&gt;Albun-&gt;exists($id)) {
			throw new NotFoundException(__('Albun inválido'));
		}
		if ($this-&gt;request-&gt;is(array('post', 'put'))) {
			if ($this-&gt;Albun-&gt;save($this-&gt;request-&gt;data)) {
				$this-&gt;Session-&gt;setFlash(__('O álbum foi salvo.'));
				return $this-&gt;redirect(array('action' =&gt; 'index'));
			} else {
				$this-&gt;Session-&gt;setFlash(__('Erro ao criar o álbum, tente novamente.'));
			}
		} else {
			$options = array('conditions' =&gt; array('Albun.' . $this-&gt;Albun-&gt;primaryKey =&gt; $id));
			$this-&gt;request-&gt;data = $this-&gt;Albun-&gt;find('first', $options);
		}
}
</pre>

E a view (app/View/Albuns/admin_editar.ctp)

**Cod. 8A:**

<pre class="lang-html">&lt;div class="albuns form"&gt;
&lt;?php echo $this-&gt;Form-&gt;create('Albun'); ?&gt;
 &lt;fieldset&gt;
 &lt;legend&gt;Editando album&lt;/legend&gt;
 &lt;?php
 echo $this-&gt;Form-&gt;input('id');
 echo $this-&gt;Form-&gt;input('titulo');
 ?&gt;
 &lt;/fieldset&gt;
&lt;?php echo $this-&gt;Form-&gt;end(__('Submit')); ?&gt;
&lt;/div&gt;

</pre>

**Configurando a remoção de álbuns de imagens na administração**

Também preciso remover o álbum quando não precisar mais dele. Temos uma action que pode cuidar disso, é bem parecido com a admin_editar, mas desta vez ele usa **delete** em vez de **save**:

**Cod. 9:**

<pre>public function admin_remover($id = null) {
		$this-&gt;Albun-&gt;id = $id;
		if (!$this-&gt;Albun-&gt;exists()) {
			throw new NotFoundException(__('Invalid albun'));
		}
		$this-&gt;request-&gt;onlyAllow('post', 'delete');
		if ($this-&gt;Albun-&gt;delete()) {
			$this-&gt;Session-&gt;setFlash(__('The albun has been deleted.'));
		} else {
			$this-&gt;Session-&gt;setFlash(__('The albun could not be deleted. Please, try again.'));
		}
		return $this-&gt;redirect(array('action' =&gt; 'index'));
}
</pre>

Este **action** redireciona para index, então ele não tem uma view.

**Configurando a listagem de álbuns de imagens na administração**

E pra fechar a administração de álbuns, a listagem de álbuns com paginação:

**Cod. 10:**

<pre>public function admin_index() {
	$this-&gt;Albun-&gt;recursive = -1;
	$this-&gt;set('albuns', $this-&gt;Paginator-&gt;paginate());
}
</pre>

O **recursive -1** impede que o álbum traga os dados relacionados que no nosso caso são as imagens, a segunda linha traz os álbuns salvos no banco com paginação (página 1, página 2&#8230;).

Não esqueça de ativar o componente paginator no seu controller acrescentando a variável $components no inicio da classe AlbunsController (logo abaixo tem um exemplo na classe imagens)

**Cod. 11:**

<pre>public $components = array('Paginator');
</pre>

E a view (app/View/Albuns/admin_index.ctp):

**Cod. 10A:**

<pre class="lang-html">&lt;div class="albuns index"&gt; &lt;h2&gt;Albuns&lt;/h2&gt;
 &lt;table cellpadding="0" cellspacing="0"&gt;
 &lt;tr&gt;
 &lt;th&gt;&lt;?php echo $this-&gt;Paginator-&gt;sort('id'); ?&gt;&lt;/th&gt;
 &lt;th&gt;&lt;?php echo $this-&gt;Paginator-&gt;sort('titulo'); ?&gt;&lt;/th&gt;
 &lt;th&gt;&lt;?php echo $this-&gt;Paginator-&gt;sort('created'); ?&gt;&lt;/th&gt;
 &lt;th&gt;&lt;?php echo $this-&gt;Paginator-&gt;sort('modified'); ?&gt;&lt;/th&gt;
 &lt;th class="actions"&gt;&lt;?php echo __('Actions'); ?&gt;&lt;/th&gt;
 &lt;/tr&gt;
 &lt;?php foreach ($albuns as $albun): ?&gt;
 &lt;tr&gt;
 &lt;td&gt;&lt;?php echo h($albun['Albun']['id']); ?&gt;&nbsp;&lt;/td&gt;
 &lt;td&gt;&lt;?php echo h($albun['Albun']['titulo']); ?&gt;&nbsp;&lt;/td&gt;
 &lt;td&gt;&lt;?php echo h($albun['Albun']['created']); ?&gt;&nbsp;&lt;/td&gt;
 &lt;td&gt;&lt;?php echo h($albun['Albun']['modified']); ?&gt;&nbsp;&lt;/td&gt;
 &lt;td class="actions"&gt;
 &lt;?php echo $this-&gt;Html-&gt;link('Editar', array('action' =&gt; 'editar', $albun['Albun']['id'])); ?&gt;
 &lt;?php echo $this-&gt;Form-&gt;postLink('Remover', array('action' =&gt; 'remover', $albun['Albun']['id']), null, __('Tem certeza que quer remover # %s?', $albun['Albun']['titulo'])); ?&gt;
 &lt;/td&gt;
 &lt;/tr&gt;
&lt;?php endforeach; ?&gt;
 &lt;/table&gt;
 &lt;p&gt;
 &lt;?php
 echo $this-&gt;Paginator-&gt;counter(array(
 'format' =&gt; __('Page {:page} of {:pages}, showing {:current} records out of {:count} total, starting on record {:start}, ending on {:end}')
 ));
 ?&gt; &lt;/p&gt;
 &lt;div class="paging"&gt;
 &lt;?php
 echo $this-&gt;Paginator-&gt;prev('&lt; ' . __('previous'), array(), null, array('class' =&gt; 'prev disabled'));
 echo $this-&gt;Paginator-&gt;numbers(array('separator' =&gt; ''));
 echo $this-&gt;Paginator-&gt;next(__('next') . ' &gt;', array(), null, array('class' =&gt; 'next disabled'));
 ?&gt;
 &lt;/div&gt;
&lt;/div&gt;
&lt;div class="actions"&gt;
 &lt;h3&gt;Actions&lt;/h3&gt;
 &lt;ul&gt;
 &lt;li&gt;&lt;?php echo $this-&gt;Html-&gt;link(__('Novo'), array('action' =&gt; 'novo')); ?&gt;&lt;/li&gt;
 &lt;/ul&gt;
&lt;/div&gt;

</pre>

**Configurando a administração de imagens**

A administração de imagens é bem parecida com a de álbuns, vou apenas passar o código pra gente não se estender muito, mas está bem simples de entender.

Primeiro o controller ImagensController.php

**Cod. 12:**

<pre class="lang-php">public $components = array('Paginator');

	public function admin_index() {
		$this-&gt;Imagen-&gt;recursive = 0;
		$this-&gt;set('imagens', $this-&gt;Paginator-&gt;paginate());
	}

	public function admin_novo() {
		if ($this-&gt;request-&gt;is('post')) {
			$this-&gt;Imagen-&gt;create();
			$this-&gt;request-&gt;data['Imagen']['url'] = $this-&gt;Imagen-&gt;upload($this-&gt;request-&gt;data['Imagen']['url'], $this-&gt;request-&gt;data['Imagen']['albun_id']);
			if ($this-&gt;Imagen-&gt;save($this-&gt;request-&gt;data)) {
				$this-&gt;Session-&gt;setFlash(__('The imagen has been saved.'));
				return $this-&gt;redirect(array('action' =&gt; 'index'));
			} else {
				$this-&gt;Session-&gt;setFlash(__('The imagen could not be saved. Please, try again.'));
			}
		}
		$albuns = $this-&gt;Imagen-&gt;Albun-&gt;find('list', array('fields'=&gt;array('id','titulo')));
		$this-&gt;set(compact('albuns'));
	}

	public function admin_editar($id = null) {
		if (!$this-&gt;Imagen-&gt;exists($id)) {
			throw new NotFoundException(__('Invalid imagen'));
		}
		if ($this-&gt;request-&gt;is(array('post', 'put'))) {
			$this-&gt;request-&gt;data['Imagen']['url'] = $this-&gt;Imagen-&gt;upload($this-&gt;request-&gt;data['Imagen']['url'], $this-&gt;request-&gt;data['Imagen']['albun_id']);
			if ($this-&gt;Imagen-&gt;save($this-&gt;request-&gt;data)) {
				$this-&gt;Session-&gt;setFlash(__('The imagen has been saved.'));
				return $this-&gt;redirect(array('action' =&gt; 'index'));
			} else {
				$this-&gt;Session-&gt;setFlash(__('The imagen could not be saved. Please, try again.'));
			}
		} else {
			$options = array('conditions' =&gt; array('Imagen.' . $this-&gt;Imagen-&gt;primaryKey =&gt; $id));
			$this-&gt;request-&gt;data = $this-&gt;Imagen-&gt;find('first', $options);
		}
		$albums = $this-&gt;Imagen-&gt;Albun-&gt;find('list', array('fields'=&gt;array('id','titulo')));
		$this-&gt;set(compact('albums'));
	}

	public function admin_remover($id = null) {
		$this-&gt;Imagen-&gt;id = $id;
		if (!$this-&gt;Imagen-&gt;exists()) {
			throw new NotFoundException(__('Invalid imagen'));
		}
		$this-&gt;request-&gt;onlyAllow('post', 'delete');
		if ($this-&gt;Imagen-&gt;delete()) {
			$this-&gt;Session-&gt;setFlash(__('The imagen has been deleted.'));
		} else {
			$this-&gt;Session-&gt;setFlash(__('The imagen could not be deleted. Please, try again.'));
		}
		return $this-&gt;redirect(array('action' =&gt; 'index'));
	}
</pre>

E as views:

**Cod. 12A:**

<pre class="lang-html">//app/View/Imagens/admin_index.ctp
&lt;div class="imagens index"&gt;
 &lt;h2&gt;Imagens&lt;/h2&gt;
 &lt;table cellpadding="0" cellspacing="0"&gt;
 &lt;tr&gt;
 &lt;th&gt;&lt;?php echo $this-&gt;Paginator-&gt;sort('id'); ?&gt;&lt;/th&gt;
 &lt;th&gt;&lt;?php echo $this-&gt;Paginator-&gt;sort('imagem'); ?&gt;&lt;/th&gt;
 &lt;th&gt;&lt;?php echo $this-&gt;Paginator-&gt;sort('titulo'); ?&gt;&lt;/th&gt;
 &lt;th&gt;&lt;?php echo $this-&gt;Paginator-&gt;sort('descricao'); ?&gt;&lt;/th&gt;
 &lt;th&gt;&lt;?php echo $this-&gt;Paginator-&gt;sort('albun_id'); ?&gt;&lt;/th&gt;
 &lt;th&gt;&lt;?php echo $this-&gt;Paginator-&gt;sort('created'); ?&gt;&lt;/th&gt;
 &lt;th&gt;&lt;?php echo $this-&gt;Paginator-&gt;sort('modified'); ?&gt;&lt;/th&gt;
 &lt;th class="actions"&gt;&lt;?php echo __('Actions'); ?&gt;&lt;/th&gt;
 &lt;/tr&gt;
 &lt;?php foreach ($imagens as $imagen): ?&gt;
 &lt;tr&gt;
 &lt;td&gt;&lt;?php echo h($imagen['Imagen']['id']); ?&gt;&nbsp;&lt;/td&gt;
 &lt;td&gt;&lt;?php echo h($imagen['Imagen']['url']); ?&gt;&nbsp;&lt;/td&gt;
 &lt;td&gt;&lt;?php echo h($imagen['Imagen']['titulo']); ?&gt;&nbsp;&lt;/td&gt;
 &lt;td&gt;&lt;?php echo h($imagen['Imagen']['descricao']); ?&gt;&nbsp;&lt;/td&gt;
 &lt;td&gt;&lt;?php echo h($imagen['Imagen']['albun_id']); ?&gt;&nbsp;&lt;/td&gt;
 &lt;td&gt;&lt;?php echo h($imagen['Imagen']['created']); ?&gt;&nbsp;&lt;/td&gt;
 &lt;td&gt;&lt;?php echo h($imagen['Imagen']['modified']); ?&gt;&nbsp;&lt;/td&gt;
 &lt;td class="actions"&gt;
 &lt;?php echo $this-&gt;Html-&gt;link('Editar', array('action' =&gt; 'editar', $imagen['Imagen']['id'])); ?&gt;
 &lt;?php echo $this-&gt;Form-&gt;postLink('Delete', array('action' =&gt; 'remover', $imagen['Imagen']['id']), null, __('Tem certeza que quer remover # %s?', $imagen['Imagen']['titulo'])); ?&gt;
 &lt;/td&gt;
 &lt;/tr&gt;
&lt;?php endforeach; ?&gt;
 &lt;/table&gt;
 &lt;p&gt;
 &lt;?php
 echo $this-&gt;Paginator-&gt;counter(array(
 'format' =&gt; __('Page {:page} of {:pages}, showing {:current} records out of {:count} total, starting on record {:start}, ending on {:end}')
 ));
 ?&gt; &lt;/p&gt;
 &lt;div class="paging"&gt;
 &lt;?php
 echo $this-&gt;Paginator-&gt;prev('&lt; ' . __('previous'), array(), null, array('class' =&gt; 'prev disabled'));
 echo $this-&gt;Paginator-&gt;numbers(array('separator' =&gt; ''));
 echo $this-&gt;Paginator-&gt;next(__('next') . ' &gt;', array(), null, array('class' =&gt; 'next disabled'));
 ?&gt;
 &lt;/div&gt;
&lt;/div&gt;
&lt;div class="actions"&gt;
 &lt;h3&gt;Actions&lt;/h3&gt;
 &lt;ul&gt;
 &lt;li&gt;&lt;?php echo $this-&gt;Html-&gt;link(__('Novo'), array('action' =&gt; 'novo')); ?&gt;&lt;/li&gt;
 &lt;/ul&gt;
&lt;/div&gt;

//app/View/Imagens/admin_novo.ctp
&lt;div class="imagens form"&gt;
&lt;?php echo $this-&gt;Form-&gt;create('Imagen',array('type'=&gt;'file')); ?&gt;
 &lt;fieldset&gt;
 &lt;legend&gt;Nova imagem&lt;/legend&gt;
 &lt;?php
 echo $this-&gt;Form-&gt;input('url',array('type'=&gt;'file'));
 echo $this-&gt;Form-&gt;input('titulo');
 echo $this-&gt;Form-&gt;input('descricao');
 echo $this-&gt;Form-&gt;input('albun_id');
 ?&gt;
 &lt;/fieldset&gt;
&lt;?php echo $this-&gt;Form-&gt;end(__('Submit')); ?&gt;
&lt;/div&gt;

//app/View/Imagens/admin_editar.ctp
&lt;div class="imagens form"&gt;
&lt;?php echo $this-&gt;Form-&gt;create('Imagen'); ?&gt;
 &lt;fieldset&gt;
 &lt;legend&gt;Editando imagem&lt;/legend&gt;
 &lt;?php
 echo $this-&gt;Form-&gt;input('id');
 echo $this-&gt;Form-&gt;input('url');
 echo $this-&gt;Form-&gt;input('titulo');
 echo $this-&gt;Form-&gt;input('descricao');
 echo $this-&gt;Form-&gt;input('albun_id');
 ?&gt;
 &lt;/fieldset&gt;
&lt;?php echo $this-&gt;Form-&gt;end(__('Submit')); ?&gt;
&lt;/div&gt;

</pre>

**Configurando o upload e tratamento de imagens**

Note nas actions admin\_novo e admin\_editar do ImagensController que você tem uma linha assim:

<pre class="lang-php">$this-&gt;request-&gt;data['Imagen']['url'] = $this-&gt;Imagen-&gt;upload($this-&gt;request-&gt;data['Imagen']['url'], $this-&gt;request-&gt;data['Imagen']['albun_id']);
</pre>

Ela carrega uma função do model Imagen.php chamada upload que cuida de salvar os dados do arquivo enviado ($this->request->data\[&#8216;Imagen&#8217;\]\[&#8216;url&#8217;\]) e também criar uma pasta com o id do álbum atual ($this->request->data\[&#8216;Imagen&#8217;\]\[&#8216;albun_id&#8217;\]) no diretório app/webroot/img, mas o que ela faz ao certo?

  * Primeiro vamos verificar se o arquivo enviado tem o tipo certo (jpeg, gif, png&#8230;)
  * Em seguida verificamos se deu tudo certo durante o upload
  * Caso tenha, checo se o diretório aonde as imagens vão fica existe (será em app/webroot/img/album/{id do álbum}), se não existir eu crio
  * Então parto pra etapa de conversão de nome, transformando em um formato aceito na web, mas sem perder o nome de arquivo que o usuário tinha antes
  * E uso o WideImage pra ajustar a imagem para um tamanho aproximado de 800x600px e criar uma miniatura de 250x250px exatos (cortando o excesso a partir de centro da imagem)

O código completo vai no app/Model/Imagen.php, logo a baixo da linha da variável $belongsTo:

**Cod. 13:**

<pre class="lang-php">public function upload($arquivo, $id) {
        $ext = array(
            'image/jpeg',
            'image/pjpeg',
            'image/x-jps',
            'image/png',
            'image/gif',
        );
        
        if ($arquivo['error']!=0 || $arquivo['size']==0 || !in_array($arquivo['type'], $ext)){
            return false;
        }
        
        
        if(!is_dir(WWW_ROOT.'img'.DS.'album'.DS.$id)){  
            App::uses('Folder', 'Utility'); 
            
            $folder = new Folder();
            if($folder-&gt;create(WWW_ROOT.'img'.DS.'album'.DS.$id)){  
                //se conseguiu criar o diretório eu dou permissão  
                $folder-&gt;chmod(WWW_ROOT.'img'.DS.'album'.DS.$id, 0755, true);  
            } else {  
                return false;  
            }
            $folder = new Folder();
            if($folder-&gt;create(WWW_ROOT.'img'.DS.'album'.DS.$id.DS.'thumb')){  
                //se conseguiu criar o diretório eu dou permissão  
                $folder-&gt;chmod(WWW_ROOT.'img'.DS.'album'.DS.$id.DS.'thumb', 0755, true);  
            } else {  
                return false;  
            }
        }
        
        $pathinfo=pathinfo($arquivo['name']);
        $pathinfo['filename']=strtolower(Inflector::slug($pathinfo['filename'],'-'));
        $arquivo['name']=$pathinfo['filename'].'.'.$pathinfo['extension'];
        
        App::import('Vendor', 'wideimage/WideImage');  
        $img = WideImage::load($arquivo['tmp_name']);  
        $img = $img-&gt;resize(800,600,'outside');  
        $min = $img-&gt;resize(250,250,'outside');  
        $min = $min-&gt;crop('50%-125','50%-125',250,250);
        $img-&gt;saveToFile(WWW_ROOT.'img'.DS.'album'.DS.$id.DS.$arquivo['name']);
        $min-&gt;saveToFile(WWW_ROOT.'img'.DS.'album'.DS.$id.DS.'thumb'.DS.$arquivo['name']);
        
        return $arquivo['name'];
    }
</pre>

**Listando os álbuns**

Bem, nossa aplicação já está salvando a imagem, já cria álbuns e associa um ao outro, mas ainda não mostra o resultado final, vamos configurar isso.

Primeiro precisamos de uma listagem de álbuns com uma miniatura e um titulo para o usuário escolher o que quer ver.

Vou configurar para que a miniatura seja a primeira imagem do álbum, vamos ao controller (app/Controller/AlbunsController.php):

**Cod. 14:**

<pre>public function index() {
		$albuns = $this-&gt;Albun-&gt;find(
			'all',
			array(
				'contain'=&gt;array(
					'Imagen'=&gt;array(
						'limit'=&gt;1
					)
				)
			)
		);
		$this-&gt;set('albuns', $albuns);
	}
</pre>

Você viu que eu usei o contain ali dentro do array, isso é um behavior e ele precisa ser chamado no Model pra funcionar, para isso vá ao model Albun.php e acrescente a variável antes ou depois da var $hasMany:

**Cod. 14A:**

<pre>public $actsAs = array('Containable');</pre>

A view é a _app/Albuns/index.ctp_.

**Cod. 14B:**

<pre class="lang-html">&lt;?php

foreach ($albuns as $v) :
 if(!empty($v['Imagen'][0]['url'])) {
 echo '&lt;div style="float:left"&gt;';
 $img = $this-&gt;Html-&gt;image('album/'.$v['Albun']['id'].'/40/'.$v['Imagen'][0]['url']);
 echo $this-&gt;Html-&gt;link($img,'/albuns/ver/'.$v['Albun']['id'],array('escape'=&gt;false)).'&lt;br&gt;';
 echo $v['Albun']['titulo'];
 echo '&lt;/div&gt;';
 }
endforeach;
</pre>

**Listando as imagens de cada álbum**

E pra fechar nossa galeria faltou apenas criarmos a exibição da galeria em si, para isso devemos trazer o nosso álbum e o CakePHP já vai trazer os dados relacionados a ele (que no nosso caso são as imagens):

**Cod. 15:**

<pre>public function ver($id = null) {
		if (!$this-&gt;Albun-&gt;exists($id)) {
			throw new NotFoundException(__('Invalid albun'));
		}
		
		$options = array('conditions' =&gt; array('Albun.' . $this-&gt;Albun-&gt;primaryKey =&gt; $id));
		$album = $this-&gt;Albun-&gt;find('first', $options);
		$this-&gt;set('album', $album);
	}
</pre>

A view ver.ctp(não vou falar o caminho desta vez, deve ter ficado claro pra você) de álbuns vai exibir o html já formatado para eu usar o Fancybox, ou seja, imagem dentro de um link.

**Cod. 15A:**

<pre class="lang-html">&lt;h3&gt;&lt;?php echo $album['Albun']['titulo'];?&gt;&lt;/h3&gt;
&lt;?php foreach ($album['Imagen'] as $v) :
 $img = $this-&gt;Html-&gt;image('album/'.$album['Albun']['id'].'/40/'.$v['url']);
 echo $this-&gt;Html-&gt;link(
 $img,
 '/img/album/'.$album['Albun']['id'].'/'.$v['url'],
 array(
 'escape'=&gt;false,
 'class'=&gt;'fancy',
 'alt'=&gt;$v['descricao'],
 'title'=&gt;$v['titulo'],
 'rel'=&gt;$album['Albun']['titulo']
 )
 );
endforeach;?&gt;
</pre>

**Integrando ao FancyBox**

O Fancybox é um plugin para frontend, então o processo é o mesmo que em qualquer outro lugar, basta criar o HTML da galeria no formato que ele usa (fizemos isso no passo anterior) e chamar os javascripts, css e configurar o plugin.

Ainda na view ver.ctp de Albuns, faça isso logo no final:

**Cod. 16:**

<pre>Html-&gt;script(
		array(
			'//ajax.googleapis.com/ajax/libs/jquery/1.11.0/jquery.min.js',
			'/fancy/jquery.fancybox.pack'
		),
		array('inline'=&gt;false)
	);
	echo $this-&gt;Html-&gt;css(
		array('/fancy/jquery.fancybox'),
		null,
		array('inline'=&gt;false)
	);
	echo $this-&gt;Html-&gt;scriptBlock(
		'$(".fancy").fancybox();',
		array('inline'=&gt;false)
	);
?&gt;
</pre>

O primeiro bloco (Html->script) chama os javascripts (o jquery do server do Google e o jquery.fancybox.pack.js que está no diretório webroot).

O segundo bloco (Html->css) faz o mesmo com o css local.

E o terceiro cria um bloco &#8230; configurando o Fancybox, note que eu coloquei tudo com inline=>false assim ele não imprime isso na view e sim nas tags script e css que estão no nosso arquivo app/View/Layout/default.ctp (já vem no CakePHP) pra evitar a bagunça (como se o javacript direto na página fosse muito organizado, mas deu pra entender bem como proceder).

### Como usar?

Fácil, você tem três urls base:
  
/albuns – listagem de álbuns
  
/admin/abuns – administração de álbuns
  
/admin/imagens – administração de imagens

Além disso você ainda pode usar estas urls, mas a navegação da galeria já vai te guia por elas:

/admin/novo
  
/admin/albuns/editar/{id do album}
  
/admin/albuns/remover/{id do álbum}
  
/admin/novo
  
/admin/imagens/editar/{id da imagem}
  
/admin/imagens/remover/{id da imagem}
  
/albuns/ver/{id do album}

Perceba que cada action gerou uma url e que o admin_ gerou um /admin em cada action, além dos ids e os controllers, no fim você entende que as urls seguem o padrão

/:prefixo/:controller/:action – lembrando que o prefixo é o admin
  
Ou
  
/:controller/:action
  
Ou
  
/:controller – e action passada é a index por padrão quando uma não for especificada.

Isso ainda pode ser personalizado, mas é outro assunto.

### Conclusão {.western}

Note que esta é uma tarefa normalmente dispendiosa, é uma administração completa de galeria de imagens que embora simples é bem completa e eu consegui resumir tudo em poucas linhas de código e um artigo apenas.

Você ainda precisa proteger a administração da sua aplicação com senha, adicionar um controle de imagens melhor, checar se o arquivo existe e alterar o nome para não substituir, apagar a imagem quando o dado for apagado do banco (tanto o álbum quanto as imagens), remover a imagem antiga quando troca no admin_editar, setar imagem de capa do álbum&#8230; enfim, mas agora você tem um norte pra começar a trabalhar.

Aqui o arquivo pronto para download (o sql do banco está em app/Config/Schema/database.sql): <http://blog.erikfigueiredo.com.br/galeria.zip>

Obrigado a todos.

 [1]: http://blog.erikfigueiredo.com.br/exemplo-de-framework-com-psr-0-psr-1-e-psr-2-entendendo-o-padrao-mvc-na-pratica-parte-01/