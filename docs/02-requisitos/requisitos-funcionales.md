# Requisitos funcionales

!!! note "Borrador"
    La minuta del 26/11/2026 menciona borradores RF-01 a RF-17. Este documento los reconstruye a partir del alcance acordado y deberá conciliarse con esos borradores. Los requisitos del sitio público provienen del relevamiento de Rojas FC.

## Sistema de gestión

| ID | Requisito | Módulo |
|---|---|---|
| RF-01 | El sistema debe permitir dar de alta, editar, desactivar y personalizar escuelas (nombre, logo, colores, contacto, disciplinas, vocabulario). | Escuelas |
| RF-02 | El sistema debe permitir gestionar usuarios con los roles superadministrador, administrador de escuela y tutor. | Usuarios |
| RF-03 | Un administrador debe poder gestionar una o varias escuelas autorizadas. | Usuarios |
| RF-04 | El sistema debe permitir que cada escuela defina sus categorías (por edad, nivel, género o turno), con días, horarios y lugar. | Categorías |
| RF-05 | El sistema debe importar respuestas de preinscripción desde Google Sheets (alimentado por Google Forms). | Preinscripciones |
| RF-06 | Cada respuesta importada debe generar una preinscripción, nunca un alumno activo. | Preinscripciones |
| RF-07 | El administrador debe poder revisar, detectar duplicados y aprobar, rechazar o marcar como incompleta una preinscripción. | Preinscripciones |
| RF-08 | Al aprobar una preinscripción, el sistema debe crear el alumno y crear o vincular sus tutores. | Alumnos / Tutores |
| RF-09 | El sistema debe permitir gestionar alumnos: alta, baja, reingreso, categoría, observaciones e historial. | Alumnos |
| RF-10 | Un alumno puede tener varios tutores y un tutor puede estar vinculado a varios alumnos. | Tutores |
| RF-11 | El sistema debe generar cuotas mensuales con vencimiento y calcular deuda e intereses por mora. | Cuotas |
| RF-12 | El administrador debe poder registrar pagos, con confirmación del servidor. | Pagos |
| RF-13 | El sistema debe emitir recibos numerados en PDF, descargables y compartibles por WhatsApp. | Recibos |
| RF-14 | El tutor debe poder consultar en el portal los alumnos vinculados, cuotas, deuda, pagos y descargar recibos. | Portal de familias |
| RF-15 | El sistema debe ofrecer reportes y listados exportables a Excel, PDF y vista de impresión (prioridad: alumnos activos por categoría). | Reportes |
| RF-16 | El sistema debe registrar auditoría de las operaciones relevantes. | Auditoría |
| RF-17 | La aplicación debe permitir consulta offline de datos sincronizados y registrar cambios no críticos en una cola local. | Offline |

## Sitio público

Heredados del relevamiento de Rojas FC, generalizados como plantilla por escuela.

| ID | Requisito |
|---|---|
| RFP-01 | Mostrar la presentación institucional de la escuela: nombre, propósito, valores y propuesta deportiva. |
| RFP-02 | Mostrar las categorías disponibles según edad o grupo. |
| RFP-03 | Informar días, horarios y lugar de entrenamiento de cada categoría. |
| RFP-04 | Permitir el contacto por WhatsApp desde un botón visible. |
| RFP-05 | Incluir acceso a la preinscripción de nuevos alumnos. |
| RFP-06 | Mostrar una galería de fotos de entrenamientos, partidos o actividades. |
| RFP-07 | Mostrar las redes sociales oficiales. |
| RFP-08 | Mostrar novedades o avisos importantes. |
| RFP-09 | Mostrar actividades especiales: torneos, campamentos, viajes, encuentros y eventos. |
| RFP-10 | Permitir publicar el detalle de cada actividad especial: fecha, lugar, descripción, requisitos e imágenes. |
| RFP-11 | Mostrar la ubicación de la sede con dirección y Google Maps. |
