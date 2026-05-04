# Memory-Wiki: Instrucciones para Claude

Este repo es la memoria persistente principal. Sin Engram, este wiki es la única fuente de contexto entre sesiones.

## Estrategia de memoria

```
SessionStart hook → inyecta INDEX.md automáticamente como contexto
       │
       ▼
1. Leer INDEX.md (ya cargado por hook)
2. Si se necesita más detalle → leer el archivo de la carpeta relevante
3. Sin datos → trabajar desde cero, guardar al terminar
       │
       ▼
Stop hook → recuerda revisar si algo merece guardarse
```

## Al iniciar una sesión (automático via hook)

El hook `SessionStart` en `~/.claude/settings.json` inyecta `INDEX.md` como contexto al arrancar. No hace falta leerlo manualmente — ya está cargado.

Si el hook no está instalado: leer `~/projects/proyects-wiki/INDEX.md` manualmente al inicio.

## Al terminar una sesión (automático via hook)

El hook `Stop` recuerda revisar si hay algo para guardar. Guardar cuando:
- Se tomó una decisión técnica (arquitectura, patrón, convención)
- Se resolvió un bug con causa no obvia
- Se aprendió un gotcha o comportamiento inesperado
- Se estableció una convención de código o proyecto

No guardar cuando sea:
- Contexto específico de una sesión o tarea puntual
- Algo ya evidente en el código o en git

## Cuándo escribir en cada carpeta

| Carpeta | Cuándo |
|---|---|
| `lecciones/` | Bug resuelto, gotcha, aprendizaje técnico reutilizable entre proyectos |
| `snippets/` | Código que vas a copiar en otro proyecto |
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
