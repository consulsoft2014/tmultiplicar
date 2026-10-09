# Mejoras de interactividad y fixes — La Isla del Tesoro Matemático

## Objetivo
Corregir bugs que debilitan el propósito pedagógico del juego y sumar mejoras de interactividad para que los chicos se mantengan motivados aprendiendo las tablas.

## Problema / por qué
Revisión del único archivo (`tesoro_tablas.html`) encontró que la respuesta correcta en el modo práctica es siempre matemáticamente la más chica de las 3 opciones (bug pedagógico grave), y otros 3 problemas menores de UX/distribución. El usuario pidió explícitamente arreglar bugs y hacer el juego más interactivo/llamativo.

## Alcance
- Archivo único: `tesoro_tablas.html` (sin build system, sin tests automatizados — hay hooks manuales `window.__islaTest`).
- No se agregan dependencias ni frameworks nuevos; se mantiene vanilla JS/CSS en un solo archivo.

## Restricciones
- Mantener compatibilidad con el estado guardado en localStorage (`islaTesoroEstableV1`) sin romper partidas en curso.
- Mantener accesibilidad existente (aria-live, labels).
- Sin frameworks de testing: verificación manual en navegador (Claude in Chrome) + revisión de los hooks `window.__islaTest`.

## Tareas

- [x] **T1 — Fix: opciones incorrectas deben poder ser menores a la correcta** (bug pedagógico principal: la correcta siempre era la mínima de las 3). Commit `7987cec`.
- [x] **T2 — Fix: distribución pareja de multiplicadores** en rondas de práctica cuando `max=8` (actualmente 1-4 se repiten y 5-8 aparecen una sola vez). Commit `2d90bf2`.
- [x] **T3 — Fix: feedback claro cuando se alcanza el límite de tablas (20)** en vez de solo cambiar el texto del botón sin explicación.
- [ ] **T4 — Feature: racha/combo visual** ("¡Llevas N seguidas! 🔥") para motivar sin depender de un timer.
- [ ] **T5 — Feature: atajos de teclado (1/2/3)** para responder las preguntas de opción múltiple.
- [ ] **T6 — Feature: celebración visual (confetti/pulso) al acertar**, usando CSS ya existente como base.

## Criterios de aceptación
- Las opciones incorrectas se generan con offsets mixtos (positivos y negativos), sin valores duplicados ni negativos, y sin patrón posicional/valor predecible.
- En niveles con `max=8`, los 8 multiplicadores aparecen de forma pareja en las 12 preguntas (no hay un grupo que se repita el doble que otro).
- Al llegar al tope de tablas (20) con "seguir automáticamente" activo, se muestra un mensaje explícito antes de permitir terminar.
- Se ve un contador de racha que crece con aciertos consecutivos y se reinicia con un error.
- Las teclas 1, 2 y 3 seleccionan la opción correspondiente cuando hay preguntas de opción múltiple visibles.
- Al acertar, hay una animación/efecto visual breve además del texto "¡Correcto!".

## Verificación
- Abrir `tesoro_tablas.html` en navegador (Claude in Chrome) y jugar manualmente: practicar, fallar a propósito, acertar, llegar a un cofre, y revisar consola sin errores.
- Ejecutar `window.__islaTest.testLevels()` en la consola del navegador y confirmar que todas las entradas son `valid: true`.
- Revisar visualmente que la racha, el confetti y los atajos de teclado funcionen.

## Progreso y evidencia
(se completa por tarea con el hash de commit correspondiente)
