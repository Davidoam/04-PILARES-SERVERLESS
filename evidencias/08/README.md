# Bloque 08

## Resultado
- Qué añadí al proyecto: configuración de despliegue AWS para el servicio `festival-control-api-alumno01`.
- Ruta o pantalla comprobada: `https://troldj9r32.execute-api.us-east-1.amazonaws.com/dev`.
- Estado y respuesta observados: el servicio se desplegó en `us-east-1`, stage `dev`, y respondió desde API Gateway.

## Comprensión
- Recorrido del dato, explicado con mis palabras: TypeScript genera `dist`, Serverless empaqueta las funciones, CloudFormation crea los recursos y API Gateway dirige la petición hacia Lambda; CloudWatch registra la ejecución.
- Cambio guiado y resultado: `serverless.yml` usa el perfil temporal, la región, el código de alumno y el rol Lambda autorizado mediante variables de entorno; el despliegue creó las siete funciones.
- Error encontrado y cómo lo resolví: no hubo errores de AWS después de corregir el perfil local `[academy]`; las credenciales no se incluyeron en el repositorio.

## Evidencias
- Captura o transcripción breve, sin credenciales:
  - `aws sts get-caller-identity --profile academy` → cuenta `787660158799`.
  - `npm run typecheck` y `npm run build` → correctos.
  - `serverless package` → paquete generado con las funciones compiladas y `LabRole`.
  - `serverless deploy` → servicio desplegado: `festival-control-api-alumno01-dev`.
  - `GET /dev/events` → `200`, `EVT-101` y `EVT-102`.
  - `GET /dev/events/EVT-101` → `200`.
  - `GET /dev/events/NO-EXISTE` → `404`.
  - CloudWatch `listEvents` → `LIST eventos: GET`.
  - CloudWatch `getEvent` → `GET evento: EVT-101` y `GET evento: NO-EXISTE`.
- Limitaciones del ejercicio: las credenciales del laboratorio son temporales y pueden caducar; el endpoint pertenece al laboratorio AWS activo y no se añadió almacenamiento.
