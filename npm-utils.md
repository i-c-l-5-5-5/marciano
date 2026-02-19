# 20 Comandos npm/npx Essenciais para Manutenção de Projetos

---

## 📦 Atualização de Dependências

### 1. Verificar pacotes desatualizados

```bash
npm outdated
```
Lista todos os pacotes com versão atual, desejada e mais recente.

---

### 2. Atualizar todos os pacotes respeitando o semver

```bash
npm update
```

---

### 3. Atualizar um pacote específico para a versão mais recente

```bash
npm install nome-do-pacote@latest
```

---

### 4. Atualizar pacotes ignorando restrições de semver

```bash
npx npm-check-updates -u
```
Reescreve o `package.json` com as versões mais recentes. Após isso, rode `npm install`.

> **Dica:** Para atualizar apenas um grupo específico de dependências:
> ```bash
> npx npm-check-updates -u --dep prod   # só dependencies
> npx npm-check-updates -u --dep dev    # só devDependencies
> ```

---

### 5. Modo interativo do npm-check-updates

```bash
npx npm-check-updates -i
```
Permite escolher quais pacotes atualizar um a um.

---

## 🔷 tsconfig e TypeScript

### 6. Gerar um `tsconfig.json` padrão

```bash
npx tsc --init
```

---

### 7. Verificar erros de TypeScript sem compilar

```bash
npx tsc --noEmit
```
Ideal para CI ou validação rápida.

---

### 8. Inspecionar o tsconfig resolvido (com todas as extensões)

```bash
npx tsc --showConfig
```
Mostra o `tsconfig` final após todos os `extends`.

---

### 9. Migrar configurações de TypeScript 5 para 6

```bash
npx @andrewbranch/ts5to6 --fixBaseUrl .
```

---

## 🔧 Resolução de Conflitos e Integridade

### 10. Resolver conflitos no `package-lock.json`

```bash
npm install --package-lock-only
```
Regenera o lockfile sem instalar nada no `node_modules`.

---

### 11. Verificar inconsistências na árvore de dependências

```bash
npm ls
```

---

### 12. Auditar vulnerabilidades de segurança

```bash
npm audit
```

---

### 13. Corrigir vulnerabilidades automaticamente

```bash
npm audit fix
```

---

### 14. Forçar correção mesmo com breaking changes

```bash
npm audit fix --force
```
> ⚠️ **Atenção:** Use com cautela — pode quebrar compatibilidade.

---

### 15. Remover pacotes duplicados do `node_modules`

```bash
npm dedupe
```

---

## 🧹 Limpeza e Reset

### 16. Limpar o cache do npm

```bash
npm cache clean --force
```

---

### 17. Reinstalação limpa (equivalente ao clean install)

```bash
rm -rf node_modules && npm ci
```
O `npm ci` instala exatamente o que está no lockfile, sem tolerância a divergências.

---

## 🔍 Diagnóstico e Informações

### 18. Ver todas as versões instaladas em árvore

```bash
npm ls --depth=2
```

---

### 19. Ver de onde vem uma dependência transitiva

```bash
npm why nome-do-pacote
```
Explica por que um pacote está instalado e quem o exige.

---

### 20. Verificar o ambiente npm (versão, paths, configs)

```bash
npm doctor
```
Checa Node, npm, git, permissões e conectividade com o registry.

---

### 21. Rodar scripts com log detalhado para debug

```bash
npm run seu-script --loglevel verbose
```
Útil para identificar exatamente onde um build ou script falha.

---

## ✅ Fluxo Recomendado para Atualização Segura

```bash
# 1. Ver o que está desatualizado
npm outdated

# 2. Escolher o que atualizar de forma interativa
npx npm-check-updates -i

# 3. Reinstalar com lockfile limpo
npm ci

# 4. Verificar tipagem
npx tsc --noEmit

# 5. Auditar segurança
npm audit
```
