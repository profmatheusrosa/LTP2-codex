# Curso LTP3

Curso completo sobre desenvolvimento de aplicações web Java com foco em Servlets, JSP, arquitetura MVC e integração de camadas cliente e servidor.

## Visão Geral do Curso

- **Carga Horária Total:** 80 horas
- **Duração por Aula:** 1 hora

## Estrutura de Pastas

```
LTP3/
├── teoria/
├── exercicios/
├── projetos/
├── materiais_complementares/
├── imagens/
├── README.md
├── planejamento_aulas.md
└── LICENSE
```

## Conteúdo Programático

| Módulo | Tópicos Principais | Subtópicos | Detalhes |
|--------|-------------------|------------|----------|
| Módulo 1: Aplicação Web e Tecnologias do Lado Cliente | Aplicação Web; Tecnologias do Lado Cliente | Arquitetura e Funcionamento; Cliente Web; Servidor Web; Protocolo HTTP; Marcação XHTML; Estilos CSS; Scripts JavaScript | Fundamentos da web, ciclo cliente-servidor e tecnologias essenciais de front-end. |
| Módulo 2: Servlets | Servlets | Definição; Ciclo de Vida; GET e POST; Parâmetros e Respostas; Redirecionamento e Encaminhamento; Sessões | Construção da camada de controle com Servlets e gerenciamento de estado. |
| Módulo 3: Java Server Pages (JSP) | JSP Parte 1 e Parte 2 | Scriptlets; Declarações; Expressões; Objetos Implícitos; Diretivas; Ações; EL; JSTL | Criação de camadas de visão dinâmicas utilizando JSP, EL e JSTL. |
| Módulo 4: Arquitetura MVC e Padrões de Projeto | Arquitetura MVC | Visão Geral; Camada Modelo; DAO; Camada Visão; Camada Controle | Organização em camadas, padrões de projeto e boas práticas estruturais. |
| Módulo 5: Projeto de Conclusão de Curso | Projeto Integrador | Desenvolvimento | Integração de todos os conceitos em um projeto completo. |

## Links Rápidos

| Módulo | Teoria | Exercícios | Projeto |
|--------:|:------:|:----------:|:-------:|
| Módulo 1<br>Aplicação Web e Tecnologias do Lado Cliente | [Teoria](teoria/modulo_01_aplicacao_web_e_tecnologias_do_lado_cliente.md) | [Exercícios](exercicios/modulo_01_exercicios_aplicacao_web_e_tecnologias_do_lado_cliente.md) | [Projeto](projetos/modulo_01_projeto_aplicacao_web_e_tecnologias_do_lado_cliente.md) |
| Módulo 2<br>Servlets | [Teoria](teoria/modulo_02_servlets.md) | [Exercícios](exercicios/modulo_02_exercicios_servlets.md) | [Projeto](projetos/modulo_02_projeto_servlets.md) |
| Módulo 3<br>Java Server Pages (JSP) | [Teoria](teoria/modulo_03_java_server_pages_parte_1.md) | [Exercícios](exercicios/modulo_03_exercicios_java_server_pages.md) | [Projeto](projetos/modulo_03_projeto_java_server_pages.md) |
| Módulo 4<br>Arquitetura MVC e Padrões de Projeto | [Teoria](teoria/modulo_04_arquitetura_mvc_e_padroes_de_projeto.md) | [Exercícios](exercicios/modulo_04_exercicios_arquitetura_mvc_e_padroes_de_projeto.md) | [Projeto](projetos/modulo_04_projeto_arquitetura_mvc_e_padroes_de_projeto.md) |
| Módulo 5<br>Projeto de Conclusão de Curso | [Teoria](teoria/modulo_05_projeto_de_conclusao_de_curso.md) | [Exercícios](exercicios/modulo_05_exercicios_projeto_de_conclusao_de_curso.md) | [Projeto](projetos/modulo_05_projeto_de_conclusao_de_curso.md) |

## Planejamento das Aulas

- Consulte o arquivo [planejamento_aulas.md](planejamento_aulas.md) para a divisão completa das 80 aulas e correlação com materiais de apoio.

## Instruções de Uso

1. Clone o repositório:
   ```bash
   git clone <url-do-repositorio>
   cd LTP3
   ```
2. Navegue pelos módulos acessando as pastas `teoria/`, `exercicios/` e `projetos/` conforme o plano de estudos.
3. Utilize um servidor de aplicações Java (Tomcat 10+, Jetty 11+) para executar os exemplos práticos.
4. Requisitos recomendados: JDK 17+, Maven 3.9+ ou Gradle 8+, Node.js 18+ para recursos front-end opcionais.
5. Ferramentas adicionais sugeridas estão em [materiais_complementares/ferramentas_e_softwares_ltp3.md](materiais_complementares/ferramentas_e_softwares_ltp3.md).

## Verificação e Boas Práticas

- [ ] Todos os links relativos foram revisados.
- [ ] Arquivos de teoria, exercícios e projetos seguem nomes padronizados em minúsculas com underscores.
- [ ] Placeholders de imagens possuem descrições correspondentes em `imagens/lista_imagens_a_gerar.md`.

Execute a verificação rápida de links no PowerShell:

```powershell
Get-Content README.md -Raw | Select-String -Pattern "\[.*?\]\((.*?)\)" -AllMatches | ForEach-Object { $_.Matches } | ForEach-Object { $_.Groups[1].Value } | ForEach-Object { if (-Not (Test-Path $_)) { Write-Host "Link quebrado: $_" } }
```

## Exemplo de Template de README

~~~~markdown
# Curso de Exemplo: Nome do Curso

Breve descrição do curso...

## Visão Geral do Curso

- **Carga Horária Total:** 60 horas
- **Duração por Aula:** 1 hora

## Estrutura de Pastas

    curso_novo_nome/
    ├── teoria/
    ├── exercicios/
    ├── projetos/
    ├── materiais_complementares/
    ├── imagens/
    ├── README.md
    ├── planejamento_aulas.md
    └── LICENSE

## Conteúdo Programático

| Módulo | Tópicos Principais | Subtópicos | Detalhes |
|--------|-------------------|------------|----------|
| Módulo 1 | Título do Módulo | 1.1 Subtopico | Descrição |

## Links Rápidos

| Módulo | Teoria | Exercícios | Projeto |
|--------:|:------:|:----------:|:-------:|
| Módulo 1<br>Nome do Módulo | [Teoria](teoria/modulo_01_nome_do_modulo.md) | [Exercícios](exercicios/modulo_01_exercicios_nome_do_modulo.md) | [Projeto](projetos/modulo_01_projeto_nome_do_modulo.md) |

## Planejamento das Aulas

- Ver `planejamento_aulas.md` para uma tabela detalhada.

## Instruções de Uso

- Clone o repositório e abra os arquivos Markdown.
~~~~
