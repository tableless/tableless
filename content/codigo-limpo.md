---
title: Código Limpo
author: Alan Cezar
type: post
date: 2015-02-11
url: /codigo-limpo/
categories:
  - Artigos
  - Código
  - Geral
  - Mercado e Comportamento
  - Técnicas e Práticas
  - Tecnologia e Tendências
tags:
  - aprender javascript
  - bonitodesever
  - cotidiano
  - desenvolvimento web
  - JavaScript
  - Na Prática
  - padroes web
  - Técnicas e Práticas

---
Um dos assuntos que costumo discutir bastante com a galera é sobre qualidade de código. Nesses papos sempre vem questões como: quais práticas podemos adotar para ter um código de alta qualidade? E como sabemos se o nosso código está bom? Como temos certeza de que estamos no caminho certo?

Vou explicar meu humilde ponto de vista com exemplos e opiniões sobre qualidade de código. Vou abordar casos de uso com JavaScript, mas nada te impede aplicar muitas dessas dicas usando outras linguagens.

## GDD &#8211; Gambiarra Driven Development

Vamos começar pela metodologia mais antiga e talvez a mais adotada no mercado. Já trabalhei com profissionais que defendiam com unhas e dentes o não uso de padrões e boas práticas. Vamos ver as <del>desculpas</del> justificativas mais usadas:

  1. O projeto é muito simples. Não precisa de muita frescura.
  2. Faço isso há muitos anos e dificilmente tenho problemas.
  3. Desse jeito entrego em 10 minutos o que faríamos em horas.
  4. Não preciso padronizar, o código tá fácil de entender.
  5. Não temos tempo para documentar.
  6. Não temos tempo para escrever testes.
  7. Não temos tempo para refatorar.
  8. Esse código aí não é meu.

Conseguiu se lembrar de alguns momentos na sua carreira, onde você já falou ou ouviu qualquer uma das frases acima? Não? Sortudo!

> Não acredito que é errado você usar uma gambiarra para resolver um erro, desde que posteriormente você empregue uma solução mais robusta. O problema maior ocorre quando o uso de soluções paliativas se tornam frequentes.

Mas de longe esse é o único ou pior problema que encontramos na codificação. Gambiarras e _anti-patterns_ podem ser bons e eficientes a curto prazo, mas a longo prazo te mostram o inferno na terra.

Vou apontar algumas boas práticas voltadas á escrita de código e o motivo para usá-las.

## Antes de tudo&#8230;

> Você como desenvolvedor, tem a obrigação de entender cada linha de código que você escreve.

Estude boas práticas e metodologias sempre. Mas não seja ingênuo a ponto de acreditar que a adoção de uma delas irá salvar parte do seu projeto/equipe. Muitas soluções podem trazer novos problemas. Quantas vezes a solução de um bug gerou outros 10 na aplicação? Por isso é necessário sempre ter na equipe alguém experiente com bastante vivência, que saiba direcionar o projeto nesses cenários.

Já vi projetos que começaram repletos de boas práticas, e terminaram desastrados por conta da falta de maturidade prática da equipe. O ponto inicial que jamais deve ser ignorado é: **você como desenvolvedor, tem a obrigação de entender cada linha de código que você escreve**.

## No caminho certo

Seu código atual tem uma qualidade superior comparado com o que você escreveu há 6 meses atrás? Se sua resposta for sim, isso indica que você está no caminho certo. Programação é algo em constante evolução, o você programador, também deve evoluir. Com o passar dos anos seu código deve se tornar mais bem organizado, limpo e elegante.

Uma leitura obrigatória é o livro <a href="http://www.saraiva.com.br/clean-code-a-handbook-of-agile-software-craftsman-3095979.html" target="_blank">Clean Code</a>. Muitos artigos e palestras sobre boas práticas (incluindo esse artigo), repetem pontos abordados nesse livro. Já vi até empresas cobrando a leitura desse livro como requisito para contratação.

## Código Limpo

Enquanto o _GDD_ pode te dar felicidade a curto prazo, escrever código de forma limpa e consistente vai te garantir um futuro mais confortável. Você terá um código de fácil entendimento, o que tornará sua manutenção mais eficiente. E se você for um garoto prendado e cobrir sua aplicação com o máximo possível de testes, erros de regressão não irão mais chatear teu cliente/chefe.

Vou focar em poucos pontos. Se quiser mais conteúdo, leia o <a href="http://www.saraiva.com.br/clean-code-a-handbook-of-agile-software-craftsman-3095979.html" target="_blank">Clean Code</a>.

### Code Review

Sempre peça para um colega revisar teu código. Se outra pessoa entendeu perfeitamente o que você escreveu, é um bom sinal.

> &#8220;Qualquer tolo consegue escrever código que um computador entenda. Bons programadores escrevem código que humanos possam entender.&#8221; &#8211; Martin Fowler

### Linters

Ferramentas que escaneiam nosso código procurando o uso de más práticas e possíveis erros de execução, são nossos aliados. No dia-a-dia costumo usar o <a href="http://jshint.com/" target="_blank">JSHint</a> e agora meu novo parceiro: <a href="https://github.com/danielstjules/jsinspect" target="_blank">JSInspect</a>.

Gosto do JSHint pelo fato de poder customizar algumas regras. Já o JSInspect te ajuda á identificar o padrão _copy & paste_, te ajudando a escrever módulos melhores.

### Nomenclaturas

Quando me perguntam qual parte da programação eu acho mais difícil, respondo na lata: nomear coisas.

Passamos boa parte do tempo fazendo isso no nosso código, nomeando funções, variáveis, classes, namespaces, etc. Muitas vezes demoramos até chegar em um resultado bacana.

### Seja verboso

> &#8220;Existem duas coisas muito difíceis na Ciência da Computação: invalidar cache e dar nome às coisas.&#8221; &#8211; Phil Karlton

Consegue me dizer se você entende de cara o que faz a instrução abaixo?

<pre>u.cptTasks = false;</pre>

E agora com o código abaixo?

<pre>var u = new User();
u.name = 'Joana Souza';
u.adminPerm = true;
u.cptTasks = false;
u.save();</pre>

Conseguiu entender tudo? Vamos ver se fica mais fácil:

<pre>var user = new User();
user.name = 'Joana Souza';
user.hasAdministratorPermissions = true;
user.didCompleteAllTasks = false;
user.save();</pre>

Nomear a variável como _u_ não ajudou muito. Principalmente se você for reutilizar essa variável muitas linhas abaixo. Abreviações também atrapalham bastante. Duvido que de imediato você soube o significado de _u.cptTasks_. Pode ter tido várias idéias, o que te guiou ao velho _achismo_. E quantos erros já não cometemos pelo simples fato de _acharmos_ isso ou aquilo?

### Considere o uso da nossa querida Língua Portuguesa

Usar a língua portuguesa para nomear coisas pode ser muito bom, principalmente para os novatos. Pelo simples motivo de que fazendo isso, fica mais visível o que é API nativa da linguagem/browser, e API proprietária. Dá uma olhada:

<pre>var usuario = new Usuario();
usuario.nome = 'Joana Souza';
usuario.temPermissoesAdministrativas = true;
usuario.completouTodasTarefas = false;
usuario.salvar();</pre>

Ficou mais confortável né? Seu cérebro praticamente se deu ao único trabalho de compreender o código. Não precisou traduzir de um idioma para outro. Mas isso é também uma faca de dois gumes.

Conhecer a língua inglesa é extremamente importante no mundo da programação, pois muitas documentações e materiais estão nesse idioma. Logo, nomear coisas em português te tira a oportunidade de praticar o idioma, pelo menos na forma escrita. Vale á pena bater um papo com a sua equipe á respeito disso.

### Adote uma convenção

A adoção de uma convenção facilita muito na padronização de estilo de escrita e organização de código. É uma ótima opção iniciar com alguma existente:

  * <a href="http://snowdream.github.io/javascript-style-guide/javascript-style-guide/br/naming-conventions.html" target="_blank">Convenção de Nomenclatura &#8211; Airbnb</a>
  * <a href="http://andrecomws.com/lab/code-standards/" target="_blank">Padrões de Código Front-End &#8211; Isobar</a> (a versão original está <a href="http://isobar-idev.github.io/code-standards/" target="_blank">aqui</a>)
  * <a href="http://javascript.crockford.com/code.html" target="_blank">Convenções do Douglas Crockford</a>
  * <a href="https://google.github.io/styleguide/javascriptguide.xml" target="_blank">Padrões de Código da Google</a>

Bônus:

  * Leitura obrigatória: <a href="http://jstherightway.org/pt-br/" target="_blank">JavaSript the Right Way</a>

### Variáveis e funções não utilizadas

Variáveis e funções não utilizadas são um belo exemplo de sujeira. Alguma vez você já deu manutenção em algum código, cujo algum tempo foi investido para compreender o que foi escrito, pra no final das contas perceber que o código estava morto, sem utilização? Chato, né?

Pra se livrar dessa sujeira é bem simples: ninguém está usando? Apague! Essa regra também vale para código comentado.

### Reinvenção da roda

Esse erro é geralmente cometido por novos e _antigos juniores_ (entendo como antigo júnior aquele profissional que programa há muitos anos, mas nunca se interessou em aprofundar em uma linguagem).

O fato de não conhecer muito bem a API da linguagem, pode te levar á reinventar á roda.

Um exemplo disso é quando precisamos fazer um filtro em um array. Quem não está familiarizado, irá primeiramente fazer o bom e velho _for_, possivelmente desconhecendo outras opções como _Array.filter_ e _Array.map_.

### Funções Pequenas

Funções devem ser claras, objetivas e pequenas. Respeite a regra da responsabilidade única: sua função deve fazer somente uma coisa, e deve fazê-la muito bem.

Dá uma olhada no exemplo abaixo:

<pre>usuario.salvar()

...

function salvar() {
    var camposObrigatorios = [ 'nome', 'email', 'cpf' ];

    camposObrigatorios.forEach( ( propriedade ) =&gt; {
        if ( !usuario[ propriedade ] ) {
            throw new Error( `É obrigatório informar o ${ propriedade } do usuário.` );
        }
    } );

    $http.post( 'http://app.com/api/usuario', usuario )
        .success( ... )
        .error( ... )
        .finally( ... );
}</pre>

Pelo nome da função ficou claro o objetivo dela. Mas analisando vemos a implementação de duas coisas: validação e persistência dos dados. Poderíamos dividir as responsabilidades da seguinte forma:

<pre>validarUsuario() && usuario.salvar();

...

function validarUsuario() {
    var camposObrigatorios = [ 'nome', 'email', 'cpf' ];

    camposObrigatorios.forEach( ( propriedade ) =&gt; {
        if ( !usuario[ propriedade ] ) {
            throw new Error( `É obrigatório informar o ${ propriedade } do usuário.` );
        }
    } );

    return true;
}

function salvar() {
    $http.post( 'http://app.com/api/usuario', usuario )
        .success( ... )
        .error( ... )
        .finally( ... );
}</pre>

Manter suas funções enxutas te auxilia á praticar o reuso do código.

Esse é um assunto que pode ser extenso. Uma discussão bem bacana rolou no StackOverflow. Dá uma olhada <a href="http://pt.stackoverflow.com/questions/30772/uma-fun%C3%A7%C3%A3o-grande-ou-muitas-pequenas" target="_blank">aqui</a>.

### 

### Comentários

Já ouvi dizer que código semântico dispensa comentários. Concordo parcialmente com isso. Acredito que é válido usar comentários nas seguintes situações:

  * Utilização muito pouco comum de uma parte da API pode ajudar a galera mais nova
  * Nem sempre conseguimos deixar nosso código semântico, a ponto dele _contar o que está acontecendo_
  * Existem poucos momentos em que devemos fazer uso de uma má prática. E é bom deixar documentado o motivo antes que alguém refatore e quebre alguma funcionalidade
  * Sua aplicação expõe uma API pública. Sugiro o uso do <a href="http://usejsdoc.org/" target="_blank">JSDocs</a> para manter um padrão.

Agora  **/\* código comentado \*/ **é algo deve ter pouquíssima tolerância.

### Indentação

Esse é conhecido como _problema de perfumaria_. Saca só:

<pre>if(usuario.idade!==null||usuario.idade!==undefined||typeof usuario.idade == 'number'||usuario.idade&lt;18){
  alert('O usuário não possui idade suficiente para ser cadastrado nesse sistema.');
  return false;
}else{
    usuario.salvar();
}</pre>

Lindo né? Que tal dar mais espaço pra essa bagunça?

<pre>if ( usuario.idade && typeof usuario.idade === 'number' && usuario.idade &lt; 18 ) {
    alert( 'O usuário não possui idade suficiente para ser cadastrado nesse sistema.' );
    return false;
}

usuario.salvar();</pre>

E agora? Ficou mais fácil de ler?

Enfiar todo o código em uma pequena lata de sardinha pode dificultar um pouco a sua compreensão, por mais que o seu editor de texto ou IDE tenha um highlight com alto contraste. Uma ferramenta bacana pra te ajudar á manter esse padrão é o <a href="http://jscs.info/" target="_blank">JSCS</a>. Gosto de usar o preset jQuery dessa ferramenta, pois o código fica com mais espaçamento, deixando o mais confortável para ler.

### Vale lembrar que&#8230;

Muitas dicas dadas aqui retirei do livro Clean Code, e outras aprendi com o passar do tempo em experiência com diversos projetos. O seu comentário com um ponto de vista diferente pode me ajudar á aprender mais sobre o assunto.

Espero ter ajudado.

=)