# Confluence → Copilot: processo seguro e eficiente

> **Atenção:** Confluence pode conter informação interna. Utilize somente Copilot, conectores, dispositivos e repositórios corporativos **autorizados**. Este repositório público contém apenas a metodologia; **nunca cole aqui material real**.

## O Confluence é fonte de requisitos, não prompt de execução
Uma especificação bem escrita ainda pode conter premissas, decisões em aberto, campos não implementados, versões desatualizadas e informações irrelevantes para determinada camada. Colar tudo com “faz aí” faz o modelo **decidir silenciosamente** como interpretar essas lacunas.

## Protocolo de sete passos
1. **Permissão e classificação:** o conteúdo pode ser usado na ferramenta selecionada? Proteja clientes, segredos, infraestrutura e dados internos.
2. **Leitura humana:** dev identifica objetivo, entradas/saídas, critérios, exceções e dúvidas.
3. **Extrato estruturado:** montar o [MODELO-HISTORIA.md](MODELO-HISTORIA.md) **no ticket ou ambiente autorizado**, não necessariamente copiar página inteira.
4. **Refinamento read-only:** Copilot converte extrato em cenários e perguntas; **não gera código**.
5. **Validação humana:** PO resolve dúvidas funcionais; TL/arquitetura, decisões técnicas; registrar o que foi decidido na fonte autorizada.
6. **Mapa e plano:** Copilot localiza arquivos, impactos, testes e propõe pequenas etapas. O dev confirma.
7. **Implementação controlada:** apenas fatias aprovadas, com diff, testes reais e revisão.

## Estrutura recomendada para o extrato
```text
HISTÓRIA: [ID]
OBJETIVO: [resultado observável]
COMPORTAMENTO ATUAL: [...]
COMPORTAMENTO ESPERADO: [...]
REGRAS CONFIRMADAS: [R1, R2...]
CRITÉRIOS DE ACEITE: [CA1, CA2...]
EXCEÇÕES E SEGURANÇA: [...]
CONTRATOS/CAMADAS: [...]
FORA DE ESCOPO: [...]
DÚVIDAS: [...] (com donos)
REFERÊNCIA CONFLUENCE: [link interno somente onde permitido]
```

**Resumo não é fonte de verdade:** se o extrato divergir da página, resolver no documento/ticket autorizado antes de implementar.

## Sessões recomendadas no Copilot

### Sessão A — entender (Ask)
```text
Sem alterar arquivos, confronte o extrato da história
com os critérios de aceite. Organize fatos, inferências,
dúvidas bloqueantes, exemplos positivos/negativos,
pontos de integração e questões para PO/TL.
Não invente regra que não foi documentada.
```

### Sessão B — mapear e planejar (Plan)
```text
Com dúvidas bloqueantes resolvidas, localize somente
caminhos relacionados a [comportamento]. Proponha plano
incremental por camada, contratos e testes.
Liste dependências entre etapas e critério de parada.
Não edite arquivos.
```

### Sessão C — executar (Agent)
```text
Execute exclusivamente [etapa aprovada] nos arquivos [lista].
Mantenha convenções do projeto e compatibilidade.
Ao final apresente diff, comandos/testes executados
e resultados observados, sem inventar validações.
Pare se forem necessárias decisões não resolvidas.
```

## Condições de parada
- Critério de aceite contraditório / omissão relevante.
- Alteração de contrato, privilégio ou persistência não aprovada.
- Arquivo/endpoint sugerido não existe.
- Fonte Confluence mais recente conflita com histórico/ticket.
- Dados classificados como sigilosos não podem ser compartilhados com o meio selecionado.

## Economia de contexto
Não reler a página toda a cada pergunta: manter **extrato validado**, decisões, lista de arquivos encontrados e pendências. Solicitar o trecho original só se for necessário para esclarecer um detalhe. Não espalhar cópias de material corporativo no Git público.
