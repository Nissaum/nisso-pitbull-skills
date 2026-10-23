# Política proposta — consumo, contexto e segurança do Copilot

> Confirmar com a organização **modelo de cobrança, licenças, AI Credits/tokens e limites vigentes**, pois mudam com planos e políticas. Não prometer economia percentual sem medição.

## Boas práticas para reduzir consumo desperdiçado
1. **Primeiro Ask/Plan (read-only).** Agent só com tarefa, escopo e saída definidos.
2. **Contexto mínimo:** história estruturada + padrões do repo + 2–5 arquivos relevantes, expandindo quando necessário.
3. **Reaproveitar conhecimento estável** via `.github/copilot-instructions.md`, instruções por path, `docs/ai-context.md`; mantê-los **curtos**, evitando texto gigante sempre injetado.
4. **Uma fatia por iteração.** Inspecionar diff e executar teste direcionado antes de avançar.
5. **Separar histórias.** Ao alongar sessão, criar resumo validado de decisões, pendências e arquivos afetados; evitar transportar histórico desnecessário.
6. **Modelos:** usar seleção automática/modelo econômico permitido por padrão; avançado para raciocínio difícil; comparar qualidade e custo real.
7. **Resultados compactos:** não pedir documentação volumosa, dump de logs ou releitura de repositório sem necessidade.
8. **Repetição de erro:** duas tentativas malsucedidas → rever diagnóstico com humano.
9. **Medir créditos por complexidade + retrabalho + bugs**, nunca tratar menos tokens isoladamente como desempenho melhor.

### Fórmula do pedido eficaz
**Objetivo + contexto mínimo + arquivos envolvidos + restrições + critérios de aceite + evidência requerida + critério de parada.**

## Proteção e governança
- Usar **somente ferramentas, conectores e ambientes autorizados pela empresa** para conteúdo interno Confluence e código privado.
- Não enviar dados de clientes, PII, credenciais, tokens, logs de produção nem segredos em prompts, fixtures e PRs.
- Não publicar material corporativo neste repositório público; usar cenários sintéticos nos exemplos.
- Não confiar exclusivamente em exclusão de conteúdo para Agent/CLI: revisar comportamento e políticas aplicáveis.
- Agente sem permissões indiscriminadas para produção, deploy, merge, migrations destrutivas, alteração de controle de acesso ou comandos massivos.
- Revisão humana e pipelines permanecem obrigatórios.
- Uma resposta do Copilot não é comprovação de build/teste executado.

## Controles sugeridos ao TL
- Limites/avisos corporativos a 70% e 90% da verba disponível **como indicadores**, não barreiras rígidas arbitrárias.
- Painel semanal: custo por história similar, nº de chamadas extensas, taxa de retrabalho, tempo e defeitos.
- Revisar permissões das ferramentas conectadas, instruções e prompts em PR.
- Confirmar políticas de retenção, DLP e classificação com Segurança da Informação.

## Fontes oficiais úteis
- https://docs.github.com/en/copilot/tutorials/optimize-ai-usage
- https://docs.github.com/en/copilot/concepts/billing-and-usage
- https://docs.github.com/en/copilot/how-tos/configure-content-exclusion/exclude-content-from-copilot
