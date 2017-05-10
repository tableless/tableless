---
title: RGB e HSL
author: Diego Eis
type: post
date: 2011-06-27
excerpt: RGB e HSL são os formatos que estão se tornando populares no desenvolvimento web. Entenda como cada um funciona e saiba quais suas vantagens.
url: /rgb-e-hsl/
tweetbackscheck:
  - 1356422305
shorturls:
  - 'a:3:{s:9:"permalink";s:33:"http://tableless.com.br/rgb-e-hsl";s:7:"tinyurl";s:26:"http://tinyurl.com/3tgl4pb";s:4:"isgd";s:19:"http://is.gd/mYuEkX";}'
twittercomments:
  - 'a:6:{i:109965506114629632;s:7:"retweet";i:109689656509083648;s:7:"retweet";i:109688123797143552;s:7:"retweet";i:109680690844545024;s:7:"retweet";i:149525146946904064;s:7:"retweet";i:148725116312879104;s:7:"retweet";}'
tweetcount:
  - 11
dsq_thread_id: 503040329
categories:
  - CSS
  - CSS3
  - HTML
tags:
  - 2011
  - CSS3
  - desenvolvimento web
  - web standards

---
A manipulação de cores no HTML nunca foi muito flexível. No começo escolhíamos as cores escrevendo seus nomes por extenso. Os nomes eram padrões eram: black, blue, yellow, green, olive, maroon, fuchsia, red, white, silver, navy, teal, purple, lime, gray, aqua. Na década de 80 houve um acréscimo de 131 novas cores com nomes estranhos chamada [X11][1]. Estes nomes foram adotados pelos primeiros browsers tem sido suportados até hoje. Há nomes como mintcream, moccasin, navajowhite, powderblue, springgreen entre outros&#8230; O W3C ainda mantém uma [lista completa com os nomes destas cores aqui][2].

Além de ser muito difícil de manter uma coleção de cores com seus nomes esquisitos, é quase impossível você criar um website tentando se adequar a quantidade limitada de cores disponíveis. Já tínhamos problemas sufientes com a quantidade limitada de fonts que poderíamos utilizar. Isso não poderia acontecer com as cores também. Com esse problemas vários padrões matemáticos foram estabelecidos para que criássemos as cores que gostaríamos de utilizar. Vou falar de dois padrões aqui: RGB e HSL. Vou ligá-los ao desenvolvimento web e não de uma forma geral. Caso contrário o artigo seria mais longo e envolveríamos outros assuntos mais extensos.

Você já deve ter lido algo sobre utilizar para web cores no formato RGB. Esse formato está ficando mais popular com o CSS3 por que agora podemos controlar o canal alpha, tendo uma [combinação nova chamada RGBA][3]. Há também outro formato que ganhou alguma atenção do workgroup no W3C que é o formato de cor chamado HSL. Como o RGB, o HSL também ganhou um canal de opacidade, ficando HSLA. Muitos desenvolvedores ainda tem dúvidas sobre as diferenças entre RGBA e HSLA e qual utilizar.

Tudo é muito simples de entender. RGB e HSL são dois formatos de composição de cores digitais. Você pode escolher qual dos dois utilizar, vai do seu gosto. Contudo como até hoje utilizamos o HEXADECIMAL como padrão de cores para web, minha sugestão é esperar para ver qual das duas específicações cairá no gosto do mercado para escolher um dos formatos para utilizá-la mais frenquentemente nos projetos. Entretanto os dois formatos tem flexibilidades diferentes e por isso pode ser muito difícil apenas uma delas se tornar mais popular que outra.

Abaixo vou introduzir brevemente as diferenças entre o formato HSL e RGB para que você entenda quais suas características.

### O RGB

O processo é simples: como na vida real onde você mistura cores para obter uma outra cor como resultado, você faz a mesma coisa com o RGB: você mistura as cores para obter uma outra cor como resultado. Para tanto você utilizará a soma de 3 valores: Red, Green e Blue: rgba(red, green, blue);

Veja a sintaxe abaixo para entender melhor a aplicação:

[cc lang=&#8221;css&#8221;]
  
p {
     
color: rgb(100%, 100%, 0%);
  
}
  
[/cc]

Os três valores são ligados às três principais respectivamente vermelha, verde e azul. No caso acima inseri 100% de cor para Vermelho e Verde. Como bom aluno de educação artística, você deve saber que misturando vermelho e verde a cor resultante será amarelo.

Você pode ser mais específico controlando até mesmo a fração da porcentagem, por exemplo: 

[cc lang=&#8221;css&#8221;]
  
p {
     
color: rgb(55.2%, 100%, 0%);
  
}
  
[/cc]

Assim você consegue exatamente a cor que precisa. Esse formato de porcentagem e controle de fração também é aplicado ao HSL.

O RGB pode ser configurado utilizando valores hexadecimais. A conta não é simples e você precisa ser um pouco nerd para entender. A explicação é meio longa. Sugiro que [você leia no Wikipedia][4] algo mais detalista.

### O HSL

O HSL funciona um pouco diferente. A sintaxe é como abaixo:

[cc lang=&#8221;css&#8221;]
  
p {
     
color: hsl(0, 100%, 30%);
  
}
  
[/cc]

A escolha de cores no HSL não é baseado na mistura mas sim em um esquema baseado em um cilindro. O primeiro número de valor na sintaxe é onde escolhemos a cor. Começamos no topo com vermelho, onde o valor é 0, e damos uma volta de 360 graus, retornando novamente no topo, na cor vermelha. Conforme aumentamos o valor vamos selecionando as cores. Por exemplo, se selecionarmos um valor por volta de 120 obtemos um verde. 

Veja a imagem abaixo para entender melhor:

![][5]

Embora possamos escolher qualquer cor misturando as cores com o RGB, é muito mais instintivo escolhermos uma cor específica e modificarmos sua luminosidade. Escolhemos o azul e modificamos sua luminosidade para obtermos o tom que você deseja.

Para escolhermos a luminosidade e a saturação da cor modificamos os dois outros valores, o segundo valor é a luminosidade e o terceiro valor é a saturação ou a quantidade de cinza que você colocará na cor. Modificar a saturação é como se você mudasse a quantidade de cor. Quanto menos cor, mais cinza. Se você quiser uma cor mais suja, mais apagada, você diminui este valor. Caso contrário você a mantém como 100% e utiliza a quantidade integral da cor. Normalmente esse será o padrão.

### E o hexadecimal?

O hexadecimal, queridinho dos nossos corações, sempre estará ao nosso lado. A sintaxe é muito mais curta que as outras duas específicações. Não temos todas as vantagens que as outras especificações nos dão, começando pelo canal alpha. Com a grande maioria dos programas visuais dando suporte ao formato hexadecimal ele ainda perdurará durante muito tempo ainda em nossas vidas.

 [1]: http://en.wikipedia.org/wiki/X11_color_names
 [2]: http://www.w3.org/TR/SVG/types.html#ColorKeywords
 [3]: http://tableless.com.br/css3-breve-introducao-a-rgba
 [4]: http://en.wikipedia.org/wiki/RGB_color_model
 [5]: http://tableless.com.br/uploads/2011/06/HSL_color_solid_cylinder_alpha_lowgamma.jpg "HSL_color_solid_cylinder_alpha_lowgamma"