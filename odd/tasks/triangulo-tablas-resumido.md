# Triángulo del Tesoro — tablas resumidas (sin combinaciones repetidas)

## Objetivo
Crear una segunda página de aprendizaje, enfocada en que los chicos entiendan que `a×b` y `b×a` son lo mismo, mostrando/practicando solo las 55 combinaciones únicas de las tablas del 1 al 10 (en vez de las 100 que resultarían de practicar cada tabla completa por separado).

## Problema / por qué
El usuario pidió otra página "resumida" para aprender las tablas sin repetir las combinaciones que ya son iguales por conmutatividad, manteniendo el enfoque lúdico para chicos. Mecánica elegida por el usuario: **triángulo visual explorable** (flashcards tipo descubrimiento, no quiz de opción múltiple).

## Alcance
- Archivo nuevo: `tabla_resumida.html` (mismo estilo vanilla HTML/CSS/JS de un solo archivo, sin build).
- Enlaces cruzados entre `tesoro_tablas.html` / `index.html` y la nueva página.
- Sumar la nueva página al precache del `service-worker.js` para que también funcione offline.
- Mismo universo visual (paleta, tipografía) que el juego existente para que se sienta parte del mismo sitio.

## Restricciones
- Sin frameworks ni dependencias nuevas.
- Progreso persistido en localStorage (clave separada, no pisar `islaTesoroEstableV1`).
- Accesible: celdas como `<button>` reales (focuseables, activables con teclado), `aria-live` para el contador de progreso.
- Responsive (reutilizar el patrón de breakpoint `max-width:580px` + overflow-x scroll para la grilla en mobile si hace falta).

## Tareas
- [x] **T1 — Construir `tabla_resumida.html`**: grilla triangular de 55 celdas (a≤b, 1 a 10), cada celda es flashcard (tap para revelar/ocultar el resultado), celdas de la diagonal (cuadrados perfectos) destacadas, sonido y celebración visual al descubrir una celda nueva, contador de progreso persistido, botón de reinicio.
- [x] **T2 — Enlaces cruzados** entre las páginas existentes (`tesoro_tablas.html`, `index.html`) y la nueva, para navegar entre ambas.
- [ ] **T3 — Sumar la página nueva al precache del service worker** (bump de versión de cache para que los usuarios que ya instalaron la PWA reciban la actualización).
- [ ] **T4 — Verificación manual en navegador**: cargar la página, descubrir celdas, confirmar que el progreso persiste tras recargar, y que sigue funcionando sin conexión.

## Criterios de aceptación
- Exactamente 55 celdas visibles (combinaciones únicas 1≤a≤b≤10), sin ninguna combinación repetida por conmutatividad.
- Tocar una celda la da vuelta y muestra el resultado; tocar de nuevo la vuelve a tapar (flashcard real, no solo "mostrar una vez").
- El contador de progreso ("X/55 descubiertas") persiste entre recargas de página.
- Funciona offline una vez visitada (vía service worker actualizado).
- Hay un link visible para ir y volver entre el juego principal y esta página.

## Progreso y evidencia
(se completa por tarea con el hash de commit correspondiente)
