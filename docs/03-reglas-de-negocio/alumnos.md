# Alumnos: altas, bajas y categorías

## Altas y bajas

**RN-30 – Alta a mitad de mes.** Si un alumno se incorpora con el mes ya empezado, le corresponde un importe proporcional. El administrador carga ese importe manualmente en la cuota del mes.

**RN-31 – Vigencia hasta la baja.** Las cuotas se siguen generando mientras el alumno esté activo, aunque haya dejado de asistir sin avisar. Solo dejan de generarse cuando el administrador registra la baja. La cuota del mes de la baja se genera completa, salvo que el administrador la ajuste.

**RN-32 – Deuda al dar de baja.** La baja no elimina la deuda: queda registrada y visible en el historial del alumno.

**RN-33 – Ajuste y anulación de deuda.** El administrador puede modificar manualmente el importe de una cuota, o anular cualquier deuda (cuota, recargo, evento o pedido de indumentaria). Cada ajuste o anulación registra el importe anterior, el nuevo, el motivo, el administrador y la fecha. Nada se borra.

## Reincorporación

**RN-34 – Reactivación.** Cuando un alumno vuelve, el administrador lo reactiva con los datos que ya estaban cargados; no se repite el formulario de inscripción. Al reactivarlo, el sistema muestra la deuda anterior y el administrador decide si exige saldarla.

**RN-35 – Historial de permanencias.** Cada período en que el alumno estuvo activo (fecha de alta y de baja) queda registrado. Las bajas y reincorporaciones no borran información.

## Categorías

**RN-36 – Categoría.** En la v1.0 la categoría de un alumno es su **año de nacimiento**, y el sistema la calcula a partir de la fecha de nacimiento. No se guarda aparte ni se asigna a mano. Las categorías propias de cada escuela (por ejemplo, "Sub-12" o "Principiantes") y sus horarios quedan para una versión futura ([ADR-004](../adr/0004-plataforma-multidisciplina.md)). Los cambios de grupo que decide el profesor no se gestionan en el sistema en la v1.0.
