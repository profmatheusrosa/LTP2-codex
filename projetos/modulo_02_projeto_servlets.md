# Projeto do Módulo 2: Sistema de Atendimento Online

## Contexto
Uma clínica deseja disponibilizar um sistema web para agendamento e acompanhamento de atendimentos. O foco é construir a camada de controle com Servlets, manipulando diferentes fluxos de navegação.

## Requisitos Principais
1. Cadastro de pacientes com validação server-side e feedback em JSPs.
2. Agendamento de consultas via formulário POST, armazenando dados em uma estrutura em memória ou banco leve.
3. Listagem de consultas com filtros por data e status via parâmetros GET.
4. Implementação de redirecionamentos para confirmar ações e encaminhamentos para JSPs de visualização.
5. Gestão de sessão para autenticação simples de atendentes.

## Etapas Sugeridas
1. Modelar Servlets específicos (`PacienteServlet`, `ConsultaServlet`) e um `AuthServlet` para login.
2. Configurar filtros para proteger rotas autenticadas.
3. Utilizar `RequestDispatcher` para encaminhar dados para JSPs.
4. Implementar tratamento de erros personalizados com páginas de erro e códigos adequados.
5. Registrar logs das operações importantes para auditoria.

## Critérios de Avaliação
- Uso correto do ciclo de vida dos Servlets e distinção entre GET/POST.
- Navegação clara e feedback ao usuário.
- Organização do código e documentação das rotas disponíveis.
