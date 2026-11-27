# Minuta – Conciliación de requisitos y reglas – 26/11/2026

**Participantes:** Marina · **Escuela de referencia:** Rojas FC

Antes de diseñar el modelo de datos se revisó la documentación y se resolvieron las diferencias entre requisitos, historias de usuario, ADR y reglas de negocio.

## Contradicciones resueltas

- **Alta de escuelas:** autoregistro, y el superadministrador también puede crearlas (RN-41, RF-01, HU-13, HU-14).
- **Administradores de varias escuelas:** un usuario puede tener permisos en más de una escuela; en la v1.0 la interfaz trabaja con una a la vez (RN-40, RF-03).
- **Preinscripciones:** estados pendiente, aprobada y rechazada; no hay "incompleta" porque los campos obligatorios se exigen en el formulario (RN-27, RF-07, ADR-002).
- **Vocabulario:** se usa "recargo" en todos los documentos, en lugar de "intereses".
- **WhatsApp:** botón "Compartir por WhatsApp" que abre el chat con el mensaje armado; lo envía el administrador (RN-24, RN-44).
- **Correos:** la v1.0 envía solo correos transaccionales (RF-18).

## Reglas completadas

- **Apertura del mes:** las cuotas no se generan solas; el administrador abre cada mes con monto, vencimiento y recargo, y el dashboard avisa si no lo hizo (RN-03, RN-05, RN-08, RN-49).
- **Pagos adelantados:** quedan como saldo a favor y se imputan al generarse la cuota (RN-15).
- **Anulación en pagos familiares:** se puede anular el pago de un solo alumno o la operación completa (RN-18).
- **Descuento por hermanos:** se guarda en cada cuota; una baja afecta desde la próxima cuota generada (RN-06).
- **Tutores:** una sola cuenta por DNI en toda la plataforma; todos los tutores vinculados ven lo mismo (RN-45, RN-48).
- **Recibos:** a nombre del alumno (RN-20).
- **Baja de una escuela:** a los 6 meses se anonimizan los datos personales y se conservan los importes (RN-42).
- **Configuración por escuela:** alcance de la v1.0 definido y ADR-004 aceptada (RN-36).
- **Datos de salud:** solo para administradores, fuera de listados y exportaciones; apto médico opcional, sin control de vencimiento (RN-26).

## Próximos pasos

- ADR de aislamiento multiescuela, stack y PostgreSQL, historial y auditoría, y numeración de recibos.
- Modelo de datos conceptual y relacional.
