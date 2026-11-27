# Recibos

**RN-19 – Generación automática.** Al registrar un pago, el sistema genera el recibo automáticamente con los datos ya cargados (alumno, período, fecha), sin volver a ingresarlos. Se emite **un recibo por alumno**.

**RN-20 – Contenido.** El recibo se emite **a nombre del alumno** e incluye: datos de la escuela, número de recibo, fecha, alumno, período o períodos cancelados, importe, forma de pago y, si corresponde, el **saldo pendiente**.

**RN-21 – Numeración.** Los recibos se numeran de forma correlativa por escuela. La estrategia técnica se formalizará en un ADR.

**RN-22 – Carácter interno.** El recibo es un comprobante interno, no una factura, y así lo indica. Si la familia necesita factura, el sistema ofrece un enlace a la web de ARCA (ex AFIP) para que el administrador la emita. No hay integración fiscal automática en la v1.0.

**RN-23 – Inmutabilidad y anulación.** Un recibo emitido no se modifica ni se borra. Para corregirlo, se anula (con motivo, usuario y fecha) y se emite uno nuevo. El historial queda disponible.

**RN-24 – Distribución.** El recibo se genera en PDF y se puede descargar o compartir. El botón "Compartir por WhatsApp" abre el chat con el mensaje ya armado y el administrador lo envía; no hay envío automático en la v1.0. Los tutores pueden descargar los recibos de sus alumnos desde el portal de familias.
