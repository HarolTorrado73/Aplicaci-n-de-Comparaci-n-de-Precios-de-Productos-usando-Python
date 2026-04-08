# Política de Seguridad

## Reporte de vulnerabilidades

Si encuentras una vulnerabilidad, repórtala de forma privada al mantenedor del repositorio. No publiques detalles sensibles en issues públicos.

## Alcance

Esta política cubre:

- Código de frontend en `html/index.html`.
- Configuración de despliegue y servidor Flask.
- Dependencias declaradas en `requirements.txt`.

## Buenas prácticas del proyecto

- No almacenar secretos en el repositorio.
- No incluir credenciales en código fuente.
- Revisar dependencias periódicamente.
- Limitar CORS y endpoints según entorno productivo.

## Recomendaciones operativas

- Usar variables de entorno para configuración sensible.
- Escanear imágenes y dependencias en CI.
- Aplicar principio de mínimo privilegio en IAM/Code Engine.
