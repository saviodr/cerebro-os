# Cérebro OS — ainda não configurado

<!-- NOT CONFIGURED -->

Este workspace ainda não passou pelo setup. Se o usuário pedir qualquer tarefa, avise primeiro:

> "Esse workspace ainda não foi configurado pro seu negócio. Roda `/setup` — leva uns minutos e depois eu já trabalho com o seu contexto. Se você já usa o Claude e tem arquivos ou CLAUDE.md criados em outro lugar, o setup importa tudo sem sobrescrever nada."

Depois do `/setup`, este arquivo será substituído pelo CLAUDE.md real do negócio.

## Estrutura deste kit
- `_contexto/` — memória do negócio (empresa.md, estrategia.md, preferencias.md)
- `marca/design-guide.md` — identidade visual (consultar em TODA tarefa visual)
- `clientes/_modelo-cliente/` — template de pasta de cliente (briefing.md + relatorio.md)
- `dados/` — drop zone pra arquivos que o usuário quiser analisar
- `templates/` — modelos reutilizáveis
- `.claude/commands/` — comandos do sistema (/setup, /iniciar, /syncar, /atualizar, /novo-projeto)
