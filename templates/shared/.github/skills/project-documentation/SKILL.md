---
name: project-documentation
description: Criar, validar e manter documentação técnica factual de um projeto para uso pelo Copilot, especialmente docs/ai-context.md. Use em bootstrap, onboarding ou mudanças de stack, arquitetura, contratos e testes.
---
# Skill: documentação de contexto do projeto

Siga estes passos diretamente no repositório da aplicação. O guia completo está em `DOCUMENTACAO-DE-PROJETOS.md` no repositório do playbook, mas esta skill não depende dele para funcionar:

1. Inspecione README, build, CI, módulos e pequena amostra de classes/componentes e testes.
2. Produza `docs/ai-context.md` **curto** com papel do serviço, stack verificada, mapa, contrato, comandos encontrados, exemplos e riscos, com fonte por informação.
3. Preservar documentação existente. Documentos extensos opcionais: `docs/architecture.md`, `docs/contracts.md` e `docs/testing.md`, referenciados do contexto.
4. Distinga CONFIRMADO / INFERIDO / NÃO VERIFICADO; não invente endpoints, resultados ou versões.
5. Só edite documentação autorizada, nunca código/configuração/CI por conta da documentação.
6. Liste pendências e solicite revisão humana no PR.

**Atenção:** o caminho de diretriz acima refere-se somente à fonte no playbook e não deve ser necessário após copiar a skill para outro repo.
