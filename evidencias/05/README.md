# Bloque 05

## Resultado
- Qué añadí al proyecto: una aplicación Expo/React Native Web en `mobile` con dos eventos locales y selección mediante estado.
- Ruta o pantalla comprobada: `http://localhost:8081` con Expo Web.
- Estado y respuesta observados: Expo sirvió la aplicación con `200 OK`; el bundle contiene las tarjetas `EVT-101` y `EVT-102`, el botón `Seleccionar EVT-101` y el estado inicial `Selección: ninguna`.

## Comprensión
- Recorrido del dato, explicado con mis palabras: `localEvents` es un array local tipado; `map` dibuja las tarjetas y `useState` conserva la selección durante los renders.
- Cambio guiado y resultado: añadí el cliente `mobile` con Expo, TypeScript y React Native Web; `npm run typecheck` y `expo export --platform web` terminaron correctamente.
- Error encontrado y cómo lo resolví: no hubo errores de compilación ni de Metro. El entorno no tenía un navegador controlable para automatizar el clic, por lo que la interacción visual queda pendiente de comprobación manual.

## Evidencias
- Captura o transcripción breve, sin credenciales:
  - `npm install` completado y `mobile/package-lock.json` generado.
  - `npm run typecheck` → sin errores.
  - `npm run web` → Metro iniciado en `http://localhost:8081` y bundle web compilado.
  - `HEAD http://localhost:8081` → `200 OK`, `Content-Type: text/html`.
  - `npm run build:web` → exportación web completada en `dist`.
  - El bundle contiene `EVT-101`, `EVT-102`, `Seleccionar EVT-101` y `Selección: ninguna`.
  - No hay llamadas de aplicación a `/events`; los datos proceden de `localEvents`.
- Limitaciones del ejercicio: no se pudo automatizar desde este entorno el clic y la recarga del navegador; el código conecta el botón con `setSelected('EVT-101')` y la recarga reinicia el estado local.
