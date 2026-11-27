# Cuotas, descuentos y recargos

## Monto

**RN-01 – Monto único.** Cada escuela define un monto de cuota mensual único para todos sus alumnos. No varía por categoría.

**RN-02 – Actualización con vigencia.** El administrador registra cada nuevo monto con una fecha desde la cual rige. El sistema conserva el historial de montos. Cada cuota guarda el monto vigente al momento de generarse; un aumento no modifica cuotas ya generadas, salvo lo previsto en RN-15 para pagos adelantados.

## Generación y vencimiento

**RN-03 – Apertura del mes.** Las cuotas no se generan solas. Cada mes el administrador **abre el mes**: revisa o modifica el monto (RN-02), fija la fecha de vencimiento (RN-05) y los recargos (RN-08, RN-09). Al confirmar, el sistema genera una cuota del mes en curso para cada alumno activo e imputa los saldos a favor (RN-15). Si el mes en curso todavía no se abrió, el dashboard lo avisa (RN-49).

**RN-61 – Anulación de la apertura.** Si el administrador se equivocó al abrir el mes, puede anular la apertura mientras ninguna cuota de ese mes tenga pagos registrados. Las cuotas quedan anuladas (no se borran) y los saldos a favor que se habían imputado vuelven a estar disponibles. Después puede abrir el mes de nuevo. Queda registrado el motivo, quién y cuándo.

**RN-04 – Meses sin cuota.** Un mes que no se cobra (en Rojas FC, enero) simplemente no se abre. Para que el aviso del dashboard no aparezca, el administrador marca ese mes como **sin cobro**.

**RN-05 – Vencimiento.** El vencimiento no es un día fijo: se define para cada mes al abrirlo (RN-03). La escuela configura un día sugerido (Rojas FC: el 10), que el sistema propone siempre; el administrador lo confirma o lo modifica. No hay calendario de feriados: si el día sugerido es feriado, el administrador lo corre.

## Descuentos

**RN-06 – Descuento por hermanos.** Los alumnos que tienen al menos un hermano activo en la misma escuela reciben un descuento porcentual sobre la cuota.

- El porcentaje es configurable por escuela.
- Se aplica por igual a **todos** los hermanos, incluido el primero.
- El porcentaje es el mismo sin importar la cantidad de hermanos.
- Dos alumnos son hermanos cuando el administrador los vincula a mano en un mismo **grupo familiar**. No se deduce de que compartan tutor.
- El descuento se calcula al generar la cuota y queda guardado en ella. Si un hermano se da de baja, el que sigue pierde el descuento desde la próxima cuota que se genere; las cuotas ya generadas no cambian.

**RN-07 – Sin otros descuentos.** En la v1.0 el único descuento es el de hermanos. Becas u otros descuentos quedan fuera de alcance.

## Recargos por mora

**RN-08 – Recargo.** Si al vencimiento la cuota tiene saldo impago, se aplica un recargo porcentual. La escuela configura un valor sugerido y el administrador lo confirma al abrir el mes (RN-03). El recargo se calcula sobre el **saldo impago de la cuota con el descuento ya aplicado**.

**RN-09 – Escalones.** La escuela puede configurar hasta dos escalones de recargo, cada uno con su porcentaje y su fecha de aplicación (por ejemplo, el primero al vencer y el segundo desde el día 20). Cada escalón se cobra una sola vez. Rojas FC usa un solo escalón.

**RN-10 – Condonación.** El administrador puede no aplicar un recargo en casos puntuales. Debe indicar un motivo, y el sistema registra quién lo hizo y cuándo.

**RN-62 – Pago con fecha anterior al vencimiento.** Si el administrador registra un pago con una fecha de pago anterior al vencimiento (RN-12) y el recargo ya se había aplicado: si el pago cubría todo el saldo, el recargo se anula automáticamente con el motivo "pagó antes del vencimiento"; si cubría una parte, el recargo se anula y se vuelve a calcular sobre lo que quedó impago al vencimiento. Todo queda en el historial.
