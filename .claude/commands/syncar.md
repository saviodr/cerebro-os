---
name: syncar
description: >
  Salva o workspace no GitHub (add + commit + push). Configura o remote na
  primeira vez. Use ao fim de um bloco de trabalho ou quando o usuário disser
  "syncar", "salva no github", "faz backup", "commit".
---

# /syncar — Backup no GitHub

## Estado atual
Rodar `git status --short` e `git remote get-url origin`.

## Primeira vez (sem remote)
Orientar: criar repositório **privado** e **vazio** (sem README) em github.com/new — nome sugerido: `[empresa]-os` — e trazer o link. Então:
```
git init (se preciso) → git add -A → git commit → git remote add origin [link] → git branch -M main → git push -u origin main
```

## Uso normal (com remote)
1. **`git pull` primeiro** — em workspace de equipe isso é obrigatório: traz o trabalho dos outros antes de subir o seu e evita conflito/sobrescrita. Se der conflito de merge, explicar em linguagem simples qual arquivo conflitou e resolver junto com o usuário — nunca usar force-push.
2. `git add -A` → revisar rapidamente o `git status` (nada de `.env` ou arquivo com cara de segredo) → `git commit -m "sync: [o que foi feito na sessão]"` → `git push`.
3. Confirmar em uma linha: "Salvo em [url]."

## Sem mudanças
"Tudo já sincronizado."

## Erro no push
Mostrar o erro em linguagem simples + o que fazer (internet? autenticação? conflito?). Nunca só despejar o erro cru.

## Regras
- NUNCA commitar `.env` ou credenciais (conferir antes do commit, não depois)
- NUNCA force-push
- Não explicar git a fundo, a menos que o usuário pergunte
