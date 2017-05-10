---
title: WordPress e seus utilizadores
author: Mazetto
type: post
date: 2013-11-14
excerpt: Quem são os envolvidos no contexto de criação de projetos baseados em WordPress? Como diferentes profissões podem usar e tirar proveito do CMS?
url: /wordpress-e-seus-utilizadores/
dsq_thread_id: 1929518585
categories:
  - Wordpress
tags:
  - Wordpress

---
O WordPress sem dúvidas é uma excelente alternativa caso precise de um sistema para gerenciar o conteúdo de um site. No entanto entre os mais diversos envolvidos no processo de criação de um site reside algumas questões a serem respondidas. Como um designer deve encarar um projeto para WordPress, o quê um front-end precisa saber, qual o papel do gestor de conteúdo diante disso tudo; são apenas algumas indagações entre outras que serão abertas para discussão a seguir.

## Todos os utilizadores

Não importa se você é um designer, desenvolvedor front ou back-end, gestor de conteúdo ou possui qualquer outra função/profissão que venha a trabalhar com o WordPress; para saber tirar melhor proveito dos recursos que o sistema lhe proverá, você deve utilizá-lo. Muito. Tenha uma instalação local em sua máquina e divirta-se. Conheça todas os recursos que o CMS traz por padrão, entenda seu funcionamento por completo.

> Para saber aproveitar da melhor forma os recursos que o sistema oferece, você deve utilizá-lo. Muito.

Gerencie o conteúdo em todas as suas variações de status, trabalhe com os posts e seus diferentes Formatos, utilize as páginas e seus Modelos, envie Arquivos de Mídia, pratique a moderação de Comentários, configure seu ambiente, tente migrar o conteúdo e não se esqueça de trabalhar com vários usuários de permissões distintas.

Feito isso pesquise os plugins disponíveis, comece pelos mais populares e em seguida vá em direção a soluções mais específicas que você acredita precisar. A idéia é conhecer suas possibilidades, identificar recursos em potencial e claro, se familiarizar cada vez mais com o WordPress.

Encontre também diferentes Temas que servirão para quebrar algumas barreiras sobre quais tipos de sites podem ser suportados pela estrutura do CMS. Através de uma busca rápida você terá acesso a Temas que vão desde o modelo mais básico de blog até eficientes sistemas de e-commerce.

Não se apresse nessa etapa de reconhecimento, principalmente caso nunca tenha utilizado o WordPress, você certamente ganhará tempo fazendo essas atividades citadas. Somente após estar seguro de todo o modus operandi, você parte para sua área de especialização.

## Análise de sistemas

A primeira pergunta a ser respondida: Devo usar WordPress para esse projeto? A resposta pode ser um ligeiro Sim para todos os projetos de sua empresa, porém não descarte outras possibilidades. Um projeto de uma única ou de poucas telas e um e-commerce são alguns casos que podem requerer uma reflexão um pouco mais atenciosa. Certamente que em ambos os exemplos o WordPress se encaixa e pode sim ser utilizado, porém pode não ser a melhor escolha. Cabe a você avaliar se a estrutura se manterá estática, se a quantidade de mudanças a serem feitas no sistema compensa em relação ao desenvolvimento de uma solução personalizada, o custo do projeto e outros fatores que você saberá avaliar.

Escolhido o WordPress como base para o job é preciso planejar qual será o comportamento e a relação entre funções, recursos do site com o sistema. Você estará pensando no desenvolvimento de um Tema ou de um Plugin. Para essa integração, defina qual informação será Post, Página, se precisará registrar Custom Post Types, quais são as categorias, tags, taxonomias adicionais; enfim todo o conteúdo.

Estipule quais itens tornar gerenciável como quantidade de resultados por página, e-mail que receberá a notificação por ações ocorridas dentro do site, meta tags, integração com redes socias e todo tipo de informação que não se enquadra na estrutura de conteúdo, mas que também precisa ser facilmente modificada.

## Web Design

Por ser fundamentalmente baseado em questões de desenvolvimento e conteúdo, algumas vezes questões de Layout se confundem; por isso um adendo muito importante cabe aos Web Designers: criar uma arte para um site com WordPress é o mesmo que criar uma arte para um site sem WordPress. Não estabeleça limites na criação pelo fato de usar o WordPress como gerenciador do conteúdo. As limitações serão impostas pelos padrões web, compatibilidade entre os navegadores; mas não pelo sistema.

> Criar uma arte para um site com WordPress é o mesmo que criar uma arte para um site sem WordPress, o sistema não impõe limites a criação e nem pretende estabelecer um padrão de design aos projetos que suporta.

Importante ressaltar esse ponto para deixar claro que não é preciso fazer um site padronizado, uma estrutura de blogs ou qualquer outro modelo mais engessado; sinta-se livre e deixe fluir seus dotes artísticos ;D

## Front-end

Como codificar um layout para WordPress se nem mesmo colocar a mão em uma linha sequer do PHP? Conheça as estruturas HTML e respectivas classes padrões do sistema. Para os recursos inerentes a ferramenta, como os Widgets; a marcação HTML e as classes das tags são geradas automaticamente. Não perca tempo de desenvolvimento diante de formulário de busca, menus de nevagação, comentários, calendário de publicações e paginação de resultados; por exemplo. Caso tenha sido definido que tais elementos serão recuperados do próprio sistema, preocupe-se em conhecer a estrutura das respostas e desenvolver apenas os ajustes necessários para o job em questão.

Da mesma forma o conteúdo também recebe classes específicas. Com o simples uso de algumas funções pelo back-end, você terá uma lista de classes a empregar para as telas de Pesquisa, Home, Arquivo, Post, Páginas, Arquivos anexos e todas as variações de conteúdo acessáveis no site. Porém, mesmo com a possibilidade de utilizar essas classes, não hesite em aplicar suas próprias nomenclaturas; assim como é possível ao back-end exibir classes genéricas, ele pode também não intereferir nessa questão.

> Classes específicas para diferentes situações e recursos variados podem ser gerados de modo automático pelo WordPress, aproveite a estrutura fornecida quando viável.

Um outro ponto a ser considerado são os recursos JavaScript que o WordPress traz consigo, veja a lista de alguns desses recursos no [Codex][1]. Verifique se algum componente previsto de ser utilizado existe dentro do próprio sistema, certifique-se de sua possibilidade de personalização (se necessário) e cuidado com a compatibilidade de versões; caso não utilize a versão que está contida no CMS deixe isso bem claro para evitar problemas futuros.

## Back-end

Nessa etapa são desenvolvidos códigos PHP para integrar de fato o site com o WordPress. Aprofunde seus estudos e tenha como fonte principal de informações o próprio código-fonte do sistema, ele dirá muito a você. Para conseguir exemplos práticos do uso de classes e funções, consulte a [documentação oficial][2].

Alguns pontos muito importantes para qualquer tipo de trabalho de programação com o WordPress, seja criação de um Tema ou Plugin:

  * Conhecer sua base de dados, o modelo como a informação é armazenada;
  * Saber como recuperar e iterferir nesses dados como sugere o CMS;
  * Entender o funcionamento da Hierarquia de templates;
  * Dominar a Plugin API e o funcionamento dos Hooks.

Obviamente que é preciso adotar algumas regras, tais como os comentários que definem a identificação de um Tema, Plugin ou Modelo de página; mas de modo geral o WordPress oferece total liberdade (e muitos recursos) para você desenvolver qualquer aplicação dentro dele a partir de suas idéias e códigos personalizados.

## Profissional de conteúdo

Você está mais interessado em utilizar o WordPress e através dele conseguir o que se espera; ter o conteúdo publicado, divulgar uma campanha publicitária, alimentar uma base de prospects, tratar do conteúdo do site de um modo mais amplo. Pois bem, caso tenha feito uso intensivo do CMS como abordado anteriormente para todos os profissionais; você já deve conseguir se virar bem por conta própria em grande parte das situações.

Caso exista alguma demanda não atendida e você tenha a seu dispor terceiros para desenvolver alguma solução; você saberá o quê solicitar, se é possível e/ou viável para a questão. Pode ainda ser atendido por algum plugin específico, e aqueles que trabalham com SEO on-page no WordPress sabem o que eu quero dizer (rs).

## Otimização dos resultados

Perceba que a idéia é otimizar cada tipo de serviço diante das caracteristícas apresentadas pelo WordPress. Definido o uso do CMS, o melhor é manter uma comunicação baseada em suas diretrizes e bem alinhada com todos os envolvidos; sendo de suma importância conhecer o sistema e suas possibilidades, de modo a proporcionar melhores experiências para cada membro da equipe.

 [1]: http://codex.wordpress.org/Function_Reference/wp_enqueue_script#Default_Scripts_Included_and_Registered_by_WordPress%20
 [2]: http://codex.wordpress.org/