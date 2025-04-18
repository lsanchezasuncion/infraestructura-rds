# middleware/README.md

## Middleware HTTP→MQTT

Servicio en Node.js que recibe peticiones HTTP GET/POST en `/sensorData` (y `/health` para health‑checks) y publica mensajes en un broker MQTT.

### Estructura

- **Dockerfile**: imagen Node.js.
- **package.json**: dependencias (express, mqtt, body-parser).
- **src/index.js**: código fuente.

### Endpoints

- `GET|POST /sensorData?sensorID={id}&temperature={temp}` → publica en tópico `sensors/{id}/temperature`.
- `GET /health` → responde 200 OK.

### Levantamiento

```bash
docker-compose up -d middleware
```
