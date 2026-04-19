# 🏢 Moradas

[![Ruby Style Guide](https://img.shields.io/badge/code_style-rubocop-brightgreen.svg)](https://github.com/rubocop/ruby-style-guide)
[![Clean Architecture](https://img.shields.io/badge/Architecture-Clean_Architecture-blue)](docs/architecture.md)
[![DDD](https://img.shields.io/badge/Design-DDD-orange)](docs/domain_mapping.md)

Uma API robusta para gestão de condomínios, focada em comunicação (mural de avisos) e conformidade (multas e notificações), construída com **Ruby on Rails** sob a ótica de **Clean Architecture** e **Domain-Driven Design (DDD)**.

## 🎯 Objetivo do Projeto
Este projeto foi desenvolvido como um portfólio técnico para demonstrar a aplicação de padrões de arquitetura avançados no ecossistema Ruby. O foco é o desacoplamento total da lógica de negócio em relação ao framework, permitindo escalabilidade e facilidade de testes.

> **Nota:** Este sistema permite que uma única conta (CPF ou CNPJ) possua múltiplos papéis em diferentes condomínios (ex: ser Síndico no Condomínio A e Morador no Condomínio B).

## 🚀 Diferenciais Técnicos

- **Clean Architecture:** Divisão clara entre Entidades de Domínio, Casos de Uso e Adaptadores.
- **DDD (Domain-Driven Design):** Organização do código por contextos delimitados (*Identity*, *Communication*, *Compliance*).
- **Framework as a Detail:** O Rails é utilizado apenas como camada de transporte (API) e persistência, mantendo o "core" do negócio em Ruby Puro (POROs).
- **Repository Pattern:** Abstração total do ActiveRecord para evitar vazamento de lógica de banco para o domínio.
- **Dry-Monads:** Fluxo de controle baseado em objetos de Resultado (`Success` e `Failure`), evitando o uso excessivo de exceções.

## 🗺️ Visão da Arquitetura

O projeto segue a regra de dependência, onde as camadas internas não conhecem as externas:

1.  **Entities:** Regras de negócio globais (ex: o que valida um CPF).
2.  **Use Cases:** Regras de aplicação (ex: o passo-a-passo para emitir uma multa).
3.  **Adapters:** Controllers, Repositories e Presenters.
4.  **Frameworks:** Rails, Postgres, Sidekiq.



## 🛠️ Tecnologias Utilizadas

- **Linguagem:** Ruby 3.x
- **Framework:** Ruby on Rails 8 (API Mode)
- **Banco de Dados:** PostgreSQL

## 📂 Documentação Detalhada

Para entender as decisões de design e o roadmap do projeto, consulte:

1.  [**Documento de Arquitetura**](docs/architecture.md): Detalhes sobre a estrutura de pastas e padrões de código.
2.  [**Mapeamento de Domínio**](docs/domain_mapping.md): Explicação dos contextos e entidades.
3.  [**Roadmap de Desenvolvimento**](docs/product_roadmap.md): Status das funcionalidades e plano de execução.
4.  [**PRD (Produto)**](docs/prd.md): Visão de negócio e regras de usuário.

---

## 🏗️ Como Rodar

```bash
# Clone o repositório
git clone git@github.com:tota1099/moradas.git

# Instale as dependências
bundle install

# Setup do banco
rails db:prepare

# Rode os testes (o coração da aplicação)
bundle exec rspec
