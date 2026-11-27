# ADR-009: Numeración correlativa de recibos por escuela

- **Estado:** Aceptada
- **Fecha:** 2026-11-26 (aceptada el 2026-11-27)

## Contexto

Los recibos se numeran de forma correlativa por escuela ([RN-21](../03-reglas-de-negocio/recibos.md)) y solo los emite el servidor al confirmar un pago ([ADR-003](0003-pagos-confirmados-por-servidor.md)). Un pago familiar genera varios recibos en una misma operación ([RN-16](../03-reglas-de-negocio/pagos.md)), y dos administradores pueden registrar pagos al mismo tiempo.

## Decisión

- Cada escuela tiene un **contador propio** en una tabla de numeradores.
- Al confirmar un pago, la misma transacción bloquea la fila del contador de esa escuela (`SELECT … FOR UPDATE`), toma el siguiente número, emite el recibo y actualiza el contador.
- Si la transacción falla, el número no se consume: la numeración **no tiene huecos**.
- Un recibo anulado conserva su número; el recibo que lo reemplaza recibe un número nuevo ([RN-23](../03-reglas-de-negocio/recibos.md)).
- La base garantiza la unicidad con una restricción única sobre escuela y número.

## Alternativas consideradas

- **Secuencias de PostgreSQL:** más simples y sin bloqueo, pero dejan huecos cuando una transacción se revierte.
- **Calcular el máximo más uno:** falla con dos pagos simultáneos.

## Consecuencias

- Los pagos de una misma escuela se serializan en el momento de numerar, algo aceptable para el volumen previsto.
- El formato visible del número (prefijo, ceros a la izquierda) se define en el diseño del recibo.
