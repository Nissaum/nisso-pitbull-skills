# Skills Pitbull — descoberta, seleção e evidência de uso

## Distinções
- **Instruções:** regras curtas e permanentes (`copilot-instructions.md`).
- **Custom agents:** papéis de refinamento, documentação, revisão.
- **Subagentes:** delegações de tarefas delimitadas em contexto separado.
- **Skills:** procedimentos especializados acionados quando relevantes, em `.github/skills/<slug>/SKILL.md`.
- **Mend:** scanner corporativo com relatório real, não uma skill de IA que "adivinha" vulnerabilidades.

## Skills incluídas nos templates
| Skill | Copiar para | Gatilho |
|---|---|---|
| `angular-frontend` | FED | component, template, form, route, HTTP, accessibility |
| `spring-boot-backend` | BFF/SRV | Java 21, Spring Boot, validação, testes, integração |
| `bff-contracts` | BFF | adaptação de contratos, erros, segurança FED↔SRV |
| `project-documentation` | FED/BFF/SRV | inventário, `docs/ai-context.md` e atualização de docs |
| `mend-security-review` | FED/BFF/SRV | leitura/triagem de findings Mend SCA/SAST; não escaneia |

## Matriz de seleção a preencher antes da execução
| Habilidade | Aplicável? | Disponível? | Uso comprovado? | Evidência |
|---|---|---|---|---|
| Angular | sim/não | sim/não | sim/não/não verificado | atividade do Copilot |
| Spring Boot | sim/não | sim/não | sim/não/não verificado | atividade do Copilot |
| Contratos BFF | sim/não | sim/não | sim/não/não verificado | atividade do Copilot |
| Documentação | sim/não | sim/não | sim/não/não verificado | arquivo e PR |
| Mend | sim/não | sim/não | sim/não/não verificado | relatório/status e commit |

**Atenção:** a simples presença de `SKILL.md` não comprova carregamento ou uso. Os modelos podem escolher não ativá-la; usar acionamento explícito quando uma skill obrigatória não for selecionada e conferir atividade.

## Critérios de qualidade da skill
- Nome coincide com pasta, kebab-case;
- Descrição específica de quando usar;
- Só o mínimo para o workflow, com links a exemplos/recursos;
- Não duplica instructions nem inventa resultados;
- Sem credenciais/comandos perigosos;
- Validada na IDE/harness/versão que a equipe usa;
- Custo por tarefa e resultados comparados com baseline.

## Antes de criar skills novas
Verificar versão do stack e padrões reais. Dê preferência à skill **aprovada internamente** se existir, ao invés de baixar pacote arbitrário. Revisar proveniência, permissões, scripts e segurança de skills de terceiros.

**Leitura:** https://code.visualstudio.com/docs/agent-customization/agent-skills
