---
title: Lojas virtuais com WooCommerce
author: Dani Guerrato
type: post
date: 2013-10-08
excerpt: Conheça a ferramenta que permite o desenvolvimento de lojas virtuais através do Wordpress, veja um passo-a-passo de instalação, confira as principais funcionalidades e leve de bônus uma lista de plugins úteis.
url: /lojas-virtuais-com-woocommerce/
dsq_thread_id: 1824939556
categories:
  - Wordpress
tags:
  - eCommerce
  - loja virtual
  - WooCommerce

---
## O que é WooCommerce?

O [WooCommerce][1] é um plugin gratuito que permite a criação de lojas virtuais diretamente através do WordPress. Ele funciona como um kit de ferramentas modular contendo os elementos mais comuns em eCommerce como carrinho de compras, gerenciamento de estoques, estatísticas, gateways de pagamento, etc. O WooCommerce foi criado pela empresa [WooThemes][2] de forma opensource e traduzido para diversas línguas, inclusive português brasileiro. Por padrão o WooCommerce é integrado ao PayPal, mas é possível integrar outros métodos de pagamento através de extensões gratuitas e pagas.

Em resumo, é uma ótima ferramenta para quem já está acostumado com o WordPress e pretende criar uma loja virtual simples.

### Como funciona

O plugin adiciona algumas features ao WordPress como tipos diferentes de páginas (carrinho de compras, checkouts, estoque&#8230;), post customizados para pedidos e produtos, widgets, shortcodes e novos papeis de usuário para administradores e clientes. Isto permite a criação de lojas tanto de produtos físicos quanto para itens online adquiridos via download (como músicas e livros digitais).

### Vantagens de desenvolvimento

A [documentação extensiva][3], a grande participação da comunidade na criação de extensões, o vinculo com o WordPress e a possibilidade de criar temas personalizados fazem do WooCommerce uma ferramenta atrativa para desenvolvedores que pretendem se aventurar no mundo do eCommerce. Como a integração funciona através de variáveis pré-criadas não é necessário possuir um conhecimento aprofundado em programação back-end para obter um resultado interessante. Outro ponto bacana é a integração com o Schema que pode dar um empurrãozinho na questão de SEO.

Para a pessoa que vai de fato administrar a loja o ambiente familiar do CMS pode pesar a favor da ferramenta, outras funcionalidades como integração com o Google Analytics e estatísticas de compras em formato de gráficos também são interessantes. Já o usuário final pode curtir o processo simplificado de compra e a integração com redes sociais (é possível compartilhar descontos, por exemplo). É claro que diversas outras ferramentas possuem os mesmos atributos e, obviamente, se você tiver conhecimento de programação poderá construir um sistema muito mais robusto e complexo. Em geral este é o caminho mais recomendável, afinal, você pode criar algo exclusivo levando em conta as necessidades específicas do seu projeto. Mas nem sempre o tempo e orçamento contam a nosso favor e a praticidade de uso certamente é a característica mais interessante do WooCommerce.

### Requisitos mínimos

  * WordPress 3.5 ou superior;
  * PHP 5.2.4 ou superior;
  * MySQL 5.0 ou superior;
  * Modulo de apache mod_rewrite (para permalinks);
  * Suporte a fsockopen (para gateway de pagamento IPN);
  * (opcional) Certificado SSL para gateways de pagamento diretos.
  * (opcional) Alguns plugins para WooCommerce requerem CURL.
  * (opcional) Alguns plugins para WooCommerce require SOAP.

## Instalação

Instalar o WooCommerce não é muito diferente de instalar qualquer plugin de WordPress. Entre no seu painel de administração, escolha a opção **Plugins** na sidebar e clique em **Adicionar Novo**. Digite &#8220;WooCommerce&#8221; no campo e busca. Deve ser o primeiro resultado que aparecer, mas por garantia se certifique que o desenvolvedor é WooThemes. Agora é só clicar em **Instalar**. Fácil e indolor.

Se a mensagem roxa gigante aparecer você está pronto para começar. Clique em **instalar as páginas do WooCommerce**.

<img src="http://tableless.com.br/uploads/2013/10/woocommerce-bemvindo.jpg" alt="woocommerce-bemvindo" width="660" height="440" class="alignnone size-full wp-image-39126" srcset="uploads/2013/10/woocommerce-bemvindo.jpg 660w, uploads/2013/10/woocommerce-bemvindo-252x168.jpg 252w, uploads/2013/10/woocommerce-bemvindo-465x310.jpg 465w" sizes="(max-width: 660px) 100vw, 660px" />

Se você preferir também pode instalar manualmente.
  
1. Baixe o plugin no seu computador através do site oficial e descompacte o zip.
  
2. No seu programa de FTP favorito faça o upload dos arquivos descompactados no diretório do WordPress wp-content/plugins/
  
3. Ative o plugin através do painel de administração do WordPress.

## Configurações Básicas

Antes de começar a vender é preciso, obviamente, fornecer algumas informações para o plugin. Clique em **WooCommerce** e **Configurações**. 

<img src="http://tableless.com.br/uploads/2013/10/plugins.jpg" alt="plugins" width="660" height="440" class="alignnone size-full wp-image-39123" srcset="uploads/2013/10/plugins.jpg 660w, uploads/2013/10/plugins-252x168.jpg 252w, uploads/2013/10/plugins-465x310.jpg 465w" sizes="(max-width: 660px) 100vw, 660px" />

A partir deste painel você pode setar as informações fundamentais para o funcionamento de uma loja como moeda, localização, estoque, impostos, frete, pagamento, e-mail, etc.  Os campos são auto explicativos, mas se você precisar de uma ajuda dê uma olhada na [documentação sobre configurações.][4]

Agora você pode [criar o seu próprio tema][5] ou escolher um [template pronto][6].

[<img src="http://tableless.com.br/uploads/2013/10/woocommerce-temas.jpg" alt="woocommerce-temas" width="660" height="440" class="alignnone size-full wp-image-39128" srcset="uploads/2013/10/woocommerce-temas.jpg 660w, uploads/2013/10/woocommerce-temas-252x168.jpg 252w, uploads/2013/10/woocommerce-temas-465x310.jpg 465w" sizes="(max-width: 660px) 100vw, 660px" />][7]

Para fins de aprendizado neste artigo vamos trabalhar com o tema padrão do WordPress. 

### Conteúdo falso

Sua loja está vazia. Você pode começar a preencher o seu estoque de produtos ou adicionar um conteúdo falso para teste. O plugin vem com alguns dados falsos para você visualizar o layout das paginas da sua loja. Para isto importe o arquivo dummy_data.xml através do plugin [WordPress Importer][8] ou use a [suite de importação da WooThemes][9] (por $199) e importe dummy\_data.csv e dummy\_data_variations.csv.

Como dinheiro não nasce em árvore vamos considerar que você está utilizando o Importer. Basta clicar em **plugins** e localizar o **WordPress Importer**. Instale o plugin, ative e blá bla blá… Depois clique em **Ferramentas**, **Importar**. Na próxima tela selecione a opção **WordPress**. Procure pelo arquivo to the dummy_data.xml na pasta wp-content/plugins/woocommerce. Clique em **fazer upload**. Crie ou selecione um usuário responsável pela importação, marque a opção **Download and import file attachments** aperte o botão submit e pronto!

Agora você é o orgulhoso dono de uma loja de mentirinha cheia de produtos falsos. O que é super útil como modelo para testarmos todas as funções do plugin antes de usarmos o conteúdo real, certo?

<img src="http://tableless.com.br/uploads/2013/10/woocommerce-produtos.jpg" alt="woocommerce-produtos" width="660" height="440" class="alignnone size-full wp-image-39127" srcset="uploads/2013/10/woocommerce-produtos.jpg 660w, uploads/2013/10/woocommerce-produtos-252x168.jpg 252w, uploads/2013/10/woocommerce-produtos-465x310.jpg 465w" sizes="(max-width: 660px) 100vw, 660px" />

O layout da página de produto no tema padrão ficará mais ou menos assim:

<img src="http://tableless.com.br/uploads/2013/10/exemplo-produto.jpg" alt="exemplo-produto" width="660" height="440" class="alignnone size-full wp-image-39121" srcset="uploads/2013/10/exemplo-produto.jpg 660w, uploads/2013/10/exemplo-produto-252x168.jpg 252w, uploads/2013/10/exemplo-produto-465x310.jpg 465w" sizes="(max-width: 660px) 100vw, 660px" />

## A estrutura

A interface do WooCommerce aproveita muitos elementos originais do WordPress. Adicionar e [editar produtos][10], por exemplo, é uma tarefa muito parecida com criar um posts. Basta clicar no item **Produtos** na sidebar e escolher a opção **Novo Produto**. A partir daí é só uma sequência de formulários que qualquer usuário familiarizado com o WordPress é mais do que capaz de compreender.

<img src="http://tableless.com.br/uploads/2013/10/novo-produto.jpg" alt="novo-produto" width="660" height="440" class="alignnone size-full wp-image-39122" srcset="uploads/2013/10/novo-produto.jpg 660w, uploads/2013/10/novo-produto-252x168.jpg 252w, uploads/2013/10/novo-produto-465x310.jpg 465w" sizes="(max-width: 660px) 100vw, 660px" />

Não vou perder tempo descrevendo como realizar as tarefas básicas pois não existe segredo algum.  Como o foco deste artigo é desenvolvimento vamos conversar um pouco sobre a estrutura do plugin para que você possa projetar suas próprias páginas.

### Páginas e Widgets

  * **Shopping Cart** – Carrinho de compras.
  * **Price Filter** – Permite o usuário refinar produtos baseados em preços ou categorias.
  * **Layered Nav** – Permite ao usuário refinar os produtos baseado em atributos.
  * **WooCommerce Layered Nav Filters** &#8211; Mostra quais filtros estão ativos para que o usuário possa ativar/desativar.
  * **Recent Products** – Lista de produtos recentes.
  * **Top Rated Products** – Lista de produtos com melhor classificação.
  * **Featured Products** – Mostra produtos em destaque.
  * **Recently Viewed Products** – Mostra uma lista de produstos visualizados recentemente pelo usuario.
  * **Product Search** – Busca por produtos.
  * **Product Categories** – Lista de categoras de produto.
  * **Product Tag Cloud** – Nuvem de tags de produtos.
  * **Recent Reviews** – Lista de produtos recém avaliados.

### Shortcodes

Este é o coração do plugin. Os shortcodes funcionam como atalhos para cada módulo. Basta inserir o shortcode correspondente na página ou post que você desejar para mostrar o conteúdo dele em seu layout. Você pode inserir os shortcodes copiando e colando o código ou clicando no ícone do Woo.

<img src="http://tableless.com.br/uploads/2013/10/shortcode.jpg" alt="shortcode" width="660" height="440" class="alignnone size-full wp-image-39124" srcset="uploads/2013/10/shortcode.jpg 660w, uploads/2013/10/shortcode-252x168.jpg 252w, uploads/2013/10/shortcode-465x310.jpg 465w" sizes="(max-width: 660px) 100vw, 660px" />

#### Shortcodes Padrão

Estes atalhos são instalados automaticamente. Mas é bom conhece-los caso você queira criar seu próprio tema ou modificar um pré-existente.

**[woocommerce_cart]** – página de carrinho.
  
**[woocommerce_checkout]** – página de checkout (finalizar compra).
  
**[woocommerce_pay]** – página de finalizar pagamento.
  
**[woocommerce_thankyou]** – página de pedido recebido.
  
**[woocommerce\_order\_tracking]** – rastreamento do produto.
  
**[woocommerce\_my\_account]** – conta do usuário.
  
**[woocommerce\_edit\_address]** – página de edição de endereço do usuário.
  
**[woocommerce\_view\_order]** – visualização de pedido.
  
**[woocommerce\_change\_password]** – página de modificação de senha
  
**[woocommerce\_lost\_password]** – página de senha perdida.
  
**[woocommerce_logout]** – página de log-out.

### Shortcodes Opcionais

**[recent\_products per\_page=&#8221;12&#8243; columns=&#8221;4&#8243;]** &#8211; Lista produtos recentes. É possível editar a quantidade e número de colunas.
  
**[featured\_products per\_page=&#8221;12&#8243; columns=&#8221;4&#8243;]** &#8211; Produtos em destaque.
  
**[product id=&#8221;99&#8243;]** ou [**product sku=&#8221;FOO&#8221;]** &#8211; Mostra um produto específico. É necessário determinar um valor de ID ou SKU.
  
**[products ids=&#8221;1, 2, 3, 4, 5&#8243;]** ou **[products skus=&#8221;foo, bar, baz&#8221; orderby=&#8221;date&#8221; order=&#8221;desc&#8221;]** &#8211; Mostra diversos produtos. Novamente determine uma ID ou Sku separando os valores por virgula.
  
**[add\_to\_cart id=&#8221;99&#8243;]** &#8211; Preço e botão de adicionar ao carrinho de um produto especifico.
  
**[add\_to\_cart_url id=&#8221;99&#8243;]** &#8211; Mostra a URL de adicionar ao carrinho.
  
**[product_page id=&#8221;99&#8243;]** ou **[product_page sku=&#8221;FOO&#8221;]** &#8211; Mostra a página do produto completa.
  
**[product_category category=&#8221;tecnologia&#8221;]** &#8211; Mostra diversos produtos de uma determinada categoria. Preencha o parametro category com o slug correspondente.
  
**[product_categories number=&#8221;12&#8243; parent=&#8221;0&#8243;]** &#8211; Loop de categoria de produtos.
  
**[sale\_products per\_page=&#8221;12&#8243;]** &#8211; Produtos em promoção
  
**[best\_selling\_products per_page=&#8221;12&#8243;]** &#8211; Produtos mais vendidos.
  
**[top\_rated\_products per_page=&#8221;12&#8243;]** &#8211; Produtos melhor classificados.
  
**[product_attribute attribute=&#8217;color&#8217; filter=&#8217;blue&#8217;]** &#8211; Lista produtos com um determinado atributo. Ex: apenas produtos da cor azul.
  
**[related\_products per\_page=&#8221;12&#8243;]** &#8211; Lista de produtos relacionados.

Estes são os shortcodes básicos do WooCommerce. Para mais informações sobre cada item, incluindo especificações mais detalhadas de uma olhada no item shortcodes na [documentação do plugin][11].

### Banco de Dados

O WooCommerce instala algumas tabelas específicas no banco de dados. São elas:

**woocommerce\_attribute\_taxonomies** &#8211; Armazena atrubutos definidos pelo usuario utilizados para criar taxonomias.
  
**woocommerce\_downloadable\_product_permissions** &#8211; Armazena quais usuários tem permissão para fazer download de produtos.
  
**woocommerce_termmeta** &#8211; Armazena metadados para definir ordem de categorias customizadas.

## Plugins Úteis

É possível aumentar as funcionalidades padrões do WooCommerce através de plugins e extensões. Para mais extensões úteis de uma olhada na [biblioteca oficial][12]. Segue uma listinha útil para lojas brasileiras.

### Correios

[WooCommerce Correios][13]
  
Através deste plugin você pode fornecer os seguintes métodos de entrega: PAC, SEDEX, SEDEX 10, SEDEX Hoje e e-SEDEX.
  
**Preço**: Gratuito

### Campos extras para Checkout

[WooCommerce Extra Checkout Fields for Brazil][14]
  
Adiciona novos campos no formulário específicos para lojas brasileiras como pessoa física, pessoa jurídica, bairro, etc.
  
**Preço**: Gratuito

### Integração com PagSeguro

[WooCommerce PagSeguro][15]
  
Adicione o método de pagamento PagSeguro.
  
**Preço**: Gratuito

### Multilinguagem

[WooCommerce Multilingual][16]
  
Crie loja com suporte para diversas línguas.
  
**Preço**: Gratuito

### Conversor de moedas

[Currency Converter Widget][17]
  
Crie loja com suporte para diversas moedas.
  
**Preço**: $29

### Lojas no Facebook

[Facebook Tab][18]
  
Venda os produtos através de uma Facebook Tab.
  
**Preço**: $49

### Mailchimp

[Newsletter Subscription][19]
  
Integração com newsletter do MailChimp.
  
**Preço**: $40

## Saiba mais

[Site oficial][20]
  
[Documentação][21]
  
[Github][22]
  
[Extensões][23]
  
[Forum][24]

 [1]: http://www.woothemes.com/woocommerce/ "WooCommerce"
 [2]: http://www.woothemes.com/ "WooThemes"
 [3]: http://docs.woothemes.com/documentation/plugins/woocommerce/ "WooCommerce Documentation"
 [4]: http://docs.woothemes.com/document/configuring-woocommerce-settings/ "Configuring woocommerce settings"
 [5]: http://docs.woothemes.com/documentation/plugins/woocommerce/woocommerce-codex/theming/ "Woocommerce codex theming"
 [6]: http://www.woothemes.com/product-category/themes/woocommerce "WooCommerce Themes"
 [7]: http://www.woothemes.com/product-category/themes/woocommerce
 [8]: http://wordpress.org/extend/plugins/wordpress-importer/ "Wordpress Importer"
 [9]: http://www.woothemes.com/products/product-csv-import-suite/ "Product csv import suite"
 [10]: http://docs.woothemes.com/document/managing-products/ "Managing Products"
 [11]: http://docs.woothemes.com/document/woocommerce-shortcodes/ "WooCommerce Shortcodes"
 [12]: http://www.woothemes.com/product-category/woocommerce-extensions/ "Woocommerce extensions"
 [13]: http://wordpress.org/plugins/woocommerce-correios/ "Woocommerce Correios"
 [14]: http://wordpress.org/plugins/woocommerce-extra-checkout-fields-for-brazil/ "Woocommerce extra checkout fields for brazil"
 [15]: http://wordpress.org/plugins/woocommerce-pagseguro/ "Woocommerce Pagseguro"
 [16]: http://wordpress.org/plugins/woocommerce-multilingual/ "Woocommerce multilingual"
 [17]: http://www.woothemes.com/products/currency-converter-widget/ "Currency converter widget"
 [18]: http://www.woothemes.com/products/facebook-tab/ "Facebook Tab"
 [19]: http://www.woothemes.com/products/newsletter-subscription/ "Newsletter Subscription"
 [20]: http://www.woothemes.com/woocommerce "WooCommerce"
 [21]: http://docs.woothemes.com/documentation/plugins/woocommerce/ "Documentação"
 [22]: https://github.com/woothemes/woocommerce "Github"
 [23]: http://www.woothemes.com/product-category/woocommerce-extensions/ "Extensions"
 [24]: http://wordpress.org/support/plugin/woocommerce "Forum "