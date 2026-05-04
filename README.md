# proyects-wiki

A file-based persistent memory system for Claude Code. Knowledge lives as plain Markdown, versioned in Git, readable in Obsidian — no plugins, no external services, no lock-in.

## How it works

Claude loads the wiki at session start via a `SessionStart` hook and gets a reminder to update it at the end of each turn via a `Stop` hook. Everything is automatic once the hooks are installed.

```
Session starts → INDEX.md injected into context automatically
       │
       ▼
Claude reads relevant notes when needed
       │
       ▼
Session ends → Claude checks if anything is worth saving
       │
       ▼
New note committed → git push
```

## What lives here

- Architecture decisions and conventions
- Lessons learned and gotchas per project
- Reusable snippets
- Code style guides
- Project-level context

## Structure

```
proyects-wiki/
├── INDEX.md              # Obsidian dashboard (auto-loaded by hook)
├── proyectos/            # Per-project context and decisions
├── lecciones/            # Lessons learned, gotchas
├── estilos/              # Code style and conventions
├── snippets/             # Reusable code
├── arquitectura/         # Architecture decisions
└── _templates/           # Note templates per type
```

## Coming from Engram?

If you used Engram before, you can migrate your observations into this wiki. See the **Post-Install Action** section in [`master-plan.md`](master-plan.md) for the migration steps.

## Master plan

| File | Description |
|------|-------------|
| [`master-plan.md`](master-plan.md) | English setup guide — hooks, templates, optional Engram migration |
| [`master-plan.es.md`](master-plan.es.md) | Spanish version |

## Stack

- **Obsidian** — note-taking front-end with Dataview plugin
- **Git** — version control and sync across machines
- **Claude Code hooks** — automatic session load and save reminders
