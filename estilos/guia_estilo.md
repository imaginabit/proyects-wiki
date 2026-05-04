---
fecha: 2026-05-04
tecnologias: [#php, #javascript, #general]
tipo: #arquitectura
estado: #activo
---
# 🎨 Guía de Estilo de Código

## Filosofía General
- **Clean Code** — código legible y expresivo, sin trucos
- **TDD** — tests primero, luego implementación
- **Tidy First** (Kent Beck) — estructura antes que comportamiento
- **YAGNI** — solo construir lo que se necesita ahora
- **KISS** — la solución más simple gana

## Stack Principal
- **Backend:** Laravel 8.x + PHP
- **Frontend:** Vue 3 + PrimeVue + Inertia.js
- **Lenguajes:** PHP, JavaScript/TypeScript

## Convenciones

### PHP / Laravel
- Nombres de clases en PascalCase
- Métodos y variables en camelCase
- Tablas de base de datos en snake_case plural
- Relaciones Eloquent explícitas, sin magic strings

### JavaScript / Vue
- Componentes en PascalCase
- Props y emits siempre tipados
- Composables con prefijo `use`

## Comentarios
- Por defecto: ninguno
- Solo comentar el **POR QUÉ**, nunca el qué
- Un línea máximo, nunca bloques multi-línea

## Idioma
- Código: inglés (nombres de variables, métodos, clases)
- Comentarios: español
- Commits: Conventional Commits en inglés

[[arquitectura/decisiones_globales]]
