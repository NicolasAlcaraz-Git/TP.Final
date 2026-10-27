# GDD — Tower Defense con NPCs perceptivos

| | |
|---|---|
| **Asignatura** | Programación de IA y Patrones de Comportamiento |
| **Trabajo** | TP Final Integrador |
| **Integrantes** | Nicolas Alcaraz y Eduardo Acosta (3.º año, Lic. en Producción de Videojuegos y Entretenimiento Digital) |
| **Fecha** | 27/10/2026 |
| **Versión** | 1.0 |
| **Estado** | Entregable |

*Nombre tentativo del juego: a definir en producción.*

## 1. Idea

Tower defense top-down 2D (Canvas, JS). El jugador coloca torres y además camina un **héroe** por el campo. Enemigos salen de un spawn, buscan camino hasta el núcleo y tratan de destruirlo; el héroe los atrae/estorba, y ellos lo detectan y se alertan entre sí.

## 2. Interacción

- Clic para colocar torres (con costo) y botones de upgrade.
- WASD/flechas para mover al héroe.
- Panel para elegir: algoritmo de búsqueda (BFS / A*), navegación (Flow field / Steering) y regenerar escenario.
- Olas de enemigos; gana resistiendo, pierde si el núcleo llega a 0.

## 3. Escenario y escenarios variables

Grid con spawn y núcleo. Cada partida genera un laberinto/patrón de obstáculos nuevos (rutas largas, bifurcaciones, callejones sin salida). Las rutas **se recalculan** con el algoritmo elegido — nada hardcodeado. La opción "reiniciar escenario" regenera otro distinto.

Si se incorporan centinelas con patrullaje, sus rutas se generan desde el escenario actual: nunca hay una trayectoria fija preparada.

## 4. NPC: percepción

- **Visión**: cono/raycast corto. Si ve al héroe → estado *Alerta*.
- **Comunicación**: un NPC en alerta avisa a los cercanos (radio) → todos reaccionan (cambian de ruta/lo rodean).
- Sin visión → estado *Avanzar* siguiendo la ruta al núcleo.

## 5. Objetivos del NPC

- Primario: llegar al núcleo y atacarlo.
- Secundario (alertado): perseguir/interrumpir al héroe si está cerca, luego volver al primario.

## 6. Comportamiento (FSM)

`AVANZAR → ALERTA → PERSIGUIR → (volver) AVANZAR → ATACAR_NUCLEO → MORIR`

Solo FSM por ahora (una técnica, alcanza y es explicable).

## 7. Búsquedas (seleccionables)

- **BFS**: camino más corto en pasos, barato, ideal con costos uniformes.
- **A***: con heurística Manhattan, menos nodos explorados.
- Ambos usados para recalcular rutas/flow field al mover obstáculos o regenerar.

## 8. Alternativas de navegación (seleccionables, observables)

1. **Flow field / crowd**: cada celda tiene dirección vectorial; los NPCs la siguen con separación entre aliados → movimiento grupal fluido.
2. **Steering con evasión local**: siguen el camino pero esquivan obstáculos y aliados con seek + avoid → movimiento más errático e individual.

Elegir BFS vs A* **no** cuenta como navegación distinta: va por separado.

## 9. Qué cambia entre escenarios

Distinta disposición de obstáculos, longitud/cantidad de rutas, posición de spawn/núcleo dentro de rangos, y variación entre caminos abiertos vs. cerrados que fuerzan re-ruteo.

## 10. Fuera de alcance

- Economía compleja, árbol de upgrades, héroes jugables múltiples.
- Árboles de comportamiento / utilidad / GOAP (solo FSM).
- Dijkstra y DFS como opciones (BFS + A* bastan; el resto es opcional).
- Multiplayer, guardado de partidas, métricas/semillas.
- Assets artísticos: colores, formas y una UI mínima.
- MCP, modelo de lenguaje dentro del juego y servicios pagos.

## 11. Cumplimiento de requisitos

| Requisito del trabajo | Dónde se cumple |
|---|---|
| NPC con percepción, objetivos y comportamientos | §§4, 5, 6 |
| Al menos 2 algoritmos de búsqueda seleccionables | §7 (BFS, A*) |
| Al menos 2 alternativas de navegación (no = cambiar búsqueda) | §8 (flow field, steering) |
| Comportamiento con FSM / BT / utilidad / GOAP | §6 (FSM) |
| Escenarios variables que cambien obstáculos y recorridos | §§3, 9 |
| Escenarios jugables y cumplir objetivos | §§2, 3 |
| Patrullaje adaptado al escenario (si existe) | §3 |
| Alternativas seleccionables y observables jugando | §§7, 8 + modo debug |
| Proceso spec-driven con OpenCode | `specs/` (SDD) |

## 12. Herramientas y proceso

Desarrollo con **OpenCode** siguiendo un proceso spec-driven básico: especificaciones pequeñas y ordenadas por dependencias dentro de `specs/`, implementadas de a una con aprobación previa de cada plan.
