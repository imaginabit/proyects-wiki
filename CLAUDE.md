# Memory-Wiki: Instrucciones para Claude

Este repo es la capa de memoria persistente secundaria. La primaria es Engram.

## Estrategia de memoria

```
1. Engram  → buscar primero (mem_search / mem_context)
2. Este repo → buscar si Engram no tiene datos (leer INDEX.md, luego la carpeta relevante)
3. Sin datos → trabajar desde cero y guardar en ambas capas al terminar
```

## Al iniciar una sesión en cualquier proyecto

1. Llamar `mem_context` en Engram
2. Si no hay datos relevantes, leer `~/projects/proyects-wiki/INDEX.md`
3. Si hay contexto útil aquí, leerlo antes de responder

## Cuándo escribir una nota aquí

Pedir permiso al usuario antes de documentar. Escribir aquí cuando el conocimiento:
- Deba sobrevivir un reset de Engram o cambio de máquina
- Sea una convención estable (estilo, arquitectura, patrón)
- Sea demasiado largo para una observación de Engram

No escribir aquí cuando sea:
- Contexto específico de una sesión
- Algo ya en el código o en git

## Cómo crear una nota

1. Usar la plantilla en `_templates/nota_base.md`
2. Guardar en la carpeta correcta:
   - `lecciones/` — bugs resueltos, gotchas, aprendizajes
   - `snippets/` — código reutilizable
   - `arquitectura/` — decisiones de diseño
   - `proyectos/` — contexto por proyecto
   - `estilos/` — convenciones y guías
3. Actualizar la sección "Últimos Conocimientos" en `INDEX.md`
4. Hacer commit con `docs: add <nombre-nota>`

## Ruta de este repo

`~/projects/proyects-wiki/`
