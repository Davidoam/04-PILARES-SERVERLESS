# Bloque 07

## Resultado
- Qué añadí al proyecto: helpers de escritura HTTP y cuatro acciones en la pantalla Expo.
- Ruta o pantalla comprobada: `POST`, `PUT`, `PATCH` y `DELETE` sobre `http://localhost:3000/dev/events`.
- Estado y respuesta observados: POST devolvió `201`; PUT, PATCH y DELETE devolvieron `200` con sus operaciones simuladas.

## Comprensión
- Recorrido del dato, explicado con mis palabras: cada botón llama a una función de `api.ts`; `run` espera la Promise, bloquea las acciones y muestra el JSON recibido.
- Cambio guiado y resultado: añadí creación, sustitución, cambio parcial y eliminación; la lista no se modifica de forma optimista ni desaparecen las tarjetas tras DELETE.
- Error encontrado y cómo lo resolví: una primera prueba POST desde PowerShell envió las comillas del JSON de forma incorrecta; repetí la petición por stdin y obtuve `201`.

## Evidencias
- Captura o transcripción breve, sin credenciales:
  - `POST /dev/events` con evento completo → `201`, `EVT-NEW`.
  - `PUT /dev/events/EVT-101` con objeto completo → `200`, `operation: REPLACED`.
  - `PATCH /dev/events/EVT-101` con `{"status":"CANCELLED"}` → `200`, `operation: UPDATED`.
  - `DELETE /dev/events/EVT-102` → `200`, `operation: DELETED`.
  - PATCH de comprobación con `CONFIRMED` → `200`, `changes.status: CONFIRMED`.
  - GET posterior → `200` y conserva `EVT-101` y `EVT-102` con `CONFIRMED`.
  - Logs observados: `POST evento`, `PUT evento`, `PATCH evento` y `DELETE evento`.
  - `mobile npm run typecheck` y `npm run build:web` → correctos.
  - El bundle contiene los cuatro botones y los helpers HTTP.
- Limitaciones del ejercicio: no se automatizó el clic en el navegador porque no había navegador controlable; las peticiones y el bundle se verificaron desde terminal.
