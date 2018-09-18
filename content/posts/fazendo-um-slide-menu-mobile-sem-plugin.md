---
title: Fazendo um slide menu mobile – sem plugin
authors: Diego Eis
type: post
date: 2013-09-30
excerpt: Entenda como fazer um menu como nos aplicativos mobile, como o facebook.
url: /fazendo-um-slide-menu-mobile-sem-plugin/
dsq_thread_id: 1809874159
categories:
  - Código
  - CSS3
  - HTML
  - Técnicas e Práticas
tags:
  - CSS
  - css transform
  - CSS3
  - Javascript
  - translate

---
Vou ensinar o básico para você que quer fazer um slide menu para mobile, isso quer dizer que você vai ter **pouquíssimo** javascript. Por isso não vai ter swipe para fazer o menu aparecer.

## O resultado

O resultado é bastante simples: você quer um menu como os apps nativos, daqueles que o menu fica escondido na esquerda e quando há um clique naqueles três &#8220;risquinhos&#8221; o menu sai da esquerda e vai para a direita. Geralmente, até a atualização do iOS7, o menu empurrava o conteúdo principal para o lado. Vamos fazer essa versão!

Veja aqui o resultado final.

{{< codepen 
  hash="ADnfr"
  user="diegoeis"
  author="Diego Eis"
  title="Slide menu 3"
  height="401"
>}}

## O HTML

O código HTML pode ser feito de várias formas. O mais fácil é se você conseguir fazer uma versão mobile e desktop usando a mesma estrutura HTML para não precisar fazer ajustes malucos. O formato mais básico que você pode fazer é tirando o MENU de dentro do header, ficando com a estrutura nessa ordem: HEADER, MENU, MAIN. Como abaixo:

<pre class="lang-html">&lt;header&gt;
	&lt;h1&gt;LOGO&lt;/h1&gt;
	&lt;input type="text" value="busca"&gt;
        &lt;span class="menu-anchor"&gt;Menu&lt;/span&gt;
&lt;/header&gt;

&lt;menu&gt;
	&lt;ul&gt;
		&lt;li&gt;&lt;a href="#"&gt;Home&lt;/a&gt;&lt;/li&gt;
		&lt;li&gt;&lt;a href="#"&gt;Produtos&lt;/a&gt;&lt;/li&gt;
		&lt;li&gt;&lt;a href="#"&gt;Servi&ccedil;os&lt;/a&gt;&lt;/li&gt;
		&lt;li&gt;&lt;a href="#"&gt;Sobre&lt;/a&gt;&lt;/li&gt;
		&lt;li&gt;&lt;a href="#"&gt;Contato&lt;/a&gt;&lt;/li&gt;
	&lt;/ul&gt;
&lt;/menu&gt;

&lt;section class="main"&gt;
   &lt;p&gt;Conte&uacute;do do site&lt;/p&gt;
&lt;/section&gt;
</pre>

Lembrando que se você não se sentir à vontade com essa estrutura, faça modificações para manter do jeito que você quer. Isso vai exigir adaptações também no CSS. Essa estrutura te facilita as coisas, embora danifique um pouquinho a semântica.

Aquele SPAN ali é necessário. Você pode inserí-lo via Javascript em um mundo ideal, assim o código html original não fica tão sujo. Para não complicarmos este tutorial, vamos deixar ele direto no html, ok?

## O Javascript

Coisa simples. Pudim de leite. Mamão com açúcar. Você não fará nada complexo, só precisa apenas incluir uma classe da tag HTML (ou body se preferir) para sabermos quando o menu está ativo. O código abaixo resolve bem.

<pre class="lang-javascript">$('.menu-anchor').on('click touchstart', function(e){
	$('html').toggleClass('menu-active');
  	e.preventDefault();
});
</pre>

Na primeira linha capturamos o clique no elemento **.menu-anchor**, que é o botão que terá os 3 risquinhos tradicionais. Note que eu também coloquei um outro evento para ser capturado chamado **touchstart**. Este evento detecta quando o touch inicia na tela do aparelho. O [Javascript já entende esse evento][1] nativamente. É interessante que ele esteja ali, para que os mobiles tenham uma performance e receptividade melhor. Geralmente com [o click o Safari Mobile tem um delay de 300ms][2] para identificar a ação e só depois desse tempo ele executa. Com o **touchstart** previnimos isso, fazendo-o executar a função assim que o touch iniciar. É necessário ter o click também para contemplarmos aparelhos que usam ponteiros, como o mouse. Aparelhos que suportam ponteiros e touch estão se popularizando desde o lançamento do Windows 8. 

## O CSS

Agora iniciamos a mágica do CSS. Suponha que você já tenha o layout pronto, posicionando o menu onde ele deveria ficar quando aberto. Como esse exemplo: 

{{< codepen 
  hash="pCiah"
  user="diegoeis"
  author="Diego Eis"
  height="375"
>}}

Note que o menu ainda está em cima do HEADER e do MAIN. Vamos então deslocá-lo de forma que ele fique escondido, fora do viewport. Assim que o script acima for executado e inserir a classe **menu-active** no HTML, você muda a posição do menu, fazendo-o reaparecer na posição original.

> Simuladores ajudam muito, mas só bata o martelo se você já tiver testado em alguns aparelhos reais, só assim você vai ter certeza do tamanho da tela, utilização real, performance e outros ajustes.

Sua primeira reação pode ser essa: &#8220;é bico: basta fazer uma jogadkmha com position, manipulando o valor da propriedade left e pronto&#8221;. Aí você testa em tudo quanto é simulador (eu uso o nativo do iPhone no Mac) e vê que tudo funciona bem. O código fica mais ou menos assim:

_**Não esqueça de usar os prefixos de browser nas propriedades transition e transform**_

<pre class="lang-css">/* posicionando pra fora do viewport */
.menu {
   left: -220px;
   transition: left .25s linear;
}

/* quando o script inserir a classe, nós retornamos o menu para a posição original */
.menu-active .menu {
   left: 0;
}
</pre>

Mas aí você testa em um aparelho de verdade e vê que a animação tem um lag maldito. O problema é que fazer animação com position é uma desgraça! Quando animamos os valores de position do CSS, há uma carga de processamento muito grande do browser para fazer tudo aqui acontecer. Você só percebe a olho nu quando testa direto nos aparelhos. E aqui vai outra dica: use sempre aparelhos para testar suas versões. Simuladores ajudam muito, mas só bata o martelo se você já tiver testado em alguns aparelhos reais, só assim você vai ter certeza do tamanho da tela, utilização real, performance e outros ajustes.

### CSS Repainting

Se você não leu ainda o estudo que o Paul Irish fez [sobre movimentar elementos usando translate em vez de position, vá agora lá e leia][3]. Ele também comenta que o [Chris Coyier fez um estudo antes também][4]. Estou preparando um artigo sobre o assunto que logo mais será publicado aqui no Tableless.

Quando você posiciona qualquer elemento em um determinado lugar da tela utilizando coordenadas em position, o browser redenha aquele elemento naquela coordenada que você definiu. Quando você faz uma animação, onde você muda a coordenada seguidamente, o browser redesenha aquele elemento pixel por pixel durante toda a animação. Em um ou outra animação no desktop fica difícil ver a olho nu a força que o browser está fazendo. Mas quando usamos o inspector e monitoramos os frames, você percebe que o browser passa muito tempo redesenhando o elemento na tela, pixel por pixel, passo a passo durante toda a animação.

No inspector você pode perceber exatamente o que browser faz quando vai na parte de TIMELINE > FRAME, percebe o processo executado.

<img src="https://raw.githubusercontent.com/diegoeis/tableless-static-images/master/2013/09/Screen-Shot-2013-09-29-at-8.40.25-PM.png" alt="Screen Shot 2013-09-29 at 8.40.25 PM" width="949" height="432" class="alignnone size-full wp-image-39086" srcset="uploads/2013/09/Screen-Shot-2013-09-29-at-8.40.25-PM.png 949w, uploads/2013/09/Screen-Shot-2013-09-29-at-8.40.25-PM-329x149.png 329w, uploads/2013/09/Screen-Shot-2013-09-29-at-8.40.25-PM-588x267.png 588w, uploads/2013/09/Screen-Shot-2013-09-29-at-8.40.25-PM-660x300.png 660w" sizes="(max-width: 949px) 100vw, 949px" />

Quando usamos o top/left, o browser leva um tempo muito grande para redesenhar cada frame da animação, o que resulta em uma animação ruim, nada suave. Se o elemento utiliza muitos detalhes como sombras, bordas, transparências e etc, o browser consome muito processamento para gerar todos esses efeitos. Se há uma sombra atrás do elemento por exemplo, o browser tem que calcular todo o gradiente semi-transparente que essa sombra gera com o background da página a todo momento. 

Ao fazermos a animação usando o translate da propriedade transform do CSS3, todo esse cálculo é feito diretamente pela GPU, em uma linha de processamento própria chamada RenderLayer, usando a placa de vídeo do aparelho para calcular tudo isso. Qualquer transformação 2D, 3D, mudanças de opacidade e tudo mais é executado pela GPU do dispositivo, fazendo uma animação mais suave.

Veja uma comparação abaixo. Do lado esquerdo é uma animação usando posicionamento normal, com absolute, top/left. Do lado direito é usando o CSS Transform.

<img src="https://raw.githubusercontent.com/diegoeis/tableless-static-images/master/2013/09/timeline-frames-macbook1.png" alt="timeline-frames-macbook1" width="720" height="193" class="alignnone size-full wp-image-39087" srcset="uploads/2013/09/timeline-frames-macbook1.png 720w, uploads/2013/09/timeline-frames-macbook1-329x88.png 329w, uploads/2013/09/timeline-frames-macbook1-588x157.png 588w, uploads/2013/09/timeline-frames-macbook1-660x176.png 660w" sizes="(max-width: 720px) 100vw, 720px" />

As barras verdes indicam o quanto o elemento foi redesenhado na tela.

Se você ainda não parou pra entender essa ferramenta do inspector, me faça um favor e vai lá dar uma olhadinha. No Chrome é melhor.

### Animando as coisas com translate

Se você não sabe ainda o que é o translate, sugiro que pare aqui e [leia agora esse artigo][5]. Agora que você sabe o básico sobre a performance do translate e top/left, vamos voltar à nossa programação normal. Você vai precisar mover 3 elementos: o header, o main e o menu. O HEADER e o MAIN começarão com o valor inicial de 0, obviamente por que eles estarão em seus lugares originais, o código fica assim:

<pre class="lang-css">/*
   Essa é a posição original do HEADER e do MAIN
*/
header, .main {
	-webkit-transform: translateX(0);
}
</pre>

Agora temos que colocar o MENU para fora da tela, essa vai se a posição inicial dele. O código fica assim:

<pre class="lang-css">/*
   Aqui você esconde o menu para fora da tela 
   O valor é exatamente a largura da sidebar
*/
menu {
	transform: translateX(-220px);
}
</pre>

O valor ali é exatamente o valor da largura do MENU. E esse será o valor que iremos colocar no translate final do HEADER e do MAIN.

Lembra-se do processo? Quando clicarmos nos 3 risquinhos, o javascript adiciona a classe **menu-active** na tag HTML. Quando houver essa classe, o HEADER e o MAIN tem o valor do translate alterado, empurrando-os para a direta. O MENU também terá seu translate alterado, para o valor 0, fazendo-o voltar para a tela. O código mostrando essas diferenças é o que segue abaixo:

<pre class="lang-css">/*
   Com a classe menu-active na tag HTML
*/
.menu-active menu {
	transform: translateX(0);
}

.menu-active header, 
.menu-active .main {
	transform: translateX(220px);
}
</pre>

Maravilha! Veja como está agora sem animação:

{{< codepen 
  hash="kBmDJ"
  user="diegoeis"
  author="Diego Eis"
  title="Slide menu 2"
  height="393"
>}}

Vamos inserir agora a animação. Usaremos para isso a propriedade transition do CSS3. Se você não conhece essa propriedade, leia [esse][6], [esse][7] e [esse][7] artigo para entender melhor.

<pre class="lang-css">/*
	Aqui você esconde o menu para fora da tela 
	O valor é exatamente a largura da sidebar
*/
menu {
	transform: translateX(-220px);
	transition: all .25s linear;
}

/*
	Essa é a posição original do HEADER e do MAIN
*/
header, .main {
	transform: translateX(0);
	transition: all .25s linear;
}
</pre>

Veja o resultado final com animação:

{{< codepen 
  hash="ADnfr"
  user="diegoeis"
  author="Diego Eis"
  title="Slide menu 3"
  height="401"
>}}

E eu acho que é só. Se quiser ver direto no seu aparelho, visite este endereço: <https://cdpn.io/ADnfr>

 [1]: https://developer.mozilla.org/en-US/docs/Web/API/TouchEvent
 [2]: https://www.google.com.br/search?client=safari&rls=en&q=click+mobile+delay&ie=UTF-8&oe=UTF-8&gws_rd=cr&ei=mFhHUsPyIpSI9ATun4HwDg
 [3]: https://www.paulirish.com/2012/why-moving-elements-with-translate-is-better-than-posabs-topleft/
 [4]: https://css-tricks.com/tale-of-animation-performance/
 [5]: https://tableless.com.br/css-transforms/
 [6]: https://tableless.com.br/transition-e-animation/
 [7]: https://tableless.com.br/introducao-ao-css-animation/