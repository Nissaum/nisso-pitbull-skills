---
name: mend-security-review
description: Interpretar e priorizar achados de relatórios reais Mend SCA ou Mend SAST relacionados a um commit/PR, com severidade, evidência e remediação. Não realiza scan e não substitui gate de segurança.
---
# Skill: revisão assistida de resultados Mend

## Pré-requisito
Relatório/status SCA/SAST **real, recente e autorizado**, associado a projeto, branch e commit corretos. Se ausente, saída obrigatória `NÃO VERIFICADO: scan indisponível/não executado`.

## Procedimento
1. Diferencie **SCA** (dependências e licenças) de **SAST** (código). Não inferir uma a partir da outra.
2. Consulte somente finding necessário: id/CVE/CWE, severidade, arquivo/componente, versão e evidências, solução sugerida e política aplicada.
3. Separe findings novos/legados/desconhecidos com justificativa; sinalize falso positivo apenas como hipótese para AppSec.
4. Proponha remediação mínima compatível com build e testes; jamais autoaprovar exceção, suprimir finding ou desabilitar scan.
5. Solicite novo scan **real** após correção e registre resultado observado.
6. Sem evidência documental, não afirmar que o projeto está livre de vulnerabilidades.

## Saída
`status | origem/commit | tipo SCA/SAST | achados com evidência | risco | correção recomendada | pendência AppSec`.

A CLI Mend pode oferecer `mend dep` e `mend code`, porém sua execução exige aprovação/ambiente/configuração corporativa próprios, e **não faz parte desta skill read-only**.
