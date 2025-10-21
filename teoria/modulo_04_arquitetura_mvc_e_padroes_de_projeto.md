# Módulo 4: Arquitetura MVC e Padrões de Projeto

## Sumário
- [Introdução ao Módulo](#introdução-ao-módulo)
- [6. Arquitetura MVC e Padrões de Projeto](#6-arquitetura-mvc-e-padrões-de-projeto)
  - [6.1 Visão Geral](#61-visão-geral)
  - [6.2 Camada Modelo](#62-camada-modelo)
  - [6.3 Camada de Acesso a Dados (DAO)](#63-camada-de-acesso-a-dados-dao)
  - [6.4 Camada Visão](#64-camada-visão)
  - [6.5 Camada Controle](#65-camada-controle)
- [Conclusão](#conclusão)

## Introdução ao Módulo
Este módulo mostra como organizar aplicações web Java utilizando o padrão Model-View-Controller (MVC) e padrões complementares. A divisão em camadas aumenta a coesão, diminui o acoplamento e facilita testes, manutenção e evolução da aplicação.

## 6. Arquitetura MVC e Padrões de Projeto
O padrão MVC separa a aplicação em três papéis principais: modelo (dados e regras), visão (interface) e controle (fluxo). Ele pode ser combinado com outros padrões, como DAO, Factory e Service, para construir soluções escaláveis. [IMAGEM_MVC_VISAO_GERAL]

### 6.1 Visão Geral
MVC promove modularidade. O controlador coordena interações, atualiza modelos e escolhe a visão apropriada. Vantagens incluem reutilização de componentes, testes independentes e facilidade de implementação de múltiplas interfaces (web, mobile). [IMAGEM_MVC_COMPONENTES]

**Exercício 4:** Qual papel o controlador desempenha no MVC?
 a) Gerenciar apenas a renderização de CSS.

 b) Coordenar a interação entre modelos e visões, definindo o fluxo da aplicação.

 c) Armazenar dados no banco de dados diretamente.

 d) Substituir o servidor de aplicação.

<details>
<summary>Ver Resposta</summary>

**Resposta:** b) Coordenar a interação entre modelos e visões, definindo o fluxo da aplicação.

**Explicação:** O controlador atua como mediador, recebendo requisições, acionando regras de negócio no modelo e selecionando a visão adequada.
</details>

### 6.2 Camada Modelo
A camada modelo representa entidades de domínio e regras de negócio. Classes como `Cliente`, `Pedido` e `Produto` encapsulam invariantes e comportamentos. Pode-se aplicar padrões como Value Object, Service e Factory para organizar responsabilidades. Validações, cálculos e políticas de domínio pertencem ao modelo. [IMAGEM_MVC_MODELO]

```java
public class Pedido {
    private final List<ItemPedido> itens = new ArrayList<>();

    public BigDecimal calcularTotal() {
        return itens.stream()
            .map(ItemPedido::subtotal)
            .reduce(BigDecimal.ZERO, BigDecimal::add);
    }
}
```

**Exercício 4.1:** Qual responsabilidade pertence à camada modelo?
 a) Renderizar HTML para o usuário final.

 b) Gerenciar o roteamento de URLs.

 c) Implementar regras de negócio e invariantes das entidades.

 d) Carregar arquivos CSS dinamicamente.

<details>
<summary>Ver Resposta</summary>

**Resposta:** c) Implementar regras de negócio e invariantes das entidades.

**Explicação:** O modelo concentra a lógica central que mantém a integridade do domínio, garantindo coerência dos dados independentemente da interface.
</details>

### 6.3 Camada de Acesso a Dados (DAO)
O padrão DAO encapsula operações de persistência. Ele abstrai detalhes de SQL, ORMs ou APIs externas, oferecendo métodos CRUD específicos do domínio. Isso desacopla a camada modelo de detalhes de armazenamento, facilitando testes e substituição de tecnologias. [IMAGEM_MVC_DAO]

```java
public interface PedidoDAO {
    void salvar(Pedido pedido);
    Optional<Pedido> buscarPorId(Long id);
    List<Pedido> listarAbertos();
}
```

**Exercício 4.2:** Qual vantagem o padrão DAO oferece?
 a) Permitir que a visão acesse diretamente o banco.

 b) Centralizar regras de layout.

 c) Isolar a lógica de persistência, facilitando mudanças na infraestrutura de dados.

 d) Executar scripts de build automaticamente.

<details>
<summary>Ver Resposta</summary>

**Resposta:** c) Isolar a lógica de persistência, facilitando mudanças na infraestrutura de dados.

**Explicação:** O DAO separa a persistência do restante da aplicação, promovendo testes e substituição de tecnologias sem afetar camadas superiores.
</details>

### 6.4 Camada Visão
A visão apresenta dados ao usuário. Em aplicações Java web, JSPs e tecnologias front-end compõem essa camada. A visão deve ser passiva, recebendo dados prontos para renderização. Padrões como Template View e View Helper evitam duplicação e mantêm responsabilidades organizadas. [IMAGEM_MVC_VISAO]

**Exercício 4.3:** Qual é uma boa prática para a camada visão?
 a) Implementar regras de negócio complexas diretamente na JSP.

 b) Delegar cálculos ao JavaScript sempre que possível.

 c) Manter a visão focada em apresentação, recebendo dados preparados pelo controlador e modelo.

 d) Acessar diretamente o banco de dados para montar tabelas.

<details>
<summary>Ver Resposta</summary>

**Resposta:** c) Manter a visão focada em apresentação, recebendo dados preparados pelo controlador e modelo.

**Explicação:** A visão deve apresentar dados já tratados, evitando lógica de negócio ou persistência para preservar a separação de responsabilidades.
</details>

### 6.5 Camada Controle
A camada controle coordena requisições. Em Java, Servlets atuam como controladores, interpretando parâmetros, validando entradas, chamando serviços e definindo qual visão será renderizada. Padrões como Front Controller e Command organizam fluxos complexos. [IMAGEM_MVC_CONTROLE]

```java
@WebServlet("/pedidos")
public class PedidoController extends HttpServlet {
    private PedidoService service;

    @Override
    public void init() {
        this.service = (PedidoService) getServletContext().getAttribute("pedidoService");
    }

    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        List<Pedido> pedidos = service.listarAbertos();
        req.setAttribute("pedidos", pedidos);
        req.getRequestDispatcher("/WEB-INF/pedidos/lista.jsp").forward(req, resp);
    }
}
```

**Exercício 4.4:** Por que o padrão Front Controller é útil?
 a) Permite que múltiplos Servlets manipulem a mesma URL simultaneamente.

 b) Centraliza o processamento inicial das requisições, aplicando filtros e roteamento consistentes.

 c) Dispensa a necessidade de autenticação.

 d) Impede o uso de filtros HTTP.

<details>
<summary>Ver Resposta</summary>

**Resposta:** b) Centraliza o processamento inicial das requisições, aplicando filtros e roteamento consistentes.

**Explicação:** O Front Controller garante um ponto único para lidar com preocupações transversais, como segurança, logging e roteamento, antes de delegar a controladores específicos.
</details>

## Conclusão
Arquitetura MVC, combinada com padrões como DAO, oferece base robusta para aplicações web escaláveis. Ao separar responsabilidades, torna-se mais simples evoluir a aplicação e integrar novas interfaces ou serviços.

[← Módulo anterior](../teoria/modulo_03_java_server_pages_parte_1.md) | [Próximo módulo →](../teoria/modulo_05_projeto_de_conclusao_de_curso.md) | [← Voltar ao README](../README.md)
