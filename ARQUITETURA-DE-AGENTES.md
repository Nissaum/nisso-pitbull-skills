# Arquitetura de agentes Pitbull v0.4

> **Status:** proposta de piloto, para Copilot com subagentes habilitados e ferramentas autorizadas. Não se trata de uma orquestração automática garantida em todas as IDEs. Exemplos públicos e fictícios; nenhuma especificação interna deve ser publicada aqui.

## 1. Problema que resolvemos
Histórias frequentemente cruzam FED → BFF → SRV. Três refinadores independentes geram decisões incongruentes, contratos diferentes e duplicam contexto. Um **orquestrador único** produz uma visão consolidada, e especialistas respondem somente perguntas delimitadas do seu domínio.

```text
História / extrato de Confluence autorizado
                  |
            Refinador Central
       (lê contexto + classifica)
                  |
        +---------+---------+
        |         |         |
  Análise FED   Análise BFF  Análise SRV
  (se impacto)  (se impacto)  (se impacto)
        +---------+---------+
                  |
      Contratos + dependências
      Plano integrado + dúvidas
                  |
         Aprovação dev / TL
                  |
     Implementadores existentes
                  |
     Testes + Mend + revisão + PR
```

**A delegação é seletiva:** não chamar FED/BFF/SRV por hábito, somente quando a evidência apontar impacto ou incerteza relevante. Em tarefas pequenas, o agente central pode não delegar.

## 2. Papéis e ferramentas
| Papel | Template | Ferramentas | Saída |
|---|---|---|---|
| Refinador central | `pitbull-refinador-central.agent.md` | leitura, busca, delegação | refinamento ponta a ponta e plano único |
| Especialista FED | `pitbull-fed-analista.agent.md` | leitura e busca | análise Angular com arquivos e testes |
| Especialista BFF | `pitbull-bff-analista.agent.md` | leitura e busca | adaptação/contratos BFF |
| Especialista SRV | `pitbull-srv-analista.agent.md` | leitura e busca | domínio, integrações, dados |
| Documentador | `pitbull-documentador.agent.md` | leitura, busca, edição | `docs/ai-context.md` e docs técnicas |
| Auditor de skills | `pitbull-skills-auditor.agent.md` | leitura e busca | matriz de skills aplicáveis e lacunas |
| Revisor Mend | `pitbull-mend-reviewer.agent.md` | leitura e busca | triagem de achados **de scans existentes** |

O documentador é um processo de **bootstrap/manutenção**, não uma etapa para reproduzir documentação inteira antes de cada conversa. Especialistas não fazem alterações e não criam subagentes; o central consolida.

## 3. Pré-requisito — contexto do projeto
Cada aplicação precisa ter um `docs/ai-context.md` **real, curto e revisado**, com:
- Nome/tipo/responsabilidades do projeto, versão de stack confirmada pelo build;
- Fluxos e diretórios relevantes; exemplos reais de classes/componentes/testes;
- Contratos expostos/consumidos, donos e fronteiras de responsabilidade;
- Comandos **confirmados** (build, teste, lint) e padrões reais;
- Dependências externas, riscos, referências para documentação detalhada;
- Data e responsável da revisão (sem PII ou links sensíveis neste repo público).

**Gate C0 (contexto):** (a) documento existe; (b) informações importantes possuem fonte (arquivo); (c) versões/comandos foram verificados; (d) faltas foram marcadas "NÃO VERIFICADO". Se incompleto, **chamar documentador em tarefa separada** ou mapear lacunas. Não deixar agente inventar arquitetura para avançar.

O documento de contexto não substitui leitura de código, nem precisa ser recopiado integralmente em cada prompt. Detalhes grandes ficam em `docs/architecture.md`, `docs/contracts.md` etc., carregados quando necessários.

## 4. Contrato de entrada e saída dos analistas
O central envia para cada especialista:

```text
História/ID: ...
Regras/CA confirmados: ...
Pergunta específica por camada: ...
Repositório/workspace visível: ...
Contexto aprovado: docs/ai-context.md + caminhos relevantes
Restrições: somente leitura; não inventar; máximo de 5–8 arquivos foco
Saída esperada: resposta no formato padrão abaixo
```

Especialista responde:

| Campo | Obrigatório |
|---|---|
| Camada | FED / BFF / SRV |
| Impacto | Confirmado / Provável / Sem evidência |
| Evidências | Arquivos e trechos realmente consultados |
| Responsabilidade | O que pertence a essa camada; o que não pertence |
| Contrato | Entradas, saídas, erros, compatibilidade e versão |
| Modificações sugeridas | Lista limitada de arquivos, sem editar |
| Testes | Unitário, contrato, integração, cenários negativos |
| Dúvidas / bloqueios | O que depende de outro repo/PO/TL |
| Skills relevantes | Nome da skill, por quê, usada? com evidência ou "não verificado" |

## 5. Consolidação obrigatória pelo refinador central
- Uma só descrição dos cenários e critérios de aceite (sem duplicatas).
- **Matriz de impacto** por FED/BFF/SRV, com evidência e grau de certeza.
- **Contrato entre camadas**: campo/tipo, regras, versão, status/erros, autorização, quem produz e quem consome.
- **Plano ordenado por dependências**, preferencialmente contrato + SRV → BFF → FED, mas sem impor ordem quando contexto real pedir outra.
- Testes por fronteira e estratégia de rollback, com validação humana.
- **Conflitos**: decisões divergentes entre especialistas aparecem como "PENDÊNCIA", não solução por suposição.
- Seleção e evidência de skills: **necessária / disponível / utilizada (confirmado ou não verificado)**.
- Contexto ausente/sem acesso explicitado.

## 6. Fronteira entre repositórios (crítica!)
Um agent aberto só em `fed` **não lê automaticamente** outros repositórios. Há dois modos:

**Modo A — workspace multirraiz autorizado:** abrir FED, BFF e SRV no mesmo workspace, com permissão e descoberta de custom agents compatíveis com a IDE. Testar se os especialistas conseguem acessar cada projeto. Se não, não simular acesso.

**Modo B — handoff manual (mais portável):** executar especialistas no repositório correspondente, exportar apenas relatórios de interface **autorizados e sanitizados** no formato [HANDOFF-REFINAMENTO.md](HANDOFF-REFINAMENTO.md) em espaço corporativo apropriado. O central consolida os relatórios, identificando qualquer parte não inspecionada.

Em ambos: não transferir código/Confluence interno para este repositório público.

## 7. Contexto, skills e custos
- Skills ficam em `.github/skills/<nome>/SKILL.md`, e normalmente são descobertas por nome/descrição. O corpo é carregado quando relevante, não é necessário anexar todas as skills em cada chamada.
- **Uma skill disponível não significa uma skill realmente utilizada**. Verificar a atividade do agente ou registrar "não verificado".
- Não chamar especialistas de camadas não impactadas; evitar repassar páginas inteiras do Confluence a cada subagente.
- Entregar ao central **resumo estruturado** e não todos os logs de subagentes.
- Skills e subagentes podem aumentar o consumo total, embora reduzam o contexto principal.
- Instruções não são enforcement: use CI, proteção de branches e controles organizacionais reais.

## 8. Mend é um gate de segurança, não um simples prompt
- **Mend SCA** verifica dependências; **Mend SAST** verifica código-fonte quando licenciado/configurado. Executar pela integração/CI ou CLI **autorizada**, não por suposição.
- O agente `pitbull-mend-reviewer` **lê achados existentes** (escopo, arquivo, evidência, severidade, fix, false-positive, política) e recomenda encaminhamento. Não se declara scanner.
- Sem scan ou sem acesso: **NÃO VERIFICADO**, não "sem vulnerabilidades".
- Bloqueios e exceções são definidos por Segurança/DevSecOps; não suprimir achados nem mudar dependências automaticamente.
- Consulte [MEND-VALIDACAO.md](MEND-VALIDACAO.md).

## 9. Piloto e critérios de aceite
1. Dois cenários fictícios: apenas FED e história FED+BFF+SRV.
2. O central **não** chama SRV para alteração apenas visual; faz 3 análises na história cross-repo **somente se** necessário.
3. Cada especialista retorna arquivos reais ou "não inspecionado"; zero paths inventados.
4. Contrato único com ambiguidades e dependências claramente registradas.
5. Documentador produz documento com fontes, comandos verificados e lacunas sem inventar.
6. Audit de skills distingue aplicável/disponível/executada.
7. Mend: sem relatório => "não verificado"; com relatório sintético => achados priorizados.
8. Revisão humana antes de implementar; comparar consumo total e retrabalho com fluxo antigo.

**Referências oficiais:** https://docs.github.com/en/copilot/reference/customization-cheat-sheet · https://docs.github.com/en/copilot/how-tos/copilot-in-your-ide/use-copilot-agents/use-subagents · https://docs.mend.io/integrations/latest/scan-open-source-sca-with-mend-for-github
