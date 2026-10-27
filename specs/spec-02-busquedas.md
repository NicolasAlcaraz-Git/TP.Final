# Spec 02 — Búsquedas BFS y A* seleccionables

## Objetivo

Implementar pathfinding sobre el grid con **BFS** y **A\***, seleccionables en pantalla, y usar el resultado para que los enemigos recorran el camino calculado hasta el núcleo.

## Comportamiento esperado

- Botón/toggle para elegir BFS o A* (por defecto A*).
- Al iniciar la ola (o al regenerar), se calcula la ruta desde el spawn al núcleo evitando obstáculos.
- Los enemigos siguen celda a celda el camino calculado (no caminan en línea recta).
- Modo debug (tecla D) dibuja el camino calculado y, opcionalmente, los nodos explorados.
- BFS y A* producen caminos válidos; A* explora menos nodos (visible en debug).

## Fuera de alcance

Dijkstra, DFS, costos variables de terreno, flow field, steering.

## Cómo comprobarla jugando

Cambiar entre BFS y A* y ver el camino en debug; posicionar obstáculos en el mapa y confirmar que ambos rodean el bloqueo. Activar D y comparar nodos explorados.

## Archivos

- `src/pathfinding.js` — `bfs(grid, start, goal)`, `astar(grid, start, goal)`.
- `src/grid.js` — obstáculos del nivel.
