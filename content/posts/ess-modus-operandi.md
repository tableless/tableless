---
title: WordPress Modus Operandi
author: Mazetto
type: post
date: 2013-12-03
excerpt: O WordPress tem sido utilizado por diferentes tipos de usuários e para diversas finalidades; a proposta mais recente é utilizá-lo como plataforma de aplicações. No entanto, muitos de seus usuários não exploram suas capacidades. Para estimular a compreensão do WordPress e ampliar seu uso para projetos diferenciados, temos aqui um estudo diferente.
url: /wordpress-modus-operandi/
dsq_thread_id: 2004368857
categories:
  - Wordpress
tags:
  - wcsp
  - wordcamp

---
Sábado, dia 23 de Novembro, tive o prazer de participar do WordCamp São Paulo 2013. De acordo com informações divulgadas no site do evento, foram mais de 200 inscritos a procura de compartilhar e trocar idéias sobre o uso do WordPress em seus projetos. Essa edição do WordCamp contou com palestras nas áreas de design e desenvolvimento, produção de conteúdo e negócios.

Acredito que ter ampliado o alcance dos temas abordados, não restrigindo apenas a códigos e aberto espaço para discussões referente ao mercado, negócios; foi sem dúvida uma grande sacada dos organizadores que agregou imenso valor a esse encontro de profissionais.

## Uma nova visão sobre o WordPress

Assim como os organizadores do evento e a comunidade se mostraram muito interessados em debater como estão aplicando o CMS em seus trabalhos, em quais pontos poderiam melhorar, viabilizando soluções viáveis e praticáveis no mercado; eu também abracei a causa e apresentei no evento uma modo diferenciado de enxergar, entender e utilizar o WordPress.



Minha apresentação foi WordPress Developer: Uma nova profissão?, voltada para o ambiente gerencial dos trabalhos. Na palestra explanei minha definição, idéia a respeito do profissional WordPress Developer, uma grande oportunidade aos desenvolvedores; mas que abordarei em mais detalhes num próximo artigo, nesse vou focar na maneira de trabalhar com o sistema. O objetivo principal aqui é colocar em pauta diferentes abordagens a fim de estimular a criação de projetos diferenciados e dar continuidade a evolução técnica e profissional desse mercado.

## Mercado no cenário atual

Pensando em identificar o modelo de trabalho e os usuários do WordPress fiz uma análise sobre os dados apresentados por Matt Mullenweg, um dos criadores do WordPress, durante sua apresentação na edição de São Francisco do WordCamp; na ocasião ele revelou que de todos os sites da web 18,9% rodam em WordPress, um aumento de 2,2% nesse último ano.

Independente dos motivos, seja possuir uma curva de aprendizado pequena, por ser de fácil manipulação ou quaisquer outras vantagens que cada usuário do WordPress pode salientar; o fato é que o número de adeptos a ferramenta segue em expansão. Junto a isso, em eventos como esse em que estive presente, é possível verificar também que pessoas de diferentes formações e ofícios vêm utilizando o WordPress em seus trabalhos com diferentes propósitos.

Nessa mesma apresentação, Matt apresentou o resultado de uma pesquisa com mais de 30 mil entrevistados de 178 países diferentes onde foi detectado o modo como esses usuários estão usando o WordPress:

  * 6% apenas para blogs
  * 7% como uma plataforma de aplicações
  * 20% para blogs e gerenciamento de conteúdo diverso
  * 69% apenas como gerencidor de informações

Podemos verificar que assim como a ferramenta está em constante aprimoramento, recebendo versões novas em curtos intervalos de tempo, com novos recursos; seus usuários estão sabendo cada vez mais tirar proveito disso. O uso do WordPress como CMS já havia sido emplacado há algum tempo, mas o significativo número de utilizadores que tratam o sistema como plataforma de aplicações mostra o quanto eles estão se especializando e como ainda existe muito território a ser desbravado dentro desse recente conceito.

## Funcionamento do sistema

Imagino que a dificuldade de utilizar o WordPress em projetos diversos ocorre muito em razão da falta de uma visão geral de seu funcionamento. Minha proposta para compreensão do sistema é uma visão ampla dos recursos, de como eles operam e com qual finalidade. Acredito bastante nesse conceito pois a partir dele fica muito mais fácil visualizar o alcance do WordPress e o método que utilizaremos para integrar nossos projetos a ele. Veja abaixo o gráfico com o esquema proposto:

[<img class="alignnone size-full wp-image-39737" alt="WP Modus Operandi" src="http://tableless.com.br/uploads/2013/11/wp-modus-operandi.png" width="600" height="753" srcset="uploads/2013/11/wp-modus-operandi.png 600w, uploads/2013/11/wp-modus-operandi-133x168.png 133w, uploads/2013/11/wp-modus-operandi-247x310.png 247w" sizes="(max-width: 600px) 100vw, 600px" />][1]

Inicialmente temos que pensar no WordPress em seu princípio essencial: gerenciar conteúdo. Partindo dessa premissa básica temos duas vertentes, dois elementos que compõem e dão sentido ao sistema existir: o conteúdo em si e os usuários, os profissionais responsáveis por interagir com tal informação.

Dentro do painel administrativo os usuários são gerenciados através de diferentes níveis de permissões e acesso a determinados recursos. A extensão desse controle pode ser feita através de meta dados.

Por outro lado o conteúdo subdivide-se em três tipos de informações: publicações, termos e comentários. As publicações são responsáveis por todo material gerenciado; textos, arquivos multimídia, anexos diversos e o que mais você quiser gerenciar. Para catalogar esse material e organizá-lo adequadamente são utilizados os termos. Por fim, mas não menos importante, os comentários servem para facilitar a interação entre os visitantes, eventuais clientes e os responsáveis pelo site, fornecedores.

Procure não se ater ao nome &#8216;Comentários&#8217;, assim como as publicações, o uso dessa interação pode ser expandido para outro significado, algo que se adeque a proposta de seu negócio; como reviews por exemplo. O termo foi utilizado para manter a relação com a base de dados, talvez &#8216;Interações&#8217; ou algo do gênero seria o melhor a ser adotado.

Do mesmo modo que os usuários tem o gerenciamento expandido pelos meta dados o mesmo ocorre com as publicações e os comentários. Os termos não acompanham esse recurso por padrão, mas acredito que em breve isso deva ocorrer; existe uma discussão na equipe de desenvolvimento justamente sobre aprimorar tal estrutura de dados.

## Conteúdo em atividade

Definida a base do nosso sistema e como os dados são classificados, agora resta saber como os usuários interferem nesses dados. A comunicação entre as partes foi classificada em 3 grupos distintos com base no tipo de ação a ser feita:

  * **Configurações:** Nessa área o usuário administrador do site realiza ajustes no WordPress e em seu funcionamento;
  * **Ferramentas:** São os meios pelos quais o usuário desenvolvedor controla a informação e modifica o comportamento do sistema, sendo elas Temas, Plugins e ferramentas de manipulação dos dados como a importação e exportação do conteúdo;
  * **Personalizações:** Áreas do painel administrativo onde o usuário gestor de conteúdo (profissional de SEO, marketing e áreas de informação) consegue realizar mudanças nas Ferramentas (item acima) sem utilizar códigos, tudo feito através de um ambiente visual de fácil manipulação; como exemplo temos os Menus e os Widgets.

Perceba como o fluxo de trabalho fica mais claro desse modo: os dois agentes que movem o sistema (conteúdo e usuário), como cada um deles são tratados e conhecemos os modelos de comunicação entre as partes. A partir desse esquema a expansão não tem limites, surgem agora novas perguntas do tipo: em qual parte (agentes, tratamento ou comunicação) do sistema pretendo aperfeiçoá-lo? De que maneira posso inovar dentro dessa estrutura? E o que mais for conveniente. Ingressamos de vez na época das aplicações sustentadas pelo WordPress.

## Levando a prática

Um ponto muito interessante do evento foi ver que os profissionais estão empenhados em fazer mais, em fazer diferente e contribuir para amadurecimento/fortalecimento do mercado. Muitos já estão se especializando cada vez mais, aprofundando os conhecimentos em front-end, buscando melhorias e seguranças de desenvolvimento no back-end, aplicando técnicas de otimização, de aumento de conversão; e o resultado desse esforço sem dúvida vem somar para todos, principalmente para o cliente que recebe uma solução melhor para seus problemas.

Como abordei no início do artigo, a idéia central desse estudo é tirar da mente a idéia engessada de posts, páginas, comentários e afins; assumir de vez os tipos personalizados de posts, taxonomias e ir além, nos permitir criar algo inovador com os recursos da ferramenta. Conto com você para seguirmos com esse debate, o que você achou disso tudo? Concorda? Caso possua uma visão diferente, compartilhe também. ; )

 [1]: http://tableless.com.br/uploads/2013/11/wp-modus-operandi.png