## Setup: Global Memory System (Claude Code + Obsidian)

Hey Claude. Act as a Platform Engineer. Your goal is to configure my persistent memory system on this PC following these exact instructions.

## 1. Folder Structure

Create the following directory structure under the user's home:

```bash
mkdir -p ~/projects-wiki/{proyectos,lecciones,estilos,snippets,_templates}
touch ~/projects-wiki/INDEX.md
```

## 2. Master Note Template

Every note you create in the wiki must use this frontmatter format:

```markdown
---
fecha: {{date}}
tipo: #leccion | #snippet | #arquitectura | #config
proyecto_origen: [[ProjectName]]
tecnologias: []
estado: #finalizado
---

# [Title]

## 📝 Context

## 💻 Solution / Code
```

## 3. Global System Prompt Configuration

Run this configuration command internally so it persists in Claude Code:

```
claude config set --system-prompt "Your global memory lives in ~/projects-wiki/. Check INDEX.md at startup. You have permanent read/write permission in ~/projects-wiki/ to keep my knowledge base up to date across projects. Use Obsidian-compatible Markdown [[links]]. Every new note MUST use the defined frontmatter template."
```

## 4. Content Migration (Engram → Wiki)

Perform the following migration steps:

1. **Access** — Read data from `mcp__plugin_engram`.
2. **Transform** — Convert each Engram entry into an individual `.md` file inside `~/projects-wiki/`.
3. **Classify** — Move notes to their folder (`/lecciones`, `/snippets`, etc.) based on content.
4. **Link** — If two notes reference the same technology, add an `[[technology]]` cross-link between them.
5. **Cleanup** — Discard or merge empty or duplicate Engram entries.

## 5. Control Panel (INDEX.md)

Overwrite `~/projects-wiki/INDEX.md` with the following Obsidian dashboard:

```markdown
# 🧠 My Digital Brain (Global Wiki)

## 📌 Quick Access
- [[proyectos/Lista_Proyectos|📁 My Projects]]
- [[estilos/Guia_Estilo|🎨 Code Style Guide]]

## 🕒 Latest Lessons (Dataview)
\`\`\`dataview
LIST FROM "lecciones"
SORT fecha DESC
LIMIT 5
\`\`\`

---
*Claude: Update this index every time we add an important section.*
```

---

## Confirmation Checklist

Claude, once you finish executing these steps, confirm:

1. The `~/projects-wiki` folder exists.
2. You successfully migrated Engram data.
3. The `claude config set` command executed correctly.

---

## Frequently Used Terminal Commands

```markdown
---
fecha: 2024-03-20
tipo: #snippet
proyecto_origen: [[Global]]
tecnologias: [#terminal, #bash, #git]
estado: #finalizado
---
```

### Memory Management
- **View Claude logs:** `claude logs`
- **Current config:** `claude config get`
- **Sync wiki:** `cd ~/projects-wiki && git add . && git commit -m "Update memory" && git push`

### General Development
- **Clear Node cache:** `npm cache clean --force`
- **Kill process on port (e.g. 3000):** `lsof -ti:3000 | xargs kill -9`
- **Docker: clean everything:** `docker system prune -a --volumes`

### Git
- **Undo last commit (keep changes):** `git reset --soft HEAD~1`
- **Delete already-merged local branches:** `git branch --merged | grep -v "\*" | xargs -n 1 git branch -d`

---
*Claude: If I run a complex command successfully in the terminal, ask me whether to add it to this list automatically.*
