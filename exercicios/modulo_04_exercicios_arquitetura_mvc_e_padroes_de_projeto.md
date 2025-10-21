# Exercícios Práticos – Módulo 4: Arquitetura MVC e Padrões de Projeto

## Exercício 1: Refatorando para MVC
Receba uma aplicação web simples que mistura lógica de negócio e apresentação na mesma JSP. Reestruture o código criando classes de modelo, DAOs simulados com listas em memória e um Servlet controlador que encaminha dados processados para JSPs especializadas. Documente as mudanças em um arquivo `REFATORACAO.md`.

### Requisitos
- Utilizar padrão DAO para encapsular persistência em memória.
- Implementar testes unitários para o modelo com JUnit.
- Registrar no relatório quais responsabilidades foram movidas para cada camada.

## Exercício 2: Front Controller com Filtro
Implemente um Front Controller usando um Servlet principal que roteia para comandos específicos (classes que implementam uma interface `Comando`). Utilize um filtro (`Filter`) para autenticação simulada antes de chegar ao controlador. Crie pelo menos três comandos diferentes (listar, salvar, remover).

### Dicas
- Use o padrão Command para separar ações e facilitar manutenção.
- Configure o filtro via anotação `@WebFilter` e compartilhe recursos via `ServletContext`.
