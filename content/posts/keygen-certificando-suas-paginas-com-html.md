---
title: 'Keygen: Certificando suas paginas com HTML'
author: Alysson Franklin
type: post
date: 2011-04-13
excerpt: Uma tag que ressucitou do passado com mais força e vigor.
url: /keygen-certificando-suas-paginas-com-html/
tweetbackscheck:
  - 1356414442
shorturls:
  - 'a:3:{s:9:"permalink";s:65:"http://tableless.com.br/keygen-certificando-suas-paginas-com-html";s:7:"tinyurl";s:26:"http://tinyurl.com/42kr49b";s:4:"isgd";s:19:"http://is.gd/gjHkl2";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 503027406
categories:
  - Código
  - HTML
  - Tecnologia e Tendências
tags:
  - certificado
  - keygen
  - segurança
  - ssl

---
Com a convergência tudo está indo para a web. Tudo. Por enquanto a grande maioria das apps e paginas estão abertas, mas a medida que o tempo passa, a web também evolui. Em um ambiente completamente social, aonde a relevância do conteúdo não está mais nas mãos de quem anuncia, mas sim na dos leitores, conteúdo cada vez mais segmentado vai surgir. E inevitavelmente, cada vez mais precisaremos de **certificados**. 

## O que são e como funcionam os certificados?

Em criptografia, um certificado de chave pública (também conhecido como um certificado digital ou certificado de identidade – aka SSL) é um documento eletrônico que usa uma assinatura digital para vincular uma chave pública com informações sobre a identidade do remetente – que pode ter informações como o nome de uma pessoa ou um organização, seu endereço e assim por diante. O certificado pode ser usado para verificar se uma chave pública pertence a um indivíduo. Vamos cada vez mais agregando valor ao conteúdo na web através de rating, comentários, presença online, etc. Mas ainda sim a web oferece brechas no sistema, permitindo que pessoas possam emitir valores e opiniões sem a devida validação. Essas brechas vao diminuindo a medida que os certificados vão sendo usados, e em uma web puramente social, é difícil se imaginar sem um destes certificados, e acho que no futuro próximo, isso será realidade mandatória para todos. 

O uso mais comum dos certificados é de web sites baseados em HTTPS. Browsers validam certificados SSL de servidores web, para que o usuário pode se sentir seguro de que sua interação com o site não tem espiões e que o site é quem afirma ser. Na prática, um usuário obtém uma chave criptografada gerada pelo website, que validada com um fornecedor certificado (uma loja de certificado$) confirma a procedência do certificado. Durante a navegação, este certificado público é enviado a qualquer browser que se conecte ao site, mostrando para o usuário que o endereço é validado – e seguro.

<div id="attachment_3480" style="width: 662px" class="wp-caption alignleft">
  <a href="http://tableless.com.br/uploads/2011/04/certifi.png"><img src="http://tableless.com.br/uploads/2011/04/certifi.png" alt="Esta imagem é uma representacao grafica do ultimo paragrafo, mostrando a interacao que o usuario tem com servidor atraves de SSL" width="652" height="207" class="size-full wp-image-3480" srcset="uploads/2011/04/certifi.png 652w, uploads/2011/04/certifi-300x95.png 300w" sizes="(max-width: 652px) 100vw, 652px" /></a>
  
  <p class="wp-caption-text">
    Intercação de usuário com website seguro atraves de certificados SSL
  </p>
</div>

Quem faz esta validação é chamado de **entidade certificadora**, e poderíamos mencionar a **Certisign**, **Verisign** e **Serasa** além de **Federações e Sindicatos**, como a **FENACON** e a **PRODEMGE**. No Brasil por exemplo, manter uma chave publica pessoal para atestar sua identidade ([e-CPF][1]) custa em média R$130,00.

## Single sign-on X Certificados

É notório que o custo dos certificados são suas maiores barreiras. É visível o custo de manutenção de estruturas para manter servidores **apenas** para validar certificados – e não são poucos. Mas mesmo assim, algo tão importante deveria ser mantido em regime de economia de escala &#8211; e ser oferecido de maneira mais acessível a população. 

Enquanto isso, vamos oferecendo soluções para os clientes que envolvem na maioria das vezes, [single-sign-on (SSO)][2]. O conceito vem sendo pregado pelo [Open Group][2] a muito tempo, e dele surgiu o [OpenID][3].

O funcionamento de um **OpenID** é simples, ele simplesmente valida a existência de um usuário baseado em serviços ja consolidados de login, que oferecem uma API bem documentada e incentivam o seu uso. [Google, Facebook e outras empresas oferecem estes servicos][4]. “Cascatear” a validação, oferecendo a segurança de uma entidade como as mencionadas é algo que fortalece muito a segurança da sua aplicação e a confiança do usuário. Se você não existe em uma rede social (eis que chegamos na [reificação][5] do usuário através de sua existencia digital), não tem como logar, validar, navegar&#8230; enfim, nada.

Mas ainda sim este método apresenta falhas. Alguém que tenha posse de seu user e senha pode facilmente se passar por você. Isso o single sign-on não pode evitar, mas certificados resolvem este problema. Mas também não são perfeitos. É importante conhecer os dois métodos pois dependendo do nível de segurança que você precisa oferecer a aplicação, qualquer uma das opções serão válidas. Quer apenas ter certeza que o usuário existe antes de postar um comentário em seu site? Ok, dá pra usar um single sign-on sem problemas. Precisa mostrar que seu site é **realmente seguro** para garantir transações financeiras e honrar o cadeadinho na tray do navegador? Certificados são o que você deverá usar.

## Como requerer um certificado pelo método usual?

Um certificado custa dinheiro. E não é barato. Talvez por isso eles ainda nao sejam amplamente utilizados. Bancos por exemplo costumam pagar para seus clientes seus certificados como ferramentas de fidelização. Certificados são temporais e muitas pessoas quando necessitam, compram por um ano ou tres o serviço. Existem leis em tramite no congresso em relação ao RIC, o registro de identidade civil, com vinculações ao e-cpf, o que virtualmente obriga todos a possuírem certificados digitais atrelados ao CPF no longo prazo.

## Como montar um certificado apenas com&#8230; HTML?

Mas até ai nada novo. Na real, nada do que esta neste post é novo, apenas **obscuro**. Desde a época do saudoso Netspace Navigator existe uma tag pouco utilizada, e da mesma maneira pouco conhecida &#8211; <keygen> </em>.

      <a href="http://tableless.com.br/uploads/2011/04/IC341506.gif"><img src="http://tableless.com.br/uploads/2011/04/IC341506.gif" alt="" width="561" height="200" class="alignleft size-full wp-image-3481" /></a>
    

Quando a internet ainda engatinhava, a Netscape criou um meio dela mesma poder emitir – e validar – certificados, usando HTTP e HTML. Essa tag é suportada pela maioria dos browsers (exceção a Apple – Safari e iOS), porém nunca foi oficialmente colocada no pacote das especificações HTML. Vinha sendo usada de maneira tímida, mas voltou aos spots com o HTML5. Ou seja, embora muitas documentações mencionem ela como elemento HTML5 (inclusive a do Mozilla Developer Network), é quase mais velha que a especificação HTML4.

## Como funciona?

A sintaxe é simples e suporta atributos globais como o autofocus.

<pre lang="html" line="1">&lt;keygen name="soureal" challenge="String de verificacao" keytype="tipo de chave" keyparams="pqg-params">
</pre>

**Challenge**
  
Uma seqüência de desafio que é apresentado juntamente com a chave pública. O padrão é uma string vazia se não for especificada. 

**Disabled**
  
Atributo booleano que indica que o controle de formulário não está disponível para interação. 

**Form**
  
Todo `keygen` para funcionar depende de um form que processa a informação. Com isso, podemos dizer que por enquanto, adeus Ajax para fazer uso de keygen sem submeter formulários. Foi da tentativa de conseguir isso que resolvi criar este post. O elemento de form precisa existir associado ao <keygen&gt.

keyType
:   O tipo de chave gerada. O valor padrão é o RSA.

Nome
:   O nome do campo

**Name** e **Challenge** são attributos obrigatórios. **Keytype** especifica o tipo de chave (RSA-DSA e EC). Caso use chaves DSA ou EC você precisa especificar **keyparams**. Para declará-los da seguinte maneira: **keyparams=&#8221;pqg-params&#8221;** ou **pqg=&#8221;pqg-params&#8221;**.

O modo como o keygen é apresentado varia de navegador a navegador, desde os tempos de Netscape (a Microsoft acreditem – criou um suporte sensacional – porém atrelado a registro de DLL’s, te obrigando a ter um IIS, e por consequencia uma licença de Windows). A interface do usuário para pode ser um menu, botões de rádio, ou até abordagens que ainda não conhecemos. As opções de encriptação apresentam níveis, médio e alto. Se o navegador do usuário estiver configurado para suportar
  
hardware criptográfico (por exemplo, &#8220;smart cards&#8221;), o usuário também poderá escolher aonde salvar seu certificado, em um cartão inteligente ou em um software(browser) e armazenado no disco.

## E o código?

<pre lang="html" line="1"></pre>

Para ver o em ação, clique aqui: <http://koolbanana.com.br/usehtml/keygen.html>

E pra quem achava que keygen era coisa de pirata&#8230;

Gostaria de agradecer o **Gabriel Pereira Borges** por ter ajudado (e inspirado) este post. A dor de cabeça valeu a pena!

### Referências

  * Certificados SSL: http://en.wikipedia.org/wiki/Ssl_certificate  
    http://www.networksolutions.com/SSL-certificates/how-ssl-works.jsp
  * e-cpf: http://www.certisign.com.br/produtos-e-servicos/certificados-digitais/e-cpf  
    http://www.receita.fazenda.gov.br/atendvirtual/solicemrenrevcd.htm
  * Open Group: http://www.opengroup.org/
  * SSO: http://www.opengroup.org/security/sso/  
    http://code.google.com/googleapps/marketplace/sso.html
  * SAML: http://code.google.com/googleapps/domain/sso/saml\_reference\_implementation.html
  * OpenID: http://openid.net/get-an-openid/  
    http://openid.net/get-an-openid/what-is-openid/
  * Reificação: http://pt.wikipedia.org/wiki/Reifica%C3%A7%C3%A3o_(marxismo)
  * RIC: http://portal.mj.gov.br/ric
  * Keygen: https://developer.mozilla.org/En/HTML/Element/keygen  
    Obscure tags: http://obscuretags.com/showcode.php?id=19  
    http://dev.w3.org/html5/markup/keygen.html  
    http://msdn.microsoft.com/en-us/library/cc249768(v=prot.13).aspx
  * documentacao de 1998(!!!): http://devedge-temp.mozilla.org/library/manuals/1998/htmlguide/tags10.html#1615503
  * Gerando chaves com Keygen em IIS: http://forums.hostsearch.com/archive/index.php?t-2094.html
  * IIS suporte a keygen: http://certs.ipsca.com/Support/CSRMicrosoft-Internet-Information-Server-4.0.asp

 [1]: http://www.certisign.com.br/produtos-e-servicos/certificados-digitais/e-cpf
 [2]: http://www.opengroup.org/security/sso/
 [3]: http://openid.net/get-an-openid/what-is-openid/
 [4]: http://openid.net/get-an-openid/
 [5]: http://pt.wikipedia.org/wiki/Reifica%C3%A7%C3%A3o_(marxismo)