# 🚀 Plano de Desenvolvimento (Roadmap)

Este roadmap está dividido em fases incrementais, focando primeiro no robustecimento do Backend.

## Fase 1: Fundação (The Foundation)
- [ ] Setup Rails 8 API-only.
- [ ] Implementação da estrutura de pastas `app/domain`.
- [ ] Configuração de RSpec e Dry-Monads (para tratamento de retornos Success/Failure).
- [ ] Criação do Value Object `Identifier` (validação de CPF/CNPJ).

## Fase 2: Gestão de Identidade (Identity)
- [ ] **Use Case:** `RegisterAccount` (Criar CPF/CNPJ no sistema).
- [ ] **Use Case:** `CreateCondominium` (Apenas Admin).
- [ ] **Use Case:** `AssignRole` (Vincular conta a um condomínio como Síndico ou Morador).
- [ ] Testes unitários de autorização (ex: "Um morador não pode promover outro").

## Fase 3: Comunicação (Communication)
- [ ] **Use Case:** `PostAnnouncement`.
  - Regra: Validar se o autor possui o Membership de Síndico no condomínio alvo.
- [ ] **Use Case:** `ListMural`.
  - Regra: Filtrar apenas avisos ativos do condomínio do usuário logado.

## Fase 4: Conformidade (Compliance)
- [ ] **Use Case:** `IssueFine`.
  - Regra: Validar se autor (Síndico) e alvo (Morador) pertencem ao mesmo Condomínio.
- [ ] **Use Case:** `ListMyFines`.
  - Regra: Garantir que um morador nunca veja multas de outro morador.

## Fase 5: Exposição (API & Integrations)
- [ ] Implementação dos Controllers mapeando para os Use Cases.
- [ ] Setup de Autenticação JWT.
- [ ] Documentação de endpoints (Swagger/OpenAPI).

---
