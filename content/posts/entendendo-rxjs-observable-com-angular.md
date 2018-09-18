---
title: Entendendo RxJS Observable com Angular
authors: Wendel Nascimento
type: post
image: https://i.imgur.com/da746Te.png
date: 2017-09-03
excerpt: Uma forma simples de utilizar RxJS para aplicar conceitos de programação reativa com Angular
categories:
  - Javascript
  - Tecnologia e Tendências
  - AngularJS
---

Após passar por um projeto com *Angular 2* (ou somente *Angular*, para os mais íntimos) posso dizer que: É um *framework* com muitas vantagens, e uma das coisas mais fascinantes que conheci foi a biblioteca *[RxJS](https://github.com/Reactive-Extensions/RxJS)* (estude este cara e verá as maravilhas de um mundo moderno), o famoso ***Observable*** mudou minha vida.

### O que é um Observable?

Por definição é uma coleção que funciona de forma unidirecional, ou seja, ele emite notificações sempre que ocorre uma mudança em um de seus itens e a partir disso podemos executar uma ação. Digamos que ele resolve o mesmo problema que a versão anterior do *Angular* havia resolvido com o *$watch*, porém sem usar força bruta. Enquanto no *$watch* verificamos todo nosso escopo por alterações após cada *$digest cycle* (o que tem um grande custo na performance), com *Observable* esta verificação não acontece, pois para cada evento é emitida uma notificação para nosso *Observable* e então tratamos os dados.

### O que faço com Observable? E onde entra Angular nessa história?

Vamos imaginar o consumo de uma *web service*, algo bem comum em aplicação *Single Page*, antes do Observable faríamos dessa maneira

    getUsers(): Promise<User[]>{
      return fetch(myApiUrl)
      .then(res=>res.json())
      .catch(err=> Observable.throw(err.message));
    }

O código acima é bem simples, estamos buscando um recurso (Uma lista de usuários) e após a resposta transformamos tudo em *JSON.*

Entretanto, o novo Angular foi construído pensando em aplicações reativas, abandonando o uso de *Promises* e adotando por padrão o ***Observable***.

Usando Observable a mesma função ficaria da seguinte maneira:

    @Injectable()
    class UserService {
     ...
     getUsers(): Observable<User[]> {
        return this.http.get(myApiUrl)
                        .map(res=>res.json())
                        .catch(err=> Observable.throw(err.message));
     } 
     ...
    }

### Mas quais são as vantagens de usar Observable e não Promises?

A grande vantagem está nos “poderes” que o *Observable* nos dá com seus **operadores**, por exemplo: Podemos “cancelar” *requests* para poupar processamento, ou até mesmo tentar fazer uma nova requisição caso algum problema como perda de conexão aconteça.

O usuário não precisa ver aquela tela de erro.

### Operador Subscribe

Um dos operadores mais importantes do *Observable* é o *subscribe*, que é o equivalente ao *then* de uma *promise* ou ao *$watch*.

    import { UserService } from 'user.service';

    @Component({
      /* Propriedades do componente*/
    })
    class UserComponent {
      ...
      constructor(private userService: UserService){}

      private users: User[]; // Lista de usuários

      /* Neste método chamamos a função userService.getUsers, que nos retorna um Observable contendo um array de usuários, então atribuímos ao this.users */
      getUsers() {
        this.userService.getUsers()
                        .subscribe(
                          users => this.users = users,
                          error => /* Tratamos erros aqui :) */);

      }

      ...
    }

Estamos chamando a função *getUsers()* criada anteriormente e deixamos um *subscribe* ali, ou seja, assim que a nossa resposta vier e for transformada em *JSON*, seremos notificados e o *array* *users* receberá a lista de usuários, ou caso seja um erro, tratamos o erro onde deixei um comentário. Simples?

Um cenário ainda melhor seria uma aplicação que use *web sockets*, pois a cada atualização o *subscribe* iria atualizar o *array users* novamente, tudo de forma unidirecional e sem grande consumo de recursos com um *$watch* da vida.

Se ainda assim você quer muito usar *Angular* em seu projeto e não quer utilizar *Observable* em tudo, o operador *toPromise()* é perfeito para você!

### Operador Retry

Vamos supor que você está tentando fazer o download de um arquivo, mas está em uma conexão com muita oscilação (o que convenhamos que é bem comum no Brasil), é de se esperar que o download falhe.
Nestes casos podemos utilizar o operador *retry*, que é extremamente simples e funciona da seguinte forma: Se a operação falhar, será executada novamente para tentar completá-la (a quantidade de tentativas é especificada como parâmetro do *retry*). No código ficaria algo parecido com isso:

    @Injectable()
    class downloadFileService {
      ...

      downloadFile(attachment: Attachment)  {
        this.http
            .get(/* URL de download do arquivo */, { responseType:   ResponseContentType.Blob })
            .retry(3) // Aqui especificamos que a quantidade de tentativas caso o download falhe é 3.
            .map((response: any) => response.blob())
            /* Agora temos o arquivo e é só mandar para o usuário :) */
            }, (err:any) => /* Tratamos erros aqui :) */);
       }

      ...
    }

### Otimizando processo de busca com Observable

E se em nossa lista de usuários houvesse uma barra de pesquisa onde ao digitar qualquer tecla já fosse disparada a requisição para filtrar os usuários? Parece bem simples. Normalmente, no event *keyup* do campo colocaríamos uma função que filtraria a lista com base no que foi digitado, mas isso tem um problema: Para cada tecla digitada seria gerada uma nova requisição e toda a lista de usuários seria substituída.

Concordemos que substituir a lista a cada letra digitada não é o que queremos fazer. Em um mundo perfeito, a única *request* que deve ser considerada é a gerada pelo evento da última letra digitada, isto pode ser resolvido com dois métodos do *Observable*, o *switchMap* e o *debounceTime*.

### Operador switchMap

Este operador soluciona um dos problemas, mesmo mais antigas. Por exemplo: Se você pesquisou por **Paulo**, serão 5 requisições, uma para cada letra, você irá construir os objetos e substituir em seu array 5 vezes, é algo custoso.

O *switchMap* é um dos operadores que você irá usar e se orgulhar infinitamente. Se você fez 5 requisições, ele irá processar apenas a última delas, que é a que realmente importa para nós, construiremos nosso objeto uma vez e substituiremos o array somente uma vez. Seu uso é simples, assim como todos os operadores que vimos até agora.

    import { UserService } from 'user.service';

    @Component({
      /* Propriedades do componente*/
    })
    class userComponent {
      ...

      constructor(private userService: UserService){}

      private users: User[]; // Nossa lista de usuários

      /* Variável que recebe o valor da função handleFilterChange */
      private filterString:Subject<string> = new Subject<string>();

      /* Função que recebe o valor digitado e coloca em nosso Subject */
      handleFilterChange(value: string) {
        this.filterString.next(value);
      }

      /* Fazemos um switchMap em nosso Subject filterString e atribuímos o resultado à nossa lista de usuários */
      ngOnInit() {
        this.users = this.filterString
            .switchMap(value => this.userService.getUsers(value))
            .catch(error => /* Tratamos erros aqui :) */);
      }

      ...
    }

Temos um pouco mais de código, mas nada muito complexo, a lógica é simples: No evento *keyup* da barra de pesquisa a função ***handleFilterChange*** é chamada e ela adiciona o valor ao *[Subject](https://reactivex.io/documentation/subject.html)* (que em tese, é uma versão bidirecional do *Observable*), após isso, temos no *ngOnInit* a variável *users* recebendo o resultado do *switchMap*, que busca os usuários filtrando com o valor passado. Sendo assim, quando digitarmos *“Paulo”*, apenas a última requisição será processada e terá seu valor atribuído à variável *users*, pois foi a última a ser enviada.

Mas ainda assim, podemos diminuir este número para apenas uma requisição, e poupar, além de processamento, consumo de dados!

### Operador debounceTime

Para chegar a apenas uma requisição é fácil, não precisamos buscar enquanto o usuário ainda não terminou de digitar, ou seja, se queremos buscar por “Paulo”, não há motivo para buscarmos somente a letra **“P”**, depois somente as letras **“Pa”**, e assim sucessivamente até completarmos a palavra.

É aí que entra o operador ***debounceTime***, seu funcionamento não é nada complexo: Ele só executa uma ação caso tenha se passado uma certa quantidade de tempo desde a última execução desta ação.

Por exemplo: Com um ***debounceTime*** de 300 milissegundos, quando começarmos a digitar “Paulo”, começamos pela letra **“P”**, mas se logo em seguida digitarmos a próxima letra, que é **“A”**, ele não irá disparar outra requisição, pois ainda não se passaram 300 milissegundos desde a última vez em que você digitou uma letra.

Com o código que havíamos feito anteriormente ficaria assim:

    import { UserService } from 'user.service';

    @Component({
      /* Propriedades do componente*/
    })
    class userComponent {
      ...

      constructor(private userService: UserService){}

      private users: User[]; // Nossa lista de usuários

      /* Variável que recebe o valor da função handleFilterChange */
    private filterString:Subject<string> = new Subject<string>();

      /* Função que recebe o valor digitado e coloca em nosso Subject */
      handleFilterChange(value: string) {
        this.filterString.next(value);
      }

      /* Fazemos um switchMap em nosso Subject filterString e atribuímos o resultado à nossa lista de usuários, porém existe um debounceTime de 300 milissegundos para evitar fazer requisições enquanto o usuário ainda não finalizou a digitação */
      ngOnInit() {
        this.users = this.filterString
            .debounceTime(300)
            .switchMap(value => this.userService.getUsers(value))
            .catch(error => /* Tratamos erros aqui :) */);
      }

      ...
    }

Com isso temos um componente de pesquisa sensacional, e com pouquíssimas linhas de código. Tudo com o poder do *Observable*!

Estes operadores são apenas alguns entre muitos que o ***Observable*** possui. Com um pouco mais de leitura podemos aprender a utilizá-los e otimizar muito nossa aplicação, tornando-a não apenas mais rápida, mas também mais inteligente, ajudando o usuário a poupar processamento e dados (o que deve ser uma preocupação, principalmente pensando em aplicações que tendem a ser mais utilizadas em dispositivos móveis).

Quanto mais reativa é a solução que você precisa, melhor é trabalhar com *Observable*. Isso quer dizer que se você está trabalhando com uma aplicação que funcione de forma assíncrona (onde a ordem de execução não é um fator determinante para o funcionamento, com *Observable* não existem operações blocantes) ou *realtime*, as vantagens crescem muito se compararmos o trabalho que teríamos utilizando *Promises*, por exemplo. O poder que o *RxJS* nos dá para trabalhar com múltiplos eventos de forma completamente assíncrona pode nos ajudar a construir aplicações muito mais consistentes e resilientes.
