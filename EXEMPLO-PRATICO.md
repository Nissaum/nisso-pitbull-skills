# Exercício completo — história fictícia FED + BFF + SRV

> **100% sintético.** Não representa endpoints, regras ou tecnologia interna da empresa.

## Especificação de exemplo
**História:** HP-123 — Exibir o status de um pedido fictício na tela de detalhes.

**Regras confirmadas de exemplo**
- R1: um pedido pode ter status `CRIADO`, `EM_PROCESSAMENTO`, `CONCLUIDO` ou `CANCELADO`.
- R2: quando um pedido não existir, a API retorna HTTP 404.
- R3: um usuário só visualiza pedidos de sua própria conta.
- R4: nenhum dado sensível adicional é exposto no retorno.

**Critérios de aceite**
- CA1: dado um pedido autorizado existente, quando abrir detalhes, então mostrar status correto.
- CA2: dado um pedido inexistente, quando consultar, então mostrar estado amigável de não encontrado.
- CA3: dado um pedido de outro usuário, quando consultar, então impedir acesso sem expor dados.
- CA4: em erro de rede, a tela deve oferecer nova tentativa sem travar.

## Passo 1 — prompt de refinamento (Ask)
```text
Não escreva código. Analise a história fictícia HP-123,
reformule CA1–CA4 em Dado/Quando/Então, inclua cenários
negativos e aponte dúvidas de contrato e autorização.
Separe FATO/HIPÓTESE/PERGUNTA. No máximo 15 itens.
```

**Resposta que o dev precisa buscar:** CA1–CA4 preservados, 404 versus erro de permissão tratado sem vazamento, pergunta sobre API existente e tratamento de timeout, dúvidas identificadas — não decisões inventadas.

## Passo 2 — confirmar dúvidas com humanos
Em cenário real, PO/TL/SI confirmariam contrato existente, dono da autorização, padrão de resposta de erro e compatibilidade de releases. **Não seguir** até resolver bloqueantes.

## Passo 3 — análise de impacto (Ask/Plan)
```text
Usando somente a área relacionada a pedidos e
docs/ai-context.md, identifique classes/componentes reais
que implementam consulta de detalhes e autorização.
Não edite nada. Entregue tabela por FED/BFF/SRV,
incluindo contrato, testes e dependências.
Se algum arquivo não for encontrado, marque como dúvida.
```

**Plano humano aprovado (ilustrativo, não paths reais)**
| Passo | Camada | Mudança limitada | Validação |
|---|---|---|---|
| 1 | SRV | assegurar retorno do status e autorização existente | teste positivo + negado |
| 2 | BFF | mapear contrato autorizado, 404 e erro genérico | teste de contrato e falha |
| 3 | FED | mostrar status, loading, not-found e retry | teste de componente e acessibilidade |
| 4 | E2E | verificar payload, status, erros e integração | matriz CA1–CA4 |

## Passo 4 — implementação de uma fatia (Agent)
```text
Implemente somente passo 2 (BFF) da HP-123.
Respeite Java 21 e versão Spring Boot declarada no build.
Use apenas classes que identificamos e confirmamos.
Não mude SRV, FED, schema, dependências ou segurança.
Preserve contrato, 404 e semântica de autorização.
Adicione teste de adaptação contratual relevante.
Pare se o contrato atual divergir do plano.
Apresente diff resumido e resultados REAIS dos testes.
```

## Passo 5 — checar evidência
O dev verifica se o diff se limita à fatia, inspeciona todos os mapeamentos e executa o teste **no ambiente autorizado**. Verificar se erros e ausência de autorização não vazam dados.

## Passo 6 — revisão do PR
```text
Revise apenas meu diff da HP-123. Analise regressões,
controle de acesso, semântica 404/403, tratamento de
falhas, legibilidade e testes. Relate achados por
severidade com arquivo/trecho e correção sugerida.
Não declare testes aprovados se não executados.
```

## Resultado esperado de aprendizagem
O dev deve conseguir explicar: **o que fez, por que nesta camada, o que deliberadamente não alterou, como comprovou, que risco resta e quem aprova**. Se não conseguir, volte ao planejamento antes do merge.
