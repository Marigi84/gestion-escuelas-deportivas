# ADR-003: Pagos definitivos solo con confirmación del servidor

- **Estado:** Aceptada
- **Fecha:** 2026-11-26

## Contexto

La aplicación tendrá un modo offline. Registrar pagos sin conexión podría generar recibos duplicados, numeración inconsistente o deudas mal calculadas.

## Decisión

- Un pago solo es **definitivo** cuando el servidor lo confirma dentro de una transacción.
- Solo los pagos definitivos emiten recibos numerados.
- Una eventual captura provisional offline queda por definir y **no** emitirá recibos definitivos.

## Consecuencias

- Se garantiza la integridad de la numeración de recibos y del cálculo de deuda.
- Registrar pagos requiere conexión en la v1.0.
- La confirmación completa de pagos offline queda en el backlog futuro.
