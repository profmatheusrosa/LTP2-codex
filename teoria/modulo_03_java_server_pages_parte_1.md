# Módulo 3: Java Server Pages (JSP)

## Sumário
- [Introdução ao Módulo](#introdução-ao-módulo)
- [4. Java Server Pages (JSP) – Parte 1](#4-java-server-pages-jsp-–-parte-1)
  - [4.1 Scriptlets](#41-scriptlets)
  - [4.2 Declarações](#42-declarações)
  - [4.3 Expressões](#43-expressões)
  - [4.4 Objetos Implícitos](#44-objetos-implícitos)
- [5. Java Server Pages (JSP) – Parte 2](#5-java-server-pages-jsp-–-parte-2)
  - [5.1 Diretivas](#51-diretivas)
  - [5.2 Ações](#52-ações)
  - [5.3 Linguagem de Expressão – EL](#53-linguagem-de-expressão-–-el)
  - [5.4 Biblioteca de Tags Padrão – JSTL](#54-biblioteca-de-tags-padrão-–-jstl)
- [Conclusão](#conclusão)

## Introdução ao Módulo
Este módulo apresenta a tecnologia Java Server Pages (JSP) em duas partes. Primeiro, exploramos os elementos básicos — scriptlets, declarações, expressões e objetos implícitos. Em seguida, abordamos diretivas, ações, Expression Language (EL) e a JSTL, que promovem uma camada de visão mais limpa e expressiva.

## 4. Java Server Pages (JSP) – Parte 1
JSPs são templates HTML com extensões `.jsp` que o servidor converte em Servlets. Elas permitem combinar marcação com código Java para gerar conteúdo dinâmico. [IMAGEM_JSP_RENDERIZACAO]

### 4.1 Scriptlets
Scriptlets são blocos Java delimitados por `<% ... %>`. Usam-se para lógica de controle simples, mas o uso excessivo gera páginas difíceis de manter. Boas práticas recomendam mover a lógica para Servlets ou classes auxiliares, mantendo a JSP focada em apresentação.

```jsp
<ul>
<%
    List<String> linguagens = (List<String>) request.getAttribute("linguagens");
    for (String linguagem : linguagens) {
%>
    <li><%= linguagem %></li>
<%
    }
%>
</ul>
```

**Exercício 3:** Qual é o principal uso de scriptlets em JSP?
 a) Definir estilos CSS reutilizáveis.

 b) Incluir blocos de lógica Java embutidos em HTML.

 c) Configurar servidores de aplicação.

 d) Criar bancos de dados relacionais.

<details>
<summary>Ver Resposta</summary>

**Resposta:** b) Incluir blocos de lógica Java embutidos em HTML.

**Explicação:** Scriptlets inserem código Java diretamente na página, mas devem ser usados com parcimônia em favor de abordagens mais organizadas.
</details>

### 4.2 Declarações
Declarações (`<%! ... %>`) permitem definir variáveis e métodos membro na classe gerada da JSP. São úteis para constantes ou utilidades leves, mas representam estado compartilhado entre requisições. É crucial garantir imutabilidade para evitar problemas concorrentes. [IMAGEM_JSP_DECLARACOES]

```jsp
<%!
    private static final DateTimeFormatter FORMATTER = DateTimeFormatter.ofPattern("dd/MM/yyyy");
    public String formatar(LocalDate data) {
        return FORMATTER.format(data);
    }
%>
<p>Data atual: <%= formatar(LocalDate.now()) %></p>
```

**Exercício 3.1:** Qual cuidado é necessário ao usar declarações em JSP?
 a) Garantir que variáveis de instância sejam imutáveis para evitar concorrência.

 b) Usar declarações para manipular DOM do navegador diretamente.

 c) Evitar qualquer importação de pacotes Java.

 d) Declarar métodos apenas dentro de Servlets.

<details>
<summary>Ver Resposta</summary>

**Resposta:** a) Garantir que variáveis de instância sejam imutáveis para evitar concorrência.

**Explicação:** Declarar estado mutável na JSP pode gerar condições de corrida, pois a mesma instância atende múltiplas requisições simultaneamente.
</details>

### 4.3 Expressões
Expressões (`<%= ... %>`) avaliam código Java e escrevem o resultado diretamente na saída. Elas são ideais para exibir valores simples, como atributos de requisição ou resultados de métodos utilitários, evitando chamadas explícitas a `out.println`. [IMAGEM_JSP_EXPRESSOES]

```jsp
<p>Total de pedidos: <%= request.getAttribute("totalPedidos") %></p>
```

**Exercício 3.2:** Qual é a vantagem de usar expressões em JSP?
 a) Permitir loops complexos sem scriptlets.

 b) Inserir dados dinamicamente sem chamadas explícitas a `out.println`.

 c) Definir diretivas `taglib` automaticamente.

 d) Executar requisições assíncronas no cliente.

<details>
<summary>Ver Resposta</summary>

**Resposta:** b) Inserir dados dinamicamente sem chamadas explícitas a `out.println`.

**Explicação:** Expressões simplificam a exibição de valores resultantes de objetos Java, tornando a JSP mais legível e concisa.
</details>

### 4.4 Objetos Implícitos
Objetos implícitos (`request`, `response`, `session`, `application`, `out`, `config`, `pageContext`, `page`, `exception`) estão disponíveis sem declaração prévia. Eles permitem acessar dados de escopos distintos e manipular a resposta HTTP diretamente. Conhecer quando usar cada objeto é essencial para manter a lógica organizada. [IMAGEM_JSP_OBJETOS_IMPLICITOS]

```jsp
<%
    String usuario = (String) session.getAttribute("usuario");
    if (usuario == null) {
        response.sendRedirect("login.jsp");
    }
%>
```

**Exercício 3.3:** Qual objeto implícito representa a sessão do usuário?
 a) `request`

 b) `session`

 c) `application`

 d) `page`

<details>
<summary>Ver Resposta</summary>

**Resposta:** b) `session`

**Explicação:** O objeto `session` expõe a `HttpSession` associada ao usuário, permitindo armazenar dados entre requisições.
</details>

## 5. Java Server Pages (JSP) – Parte 2
A segunda parte enfatiza recursos declarativos que tornam as JSPs mais limpas, reduzindo código Java e favorecendo reuso através de tags e EL. [IMAGEM_JSP_PARTE2_VISUAL]

### 5.1 Diretivas
Diretivas (`<%@ ... %>`) influenciam a página inteira. `page` define linguagem, importações e tratamento de exceções; `include` insere arquivos estáticos no tempo de compilação; `taglib` registra bibliotecas de tags. Manter importações específicas evita carregamento desnecessário. [IMAGEM_JSP_DIRETIVAS]

```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" %>
<%@ page import="java.time.LocalDate" %>
<%@ include file="cabecalho.jsp" %>
```

**Exercício 3.4:** Qual diretiva inclui conteúdo estático no momento da tradução da JSP?
 a) `page`

 b) `include`

 c) `taglib`

 d) `useBean`

<details>
<summary>Ver Resposta</summary>

**Resposta:** b) `include`

**Explicação:** A diretiva `include` mescla arquivos durante a tradução, permitindo compartilhar cabeçalhos e rodapés sem duplicação.
</details>

### 5.2 Ações
Ações JSP (`<jsp:useBean>`, `<jsp:setProperty>`, `<jsp:forward>`) encapsulam operações comuns. Elas instanciam beans, populam propriedades a partir de parâmetros e encaminham requisições. Com `<jsp:include>`, é possível incluir recursos dinamicamente no tempo de execução. [IMAGEM_JSP_ACOES]

```jsp
<jsp:useBean id="cliente" class="com.exemplo.Cliente" scope="request" />
<jsp:setProperty name="cliente" property="*" />
<jsp:forward page="/WEB-INF/paginas/detalhes.jsp" />
```

**Exercício 3.5:** O que faz a ação `<jsp:setProperty name="cliente" property="*" />`?
 a) Define todas as propriedades do bean `cliente` com valores padrão nulos.

 b) Popula propriedades com nomes correspondentes aos parâmetros da requisição.

 c) Remove o bean do escopo da requisição.

 d) Cria uma nova instância de Servlet.

<details>
<summary>Ver Resposta</summary>

**Resposta:** b) Popula propriedades com nomes correspondentes aos parâmetros da requisição.

**Explicação:** A ação percorre parâmetros HTTP e atribui valores aos setters do bean com nomes compatíveis, simplificando o binding.
</details>

### 5.3 Linguagem de Expressão – EL
EL (`${...}`) possibilita acessar atributos de escopos (`requestScope`, `sessionScope`) e chamar métodos simples com sintaxe enxuta. Operadores lógicos, relacionais e de coleção permitem construir expressões declarativas. EL melhora a leitura e substitui expressões Java. [IMAGEM_JSP_EL]

```jsp
<p>Bem-vindo, ${sessionScope.usuario.nome}!</p>
<c:if test="${not empty requestScope.erros}">
    <ul>
        <c:forEach var="erro" items="${requestScope.erros}">
            <li>${erro}</li>
        </c:forEach>
    </ul>
</c:if>
```

**Exercício 3.6:** Qual benefício a EL oferece?
 a) Executar consultas SQL diretamente na JSP.

 b) Simplificar acesso a dados de escopo com sintaxe declarativa.

 c) Substituir o uso de JSTL.

 d) Configurar filtros de segurança no servidor.

<details>
<summary>Ver Resposta</summary>

**Resposta:** b) Simplificar acesso a dados de escopo com sintaxe declarativa.

**Explicação:** EL evita código Java verboso na JSP, oferecendo uma sintaxe amigável para acessar atributos e avaliar expressões condicionais.
</details>

### 5.4 Biblioteca de Tags Padrão – JSTL
A JSTL fornece tags para lógica condicional (`c:if`), iteração (`c:forEach`), formatação (`fmt:formatNumber`), SQL (usado com cautela) e funções (`fn:length`). O uso combinado de JSTL e EL elimina quase todo o código Java das JSPs, tornando-as mais fáceis de testar e manter. [IMAGEM_JSP_JSTL]

```jsp
<%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>
<c:forEach var="produto" items="${requestScope.produtos}">
    <div class="produto">
        <h3>${produto.nome}</h3>
        <p><fmt:formatNumber value="${produto.preco}" type="currency"/></p>
    </div>
</c:forEach>
```

**Exercício 3.7:** Qual é o objetivo principal da JSTL?
 a) Substituir todos os Servlets da aplicação.

 b) Fornecer um conjunto padronizado de tags para lógica, iteração e formatação em JSPs.

 c) Renderizar componentes gráficos em Swing.

 d) Criar classes de modelo automaticamente.

<details>
<summary>Ver Resposta</summary>

**Resposta:** b) Fornecer um conjunto padronizado de tags para lógica, iteração e formatação em JSPs.

**Explicação:** A JSTL padroniza operações comuns em JSPs, reduzindo a necessidade de código Java e promovendo reutilização.
</details>

## Conclusão
Ao dominar os recursos básicos e avançados de JSP, você está preparado para construir camadas de visão limpas e expressivas, integradas a Servlets e padrões MVC. O próximo módulo mostrará como organizar esses componentes em uma arquitetura sustentável.

[← Módulo anterior](../teoria/modulo_02_servlets.md) | [Próximo módulo →](../teoria/modulo_04_arquitetura_mvc_e_padroes_de_projeto.md) | [← Voltar ao README](../README.md)
