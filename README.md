# 🐾 Squad Pitbull — Engenharia Assistida por IA

**Playbook v0.3 · GitHub Copilot · FED (Angular) · BFF/SRV (Java 21 + Spring Boot 4.1 informado)**

> **Material de referência para piloto, não uma política corporativa aprovada.** Este repositório é **público** e contém apenas templates e exemplos fictícios. Nunca publique aqui páginas internas do Confluence, código proprietário, endpoints internos, segredos, dados de clientes ou incidentes reais.

## Comece aqui

| Perfil | Primeira leitura | Próximo passo |
|---|---|---|
| Desenvolvedor(a) iniciante | [Guia de prompts](GUIA-DE-PROMPTS.md) | [Checklist diário](CHECKLIST-DEVS.md) |
| Desenvolvedor(a) experiente | [Playbook](PLAYBOOK.md) | [Modelos de prompts](templates/shared/.github/prompts/) |
| TL/referência técnica | [Inventário](INVENTARIO-TECNICO.md) | [Métricas e piloto](METRICAS-E-PILOTO.md) |
| Equipe inteira | [Confluence → Copilot](CONFLUENCE-PARA-COPILOT.md) | [Exercício guiado](EXEMPLO-PRATICO.md) |

**Regra de ouro:** IA ajuda a **entender → questionar → mapear → planejar → implementar → testar → revisar**. Nunca começar no “faz aí”.

## Conteúdo
- [PLAYBOOK.md](PLAYBOOK.md): fluxo de 8 gates, trilhas curta e completa, responsabilidades e DoD.
- [CHECKLIST-DEVS.md](CHECKLIST-DEVS.md): roteiro operacional para juniores e plenos.
- [MODELO-HISTORIA.md](MODELO-HISTORIA.md): estrutura mínima de entrada.
- [GUIA-DE-PROMPTS.md](GUIA-DE-PROMPTS.md): engenharia de prompts com exemplos fracos e bons.
- [CONFLUENCE-PARA-COPILOT.md](CONFLUENCE-PARA-COPILOT.md): como usar especificações sem "copiar e mandar fazer".
- [EXEMPLO-PRATICO.md](EXEMPLO-PRATICO.md): história fictícia FED/BFF/SRV completa.
- [TRILHA-DE-CAPACITACAO.md](TRILHA-DE-CAPACITACAO.md): laboratório, exercícios e rubrica.
- [INVENTARIO-TECNICO.md](INVENTARIO-TECNICO.md): contexto e versões a confirmar.
- [POLITICA-CUSTO-E-SEGURANCA.md](POLITICA-CUSTO-E-SEGURANCA.md): custos, tokens, permissões e limites.
- [METRICAS-E-PILOTO.md](METRICAS-E-PILOTO.md): proposta de implantação em quatro semanas.
- [templates/](templates/): arquivos para **copiar seletivamente** nos repositórios FED/BFF/SRV.

## Aplicação dos templates
1. **Verifique** versões, dependências, políticas internas e comandos reais; não execute código apenas com base nestes templates.
2. Copie os arquivos de `templates/fed`, `templates/bff` ou `templates/srv` para a **raiz do projeto correspondente**, preservando `.github/` e `docs/`.
3. Copie os arquivos de `templates/shared/.github/prompts/` e o modelo de PR para cada projeto (faça merge, não sobrescreva cegamente).
4. Ajuste os `PREENCHER` com dados **não sensíveis** e exemplos reais apenas em **repositórios corporativos autorizados**.
5. Valide os prompts com um dev menos experiente e mantenha revisão humana nos PRs.

**Compatibilidade:** FED Angular, versão ainda pendente. BFF/SRV: Java 21 + Spring Boot 4.1 conforme informado, validar versão efetiva em cada `pom.xml` ou Gradle. As opções de Copilot variam por IDE e licença.

## Uso responsável
Materiais do Confluence: referenciar e resumir **apenas em ferramentas e repositórios aprovados pela organização**. Em espaço público, utilizar exemplos sintéticos. A IA **não** decide regra de negócio nem substitui revisão, testes, segurança ou aprovação de entrega.
