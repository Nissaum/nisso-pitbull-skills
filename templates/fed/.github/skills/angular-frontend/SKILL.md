---
name: angular-frontend
description: Analisar, implementar ou validar alterações no FED Angular com atenção à versão instalada, componentes, serviços HTTP, acessibilidade e contratos com BFF. Use apenas em tarefas de frontend Angular.
---
# Skill: Angular no FED Pitbull

## Entradas mínimas
- História/CA validado e `docs/ai-context.md`;
- `package.json`, `angular.json`, `tsconfig*.json` e arquivos realmente envolvidos.

## Procedimento
1. Confirmar `@angular/core`, TypeScript, RxJS e padrões **existentes** (NgModule/standalone, estado, formulário, interceptors, estilo). Não presumir recursos de versões futuras.
2. Localizar o caminho real: rota → componente → serviço → BFF. Não ler todo o repositório.
3. Definir mudança mínima, contrato de entrada/saída, estados loading/empty/error, acessibilidade e i18n.
4. Verificar permissões, validação de dados, tratamento de falhas e ausência de dados sensíveis.
5. Planejar teste de componente/serviço/interceptor com framework e scripts reais do projeto.
6. Antes de editar, exigir plano aprovado; quando autorizado, modificar só arquivos da etapa; registrar diff e evidências reais.

## Saída
`Versão confirmada | arquivos consultados | alteração mínima | contrato | testes | riscos | dúvidas`.

Se a história for somente SRV, esta skill **não** se aplica. Não inferir que já foi carregada sem atividade da sessão.
