# 🔧 SGOM – Sistema de Gestão de Oficina Mecânica 👨‍💻

> [!NOTE]
> O SGOM digitaliza o fluxo completo de uma oficina mecânica — do agendamento à entrega do veículo — centralizando ordens de serviço, orçamentos, estoque de peças e pagamentos em uma única aplicação web.

<table>
  <tr>
    <td width="800px">
      <div align="justify">
        O <b>SGOM</b> é um sistema web para gestão de oficinas mecânicas de pequeno e médio porte. Ele organiza o ciclo de atendimento em torno da <b>Ordem de Serviço (OS)</b>: cadastro de clientes e veículos, agendamento, abertura de OS com checklist de entrada, elaboração de orçamento com serviços e peças, aprovação pelo cliente, execução com baixa automática de estoque, pagamento via gateway e encerramento com entrega do veículo. Este repositório contém a <i>documentação de projeto</i> (Trabalho 2 da disciplina Projeto de Software), incluindo todos os diagramas UML elaborados em <b>PlantUML</b>.
      </div>
    </td>
    <td>
      <div align="center">
        🔧🚗
      </div>
    </td>
  </tr>
</table>

---

## 🚧 Status do Projeto

[![Versão](https://img.shields.io/badge/Versão-v1.0.0-blue?style=for-the-badge)]() ![Java](https://img.shields.io/badge/Java-21-007ec6?style=for-the-badge&logo=openjdk&logoColor=white) ![Spring Boot](https://img.shields.io/badge/Spring_Boot-3.x-007ec6?style=for-the-badge&logo=springboot&logoColor=white) ![React](https://img.shields.io/badge/React-18-007ec6?style=for-the-badge&logo=react&logoColor=white) ![TypeScript](https://img.shields.io/badge/TypeScript-5.x-007ec6?style=for-the-badge&logo=typescript&logoColor=white) ![Vite](https://img.shields.io/badge/Vite-5.x-007ec6?style=for-the-badge&logo=vite&logoColor=white) ![PostgreSQL](https://img.shields.io/badge/PostgreSQL-16-007ec6?style=for-the-badge&logo=postgresql&logoColor=white) ![Status](https://img.shields.io/badge/Status-Documentação%20de%20Projeto-yellow?style=for-the-badge)

> ⚠️ **Escopo do trabalho:** apenas projeto / diagramação / arquitetura. Não há código de implementação neste repositório.

---

## 📚 Índice
- [Links Úteis](#-links-úteis)
- [Sobre o Projeto](#-sobre-o-projeto)
- [Funcionalidades Principais](#-funcionalidades-principais)
- [Tecnologias Utilizadas](#-tecnologias-utilizadas)
- [Arquitetura](#-arquitetura)
- [Instalação e Execução](#-instalação-e-execução)
- [Deploy](#-deploy)
- [Estrutura de Pastas](#-estrutura-de-pastas)
- [Demonstração](#-demonstração)
- [Testes](#-testes)
- [Documentações utilizadas](#-documentações-utilizadas)
- [Autores](#-autores)
- [Contribuição](#-contribuição)
- [Agradecimentos](#-agradecimentos)
- [Licença](#-licença)

---

## 🔗 Links Úteis
* 🌐 **Demo Online:** *(não aplicável — projeto sem implementação)*
* 📖 **Documentação:** [Documentação de Projeto (Word)](./docs/Documentacao_de_Projeto_SGOM.docx)
* 🧩 **Diagramas PlantUML:** [/diagramas](./diagramas)
* 🖥️ **Editor PlantUML Online:** [plantuml.com](https://plantuml.com/)

---

## 📝 Sobre o Projeto

Oficinas mecânicas de pequeno porte ainda operam, em grande parte, com fichas de papel e planilhas: orçamentos se perdem, o estoque de peças diverge do real e o cliente não tem visibilidade do andamento do serviço. O SGOM nasce nesse contexto acadêmico (disciplina **Projeto de Software**) para projetar uma solução que resolva essas dores.

- **Por que existe:** eliminar retrabalho e perda de informação no fluxo de atendimento da oficina.
- **Problema que resolve:** controle confiável de OS, orçamento, estoque e pagamento em um único lugar.
- **Contexto:** acadêmico, com regras de negócio realistas de uma oficina mecânica.
- **Onde pode ser usado:** oficinas independentes, autocenters e concessionárias de pequeno porte.

O valor central é o **ciclo de vida rastreável da OS** (Aberta → Em Diagnóstico → Aguardando Aprovação → Aprovada → Em Execução → Finalizada → Entregue), garantindo que nenhum serviço seja executado sem orçamento aprovado e que toda peça consumida tenha baixa em estoque.

---

## ✨ Funcionalidades Principais

- 🔐 **Autenticação Segura:** login com perfis Atendente, Mecânico e Gerente (JWT).
- 👥 **Cadastro de Clientes e Veículos:** CRUD completo com histórico por veículo.
- 📅 **Agendamento de Atendimentos:** agenda com confirmação e controle de não comparecimento.
- 🧾 **Ordem de Serviço:** abertura com relato do problema e checklist de entrada.
- 💰 **Orçamento Digital:** composição de serviços e peças com verificação de estoque e aprovação pelo cliente.
- 🔩 **Gestão de Estoque de Peças:** baixa automática na execução, movimentações e alerta de estoque mínimo.
- 💳 **Pagamentos:** integração com gateway (crédito, débito e Pix) e emissão de comprovante.
- 📊 **Relatórios Gerenciais:** faturamento por período, OS por status e giro de estoque.

---

## 🛠 Tecnologias Utilizadas

### 💻 Front-end
* **Framework/Biblioteca:** React 18
* **Linguagem/Superset:** TypeScript 5
* **Estilização:** Tailwind CSS + shadcn/ui
* **Gerenciamento de Estado:** Context API + TanStack Query
* **Build Tool:** Vite 5

### 🖥️ Back-end
* **Linguagem/Runtime:** Java 21 (JDK)
* **Framework:** Spring Boot 3.x
* **Banco de Dados:** PostgreSQL 16
* **ORM / Query Builder:** Hibernate / Spring Data JPA
* **Autenticação:** Spring Security + JWT

### ⚙️ Infraestrutura & DevOps
* **Containerização:** Docker e Docker Compose
* **Cloud:** VPS (back-end + banco) e Vercel (front-end)
* **CI/CD:** GitHub Actions

### 🧩 Modelagem
* **Diagramas:** PlantUML (todos os códigos-fonte em [/diagramas](./diagramas))

---

## 🏗 Arquitetura

O SGOM segue uma **arquitetura em camadas** no estilo cliente-servidor:

- **Apresentação (Controllers REST):** expõe a API JSON consumida pela SPA.
- **Aplicação (Services):** concentra as regras de negócio — transições de estado da OS, cálculo de orçamento, baixa de estoque, orquestração do pagamento.
- **Persistência (Repositories / Spring Data JPA):** acesso ao PostgreSQL.
- **Integração:** componente dedicado para comunicação com o gateway de pagamento externo.

**Padrões adotados:** Repository, Service Layer, DTOs, State (ciclo de vida da OS) e injeção de dependências.

**Decisões e trade-offs:** optou-se por um **monólito modular** (em vez de microsserviços) pela simplicidade operacional adequada ao porte do domínio; a API stateless com JWT facilita o deploy horizontal futuro.

### Exemplos de diagramas

| Diagrama | Arquivo PlantUML |
| :--- | :--- |
| Casos de Uso | [`01-casos-de-uso.puml`](./diagramas/01-casos-de-uso.puml) |
| DSS (UC-03, UC-04, UC-07) | [`02`](./diagramas/02-dss-uc03.puml) · [`03`](./diagramas/03-dss-uc04.puml) · [`04`](./diagramas/04-dss-uc07.puml) |
| Arquitetura | [`05-arquitetura.puml`](./diagramas/05-arquitetura.puml) |
| Componentes / Implantação | [`06`](./diagramas/06-componentes.puml) · [`07`](./diagramas/07-implantacao.puml) |
| Classes | [`08-classes.puml`](./diagramas/08-classes.puml) |
| Sequência (projeto) | [`09`](./diagramas/09-sequencia-uc03.puml) · [`10`](./diagramas/10-sequencia-uc04.puml) · [`11`](./diagramas/11-sequencia-uc07.puml) |
| Estados (OS / Agendamento) | [`12`](./diagramas/12-estados-os.puml) · [`13`](./diagramas/13-estados-agendamento.puml) |
| Comunicação | [`14`](./diagramas/14-comunicacao-uc03.puml) · [`15`](./diagramas/15-comunicacao-uc07.puml) |
| Modelo de Dados (DER) | [`16-modelo-dados.puml`](./diagramas/16-modelo-dados.puml) |

---

## 🔧 Instalação e Execução

> ⚠️ Seção ilustrativa: descreve como o sistema **seria** executado caso implementado.

### Pré-requisitos
* **Java JDK:** 21 ou superior
* **Node.js:** v20 LTS ou superior
* **Docker / Docker Compose**
* **Gerenciador de Pacotes:** npm

### 🔑 Variáveis de Ambiente

#### 1️⃣ Back-end (Spring Boot)
```properties
SPRING_DATASOURCE_URL=jdbc:postgresql://localhost:5432/sgom
SPRING_DATASOURCE_USERNAME=sgom
SPRING_DATASOURCE_PASSWORD=sgom
JWT_SECRET=troque-este-segredo
GATEWAY_PAGAMENTO_URL=https://api.gateway-exemplo.com
GATEWAY_PAGAMENTO_TOKEN=token-fic-ticio
```

#### 2️⃣ Front-end (React, Vite)
```env
VITE_API_BASE_URL=http://localhost:8080/api
```

### 📦 Instalação de Dependências

#### Front-end (React)
```bash
cd frontend
npm install
```

#### Back-end (Spring Boot)
```bash
cd backend
./mvnw clean install
```

### 🗄 Inicialização do Banco de Dados (PostgreSQL)
```bash
docker run -d --name postgres-sgom -e POSTGRES_DB=sgom \
  -e POSTGRES_USER=sgom -e POSTGRES_PASSWORD=sgom -p 5432:5432 postgres:16
```

### ▶️ Como Executar a Aplicação

#### Terminal 1: Back-end (Spring Boot)
```bash
cd backend && ./mvnw spring-boot:run
```

#### Terminal 2: Front-end (React, Vite)
```bash
cd frontend && npm run dev
```

#### 🐳 Execução Local Completa com Docker Compose
```bash
docker compose up --build
```

---

## 🚀 Deploy

- **Front-end:** build estático (`npm run build`) publicado na Vercel.
- **Back-end + Banco:** containers Docker (`backend-sgom`, `postgres-sgom`) em VPS, atrás de nginx com TLS.
- **CI/CD:** GitHub Actions executa build, testes e publicação das imagens a cada push na `main`.

---

## 📁 Estrutura de Pastas

```text
sgom/
├── docs/
│   └── Documentacao_de_Projeto_SGOM.docx
├── diagramas/
│   ├── 01-casos-de-uso.puml
│   ├── 02-dss-uc03.puml
│   ├── ...
│   ├── 16-modelo-dados.puml
│   └── png/                # diagramas renderizados
└── README.md
```

---

## 🎬 Demonstração

### 💻 Aplicação Web
*(não aplicável — o escopo do trabalho é exclusivamente o projeto/diagramação; as telas seriam: painel de OS em Kanban por status, formulário de orçamento e dashboard gerencial)*

### 🖥️ Exemplo de saída no Terminal (para Back-end, API, CLI)
```text
2026-06-07T10:00:00  INFO  SgomApplication : Started SgomApplication in 4.2 seconds
2026-06-07T10:01:12  INFO  OrdemServicoService : OS 2026-000123 criada (status=ABERTA)
```

---

## 🧪 Testes

Estratégia prevista:
- **Unitários (JUnit 5 + Mockito):** regras de negócio dos Services (transições de StatusOS, cálculo de orçamento, baixa de estoque).
- **Integração (Spring Boot Test + Testcontainers):** repositórios contra PostgreSQL real em container.
- **Front-end (Vitest + React Testing Library):** componentes críticos de formulário de OS e orçamento.

---

## 📖 Documentações utilizadas

* [PlantUML](https://plantuml.com/)
* [Spring Boot Reference](https://docs.spring.io/spring-boot/index.html)
* [Spring Data JPA](https://docs.spring.io/spring-data/jpa/reference/)
* [React](https://react.dev/)
* [Vite](https://vite.dev/)
* [PostgreSQL 16](https://www.postgresql.org/docs/16/)
* Larman, C. *Utilizando UML e Padrões* (contratos de operação e DSS)

---

## 👥 Autores

| Aluno | Curso | Instituição |
| :--- | :--- | :--- |
| **Vinicius Oliveira Ramos** | Engenharia de Software | PUC Minas |

Trabalho **individual** da disciplina **Projeto de Software**.

---

## 🤝 Contribuição

Por se tratar de um trabalho acadêmico individual, contribuições externas não são aceitas. Sugestões podem ser registradas via *Issues*.

---

## 🙏 Agradecimentos

Ao professor da disciplina de Projeto de Software pelo template de documentação e pelas orientações de modelagem.

---

## 📄 Licença

Este projeto é de uso acadêmico. Distribuído sob a licença **MIT** para fins de estudo.
