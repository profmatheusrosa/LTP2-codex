# Exercícios Práticos – Módulo 3: Java Server Pages (JSP)

## Exercício 1: Catálogo Dinâmico com JSTL
Crie uma página JSP que receba, via atributo de requisição, uma lista de produtos (nome, preço, categoria). Utilize JSTL e EL para exibir os itens em cards responsivos. Adicione filtros por categoria usando parâmetros de consulta e destaque a categoria selecionada.

### Requisitos
- Registrar a biblioteca core da JSTL e utilizar `<c:forEach>` e `<c:if>`.
- Formatar preços com `<fmt:formatNumber>` e internacionalizar textos usando bundles.
- Evitar scriptlets; toda a lógica deve usar JSTL/EL ou Servlets auxiliares.

## Exercício 2: Formulário com Beans e Validação
Implemente uma página JSP que usa `<jsp:useBean>` e `<jsp:setProperty>` para popular um bean `Cliente`. Exiba mensagens de validação retornadas por um Servlet utilizando objetos implícitos e EL. Garanta que, após erro, os campos mantenham os valores inseridos.

### Dicas
- Utilize escopos `request` e `session` conscientemente para mensagens e dados persistentes.
- Mantenha a formatação HTML semântica para facilitar estilos e acessibilidade.
