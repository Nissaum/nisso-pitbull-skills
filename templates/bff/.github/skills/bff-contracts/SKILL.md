---
name: bff-contracts
description: Refinar e revisar contratos entre FED Angular, BFF e SRV, incluindo DTOs, erros HTTP, autorização, timeout e compatibilidade de rollout. Use quando a história atravessa uma fronteira de API.
---
# Skill: Contratos e fronteiras BFF

1. Identifique endpoints/esquemas reais ou marque como NÃO INSPECIONADO; não crie contrato por suposição.
2. Monte matriz: produtor, consumidor, rota, payload, tipo, status, erros, autorização, compatibilidade/versionamento.
3. Aponte onde traduzir DTOs e erros, onde a regra mora e quais dependências ficam no SRV.
4. Confirme tratamento de falha da dependência, timeout/retry, idempotência se aplicável e trace/correlation-id.
5. Sugira testes de contrato, integração e regressão no projeto que **realmente** disponibiliza cada interface.
6. Indique mudanças quebrando consumidor, sequência de release e rollback.
7. Entregue relatório ao refinador central, sem assumir que teve acesso a outros repositórios.

Formato: `contrato atual (evidência) | contrato proposto (pendente de aprovação) | risco de quebra | testes | pendências`. Não edite no modo refinamento.
