---
title: "Git na Prática: Do Básico ao Fluxo Profissional"
date: 2024-04-01
tags: ["git", "versionamento", "ferramentas"]
---

Git é uma ferramenta indispensável para qualquer desenvolvedor. Mas vai além
do básico `add`, `commit` e `push` — existe um conjunto de práticas que
separam um fluxo amador de um profissional.

---

## Comandos Fundamentais

```bash
# Configuração inicial (faça uma vez)
git config --global user.name "othiagob"
git config --global user.email "seuemail@exemplo.com"

# Começar um repositório
git init meu-projeto
cd meu-projeto

# Ciclo básico de trabalho
git status                    # ver o que mudou
git add arquivo.txt           # preparar arquivo específico
git add .                     # preparar tudo
git commit -m "feat: add login screen"
git push origin main
```

---

## Conventional Commits

Mensagens de commit bem escritas contam a história do projeto. Use o padrão
**Conventional Commits**:

```
<tipo>(<escopo opcional>): <descrição>

[corpo opcional]

[rodapé opcional]
```

### Tipos mais usados

| Tipo       | Quando usar                                      |
|------------|--------------------------------------------------|
| `feat`     | Nova funcionalidade                              |
| `fix`      | Correção de bug                                  |
| `docs`     | Mudança na documentação                          |
| `style`    | Formatação, sem mudança de lógica                |
| `refactor` | Refatoração, sem nova feature nem bug fix        |
| `test`     | Adição ou correção de testes                     |
| `chore`    | Tarefa de manutenção (deps, config, CI)          |

### Exemplos reais

```bash
git commit -m "feat(auth): add JWT refresh token support"
git commit -m "fix(api): handle null response from payment gateway"
git commit -m "docs: update README with Docker instructions"
git commit -m "chore(deps): bump Hugo from 0.120 to 0.157"
```

---

## Branches e Fluxo de Trabalho

```bash
# Criar e mudar para nova branch
git checkout -b feature/minha-feature

# Listar branches
git branch -a

# Merge com fast-forward desativado (mantém histórico limpo)
git merge --no-ff feature/minha-feature

# Deletar branch após merge
git branch -d feature/minha-feature
git push origin --delete feature/minha-feature
```

### Estratégia de branches

```
main          ─────●─────────────────●────────●──→
                   │                 ↑        ↑
develop       ─────●────●────●───────●──→     │
                        │    ↑                │
feature/login ──────────●────●               │
                                              │
hotfix/crash  ───────────────────────────●───●──→
```

---

## Comandos Avançados que Fazem Diferença

### Rebase interativo — reescrever história

```bash
# Reescrever os últimos 3 commits
git rebase -i HEAD~3

# No editor, você pode:
# pick   = manter como está
# reword = alterar mensagem
# squash = juntar com commit anterior
# drop   = remover commit
```

### Stash — guardar mudanças temporariamente

```bash
# Guardar mudanças sem commitar
git stash push -m "wip: form validation"

# Ver lista de stashes
git stash list

# Recuperar último stash
git stash pop

# Recuperar stash específico
git stash apply stash@{2}
```

### Log visual e útil

```bash
# Log compacto e colorido
git log --oneline --graph --all --decorate

# Buscar commits por conteúdo
git log -S "nome_da_função" --source --all

# Ver quem alterou cada linha
git blame arquivo.py
```

---

## Alias Úteis para o `.gitconfig`

```ini
[alias]
    # Status compacto
    st = status -sb

    # Log bonito
    lg = log --oneline --graph --all --decorate

    # Desfazer último commit (mantém as mudanças)
    undo = reset HEAD~1 --mixed

    # Commitar tudo rapidamente
    ca = commit -am

    # Limpar branches já mergeadas
    cleanup = "!git branch --merged | grep -v '\\*\\|main\\|develop' | xargs -n 1 git branch -d"
```

---

## Dicas de Ouro

> **Commit cedo, commit sempre.** Commits pequenos e frequentes são mais fáceis
> de revisar, reverter e entender do que um mega-commit com 50 arquivos.

1. **Nunca force-push em branches compartilhadas** (`main`, `develop`)
2. **Revise antes de commitar** — `git diff --staged` mostra o que vai entrar
3. **Use `.gitignore`** — não versione `node_modules/`, `.env`, binários
4. **Tags para releases** — `git tag -a v1.0.0 -m "Primeira versão estável"`

---

Dominar Git transforma a forma como você trabalha. Invista tempo nisso — vale
cada minuto. 🎯
