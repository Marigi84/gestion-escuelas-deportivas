# ADR-002: Preinscripciones sujetas a aprobación administrativa

- **Estado:** Aceptada
- **Fecha:** 2026-11-26

## Contexto

Las familias cargarán sus datos mediante Google Forms y las respuestas se guardarán en Google Sheets. Esos datos pueden llegar incompletos, con errores o duplicados.

## Decisión

- Las respuestas se incorporan inicialmente mediante una **importación** desde la aplicación.
- Cada respuesta genera una **preinscripción**, nunca un alumno activo de forma automática.
- El administrador revisa los datos, controla duplicados y aprueba o rechaza la solicitud. No hay estado "incompleta" porque los campos obligatorios se exigen en el formulario (actualizado el 2026-11-26, ver RN-27).
- Al aprobar, se crea el alumno y se crea o vincula el tutor.

## Consecuencias

- Los datos de alumnos activos mantienen calidad y control.
- Se requiere una pantalla de revisión y un mecanismo de detección de duplicados.
- La integración automática con Google Sheets queda para una evolución posterior.
