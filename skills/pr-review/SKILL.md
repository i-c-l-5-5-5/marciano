---
name: PR Review
description: Review estruturado de Pull Requests com foco em qualidade, testes, tipos e simplificação
---

# PR Review

Skill para revisar PRs de forma estruturada, cobrindo 6 dimensões.

## Fluxo de Review

```
1. Contexto → 2. Testes → 3. Erros → 4. Tipos → 5. Qualidade → 6. Simplificação
```

## 1. Contexto e Propósito

- [ ] PR tem descrição clara do que muda e por quê
- [ ] Tamanho razoável (<400 linhas de diff, idealmente <200)
- [ ] Mudança é coerente (não mistura features com refactors)
- [ ] Branch name segue convenção

## 2. Testes

- [ ] Novos testes para novas funcionalidades
- [ ] Testes existentes atualizados para mudanças de comportamento
- [ ] Edge cases testados
- [ ] Testes não são frágeis (não dependem de ordem, tempo, etc)
- [ ] Coverage não diminuiu

**Red flags:**

- Testes removidos sem justificativa
- `skip()` ou `.only()` commitado
- Assertions vagas (`.toBeTruthy()` em vez de valor específico)

## 3. Error Handling

- [ ] Operações async têm try-catch ou `.catch()`
- [ ] Erros são logados com contexto suficiente
- [ ] Erros não são silenciados (`catch(e) {}`)
- [ ] Fallbacks fazem sentido para o negócio
- [ ] Sem falhas silenciosas (promises não-tratadas)

## 4. Design de Tipos (TypeScript)

- [ ] Sem `any` — usar `unknown` + type guard se necessário
- [ ] Interfaces definem contratos claros
- [ ] Enums ou union types para estados (não strings/booleans)
- [ ] Generics onde há reuso de lógica com tipos diferentes
- [ ] Tipos exportados para consumidores da API

## 5. Qualidade de Código

- [ ] DRY — sem código duplicado
- [ ] SRP — funções com responsabilidade única
- [ ] Nomes autodescritivos (sem `data`, `info`, `temp`, `x`)
- [ ] Sem side effects escondidos
- [ ] Complexidade ciclomática baixa (poucos if/else aninhados)
- [ ] Constantes nomeadas (sem magic numbers)

## 6. Oportunidades de Simplificação

- [ ] Código que pode ser removido (dead code)
- [ ] Abstrações que podem ser simplificadas
- [ ] Lógica condicional que pode ser reduzida
- [ ] Uso de métodos nativos ao invés de implementações manuais

```typescript
// ❌ Manual
const result = [];
for (const item of items) {
  if (item.active) result.push(item.name);
}

// ✅ Nativo
const result = items.filter((i) => i.active).map((i) => i.name);
```

## Template de Review

```markdown
## 📋 PR Review: #<número>

**Veredicto:** ✅ Aprovado | 🔄 Mudanças necessárias | ❌ Rejeitar

### Resumo

Breve resumo das mudanças e opinião geral.

### Issues encontradas

1. [🔴/🟡/🟢] Descrição
2. ...

### Pontos positivos

- O que foi bem feito

### Sugestões (não-bloqueantes)

- Melhorias opcionais
```
