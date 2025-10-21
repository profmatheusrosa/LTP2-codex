# Projeto do Módulo 4: Plataforma de Pedidos MVC

## Contexto
Uma rede de restaurantes quer uma plataforma centralizada para gerenciar pedidos online, cozinhas e entregas. O objetivo é projetar e implementar a aplicação seguindo rigorosamente o padrão MVC e padrões associados.

## Requisitos Principais
1. Modelagem de entidades (`Cliente`, `Pedido`, `ItemPedido`, `Restaurante`) com regras de negócio.
2. DAO abstrato com implementação em memória e camada de serviço mediando regras.
3. Servlets controladores que roteiam ações (listar, criar, atualizar, cancelar pedidos).
4. JSPs com JSTL para exibir listas, formulários e relatórios.
5. Integração com filtros para auditoria e controle de acesso básico.

## Etapas Sugeridas
1. Desenhar diagrama de classes e fluxo MVC antes da implementação.
2. Criar camada de serviço responsável por transações e validações complexas.
3. Implementar DAOs com interfaces e classes concretas, permitindo substituição futura por JDBC ou JPA.
4. Construir controladores finos que delegam à camada de serviço e encaminham para visões.
5. Escrever testes unitários para o modelo e mocks para DAOs.

## Critérios de Avaliação
- Aderência ao padrão MVC com responsabilidades claras.
- Facilidade de substituição da camada de persistência.
- Documentação arquitetural e de implantação.
