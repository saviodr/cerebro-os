---
name: setup
description: >
  Instala o Cérebro OS pro negócio do usuário. Primeiro mapeia o que JÁ existe
  (CLAUDE.md antigos, pastas de clientes, contexto de outros assistentes) e importa
  sem sobrescrever; depois entrevista o usuário só sobre o que faltou e gera
  CLAUDE.md, arquivos de contexto, identidade visual e estrutura de pastas.
  Use quando o usuário chamar /setup, quando _contexto/empresa.md estiver vazio
  ou com <!-- NOT CONFIGURED -->, ou quando disser "configurar o sistema".
---

# /setup — Instalação do Cérebro OS

## Regra de ouro (vale pro fluxo inteiro)

**NUNCA sobrescrever ou apagar conteúdo que o usuário já tinha sem mostrar antes e ter um "sim" explícito.** Todo conteúdo pré-existente é importado, consolidado ou preservado — nunca perdido. Se houver dúvida entre sobrescrever e perguntar, perguntar.

## Etapa 0 — Já foi configurado?

Se `_contexto/empresa.md` existe COM conteúdo real (sem `<!-- NOT CONFIGURED -->`): avisar que o setup já rodou e perguntar se quer refazer tudo ou só atualizar uma parte (nesse caso, sugerir `/atualizar`).

## Etapa 1 — Mapear o que JÁ existe (modo brownfield)

Antes de qualquer pergunta, varrer o terreno. Procurar:

1. **Neste workspace:** CLAUDE.md soltos, pastas de clientes/projetos já criadas, arquivos de contexto de qualquer formato
2. **Na máquina:** `~/.claude/CLAUDE.md` (global) e memórias em `~/.claude/projects/`
3. **Perguntar ao usuário:** "Você ou alguém do time já usou o Claude (Desktop, web ou Code) pra organizar coisas do negócio — tipo arquivos de contexto por cliente? Se sim, me diz onde estão que eu importo."

### Se encontrar material existente

Apresentar um inventário do que foi achado (ex.: "encontrei 8 CLAUDE.md de clientes criados no Claude Desktop") e propor a consolidação no padrão do Cérebro OS:

- **Conteúdo sobre O NEGÓCIO** (quem é a empresa, como funciona) → consolida em `_contexto/empresa.md` e no CLAUDE.md raiz
- **Conteúdo POR CLIENTE** → vira `clientes/[nome]/briefing.md` (o padrão é **1 CLAUDE.md por negócio, não por cliente** — cliente tem briefing.md + relatorio.md; isso evita contexto duplicado e pesado)
- **Preferências de escrita/tom** → `_contexto/preferencias.md`

Mostrar o plano de consolidação ANTES de executar, arquivo por arquivo, e só aplicar com aprovação. Os arquivos originais não são apagados — se o usuário quiser, mover pra uma pasta `_importado/` como backup.

Depois de importar, **pular as perguntas da Etapa 2 que já foram respondidas pelo material** — confirmar o resumo com o usuário e perguntar só o que faltou.

### Se o usuário usa outro assistente (ChatGPT, Gemini, Claude web)

Entregar este prompt pra ele colar lá e trazer a resposta:

```
Preciso exportar o contexto do meu negócio das nossas conversas pra configurar uma
nova ferramenta. Responda o que sabe sobre mim (deixe em branco o que não souber):
NOME / NEGÓCIO / O QUE FAZ / PRINCIPAIS ATIVIDADES / CLIENTES (externos, interno ou
ambos) / EQUIPE / FERRAMENTAS / IDENTIDADE VISUAL / TOM DE VOZ / O QUE EVITAR /
OUTROS DETALHES RELEVANTES
```

Extrair da resposta, montar resumo, confirmar, e pular o que já foi respondido.

### Se não encontrar nada

Seguir direto pra Etapa 2 (setup limpo).

## Etapa 2 — Entrevista (só o que faltou)

Uma pergunta por vez, conversa natural — nunca despejar a lista inteira:

1. Nome do usuário e do negócio
2. O que mais produz no dia a dia (conteúdo, propostas, relatórios, campanhas...)
3. Atende clientes externos, uso interno, ou ambos
4. Foco principal dos próximos meses
5. Ferramentas que usa (Notion, Drive, Canva, Meta Ads, WhatsApp...)
6. Identidade visual — aceitar em qualquer formato: URL do site (analisar com WebFetch), prints na pasta `dados/`, descrição em texto, ou "ainda não tenho" (deixar template pra depois). Sempre perguntar pelo logo (PNG/SVG na pasta `marca/`)
7. Como prefere que o Claude escreva / o que incomoda em texto de IA
8. Equipe ou solo — **se tem equipe usando o Claude junto: anotar pra configurar o fluxo git multiusuário (cada pessoa com sua conta e seu clone; pull antes de trabalhar, /syncar ao terminar)**

Detectar o perfil: agência / freelancer / solopreneur / criador / empresa / profissional.

## Etapa 3 — Gerar os arquivos (tudo de uma vez no final)

1. **`CLAUDE.md` raiz** — o que é o workspace, sobre o negócio, estrutura de pastas, tom de voz, ferramentas conectadas + as três seções permanentes: *ler `_contexto/` no início de toda conversa; consultar `marca/design-guide.md` em toda tarefa visual; aprender com correções (quando o usuário corrigir algo permanente, perguntar se quer salvar e gravar no arquivo certo)*. Enxuto: aponta pros docs, não duplica.
2. **`_contexto/empresa.md`** — quem é, o que faz, perfil, equipe, ferramentas, entregas
3. **`_contexto/estrategia.md`** — fase, prioridade principal, o que pode esperar
4. **`_contexto/preferencias.md`** — tom de voz, o que evitar, estilo
5. **`marca/design-guide.md`** — preenchido com o que foi coletado (ou template comentado)
6. **Estrutura de pastas** — propor a estrutura do perfil detectado, MOSTRAR antes de criar, ajustar conforme o usuário quiser. Agência/freelancer: `clientes/` (uma pasta por cliente, com `_modelo-cliente/` de template) + `conteudo/` + `tarefas.md`. Nunca mover pastas existentes sem perguntar.
7. **Conectores (MCP)** — cruzar as ferramentas citadas com os conectores disponíveis (Claude web → Configurações → Conectores pros nativos: Gmail, Drive, Notion, Canva...). Oferecer instalar agora ou anotar em `tarefas.md`.

## Etapa 4 — Fechamento

Resumir o que foi criado/importado e orientar os dois próximos passos:

1. **Segurança:** chaves de API sempre em `.env` (já protegido pelo `.gitignore` — nunca sobe pro GitHub)
2. **Backup:** rodar `/syncar` pra conectar o workspace ao GitHub da empresa. Se tem equipe: repositório compartilhado + cada pessoa clona o seu; pull antes, push depois — é o que impede um sobrescrever o trabalho do outro.

## Regras
- Tom direto e humano, sem entusiasmo forçado
- Respostas vagas → uma pergunta de acompanhamento antes de seguir
- Gerar arquivos todos de uma vez no final, não durante a entrevista
- No fechamento, resumir — não listar linha por linha o que foi escrito
