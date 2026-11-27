# Minuta – Revisión del modelo conceptual – 27/11/2026

**Participantes:** Marina · **Escuela de referencia:** Rojas FC

Se revisó el modelo conceptual en cuatro bloques (plataforma y escuelas, alumnos y familias, cuotas, pagos y recibos) y se ajustaron las reglas de negocio.

## Decisiones

- **Categoría:** es el año de nacimiento, calculado. Sin tabla de categorías ni horarios en la v1.0; las categorías propias pasan al backlog (RN-36).
- **Meses sin cuota:** no se configuran; un mes que no se cobra no se abre y se marca como "sin cobro" (RN-04).
- **Apertura del mes:** se puede anular mientras nadie haya pagado (RN-61).
- **Preinscripciones:** al aprobarse se borran sus datos personales; las rechazadas, a los 30 días. Aviso de duplicados por DNI (RN-27, RN-29).
- **Hermanos:** el administrador los vincula a mano en un grupo familiar (RN-06).
- **Contacto de emergencia:** un número de teléfono del tutor.
- **Operación:** fecha de pago cargada por el administrador, descripción opcional en lugar del número de operación y aviso suave de duplicados (RN-12).
- **Pago con fecha anterior al vencimiento:** el recargo se anula o se recalcula automáticamente (RN-62).
- **Saldo a favor al dar de baja:** se conserva; si se devuelve, se anula con motivo (RN-63).
- **Anulación de deudas:** el administrador puede anular cualquier deuda con historial (RN-33).
- **Pagos sin conexión:** entran en la v1.0; quedan pendientes hasta que el servidor los confirma (RN-17, ADR-003).
- **Eventos e indumentaria:** entran en la v1.0, con deuda e ingresos separados por concepto (RN-55 a RN-60).
- Las mejoras que en el Trabajo Final quedaron como futuras se desarrollan en este proyecto. Los recibos no se envían automáticamente.

## Próximos pasos

- Casos de uso por rol para validar el modelo.
- DER con atributos, claves y cardinalidades.
- Modelo lógico (relacional) y modelo físico.
