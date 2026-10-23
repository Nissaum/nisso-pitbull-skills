# Guia prático de prompts — do “faz aí” à engenharia assistida

**Público:** devs juniores, plenos e seniores da Squad Pitbull.

## O problema
Colar a especificação inteira do Confluence e acrescentar “faz aí” **não orienta a IA** sobre o que deve fazer primeiro, o que é decisão humana, em quais arquivos pode atuar, quais critérios importam e como provar que terminou. Frequentemente isso resulta em alterações amplas, suposições, testes incompletos e consumo excessivo de contexto.

**Mudança obrigatória do hábito:** `entender → perguntar → mapear → planejar → fazer uma parte → testar → revisar`.

## Anatomia de um bom pedido (7 blocos)
| Bloco | Pergunta que o dev deve responder |
|---|---|
| 1. Objetivo | Que comportamento precisa mudar e por quê? |
| 2. Contexto | Qual parte **autorizada** da história, contrato e código importa? |
| 3. Tarefa | O que a IA deve entregar **nesta interação**? |
| 4. Escopo | Quais módulos/arquivos pode ler e/ou modificar? |
| 5. Restrições | Versões, padrões, proibições e decisões que não pode inventar? |
| 6. Validação | Qual saída ou teste comprova que o passo deu certo? |
| 7. Parada | Quando deve interromper e consultar o humano? |

Não precisa escrever um texto enorme. Um prompt curto com estes elementos tende a ser melhor que centenas de linhas sem objetivo.

## Exemplo 1 — refinamento técnico

❌ **Ruim:** "Segue a especificação do Confluence. Faz aí."

✅ **Bom (Ask / sem edição):**

```text
Objetivo: compreender a história [ID] antes de implementar.
Contexto: resumo sanitizado e critérios aceitos abaixo.
Tarefa: reescreva o comportamento esperado em 5 linhas,
identifique regras, exceções e cenários Dado/Quando/Então.
Separe FATO, HIPÓTESE e DÚVIDA.
Escopo: só esta especificação e docs/ai-context.md.
Saída: lista curta de questões bloqueantes para PO/TL,
possíveis impactos FED/BFF/SRV e DoR proposta.
NÃO altere código, NÃO invente API/regras.
Se houver dúvida bloqueante, pare sem implementar.
[INCLUIR CONTEXTO APROVADO]
```

**O dev confere:** resumo corresponde ao entendimento? Há ambiguidade real? Alguma regra foi inventada?

## Exemplo 2 — localizar impacto

❌ **Ruim:** "Analisa todo o projeto e altera o que precisar."

✅ **Bom (Ask/Plan):**

```text
Com critérios de aceite já confirmados, localize o caminho
de execução de [comportamento] no projeto atual.
Consulte primeiro docs/ai-context.md e apenas os pacotes
relevantes; indique caminhos reais de classes/componentes.
Saída: tabela arquivo/ação/motivo, contratos afetados,
testes e riscos. Marque "não encontrado" ao invés de inventar.
SEM editar, SEM refatorar, SEM mudar dependências.
Limite: primeiro indique até 5 arquivos candidatos;
se precisar ampliar a busca, explique o motivo.
```

**O dev confere:** caminhos existem? Regra de negócio está na camada correta? Há compatibilidade de contratos?

## Exemplo 3 — implementar uma fatia

❌ **Ruim:** "Beleza, pode fazer tudo."

✅ **Bom (Agent controlado):**

```text
Implementar apenas a etapa 2 do plano aprovado:
expor status de pedido já existente no SRV via BFF.
Arquivos permitidos: [CAMINHOS VALIDADOS].
Java 21 / Spring Boot 4.1 informado; confirme dependências
reais antes de escolher classes/annotations.
Preserve contratos existentes e padrão de erro.
Não altere FED, banco, dependências, security nem pipeline.
Crie/ajuste teste apropriado e execute comando autorizado
se houver ferramenta disponível.
Ao final: diff resumido + arquivos modificados + comandos
e RESULTADOS REAIS + pendências.
Se a implementação requerer contrato novo, pare e pergunte.
```

**O dev confere:** diff ficou no escopo? O teste valida a regra? Os resultados foram realmente executados?

## Exemplo 4 — diagnóstico sem “tentativa infinita”

❌ **Ruim:** "Não funcionou, tenta outra coisa."

✅ **Bom:**

```text
Resultado observado: HTTP 422 para cenário X.
Esperado: HTTP 200 conforme critério CA-2.
Alterações atuais: [classes relevantes].
Log sanitizado: [somente linhas essenciais].
Não edite. Produza até 3 hipóteses ordenadas por evidência,
um teste discriminante para cada hipótese e arquivos exatos
a inspecionar. Identifique qual informação está faltando.
```

## Anti-padrões a evitar
- **Prompt-caminhão:** inserir dezenas de páginas sem filtragem.
- **Prompt mágico:** “faz aí”, “corrige tudo”, “refatora todo o backend”.
- **Agent antes do plano:** liberação de escrita sem escopo.
- **Aceitar relato da IA como prova:** testes/CI não executados.
- **Corrigir indiscriminadamente:** mudar vários arquivos sem saber causa.
- **Repetir contexto antigo:** prompts que reabrem um repositório inteiro a cada passo.
- **Substituir entendimento:** dev não sabe explicar o porquê do código.

## Perguntas que o dev DEVE conseguir responder antes de aprovar o Agent
1. Qual problema esta mudança resolve?
2. Em qual camada mora a regra? Por quê?
3. O que **não** pode mudar?
4. Como vou provar o resultado?
5. Quando peço ajuda para PO, TL ou QA?

Se não conseguir, a próxima ação é refinamento/mentoria, **não codificação automática**.

## E se o prompt não resolver de primeira?
Pare, observe o resultado e reduza a incerteza: `evidência → hipótese → experimento menor → aprendizado`. Trocar só as palavras do mesmo “faz aí” normalmente não melhora a investigação.

**Atalhos:** [modelo da história](MODELO-HISTORIA.md), [guia Confluence](CONFLUENCE-PARA-COPILOT.md), [exercício completo](EXEMPLO-PRATICO.md), [prompts versionados](templates/shared/.github/prompts/).
