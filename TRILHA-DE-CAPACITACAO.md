# Capacitação prática — devs que ainda usam “faz aí”

## Objetivo
Ensinar a equipe a **conduzir a IA** como ferramenta de raciocínio e produtividade, não como executor sem supervisão. Foco em iniciantes, mas com práticas comuns a todos.

## Sessão de 60 minutos (com pares)
| Tempo | Dinâmica | Produto |
|---|---|---|
| 0–10 min | Contraste: “copiar e faz aí” vs. prompt em 7 blocos | perceber riscos |
| 10–20 min | Traduzir história fictícia em critérios e dúvidas | extrato estruturado |
| 20–35 min | Refinamento com IA em Ask; corrigir hipóteses falsas | lista validada |
| 35–45 min | Mapa e plano em Plan, sem escrita | etapas + testes |
| 45–55 min | Simular execução de **uma** fatia e code review do diff | evidências |
| 55–60 min | Debrief + plano de aplicação | 1 melhoria pessoal |

## Exercícios rápidos
**1. Prompt ruim:** “Segue o Confluence, faz aí”. Reescrever com objetivo, escopo, restrições, saída e parada.

**2. Caça à alucinação:** entregar uma história fictícia com contrato ausente; o dev deve conseguir fazer o Copilot **perguntar**, não inventar endpoint.

**3. Diferenças entre camadas:** classificar cenários em FED (exibição), BFF (adaptação) e SRV (regra/persistência), justificando exceções.

**4. Diagnóstico disciplinado:** apresentar teste com falha e exigir hipótese + experimento discriminante antes de editar.

**5. Auditoria:** descobrir arquivo fora do escopo e teste não executado em um diff/resumo fictício.

## Rubrica de aprendizagem — uso formativo, não ranking
Pontuar cada dimensão 0 (não demonstra), 1 (com ajuda), 2 (autônomo):
- Explica objetivo e critérios sem ler texto literalmente.
- Distingue fatos, hipóteses e dúvidas.
- Define escopo e critério de parada do prompt.
- Confere arquivos/contratos reais antes de implementar.
- Verifica diff, testes e evidências observadas.
- Sabe quando envolver PO/TL/Segurança.

**Meta do piloto:** progresso da equipe e segurança de execução, não pontuação competitiva individual.

## Reforço após workshop
- **Semana 1:** pair prompting na primeira história de cada participante.
- **Semana 2:** cada dev compartilha um exemplo anonimizado de prompt ruim → melhorado e resultado verificado.
- **Semana 3:** retro de custo/retrabalho focada em processo, não culpa.
- **Semana 4:** incorporar os melhores prompts validados aos arquivos versionados.

## Responsabilidade do mentor
Não entregar apenas o prompt pronto. Perguntar: “qual é o objetivo?”, “o que a IA não sabe?”, “como vamos medir se deu certo?”, “qual decisão é sua?”. Revisar o raciocínio antes de revisar só a sintaxe.

**Artefatos de apoio:** [guia de prompts](GUIA-DE-PROMPTS.md), [Confluence → Copilot](CONFLUENCE-PARA-COPILOT.md), [exercício](EXEMPLO-PRATICO.md) e [checklist](CHECKLIST-DEVS.md).
