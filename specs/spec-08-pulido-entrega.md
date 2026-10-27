# Spec 08 — Pulido, patrullaje adaptativo y entrega

## Objetivo

Cierre integrador: que el conjunto se vea y se explique bien, con instrucciones de ejecución y material para la exposición.

## Comportamiento esperado

- Si se incluye patrullaje (enemigos/centinelas), sus rutas se generan desde el escenario actual (recalculadas), nunca trayectoria fija.
- Panel de selección visible: búsqueda (BFS/A*), navegación (flow field/steering), nuevo escenario.
- README de ejecución: cómo abrir el juego, controles, qué probar de cada spec.
- Balance mínimo: las torres/héroe permiten ganar y perder de forma posible.
- `GDD.md`, `specs/` y presentación dentro del repo.

## Fuera de alcance

Métricas, tablas comparativas, semillas, informe extenso, carpeta de evidencias.

## Cómo comprobarla jugando

Seguir la checklist de ejecución del README completa: generar 3 escenarios, alternar búsqueda y navegación, alertar un grupo con el héroe, ganar y perder una partida. Mostrar una spec a elección en la exposición.

## Archivos

- `README.md` — instrucciones de ejecución.
- `docs/` — presentación.
- ajustes en specs anteriores.
