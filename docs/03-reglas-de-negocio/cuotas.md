# Cuotas, descuentos y recargos

## Monto

**RN-01 – Monto único.** Cada escuela define un monto de cuota mensual único para todos sus alumnos. No varía por categoría.

**RN-02 – Actualización con vigencia.** El administrador registra cada nuevo monto con una fecha desde la cual rige. El sistema conserva el historial de montos. Cada cuota guarda el monto vigente al momento de generarse; un aumento no modifica cuotas ya generadas, salvo lo previsto en RN-15 para pagos adelantados.

## Generación y vencimiento

**RN-03 – Cuota del mes en curso.** Se genera una cuota por mes para cada alumno activo, correspondiente al mes en curso.

**RN-04 – Meses sin cuota.** Cada escuela configura, por año, los meses en que no se cobra cuota. Valor inicial de Rojas FC: enero.

**RN-05 – Vencimiento.** El vencimiento no es un día fijo: se define para cada mes. La escuela configura un día de referencia (Rojas FC: el 10) y el sistema propone ese día o, si no es hábil, el siguiente día hábil, nunca uno anterior. El administrador confirma o ajusta la fecha de cada mes.

## Descuentos

**RN-06 – Descuento por hermanos.** Los alumnos que tienen al menos un hermano activo en la misma escuela reciben un descuento porcentual sobre la cuota.

- El porcentaje es configurable por escuela.
- Se aplica por igual a **todos** los hermanos, incluido el primero.
- El porcentaje es el mismo sin importar la cantidad de hermanos.
- Dos alumnos se consideran hermanos cuando el administrador los vincula como tales (por ejemplo, al compartir tutor).

**RN-07 – Sin otros descuentos.** En la v1.0 el único descuento es el de hermanos. Becas u otros descuentos quedan fuera de alcance.

## Recargos por mora

**RN-08 – Recargo.** Si al vencimiento la cuota tiene saldo impago, se aplica un recargo porcentual configurable por la escuela. El recargo se calcula sobre el **saldo impago de la cuota con el descuento ya aplicado**.

**RN-09 – Escalones.** La escuela puede configurar hasta dos escalones de recargo, cada uno con su porcentaje y su fecha de aplicación (por ejemplo, el primero al vencer y el segundo desde el día 20). Cada escalón se cobra una sola vez. Rojas FC usa un solo escalón.

**RN-10 – Condonación.** El administrador puede no aplicar un recargo en casos puntuales. Debe indicar un motivo, y el sistema registra quién lo hizo y cuándo.
