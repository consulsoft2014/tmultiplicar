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
- [ ] **T2 — Repuntar navegación** en ambas páginas de juego hacia `index.html`.
- [ ] **T3 — Bump de versión del service worker** y verificación manual (carga, tarjetas llevan a cada juego, funciona offline).

## Progreso y evidencia
(se completa por tarea)
