# broker-mqtt/README.md

## Broker MQTT (Mosquitto)

Este directorio contiene la configuración del broker MQTT basado en Eclipse Mosquitto.

- **mosquitto.conf**: define un listener en el puerto 1883, permite conexiones anónimas y configura persistencia.
- **README.md**: este archivo.

### Uso

1. Levantar el broker con Docker Compose: `docker-compose up -d broker`
2. Conectarse al broker en `mqtt://<host>:1883`.

