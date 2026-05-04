# proyects-wiki

Persistent knowledge base used as the **primary memory fallback** when Engram has no data for a topic. Together they form a two-layer memory system for Claude Code across all projects.

## Memory strategy

```
Engram (session memory, fast)
  └─ hit  → use it
  └─ miss → check proyects-wiki (this repo)
               └─ hit  → use it
               └─ miss → work from scratch, then save to both
```

At the end of every session, key decisions and discoveries are saved to Engram via `mem_session_summary`. Important or long-lived knowledge is also written here as Markdown so it survives Engram resets or is available on machines where Engram is not configured.

## What lives here

- Architecture decisions and conventions
- Lessons learned and gotchas per project
- Reusable snippets
- Code style guides
- Project-level context that is too large for a single Engram observation

## Structure

```
proyects-wiki/
├── INDEX.md              # Obsidian dashboard
├── proyectos/            # Per-project context and decisions
├── lecciones/            # Lessons learned, gotchas
├── estilos/              # Code style and conventions
├── snippets/             # Reusable code
└── _templates/           # Note templates
```

## Master plan

| File | Description |
|------|-------------|
| [`master-plan.md`](master-plan.md) | English setup guide — folder structure, templates, migration steps |
| [`master-plan.es.md`](master-plan.es.md) | Spanish version |

## Stack

- **Obsidian** — note-taking front-end with Dataview plugin
- **Engram** — Claude Code MCP plugin for fast session memory (primary)
- **proyects-wiki** — this repo, Markdown-based fallback memory (secondary)
- **Git** — version control and sync across machines
