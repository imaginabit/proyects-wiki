# 🧠 Installing the Thinking System: Global Memory-Wiki

Hey Claude. This file contains the instructions to install my "External Brain" on this PC. If there is no prior Engram data, skip the migration and focus on creating the empty structure, ready to start learning.

## 1. Directory Infrastructure
Create the folder system under the user's home so it is accessible from any project:
```bash
mkdir -p ~/projects-wiki/{arquitectura,lecciones,estilos,snippets,proyectos,_templates}
touch ~/projects-wiki/INDEX.md
```

## 2. The Memory "Contract" (System Prompt)
Configure your global behaviour so you always operate under this system:
```bash
claude config set --system-prompt "Your global memory lives in ~/projects-wiki/.
1. Check INDEX.md at the start of every session.
2. If we make a technical decision or fix a bug, ask me before documenting it in ~/projects-wiki/lecciones/ or snippets/.
3. Always use Obsidian [[links]] format to connect concepts.
4. Stay consistent with my style guide at ~/projects-wiki/estilos/guia_estilo.md."
```

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
1. If content exists in `mcp__plugin_engram`, process it and move it into this new structure following the template.
2. If NO prior content exists, confirm the structure is ready to record the first session.
