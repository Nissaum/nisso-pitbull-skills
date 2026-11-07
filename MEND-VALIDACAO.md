# Mend na Squad Pitbull — validação de vulnerabilidades

> Guia de integração, **não** instalação ou execução automática. Alinhar licença, políticas, acesso, categorias e gates com AppSec/DevSecOps.

## Escopos distintos
| Verificação | Ferramenta | Evidência desejada |
|---|---|---|
| Componentes/dependências e licenças | Mend SCA | relatório da execução e inventário afetado |
| Segurança de código | Mend SAST, se habilitado | achados do scanner com evidência |
| Alterações de dependências | Mend Remediate/Renovate, se configurado | PRs sugeridos e impacto revisado |
| Vulnerabilidade de app em runtime | Ferramentas de DAST/runtime aprovadas | não inferir a partir do Mend SCA/SAST |

A integração Mend com GitHub pode publicar **Security Checks** em commits/PRs. Não assumir que está instalada, que roda em todos os projetos ou que todas as categorias são licenciadas.

## Padrão de uso no fluxo
1. **Antes da codificação:** saber qual scanner é exigido e quais políticas de severidade são aplicadas.
2. **Na alteração:** evitar atualizar dependências por conta própria sem análise do BOM/build e sem aprovação.
3. **Na revisão/PR:** coletar status real do Mend para o commit/PR correto. O gate corporativo é a fonte de verdade.
4. **Se falhar:** identificar ID da ocorrência (ex.: CVE/CWE), componente/arquivo, versão, alcance, severidade, explorabilidade, falso positivo e correção suportada.
5. **Remediação:** corrigir com menor mudança, executar testes relevantes, solicitar novo scan e manter evidência. Exceção somente pela política aprovada de AppSec.

## Agente revisor
`pitbull-mend-reviewer` **não executa scanner**: lê resultados SCA/SAST fornecidos por integração autorizada e devolve matriz:
```text
Status do scan: APROVADO|FALHOU|PENDENTE|NAO_EXECUTADO|NAO_ACESSIVEL
Origem/commit/data: ...
Tipo: SCA|SAST
ID | Severidade | Evidência | Mudança introduzida? | Ação sugerida | Responsável
Risco residual / decisão AppSec: ...
```
**Sem evidência:** "scan não verificado" — nunca afirmar segurança por ausência de saída.

## CLI (somente quando autorizada e disponível)
As documentações atuais descrevem `mend dep` (SCA) e `mend code` (SAST), mas **não** execute esses comandos automaticamente em máquinas corporativas ou CI sem aprovar instalação, autenticação, escopo e política. Tokens e credenciais ficam em secret stores aprovadas, nunca em `SKILL.md`, arquivos de configuração versionados ou saída para chat.

## Não fazer
- Não inserir credenciais Mend em repositório ou prompt.
- Não alterar `.whitesource`/configuração do scanner ou políticas para "ficar verde" sem AppSec.
- Não suprimir finding automaticamente nem marcar falso positivo sem prova.
- Não tomar a opinião da IA como substituta da plataforma Mend.
- Não publicar relatórios privados de segurança no playbook público.

## Referências
- https://docs.mend.io/integrations/latest/scan-open-source-sca-with-mend-for-github
- https://docs.mend.io/integrations/latest/scan-your-custom-code-sast-with-mend-for-github
- https://docs.mend.io/platform/latest/configure-the-mend-cli-for-sca
- https://docs.mend.io/platform/latest/configure-the-mend-cli-for-sast
