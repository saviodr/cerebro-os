---
name: iniciar
description: >
  Abre a sessão de trabalho: carrega o contexto do negócio e pergunta o que
  o usuário quer fazer. Use no começo de cada sessão nova, ou quando o usuário
  chamar /iniciar, "bora trabalhar", "começar o dia".
---

# /iniciar — Abrir a sessão

1. Ler `_contexto/empresa.md`, `_contexto/estrategia.md` e `_contexto/preferencias.md`.
2. Se algum tiver `<!-- NOT CONFIGURED -->` ou não existir → avisar: "O sistema ainda não foi configurado. Roda `/setup` primeiro."
3. Se o workspace é git com remote e tem equipe: rodar `git pull` antes de qualquer coisa (pega o trabalho dos colegas) e avisar em uma linha se veio algo novo.
4. Apresentar um resumo de NO MÁXIMO 5 linhas:

```
Contexto carregado.
**Negócio:** [uma linha]
**Foco agora:** [prioridade de estrategia.md]
**Pendências:** [até 3 itens de tarefas.md, se houver]

O que vamos fazer hoje?
```

## Regras
- Sem "Olá! Fico feliz em ajudar!" — direto ao ponto
- Não listar os arquivos lidos, só usar o contexto
- Depois do resumo, esperar o usuário dizer o que quer
