# Módulo 1: Aplicação Web e Tecnologias do Lado Cliente

## Sumário
- [Introdução ao Módulo](#introdução-ao-módulo)
- [1. Aplicação Web](#1-aplicação-web)
  - [1.1 Arquitetura e Funcionamento](#11-arquitetura-e-funcionamento)
  - [1.2 Cliente Web](#12-cliente-web)
  - [1.3 Servidor Web](#13-servidor-web)
  - [1.4 Protocolo HTTP](#14-protocolo-http)
- [2. Tecnologias do Lado Cliente](#2-tecnologias-do-lado-cliente)
  - [2.1 Marcação XHTML](#21-marcação-xhtml)
  - [2.2 Estilos CSS](#22-estilos-css)
  - [2.3 Scripts JavaScript](#23-scripts-javascript)
- [Conclusão](#conclusão)

## Introdução ao Módulo
Este módulo apresenta os fundamentos das aplicações web modernas, explorando a comunicação cliente-servidor, os principais componentes de uma aplicação na web e as tecnologias usadas no lado do cliente para construir interfaces ricas e responsivas.

## 1. Aplicação Web
As aplicações web são sistemas acessados via navegador que dependem de um fluxo contínuo de comunicação entre clientes e servidores conectados pela internet ou redes internas. [IMAGEM_APLICACAO_WEB_INTERACAO]

### 1.1 Arquitetura e Funcionamento
Uma aplicação web segue uma arquitetura distribuída que separa responsabilidades entre camadas. O cliente envia uma requisição HTTP para o servidor, que processa a solicitação, interage com bancos de dados ou serviços externos e devolve uma resposta, normalmente em HTML, JSON ou XML. Esse ciclo acontece rapidamente e de forma repetida, permitindo interatividade contínua. Arquiteturas multicamadas, como a clássica divisão em apresentação, lógica e dados, oferecem escalabilidade e manutenção simplificada.

**Exercício 1:** Qual é a principal característica da arquitetura de aplicações web?
 a) Todo o processamento ocorre exclusivamente no cliente.

 b) A aplicação é executada apenas em um servidor monolítico sem camadas.

 c) A separação de responsabilidades entre cliente, servidor e dados garante escalabilidade e manutenção.

 d) O servidor não precisa conhecer a origem da requisição.

<details>
<summary>Ver Resposta</summary>

**Resposta:** c) A separação de responsabilidades entre cliente, servidor e dados garante escalabilidade e manutenção.

**Explicação:** Arquiteturas em camadas permitem dividir responsabilidades, facilitando escalabilidade, segurança e manutenção independente de cada camada.
</details>

### 1.2 Cliente Web
O cliente web é geralmente um navegador que renderiza HTML, CSS e executa JavaScript. Ele traduz respostas do servidor em interfaces visuais e gerencia interações do usuário. Os navegadores também oferecem APIs para armazenamento local, comunicação em tempo real e segurança. Os clientes modernos implementam engines de renderização e JavaScript altamente otimizadas, garantindo experiências consistentes.

**Exercício 1.1:** Qual é uma responsabilidade típica do cliente web?
 a) Executar consultas SQL diretamente em bancos de dados do servidor.

 b) Renderizar o HTML e aplicar estilos CSS provenientes do servidor.

 c) Gerenciar a persistência completa dos dados corporativos.

 d) Evitar qualquer execução de scripts para proteger o usuário.

<details>
<summary>Ver Resposta</summary>

**Resposta:** b) Renderizar o HTML e aplicar estilos CSS provenientes do servidor.

**Explicação:** O cliente recebe a resposta do servidor e a transforma na interface visual, aplicando estilos e executando scripts para permitir interatividade.
</details>

### 1.3 Servidor Web
O servidor web recebe solicitações, executa regras de negócio, acessa dados e envia respostas estruturadas. Ele pode ser composto por múltiplos serviços coordenados, como balanceadores de carga, servidores de aplicação e bancos de dados. A hospedagem pode ocorrer em data centers próprios, provedores cloud ou ambientes híbridos. A segurança e o desempenho do servidor dependem de configurações adequadas, monitoramento contínuo e atualizações constantes. [IMAGEM_SERVIDOR_WEB_FLUXO]

**Exercício 1.2:** Qual é uma função essencial de um servidor web?
 a) Garantir que o navegador renderize o HTML de maneira idêntica em qualquer dispositivo.

 b) Processar requisições, aplicar regras de negócio e retornar respostas apropriadas ao cliente.

 c) Substituir o navegador na execução de scripts JavaScript.

 d) Assumir o papel de banco de dados principal em todas as soluções.

<details>
<summary>Ver Resposta</summary>

**Resposta:** b) Processar requisições, aplicar regras de negócio e retornar respostas apropriadas ao cliente.

**Explicação:** O servidor web é o componente que processa a lógica da aplicação, acessa dados e envia respostas ao cliente para renderização.
</details>

### 1.4 Protocolo HTTP
HTTP é o protocolo de comunicação base entre cliente e servidor. Ele define métodos (GET, POST, PUT, DELETE), códigos de status (200, 404, 500) e cabeçalhos que controlam cache, autenticação e conteúdo. A comunicação é stateless, ou seja, cada requisição é independente. Para manter estado, usam-se cookies, tokens ou sessões. A transição para HTTPS adiciona criptografia TLS, garantindo confidencialidade e integridade. [IMAGEM_HTTP_CICLO]

**Exercício 1.3:** Qual afirmação descreve corretamente o protocolo HTTP?
 a) HTTP mantém estado automaticamente entre requisições sem mecanismos adicionais.

 b) O método GET é usado para enviar dados sensíveis no corpo da requisição.

 c) HTTP define métodos, cabeçalhos e códigos de status que estruturam a comunicação cliente-servidor.

 d) HTTPS remove a necessidade de certificados digitais.

<details>
<summary>Ver Resposta</summary>

**Resposta:** c) HTTP define métodos, cabeçalhos e códigos de status que estruturam a comunicação cliente-servidor.

**Explicação:** HTTP estabelece regras para troca de mensagens. Para manter estado, mecanismos adicionais são necessários e o HTTPS adiciona criptografia via certificados.
</details>

## 2. Tecnologias do Lado Cliente
O desenvolvimento no lado cliente combina marcação semântica, estilos avançados e scripts que tornam a experiência dinâmica e acessível.

### 2.1 Marcação XHTML
XHTML é uma reformulação do HTML com regras mais estritas baseadas em XML. Exige tags bem formadas, atributos em minúsculas e fechamento explícito. O uso de XHTML promove consistência e interoperabilidade. Um documento típico começa com uma declaração `<?xml?>` seguida de `<!DOCTYPE>`. [IMAGEM_XHTML_ESTRUTURA]

```xhtml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
  <head>
    <title>Exemplo XHTML</title>
  </head>
  <body>
    <h1>Documento Bem Formado</h1>
    <p>Todo elemento possui fechamento explícito.</p>
  </body>
</html>
```

**Exercício 1.4:** Qual regra distingue XHTML do HTML tradicional?
 a) Permitir que atributos fiquem sem valores definidos.

 b) Aceitar tags abertas sem fechamento correspondente.

 c) Exigir que todo elemento seja bem formado e que atributos sejam escritos em minúsculas.

 d) Impedir o uso de folhas de estilo CSS.

<details>
<summary>Ver Resposta</summary>

**Resposta:** c) Exigir que todo elemento seja bem formado e que atributos sejam escritos em minúsculas.

**Explicação:** XHTML segue as regras de XML, demandando sintaxe estrita para garantir interoperabilidade entre agentes de usuário e ferramentas automatizadas.
</details>

### 2.2 Estilos CSS
CSS controla a apresentação visual, desde cores até layouts responsivos. O modelo de caixa define como margens, bordas e preenchimento compõem cada elemento. Técnicas modernas como Flexbox e Grid permitem layouts adaptáveis. O uso de pré-processadores (Sass, Less) e metodologias (BEM, SMACSS) melhora a escalabilidade. [IMAGEM_CSS_LAYOUT]

```css
.card {
  display: grid;
  grid-template-columns: 1fr 2fr;
  gap: 1rem;
  padding: 1.5rem;
  border-radius: 8px;
  background: linear-gradient(135deg, #1f3b4d, #4f8fb8);
  color: #fff;
}
```

**Exercício 1.5:** Qual técnica CSS cria layouts bidimensionais com linhas e colunas controladas?
 a) Box Model

 b) Flexbox

 c) CSS Grid

 d) Float

<details>
<summary>Ver Resposta</summary>

**Resposta:** c) CSS Grid

**Explicação:** CSS Grid fornece controle bidimensional sobre linhas e colunas, facilitando layouts complexos e responsivos sem hacks baseados em floats.
</details>

### 2.3 Scripts JavaScript
JavaScript manipula a árvore DOM, responde a eventos e integra APIs. Técnicas modernas incluem uso de módulos ES, async/await e frameworks como React e Vue. Validações de formulários, requisições AJAX e interações acessíveis dependem de JavaScript bem estruturado. Boas práticas incluem evitar mutações globais, usar ferramentas de build e garantir acessibilidade. [IMAGEM_JAVASCRIPT_DOM]

```javascript
const form = document.querySelector('form');

form.addEventListener('submit', async (event) => {
  event.preventDefault();
  const data = new FormData(form);
  const response = await fetch('/api/contato', {
    method: 'POST',
    body: data,
  });
  const resultado = await response.json();
  document.querySelector('#status').textContent = resultado.mensagem;
});
```

**Exercício 1.6:** Qual prática ajuda a manter código JavaScript modular e reutilizável?
 a) Manipular diretamente variáveis globais compartilhadas por todo o aplicativo.

 b) Usar módulos ES6 para encapsular funcionalidades e importar apenas o necessário.

 c) Evitar o uso de qualquer ferramenta de build ou linting.

 d) Criar funções com efeitos colaterais imprevisíveis.

<details>
<summary>Ver Resposta</summary>

**Resposta:** b) Usar módulos ES6 para encapsular funcionalidades e importar apenas o necessário.

**Explicação:** Módulos ES6 organizam o código, reduzem dependências globais e promovem reutilização, favorecendo manutenção e testes.
</details>

## Conclusão
A compreensão da arquitetura de aplicações web e das tecnologias de front-end é a base para construir soluções escaláveis, acessíveis e seguras. Esses conceitos serão retomados ao longo do curso, com foco na integração com tecnologias server-side em Java.

[Próximo módulo →](../teoria/modulo_02_servlets.md) | [← Voltar ao README](../README.md)
