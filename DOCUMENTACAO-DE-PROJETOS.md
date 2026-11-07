# Documentação mínima por projeto — bootstrap e manutenção

## Por que?
Antes de analisar uma história, o Copilot precisa conhecer responsabilidades, versões e convenções de **cada** repositório. Sem isso, tende a gastar contexto explorando arquivos e pode reproduzir exemplos incompatíveis.

## O que criar
**Obrigatório (curto):** `docs/ai-context.md`, recomendado até 150–250 linhas, com:
1. **Identidade**: responsabilidade do sistema, limites de domínio e integração;
2. **Stack verificada**: `package.json` / `angular.json` ou `pom.xml` / `build.gradle`;
3. **Mapa**: diretórios, entrypoints, fluxo de execução, camadas e convenções;
4. **Contratos**: provedores/consumidores e localização de OpenAPI/schema/DTOs, sem colar conteúdo extenso;
5. **Comandos reproduzíveis**: build, lint, unit, integração, cobertura, versão runtime e requisitos;
6. **Padrões demonstrados**: 1 a 3 arquivos de exemplo por responsabilidade, com caminhos reais;
7. **Qualidade e segurança**: autenticação, dados sensíveis, testes, Mend e política de CI quando constatados;
8. **Fontes e lacunas**: arquivo usado como evidência, status PREENCHER/NÃO VERIFICADO, data da revisão.

**Opcional**: `docs/architecture.md`, `docs/contracts.md`, `docs/testing.md` quando o material não couber no resumo. O `ai-context.md` linka para essas páginas; não repete tudo.

## Papel do documentador
Agente `pitbull-documentador` começa examinando arquivos de build/CI/README e amostra pequena de código e testes, distingue **confirmado / inferido / não encontrado**, e **edita exclusivamente documentação aprovada**, preservando documentação existente. Sem executar comandos destrutivos e sem inventar resultados.

## Fluxo recomendado
- Uma vez por aplicação: bootstrap em branch → revisão por dev responsável → PR → merge.
- A cada mudança de arquitetura, versão, contrato ou build: atualizar `docs/ai-context.md` **no mesmo PR** da mudança.
- Em cada refinamento: checagem breve de existência, versão, data de revisão e links — sem executar o documentador inteiro se a documentação estiver atual.
- Se o documento não existe: central sinaliza gate C0 e solicita bootstrap. Se bloqueio não for crítico, dev pode fazer discovery read-only, mas não inventa informações faltantes.

## Quality gate do contexto
- [ ] Projeto e limites claros
- [ ] Stack/versão conferida no build
- [ ] Mapa aponta arquivos que existem
- [ ] Comandos presentes nos scripts/wrapper (execução marcada separadamente)
- [ ] Contratos e responsáveis reconhecidos
- [ ] Nenhum segredo, PII ou dados classificados
- [ ] Não verificados assinalados, com dono para resolver
- [ ] Revisão humana e atualização prevista

**Observação:** repositório de playbook é público; aplicação real dos templates e documentos internos deve ficar no Git corporativo autorizado.
