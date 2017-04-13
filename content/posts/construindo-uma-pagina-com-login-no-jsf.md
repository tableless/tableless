---
title: Construindo uma página com login no JSF
author: Julio Cezar Dourado
type: post
date: 2016-09-06
excerpt: 'Vamos criar passo-a-passo um login utilizando o framework de Java - JSF. Conheceremos, também, as sessões do JSF e como interceptá-las.'
url: /construindo-uma-pagina-com-login-no-jsf/
titulo_personalizado:
  - 'Criando uma página de login com <strong>JSF</strong>.'
categories:
  - Back-end
  - Código
  - Destaques
  - Java
tags:
  - java
  - java web
  - JSF
  - login-jsf
  - sessoes jsf

---
Neste post vou falar sobre um assunto um pouco trivial e que qualquer iniciante no framework **JSF** pode se perder: **As fases do JSF e onde interceptar a navegação para que o usuário realize a autenticação**.

É importante que você saiba o que é JSF e como configurá-lo em seu editor, aqui estarei utilizando o Eclipse, caso não saiba como configurar em seu editor, ao final, deixarei alguns links para lhe ajudar.

Vamos la =) .

## Fases do JSF

O JSF funciona através de fases que são invocadas a partir do momento que abrimos uma página.

Então, o JSF executa um processo para coletar as informações, validar e criar a página de resposta que será enviada ao usuário.

Este processo é composto por 6 fases:

<img class="alignnone size-full wp-image-55231" src="http://tableless.com.br/uploads/2016/07/fases-jsf.png" alt="Fases do JSF" width="748" height="411" />

&nbsp;

### Restore View

Fase onde o JSF criará uma árvore de componentes, contendo um objeto para cada componente visual do formulário e, se for a primeira exibição da página, ele pula todas as fases e vai para a **Render Response**.

Se a página já foi exibida, o framework buscará pela árvore já existente.

### Apply Request Values

Nesta fase, o framework pega os valores do formulário, eles são recebidos como Strings independente do tipo.

### Process Validation

O JSF converte os valores existentes para os tipos que estão vinculados nas propriedades dos Managed Beans.

Após a conversão, é feita a validação desses valores.

Se ocorrer algum erro em qualquer dessas etapas, o JSF redireciona para a fase Render Response.

### Update Model Values

Os dados convertidos são colocados nos objetos Managed Beans que estão vinculados.

### Invoke Application

O método do atributo action que está vinculado a algum botão que foi acionado é avalido pela Expression Language e seu valor é retornado.

### Render Response

O JSF processa a página recebida pelas fases anteriores e gera o código XHTML para o usuário.

## Criação do Login

Primeiramente vamos criar nosso xhtml com os campos e botões para login vinculado com um Managed Bean e outro xhtml para ser a página inicial após o login do usuário.

A página deve ter os campos vinculados a um Managed Bean chamado usuário e um botão vinculado a algum método para logar.

Este foi meu código, claro, há diversos meios diferente para se fazer o mesmo:

<pre class="lang-html">&lt;?xml version="1.0" encoding="ISO-8859-1" ?&gt;
&lt;!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd"&gt;
&lt;html xmlns="http://www.w3.org/1999/xhtml"
      xmlns:h="http://java.sun.com/jsf/html"
      xmlns:f="http://java.sun.com/jsf/core"
>
&lt;h:head&gt;
&lt;meta http-equiv="Content-Type" content="text/html; charset=ISO-8859-1" /&gt;
&lt;title&gt;Login&lt;/title&gt;
&lt;/h:head&gt;
&lt;h:body&gt;
    &lt;h:form&gt;
        &lt;h:panelGrid columns="2"&gt; 
            &lt;h:outputLabel value="Usuário:" /&gt;
            &lt;h:inputText value="#{usuario.usuario}" size="20" /&gt;
            
            &lt;h:outputLabel value="Senha:" /&gt;
            &lt;h:inputSecret value="#{usuario.senha}" size="20" /&gt;
                
            &lt;h:commandButton value="Logar" action="#{usuario.logar}" /&gt;
        &lt;/h:panelGrid&gt;
        &lt;h:messages /&gt;    
    &lt;/h:form&gt;
&lt;/h:body&gt;
&lt;/html&gt;
</pre>

E este foi o resultado:

<img class="alignnone size-full wp-image-55232" src="http://tableless.com.br/uploads/2016/07/result-jsf-login.png" alt="Formulário de login XHTMl" width="261" height="89" />

No método logar vou verificar se o usuário e a senha correspondem ao meu nome: &#8220;Julio&#8221;.

Caso o usuário ou a senha forem diferentes de &#8220;Julio&#8221;, exibirei uma mensagem informando que o usuário é inválido.

Em outros casos será invocado um _DAO_, que verificará se o usuário existe na base de dados ou o que for preciso.

Crie, também, uma página de resposta caso o usuário esteja correto.

Segue o código da classe Usuário:

<pre class="lang-java">package root;

import javax.faces.application.FacesMessage;
import javax.faces.bean.ManagedBean;
import javax.faces.bean.SessionScoped;
import javax.faces.context.FacesContext;

@ManagedBean
@SessionScoped
public class Usuario {
    private String usuario = "";
    private String senha = "";
    
    public String logar(){
        if(usuario.equals("Julio") && senha.equals("Julio")){
            return "pag-sucesso";
        }
        FacesContext ctx = FacesContext.getCurrentInstance();
        FacesMessage msg = new FacesMessage(FacesMessage.SEVERITY_ERROR, "Usuário inválido", "Usuário inválido");
        ctx.addMessage(null, msg);
        return "";              
    }
    
    
    public String getUsuario() {
        return usuario;
    }
    public void setUsuario(String usuario) {
        this.usuario = usuario;
    }
    public String getSenha() {
        return senha;
    }
    public void setSenha(String senha) {
        this.senha = senha;
    }
}
</pre>

E, também, o código do XHTML de resposta em caso de sucesso.

<pre class="lang-html">&lt;?xml version="1.0" encoding="ISO-8859-1" ?&gt;
&lt;!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd"&gt;
&lt;html xmlns="http://www.w3.org/1999/xhtml"
      xmlns:h="http://java.sun.com/jsf/html"
      xmlns:f="http://java.sun.com/jsf/core"
>
&lt;h:head&gt;
&lt;meta http-equiv="Content-Type" content="text/html; charset=ISO-8859-1" /&gt;
&lt;title&gt;Sucesso!!&lt;/title&gt;
&lt;/h:head&gt;
&lt;h:body&gt;
    Usuário logado!!!
&lt;/h:body&gt;
&lt;/html&gt;
</pre>

### 

### Testes

Vamos testar nossa página:

<img class="alignnone size-full wp-image-55233" src="http://tableless.com.br/uploads/2016/07/teste-jsf.png" alt="Teste do login em sucesso" width="295" height="111" />
  
Primeiramente coloquei os campos de modo correto, ou seja, com os valores em &#8220;Julio&#8221;, e após pressionar o botão &#8220;Logar&#8221; a página de sucesso foi retornada como esperado.

<img class="alignnone size-full wp-image-55234" src="http://tableless.com.br/uploads/2016/07/teste-jsf-sucesso.png" alt="teste-jsf-sucesso" width="159" height="62" />
  
Mas tem um problema, conseguimos acessarmos diretamente a página de sucesso, pois não há nenhuma validação se o usuário está logado. Em casos de sistemas grandes, isso pode ser um enorme problema, pois qualquer usuário poderia ter acesso a informações não permitidas.

### Correção

Devemos criar um login que valide se o usuário já está no sistema, então vamos criar uma classe que sirva como ouvinte entre as fases do JSF.

Para isto, é preciso:

  * Criar uma classe que implemente a interface **PhaseListener**;
  * Registrar no faces-config.xml.

Criarei uma classe chamada &#8220;Listener&#8221; que implementa a interface PhaseListener.

Esta interface possui 3 métodos:

  * beforePhase: código que será executado antes do processamento da fase;
  * afterPhase: código que será executado após o processamento da fase;
  * getPhaseId: retorna um Enum com o nome da fase atual.

Devemos implementar nosso método para verificar se o usuário está logado no método &#8220;afterPhase&#8221;.

Para verificar se a página que está sendo acessada é diferente da página &#8220;login.xhtml&#8221; devemos pegar a instância atual do &#8220;FacesContext&#8221; e, partir dele, pegar o ViewRoot e o ViewId que contém o nome da página atual:

<pre class="lang-java">package root;

import javax.faces.application.Application;
import javax.faces.application.NavigationHandler;
import javax.faces.context.FacesContext;
import javax.faces.event.PhaseEvent;
import javax.faces.event.PhaseId;
import javax.faces.event.PhaseListener;

public class Listener implements PhaseListener{

    /**
     * 
     */
    private static final long serialVersionUID = 1L;

    @Override
    public void beforePhase(PhaseEvent arg0) {
    }

    @Override
    public void afterPhase(PhaseEvent arg0) {
        FacesContext ctx = FacesContext.getCurrentInstance();
        if(!ctx.getViewRoot().getViewId().equals("/login.xhtml")){
                    
        }
    }

    @Override
    public PhaseId getPhaseId() {
        return null;
    }

}

</pre>

Após isto, é preciso verificar se o usuário está logado, isto pode ser feito com um atributo booleano na classe Usuario ou verificar se os parâmetros estão de acordo com o que queremos, vou utilizar esta segunda opção.

Para pegar o objeto Usuario que queremos, devemos utilizar o objeto &#8220;Application&#8221; a partir do FacesContext atual, através do método &#8220;getApplication&#8221;.

Então utilizamos o método &#8220;evaluateExpressionGet&#8221; do objeto &#8220;Application&#8221;:

<pre class="lang-java">package root;

import javax.faces.application.Application;
import javax.faces.application.NavigationHandler;
import javax.faces.context.FacesContext;
import javax.faces.event.PhaseEvent;
import javax.faces.event.PhaseId;
import javax.faces.event.PhaseListener;

public class Listener implements PhaseListener{

    /**
     * 
     */
    private static final long serialVersionUID = 1L;

    @Override
    public void beforePhase(PhaseEvent arg0) {
    }

    @Override
    public void afterPhase(PhaseEvent arg0) {
        FacesContext ctx = FacesContext.getCurrentInstance();
        if(!ctx.getViewRoot().getViewId().equals("/login.xhtml")){
            Application app = ctx.getApplication();
            Usuario u = app.evaluateExpressionGet(ctx, "#{usuario}", Usuario.class);
        }
    }

    @Override
    public PhaseId getPhaseId() {
        return null;
    }

}
</pre>

Agora aplicamos nossa validação, no meu caso apenas peguei o atributo usuario a partir do objeto Usuario atual e verifiquei se é diferente de &#8220;Julio&#8221;, se for, **retorno a navegação para a página login**.

Isto é feito a partir do objeto &#8220;NavigationHandler&#8221; conseguido a através do objeto &#8220;Application&#8221; e invoco o método &#8220;handleNavigation&#8221;, que altera o fluxo. Por último chamo o método &#8220;renderResponse&#8221; do FacesContext.

E, claro, devemos indicar ao Listener qual fase que desejamos interceptar, que no nosso caso é a &#8220;Restore View&#8221; indicando no método &#8220;getPhaseId&#8221;.

<pre class="&quot;lang-java">package root;

import javax.faces.application.Application;
import javax.faces.application.NavigationHandler;
import javax.faces.context.FacesContext;
import javax.faces.event.PhaseEvent;
import javax.faces.event.PhaseId;
import javax.faces.event.PhaseListener;

public class Listener implements PhaseListener{

    /**
     * 
     */
    private static final long serialVersionUID = 1L;

    @Override
    public void beforePhase(PhaseEvent arg0) {
    }

    @Override
    public void afterPhase(PhaseEvent arg0) {
        FacesContext ctx = FacesContext.getCurrentInstance();
        if(!ctx.getViewRoot().getViewId().equals("/login.xhtml")){
            Application app = ctx.getApplication();
            Usuario u = app.evaluateExpressionGet(ctx, "#{usuario}", Usuario.class);
            if(!u.getUsuario().equals("Julio")){
                NavigationHandler handler = app.getNavigationHandler();
                handler.handleNavigation(ctx, "", "login");
                ctx.renderResponse();
            }
        }
    }

    @Override
    public PhaseId getPhaseId() {
        return PhaseId.RESTORE_VIEW;
    }
}</pre>

Para que funcione, precisamos registrar no faces-config.xml que ele é um Listener.

<pre class="lang-xml">&lt;?xml version="1.0" encoding="UTF-8"?&gt;
&lt;faces-config
    xmlns="http://xmlns.jcp.org/xml/ns/javaee"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee http://xmlns.jcp.org/xml/ns/javaee/web-facesconfig_2_2.xsd"
    version="2.2"&gt;
    &lt;lifecycle&gt;
        &lt;phase-listener&gt;root.Listener&lt;/phase-listener&gt;
    &lt;/lifecycle&gt;

&lt;/faces-config&gt;
</pre>

Agora ao tentarmos entrar na página de sucesso diretamente, ele não vai.
  
<img class="alignnone size-full wp-image-55235" src="http://tableless.com.br/uploads/2016/07/resultado-final-jsf.png" alt="Resultado final" width="479" height="267" />

Para quem deseja obter a URL correta, apenas adicionar &#8220;?faces-redirect=true&#8221; ao final da String de redirecionamento no Listener:

<pre class="lang-java">package root;

import javax.faces.application.Application;
import javax.faces.application.NavigationHandler;
import javax.faces.context.FacesContext;
import javax.faces.event.PhaseEvent;
import javax.faces.event.PhaseId;
import javax.faces.event.PhaseListener;

public class Listener implements PhaseListener{

    /**
     * 
     */
    private static final long serialVersionUID = 1L;

    @Override
    public void beforePhase(PhaseEvent arg0) {
    }

    @Override
    public void afterPhase(PhaseEvent arg0) {
        FacesContext ctx = FacesContext.getCurrentInstance();
        if(!ctx.getViewRoot().getViewId().equals("/login.xhtml")){
            Application app = ctx.getApplication();
            Usuario u = app.evaluateExpressionGet(ctx, "#{usuario}", Usuario.class);
            if(!u.getUsuario().equals("Julio")){
                NavigationHandler handler = app.getNavigationHandler();
                handler.handleNavigation(ctx, "", "login?faces-redirect=true");
                ctx.renderResponse();
            }
        }
    }

    @Override
    public PhaseId getPhaseId() {
        return PhaseId.RESTORE_VIEW;
    }

}
</pre>

Então:

<img class="alignnone size-full wp-image-55236" src="http://tableless.com.br/uploads/2016/07/alteracao-param-jsf-2.png" alt="Entrada no browser" width="439" height="92" />

Retorna:

<img class="alignnone size-full wp-image-55237" src="http://tableless.com.br/uploads/2016/07/alteracao-param-jsf-3.png" alt="Resposta no browser" width="383" height="193" />

Obtendo o resultado desejado.

Comente em caso de dúvidas ou falhas =D.

Em meu blog tem alguns outros artigos deste mesmo tipo, se deseja ver: <http://jcdourado.github.io>

Obrigado!!

Segue alguns links de artigos e alguns livros que ajudam nessa caminhada:

<http://www.devmedia.com.br/jsf-session-criando-um-modulo-de-login/30975>

<http://www.devmedia.com.br/java-web-criando-uma-tela-de-login-com-jpa-jsf-primefaces-e-mysql/32456>

<http://www.universidadejava.com.br/materiais/jsf-tela-login/>

Livro: **JSF Eficaz** &#8211; Casa do Código.

&nbsp;