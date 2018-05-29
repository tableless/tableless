---
title: Formsquash, formulários para sites estáticos
authors: Jean Lucas de Carvalho
type: post
image: https://formsquash.io/static/images/cover.jpg
date: 2018-05-27
excerpt: Criando formulários para sites estáticos com o Formsquash
categories:
  - Artigos
  - Ferramentas
  - HTML
  - Tecnologia e Tendências
tags:
  - formsquash
  - html
  - websites
---

Nos últimos anos os geradores de sites estáticos ganharam muita popularidade, graças aos ganhos de performance , segurança e disponibilidade que os sites resultantes possuem quando comparados aos sites dinâmicos. E muitos sites e blogs pelo mundo utilizam de ferramentas como Hugo, Jekyll, Middleman, Wintersmith e Docpad para gerar suas páginas estáticas.

O próprio Tableless era um site dinâmico, gerenciado pelo Wordpress, e hoje é um site estático gerado pelo Hugo e você pode entender um pouco mais das motivações e vantagens e desvantagens dessa mudança nos posts do Diego Eis:

- [Agora o Tableless é estático - Artigos sobre HTML, JavaScript, CSS e desenvolvimento web](https://tableless.com.br/site-tableless-estatico/)
- [Performance do Tableless estático - Artigos sobre HTML, JavaScript, CSS e desenvolvimento web](https://tableless.com.br/velocidade-tableless-estatico/)

Porém, para resolver alguns problemas de natureza dinâmica, os geradores de sites estáticos precisam de ajuda de outras ferramentas. Quer gerenciar comentários no seu site? Existe o Disqus. Precisa de uma solução para busca? Use o DuckDuckGo Search Box. Hospedagem? Firebase Hosting.

Mas um problema que até pouco tempo continuava sem solução era o gerenciamento de formulários online. Seja um formulário de contato ou submissão de currículos, de inscrição de e-mails para newsletters ou de captura de leads para um funil de vendas. A gente sempre precisava de algum código backend (normalmente um script php) para pegar os dados submetidos no formulário e encaminhar para um e-mail predefinido.

No entanto, sites estáticos não possuem nenhum tipo de backend. Para resolver isso, é comum delegarmos esse trabalho para plataformas WYSIWYG , como o Google Forms ou o Typeform. Mas essas plataformas deixam a desejar quando precisamos manter a identidade visual dos formulários compatível com a do restante de nosso site.

Pensando nisso, o [Formsquash](https://formsquash.io/) surgiu. Com ele, tudo o que você precisa fazer é apontar seu formulário para a URL fornecida pelo serviço. Para conseguir a URL, basta fazer o cadastro e criar um formulário. A partir daí você receberá um tutorial de como integrá-lo com seu site.

Um exemplo de uso para um formulário para coletar e-mails seria:

```html
<form action="https://formsquash.io/f/id_do_form" method="POST">
  <input type="email" name="email" placeholder="Seu Email">
  <input type="submit" value="Enviar">
</form>
```

Pronto, agora você já pode receber respostas no seu formulário ;)

Não existem limitações com relação aos campos do formulário, qualquer campo recebido será tratado automaticamente e as respostas serão enviadas a você via e-mail, mas também é possível acessá-las através do Formsquash.

Além disso é possível usar o Zapier para integrar com centenas de outros serviços (como Google Sheets, Mailchimp e Intercom), abrindo muitas possibilidades para o que é possível fazer com um simples formulário. Neste artigo podemos ver como com poucas linhas conseguimos adicionar um formulário em nosso site sem precisar de código backend. 

Mais detalhes no site oficial do Formsquash: [https://formsquash.io/](https://formsquash.io/)

Se tiver alguma dúvida, só deixar aqui nos comentários :)
