# ADR-008: Historial, bajas lógicas y auditoría

- **Estado:** Aceptada
- **Fecha:** 2026-11-26 (aceptada el 2026-11-27)

## Contexto

Varias reglas exigen no perder información: bajas y reincorporaciones de alumnos ([RN-35](../03-reglas-de-negocio/alumnos.md)), ajustes de deuda ([RN-33](../03-reglas-de-negocio/alumnos.md)), anulación de pagos y recibos ([RN-18](../03-reglas-de-negocio/pagos.md), [RN-23](../03-reglas-de-negocio/recibos.md)), condonaciones ([RN-10](../03-reglas-de-negocio/cuotas.md)), trazabilidad de cada administrador ([RN-39](../03-reglas-de-negocio/usuarios-y-escuelas.md)) y accesos en modo soporte ([RN-43](../03-reglas-de-negocio/usuarios-y-escuelas.md)). Al mismo tiempo, los datos personales de una escuela dada de baja se anonimizan a los 6 meses ([RN-42](../03-reglas-de-negocio/usuarios-y-escuelas.md)).

## Decisión

- **Nada contable se borra.** Cuotas, pagos, operaciones y recibos solo cambian de estado (por ejemplo, anulado), con motivo, usuario y fecha.
- **Las correcciones son registros propios.** Ajustes, condonaciones y anulaciones se guardan como filas nuevas que referencian lo que corrigen, con el valor anterior y el nuevo.
- **Bajas lógicas** para alumnos, tutores, administradores y escuelas: un estado más las fechas. Las permanencias del alumno se guardan como períodos (alta y baja).
- **Historial con vigencia** para valores que cambian con el tiempo, como el monto de la cuota ([RN-02](../03-reglas-de-negocio/cuotas.md)): cada valor tiene su fecha desde.
- **Tabla de auditoría única**, de solo inserción: fecha, usuario, escuela, entidad, identificador, acción y detalle en `jsonb`. La escribe el backend en la misma transacción que la operación.
- **Anonimización:** al vencer el plazo de RN-42 se reemplazan los datos personales por valores neutros. Los importes, estados y numeraciones se conservan, y la auditoría no guarda datos de salud.

## Alternativas consideradas

- **Auditoría por triggers de base de datos:** captura todo, pero no conoce el usuario de la aplicación ni el motivo sin configuración extra.
- **Tablas espejo de historial por entidad:** más detalle, pero duplica el esquema.

## Consecuencias

- Las consultas de datos vigentes filtran por estado; conviene usar índices parciales sobre los registros activos.
- La auditoría crece sin límite; su conservación y archivado se definen en la etapa de despliegue.
