# 🏛 Documento de Arquitetura

Este projeto utiliza **Clean Architecture** e princípios de **DDD (Domain-Driven Design)** para isolar a lógica de negócio das ferramentas de infraestrutura (Rails, Banco de Dados, APIs externas).

## 🗂 Estrutura de Pastas

Diferente do padrão `app/models`, `app/controllers` do Rails, organizamos a lógica em:

- `domain/entities/`: Objetos puros (POROs) que representam conceitos de negócio.
- `domain/use_cases/`: Classes que executam uma única ação de negócio (Interactors).
- `repositories/`: Camada que traduz objetos de domínio para persistência (ActiveRecord).
- `controllers/api/`: Adaptadores de entrada que apenas delegam para os Use Cases.

## 🛠 Decisões de Engenharia

### Desacoplamento do Framework
O Ruby on Rails é tratado como um **detalhe de implementação**. O `ActiveRecord` não deve vazar para dentro dos Use Cases. Isso permite que a lógica de negócio seja testada sem carregar todo o framework, tornando os testes extremamente rápidos.

### Ausência de Tipagem Estática (No Sorbet)
Optamos por não utilizar Sorbet neste momento para focar na **expressividade do Ruby** e no **Duck Typing**. A integridade do sistema é garantida por:
1. **Contratos de Entrada:** Validação de parâmetros rigorosa no início de cada Use Case.
2. **Testes Automatizados:** Cobertura de testes unitários com RSpec focada no comportamento.

### Comunicação entre Contextos
Os contextos não se tocam diretamente no banco de dados. Se o contexto de `Compliance` precisa saber se um usuário é Síndico, ele consulta uma interface do contexto de `Identity`.

---
