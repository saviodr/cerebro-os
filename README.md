# 🧠 Cérebro OS

**O sistema operacional de IA da sua empresa** — por [Zapiens AI](https://zapiensai.com.br).

O Cérebro OS transforma o Claude Code no cérebro da sua operação: contexto do negócio organizado, identidade visual aplicada em tudo que ele gera, skills pros seus fluxos de trabalho e backup automático no GitHub. Instala em minutos e aprende com o uso.

## Instalação

### Pré-requisitos
- [VS Code](https://code.visualstudio.com/) com a extensão **Claude Code** instalada
- [Git](https://git-scm.com/download/win) instalado
- Conta no [GitHub](https://github.com) (pro backup do seu workspace)

### Opção 1 — Pelo próprio Claude (recomendada)

Abra o Claude Code em qualquer pasta e cole isso:

```
Clone o repositório https://github.com/saviodr/cerebro-os.git numa pasta chamada
"[nome-da-sua-empresa]-os" na minha pasta de usuário, remova a pasta .git de dentro
dela, abra essa pasta como workspace e rode /setup
```

### Opção 2 — Manual

```powershell
git clone https://github.com/saviodr/cerebro-os.git minha-empresa-os
cd minha-empresa-os
Remove-Item -Recurse -Force .git
```

Depois abra a pasta no VS Code (`File → Open Folder`), abra o Claude Code e rode `/setup`.

> 💡 **Já usa o Claude e tem arquivos/CLAUDE.md espalhados?** O `/setup` detecta o que você já tem e **importa em vez de sobrescrever**. Nada do seu trabalho se perde.

## O que vem dentro

| Comando | O que faz |
|---|---|
| `/setup` | Configura o sistema pro seu negócio (entrevista + importação do que já existe) |
| `/iniciar` | Começa a sessão de trabalho com o contexto carregado |
| `/syncar` | Salva tudo no GitHub (backup do workspace) |
| `/atualizar` | Varre o projeto e atualiza os arquivos de contexto desatualizados |
| `/novo-projeto` | Cria pasta de cliente/projeto novo com contexto próprio |

```
cerebro-os/
├── .claude/commands/   → os comandos acima
├── _contexto/          → memória do negócio (empresa, estratégia, preferências)
├── marca/              → identidade visual (design-guide.md)
├── clientes/           → uma pasta por cliente (briefing + relatório)
├── dados/              → drop zone pra arquivos analisar (CSV, XLSX, PDF, prints)
├── templates/          → modelos reutilizáveis
└── CLAUDE.md           → o cérebro: instruções que o Claude lê em toda conversa
```

## Como funciona

1. **`/setup`** entrevista você (ou importa o que já existe) e gera o contexto do negócio
2. O Claude passa a ler esse contexto em **toda conversa** — sem repetir briefing nunca mais
3. Quando você corrige algo, ele **pergunta se quer salvar** — o sistema melhora com o uso
4. **`/syncar`** guarda tudo no GitHub — nada se perde, e o time não sobrescreve o trabalho um do outro

---

Feito pela **Zapiens AI** · Consultoria de IA pra operação de empresas · Feira de Santana/BA
