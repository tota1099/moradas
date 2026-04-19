# 🗺 Mapeamento de Domínios

Dividimos a aplicação em contextos delimitados para garantir que cada parte do sistema tenha uma responsabilidade única e clara.

## 1. Contexto: Identity
**Significado:** É o guardião da identidade e dos acessos. Ele não se importa com multas ou avisos, apenas com "quem é você" e "o que você pode fazer aqui".

- **Account:** Representa o indivíduo ou empresa.
  - Atributos: `name`, `identifier` (CPF/CNPJ), `email`.
- **Condominium:** A unidade organizacional.
  - Atributos: `name`, `cnpj`, `address`.
- **Membership:** A relação entre Account e Condominium.
  - Atributos: `role` (sindico, morador), `status` (ativo, inativo).
- **Unit:** Espaço físico (Apto/Casa) dentro de um Condominium.

## 2. Contexto: Communication
**Significado:** Gere a troca de informações oficiais. Sua principal regra é a visibilidade e transparência.

- **Announcement (Aviso):** Mensagem oficial enviada pelo síndico.
  - Atributos: `title`, `content`, `priority`, `published_at`.
- **Comment:** Feedback dos moradores em avisos (quando permitido).

## 3. Contexto: Compliance
**Significado:** Garante que as regras do regimento interno sejam cumpridas. Foca em privacidade e registro histórico.

- **Fine (Multa/Notificação):** Registro de uma infração.
  - Atributos: `description`, `amount`, `issued_date`, `evidence_links`.
  - **Regra Crucial:** Uma `Fine` só é visível para o síndico emissor e para a `Account` que a recebeu.

---
