## Setup: Two-Layer Memory System (Claude Code + Obsidian)

Hey Claude. Act as a Platform Engineer. Your goal is to configure a two-layer persistent memory system — Engram as the fast primary layer, and this wiki as the fallback — following these exact instructions.

## Memory Architecture

```
Engram (session memory, fast)
  └─ hit  → use it
  └─ miss → check ~/projects-wiki (this repo)
               └─ hit  → use it
               └─ miss → work from scratch, then save to both
```

**Rule:** Never start from zero if either layer has relevant data. At the end of every session, save to Engram via `mem_session_summary`. For decisions or knowledge that must survive Engram resets or work across machines, also write a note here.

## 1. Folder Structure

```bash
mkdir -p ~/projects-wiki/{proyectos,lecciones,estilos,snippets,_templates}
touch ~/projects-wiki/INDEX.md
```

## 2. Note Template

Every note created in the wiki must use this frontmatter:

```markdown
---
fecha: {{date}}
tipo: #leccion | #snippet | #arquitectura | #config
proyecto_origen: [[ProjectName]]
tecnologias: []
estado: #finalizado
---

# [Title]

## Context

## Solution / Code
```

## 3. When to write a note here (vs. Engram only)

Write to this wiki when the knowledge:
- Should survive an Engram reset or plugin removal
- Is needed on a machine without Engram configured
- Is too large for a single Engram observation
- Is a stable convention unlikely to change (code style, architecture pattern)

Write to Engram only when knowledge is:
- Session-specific or short-lived
- Already captured in code or git history

## 4. Content Migration (Engram → Wiki)

When bootstrapping on a new machine or after an Engram reset:

1. **Access** — Read data from `mcp__plugin_engram`.
2. **Transform** — Convert durable observations into individual `.md` files.
3. **Classify** — Place notes in the right folder (`/lecciones`, `/snippets`, etc.).
4. **Link** — Cross-link notes that share a technology with `[[technology]]`.
5. **Cleanup** — Discard empty or duplicate entries.

## 5. Control Panel (INDEX.md)

```markdown
# 🧠 My Digital Brain (Global Wiki)

## Quick Access
- [[proyectos/Lista_Proyectos|My Projects]]
- [[estilos/Guia_Estilo|Code Style Guide]]

## Latest Lessons (Dataview)
\`\`\`dataview
LIST FROM "lecciones"
SORT fecha DESC
LIMIT 5
\`\`\`

---
*Claude: Update this index every time we add an important section.*
```

## 6. Global System Prompt (optional)

```
claude config set --system-prompt "Your two-layer memory: (1) Engram — check first. (2) ~/projects-wiki — fallback when Engram has no data. Read INDEX.md if starting fresh. Write durable knowledge to both layers. Every note must use the defined frontmatter template."
```

---

## Confirmation Checklist

Once setup is complete, confirm:

1. `~/projects-wiki` folder structure exists.
2. Engram is configured and reachable.
3. At least one note has been migrated or created as a test.

---

## Frequently Used Terminal Commands

```bash
# Sync wiki to remote
cd ~/projects-wiki && git add . && git commit -m "docs: update memory" && git push

# View Claude logs
claude logs

# Current Claude config
claude config get
```

### Git Helpers

```bash
# Undo last commit (keep changes staged)
git reset --soft HEAD~1

# Delete already-merged local branches
git branch --merged | grep -v "\*" | xargs -n 1 git branch -d
```
