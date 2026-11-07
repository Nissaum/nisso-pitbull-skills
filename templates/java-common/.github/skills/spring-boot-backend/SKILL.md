---
name: spring-boot-backend
description: Analisar, planejar, implementar ou revisar serviços Java 21 com Spring Boot 4.1 em BFF e SRV. Use em tarefas backend Spring, validação, persistência, integração e testes após confirmar versão do build.
---
# Skill: Java 21 / Spring Boot — BFF e SRV

## Pré-voo
Leia `docs/ai-context.md` e `pom.xml`/`build.gradle*`. Confirme patch efetivo Java/Spring Boot, starters, stack MVC/WebFlux, ferramentas de teste e dependências. Não inferir que todas as aplicações têm a mesma configuração.

## Passos
1. Determine a responsabilidade da camada (BFF adapta/orquestra; SRV costuma possuir domínio e persistência, conforme projeto).
2. Identifique 2–5 classes e testes referência, antes de ampliar busca.
3. Confira uso de `jakarta.*` **quando aplicável**, starters Spring Boot 4 e APIs disponíveis; não copiar exemplos de Boot 2/3 cegamente.
4. Valide tratamento de erros, autenticação e autorização, DTOs e contrato.
5. Para SRV, avalie transação, consistência, idempotência, concorrência, integração e migração de dados.
6. Liste testes unitários/integrados/contrato com comandos **existentes**, sem afirmar execução que não ocorreu.
7. Só implemente etapa aprovada, com diff mínimo; dependência/segurança/schema exigem revisão humana.

## Saída
`Build confirmado | classes reais | regra/camada | contrato/erro | mudanças | testes | riscos/bloqueios`.

Não ativar para histórias somente visuais de Angular.
