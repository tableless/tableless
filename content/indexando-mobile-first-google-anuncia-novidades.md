---
title: Indexando mobile-first – Google anuncia novidades
author: Rodrigo Fávaro
type: post
date: 2016-11-30
url: /indexando-mobile-first-google-anuncia-novidades/
categories:
  - Design
  - Mobile
  - Semântica
  - SEO
  - UX
tags:
  - google
  - mobile first

---
Segundo o <a href="https://webmasters.googleblog.com/2016/11/mobile-first-indexing.html" target="_blank">Google</a>, atualmente a maioria das pessoas já fazem busca utilizando um dispositivo móvel. Entretanto, os sistemas de classificação ainda costumam olhar a versão _desktop_ do conteúdo da página em questão para dar relevância ao usuário. Pensando em _mobile-first_, isso pode trazer alguns problemas caso a página _mobile_ tenha menos conteúdo do que a página _desktop_ porque os algoritmos do Google não estão avaliando a página que está sendo vista pelo usuário da página _mobile._

Para fazer com que os resultados sejam melhores, o Google está realizando experimentos para dar mais atenção à indexação de conteúdo _mobile-first_. Embora o índice de pesquisa do Google continue a ser único para sites e aplicativos, os algoritmos acabarão por usar principalmente a versão móvel do conteúdo de um site para classificar as páginas deste site, para entender os [dados estruturados][1], e para mostrar trechos dessas páginas nos resultados da pesquisa. Eles deixam claro que, enquanto este novo índice seja construído para páginas móveis, vão continuar a construir uma boa experiência de pesquisa para todos os usuários, sejam eles provenientes de dispositivos móveis ou _desktop_.

Como essa mudança de indexação é algo muito importante, o Google vai iniciar um processo de experimentação ao longo dos próximos meses, numa escala pequena até que estejam confiantes o suficiente e liberar essas mudanças a todos os usuários.

Embora estejam apenas começando tal mudança, eles já dão algumas recomendações para ajudar os desenvolvedores a preparar seus sites para o _mobile-first_:

  * Se você tem um <a href="https://developers.google.com/webmasters/mobile-sites/mobile-seo/responsive-design" target="_blank">site responsivo</a> ou um <a href="https://developers.google.com/webmasters/mobile-sites/mobile-seo/dynamic-serving" target="_blank">site de exibição dinâmica</a> e o conteúdo seja equivalente nos dispositivos móveis e no _desktop_, você **não precisa mudar nada**;
  * Se você tem alguma <a href="https://developers.google.com/webmasters/mobile-sites/mobile-seo/" target="_blank">configuração no seu site</a> onde o conteúdo principal é diferente no _mobile _e no _desktop_, você precisará então considerar os seguintes pontos: 
      * Certifique-se de utilizar marcação estruturada tanto para a versão _mobile _tanto quanto para a versão _desktop_;
      * Verificar a equivalência da sua marcação estruturada no _mobile _e _desktop_ digitando a URL de ambas as versões na <a href="https://search.google.com/structured-data/testing-tool" target="_blank">Ferramenta de Teste de Dados Estruturados</a> e comparando os resultados;
      * Ao adicionar dados estruturados para um site _mobile_, evite a edição de grandes quantidades de marcação que não seja relevante para o conteúdo desta página;
      * Use a <a href="https://support.google.com/webmasters/answer/6062598" target="_blank">Ferramenta de Teste de robots.txt</a> para verificar se a versão móvel é acessível ao Googlebot;
      * Os sites não precisam fazer mudanças nos [_canonical links_][2]. O Google vai continuar a usar esses links como guias para os resultados no _desktop _e no _mobile_;
  * Se você tem um site cuja versão desktop foi a única verificada no Search Console, lembre-se de <a href="https://support.google.com/webmasters/answer/35179" target="_blank">adicionar sua versão mobile</a>;
  * Se você tem somente uma versão _desktop_ do seu site, o Google vai continuar a indexa-lo normalmente, mesmo utilizando um agente _mobile_ para ver seu site.
  * Se você está construindo uma versão _mobile_ do seu site, tenha em mente que um site para _desktop_ completo é melhor do que um site _mobile _incompleto.

Gostaria de salientar a importância em focar no _mobile_ de agora em diante. Cada vez mais utilizamos o _smartphone_ no lugar do computador para acessar informações e precisamos que essas informações sejam relevantes e carreguem rapidamente, e claro, o Google entendeu isso e está trabalhando para melhorar cada vez mais a experiência _mobile_ de seus usuários.

Esse material foi extraído do <a href="https://webmasters.googleblog.com/2016/11/mobile-first-indexing.html" target="_blank">blog Webmasters do Google</a>, onde você poderá discutir com outros usuários e também encontrará os links para os fóruns para _webmasters_.

 [1]: http://rodrigofavaro.com/2016/07/04/introduzindo-rich-cards-um-novo-formato-de-resultados-para-buscas/
 [2]: https://developers.google.com/webmasters/mobile-sites/mobile-seo/separate-urls