---
name: Code Review
description: Revisão de código com checklist estruturado e scoring por confiança para filtrar falsos positivos
---

# Code Review

Skill para revisão de código com abordagem sistemática e multi-dimensional.

## Checklist de Review

### 1. Correção

- [ ] A lógica resolve o problema proposto?
- [ ] Edge cases estão tratados?
- [ ] Inputs inválidos são rejeitados adequadamente?
- [ ] Retornos são consistentes (não mistura null/undefined/throw)?

### 2. Segurança

- [ ] Sem injection (SQL, command, XSS)?
- [ ] Sem secrets hardcoded?
- [ ] Inputs são sanitizados/validados?
- [ ] Sem uso de `eval()`, `innerHTML`, `dangerouslySetInnerHTML`?

### 3. Performance

- [ ] Sem loops desnecessários ou complexidade O(n²)?
- [ ] Sem re-renders desnecessários (React)?
- [ ] Queries são otimizadas (N+1, índices)?
- [ ] Sem memory leaks (event listeners, timers)?

### 4. Manutenibilidade

- [ ] Nomes de variáveis/funções são descritivos?
- [ ] Funções têm responsabilidade única (SRP)?
- [ ] Sem magic numbers — constantes nomeadas?
- [ ] Código duplicado foi extraído?

### 5. Tipagem (TypeScript)

- [ ] Sem `any` desnecessário?
- [ ] Interfaces/types estão definidos?
- [ ] Generics usados quando apropriado?
- [ ] Union types ao invés de booleans para estados?

### 6. Testes

- [ ] Mudança tem teste correspondente?
- [ ] Testes cobrem happy path + edge cases?
- [ ] Mocks não escondem bugs reais?
- [ ] Assertions são específicas (não só `.toBeTruthy()`)?

## Scoring de Confiança

Ao reportar issues, classifique cada uma:

| Nível         | Confiança | Ação                     |
| ------------- | --------- | ------------------------ |
| 🔴 Crítico    | >90%      | Bloqueia merge           |
| 🟡 Importante | 70-90%    | Revisar antes do merge   |
| 🟢 Sugestão   | 50-70%    | Nice to have             |
| ⚪ Nit        | <50%      | Ignorar se não concordar |

## Template de Feedback

```markdown
### [🔴/🟡/🟢/⚪] Título curto do problema

**Arquivo:** `path/to/file.ts:42`
**Categoria:** Segurança | Performance | Correção | Manutenibilidade
**Confiança:** X%

**Problema:** Descrição do que está errado e por quê.

**Sugestão:**
\`\`\`typescript
// código sugerido
\`\`\`
```
