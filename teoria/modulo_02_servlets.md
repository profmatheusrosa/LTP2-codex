# Módulo 2: Servlets

## Sumário
- [Introdução ao Módulo](#introdução-ao-módulo)
- [3. Servlets](#3-servlets)
  - [3.1 Definição](#31-definição)
  - [3.2 Ciclo de Vida](#32-ciclo-de-vida)
  - [3.3 Tratamento de Solicitações GET e POST](#33-tratamento-de-solicitações-get-e-post)
  - [3.4 Parâmetros e Respostas](#34-parâmetros-e-respostas)
  - [3.5 Redirecionamento e Encaminhamento](#35-redirecionamento-e-encaminhamento)
  - [3.6 Sessões](#36-sessões)
- [Conclusão](#conclusão)

## Introdução ao Módulo
Este módulo apresenta os componentes Servlets da plataforma Java EE/Jakarta EE, mostrando como lidar com requisições HTTP, administrar o ciclo de vida, manipular parâmetros e controlar fluxos de navegação com redirecionamentos, encaminhamentos e sessões.

## 3. Servlets
Servlets são classes Java executadas no servidor que respondem a requisições HTTP. Eles formam a base de muitos frameworks MVC e fornecem controle fino sobre o processamento. [IMAGEM_SERVLET_FLUXO]

### 3.1 Definição
Um Servlet herda `HttpServlet` e sobrescreve métodos como `doGet` e `doPost`. O contêiner (Tomcat, Jetty, Payara) gerencia sua instância, carregando-a sob demanda conforme o mapeamento definido no `web.xml` ou via anotações `@WebServlet`.

```java
@WebServlet(name = "ExemploServlet", urlPatterns = "/exemplo")
public class ExemploServlet extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws IOException {
        response.setContentType("text/plain;charset=UTF-8");
        response.getWriter().println("Olá, Servlet!");
    }
}
```

**Exercício 2:** Qual é a função principal de um Servlet?
 a) Executar scripts JavaScript no cliente.

 b) Processar requisições HTTP no servidor e gerar respostas.

 c) Renderizar CSS responsivo.

 d) Substituir o banco de dados da aplicação.

<details>
<summary>Ver Resposta</summary>

**Resposta:** b) Processar requisições HTTP no servidor e gerar respostas.

**Explicação:** Servlets são componentes server-side que recebem, processam e respondem a requisições HTTP, integrando-se a diversas camadas da aplicação.
</details>

### 3.2 Ciclo de Vida
O ciclo de vida inclui três fases: `init`, `service` e `destroy`. Na primeira requisição, o contêiner instancia o Servlet e chama `init`. Depois, cada requisição dispara `service`, que delega para `doGet`, `doPost` etc. Quando o contêiner é desligado ou o Servlet é descarregado, `destroy` é invocado para liberar recursos. [IMAGEM_SERVLET_CICLO_VIDA]

**Exercício 2.1:** Qual método é chamado apenas uma vez durante o ciclo de vida do Servlet?
 a) `doGet`

 b) `service`

 c) `init`

 d) `doPost`

<details>
<summary>Ver Resposta</summary>

**Resposta:** c) `init`

**Explicação:** `init` é executado na primeira inicialização do Servlet e prepara recursos compartilhados. Métodos `doGet`/`doPost` executam por requisição.
</details>

### 3.3 Tratamento de Solicitações GET e POST
`doGet` lida com dados de consulta e recursos idempotentes; parâmetros são passados pela URL. `doPost` trata dados enviados no corpo, usados para operações que alteram estado. A escolha correta do método melhora semântica, caching e segurança. [IMAGEM_SERVLET_GET_POST]

```java
@Override
protected void doPost(HttpServletRequest request, HttpServletResponse response) throws IOException {
    String nome = request.getParameter("nome");
    response.setContentType("text/html;charset=UTF-8");
    PrintWriter writer = response.getWriter();
    writer.println("<h1>Cadastro recebido</h1>");
    writer.printf("<p>Bem-vindo, %s!</p>", nome);
}
```

**Exercício 2.2:** Quando preferir o método POST em vez de GET?
 a) Ao solicitar páginas estáticas públicas.

 b) Quando a operação altera dados ou envolve informações sensíveis.

 c) Sempre que o número de parâmetros for pequeno.

 d) Quando se deseja cache automático pelo navegador.

<details>
<summary>Ver Resposta</summary>

**Resposta:** b) Quando a operação altera dados ou envolve informações sensíveis.

**Explicação:** POST envia dados no corpo da requisição, não fica exposto na URL e é apropriado para operações não idempotentes ou sensíveis.
</details>

### 3.4 Parâmetros e Respostas
Servlets capturam parâmetros usando `request.getParameter`, `getParameterValues` ou leitura direta do corpo para formatos JSON. As respostas são configuradas com `setContentType`, `setStatus` e escrita no `PrintWriter` ou `OutputStream`. Também é possível definir cabeçalhos de cache, cookies e anexar arquivos binários. [IMAGEM_SERVLET_PARAMETROS]

**Exercício 2.3:** Como enviar uma resposta JSON a partir de um Servlet?
 a) Definindo o tipo de conteúdo como `text/plain` e escrevendo XML.

 b) Configurando `setContentType("application/json")` e escrevendo o JSON no `PrintWriter`.

 c) Apenas retornando objetos Java sem conversão.

 d) Configurando o status 404 automaticamente.

<details>
<summary>Ver Resposta</summary>

**Resposta:** b) Configurando `setContentType("application/json")` e escrevendo o JSON no `PrintWriter`.

**Explicação:** Para respostas JSON, define-se o MIME type adequado e escreve-se a string JSON, garantindo que clientes interpretem corretamente o conteúdo.
</details>

### 3.5 Redirecionamento e Encaminhamento
`response.sendRedirect` envia um código 302 e instrui o cliente a requisitar outra URL. `RequestDispatcher.forward` encaminha internamente para outro recurso sem nova requisição. Redirecionamentos expõem a nova URL e reiniciam o ciclo. Encaminhamentos preservam atributos de requisição e são usados para delegar a JSPs ou outros Servlets. [IMAGEM_SERVLET_REDIRECIONAMENTO]

**Exercício 2.4:** Qual opção descreve corretamente a diferença entre redirect e forward?
 a) Ambos enviam código 200 e mantêm a mesma URL no navegador.

 b) Redirect envolve uma nova requisição pelo cliente, enquanto forward ocorre internamente no servidor.

 c) Forward funciona apenas para arquivos estáticos.

 d) Redirect preserva atributos da requisição original automaticamente.

<details>
<summary>Ver Resposta</summary>

**Resposta:** b) Redirect envolve uma nova requisição pelo cliente, enquanto forward ocorre internamente no servidor.

**Explicação:** Redirect emite código 3xx e muda a URL no navegador. Forward mantém a mesma requisição e é transparente para o cliente.
</details>

### 3.6 Sessões
Sessões permitem armazenar dados por usuário entre requisições. `HttpSession` é obtido com `request.getSession()`. O contêiner associa a sessão a um cookie `JSESSIONID`. Sessões devem ser usadas com parcimônia, evitando objetos pesados e garantindo expiração apropriada. Técnicas como Session Fixation Protection e HTTPS mitigam ataques. [IMAGEM_SERVLET_SESSOES]

```java
HttpSession session = request.getSession();
session.setAttribute("usuarioAutenticado", usuario);
```

**Exercício 2.5:** Como invalidar uma sessão quando o usuário sai do sistema?
 a) Remover o cookie `JSESSIONID` manualmente.

 b) Chamar `session.invalidate()` para destruir a sessão e liberar dados.

 c) Forçar o usuário a fechar o navegador.

 d) Criar uma nova sessão vazia sem apagar a antiga.

<details>
<summary>Ver Resposta</summary>

**Resposta:** b) Chamar `session.invalidate()` para destruir a sessão e liberar dados.

**Explicação:** `invalidate` remove a sessão atual e garante que novos dados sejam associados apenas a uma nova sessão criada posteriormente.
</details>

## Conclusão
Serviços baseados em Servlets oferecem controle total sobre o ciclo HTTP, viabilizando arquiteturas flexíveis. A compreensão de sessões, redirecionamentos e manipulação de parâmetros é essencial para construir camadas de controle sólidas.

[← Módulo anterior](../teoria/modulo_01_aplicacao_web_e_tecnologias_do_lado_cliente.md) | [Próximo módulo →](../teoria/modulo_03_java_server_pages_parte_1.md) | [← Voltar ao README](../README.md)
