---
title: Desenvolvendo para IE6
author: Diego Eis
type: post
date: 2010-12-06
excerpt: Você ainda desenvolve para IE6? Você cobra mais por isso? Eu sim.
url: /dev-ie6/
tweetbackscheck:
  - 1356397670
shorturls:
  - 'a:3:{s:9:"permalink";s:31:"http://tableless.com.br/dev-ie6";s:7:"tinyurl";s:26:"http://tinyurl.com/3e8fddb";s:4:"isgd";s:19:"http://is.gd/b0rIpe";}'
twittercomments:
  - 'a:0:{}'
dsq_thread_id: 503039805
categories:
  - Browsers
  - Código
  - CSS
  - HTML
  - Tecnologia e Tendências
tags:
  - 2010
  - acessibilidade
  - Browsers
  - cotidiano
  - desenvolvimento web
  - ie
  - internet explorer
  - mercado

---
Você ainda faz sites para IE6? Já me fizeram uma pergunta dessas certa vez. A resposta: Sim. Mas&#8230;
  
Desenvolver para Internet Explorer 6 já foi uma obrigação. Enquanto ele era o browser mais utilizado e ainda era o browser mais atual da série, nós tínhamos que desenvolver para ele. Não havia escolha. O cenário atual é outro.

Eu não desenvolvo sites para o Internet Explorer 6 se o cliente não pedir. Nas propostas e nas reuniões costumo deixar bem claro que o IE6 está fora da cartilha de browsers compatíveis. Nesse momento é bom conversar com o cliente para entender o mercado dele. Caso ele precise que o Internet Explorer 6 seja previsto, eu aviso duas coisas: 1. O valor da proposta vai aumentar. 2. O tempo de desenvolvimento também.
  
Claro que os motivos para estas decisões precisam ser explicados. Não vou aumentar o valor da proposta simplesmente porque sou contra o IE6. Mas porque eu terei mais trabalho pela frente.

**É muito trabalho, para pouco retorno**
  
Eu não preciso dizer para você que o Internet Explorer 6 é complicado. Você já sabe. Mas o seu cliente não deve saber.
  
Para que o IE6 passe no teste de satisfação, temos que seguir alguns longos passos:

1.    Previsão de bugs de compatibilidade de CSS e HTML.
  
2.    Previsão de CSS escrito exclusivamente para o IE6.
  
3.    Bateria de testes e pente fino de Design em comparação ao layout original e outros browsers.
  
4.    Manutenção exclusiva
  
5.    Muito código e limitações de tecnologia

**Previsão de bugs de compatibilidade de CSS e HTML.**
  
Não preciso dizer que o IE6 é uma colcha de retalhos. Há dezenas de bugs conhecidos  relacionados ao desenvolvimento com CSS e HTML. Todos estes bugs precisam ser previstos e solucionados.
  
Muitos desenvolvedores já tem conhecimento destes bugs já preparam o código para que eles sejam previamente solucionados e não haja surpresas posteriores. Infelizmente isso nos leva para o próximo tópico.

**Previsão de CSS escrito exclusivamente para o IE6.**
  
Não é nada inteligente escrever código CSS cheio de Hacks. Você acaba misturando código errado com código correto. Sem contar que que usuários de browsers atuais não precisam baixar um código com hacks para solucionar problemas de um browser descontinuado. Por isso, uma solução interessante é criar um arquivo CSS apenas para o Internet Explorer 6. Entenda que nesse arquivo não haverá todo o código do site, apenas o código que servirá para curar os bugs de layout exclusivos do IE6.
  
Atualmente essa solução é a mais interessante porque o IE6 está prestes a sumir. Quando isso acontecer, basta você retirar a linha que linka esse código e pronto, seu site não suporta mais IE6.

**Bateria de testes e pente fino de Design**
  
Invarialmente você precisará gastar um tempo para fazer uma bateria de testes em todo o layout para se certificar de que nada está fora do lugar.
  
É regra haver diferenças gritantes de alinhamento, medidas e distâncias no layout do Internet Explorer 6  em relação ao layout original e aos outros browsers.

**Manutenção exclusiva**
  
Prepare-se para ter alguém cuidando exclusivamente do Internet Explorer 6 durante tempo indeterminado.
  
Com os browsers atuais, é normal fazermos implementarmos um layout e o resultado ser homogêneo durante as versões posteriores dos browsers. Se você precisar fazer alguma alteração brusca no layout, prepare-se para a manutenção no IE6.

**Muito código e limitações de tecnologia**
  
Um exemplo clássico é o suporte ao PNG. Havia um trabalho terrível para replicar sombras e determinados tipos de gradiente por conta do efeito alpha que os designers aplicavam nas imagens. O desenvolvedor client-side precisava fazer tantos slices de imagens quanto nos tempos do desenvolvimento com tabelas. A ideia de que o design deveria trabalhar para o conteúdo era totalmente esquecida. O design deveria ser seguido ao pé da letra, mesmo que isso prejudicasse a informação.
  
Ainda com o exemplo do PNG. Se quisermos que o PNG funcione no IE6, é necessário a utilização de alguns códigos extras de Javascript. O resultado não é 100%, há um consumo desnecessário de banda e também o browser consome processamento de máquina do usuário. Escrevemos muito código para ter por resultado.

Os exemplos acima são decisivos para o desenvolvimento. Isso precisa ser explicado se seu cliente faz questão do IE6. Contudo, há clientes que precisam dessa compatibilidade por obrigação, por conta de um legado que não é simples de resolver. Aí não tem jeito. Você vai ter mais trabalho e o cliente vai gastar mais. Ninguém fica feliz.

O processo de evangelização é feito nas trincheiras. Então, mãos à obra!