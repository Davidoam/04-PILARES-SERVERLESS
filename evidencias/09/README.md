# Bloque 09

## Resultado
- Qué añadí al proyecto: cambié `API_URL` del cliente para consumir el endpoint HTTPS de AWS.
- Ruta o pantalla comprobada: `https://troldj9r32.execute-api.us-east-1.amazonaws.com/dev` desde el cliente Expo Web.
- Estado y respuesta observados: los cinco métodos respondieron con los estados esperados y las respuestas se mantuvieron simuladas, sin persistencia.

## Comprensión
- Recorrido del dato, explicado con mis palabras: `api.ts` conserva los mismos métodos y rutas, pero cambia el origen; el navegador envía HTTPS a API Gateway, Lambda ejecuta el handler y devuelve JSON a la pantalla.
- Cambio guiado y resultado: solo sustituí la URL local por la base cloud; `App.tsx` y los contratos permanecieron iguales.
- Error encontrado y cómo lo resolví: no hubo errores funcionales; la API cloud y los logs de Lambda respondieron correctamente.

## Evidencias
- Captura o transcripción breve, sin credenciales:
  - `GET /events` → `200`, dos eventos.
  - `POST /events` → `201`, `EVT-NEW`.
  - `PUT /events/EVT-101` → `200`, `operation: REPLACED`.
  - `PATCH /events/EVT-101` → `200`, `operation: UPDATED`.
  - `DELETE /events/EVT-102` → `200`, `operation: DELETED`.
  - GET posterior → `200`, el catálogo conserva `EVT-101` y `EVT-102`.
  - Logs cloud: `PATCH evento: EVT-101` y `LIST eventos: GET`.
  - `mobile npm run typecheck` y `npm run build:web` → correctos.
  - El bundle final contiene la URL `execute-api` y no contiene `localhost:3000`.
- Limitaciones del ejercicio: las escrituras son simuladas y no persisten; el navegador no recibe credenciales AWS. La inspección visual de Network se documenta mediante las peticiones HTTPS y el bundle generado.
