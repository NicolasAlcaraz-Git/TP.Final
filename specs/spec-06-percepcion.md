# Spec 06 — Percepción: visión del NPC

## Objetivo

Que los NPC perciban al héroe mediante visión (cono/raycast) y transicionen a estado alerta.

## Comportamiento esperado

- Cada enemigo tiene cono de visión corto y ángulo definido; no ve a través de paredes/obstáculos (raycast bloqueado).
- Si el héroe entra al cono → transición `AVANZAR → ALERTA`.
- En `ALERTA`, el enemigo se orienta/perseguirá al héroe (transición a `PERSIGUIR` si sigue a la vista).
- Si pierde de vista por tiempo X → vuelve a `AVANZAR`.
- Debug (D) dibuja el cono de visión de cada enemigo.

## Fuera de alcance

Oído/ruido, comunicación entre NPC (spec 07), visión con memoria de último punto visto.

## Cómo comprobarla jugando

Camina el héroe cerca de un enemigo y ver su cono en D: al entrar cambia de color (ALERTA/PERSIGUIR); al esconderte detrás de un muro y esperar, vuelve a AVANZAR. Verificar que el cono se corta contra obstáculos.

## Archivos

- `src/perception.js` — cono, raycast, FOV.
- `src/fsm.js` — transiciones por percepción.
