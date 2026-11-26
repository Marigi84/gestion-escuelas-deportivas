# Pagos

**RN-11 – Formas de pago.** Cada escuela habilita sus formas de pago. Rojas FC acepta solo **efectivo** y **transferencia**.

**RN-12 – Verificación de transferencias.** Una transferencia se registra como pago recién cuando el administrador verifica el ingreso con el comprobante enviado por la familia. Se guarda el número de operación, y el sistema advierte si se intenta registrar dos veces el mismo número.

**RN-13 – Pagos parciales.** Se permite pagar una parte de la cuota. El saldo queda pendiente y, si sigue impago al vencimiento, recibe el recargo según RN-08.

**RN-14 – Imputación.** Un pago cancela siempre la deuda **más antigua** del alumno primero: recargos y cuotas de los meses anteriores antes que los del mes en curso.

**RN-15 – Pagos adelantados.** Se puede pagar por adelantado cuotas de meses que todavía no se generaron. Si luego aumenta el monto de la cuota (RN-02), la diferencia queda pendiente como saldo de ese mes.

**RN-16 – Pago familiar.** Una familia con varios hijos puede hacer un único pago o transferencia por todas las cuotas. El administrador lo registra una vez como **operación** y la reparte entre los hermanos; el sistema genera un pago por alumno, vinculado a esa operación.

**RN-17 – Confirmación del servidor.** Un pago es definitivo solo cuando el servidor lo confirma ([ADR-003](../adr/0003-pagos-confirmados-por-servidor.md)). No se registran pagos definitivos sin conexión.

**RN-18 – Anulación.** Un pago no se borra. Se anula indicando motivo, y el sistema registra usuario y fecha. Al anularse, se revierte su imputación y se anulan los recibos asociados (RN-23).
