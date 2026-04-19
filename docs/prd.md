# 📄 PRD - Documento de Requisitos do Produto

**Projeto:** Moradas
**Status:** Em Planejamento

---

## 1. Visão Geral do Produto
O **Moradas** é uma plataforma de gestão interna para condomínios. Diferente de grandes ERPs de administração financeira, o foco aqui é a **vivência e conformidade**. O sistema visa substituir murais de papel e grupos informais de mensagens por uma trilha oficial de comunicação e registros de notificações/multas.

## 2. Personas (Atores)
- **Admin Geral:** Desenvolvedor ou operador do sistema que cadastra condomínios e síndicos iniciais.
- **Síndico:** Pode ser uma Pessoa Física (CPF) ou Jurídica (CNPJ). Tem poder de gestão sobre o mural e emissão de multas.
- **Morador:** Pessoa Física que reside em uma unidade e consome as informações e notificações.
  - *Nota: Uma mesma pessoa pode ser Síndico em um condomínio e Morador em outro, utilizando a mesma conta.*

## 3. Requisitos Funcionais (Escopo do MVP)

### RF01: Gestão de Identidade Única
O sistema deve permitir que uma conta seja identificada por um CPF ou CNPJ único. 
- **Critério de aceite:** Não pode haver dois cadastros com o mesmo identificador.

### RF02: Gestão de Vínculos (Multitenancy)
O sistema deve isolar os dados por condomínio, mas permitir que o usuário transite entre eles.
- **Critério de aceite:** Ao logar, o usuário deve ser capaz de listar em quais condomínios ele possui vínculo e qual o seu papel (Role) em cada um.

### RF03: Mural de Avisos (Comunicação)
O síndico deve publicar comunicados oficiais para todos os moradores do condomínio específico.
- **Critério de aceite:** - Somente usuários com papel `sindico` podem criar avisos.
  - Moradores só podem ver avisos do condomínio onde possuem vínculo ativo.

### RF04: Gestão de Multas e Notificações (Conformidade)
Registro formal de infrações ao regimento interno.
- **Critério de aceite:**
  - O síndico emite a multa para uma conta específica.
  - A multa deve conter descrição, data e opcionalmente um valor.
  - **Privacidade:** Um morador "A" jamais pode ter acesso às multas aplicadas ao morador "B".

## 4. Requisitos Não Funcionais
- **Arquitetura:** Deve seguir Clean Architecture para facilitar a troca de banco de dados ou interface no futuro.
- **Segurança:** As APIs devem ser protegidas (autenticação JWT).
- **Escalabilidade:** A estrutura de dados deve suportar o crescimento do número de condomínios sem degradação de performance (uso de índices corretos em `condominium_id`).
- **Testabilidade:** A lógica de negócio (Use Cases) deve ter 100% de cobertura de testes unitários.

## 5. Casos de Uso (Prioritários)

| ID | Caso de Uso | Ator | Descrição |
| :--- | :--- | :--- | :--- |
| UC01 | Registrar Conta | Admin | Cria um novo usuário baseado em CPF/CNPJ. |
| UC02 | Criar Aviso | Síndico | Publica uma mensagem no mural do condomínio. |
| UC03 | Consultar Mural | Morador | Lista avisos recentes do condomínio vinculado. |
| UC04 | Aplicar Multa | Síndico | Registra uma infração para um morador específico. |
| UC05 | Ver Minhas Multas | Morador | Lista o histórico de penalidades recebidas. |

## 6. O que NÃO faremos (Out of Scope)
- Gestão de pagamentos, boletos ou fluxo de caixa.
- Reserva de áreas comuns.
- Cadastro público de usuários (self-service) - por enquanto, o Admin/Síndico cadastra os moradores.

---
