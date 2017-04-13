---
title: Login com a API do GooglePlus no Android.
author: Alessandro Barreto
type: post
date: 2016-03-31
url: /login-com-api-do-googleplus-no-android/
categories:
  - Código
  - Mobile
tags:
  - android
  - GooglePlus
  - Login

---
Temos uma opção bastante útil hoje em dia no Android, que é usar a sincronização da conta de e-mail do Google.
  
Não vou alongar muito a introdução, vamos partir para a codificação e configuração da API.

## Criando um novo Projeto no AndroidStudio

[<img class="alignnone size-full wp-image-52732" src="http://tableless.com.br/uploads/2016/01/1.png" alt="1" width="472" height="326" />][1]

Digite o **nome** da aplicação e escolha também um nome do **package**, vamos precisar para ativar a API do GooglePlus no **Console do Google.** Continuei a criação e escolha uma **Empty** **Activity**.

## Configuração no Console do Google e Ativação da API

Tenho que informar que essa é a parte mais chata do tutorial, mas enfim com pouco de paciência e atenção vamos conseguir.
  
Acesse o link para configurar <a href="https://developers.google.com/mobile/add?platform=android&cntapi=signin&cnturl=https:%2F%2Fdevelopers.google.com%2Fidentity%2Fsign-in%2Fandroid%2Fsign-in%3Fconfigured%3Dtrue&cntlbl=Continue%20Adding%20Sign-In" target="_blank">Console Configuração</a>. Você irá ver algo parecido com isso:

[<img class="alignnone size-full wp-image-52724" src="http://tableless.com.br/uploads/2016/01/c1.png" alt="c1" width="600" height="337" />][2]

  1. Adicione o **nome** para a sua aplicação (Sugiro que seja o mesmo nome que Adicionou no seu App).
  2. Adicione o nome do **package** (Você pode encontrar esse nome no seu **AndroidManisfest.xml** ou no seu **Gradle app-level** escrito **applicationId**).
  3. Escolha sua Região.
  4. Continue (Choose and configure services).

Feito, vai ser redirecionado a uma página e irar visualizar um campo vazio, lá você vai digitar o seu **SHA-1**. Porém como obter meu SHA-1? Você vai ter que acessar via linha de comando a pasta (**.android**) normalmente ela fica localizada na raiz  (**C:\Users\NomeUsuario\.android**)  dentro você vai perceber um arquivo (chave chamada **debug.keystore** ),** **quando achar digite o seguinte comando na pasta:

<pre>keytool -list -v -keystore debug.keystore -alias androiddebugkey -storepass android -keypass android</pre>

[<img class="alignnone size-full wp-image-52729" src="http://tableless.com.br/uploads/2016/01/cmd.png" alt="cmd" width="956" height="537" />][3]

Caso você não consiga acesse o link para mais informações <a href="https://developers.google.com/android/guides/client-auth" target="_blank">obter SHA-1</a>. Agora copie e cole o SHA-1 no Console do Google e você terá algo:

[<img class="alignnone size-full wp-image-52730" src="http://tableless.com.br/uploads/2016/01/c3.png" alt="c3" width="700" height="361" />][4]

Agora continue (Continue to Generate configuration files). Gere o arquivo, faça o download depois copie e cole na raiz do seu projeto exemplo (C:\Users\Alessandro\AndroidstudioProjects\GoogleSign-In\app\).

[<img class="alignnone size-full wp-image-52731" src="http://tableless.com.br/uploads/2016/01/Sem-títulooo.png" alt="Sem títulooo" width="600" height="337" />][5]

## Voltando para nosso Projeto no AndroidStudio

Feito as devidas configurações no **Console do Google**, vamos configurar o Build Gradle o suporte **Play Services** na nossa aplicação.

1. Adicione a dependência no **project-level** build.gradle:

<pre>classpath 'com.google.gms:google-services:1.5.0-beta2'</pre>

2. Adicione o plugin e dependência no **app-level** build.gradle e o Play services Auth:

<pre>apply plugin: 'com.google.gms.google-services'</pre>

<pre>compile 'com.google.android.gms:play-services-auth:8.3.0'</pre>

[<img class="alignnone size-full wp-image-52733" src="http://tableless.com.br/uploads/2016/01/teste.png" alt="teste" width="956" height="538" />][6]

## Arquivo de Layout

No arquivo de layout **activity_main.xml **adicione:

<pre class="lang-xml">&lt;?xml version="1.0" encoding="utf-8"?&gt;
&lt;LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context="barreto.alessandro.googlesign_in.MainActivity"
    android:orientation="vertical"&gt;

    &lt;RelativeLayout
        android:padding="10dp"
        android:background="#1f737373"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"&gt;

        &lt;ImageView
            android:src="@mipmap/ic_launcher"
            android:id="@+id/ivUsuario"
            android:layout_width="100dp"
            android:layout_height="100dp"
            android:layout_centerHorizontal="true" /&gt;

        &lt;TextView
            android:layout_marginTop="8dp"
            android:text="Android Teste"
            android:layout_centerHorizontal="true"
            android:textAppearance="?android:attr/textAppearanceLarge"
            android:layout_below="@+id/ivUsuario"
            android:id="@+id/tvNome"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content" /&gt;

        &lt;TextView
            android:layout_marginTop="5dp"
            android:layout_centerHorizontal="true"
            android:layout_below="@+id/tvNome"
            android:text="androidteste@gmail.com"
            android:id="@+id/tvEmail"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:textAppearance="?android:attr/textAppearanceMedium"/&gt;

    &lt;/RelativeLayout&gt;

    &lt;LinearLayout
        android:orientation="vertical"
        android:layout_marginTop="16dp"
        android:layout_gravity="center_horizontal"
        android:padding="16dp"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"&gt;

        &lt;com.google.android.gms.common.SignInButton
            android:id="@+id/sign_in_button"
            android:layout_width="match_parent"
            android:layout_height="wrap_content" /&gt;

        &lt;Button
            android:id="@+id/btnDesconectar"
            android:layout_marginTop="10dp"
            android:text="Desconectar"
            android:layout_width="match_parent"
            android:layout_height="wrap_content" /&gt;

        &lt;Button
            android:id="@+id/btnRevogar"
            android:layout_marginTop="10dp"
            android:text="Revogar acesso"
            android:layout_width="match_parent"
            android:layout_height="wrap_content" /&gt;

    &lt;/LinearLayout&gt;
&lt;/LinearLayout&gt;
</pre>

Sem muito comentário sobre o código acima, ele possui:

  * Um **ImageView** para imagem do usuário.
  * Dois **TextView** para nome e e-mail.
  * Três **Buttons** sendo que um customizado, vão servir para Login, Desconectar, Revogar o Acesso do usuário

## A Class Principal

Agora vamos fazer o vinculo entre o XML e Java API (**bindViews**). Crie um método chamado **bindViews** e adicione:

<pre class="lang-java">/**
     * Metodo para fazer o vinculo entre o xml e java api
     */
    private void bindViews(){
        ivUsuario       = (ImageView)findViewById(R.id.ivUsuario);
        tvNome          = (TextView)findViewById(R.id.tvNome);
        tvEmail         = (TextView)findViewById(R.id.tvEmail);
        btnDesconectar  = (Button)findViewById(R.id.btnDesconectar);
        btnRevogar      = (Button)findViewById(R.id.btnRevogar);
        signInButton    = (SignInButton) findViewById(R.id.sign_in_button);
        // litener de clicks
        signInButton.setOnClickListener(this);
        btnDesconectar.setOnClickListener(this);
        btnRevogar.setOnClickListener(this);
    }
</pre>

Vamos solicitar da API informações simples de um login como nome, e-mail, foto e id, no momento é o que necessitamos para esse exemplo.
  
Temos que utilizar o objeto **GoogleSignOptions **e passar como parâmetro **GoogleSignOptions.DEFAULT\_SIGN\_IN** nele contem a opção **requestEmail()**.

<pre class="lang-java">GoogleSignInOptions gso = new GoogleSignInOptions.Builder(GoogleSignInOptions.DEFAULT_SIGN_IN)
                .requestEmail()
                .build();
</pre>

Agora que já temos configurado nossa solicitação, iremos criar um objeto GoogleApiClient com acesso ao login do Google API e as opções especificadas. Colocando tudo em um método que chamei de obterConfiguracoesPadraoLogin() .

<pre class="lang-java">/**
     * Metodo para fazer as primeiras requisições da API para login simples
     */
    private void obterConfiguracoesPadraoLogin(){
        GoogleSignInOptions gso = new GoogleSignInOptions.Builder(GoogleSignInOptions.DEFAULT_SIGN_IN)
                .requestEmail()
                .build();

        mGoogleApiClient = new GoogleApiClient.Builder(this)
                .enableAutoManage(this,this)
                .addApi(Auth.GOOGLE_SIGN_IN_API, gso)
                .build();

    }
</pre>

Agora a **intenção** de login usando uma **Intent do Android** com o método getSignInIntent e passando para o **startActivityForResult**.

<pre class="lang-java">/**
     * metodo para inicar o login
     */
    private void signIn() {
        Intent signInIntent = Auth.GoogleSignInApi.getSignInIntent(mGoogleApiClient);
        startActivityForResult(signInIntent, SIGN_IN);
    }

	@Override
	public void onClick(View v) {
	    switch (v.getId()) {
	        case R.id.sign_in_button:
	            signIn();
	            break;
	        // ...
	    }
	}
</pre>

Apos isso o método **onActivityResult **será chamado com nossos resultados e para recuperar utilizamos o **getSignInResultFromIntent**.

<pre class="lang-java">@Override
    public void onActivityResult(int requestCode, int resultCode, Intent data) {
        super.onActivityResult(requestCode, resultCode, data);

        if (requestCode == SIGN_IN) {
            GoogleSignInResult resultado = Auth.GoogleSignInApi.getSignInResultFromIntent(data);
            if (resultado.isSuccess()){
                GoogleSignInAccount acct = resultado.getSignInAccount();
                obterInfoGoogle(acct);
            }
        }
    }
</pre>

Depois de recuperar o resultado, você pode verificar se a solicitação  deu certo com o método **isSuccess** . Se bem-sucedido, você pode chamar o método **getSignInAccount** para obter um objeto **GoogleSignInAccount** que contém informações sobre o usuário.

<pre class="lang-java">private void obterInfoGoogle(GoogleSignInAccount acct){
        String nome = acct.getDisplayName();
        tvNome.setText(nome);
        String email = acct.getEmail();
        tvEmail.setText(email);
        String id = acct.getId();
        Log.i(TAG,"ID do usuário no GooglePlus "+id);
        String urlFoto = acct.getPhotoUrl().toString();
        Picasso.with(MainActivity.this).load(urlFoto).resize(100,100).into(ivUsuario);
    }
</pre>

Utilizei a lib <a href="http://square.github.io/picasso/" target="_blank">Picasso</a> para o carregamento eficiente de imagem, adicione no seu **Gradle app-level**.

<pre>compile 'com.squareup.picasso:picasso:2.5.2'
</pre>

No **AndroidManifest.xml**

<pre>&lt;uses-permission android:name="android.permission.INTERNET"/&gt;
</pre>

.Agora segue toda a Class **MainActivity**

<pre class="lang-java">package barreto.alessandro.googlesign_in;

import android.content.Intent;
import android.support.v7.app.AppCompatActivity;
import android.os.Bundle;
import android.util.Log;
import android.view.View;
import android.widget.Button;
import android.widget.ImageView;
import android.widget.TextView;

import com.google.android.gms.auth.api.Auth;
import com.google.android.gms.auth.api.signin.GoogleSignInAccount;
import com.google.android.gms.auth.api.signin.GoogleSignInOptions;
import com.google.android.gms.auth.api.signin.GoogleSignInResult;
import com.google.android.gms.common.ConnectionResult;
import com.google.android.gms.common.SignInButton;
import com.google.android.gms.common.api.GoogleApiClient;
import com.google.android.gms.common.api.ResultCallback;
import com.google.android.gms.common.api.Status;
import com.squareup.picasso.Picasso;

public class MainActivity extends AppCompatActivity implements GoogleApiClient.OnConnectionFailedListener, View.OnClickListener {

    private static final String TAG = "TAG";
    private static final int SIGN_IN = 10;

    private ImageView ivUsuario;
    private TextView tvNome,tvEmail;
    private Button btnDesconectar,btnRevogar;
    private SignInButton signInButton;

    private GoogleApiClient mGoogleApiClient;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        bindViews();
        obterConfiguracoesPadraoLogin();

    }

    /**
     * Metodo para fazer o vinculo entre o xml e java api
     */
    private void bindViews(){
        ivUsuario       = (ImageView)findViewById(R.id.ivUsuario);
        tvNome          = (TextView)findViewById(R.id.tvNome);
        tvEmail         = (TextView)findViewById(R.id.tvEmail);
        btnDesconectar  = (Button)findViewById(R.id.btnDesconectar);
        btnRevogar      = (Button)findViewById(R.id.btnRevogar);
        signInButton    = (SignInButton) findViewById(R.id.sign_in_button);
        // litener de clicks
        signInButton.setOnClickListener(this);
        btnDesconectar.setOnClickListener(this);
        btnRevogar.setOnClickListener(this);
    }

    /**
     * Metodo para fazer as primeiras requisições da API para login simples
     */
    private void obterConfiguracoesPadraoLogin(){
        GoogleSignInOptions gso = new GoogleSignInOptions.Builder(GoogleSignInOptions.DEFAULT_SIGN_IN)
                .requestEmail()
                .build();

        mGoogleApiClient = new GoogleApiClient.Builder(this)
                .enableAutoManage(this,this)
                .addApi(Auth.GOOGLE_SIGN_IN_API, gso)
                .build();

    }

    /**
     * metodo para inicar o login
     */
    private void signIn() {
        Intent signInIntent = Auth.GoogleSignInApi.getSignInIntent(mGoogleApiClient);
        startActivityForResult(signInIntent, SIGN_IN);
    }
    

    @Override
    public void onActivityResult(int requestCode, int resultCode, Intent data) {
        super.onActivityResult(requestCode, resultCode, data);

        if (requestCode == SIGN_IN) {
            GoogleSignInResult resultado = Auth.GoogleSignInApi.getSignInResultFromIntent(data);
            if (resultado.isSuccess()){
                GoogleSignInAccount acct = resultado.getSignInAccount();
                obterInfoGoogle(acct);
            }
        }
    }

    private void obterInfoGoogle(GoogleSignInAccount acct){
        String nome = acct.getDisplayName();
        tvNome.setText(nome);
        String email = acct.getEmail();
        tvEmail.setText(email);
        String id = acct.getId();
        Log.i(TAG,"ID do usuário no GooglePlus "+id);
        String urlFoto = acct.getPhotoUrl().toString();
        Picasso.with(MainActivity.this).load(urlFoto).resize(100,100).into(ivUsuario);
    }

    @Override
    public void onClick(View v) {
        switch (v.getId()){
            case R.id.sign_in_button:
                signIn();
                break;
            case R.id.btnDesconectar:
                break;
            case R.id.btnRevogar:
                break;
        }
    }

    @Override
    public void onConnectionFailed(ConnectionResult connectionResult) {
        Log.e(TAG,"onConnectionFailed "+connectionResult.getErrorMessage());
    }

}
</pre>

Falta ainda fazer o **desconectar** e **revogar** acesso, estou deixando para próxima parte, até lá.

 [1]: http://tableless.com.br/uploads/2016/01/1.png
 [2]: http://tableless.com.br/uploads/2016/01/c1.png
 [3]: http://tableless.com.br/uploads/2016/01/cmd.png
 [4]: http://tableless.com.br/uploads/2016/01/c3.png
 [5]: http://tableless.com.br/uploads/2016/01/Sem-títulooo.png
 [6]: http://tableless.com.br/uploads/2016/01/teste.png