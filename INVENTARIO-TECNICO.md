# Inventário técnico — verificar por repositório antes do piloto

| Camada | Stack informada | Ainda precisamos confirmar |
|---|---|---|
| FED | Angular + TypeScript | versão Angular/CLI, Node, TypeScript, RxJS, testes, padrões |
| BFF | Java 21 + Spring Boot 4.1 | patch efetivo, Maven/Gradle, HTTP clients, segurança, testes |
| SRV | Java 21 + Spring Boot 4.1 | patch efetivo, persistência, integrações, transações, testes |

### FED — checklist sem varredura ampla da IA
- [ ] Ler `package.json`, lockfile, `angular.json`, `tsconfig*.json` e CI.
- [ ] Conferir versões `@angular/core`, `@angular/cli`, Node, TypeScript e RxJS.
- [ ] Confirmar se arquitetura usa NgModule, standalone, Signals, template syntax e gerência de estado — **não presumir**.
- [ ] Escolher 1 componente, 1 service HTTP e 1 teste como referências aprovadas.
- [ ] Identificar comandos reais de lint/test/build.

### BFF/SRV
- [ ] Ler `pom.xml` ou `build.gradle*`, wrapper e arquivos de CI.
- [ ] Validar Java 21 e **versão efetiva de Spring Boot 4.1**, respeitando exceções.
- [ ] Confirmar starters realmente presentes; em Boot 4 não assumir composição da versão 3.
- [ ] Confirmar uso de Jakarta APIs em módulos que exigem (ex.: `jakarta.validation` / `jakarta.persistence`).
- [ ] Selecionar controller/adapter, service, client/repository, DTO e teste de referência.
- [ ] Anotar comandos reais de teste/build e abordagem de contrato.

### Critério de aceite
Versões validadas no build, comandos reproduzidos em ambiente autorizado, padrões revisados pelo TL; **não** incluir credenciais, configurações de produção, URLs privadas sensíveis ou dados reais na documentação publicada aqui.
