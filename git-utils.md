# 20 Comandos Git Úteis para o Dia a Dia

## Inspeção e Histórico

### 1. Log visual e compacto
```git log --oneline --graph --all --decorate```

Exibe o histórico de commits em formato de árvore, ideal para visualizar branches.

### 2. Ver o que mudou em um commit específico
```git show <hash>```

### 3. Buscar em qual commit uma string apareceu
```git log -S "texto que você procura" --oneline```

### 4. Ver quem alterou cada linha de um arquivo
```git blame <arquivo>```

### 5. Histórico de um arquivo específico
```git log --follow -p <arquivo>```

O `--follow` rastreia renomeações do arquivo.

---

## Branches

### 6. Listar branches remotas e locais
```git branch -a```

### 7. Deletar branch local e remota de uma vez
```bash
git branch -d minha-branch
git push origin --delete minha-branch
```

### 8. Renomear branch atual
```git branch -m novo-nome```

### 9. Criar e já mudar para nova branch
```git switch -c minha-feature```

---

## Correções e Ajustes

### 10. Corrigir a mensagem do último commit
```git commit --amend -m "Nova mensagem correta"```

### 11. Adicionar esquecimento ao último commit (sem mudar mensagem)
```bash
git add arquivo-esquecido.js
git commit --amend --no-edit
```

### 12. Desfazer o último commit mantendo as alterações
```git reset --soft HEAD~1```

### 13. Descartar alterações de um arquivo específico
```git restore <arquivo>```

### 14. Remover arquivo do stage sem perder as edições
```git restore --staged <arquivo>```

---

## Stash

### 15. Salvar trabalho em progresso com nome
```git stash push -m "wip: ajuste no formulário"```

### 16. Listar e aplicar um stash específico
```bash
git stash list
git stash apply stash@{2}
```

---

## Sincronização

### 17. Baixar atualizações sem aplicar (inspecionar antes)
```bash
git fetch origin
git diff HEAD origin/main
```

### 18. Puxar com rebase (evita commits de merge desnecessários)
```git pull --rebase origin main```

---

## Utilitários Avançados

### 19. Encontrar o commit que introduziu um bug (busca binária)
```bash
git bisect start
git bisect bad          # commit atual tem o bug
git bisect good <hash>  # hash onde estava funcionando
```

O Git navega automaticamente pelos commits até isolar o culpado.

### 20. Aplicar um commit específico de outra branch
```git cherry-pick <hash>```

Muito útil para trazer um hotfix de uma branch para outra sem merge completo.

---

> 💡 **Dica bônus:** crie aliases para os comandos mais usados no seu `~/.gitconfig`:
>
> ```git config --global alias.lg "log --oneline --graph --all --decorate"```
>
> Assim você roda `git lg` no lugar do comando longo.
```