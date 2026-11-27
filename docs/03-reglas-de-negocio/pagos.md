# Pagos

**RN-11 – Formas de pago.** Cada escuela habilita sus formas de pago. Rojas FC acepta solo **efectivo** y **transferencia**.

**RN-12 – Registro de la operación.** Una transferencia se registra recién cuando el administrador verifica el ingreso con el comprobante enviado por la familia. Cada operación guarda:

- la **fecha de pago**, que carga el administrador (por defecto, la del día);
- la **fecha de registro**, que pone el sistema;
- una **descripción** opcional (por ejemplo, el número de la transferencia).

Si se intenta registrar otra operación con el mismo importe, la misma fecha de pago y los mismos alumnos, el sistema pregunta si ya se cargó y el administrador decide si continúa.

**RN-13 – Pagos parciales.** Se permite pagar una parte de la cuota. El saldo queda pendiente y, si sigue impago al vencimiento, recibe el recargo según RN-08.

**RN-14 – Imputación.** Al registrar un pago, el administrador elige a qué **concepto** se aplica: cuotas, un evento o un pedido de indumentaria ([RN-55 a RN-60](eventos-e-indumentaria.md)). Dentro de las cuotas, el pago cancela siempre la deuda **más antigua** primero: recargos y cuotas de los meses anteriores antes que los del mes en curso.

**RN-15 – Pagos adelantados.** Se puede pagar por adelantado cuotas de meses que todavía no se generaron. El importe queda como **saldo a favor** del alumno y se imputa automáticamente cuando se genera la cuota de ese mes. Si para entonces aumentó el monto (RN-02), la diferencia queda pendiente como saldo de ese mes.

**RN-16 – Pago familiar.** Una familia con varios hijos puede hacer un único pago o transferencia. El administrador lo registra una vez como **operación** y la reparte entre los hermanos y entre conceptos (por ejemplo, la cuota de un hijo y la seña del viaje de otro); el sistema genera un pago por cada parte, vinculado a esa operación.

**RN-17 – Pagos sin conexión.** Un pago es definitivo solo cuando el servidor lo confirma ([ADR-003](../adr/0003-pagos-confirmados-por-servidor.md)). Sin internet, el administrador puede cargar el pago en la aplicación y queda **pendiente de sincronizar** en el dispositivo. Mientras tanto no tiene recibo numerado (a lo sumo, un comprobante provisorio sin número) y la deuda no se actualiza. Al volver la conexión, el pago se envía, el servidor lo confirma, le asigna número y emite el recibo; si parece repetido, se aplica el aviso de RN-12.

**RN-18 – Anulación.** Un pago no se borra. Se anula indicando motivo, y el sistema registra usuario y fecha. Al anularse, se revierte su imputación y se anulan los recibos asociados (RN-23). En un pago familiar (RN-16) se puede anular solo el pago de un alumno, y el resto de la operación queda igual; si el error es de toda la operación, se anulan todos sus pagos.

**RN-63 – Saldo a favor al dar de baja.** Si un alumno se da de baja con saldo a favor, el saldo queda guardado por si vuelve. Si se le devuelve el dinero a la familia, el administrador anula el saldo a favor con motivo.
