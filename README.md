# proyects-wiki

Personal knowledge base that bridges Claude Code's persistent memory (Engram) with an Obsidian-compatible wiki, creating a unified second brain across all development projects.

## What this repo does

- Stores reusable notes, snippets, lessons learned, and architecture decisions as Markdown files
- Keeps an `INDEX.md` dashboard for quick navigation
- Organises content by type: `proyectos/`, `lecciones/`, `estilos/`, `snippets/`
- Every note follows a standard frontmatter template so Obsidian Dataview queries work out of the box
- Meant to be updated by Claude Code at the end of every session via `mem_session_summary`

## Master plan

| File | Description |
|------|-------------|
| [`master-plan.md`](master-plan.md) | English setup guide — folder structure, templates, Engram migration steps, INDEX dashboard |
| [`master-plan.es.md`](master-plan.es.md) | Spanish version of the same guide |

## Stack

- **Obsidian** — note-taking front-end with Dataview plugin
- **Engram** — Claude Code MCP plugin for persistent session memory
- **Git** — version control and sync
