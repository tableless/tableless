---
title: Web Notifications API
author: Diego Eis
type: post
date: 2014-07-14
excerpt: Aprenda o básico da API de Web Notifications.
url: /web-notifications-api/
dsq_thread_id: 2829785744
categories:
  - JavaScript
  - Técnicas e Práticas
tags:
  - api
  - html5
  - JavaScript
  - js
  - web notifications

---
Se você trabalha em um site de conteúdo ou em algum produto web, uma possibilidade interessante seria fazer com que o usuário recebesse uma notificação quando houvesse uma nova notícia ou, no caso de produtos, uma notificação do próprio serviço. Com a Notifications API agora é totalmente possível.

Caso você queira dar uma [olhada na documentação][1].

Outro detalhe importante: as notificações só podem ser ativadas por meio de uma interação do usuário, como clique de mouse, teclado e etc&#8230; Logo, vamos usar um botão em nosso exemplo para poder ativar as notificações.

> Notifications should only be presented when the user has indicated they are desired; without this they could create a negative experience for the user.

## Verificando suporte

A primeira coisa que nossa função precisa fazer é verificar se o browser suporta ou não notificações. Se ele não aceitar, ele fica em silêncio e pronto. No nosso exemplo ele vai logar uma mensagem no console, só para gente saber, ok?



## Pedindo permissão

Para não virar festa, é necessário que tenhamos a permissão do usuário para enviar as notificações via browser. Isso acontece também ao utilizar outras APIs, como a de Geolocation, por exemplo. A permissão terá três possíveis valores: um valor inicial de **default**, que significa que o usuário ainda não negou nem permitiu receber notificações deste domínio. O **denied** significa que o usuário negou receber e o **granted** que significa que usuário aceitou receber as notificações.

Agora é só fazer uma condição verificando estes estágios:



## Preparando a notificação

Se o usuário nos deu permissão para fazer a notificação, nosso domínio fica listado com permissão nas configurações do browser e aí poderemos enviar notificações até que o usuário bloqueie. Agora é hora de fazer a notificação. Para tanto, iremos executar pequena função quando a permissão for &#8220;granted&#8221;.

O código fica assim:
  


Criamos um novo objeto **Notification**, que recebe logo de cara um parâmetro que é o título da notificação. Depois há algumas opções que podemos preencher:

  * **body**: A mensagem da notificação.
  * **tag**: Identificador único da notificação. Uma string simples. Isso serve para não fazermos notificações duplicadas.
  * **onshow**: Evento que é disparado quando a notificação aparece.
  * **onclick**: Evento quando o usuário clica na notificação.
  * **onclose**: Quando o usuário fecha a notificação.
  * **onerror**: Quando há algum erro na notificação e ela não pode ser mostrada.

E voilá! Faça um teste aí. Aqui usei o Chrome e Safari. No meu Safari só funcionou depois que coloquei na minha pasta onde sirvo o localhost (httpdocs, public, www, sei lá o que você usa aí localmente). 

## O browser pensa assim

O Browser tem um processo definido pela especificação do W3C que é basicamente assim:

  * Se a permissão para a notificação não foi positiva, cancele qualquer pedido de notificação e retorne um evento de erro na notificação, finalizando todos os passos. É aqui que o **onerror** entra em ação. 
  * Se existir uma notificação pendente na lista ou se na lista de notificações ativas existem tags iguais a notificação que está sendo chamada, rode os [passos de substituição][2] e finalize as ações. 
  * Se um dispositivo autorizar, as notificações podem ser mostradas imediatamente sem limitações no número de notificações concorrentes, rodando os [passos de amostra][3] e finalizando as tarefas. 
  * Se o dispositivo tem limitações com o número de notificações concorrentes, chame imediatamente a plataforma alternativa que suporte enfileirar as notificações ou posicione as notificações em uma [lista de pendências][4]. 

É legal [ler a documentação do W3C][1], mesmo que boa parte das informações sobre essa API seja interessante para os fabricantes de browsers.

**Mais pra estudar:**

  * [Implementing Safari push notifications in OSX Mavericks][5]
  * [Using Web Notifications &#8211; MDN][6]
  * [Sending Notifications &#8211; Apple][7]
  * [Artigo sobre o mesmo assunto no LoopInfinito][8]

 [1]: http://www.w3.org/TR/notifications/
 [2]: http://www.w3.org/TR/notifications/#replace-steps
 [3]: http://www.w3.org/TR/notifications/#display-steps
 [4]: http://www.w3.org/TR/notifications/#list-of-pending-notifications
 [5]: https://zeropush.com/blog/implementing-safari-push-notifications-in-osx-mavericks
 [6]: https://developer.mozilla.org/en-US/docs/Web/API/Notification/Using_Web_Notifications
 [7]: https://developer.apple.com/library/safari/documentation/AppleApplications/Conceptual/SafariJSProgTopics/Articles/SendingNotifications.html#//apple_ref/doc/uid/TP40001483-CH23-SW1
 [8]: http://loopinfinito.com.br/2012/08/22/web-notifications-api/