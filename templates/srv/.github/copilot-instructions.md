# Copilot — SRV / Squad Pitbull

**Stack informada:** Java 21 / Spring Boot 4.1 (verificar patch, build e dependências reais).
**Responsabilidade:** regras de domínio, persistência e integrações conforme arquitetura do projeto.

- Manter regras de negócio na camada responsável e contratos esperados pelo BFF.
- Avaliar transações, idempotência, concorrência, consistência, falhas e efeitos colaterais.
- Usar APIs `jakarta.*` conforme os módulos efetivos em Boot 4 (ex.: validation/persistence); não copiar imports Java EE legados quando incompatíveis.
- Confirmar starters e anotações no pom/Gradle; não presumir equivalência direta com Boot 2/3.
- Seguir padrões de serviços, adapters, repositories, DTOs, exceptions e logs existentes.
- Cobrir casos positivo, negativo, limite e integração no nível proporcional ao risco.
- Não mudar migrações, filas, cache, contratos, segurança ou schema sem revisão explícita.
- Não adicionar dependências nem alterar fora da história; não desabilitar testes.
- Validar resultados verdadeiros de build/teste; não gerar ou incluir PII/segredos.
