# 🧠 Installing the Thinking System: Global Memory-Wiki

Hey Claude. This file contains the instructions to install my "External Brain" on this PC. If there is no prior Engram data, skip the migration and focus on creating the empty structure, ready to start learning.

## 1. Directory Infrastructure
Clone this repo — the structure is already ready:
```bash
git clone git@github.com-imaginabit:imaginabit/proyects-wiki.git ~/projects/proyects-wiki
```

The folders `arquitectura/`, `lecciones/`, `estilos/`, `snippets/`, `proyectos/`, and `_templates/` are already created. No extra setup needed.

## 2. The Memory "Contract" (CLAUDE.md + hooks)

The behaviour contract lives in `CLAUDE.md` at the root of this repo. Claude Code reads it automatically whenever you work inside the project.

To make it available globally (across all projects), copy it to your user Claude config:
```bash
cp ~/projects/proyects-wiki/CLAUDE.md ~/.claude/CLAUDE.md
```

Then add the hooks to `~/.claude/settings.json` so Claude loads the wiki automatically at session start and gets a reminder to update it at the end of each turn. The exact JSON to paste is in the **Setup de hooks** section of `CLAUDE.md`.

## 3. Memory Note Template
Create `~/projects-wiki/_templates/nota_base.md`. Every time you generate new knowledge, use this frontmatter so my Obsidian can organise it:

```markdown
---
fecha: {{date}}
tecnologias: []
tipo: #leccion | #snippet | #arquitectura
estado: #activo
---
# [Clear Title]
## 📝 Summary
## 💻 Implementation / Code
[[Related Notes]]
```

## 4. Initial Style Guide
Create a base file at `~/projects-wiki/estilos/guia_estilo.md` where you will note down how I like my code written (e.g. "Preference for Clean Code", "Comments in Spanish", etc.).

## 5. The Obsidian Dashboard (INDEX.md)
Set up the main file so that, when Obsidian opens, it looks like this:

```markdown
# 🗄️ Global Development Wiki

## 🗺️ Navigation Map
- [[estilos/guia_estilo|🎨 My Code Standard]]
- [[snippets/comandos_terminal|⌨️ Quick Commands]]
- [[proyectos/lista_proyectos|📂 My Active Projects]]

## 🧠 Latest Knowledge Acquired
(Claude: list the last 5 files you created or edited here)
```

## 6. Post-Install Action
1. If content exists in `mcp__plugin_engram`, process durable observations and save them as notes following `_templates/nota_base.md`. Update `INDEX.md` with the new entries.
2. If NO prior Engram content exists, confirm the structure is ready: folders exist, `CLAUDE.md` is in place, and `INDEX.md` is open in Obsidian.
