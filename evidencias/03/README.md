# Bloque 03

## Resultado
- Qué añadí al proyecto: el handler `createEvent` y la ruta `POST /events`.
- Ruta o pantalla comprobada: `http://localhost:3000/dev/events` con Serverless Offline.
- Estado y respuesta observados: los cuerpos válidos devolvieron `201 Created` con `EVT-NEW`; los cuerpos inválidos devolvieron `400` con mensajes de validación.

## Comprensión
- Recorrido del dato, explicado con mis palabras: el body llega como texto, se convierte con `JSON.parse`, se comprueba que sea un objeto y se validan sus campos antes de construir la respuesta.
- Cambio guiado y resultado: añadí `src/createEvent.ts` y relacioné `dist/createEvent.handler` con `POST events`; la ruta aceptó eventos válidos y rechazó entradas inválidas.
- Error encontrado y cómo lo resolví: la primera prueba desde PowerShell envió comillas escapadas como parte del body; repetí las peticiones enviando el JSON por stdin a `curl`, y las respuestas coincidieron con el contrato.

## Evidencias
- Captura o transcripción breve, sin credenciales:
  - `POST` válido con `CONFIRMED` → `201`, `EVT-NEW`.
  - `POST` válido con `CANCELLED` → `201`, `EVT-NEW`.
  - `POST` sin `status` → `201`, usando `CONFIRMED` por defecto.
  - Campo ausente → `400`, `artist, space y time (HH:mm) son obligatorios`.
  - JSON roto → `400`, `JSON inválido`.
  - `status: PAUSED` → `400`, `status debe ser CONFIRMED o CANCELLED`.
  - `time: 29:80` → `400`.
  - `GET /dev/events/EVT-NEW` → `200` con la ficha fija `Neon Waves`.
  - Log observado: `POST evento: Nova Pulse`.
- Limitaciones del ejercicio: `EVT-NEW` es fijo y el POST no guarda datos; el GET no recupera el evento enviado.
