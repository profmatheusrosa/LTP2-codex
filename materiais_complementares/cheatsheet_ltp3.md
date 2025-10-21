# Cheatsheet LTP3

## HTTP
- Métodos comuns: `GET`, `POST`, `PUT`, `DELETE`.
- Códigos de status: `200 OK`, `302 Found`, `404 Not Found`, `500 Internal Server Error`.
- Cabeçalhos úteis: `Content-Type`, `Accept`, `Authorization`, `Cache-Control`.

## Servlets
```java
@WebServlet("/exemplo")
public class ExemploServlet extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws IOException {
        response.setContentType("text/html;charset=UTF-8");
        request.setAttribute("mensagem", "Olá Servlets");
        request.getRequestDispatcher("/WEB-INF/exemplo.jsp").forward(request, response);
    }
}
```

## JSP + EL + JSTL
```jsp
<%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>
<p>Usuário: ${sessionScope.usuario.nome}</p>
<c:forEach var="pedido" items="${requestScope.pedidos}">
  <li>${pedido.id} - ${pedido.status}</li>
</c:forEach>
```

## MVC Checklist
- Model: entidades e regras de negócio.
- View: JSP/HTML/CSS/JS.
- Controller: Servlets + Filters.
- DAO: encapsula persistência.
- Service: orquestra regras complexas.

## Ferramentas Úteis
- IDE: IntelliJ IDEA, Eclipse.
- Build: Maven ou Gradle.
- Testes: JUnit, Mockito.
- Servidor: Apache Tomcat.
