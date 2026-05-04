# Memory-Wiki: Instrucciones para Claude

Este repo es el sistema de memoria persistente para Claude Code. Knowledge vive como Markdown plano, versionado en Git, sin plugins externos.

## Flujo de sesión (automático via hooks)

```
SessionStart hook → inyecta INDEX.md como contexto
       │
       ▼
Leer notas relevantes cuando haga falta
       │
       ▼
Stop hook → revisar si algo merece guardarse
       │
       ▼
Nueva nota → commit → push a develop
```

El hook `SessionStart` en `~/.claude/settings.json` inyecta `INDEX.md` al arrancar. No hace falta leerlo manualmente.

Si los hooks no están instalados: leer `~/projects/proyects-wiki/INDEX.md` manualmente al inicio de cada sesión.

## Al terminar una sesión — cuándo guardar

Guardar cuando:
- Se tomó una decisión técnica (arquitectura, patrón, convención)
- Se resolvió un bug con causa no obvia
- Se aprendió un gotcha o comportamiento inesperado
- Se estableció una convención de código o proyecto

No guardar cuando sea:
- Contexto específico de una tarea puntual
- Algo ya evidente en el código o en git

## Cuándo escribir en cada carpeta

| Carpeta | Cuándo |
|---|---|
| `lecciones/` | Bug resuelto, gotcha, aprendizaje técnico reutilizable entre proyectos |
| `snippets/` | Código que se va a copiar en otro proyecto |
| `arquitectura/` | Decisión de diseño con alternativas y consecuencias |
| `proyectos/` | Contexto de un proyecto específico (stack, links, decisiones clave) |
| `estilos/` | Convención de código, guía de estilo, preferencia de naming |

**`lecciones/` vs "Lecciones aprendidas" en `proyectos/`:**
- `lecciones/` = nota standalone, reutilizable en cualquier proyecto
- Sección en `proyectos/` = enlace `[[lecciones/nombre]]` a esas notas, filtrado por proyecto

## Cómo crear una nota

1. Usar la plantilla de `_templates/` que corresponda al tipo
2. Guardar en la carpeta correcta
3. Actualizar sección "🧠 Últimos Conocimientos Adquiridos" en `INDEX.md`
4. Commit: `docs: add <nombre-nota>`
5. Push a `develop`

## Setup de hooks (instalar una vez por máquina)

Agregar a `~/.claude/settings.json`:

```json
"hooks": {
  "SessionStart": [{
    "hooks": [{
      "type": "command",
      "command": "WIKI=\"$HOME/projects/proyects-wiki/INDEX.md\"; [ -f \"$WIKI\" ] && jq -Rs '{hookSpecificOutput: {hookEventName: \"SessionStart\", additionalContext: (\"[Memory-Wiki INDEX]\\n\" + .)}}' \"$WIKI\" 2>/dev/null || true",
      "timeout": 5,
      "statusMessage": "Loading memory wiki..."
    }]
  }],
  "Stop": [{
    "hooks": [{
      "type": "command",
      "command": "echo '{\"hookSpecificOutput\":{\"hookEventName\":\"Stop\",\"additionalContext\":\"[Memory-Wiki] Check if any decisions, bugs, or patterns from this session should be saved to ~/projects/proyects-wiki/ using the templates in _templates/.\"}}' ",
      "timeout": 3
    }]
  }]
}
```

## Ruta de este repo

`~/projects/proyects-wiki/`
