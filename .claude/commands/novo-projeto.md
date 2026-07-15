---
name: novo-projeto
description: >
  Cria a pasta de um cliente ou projeto novo com contexto próprio, seguindo o
  padrão do workspace. Use quando o usuário chamar /novo-projeto, "cliente novo",
  "criar pasta pro cliente X", "projeto novo".
---

# /novo-projeto — Cliente ou projeto novo

## Passo 1 — Entender (uma pergunta por vez; pular o que já foi respondido)
1. Nome do projeto/cliente
2. Tipo: cliente (serviço pra alguém) · produto próprio · conteúdo · interno
3. O que precisa ser entregue, em poucas palavras
4. Prazo, orçamento ou ferramenta específica

## Passo 2 — Onde criar
- **Cliente** → `clientes/[nome]/` usando o template `clientes/_modelo-cliente/` (**briefing.md + relatorio.md** — cliente NÃO ganha CLAUDE.md próprio; o contexto pesado fica no CLAUDE.md raiz e o briefing herda dele)
- **Produto / interno** → `projetos/[nome]/` com um CLAUDE.md curto próprio (menos de 30 linhas — cresce com o uso)
- **Conteúdo** → `conteudo/[nome]/`

Confirmar o local antes de criar. Nunca mover pasta existente sem perguntar. Se a pasta já existe, só gerar os arquivos dentro.

## Passo 3 — Gerar
- **briefing.md** (cliente): o que é, contato, escopo/entregas (checklist), contexto (prazo/orçamento/ferramentas), decisões e pendências. Curto — só decisão e pendência, sem prosa.
- **relatorio.md** (cliente): registro corrente de entregas e resultados.
- **CLAUDE.md** (produto/interno): o que é, escopo, contexto, regras específicas.

## Passo 4 — Registrar
Adicionar a pasta nova na estrutura de pastas do CLAUDE.md raiz e, se for cliente, oferecer adicionar na lista de clientes de `_contexto/empresa.md`.

## Regras
- Direto, sem cerimônia
- Não criar subpastas a menos que o usuário peça
- Arquivos de projeto são enxutos: decisão e pendência, não a história da conversa
