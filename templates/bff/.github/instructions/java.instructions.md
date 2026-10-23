---
applyTo: "**/*.java"
---
# Java 21 / Spring Boot 4.1 — BFF
- Use Java 21 conforme build; não aproveitar tarefa para migrar estilo/arquitetura.
- Validar módulos/starter e versões realmente disponíveis; não presumir configuração de Boot 3.
- Para interfaces Jakarta (quando presentes), usar `jakarta.*` no lugar de pacotes Java EE legados.
- Respeitar a stack MVC ou WebFlux, cliente HTTP, resilience, observabilidade e segurança existentes.
- DTOs explícitos, validação e semântica de erros; preservar contrato público.
- Testes JUnit/Mockito apenas se forem ferramentas efetivamente adotadas no projeto.
- Não alterar contratos, autorização, dados sensíveis ou dependências fora do plano aprovado.
