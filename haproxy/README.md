# haproxy/README.md

## Configuración de HAProxy

Este directorio contiene la configuración de HAProxy para balancear la capa HTTP de los sensores hacia el middleware.

- **haproxy.cfg**: configuración global, frontend `*:80` que redirige a `backend middleware_servers`.

Puntos clave de la configuración

Balanceo Round‑Robin en backend middleware_servers para repartir equitativamente la carga.

Health Check ligero (option httpchk GET /health) para asegurar que solo instancias sanas reciben tráfico.

Timeouts ajustados a 5000 ms:

timeout connect 5000: máximo 5 s para establecer conexión.

timeout client  5000: la conexión con el cliente se cierra 5 s después de la última petición.

timeout server  5000: la conexión al servidor backend se cierra 5 s después de la respuesta.

Cierre inmediato de conexiones con option http-server-close (activado por defecto en esta configuración), que libera recursos tras cada transacción.

*Cálculos de dimensionamiento*

Sensores: 14 889 enviando 1 petición/s cada uno → 14 889 rps.

Duración de conexión: 5 s → cada socket permanece activo un máximo de 5 s tras el último uso.

Concurrencia máxima de sockets:

concurrencia ≈ rps × timeout_client
             ≈ 14 889 req/s × 5 s
             ≈ 74 445 conexiones TCP simultáneas

HAProxy en hardware commodity (2 vCPUs, 2 GB RAM) maneja >100 000 rps y >100 000  conexiones concurrentes. Por tanto, la configuración de 5 s y round‑robin es suficiente para nuestro escenario.

Rendimiento de red estimado:

Petición HTTP típica ~200 B → tráfico de pico ~3 MB/s.

Respuesta similar → tráfico total ~6 MB/s.

Redes LAN/WAN modernas (≥100 Mbps) cubren ampliamente este ancho de banda.

### Uso

1. Copiar `haproxy.cfg` a `/etc/haproxy/haproxy.cfg` en Debian.
2. Reiniciar HAProxy: `sudo systemctl restart haproxy`.

