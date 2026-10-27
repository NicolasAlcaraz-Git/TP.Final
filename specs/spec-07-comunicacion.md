# Spec 07 — Comunicación entre NPCs

## Objetivo

Que un NPC alertado avise a los cercanos y todos reaccionen.

## Comportamiento esperado

- Al entrar en `ALERTA`/`PERSIGUIR`, el NPC emite un aviso en radio R.
- Los enemigos en radio que estaban en `AVANZAR` pasan a `ALERTA` (con decaimiento: vuelven solos tras un tiempo sin estímulos).
- La reacción se ve en grupo: varios enemigos cambian de color/estado a la vez.
- Debug (D) dibuja el círculo de radio de aviso al emitirse.

## Fuera de alcance

Red real/multiplayer, jerarquías de mando, memorización de posiciones históricas.

## Cómo comprobarla jugando

Acercarte con el héroe a un grupo de 5+ enemigos: al verlos uno, el resto cambia de estado dentro del radio. Alejarte y esperar: todos vuelven a AVANZAR.

## Archivos

- `src/perception.js` — broadcast de alerta.
- `src/fsm.js` — estado alerta con decaimiento.
