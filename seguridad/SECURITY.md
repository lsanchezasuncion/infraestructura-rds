# seguridad/SECURITY.md

## Consideraciones de seguridad

- MQTT: actualmente `allow_anonymous true` para pruebas; en producción, habilitar autenticación y TLS.
- HAProxy: configurado con TLS v1.2+; en producción, proporcionar certificados válidos.
- Node.js: usar variables de entorno para credenciales sensibles.
- Docker: asegurarse de usar versiones actualizadas de las imágenes.

