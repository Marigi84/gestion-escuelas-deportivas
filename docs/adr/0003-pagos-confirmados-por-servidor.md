# ADR-003: Pagos definitivos solo con confirmación del servidor

- **Estado:** Aceptada
- **Fecha:** 2026-11-26

## Contexto

La aplicación tendrá un modo offline. Registrar pagos sin conexión podría generar recibos duplicados, numeración inconsistente o deudas mal calculadas.

## Decisión

- Un pago solo es **definitivo** cuando el servidor lo confirma dentro de una transacción.
- Solo los pagos definitivos emiten recibos numerados.
- Sin conexión, el pago se carga en el dispositivo como **pendiente de sincronizar**. No emite recibo numerado ni actualiza la deuda hasta que el servidor lo confirma (actualizado el 2026-11-27, ver [RN-17](../03-reglas-de-negocio/pagos.md)).

## Consecuencias

- Se garantiza la integridad de la numeración de recibos y del cálculo de deuda.
- Se pueden cargar pagos sin conexión, pero solo son definitivos al sincronizar.
- La aplicación debe evitar el doble envío de un pago pendiente (por ejemplo, con un identificador generado en el dispositivo) y avisar de posibles duplicados (RN-12).
