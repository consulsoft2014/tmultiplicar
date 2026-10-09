# Página de inicio con selector de juegos (tarjetas)

## Objetivo
Convertir `index.html` (hoy un simple redirect) en una pantalla de selección con tarjetas grandes y vistosas para que el chico elija entre los dos modos de aprendizaje antes de entrar.

## Problema / por qué
Ahora hay dos páginas de aprendizaje (`tesoro_tablas.html` y `tabla_resumida.html`) y el usuario pidió una página que las muestre juntas para que el niño elija, con libertad creativa ("tarjetas no sé, sé creativo").

## Alcance
- Reescribir `index.html`: de redirect automático a pantalla de selección con dos tarjetas grandes y tocables (mismo estilo visual del sitio).
- Actualizar los links de navegación en `tesoro_tablas.html` y `tabla_resumida.html` para que apunten de vuelta a `index.html` ("🏠 Elegir juego") en vez de ir directo entre sí.
- Subir versión de cache del service worker (el contenido de `index.html` cambia sustancialmente).
- Se sigue trabajando en la rama `feature/triangulo-tablas-resumido` (continuación directa de ese trabajo, todavía no mergeado).

## Tareas
- [x] **T1 — Reescribir `index.html`** como pantalla de selección con dos tarjetas (Isla del Tesoro / Triángulo del Tesoro), responsive, con mismo tema visual.
- [x] **T2 — Repuntar navegación** en ambas páginas de juego hacia `index.html`.
- [x] **T3 — Bump de versión del service worker** y verificación manual (carga, tarjetas llevan a cada juego, funciona offline).

## Progreso y evidencia — verificación manual
Probado en navegador (Claude in Chrome) con server HTTP local de node:
- `index.html` nuevo carga como pantalla de selección con las dos tarjetas.
- Tarjeta "¡A jugar!" → navega a `tesoro_tablas.html`; tarjeta "¡A explorar!" → navega a `tabla_resumida.html` (confirmado con `location.href`).
- El link "🏠 Elegir juego" en ambos juegos vuelve correctamente a `index.html`.
- Service worker `isla-tesoro-v3` activo con las 6 rutas precacheadas; apagando el servidor local el hub sigue cargando (confirmado vía `document.title` tras recargar sin red).

## Estado final
Las 3 tareas completadas y commiteadas en `feature/triangulo-tablas-resumido` (commits `8480cbb`, `37c163c`, pendiente commit de T3).

## Progreso y evidencia
(se completa por tarea)
