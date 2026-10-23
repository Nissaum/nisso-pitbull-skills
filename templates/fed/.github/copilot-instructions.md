# Copilot — FED Angular / Squad Pitbull

**Stack conhecida:** Angular + TypeScript; versão do Angular ainda a confirmar por repositório.
**Antes de sugerir sintaxe nova**, inspecione `package.json`, lockfile, `angular.json`, `tsconfig*.json` e exemplos locais relevantes.

- NÃO presumir Signals, standalone components, NgModules, template control-flow, RxJS moderno ou suporte a novas APIs sem versão confirmada.
- Seguir convenções de componentes, services, interceptors, guards, forms, navegação e estado **já usadas no repo**.
- Reutilizar design system, validação, acessibilidade, tokens de estilo e traduções existentes.
- Tipar interfaces de BFF e cobrir loading, empty, error, acesso negado e navegação por teclado quando aplicável.
- Evitar mover regra de negócio do SRV para FED; manter compatibilidade dos DTOs e status HTTP.
- Não instalar dependências nem migrar arquitetura sem autorização.
- Executar scripts existentes de build/lint/test; não inventar resultado ou comando.
- Manter diff mínimo, sem PII/segredos nem refatoração fora da história.
