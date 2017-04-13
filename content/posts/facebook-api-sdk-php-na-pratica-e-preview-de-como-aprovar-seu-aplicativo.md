---
title: Facebook API – SDK PHP na prática e preview de como aprovar seu aplicativo
author: Marcelo Galvão
type: post
date: 2015-05-13
url: /facebook-api-sdk-php-na-pratica-e-preview-de-como-aprovar-seu-aplicativo/
categories:
  - Back-end
  - Código
  - PHP

---
<img class="aligncenter size-full wp-image-48618" src="http://tableless.com.br/uploads/2015/05/800px-Facebook.png" alt="facebook" width="800" height="301" />

Recentemente o Facebook anunciou que sua API seria atualizada para a versão 4.0 e a mesma sofreria fortes mudanças. Eis que esse dia chegou, pff!
  
A principal dessas mudanças foi a extinção do suporte ao FQL (Facebook Query Language &#8211; uma maneira linda de fazer requisões na API) e que os aplicativos que exigissem permições de publicar na timeline e outras coisas, passariam por um processo de aprovação, parecido com o que ocorre com a AppStore. O novo SDK faz uso de namespaces e roda no PHP 5.4 ou superior.
  
Isso para os desenvolvedores foi um caos, mas para os usuários isso é bem interessante, colocando em ordem a casa e protegendo um pouco mais sua privacidade.

Farei uso da API com o exemplo prático de um aplicativo que pega as fotos do usuários e depois faz um compartilhamento em sua própria timeline. Por fim mostrarei os passos para aprovar o aplicativo. <a href="https://github.com/facebook/facebook-php-sdk-v4/archive/4.0-dev.zip" target="_blank">Clique aqui</a> ou <a href="https://github.com/facebook/facebook-php-sdk-v4/" target="_blank">aqui</a> para baixar o SDK e vamos lá!

## Criando o App

Primeira coisa que você deve fazer é ir no <a href="https://developers.facebook.com/apps/" target="_blank">painel de aplicativos</a> do Facebook Developer e criar um novo aplicativo. É um processo bem simples e por isso vou pular essa parte. Quando solicitado a plataforma do seu app, selecione Site (www). E lá em Settings altere o &#8220;Website -> Site URL&#8221; para a URL da sua aplicação, pode ser http://localhost/ .

## Login

Em sua aplicação de Facebook você pode realizar o login do usuário usando o SDK JavaScript ou PHP. Não gosto muito de realizar o login via PHP porque já tive alguns problemas com o tal da URL Redirect (não lembro exatamente o porque rsrs, isso foi no boom das abas de fanpage e ações promocionais chovendo em sua timeline), devido a isso vou demonstrar das duas maneiras.

## Login via JavaScript

<pre lang="lang-php">// login via javascript
$('#bt-facebook').click( function(event){

    event.preventDefault();    
    destino = this.href;

    FB.login( function(response){
        if (response.authResponse) {
            document.cookie = 'meuapp_userid='+response.authResponse.userID;
            document.cookie = 'meuapp_token='+response.authResponse.accessToken;
            window.location.href = destino;
        }else{
            // console.log('O usuário Cancelou o login ou não autozirou.');
        }
    }, {scope: 'user_photos, publish_actions'});    
});
</pre>

Na linha 2 eu simulei que a solicitação veio através de um clique num link <a>. Na linha 5 guardamos o destino do link para uso posterior. Na linha 7 fazemos a chamada ao método FB.login() que irá abrir uma caixa de diálogo na tela solicitando permissão ao usuário. Caso o usuário permita o login nas linhas 9 e 10 deixamos salvo o ID do usuário e o token da permissão para uso futuro. Deixei num cookie, mas fica a vontade para guardar isso da maneira que julgar melhor. E por fim na linha 11 envio o usuário para a página de destino do link, a página principal da aplicação quando logado.
  
É importante observar a linha 15, onde mencionamos todas as permissões que vamos precisar do usuário. <a href="https://developers.facebook.com/docs/facebook-login/permissions/v2.3#reference" target="_blank">Clique aqui</a> pra ver a lista de permissões.

Ah, lembre-se de adicionar a chamada ao SDK JavaScript colocando o código abaixo antes do fechamento da tag <body>.

<pre lang="lang-javascript">&lt;script&gt;
  window.fbAsyncInit = function() {
    FB.init({
      appId      : 'APP_ID',
      xfbml      : true,
      version    : 'v2.3'
    });
  };

  (function(d, s, id){
     var js, fjs = d.getElementsByTagName(s)[0];
     if (d.getElementById(id)) {return;}
     js = d.createElement(s); js.id = id;
     js.src = "//connect.facebook.net/en_US/sdk.js";
     fjs.parentNode.insertBefore(js, fjs);
   }(document, 'script', 'facebook-jssdk'));
&lt;/script&gt;
</pre>

Lembre-se de trocar o APP_ID pelo ID da sua aplicação.

## Login via PHP

<pre lang="lang-javascript">// arquivo 1
require 'facebook/autoload.php';
use Facebook\FacebookSession;
use Facebook\FacebookRedirectLoginHelper;
use Facebook\FacebookRequest;

FacebookSession::setDefaultApplication('APP_ID', 'APP_SECRET');

$helper = new FacebookRedirectLoginHelper('URL_ARQUIVO_2');
$loginUrl = $helper-&gt;getLoginUrl();
echo "<a href="\&quot;$loginUrl\&quot;">login via php</a>";


// arquivo 2
require 'facebook/autoload.php';
use Facebook\FacebookSession;
use Facebook\FacebookRedirectLoginHelper;
use Facebook\FacebookRequest;
use Facebook\GraphUser;
use Facebook\Entities\AccessToken;

FacebookSession::setDefaultApplication('APP_ID', 'APP_SECRET');
$helper = new FacebookRedirectLoginHelper('URL_ARQUIVO_2');
try {
  $session = $helper-&gt;getSessionFromRedirect();
} catch(FacebookRequestException $ex) {
  // When Facebook returns an error
} catch(\Exception $ex) {
  // When validation fails or other local issues
}

if ($session) {
  echo "Usuário logado.";
  
  $me = (new FacebookRequest(
	  $session, 'GET', '/me'
	))-&gt;execute()-&gt;getGraphObject(GraphUser::className());

  // echo $token = $session-&gt;getToken();
  setcookie('tacaruna_token', $session-&gt;getToken());
  setcookie('tacaruna_userid', $me-&gt;getProperty('id'));
  header("Location: mosaico.php");

}else{
  echo "Não logado";
}
</pre>

Não vou entrar em detalhes nesses arquivos de login via PHP porém mais abaixo tudo é explanado. Lembre-se de trocar APP\_ID, APP\_SECRET e URL\_ARQUIVO\_2 pelos seus respectivos valores.

## Pegando as fotos do usuário

<pre>/* INCLUDE NO AUTOLOAD E CHAMA AS CLASSES NECESSÁRIAS */
require 'facebook/autoload.php';
use Facebook\FacebookSession;
use Facebook\FacebookJavaScriptLoginHelper;
use Facebook\FacebookRequest;
use Facebook\GraphUser;

FacebookSession::setDefaultApplication('APP_ID', 'APP_SECRET');

/* VERIFICA SE ESTA LOGADO */
$helper = new FacebookJavaScriptLoginHelper();
try {
  $session = new FacebookSession($_COOKIE['meuapp_token']);
}catch(FacebookRequestException $ex) {
  // When Facebook returns an error
}catch(\Exception $ex) {
  // When validation fails or other local issues
}

// caso não esteja logado
if (!$session) exit('Usuário não logado ou token expirado.');

/* PEGA OS DADOS DO USUÁRIO */
try {
	$response = (new FacebookRequest($session, 'GET', '/me'))-&gt;execute();
	$object = $response-&gt;getGraphObject();

	$fbid = $object-&gt;getProperty('id');
	$fbname = $object-&gt;getProperty('name');
	$fbgender = $object-&gt;getProperty('gender');

} catch (FacebookRequestException $ex) {
  // echo $ex-&gt;getMessage();
} catch (\Exception $ex) {
  // echo $ex-&gt;getMessage();
}


/* PEGA OS ALBUNS */
$response = (new FacebookRequest($session, 'GET', '/me/albums'))-&gt;execute();
$graphObject = $response-&gt;getGraphObject()-&gt;asArray();
$albuns = array();
foreach($graphObject['data'] as $v) $albuns[] = $v-&gt;id;

/* PEGA AS FOTOS */
// $x = 0;
foreach($albuns as $v){
	$response = (new FacebookRequest($session, 'GET', "/$v/photos"))-&gt;execute()-&gt;getGraphObject()-&gt;asArray();

	foreach($response['data'] as $fotos){
		echo '&lt;img src="'.$fotos-&gt;picture . '" data-source="'.$fotos-&gt;source.'"&gt;&lt;br&gt;';
		// if (++$x === 50) break;
	}	
}
</pre>

Nas linhas iniciais nos chamados o autoload da API para evitar ficar dando milhões de include e logo depois chamamos as classes do SDK que iremos utilizar. Na linha 8 setamos as configurações do nosso aplicativo, substitua APP\_ID e APP\_SERCRET pelos do seu aplicativo.
  
Da linha 10 à 18, verificamos se o usuários está logado. Lembra que no login eu guardei o token num cookie? Olha ele aí na linha 13.
  
Da linha 24 à 36 pegamos os dados do usuário logado para caso queira guardar num banco de dados, etc. Dê um var_dump na variável $object e veja o que ele contém.
  
Para pegar as fotos do usuário primeiro vamos pegar os álbuns e aí depois as fotos contida neles. Antigamente você pegava todas as fotos com apenas uma requisição =/ Da linha 40 à 43 pegamos os IDs dos álbuns e nas linhas 47 à 54 pegamos as fotos e exibimos na tela. Mais uma você pode dar um var_dump em $fotos e ver os dados que ela contém, são vários.

## Compartilhando na timeline

<pre>/* INCLUDE NO AUTOLOAD E CHAMA AS CLASSES NECESSÁRIAS */
require 'facebook/autoload.php';
use Facebook\FacebookSession;
use Facebook\FacebookJavaScriptLoginHelper;
use Facebook\FacebookRequest;
use Facebook\GraphUser;
use Facebook\FacebookRequestException;
use Facebook\GraphObject;

FacebookSession::setDefaultApplication('APP_ID', 'APP_SECRET');

/* VERIFICA SE ESTA LOGADO */
$helper = new FacebookJavaScriptLoginHelper();
try {
  $session = new FacebookSession($_COOKIE['meuapp_token']);
}catch(FacebookRequestException $ex) {
  // When Facebook returns an error
}catch(\Exception $ex) {
  // When validation fails or other local issues
}

// caso não esteja logado
if (!$session){
  exit('Usuário não logado ou token expirado.');

}else{
  
  /* COMPARITLHA */
  $img = realpath("CAMINHO_DA_IMAGEM");
  $txt = "TEXTO_DIGITADO_PELO_USUARIO";

  try {

    $response = (new FacebookRequest(
      $session, 'POST', '/me/photos', array(
        'source' =&gt; new CURLFile($img, 'image/jpeg'),
        'message' =&gt; "$txt"
      )
    ))-&gt;execute()-&gt;getGraphObject();

  	echo  $response-&gt;getProperty('id');

  } catch(FacebookRequestException $e) {

    // echo "Exception occured, code: " . $e-&gt;getCode();
    // echo " with message: " . $e-&gt;getMessage();
    exit("Erro ao compartilhar.");
  }
}
</pre>

Mais uma vez nas linhas iniciais nos chamados o autoload da API setamos as configurações do nosso aplicativo e logo verificamos se o mesmo está logado. Na linha 29 nos colocamos o realpath do caminho da imagem que iremos compartilhar (caso a versão do seu PHP seja inferior a 5.5, altere a linha 36 para: &#8216;source&#8217; => ‘@‘. $img). Na linha 30 temos uma frase que irá acompanhar a postagem/foto escrita pelo próprio usuário. Não é obrigado conter uma frase, pode deixar em branco. O que não pode é deixar um texto pré-definido. Caso isso ocorra o seu app não será aprovado.

## Aprovando o aplicativo

Enviar o aplicativo para aprovação não é um bicho de sete cabeças. Dá um pouco de trabalho porque você precisa tirar alguns printscreen, escrever um passo a passo e mais algumas informações. Para alguns &#8211; e principalmente agências de publicidade, isso é um inferno porque para precisaríamos de todo o layout já pronto, mas você pode dar um jeito de adiantar esse processo fazendo você mesmo um pré-layout baseado no wireframe que já serve, não precisa estar lindão, só precisa ter o protótipo do seu aplicativo com um bom gosto no css que já é o suficiente!
  
O Facebook deixou um <a href="https://developers.facebook.com/docs/opengraph/submission-process" target="_blank">página dedicada</a> a isso bem explicada e com imagens ilustrando e tudo mais. Lá no painel em Status & Review quando você clicar em Start a Submission ele vai apontar para você que está faltando e daí você vai fazendo, etc.
  
Lembre-se de deixar o seu aplicativo visível para o todos (público) para facilitar, mas pelo que vi você pode deixar privado e designar um usuário de teste para eles testarem.

<img class="aligncenter wp-image-48607 size-full" src="http://tableless.com.br/uploads/2015/05/status-public.jpg" alt="" width="500" height="161" />

Em App Details você precisa preencher a maioria dos campos, em português mesmo. Também precisa de pelo menos 3 screenshots do seu aplicativo bem como a maioria das imagens de capa, baner, ícone, etc.

<img class="aligncenter wp-image-48608 size-full" src="http://tableless.com.br/uploads/2015/05/informacoes.jpg" alt="" width="500" height="1042" />

É importante observar que como mencionei anteriormente, não podemos deixar uma frase de compartilhamento pré-definida, o que um dia foi um prática comum da maioria das marcas. Caso isso ocorra seu aplicativo não será aprovado.
  
O Facebook diz que pode precisar de até 15 dias úteis para aprovar, mas nesse exemplo que apresentei aqui ele pedio 5 dias e terminou aprovando em apenas 1 dia 🙂

Então é isso, e boa sorte na aprovação!