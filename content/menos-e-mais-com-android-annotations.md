---
title: Menos é mais com Android Annotations
author: Pablo Silva
type: post
date: 2016-09-19
url: /menos-e-mais-com-android-annotations/
titulo_personalizado:
  - 'Menos é mais com <strong>Android Annotations</strong>'
categories:
  - Destaques
  - Mobile
tags:
  - android
  - frameworks
  - mobile

---
De todo o trabalho que você tem ao programar uma aplicação android, uma grande parte dele é por conta de todo o código _boilerplate_ que **sempre** temos que fazer. Uma das coisas que mais me incomoda é que todos os recursos (_views e afins_) precisam ser referenciados para poderem ser acessados e isso, dependendo da quantidade de recursos que você precisa ter na aplicação, pode resultar em muitas e muitas linhas de código. Se você precisar criar eventos, serviços, _broadcasts_, _adapters_ ou rodar o código em uma nova _thread_  nem vou colocar em questão aqui!

Nós que programamos para android acabamos nos <del>conformando</del> acostumando com todo esse código e tempo perdido que ele gera para ser produzido porque, num fluxo normal de desenvolvimento, ele é inevitável. Sem falar em classes gigantes as quais precisaremos manter depois. E foi exatamente por estes motivos que as **<a href="http://androidannotations.org/" target="_blank">Android Annotations</a> ** foram criadas.

Essas anotações fazem parte de um framework de código livre, que utiliza <a href="https://pt.wikipedia.org/wiki/Inje%C3%A7%C3%A3o_de_depend%C3%AAncia" target="_blank">injeção de dependência</a>, para nos ajudar a eliminar todo aquele _boilerplate_, trocando-os por anotações. Uma vez que diminuímos a quantidade de código que temos que escrever, fica mais fácil de manter a aumentamos a velocidade com que desenvolvemos nossas aplicações.

Vou demonstrar aqui como utilizar as _annotation__s _em alguns dos elementos que eu mencionei para que vocês vejam como é fácil e simples e como melhora o nosso código. Vamos supor que você tem uma _main activity_ com 5 views e precisará pegar o valor do usuário de todas elas, como acontece em um cadastro por exemplo.

Primeiro vamos declarar nosso layout num arquivo XML (não estou me preocupando com a estética do layout)

<pre class="xml">&lt;!-- activity_register.xml --&gt;
&lt;LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="fill_parent"
    android:layout_height="fill_parent"
    android:orientation="vertical"
    android:layout_gravity="left"
    android:gravity="left" &gt;

    &lt;EditText
        android:id="@+id/name"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="16dp" /&gt;

    &lt;EditText
        android:id="@+id/address"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content" /&gt;

    &lt;EditText
        android:id="@+id/numberAddress"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content" /&gt;

    &lt;EditText
        android:id="@+id/telephone"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content" /&gt;

    &lt;EditText
        android:id="@+id/birthday"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content" /&gt;
    
    &lt;Button
        android:id="@+id/saveButton"
        android:layout_width="140dp"
        android:layout_height="wrap_content"
        android:text="Save" /&gt;

&lt;/LinearLayout&gt;
</pre>

e agora precisaremos criar a nossa _main activity_ para injetarmos nossas _views_ e obter as entradas do usuário. Da maneira normal fica assim

<pre class="java">public class Calculator extends Activity {
  private EditText name;
  private EditText address;
  private EditText numberAddress;
  private EditText telephone;
  private TextView birthday;
  private Button saveButton;

  @Override
  public void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.activity_register);

    name = (EditText) findViewById(R.id.name);
    address = (EditText) findViewById(R.id.address);
    numberAddress = (EditText) findViewById(R.id.numberAddress);
    telephone = (EditText) findViewById(R.id.telephone);
    birthday = (EditText) findViewById(R.id.birthday);
    saveButton = (Button) findViewById(R.id.addButton);

    saveButton.setOnClickListener(new View.OnClickListener() {
      public void onClick(View v) {
       # save the information
       ...
      }
    });
  }
}
</pre>

Como era de se esperar, inflamos nosso _layout_ xml no método `onCreate` e obtemos a referência de cada uma das _views_ das quais precisamos obter o valor (para o nosso caso todas). Além disso criamos um evento no botão de salvar, que obviamente tem a função de salvar nossos dados (não fiz a implementação disso aqui para manter simples o exemplo). Ao utilizarmos _Android Annotations_, o nosso código fica assim

<pre class="java">@EActivity(R.layout.activity_register)
public class Calculator extends Activity {
  @ViewById EditText name;
  @ViewById EditText address;
  @ViewById EditText numberAddress;
  @ViewById EditText telephone;
  @ViewById TextView birthday;
  @ViewById Button saveButton;

  @Click
  public void saveButton() {
     # as views já estão referenciadas
     # name.getText(); já está disponível por exemplo

     # salvar as informações
     ...
  }
}
</pre>

Como vocês podem perceber de cara o código é bem menor. Não precisamos mais do método `onCreate` porque para este exemplo espcificamente, a única coisa que estamos fazendo lá era inflando nossas views através do nosso layout e isso é feito automaticamente para nós utilizando a anotação `@EActivity`. Em relação a referenciar as nossas _views_, isso é feito somente adicionando a anotação `@ViewById` antes de cada uma delas que queremos referenciar. Ao fazer isso nossas _views_ já estão prontas para serem acessadas. Algo que é importante de se saber é que para que as anotações tenham efeito, os atributos precisa ter o mesmo nome das ids que estão no xml, do contrário você precisará indicar a id da seguinte maneira

<pre class="java">@ViewById(R.id.name)
EditText name;
</pre>

o que eu não recomendo que você faça pois o interessante é utilizar todo o poder do _framework_ ao nosso favor. Outro elemente que não precisamos implementar foi o evento no botão de salvar, que foi substituído pela anotação `@Click` que colocamos acima do método em que vamos tratar o nosso evento. Como vocês já devem ter percebido, o nome do método precisa ter como nome o nome do nosso botão referenciado logo acima.

E isso é tudo que precisamos fazer para inflar nossas views e adicionar um evento no nosso botão. É claro que esse é um exemplo bem básico. Agora pense em um projeto grande com múltiplas _activities_ e _fragments_, o quanto isso nos ajudaria a economizar tempo. E além do mais, o que eu mostrei aqui é só um pouquinho (pouquinho mesmo) do que se pode fazer com as anotações.

Você pode conferir todo o poder que o AA tem visitando a seu <a href="https://github.com/excilys/androidannotations/wiki/Cookbook" target="_blank">cookbook</a>. Lá existem diversos exemplos que servem como _guideline _para você começar a utilizar o _framework_ hoje mesmo e parar de perder tempo escrevendo aquele mesmo código de novo e de novo em todos os seus projetos. Eu duvido que você vai se arrepender. Até a próxima!