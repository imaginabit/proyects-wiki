# 🧠 Instalación del Sistema de Pensamiento: Memory-Wiki Global

Hola Claude. Este archivo contiene las instrucciones para instalar mi "Cerebro Externo" en este PC. Si venís de Engram, el paso 6 explica cómo migrar tus observaciones. Si empezás de cero, ignorá la migración y enfocate en crear la estructura lista para aprender.

## 1. Infraestructura de Directorios
Clona este repo — la estructura ya está lista:
```bash
git clone git@github.com-imaginabit:imaginabit/proyects-wiki.git ~/projects/proyects-wiki
```

Las carpetas `arquitectura/`, `lecciones/`, `estilos/`, `snippets/`, `proyectos/` y `_templates/` ya están creadas. No se necesita ningún paso adicional.

## 2. El "Contrato" de Memoria (CLAUDE.md + hooks)

El contrato de comportamiento vive en `CLAUDE.md` en la raíz de este repo. Claude Code lo lee automáticamente cuando trabajas dentro del proyecto.

Para que esté disponible de forma global (en todos los proyectos), cópialo a tu config de usuario:
```bash
cp ~/projects/proyects-wiki/CLAUDE.md ~/.claude/CLAUDE.md
```

Luego agrega los hooks a `~/.claude/settings.json` para que Claude cargue el wiki automáticamente al iniciar cada sesión y reciba un recordatorio de actualizarlo al final de cada turno. El JSON exacto a pegar está en la sección **Setup de hooks** de `CLAUDE.md`.

## 3. Plantilla de Nota de Memoria
Crea el archivo `~/projects-wiki/_templates/nota_base.md`. Cada vez que generes conocimiento nuevo, usa este Frontmatter para que mi Obsidian lo organice:

```markdown
---
fecha: {{date}}
tecnologias: []
tipo: #leccion | #snippet | #arquitectura
estado: #activo
---
# [Título Claro]
## 📝 Resumen
## 💻 Implementación / Código
[[Notas Relacionadas]]
```

## 4. Guía de Estilo Inicial
Crea un archivo base en `~/projects-wiki/estilos/guia_estilo.md` donde irás anotando cómo me gusta que escribas código (ej. "Preferencia por Clean Code", "Comentarios en español", etc.).

## 5. El Dashboard de Obsidian (INDEX.md)
Configura el archivo principal para que, al abrir Obsidian, tenga este aspecto:

```markdown
# 🗄️ Wiki de Desarrollo Global

## 🗺️ Mapa de Navegación
- [[estilos/guia_estilo|🎨 Mi Estándar de Código]]
- [[snippets/comandos_terminal|⌨️ Comandos Rápidos]]
- [[proyectos/lista_proyectos|📂 Mis Proyectos Activos]]

## 🧠 Últimos Conocimientos Adquiridos
(Claude: Aquí listarás los últimos 5 archivos que hayas creado o editado)
```

## 6. Acción Post-Instalación

**Empezar de cero:** Confirma que la estructura está lista — carpetas creadas, hooks instalados, `INDEX.md` abierto en Obsidian. La memoria empieza a grabarse en tu próxima sesión.

**Venís de Engram (migración opcional):** Si tenés observaciones previas en Engram que vale la pena conservar, procésalas ahora:
1. Leer observaciones de `mcp__plugin_engram`
2. Convertir las duraderas (decisiones, bugs, patrones) en notas usando `_templates/nota_base.md`
3. Descartar las específicas de una sesión o duplicadas
4. Actualizar `INDEX.md` con las nuevas notas
5. Commit: `docs: migrate Engram observations to wiki`
