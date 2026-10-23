# Copilot — BFF / Squad Pitbull

**Stack informada:** Java 21, Spring Boot 4.1 (confirmar versão efetiva e build em cada repo).
**Responsabilidade:** camada de borda e orquestração entre FED e SRV.

- Seguir arquitetura, DTOs, controllers/resolvers e clientes existentes. Controllers finos; separar orquestração de regra de domínio do SRV.
- Preservar códigos HTTP, contratos de erro, segurança, autorização, correlação e observabilidade.
- Verificar stack de MVC/WebFlux, biblioteca HTTP e políticas de retry/timeout; não inventar.
- Usar APIs `jakarta.*` apropriadas (ex.: validation e servlet) **conforme dependências presentes** em Boot 4; não copiar exemplos legados `javax.servlet`/`javax.validation`.
- Confirmar starters de Boot 4 no build; evitar configuração antiga por analogia com Boot 2/3.
- Tratar mudanças de contrato com estratégia de compatibilidade FED↔BFF↔SRV.
- Testar mapeamento, erros de dependência, acesso negado e timeouts quando relevantes.
- Diff mínimo; não trocar dependências, segurança ou infraestrutura sem aprovação.
- Não afirmar build/testes aprovados sem execução verificável.
