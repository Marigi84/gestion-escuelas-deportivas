# ADR-001: Sistema multiescuela con personalización y aislamiento

- **Estado:** Aceptada
- **Fecha:** 2026-11-26

## Contexto

Rojas Fútbol Club es la primera implementación, pero el propietario tiene otras escuelas y a futuro se prevé ofrecer la plataforma a instituciones externas. Desarrollar una aplicación por escuela multiplicaría el mantenimiento.

## Decisión

Construir un único sistema **multiescuela**:

- Cada escuela tiene su propia personalización: nombre, logo, colores, datos de contacto y configuración administrativa.
- Cada administrador accede solo a las escuelas autorizadas; cada tutor, solo a los alumnos vinculados.
- La separación de datos se verifica **en el servidor**, no solo en la interfaz.

## Consecuencias

- Todas las entidades principales quedan asociadas a una escuela.
- Cada consulta debe filtrar por las escuelas autorizadas del usuario; se necesitan pruebas específicas de aislamiento.
- Queda pendiente elegir la estrategia técnica de aislamiento (columna de escuela, esquema por escuela, etc.).
