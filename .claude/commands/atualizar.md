---
name: atualizar
description: >
  Varre o estado real do workspace e corrige os arquivos de contexto que ficaram
  pra trás (CLAUDE.md, _contexto/, marca/design-guide.md). Use quando o usuário
  chamar /atualizar, "atualiza o contexto", "sincroniza a memória", ou ao fim de
  uma sessão longa com muitas mudanças.
---

# /atualizar — Manutenção de contexto

## Passo 1 — Estado real
Levantar: pastas de primeiro nível (ignorar `.git`, `.claude`, `dados`), skills/comandos instalados, MCPs configurados, últimos commits (`git log --oneline -5` + `git status`).

## Passo 2 — Estado documentado
Ler CLAUDE.md, `_contexto/empresa.md`, `_contexto/estrategia.md`, `_contexto/preferencias.md`, `marca/design-guide.md`.

## Passo 3 — Comparar
- Estrutura de pastas do CLAUDE.md bate com as pastas reais? Cliente/projeto novo sem registro?
- Ferramentas "conectadas" estão de fato configuradas? Tem MCP novo não documentado?
- A prioridade em estrategia.md ainda é o foco (a julgar pelos arquivos recentes)? Prazo vencido?
- design-guide.md preenchido? Logo referenciado existe?

## Passo 4 — Diagnóstico + aplicar
Apresentar em três blocos: **Em dia** / **Desatualizado** (o que está errado → o que deveria ser) / **Não configurado**. Pedir aprovação e aplicar tudo de uma vez (ou item a item se o usuário preferir).

Se estiver tudo certo: dizer isso em uma linha e parar — não inventar ajuste trivial.

## Regras
- Editar só as linhas relevantes, nunca reformatar arquivo inteiro
- Não inferir o que não dá pra inferir — perguntar
- Setup recente + poucos commits = provavelmente está tudo em dia
