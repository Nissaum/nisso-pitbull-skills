# Modelo de handoff de refinamento entre repositórios

> Copiar e preencher somente em espaço **interno e autorizado**. Este documento público é um template sintético, não recebe dados reais.

```yaml
historia: "EXEMPLO-000"
origem: "FED|BFF|SRV"
observado_em: "YYYY-MM-DD"
repository_context: "docs/ai-context.md revisado? SIM|PARCIAL|NAO"
status: "CONFIRMADO|PARCIAL|NAO_INSPECIONADO"
skills:
  - nome: "angular-frontend|spring-boot-backend|bff-contracts|..."
    aplicavel: true
    disponivel: "SIM|NAO|NAO_VERIFICADO"
    utilizacao_comprovada: "SIM|NAO|NAO_VERIFICADO"
impactos:
  - responsabilidade: "..."
    evidencia_arquivo: "..."
    impacto: "CONFIRMADO|PROVAVEL|NENHUM"
contrato:
  inputs: ["..."]
  outputs: ["..."]
  erros: ["..."]
  compatibilidade: "..."
testes: ["..."]
dependencias: ["..."]
duvidas_bloqueantes: ["..."]
recomendacao: "..."
```

**Regras:** apontar caminho real de evidência, não enviar código da empresa para fora; ausência de leitura não equivale a ausência de impacto; não declarar scan Mend ou testes executados sem comprovante.
