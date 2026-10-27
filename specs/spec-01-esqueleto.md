# Spec 01 — Esqueleto del juego

## Objetivo

Tener el canvas con grid, bucle de juego, spawn, núcleo, héroe movible, colocación de torres y olas básicas de enemigos que caminan en línea recta hasta el núcleo (sin IA todavía).

## Comportamiento esperado

- Se abre en el navegador y se ven: grid, spawn (entrada), núcleo (destino), héroe.
- WASD/flechas mueven al héroe dentro del grid.
- Clic en una celda válida coloca una torre restando energía; clic inválido no hace nada.
- Las olas spawnean enemigos que avanzan hasta el núcleo y lo dañan.
- Torres disparan al enemigo más cercano en rango y lo destruyen.
- HUD: energía, vida del núcleo, número de ola, botón siguiente ola.

## Fuera de alcance

Cualquier pathfinding, FSM, percepción, navegación con steering/flow field, escenarios variables.

## Cómo comprobarla jugando

Mover el héroe por todo el grid, colocar 3 torres, lanzar una ola y ver que los enemigos llegan al núcleo y que las torres los matan antes de que lleguen. Verificá que al quedarte sin energía no podés colocar más.

## Archivos

- `src/game.js` — bucle, estado global, input.
- `src/grid.js` — grid, spawn, núcleo, torres.
- `src/entities.js` — héroe y enemigo (movimiento simple).
- `src/ui.js` — HUD y botones.
- `index.html` — página base.
