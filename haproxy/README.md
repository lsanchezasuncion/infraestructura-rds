# haproxy/README.md

## Configuración de HAProxy

Este directorio contiene la configuración de HAProxy para balancear la capa HTTP de los sensores hacia el middleware.

- **haproxy.cfg**: configuración global, frontend `*:80` que redirige a `backend middleware_servers`.

### Uso

1. Copiar `haproxy.cfg` a `/etc/haproxy/haproxy.cfg` en Debian.
2. Reiniciar HAProxy: `sudo systemctl restart haproxy`.

