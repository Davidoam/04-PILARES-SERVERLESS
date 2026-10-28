# Bloque 06

## Resultado
- Qué añadí al proyecto: `mobile/src/api.ts` y una pantalla que carga el catálogo mediante `GET /events`.
- Ruta o pantalla comprobada: frontend Expo Web en `http://localhost:8081` y backend en `http://localhost:3000/dev`.
- Estado y respuesta observados: `GET /dev/events` devolvió `200` con `EVT-101` y `EVT-102`; el cliente compila y apunta a esa respuesta HTTP.

## Comprensión
- Recorrido del dato, explicado con mis palabras: `useEffect` llama a `getEvents`, `fetch` solicita `/events`, la respuesta se valida como una lista de eventos y `setEvents` alimenta las tarjetas.
- Cambio guiado y resultado: eliminé el array local, añadí estados de carga/error y un botón `GET recargar`; la interfaz muestra el error de red y permite volver a intentar.
- Error encontrado y cómo lo resolví: no hubo errores de compilación ni de Metro; se comprobó el fallo de conexión con el backend detenido y la recuperación tras arrancarlo de nuevo.

## Evidencias
- Captura o transcripción breve, sin credenciales:
  - `mobile npm run typecheck` → sin errores.
  - `npm run web` → Metro compiló y sirvió `http://localhost:8081`.
  - `GET http://localhost:3000/dev/events` → `200` con dos actuaciones.
  - `GET http://localhost:3000/dev/ruta-inexistente` → `404`.
  - Backend detenido → conexión fallida (`HTTP 000`); backend reiniciado → `GET /events` volvió a `200`.
  - `npm run build:web` → exportación web completada.
  - El cliente usa `API_URL = http://localhost:3000/dev` y no contiene el catálogo local.
- Limitaciones del ejercicio: no había un navegador controlable para inspeccionar Network o pulsar `GET recargar`; la red y el build se comprobaron desde terminal y el código mantiene la recuperación mediante `try/catch/finally`.
