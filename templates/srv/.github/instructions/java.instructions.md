---
applyTo: "**/*.java"
---
# Java 21 / Spring Boot 4.1 — SRV
- Respeitar Java 21 e versões no build; não usar APIs posteriores.
- Usar pacotes `jakarta.persistence`, `jakarta.validation` e equivalentes quando presentes e aplicáveis.
- Verificar starters do Boot 4 existentes; não copiar recipes de Boot 3 sem validação.
- Seguir padrão real de services/repositories/controllers/adapters e testes.
- Avaliar nulos, limites, transações, concorrência, idempotência e autorização.
- Exigir revisão especial para migrations, dados, filas, cache e contratos públicos.
- Testes unitários/integrados conforme arquitetura; não mascarar bugs só com mocks.
