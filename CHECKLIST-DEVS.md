# Checklist diário — devs da Squad Pitbull

> Use em toda história. No início, **não** envie “faz aí”. Primeiro peça análise sem modificação de arquivos.

### Antes do Copilot
- [ ] Sei qual é o objetivo e o resultado verificável.
- [ ] Tenho critérios de aceite e consigo explicar a história com minhas palavras.
- [ ] Identifiquei FED/BFF/SRV e as principais dúvidas.
- [ ] Verifiquei se o uso do material Confluence foi autorizado e sanitizado.
- [ ] Sei a versão e os padrões reais do repositório.
- [ ] Escolhi Ask/Plan antes de Agent, salvo tarefa curta e conhecida.

### Durante o trabalho
- [ ] **1. Refinar:** comparar resumo da IA com requisito, registrar ambiguidades.
- [ ] **2. Mapear:** confirmar arquivos que ela sugere, não aceitar paths imaginários.
- [ ] **3. Planejar:** definir fatias, limites, testes e critério de parada.
- [ ] **4. Implementar:** executar só a fatia aprovada.
- [ ] **5. Validar:** ler diff e rodar comandos reais.
- [ ] **6. Revisar:** checar segurança, contratos, erros, regressões e testes.
- [ ] **7. PR:** incluir evidência de resultado, não frases genéricas.

### Quando pedir ajuda
- Mudança envolve autenticação, dados pessoais, migração, contrato público ou regra ambígua.
- O Agent apaga testes, introduz dependência, muda arquitetura ou altera fora do escopo.
- Duas tentativas de correção sem avanço; mudar para diagnóstico e chamar um par.

### Como economizar IA
- Um objetivo por conversa; não misturar histórias.
- Contexto cirúrgico: 2–5 arquivos relevantes ao invés de copiar todo o projeto.
- Peça primeiro **lista de dúvidas**, depois plano e só então código.
- Priorize o comando de teste/build local, não peça à IA que “simule” a validação.
- Inclua somente erros relevantes e sanitizados; saída curta em tabelas/bullets.
- Evite refatoração oportunista; mantenha modelo/ferramentas estáveis se útil.
- Registre resumo do contexto validado no ticket para evitar reexplicação.

### Ao finalizar
**ID:** … · **Plano aprovado:** … · **Arquivos alterados:** … · **Testes e resultados observados:** … · **Riscos:** … · **Evidência no PR:** …
