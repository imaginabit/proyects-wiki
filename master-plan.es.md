# 🧠 Instalación del Sistema de Pensamiento: Memory-Wiki Global

Hola Claude. Este archivo contiene las instrucciones para instalar mi "Cerebro Externo" en este PC. Si no hay datos previos de Engram, ignora la migración y céntrate en crear la estructura vacía lista para aprender.

## 1. Infraestructura de Directorios
Crea el sistema de carpetas en el home del usuario para que sea accesible desde cualquier proyecto:
```bash
mkdir -p ~/projects-wiki/{arquitectura,lecciones,estilos,snippets,proyectos,_templates}
touch ~/projects-wiki/INDEX.md
```

## 2. El "Contrato" de Memoria (System Prompt)
Configura tu comportamiento global para que siempre operes bajo este sistema:
```bash
claude config set --system-prompt "Tu memoria global reside en ~/projects-wiki/. 
1. Consulta INDEX.md al iniciar cualquier sesión.
2. Si tomo una decisión técnica o resolvemos un bug, pídeme permiso para documentarlo en ~/projects-wiki/lecciones/ o snippets/.
3. Usa siempre el formato de Obsidian [[enlaces]] para conectar conceptos.
4. Mantén consistencia con mi archivo de estilos en ~/projects-wiki/estilos/guia_estilo.md."
```

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
1. Si existe contenido en `mcp__plugin_engram`, procésalo y muévelo a esta nueva estructura siguiendo la plantilla.
2. Si NO existe contenido previo, confirma que la estructura está lista para empezar a grabar mi primera sesión.
