# Playbook de desenvolvimento assistido por IA — Squad Pitbull

**Objetivo:** estabelecer um processo previsível, auditável e econômico para histórias em FED (Angular), BFF e SRV (Java 21 / Spring Boot 4.1 informado). **Status: piloto sujeito à validação do TL, arquitetura e segurança.**

## Princípios
1. **IA sugere, dev valida, humano aprova.** A responsabilidade nunca é transferida ao modelo.
2. **Não começar codificando.** Primeiro interpretação, dúvidas e plano; depois uma fatia mínima.
3. **Separar fatos, hipóteses e decisões.** Nunca deixar a IA inventar regras, APIs ou evidências.
4. **Menor contexto suficiente.** Abrir apenas arquivos relevantes e artefatos autorizados.
5. **Critério de parada.** Dúvida bloqueante, divergência de contrato ou risco crítico interrompem o Agent.
6. **Toda história deixa rastros:** contrato de entrada, plano, diff revisado, evidências e PR.

## Escolha da trilha
- **Trilha curta:** correção pontual, sem impacto em contrato, dados, autenticação ou várias camadas. Cumprir entrada, plano enxuto, implementação, testes, review e PR.
- **Trilha completa:** regras novas, mudança de contrato, integrações, autorização, migrações, persistência, riscos altos ou FED+BFF+SRV. Todos os gates.
- **Dúvida sobre risco?** Adotar trilha completa e envolver TL.

## Fluxo e gates
| Gate | Modo sugerido | Entrega obrigatória | Prossegue quando… |
|---|---|---|---|
| 0. Entrada | Humano | história + critérios + contexto permitido | objetivo/escopo claros |
| 1. Refinamento | Ask/Plan (leitura) | dúvidas, critérios e exceções | bloqueantes respondidas |
| 2. Mapa/planejamento | Ask/Plan (leitura) | arquivos reais, impactos, plano incremental | dev aprova, TL para riscos |
| 3. Implementação | Agent com limites | diff mínimo por etapa | arquivos e comportamentos revisados |
| 4. Testes | Ferramentas + Agent controlado | comandos + resultados verificáveis | testes relevantes passam |
| 5. Integração | Testes reais + apoio IA | evidência FED ↔ BFF ↔ SRV | contratos e cenários consistentes |
| 6. Revisão | Humano + Ask (diff) | riscos corrigidos, comentários resolvidos | sem problemas críticos |
| 7. PR/release | Humano + Ask (resumo) | PR rastreável, CI e plano de rollback | políticas de branch atendidas |

### Gate 0 — Entrada / Definition of Ready
Dev e PO identificam objetivo de negócio, comportamento atual/esperado, critérios de aceite, regras, exceções e dependências. Sanitizar contexto de acordo com a política. Preencher [MODELO-HISTORIA.md](MODELO-HISTORIA.md). **Pare** se faltarem autorizações, definição de regra ou contrato necessário.

### Gate 1 — Refinamento técnico (sem escrita)
Usar `01-refinar-historia`. Exigir resumo em palavras próprias, cenários Dado/Quando/Então, perguntas bloqueantes/não bloqueantes, riscos, hipóteses e ponto de validação humano. Um resumo fluente não significa entendimento correto.

### Gate 2 — Impacto e plano (sem escrita)
Usar `02-mapear-impacto` e `03-plano`. Buscar no máximo os módulos necessários, com nomes de arquivos confirmados. Mapear dono da regra (normalmente SRV), adaptação do BFF, apresentação do FED, contratos, testes, migração/rollback e ordem de implementação. **Dev revisa o plano**. TL valida interfaces públicas, dados e segurança.

### Gate 3 — Implementação em fatias
Usar `04-implementar` especificando **uma** parte do plano, arquivos permitidos e comandos. Conferir `git diff` após cada modificação. Não mudar dependências, endpoints, permissões, migrations, testes legados nem abstrações sem autorização. Se o Copilot divergir, **interromper**, revisar hipótese e repropor uma fatia.

### Gate 4 — Testes e validação real
Usar `05-testar` para levantar casos e, quando autorizado, implementar testes. Executar localmente/CI com comandos reais: unitário, integração/contrato, erros, bordas, autorização, timeout e acessibilidade conforme impacto. Guardar **resultado observado**, não “IA disse que passou”. Não desabilitar teste para deixar CI verde.

### Gate 5 — Integração FED ↔ BFF ↔ SRV
Validar payloads, tipos, status HTTP, erros, autenticação, versionamento, compatibilidade de releases, timeouts, loading/empty/error, observabilidade e rollback. Toda condição crítica deve ter teste/evidência proporcional.

### Gate 6 — Autorrevisão e revisão humana
Usar `06-revisar` concentrado no diff. Verificar lógica, autorização, vazamentos, logs, tratamento de erros, transações, concorrência, performance, contratos e regressões. A IA **não aprova PR**.

### Gate 7 — PR e entrega
Usar `07-preparar-pr`. PR contém ID da história, resumo por camada, impactos, evidências dos testes, limitações, riscos, screenshots sintéticos para FED e estratégias de deploy/rollback quando aplicável. Aplicar as políticas de aprovação da organização.

## Responsabilidades
- **Dev autor:** compreende a história, confere plano/diff, executa testes e registra evidências.
- **PO/negócio:** confirma requisitos e resolve ambiguidades funcionais.
- **TL:** curadoria de contexto, apoio aos menos experientes e gates de arquitetura/risco.
- **QA/Segurança/Arquitetura:** requisitos específicos e controles corporativos.
- **Copilot:** instrumento de apoio, jamais dono de decisão ou evidência.

## Definition of Done
- [ ] Critérios de aceitação com evidência
- [ ] Contratos FED/BFF/SRV consistentes (quando aplicável)
- [ ] Testes reais e CI conforme pipeline
- [ ] Casos de erro, segurança e observabilidade avaliados
- [ ] Diff revisado, sem alterações oportunistas
- [ ] PR com aprovação humana e rollback quando necessário
- [ ] Sem dados sensíveis enviados ou publicados indevidamente

## Tratamento de falhas
Em erro recorrente, **pare após duas tentativas de correção sem progresso**, produza diagnóstico curto (comportamento, hipótese, trecho de log sanitizado) e peça ajuda humana. Na urgência, preserve evidência mínima e governança de mudança.
