# Spec 05 — FSM de comportamiento del NPC

## Objetivo

Organizar el comportamiento del enemigo con una máquina de estados explícita.

## Comportamiento esperado

- FSM por enemigo: `AVANZAR → ATACAR_NUCLEO → MORIR` como base, más estados de alerta listos para specs 06/07 (`ALERTA`, `PERSIGUIR`).
- En `AVANZAR` sigue la ruta al núcleo; en `ATACAR_NUCLEO` ataca en rango y reduce la vida; al morir suma energía.
- HUD o debug (tecla D) muestra el estado actual de cada enemigo (label o color por estado).
- Transiciones implementadas como tabla/clase de estados, no como `if` dispersos.

## Fuera de alcance

Árboles de comportamiento, utilidad, GOAP, percepción (spec 06), comunicación (spec 07).

## Cómo comprobarla jugando

Observar con D que los enemigos pasan por AVANZAR → ATACAR_NUCLEO → MORIR en cada ciclo, y que el color/cambia al estado correcto. Verificar que atacar el núcleo baja su vida.

## Archivos

- `src/fsm.js` — estados y transiciones.
- `src/entities.js` — integración de la FSM en el enemigo.
