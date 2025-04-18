# Root README

## Infraestructura IoT distribuida orientada a servicios

Este proyecto implementa una infraestructura de red orientada a servicios para la gestión de datos de 14.889 sensores distribuidos en tres sedes. Incluye:

- Capa de sensorización (simulada)
- Capa de red (HAProxy + Middleware HTTP→MQTT + Broker Mosquitto)
- Capa de servicios:
  - Almacenamiento (Node.js → InfluxDB)
  - Visualización (Grafana)
  - Servicio personal (por implementar)

Se basa en contenedores Docker orquestados con Docker Compose, y la configuración está versionada en GitHub.

