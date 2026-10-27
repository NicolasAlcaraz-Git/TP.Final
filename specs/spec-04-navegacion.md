# Spec 04 — Navegación: flow field y steering (alternativas)

## Objetivo

Dos alternativas de navegación seleccionables que se vean distintas al jugar.

## Comportamiento esperado

- Toggle de navegación: **Flow field** / **Steering**.
- **Flow field**: se calcula un campo de direcciones desde el goal (derivado de la búsqueda) y los enemigos lo siguen con separación entre aliados → movimiento grupal fluido, se esparcen por caminos libres.
- **Steering**: los enemigos siguen su camino con seek + avoid de obstáculos y aliados → movimiento más individual, con desvíos y empujones.
- Cambiar el toggle afecta a los enemigos en tiempo real.
- Modo debug dibuja las flechas del flow field.

## Fuera de alcance

Cambiar BFS por A* como "navegación" (eso ya está en spec 02), flocking complejo, física real.

## Cómo comprobarla jugando

Spawear una ola con 15+ enemigos, alternar el toggle y observar el movimiento: con flow field avanzan como columna fluida; con steering se abren camino de forma más errática. Ver flechas del campo con D.

## Archivos

- `src/navigation.js` — flow field y steering.
- `src/entities.js` — aplicación del steering.
