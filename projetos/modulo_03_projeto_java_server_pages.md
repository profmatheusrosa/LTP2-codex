# Projeto do Módulo 3: Painel Administrativo com JSP e JSTL

## Contexto
Uma startup precisa de um painel administrativo para gerenciar pedidos, clientes e relatórios. O objetivo é construir a camada de visão usando JSP, EL e JSTL, integrando-se a Servlets existentes.

## Requisitos Principais
1. Dashboard inicial exibindo métricas agregadas (total de pedidos, faturamento, clientes ativos) com cards responsivos.
2. Tabelas de listagem com paginação e filtros implementados via parâmetros GET e JSTL.
3. Formulários que utilizam `<jsp:useBean>` para popular objetos e exibir validações.
4. Componentização de cabeçalhos, rodapés e menus via diretiva `include` ou `<jsp:include>`.
5. Uso de bundles de internacionalização para suportar português e inglês.

## Etapas Sugeridas
1. Criar layout base com template principal e includes reutilizáveis.
2. Desenvolver tags customizadas simples para formatar status de pedidos.
3. Integrar com Servlets que fornecem dados via atributos de requisição.
4. Aplicar JSTL para lógica condicional, loops e formatação.
5. Garantir acessibilidade e usabilidade com feedback visual e ARIA.

## Critérios de Avaliação
- Separação clara entre lógica de negócio (Servlets) e visão (JSP/JSTL).
- Uso consistente de EL e JSTL sem scriptlets.
- Qualidade visual e suporte a múltiplos idiomas.
