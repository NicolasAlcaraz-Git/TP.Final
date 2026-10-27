# Spec 03 — Escenarios variables

## Objetivo

Generar escenarios nuevos que cambien obstáculos y rutas de verdad, y recalcular el camino con la búsqueda elegida.

## Comportamiento esperado

- Botón "Nuevo escenario" genera un laberinto/patrón distinto (bloques, bifurcaciones, callejones).
- Spawn y núcleo se mantienen conectados: siempre existe al menos un camino.
- Al generar, la ruta se recalcula con BFS/A* activo y los enemigos en curso usan la nueva ruta.
- Dos generaciones seguidas producen escenarios con distinta disposición de obstáculos.

## Fuera de alcance

Semillas configurables, guardado de escenarios, métricas comparativas.

## Cómo comprobarla jugando

Presionar "Nuevo escenario" 5 veces seguidas y ver 5 mapas distintos con rutas distintas (ver debug con D). Iniciar una ola y confirmar que los enemigos llegan al núcleo en cada uno.

## Archivos

- `src/scenario.js` — generador procedural con garantía de conectividad.
- `src/grid.js` — integración con obstáculos.
