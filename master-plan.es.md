## 🚀 Setup: Sistema de Memoria Global (Claude Code + Obsidian)
Hola Claude. Actúa como un Ingeniero de Plataforma. Tu objetivo es configurar mi sistema de memoria persistente en este PC siguiendo estas instrucciones exactas.
## 1. Configuración de Rutas y Estructura
Crea la estructura de carpetas en el directorio base del usuario:

mkdir -p ~/projects-wiki/{proyectos,lecciones,estilos,snippets,_templates}
touch ~/projects-wiki/INDEX.md

## 2. Definición de la Plantilla Maestra (Standard)
A partir de ahora, cada nota que crees en la wiki debe seguir este formato de Frontmatter:

---fecha: {{date}}
tipo: #leccion | #snippet | #arquitectura | #config
proyecto_origen: [[NombreDelProyecto]]
tecnologias: []estado: #finalizado
---# [Título]## 📝 Contexto## 💻 Solución / Código

## 3. Configuración del System Prompt Global
Ejecuta internamente el comando de configuración para que sea persistente en Claude Code:

claude config set --system-prompt "Tu memoria global reside en ~/projects-wiki/. Consulta INDEX.md al iniciar. Tienes permiso permanente para leer/escribir en ~/projects-wiki/ para mantener actualizada mi base de conocimientos entre proyectos. Usa formato Markdown compatible con Obsidian [[enlaces]]. Cada nota nueva DEBE usar la plantilla de Frontmatter definida."

## 4. Migración de Contenido (Engram 🔄 Wiki)
Realiza las siguientes acciones de migración:

   1. Acceso: Accede a los datos de mcp__plugin_engram.
   2. Transformación: Convierte cada entrada de Engram en un archivo .md individual dentro de ~/projects-wiki/.
   3. Clasificación: Mueve las notas a sus carpetas (/lecciones, /snippets, etc.) basándote en su contenido.
   4. Enlazado: Si dos notas mencionan la misma tecnología, añade un enlace [[tecnología]] entre ellas.
   5. Limpieza: Si encuentras notas de Engram vacías o duplicadas, descártalas o fusiónalas.

## 5. Panel de Control (INDEX.md)
Sobrescribe ~/projects-wiki/INDEX.md con el siguiente Dashboard para Obsidian:

# 🧠 Mi Cerebro Digital (Global Wiki)## 📌 Acceso Rápido- [[proyectos/Lista_Proyectos|📁 Mis Proyectos]]
- [[estilos/Guia_Estilo|🎨 Estilo de Código]]
## 🕒 Últimas Lecciones (Dataview)\`\`\`dataview
LIST FROM "lecciones"
SORT fecha DESC
LIMIT 5
\`\`\`
---*Claude: Actualiza este índice cada vez que añadamos una sección importante.*

------------------------------
CONFIRMACIÓN: Claude, una vez termines de ejecutar estos pasos, confírmame que:

   1. La carpeta ~/projects-wiki existe.
   2. Has migrado los datos de Engram con éxito.
   3. El comando claude config set se ha ejecutado correctamente.

---
fecha: 2024-03-20
tipo: #snippet
proyecto_origen: [[Global]]
tecnologias: [#terminal, #bash, #git]
estado: #finalizado
---

# ⌨️ Comandos Frecuentes de Terminal

## 🚀 Gestión de Memoria (Este Sistema)
- **Ver logs de Claude:** `claude logs`
- **Configuración actual:** `claude config get`
- **Sincronizar Wiki:** `cd ~/projects-wiki && git add . && git commit -m "Update memory" && git push` (Si decides usar Git).

## 🛠 Desarrollo Genérico
- **Limpiar caché de Node:** `npm cache clean --force`
- **Matar proceso en puerto (ej. 3000):** `lsof -ti:3000 | xargs kill -9`
- **Docker: Limpiar todo:** `docker system prune -a --volumes`

## 📦 Git
- **Deshacer último commit (manteniendo cambios):** `git reset --soft HEAD~1`
- **Borrar ramas locales ya fusionadas:** `git branch --merged | grep -v "\*" | xargs -n 1 git branch -d`

---
*Claude: Si ejecuto un comando complejo con éxito en la terminal, pregúntame si quieres añadirlo a esta lista automáticamente.*
