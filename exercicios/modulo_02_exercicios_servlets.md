# Exercícios Práticos – Módulo 2: Servlets

## Exercício 1: Cadastro de Contatos
Implemente um Servlet que receba dados de um formulário (nome, e-mail, telefone) e os persista temporariamente em uma lista mantida no contexto da aplicação. Crie rotas para exibir a lista completa e para remover contatos por índice. Utilize `doGet` para exibir formulários e `doPost` para processar submissões.

### Requisitos
- Mapeie o Servlet via anotação `@WebServlet` com múltiplos `urlPatterns`.
- Formate a resposta como HTML estruturado com tabelas ou listas.
- Valide dados no servidor, retornando mensagens de erro apropriadas.

## Exercício 2: API JSON com Servlets
Desenvolva um Servlet que responda na rota `/api/pedidos` com dados JSON simulados. Permita filtros por status via parâmetros de consulta (`?status=ABERTO`). Configure o `contentType` para `application/json` e implemente tratamento de erros com códigos HTTP adequados.

### Dicas
- Utilize classes auxiliares para representar pedidos e serializá-los manualmente com `StringBuilder` ou bibliotecas como Gson.
- Adicione testes unitários com `MockHttpServletRequest` e `MockHttpServletResponse` quando possível.
