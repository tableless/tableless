---
title: Cobertura Campus Party Brasil 2014 – Parte 2
author: Talita Pagani
type: post
date: 2014-02-04
excerpt: Continuando com a cobertura da Campus Party Brasil 2014 (CPBr7), trago os destaques do segundo dia de palestras (29/01)
url: /cobertura-campus-party-brasil-2014-parte-2/
dsq_thread_id: 2219938246
categories:
  - Eventos e Workshops
tags:
  - campus party
  - Firefox OS
  - jogos
  - ux

---
Continuando com a [cobertura][1] da [Campus Party Brasil 2014 (CPBr7)][2], trago os destaques do segundo dia de palestras (29/01). A experiência com a Campus Party é algo tão imersivo que sequer havia conseguido realizar a cobertura dos dias restantes, mas vamos lá!

## A nova geração de smartphones com Firefox OS

André Garzia, da Comunidade Mozilla Brasil, apresentou as vantagens e os primeiros passos para construir aplicativos para o Firefox OS, o sistema operacional da Mozilla para dispositivos móveis (por enquanto, apenas para smartphones) desenvolvido com tecnologias web.

O primeiro colocado foi que já comentei no [post anterior][1] com a palestra “_The Web is dead. Long live the Web_”: a Apple é uma das maiores fabricantes de smartphones e controla totalmente a plataforma, tendo uma rígida política de controle. Ela decide quais aplicativos podem ou não entrar na App Store, por parâmetros de utilidade estabelecidos por eles. Apesar de o Android ser uma plataforma mais aberta neste sentido, faltam informações sobre o versionamento da plataforma e algumas versões não disponibilizam o código aberto, dificultando até o suporte dos desenvolvedores aos seus aplicativos desenvolvidos.

Já com o Firefox OS (FFOS), temos o pensamento _open-source_ desde o começo. Ele permite ao desenvolvedor distribuir os seus programas facilmente e trouxe a liberdade da web para um sistema operacional mobile, uma vez que é construído com JS, inclusive para controlar hardware, tendo como suporte o uso do kernel do Linux. Além disso, todo o código está no Github desde o começo, demonstrando a transparência.

Os aplicativos desenvolvidos para FFOS possuem três possibilidades de níveis de acesso:

  * **Apps hospedados:** são os aplicativos normais e com menos exigências para publicações no _marketplace_;
  * **Apps privilegiados:** aplicativos que possuem acessos a mais APIs, porém, devem ser empacotados;
  * **Apps certificados:** aplicativos que possuem acesso total ao hardware e são desenvolvidos exclusivamente por engenheiros da Mozilla. Algumas APIs privilegiadas que estes aplicativos podem acessar envolvem a API do discador, a BrowserAPI, a TCP Sockets API e a Device Storage API.

André também comentou sobre o manifesto da App, que é um arquivo semelhante a um JSON contendo o nome do app, a descrição, o arquivo que é carregado no _launch_, ícones, informações do desenvolvedor e permissões. Ele também mostrou como é possível utilizar poucas linhas de código é possível realizar funções que seriam mais complexas em outros ambientes, como pegar uma imagem do telefone. Isto é possível com o _web activity_, que delega uma função para outro aplicativo.

Para simular o uso do FFOS, há um simulador como complemento para o Firefox. Esta é mais uma vantagem: para desenvolver apps para FFOS, tudo o que o desenvolvedor precisa é de um bom editor de textos e do simulador.

Por fim, como monetizar estes aplicativos? Primeiro, não é preciso utilizar o Marketplace e você pode optar por ter um aplicativo pago ou gratuito. Além disso, você pode colocar itens a serem comprados dentro do seu aplicativo.

Outra vantagem é que os apps funcionam no Android via Firefox for Android e também no desktop via Firefox Aurora.

[Assista ao vídeo][3] da palestra.

## Desenvolvimento de jogos com Construct2

Fernando Chamis apresentou um workshop introdutório sobre como utilizar o [Construct2][4], uma IDE para a criação de jogos em HTML5. O Construct possibilita facilmente a criação de _sprites_ e o desenvolvimento dos componentes do jogo em camadas (_layers_).

A interface do Construct é similar a de IDEs de desenvolvimento de software como o Visual Studio ou o Eclipse. Você pode visualizar em alguns painéis os diretórios do seu projeto para os componentes do jogo, as camadas de objetos e, geralmente à esquerda, o painel de propriedades do elemento selecionado, onde você pode alterar atributos e configurações, inclusive do jogo como um todo (tamanho do palco, etc).

Quanto à programação e configuração, os jogos são compostos basicamente de _Layouts_ e _Event Sheets_. O layout é interessante para inserir o layout padrão de um _level_ ou da tela inicial, por exemplo. E a _Event Sheet_ é onde contém os comportamentos dos personagens, NPCs e demais partes do jogo.

O interessante da ferramenta é possibilitar integração com times multidisciplinares, uma das coisas mais complexas. Para empresas que ainda estão em fase de migração do Flash para o HTML5, é uma boa a utilização do Construct.

## Lean UX

O Horácio Soares, especialista em acessibilidade digital e que dispensa maiores apresentações, trouxe o conceito de Lean UX, que traz o conceito do Lean (metodologia de processos enxutos) e do Agile (Métodos Ágeis) para trazer uma ênfase maior em entregar e na experiência real que está sendo projetada.

Mas antes de falar disso, Horácio falou dos diversos problemas de usabilidade e acessibilidade que encontramos e que (ainda) cometemos ao projetar a experiência do usuário: _captcha_, menus _dropdowns_, o famoso uso do “clique aqui”, entre outros. O que nos faz pensar: como estamos fazendo UX no momento? Como estamos testando e validando nossas interfaces? Será que estamos mais preocupados em gerar um imenso inventário de documentações e estamos nos perdendo no processo de projetar a experiência de uso?

Horácio ainda pontuou algo com o qual sempre concordei: devemos tomar cuidado com as tendências de desenvolvimento de interfaces: _parallax_, _one single page_, modal e, um dos mais frustrantes, _carousel_ automático. As tendências sempre devem ser utilizadas com cautela, pois podem não se aplicar a determinados públicos e o pior, elas podem estar incorretas e propagando alguma prática ruim. Na ânsia de projetarmos uma boa interface seguindo o modelo mental esperado do usuário, utilizamos padrões que nem sempre se aplicam.

É importante, dessa forma, testar e validar com os seus usuários e partes interessadas, mas, tendo a vista a complexidade dos processos de UX, acabamos nos concentrando mais em documentos e artefatos do que em testes e validações, pois o tempo fica escasso.

É nesse ponto que a Lean UX entra em ação, pois propõe um alinhamento entre a área de negócios e o UX designer: um dos primeiros passos é **observar** as necessidades dos usuários e analisar os objetivos da empresa, ou seja, levar em conta o ponto de vista de todas as partes interessadas. Observar as necessidades dos usuários significa ir a campo ao invés de analisar por dados, pois nem sempre o que as pessoas dizem é o que elas fazem. A Lean UX é um caminho para o equilíbrio que fornece uma modelagem participativa e colaborativa.

> “Muitas empresas falam que trabalham com UX, mas não testam com pessoas”, Horácio Soares.

O Lean UX também enxuga alguns processos e propõem menos ênfase em entregas/documentações e mais ênfase em projetar a experiência real. Não significa abrir mão de ter documentações, mas sim gerar artefatos de valor, úteis e, além disso, quebrar paradigmas ao trazer também o desenvolvedor para auxiliar a conceber a interface, algo que também apoio e concordo plenamente com o Horácio.

> Na Lean UX, qualquer validação é útil.

[slideshare id=30606324&doc=lean-ux-campusparty-140129224846-phpapp01]

[Assista ao vídeo][5] da palestra.

 [1]: http://tableless.com.br/campus-party-brasil-2014-primeiro-dia/
 [2]: http://www.campus-party.com.br/2014/index.html
 [3]: https://www.youtube.com/watch?v=X4-RsX9Dvnc
 [4]: https://www.scirra.com/construct2
 [5]: https://www.youtube.com/watch?v=mNeV9gLwFL8