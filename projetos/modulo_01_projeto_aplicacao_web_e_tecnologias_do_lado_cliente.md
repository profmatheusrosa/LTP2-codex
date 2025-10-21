# Projeto do Módulo 1: Portal de Eventos Responsivo

## Contexto
Uma empresa de eventos deseja um portal público que destaque próximos eventos, permita inscrições e apresente notícias. O objetivo é prototipar a camada cliente consumindo APIs simuladas.

## Requisitos Principais
1. Página inicial com lista de eventos, cards com título, data e botão "Inscreva-se".
2. Página de detalhes do evento carregada dinamicamente via JavaScript.
3. Formulário de inscrição validado no cliente (nome, e-mail, quantidade de ingressos).
4. Layout responsivo com CSS Grid e Flexbox, mantendo compatibilidade com navegadores modernos.
5. Simulação de requisições HTTP utilizando `fetch` com dados mockados (`events.json`).

## Arquivos de Dados
- `dados_eventos.json`: arquivo localizado na raiz com lista de eventos (id, título, data, descrição, vagas).

## Etapas Sugeridas
1. Criar estrutura XHTML e componentes reutilizáveis (cabeçalho, rodapé, seções).
2. Implementar estilos modulares (BEM ou utilitários) para garantir consistência visual.
3. Desenvolver scripts que carreguem `dados_eventos.json`, renderizem listas e tratem inscrições via armazenamento local.
4. Garantir acessibilidade com uso de ARIA, semântica e foco adequado.
5. Escrever documentação rápida (`docs/README_portal.md`) descrevendo decisões de design.

## Critérios de Avaliação
- Fidelidade aos princípios de XHTML, CSS moderno e boas práticas de JavaScript.
- Experiência responsiva em diferentes larguras.
- Clareza do código e organização de assets.
