# Bloque 04

## Resultado
- Qué añadí al proyecto: el módulo compartido de eventos y handlers para listar, consultar, crear, sustituir, actualizar y eliminar.
- Ruta o pantalla comprobada: rutas `/dev/events` y `/dev/events/{id}` con Serverless Offline.
- Estado y respuesta observados: catálogo fijo con `EVT-101` y `EVT-102`; las operaciones devolvieron los estados HTTP definidos y las respuestas JSON esperadas.

## Comprensión
- Recorrido del dato, explicado con mis palabras: cada ruta dirige a un handler separado; los handlers consultan el catálogo o validan el body mediante funciones compartidas y devuelven JSON con CORS.
- Cambio guiado y resultado: trasladé las rutas GET y POST a `src/events`, y añadí PUT, PATCH y DELETE. Las escrituras describen la operación, pero no modifican el catálogo.
- Error encontrado y cómo lo resolví: no hubo errores funcionales; el arranque, la compilación y las pruebas terminaron correctamente.

## Evidencias
- Captura o transcripción breve, sin credenciales:
  - `GET /dev/events` → `200`, exactamente `EVT-101` y `EVT-102`.
  - `GET /dev/events/EVT-101` → `200`.
  - `GET /dev/events/NO-EXISTE` → `404`.
  - `POST /dev/events` → `201`, `EVT-NEW`.
  - `PUT /dev/events/EVT-101` → `200`, `operation: REPLACED`.
  - `PATCH /dev/events/EVT-101` con `{"status":"CANCELLED"}` → `200`, `operation: UPDATED`.
  - `DELETE /dev/events/EVT-102` → `200`, `operation: DELETED`.
  - PUT incompleto y PATCH con `time` → `400`.
  - GET posterior a las escrituras conservó los dos eventos originales.
  - `GET /dev/hello` → `200`.
  - OPTIONS de `/dev/events` → `200` con `Access-Control-Allow-Origin` y métodos permitidos.
  - Logs observados: `LIST eventos`, `GET evento`, `POST evento`, `PUT evento`, `PATCH evento` y `DELETE evento`.
- Limitaciones del ejercicio: el catálogo es fijo; POST, PUT, PATCH y DELETE no persisten cambios.
