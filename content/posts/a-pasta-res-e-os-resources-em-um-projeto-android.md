---
title: A pasta “res” e os resources em um projeto Android
author: Mário Valney
type: post
date: 2015-04-15
excerpt: É preciso mais do que código para fazer um aplicativo para Android. E por mais que amemos código, temos que entender como usar todos os resources de um App.
url: /a-pasta-res-e-os-resources-em-um-projeto-android/
categories:
  - Código
  - Mobile
tags:
  - android
  - Resources

---
É preciso mais do que só código para criarmos um aplicativo realmente bom para Android. E por mais que amemos código, temos que entender como usar todos os recursos que o Android nos dá, por isso, vamos lá!

O primeiro passo é entender que _resources_ o Android nos permite usar na criação de um App.

# Tipos de Resources

Como vamos ver daqui a pouco, todos os resources de um projeto ficam na pasta **res/ **dele. E podem ser basicamente:

<a href="http://developer.android.com/guide/topics/resources/animation-resource.html" target="_blank">Animações<br /> </a>

<p style="padding-left: 30px">
  Podem ser dois tipos &#8220;interpoladas&#8221; (tween animation) e de &#8220;frames&#8221; (frames animation). A primeira consiste em criar uma animação modificando uma única imagem e a segunda segue a lógica do <em>.gif</em> ao criar uma animação com uma sequência de imagens.
</p>

<a href="http://developer.android.com/guide/topics/resources/color-list-resource.html" target="_blank">Cores</a>

<p style="padding-left: 30px">
  Você define cores de acordo com o estado da View.
</p>

<a href="http://developer.android.com/guide/topics/resources/drawable-resource.html" target="_blank">Drawable</a>

<p style="padding-left: 30px">
  Recursos gráficos que podem ser bitmaps ou XML.
</p>

<a href="http://developer.android.com/guide/topics/resources/layout-resource.html" target="_blank">Layout</a>

<p style="padding-left: 30px">
  Você pode definir vários layouts para sua UI e alterná-los de acordo com o estado da aplicação.
</p>

<a href="http://developer.android.com/guide/topics/resources/menu-resource.html" target="_blank">Menu</a>

<p style="padding-left: 30px">
  Assim como os layouts para sua UI, você pode definir &#8220;layouts de menu&#8221; para usá-los na sua aplicação (método <a href="http://developer.android.com/reference/android/app/Fragment.html#onCreateOptionsMenu(android.view.Menu,%20android.view.MenuInflater)" target="_blank">onCreateOptionsMenu()</a> da sua Activity).
</p>

<a href="http://developer.android.com/guide/topics/resources/string-resource.html" target="_blank">Strings</a>

<p style="padding-left: 30px">
  Um recurso super interessante. Pois te permite definir strings e utilizá-las por todo o seu projeto concentrando-as em apenas um lugar, caso queira modificá-las depois. Permite também a internacionalização do seu App, sendo utiliza-da na tradução da sua aplicação.
</p>

<a href="http://developer.android.com/guide/topics/resources/style-resource.html" target="_blank">Estilo</a>

<p style="padding-left: 30px">
  Define aparência e formato dos elementos da sua UI. (Uso bem parecido com o do CSS: concentrar estilização em um único arquivo.)
</p>

<a href="http://developer.android.com/guide/topics/resources/more-resources.html" target="_blank">Outros tipos de Recurso</a>

<p style="padding-left: 30px">
  Assim como as <em>strings</em>, podemos definir valores <em>booleanos</em>, <em>inteiros</em>, <em>dimensões</em>, <em>cores</em> e outras <em>arrays </em>para usarmos por toda a aplicação.
</p>

# A pasta &#8220;res&#8221;

Você deve sempre usar os arquivos e pastas de resource para armazenar valores da sua aplicação, além das imagens, é claro. Dessa forma você consegue manter e atualizar seu código muito mais facilmente, além de poder definir alternativas para cada um deles, de acordo com situações específicas, como diferentes idiomas, tamanhos e orientações de tela. Isso é ótimo, visto a gama imensa de dispositivos que utilizam o sistema do robô verde.

A pasta **res/ **é a pasta do seu projeto que guarda todos os resources da sua aplicação:

[<img class="aligncenter size-full wp-image-48069" src="http://tableless.com.br/uploads/2015/04/Tree-do-Android-Studio.png" alt="Tree do Android Studio" width="408" height="648" />][1]

Cada tipo de recurso que vimos antes deve ficar dentro de uma dessas pastas. Abaixo temos uma tabela retirada da <a href="http://developer.android.com/guide/topics/resources/providing-resources.html" target="_blank">documentação</a> do Android, com os nomes das pastas e os respectivos tipos de resource:

<table>
  <tr>
    <th scope="col">
      Diretório
    </th>
    
    <th scope="col">
      Tipo de Resource
    </th>
  </tr>
  
  <tr>
    <td>
      <code>animator/</code>
    </td>
    
    <td>
      arquivos XML que definem <a href="http://developer.android.com/guide/topics/graphics/prop-animation.html">animações de propriedades</a>.
    </td>
  </tr>
  
  <tr>
    <td>
      <code>anim/</code>
    </td>
    
    <td>
      arquivos XML que definem <a href="http://developer.android.com/guide/topics/graphics/view-animation.html#tween-animation">tween animations</a>. (Animações de propriedades podem ser salvas aqui também, mas o diretório<em> animator/</em> é preferível, por questão de organização)
    </td>
  </tr>
  
  <tr>
    <td>
      <code>color/</code>
    </td>
    
    <td>
      arquivos XML que definem um estado de lista de cores. Veja <a href="http://developer.android.com/guide/topics/resources/color-list-resource.html">Color State List Resource</a>
    </td>
  </tr>
  
  <tr>
    <td>
      <code>drawable/</code>
    </td>
    
    <td>
      arquivos Bitmap (.png, .jpg, .gif) ou arquivos XML que são compilados nos seguintes resources:</p> 
      
      <ul>
        <li>
          arquivos Bitmap
        </li>
        <li>
          <a href="http://developer.android.com/tools/help/draw9patch.html" target="_blank">9-Patch</a> (bitmaps redimensionáveis)
        </li>
        <li>
          listas de estado
        </li>
        <li>
          Shapes (formas)
        </li>
        <li>
          Animações (frame animations)
        </li>
        <li>
          Outros tipos
        </li>
      </ul>
      
      <p>
        Veja <a href="http://developer.android.com/guide/topics/resources/drawable-resource.html">Drawable Resources</a> para mais informações.</td> </tr> 
        
        <tr>
          <td>
            <code>mipmap/</code>
          </td>
          
          <td>
            Arquivos &#8220;drawable&#8221; especificamente para ícones de aplicações de diferentes tipos de densidade.
          </td>
        </tr>
        
        <tr>
          <td>
            <code>layout/</code>
          </td>
          
          <td>
            arquivos XML que definem sua UI (user interface).
          </td>
        </tr>
        
        <tr>
          <td>
            <code>menu/</code>
          </td>
          
          <td>
            arquivos XML que definem os menus da sua aplicação, como Menu de Opções, de Contexto e Sub-menus. Mais informações em: <a href="http://developer.android.com/guide/topics/resources/menu-resource.html">Menu Resource</a>.
          </td>
        </tr>
        
        <tr>
          <td>
            <code>raw/</code>
          </td>
          
          <td>
            Pasta para salvar arquivos na sua forma natural (raw).
          </td>
        </tr>
        
        <tr>
          <td>
            <code>values/</code>
          </td>
          
          <td>
            Arquivos XML que contêm valores, como strings, inteiros, e cores. Dentro dessa pasta você deve nomear cada arquivo XML com o nome do seu resource e dessa forma irá acessar com uma subclasse de <code>R</code>. Por exemplo, o arquivo <code>string.xml</code> será acessado por <code>R.string</code>. Abaixo algumas convenções:</p> 
            
            <ul>
              <li>
                <code>arrays.xml</code> para Arrays.
              </li>
              <li>
                <code>colors.xml</code> para valores de cores.
              </li>
              <li>
                <code>dimens.xml</code> para dimensões.
              </li>
              <li>
                <code>strings.xml</code> para todas as strings.
              </li>
              <li>
                <code>styles.xml</code> para estilos.
              </li>
            </ul>
          </td>
        </tr>
        
        <tr>
          <td>
            <code>xml/</code>
          </td>
          
          <td>
            Arquivos XML que podem ser lidos em tempo de execução chamando <code>&lt;a href="http://developer.android.com/reference/android/content/res/Resources.html#getXml(int)">Resources.getXML()&lt;/a></code>. Vários arquivos XML de configuração podem ser salvos aqui, por exemplo.<br /> <!-- or preferences configuration. -->
          </td>
        </tr></tbody> </table> 
        
        <h1>
           Mas e essas outras pastas?
        </h1>
        
        <p>
          Você deve ter notado que na imagem, temos outras pastas bem parecidas com as que guardam os resources por padrão. São elas: <em>drawable-hdpi</em>, <em>drawable-mdpi</em>, <em>drawable-xhdpi</em> e <em>drawable-xxhdpi</em> (que são variações da pasta <strong>drawable</strong>), <em>layout-land</em>, <em>layout-sw600dp</em> e <em>layout-sw600dp-land</em> (que são variações da pasta <strong>layout</strong>) e as variações da pasta <strong>values</strong>, que são <em>values-en</em>, <em>values-es</em> e <em>values-sw600dp</em>.
        </p>
        
        <div id="attachment_48078" style="width: 429px" class="wp-caption aligncenter">
          <a href="http://tableless.com.br/uploads/2015/04/resource_devices_diagram2.png"><img class="wp-image-48078 size-full" src="http://tableless.com.br/uploads/2015/04/resource_devices_diagram2.png" alt="resource_devices_diagram2" width="419" height="157" /></a>
          
          <p class="wp-caption-text">
            Dois dispositivos diferentes, cada um utilizando um resource de layout diferente.
          </p>
        </div>
        
        <p>
          &nbsp;
        </p>
        
        <p>
          Como vimos antes, um dos maiores benefícios de usarmos a estrutura de resources do Android é a facilidade de manutenção e a capacidade de alterar os resources de acordo com características e configurações dos dispositivos. É por isso que temos essas variações de nomes de pastas. Por exemplo: a pasta <strong>values</strong> guarda o arquivo <em>strings.xml</em>, responsável pelas strings da aplicação, como nome e versão do App, título para cada Activity, URLs e qualquer mensagem ou texto que você usar, mas temos também a pasta <strong>values-es</strong>, que também guarda um arquivo <em>strings.xml</em> (com  as mesmas strings do arquivo anterior), mas que receberá uma prioridade maior, se o idioma do dispositivo for o inglês. Ou seja, o processo de tradução da aplicação se faz apenas colocando valores traduzidos dentro dessa variação da pasta value.
        </p>
        
        <p>
          Resumindo: você pode mudar o nome da pasta para utilizar determinados resources em determinadas condições.
        </p>
        
        <h1>
          Como escolher o nome da pasta dos resources?
        </h1>
        
        <p>
          Se você está usando o Android Studio, o que eu recomendo fortemente (e ensino a instalar <a href="http://mariovalney.com/aula-2-como-instalar-o-android-studio/" target="_blank">aqui</a>), a forma mais fácil de criar uma pasta de resource é clicar com o botão direito do mouse na pasta <strong>res/</strong>, na guia <em>1. Project </em>(imagem anterior) e ir em <strong>New > Android resource directory</strong>.
        </p>
        
        <p>
          Quando você clicar, irá abrir a janela abaixo:
        </p>
        
        <p>
          &nbsp;
        </p>
        
        <p>
          <a href="http://tableless.com.br/uploads/2015/04/New-Resource-Directory.png"><img class="aligncenter size-full wp-image-48074" src="http://tableless.com.br/uploads/2015/04/New-Resource-Directory.png" alt="New Resource Directory" width="843" height="481" /></a>
        </p>
        
        <p>
          No primeiro campo, você pode alterar o nome do diretório (você não precisa digitar nada, pois a IDE irá completar o nome de acordo com as opções que você selecionar). Logo abaixo, você pode escolher o<strong> tipo de resource</strong>.
        </p>
        
        <p>
          Após escolher o tipo de resource, você deve selecionar um dos &#8220;qualificadores&#8221; à esquerda e clicar nas duas setas para a direita, que estão entre os dois quadros. Irá aparecer as opções de cada qualificador. Por exemplo, ao escolher <strong>UI Mode</strong>, teremos a possibilidade de escolher entre <em>Portrait</em>, <em>Landscape</em> e <em>Square</em>:<em><br /> </em>
        </p>
        
        <p>
          <a href="http://tableless.com.br/uploads/2015/04/New-Resource-Directory-Final.png"><img class="aligncenter size-full wp-image-48077" src="http://tableless.com.br/uploads/2015/04/New-Resource-Directory-Final.png" alt="New Resource Directory Final" width="810" height="375" /></a>
        </p>
        
        <p>
          Podemos escolher mais de um qualificador (como na imagem acima) e ao clicar nos itens da coluna da direita (Chosen qualifiers) podemos alterar as opções de cada um. No final, basta clicar em OK.
        </p>
        
        <p>
          Você pode encontrar uma lista completa dos qualificadores, caso queira escolher o nome da pasta manualmente ou não esteja usando o Android Studio, na <a href="http://developer.android.com/guide/topics/resources/providing-resources.html#table2" target="_blank">documentação do Android</a>. Lembrando que a ordem dos qualificadores deve ser a mesma da tabela, ou seja, nomear uma pasta como <strong>drawable-hdpi-port </strong>está errado e <strong>drawable-port-hdpi </strong>está certo, pois o qualificador de orientação da tela (-port) vem antes do qualificador de densidade de píxel (-hdpi).
        </p>
        
        <h1>
          Como acessar esses resources?
        </h1>
        
        <p>
          OK. Já sabemos como organizar nossos arquivos e pastas e como podemos criar um App com a melhor compatibilidade possível. Agora é hora de descobrir como acessar esses arquivos.
        </p>
        
        <p>
          Na verdade é bem simples: utilizaremos o ID de cada resource. E todos os IDs dos resources são definidos na sua classe <strong>R</strong>, que a <em>aapt tool</em> automaticamente gera.
        </p>
        
        <p>
          Quando sua aplicação é compilada a <em>aapt tool </em>gera a classe <strong>R </strong>para os resources dentro da pasta <strong>res </strong>e sub-classes para os tipos de resource. Além disso, para cada resource desse tipo é gerado um inteiro estático. Mas apesar da lasse <strong>R</strong> conter todos os IDs, você não deve precisar olhar nela para acessar um resource, basta saber que um ID é composto pelo tipo e pelo nome do resource (sem extensão). Sendo assim, você já sabe que o ID do seu arquivo<em> activity_about.xml </em>dentro da pasta layout é: <code>layout.activity_about</code>.
        </p>
        
        <p>
          Por fim, existem duas formas de acessar um resource utilizando esse ID:
        </p>
        
        <p>
          <strong>No código: </strong>usando o inteiro estático provido pela classe <strong>R</strong>, assim: <code>R.layout.activity_about</code>. Por exemplo:
        </p>
        
        <pre><code>
@Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_about);
    }
</code>
</pre>
        
        <p>
          <strong>Em um arquivo XML: </strong>usando uma sintaxe especial (@tipo/nome) usando o ID provido pela classe <strong>R</strong>, assim: <code>@string/list_item_textview_title_default</code>. Por exemplo:
        </p>
        
        <pre><code>
    &lt;TextView
        android:id="@+id/list_item_textview_title"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="@string/app_credits"
        style="@style/h1"/&gt;
</code>
</pre>
        
        <h1>
          Conclusão
        </h1>
        
        <p>
          A organização das pastas de resources do Android é bem simples e intuitiva e nos permite tornar nossa aplicação compatível com todos os tipos de dispositivos do mercado. Sendo assim, não temos desculpas para desenvolver aplicações cada vez melhores! Abraços e até a próxima!
        </p>

 [1]: http://tableless.com.br/uploads/2015/04/Tree-do-Android-Studio.png