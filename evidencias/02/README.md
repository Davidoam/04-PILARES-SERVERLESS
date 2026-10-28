# Bloque 02

## Resultado
- Qué añadí al proyecto: el handler `getEvent` y la ruta dinámica `GET /events/{id}`.
- Ruta o pantalla comprobada: `http://localhost:3000/dev/events/{id}` con Serverless Offline.
- Estado y respuesta observados: `200 OK` para `EVT-104`, `EVT-205` y `EVT-330`; cada respuesta devolvió su propio `id` y los datos simulados del evento.

## Comprensión
- Recorrido del dato, explicado con mis palabras: el valor escrito en `/events/{id}` es interpretado por API Gateway/Offline y llega al handler en `event.pathParameters?.id`; el handler lo incorpora al JSON de respuesta.
- Cambio guiado y resultado: añadí `src/getEvent.ts` y relacioné `dist/getEvent.handler` con `events/{id}` en `serverless.yml`; los tres identificadores llegaron al mismo handler.
- Error encontrado y cómo lo resolví: PowerShell bloqueaba `npm.ps1` y Serverless necesitaba autenticación; ejecuté `npm.cmd` y, tras disponer de la autenticación de Serverless, Offline arrancó correctamente.

## Evidencias
- Captura o transcripción breve, sin credenciales:
  - `GET /dev/events/EVT-104` → `200 OK`, `{"id":"EVT-104",...}`
  - `GET /dev/events/EVT-205` → `200 OK`, `{"id":"EVT-205",...}`
  - `GET /dev/events/EVT-330` → `200 OK`, `{"id":"EVT-330",...}`
  - Logs: `GET evento: EVT-104`, `GET evento: EVT-205`, `GET evento: EVT-330`.
  - `GET /dev/hello` → `200 OK`.
- Limitaciones del ejercicio: cualquier identificador no vacío devuelve los mismos datos simulados; todavía no se consulta un catálogo ni una base de datos.
