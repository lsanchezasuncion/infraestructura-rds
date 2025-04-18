# servicios/visualizacion/README.md

## Servicio de Visualización (Grafana)

Directorio para recursos de visualización: dashboards JSON, scripts de provisioning.

### Levantamiento

```bash
docker-compose up -d grafana
```

### Acceso

- UI en `http://<host>:3000`, usuario `admin` (cambiar contraseña).
- Data source: InfluxDB configurado en URL `http://influxdb:8086`, token `my-token`.

