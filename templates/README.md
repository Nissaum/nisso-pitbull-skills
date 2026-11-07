# Como aplicar os templates v0.4

Os arquivos são **modelos para copiar**, não agentes ativos neste repositório público.

1. Escolha o projeto **FED**, **BFF** ou **SRV** e copie arquivos de `templates/<camada>/` para a raiz do repositório correspondente, preservando `.github/` e `docs/`.
2. Copie os recursos comuns de `templates/shared/.github/`: `agents/`, `prompts/`, `skills/` e template de PR.
3. Para **BFF e SRV**, copie `templates/java-common/.github/skills/spring-boot-backend/` para `.github/skills/spring-boot-backend/`.
4. Use a skill `angular-frontend` só no FED; `bff-contracts` só no BFF.
5. **Não sobrescreva** agents/instructions/skills existentes no repositório corporativo. Compare nomes, responsabilidades, ferramentas e consolide com PR.
6. Execute `pitbull-documentador` no repo de aplicação para criar/revisar `docs/ai-context.md`, conferindo toda versão, rota, contrato e comando.
7. Configure permissões e teste compatibilidade com a IDE/harness (subagentes, `tools: ['agent']`, descoberta de agent/skill). O resultado é **opcional/fallback** se não houver suporte.
8. Para histórias cross-repo, use [arquitetura de agentes](../ARQUITETURA-DE-AGENTES.md): workspace multirraiz autorizado ou [handoff](../HANDOFF-REFINAMENTO.md). Não supor que um workspace conhece todos os projetos.
9. Valide as skills consultando atividade real de execução. `SKILL.md` presente ≠ carregado. Veja [skills](../SKILLS-E-ROTEAMENTO.md).
10. Integração Mend somente com aprovação de AppSec/DevSecOps. A skill `mend-security-review` **lê resultados** e não executa SCA/SAST; ver [guia Mend](../MEND-VALIDACAO.md).

## O que NÃO incluir neste repositório
Confluence interno, código proprietário, segredos, endpoints privados, credenciais de scanner, dados de clientes, logs e relatórios privados. Exemplo sintético apenas.

## Compatibilidade
Angular versão a verificar por FED. Java 21 + Spring Boot 4.1 **informado**, confirme patch por projeto. Propriedades de custom agents e execução de subagentes variam por IDE e ambiente; os prompts e a delegação podem exigir ajustes.

**Fluxo humano:** contexto → refinamento central → plano integrado aprovado → agentes implementadores já existentes → testes reais → Mend real → revisão → PR.
