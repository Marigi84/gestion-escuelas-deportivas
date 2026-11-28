# Propuesta de módulos

Este documento organiza el sistema en módulos funcionales a partir de los [requisitos funcionales](requisitos-funcionales.md), las [reglas de negocio](../03-reglas-de-negocio/index.md), los [casos de uso](casos-de-uso.md) y el [alcance de la v1.0](../01-vision-y-alcance/alcance-v1.md).

Para cada módulo se indica de qué se encarga, qué requisitos cubre, qué casos de uso incluye y con qué prioridad se desarrolla. Esta etapa define solo la estructura funcional: las entidades, atributos y tablas corresponden al [modelo de datos](../04-modelo-de-datos/index.md), que viene después.

## 1. Escuelas y configuración

**Responsabilidad:** registrar las escuelas en la plataforma, darlas de baja y reactivarlas, y guardar la configuración de cada una: nombre, logo, colores, contacto, disciplinas, formas de pago, día de vencimiento sugerido, recargos sugeridos y descuento por hermanos.

Va primero porque todos los demás datos pertenecen a una escuela ([ADR-006](../adr/0006-aislamiento-multiescuela.md)).

- **Requisitos:** RF-01.
- **Casos de uso:** CU-21 (configuración), CU-22.
- **Reglas:** RN-05, RN-06, RN-08, RN-09, RN-11, RN-40 a RN-42.
- **Prioridad:** Alta.

## 2. Usuarios y acceso

**Responsabilidad:** ingreso al sistema de administradores (con su mail) y tutores (con su DNI), roles y permisos por escuela, contraseña inicial y su cambio obligatorio, bloqueo por intentos fallidos, restablecimiento, gestión de otros administradores, modo soporte y correos transaccionales.

Se agrupan el administrador y el tutor porque usan el mismo mecanismo de acceso con distintos permisos. Qué ve cada uno una vez adentro lo resuelve su propio módulo.

- **Requisitos:** RF-02, RF-03, RF-18.
- **Casos de uso:** CU-01 (ingreso), CU-21 (administradores), CU-23.
- **Reglas:** RN-37 a RN-39, RN-43 a RN-47.
- **Prioridad:** Alta. Sin acceso no se usa ningún otro módulo.

## 3. Alumnos, tutores y categorías

**Responsabilidad:** alta directa, modificación, baja y reactivación de alumnos con su historial de permanencias; datos de salud con acceso restringido; tutores y su vínculo con cada alumno; grupo familiar de hermanos; y cálculo de la categoría a partir del año de nacimiento.

- **Requisitos:** RF-04, RF-09, RF-10.
- **Casos de uso:** CU-06, CU-07, CU-08.
- **Reglas:** RN-26, RN-28 a RN-36, RN-63.
- **Prioridad:** Alta. Es la base de las cuotas, los eventos y los pagos.

## 4. Preinscripciones

**Responsabilidad:** importar las respuestas del formulario de Google, revisarlas con control de duplicados, aprobarlas o rechazarlas, y borrar los datos de las rechazadas a los 30 días.

Se separa de Alumnos porque tiene su propio circuito y sus propios estados, y porque nunca crea un alumno sin la aprobación del administrador ([ADR-002](../adr/0002-preinscripciones-con-aprobacion.md)). Al aprobar usa el módulo 3 para crear el alumno.

- **Requisitos:** RF-05 a RF-08.
- **Casos de uso:** CU-05, CU-25 (preinscripciones).
- **Reglas:** RN-25 a RN-29.
- **Prioridad:** Media. Mientras no esté, el alta directa (CU-06) cubre el ingreso de alumnos.

## 5. Cuotas

**Responsabilidad:** historial de montos, apertura y anulación del mes, meses sin cobro, generación de cuotas con el descuento por hermanos, recargos por mora en uno o dos escalones, condonación, y ajuste o anulación de deudas.

- **Requisitos:** RF-11.
- **Casos de uso:** CU-09, CU-10, CU-11, CU-12, CU-24.
- **Reglas:** RN-01 a RN-10, RN-30 a RN-33, RN-61, RN-62.
- **Prioridad:** Alta.

## 6. Pagos y recibos

**Responsabilidad:** registrar operaciones y repartirlas en pagos por alumno y concepto, imputarlos, manejar el saldo a favor, anular pagos y recibos, y emitir recibos numerados en PDF para descargar o compartir por WhatsApp.

Se agrupan porque cada pago confirmado emite su recibo en la misma transacción: son dos partes de la misma operación ([ADR-009](../adr/0009-numeracion-de-recibos.md)).

- **Requisitos:** RF-12, RF-13.
- **Casos de uso:** CU-15, CU-17, CU-18.
- **Reglas:** RN-11 a RN-16, RN-18 a RN-24, RN-60, RN-63.
- **Prioridad:** Alta.

## 7. Eventos e indumentaria

**Responsabilidad:** crear eventos con su precio único, anotar alumnos, registrar pedidos de indumentaria y anular inscripciones o pedidos. Los pagos de estos conceptos se registran en el módulo 6.

- **Requisitos:** RF-19, RF-20.
- **Casos de uso:** CU-13, CU-14.
- **Reglas:** RN-55 a RN-60.
- **Prioridad:** Media. Complementa a las cuotas.

## 8. Dashboard y reportes

**Responsabilidad:** mostrar los indicadores al ingresar (alumnos activos, deudores, recaudación del mes y aviso de mes sin abrir), el detalle de la recaudación, y los listados y reportes exportables: alumnos por categoría, deudores, altas y bajas, participantes de eventos y pedidos de indumentaria.

En el Trabajo Final el dashboard y los reportes eran dos módulos. Acá se unen porque un mismo requisito los cubre (RF-15) y porque el detalle de la recaudación se abre desde el dashboard.

- **Requisitos:** RF-15.
- **Casos de uso:** CU-19, CU-20, CU-26, CU-27.
- **Reglas:** RN-49 a RN-54, RN-64.
- **Prioridad:** Media. Lee los datos que generan los otros módulos.

## 9. Portal de familias

**Responsabilidad:** que el tutor consulte, solo para leer, los alumnos vinculados de cualquier escuela, su deuda separada por concepto, el historial de pagos y los recibos.

El ingreso y el cambio de contraseña del tutor pertenecen al módulo 2. Este módulo resuelve qué ve el tutor una vez adentro.

- **Requisitos:** RF-14.
- **Casos de uso:** CU-02, CU-03, CU-04.
- **Reglas:** RN-45, RN-48, RN-60.
- **Prioridad:** Media.

## 10. Funcionamiento sin conexión

**Responsabilidad:** instalar la aplicación (PWA), consultar los datos sincronizados sin internet, guardar pagos pendientes de sincronizar y enviarlos al servidor cuando vuelve la conexión, sin duplicarlos.

- **Requisitos:** RF-17.
- **Casos de uso:** CU-16.
- **Reglas:** RN-17; [ADR-003](../adr/0003-pagos-confirmados-por-servidor.md).
- **Prioridad:** Media. Depende de que el registro de pagos (módulo 6) esté terminado.

## 11. Auditoría

**Responsabilidad:** registrar quién hizo cada operación relevante y cuándo, incluidos los accesos en modo soporte, y conservar el historial sin borrar nada contable.

No tiene pantallas propias en la v1.0: los otros módulos escriben en la auditoría como parte de cada operación. Se cuenta como módulo porque tiene su propio requisito (RF-16) y su propia decisión de diseño ([ADR-008](../adr/0008-historial-y-auditoria.md)).

- **Requisitos:** RF-16.
- **Casos de uso:** forma parte de todos los que modifican datos.
- **Reglas:** RN-39, RN-43; ADR-008.
- **Prioridad:** Alta. Tiene que existir desde la primera operación que se registre.

## 12. Sitio público

**Responsabilidad:** el sitio institucional de cada escuela a partir de una plantilla: presentación, categorías y horarios, actividades especiales, galería, novedades, ubicación, contacto por WhatsApp y acceso al formulario de preinscripción.

No usa la base de datos de la gestión en la v1.0: el contenido se edita aparte de la estructura visual.

- **Requisitos:** RFP-01 a RFP-11.
- **Prioridad:** Media. Es independiente del resto, por eso su hito es propio.

## Prioridad y orden de desarrollo

- **Alta:** sin estos módulos no se puede registrar un alumno, cobrarle la cuota y emitir su recibo.
- **Media:** completan el sistema. Se desarrollan después del núcleo o en paralelo, porque usan sus datos.

Todos los módulos son parte de la v1.0. La prioridad indica el orden y qué se protege primero si hay atrasos.

| Módulo | Prioridad | Hito del [roadmap](../gestion/roadmap.md) |
|---|---|---|
| 1. Escuelas y configuración | Alta | M2 |
| 2. Usuarios y acceso | Alta | M2 |
| 11. Auditoría | Alta | M2 |
| 3. Alumnos, tutores y categorías | Alta | M2 |
| 5. Cuotas | Alta | M2 |
| 6. Pagos y recibos | Alta | M2 |
| 4. Preinscripciones | Media | M2 |
| 7. Eventos e indumentaria | Media | M2 |
| 8. Dashboard y reportes | Media | M2 |
| 9. Portal de familias | Media | M3 |
| 10. Funcionamiento sin conexión | Media | M3 |
| 12. Sitio público | Media | M1 |

## Cobertura de requisitos

| Módulo | Requisitos | Cantidad |
|---|---|---|
| 1. Escuelas y configuración | RF-01 | 1 |
| 2. Usuarios y acceso | RF-02, RF-03, RF-18 | 3 |
| 3. Alumnos, tutores y categorías | RF-04, RF-09, RF-10 | 3 |
| 4. Preinscripciones | RF-05 a RF-08 | 4 |
| 5. Cuotas | RF-11 | 1 |
| 6. Pagos y recibos | RF-12, RF-13 | 2 |
| 7. Eventos e indumentaria | RF-19, RF-20 | 2 |
| 8. Dashboard y reportes | RF-15 | 1 |
| 9. Portal de familias | RF-14 | 1 |
| 10. Funcionamiento sin conexión | RF-17 | 1 |
| 11. Auditoría | RF-16 | 1 |
| **Total gestión** | **RF-01 a RF-20** | **20** |
| 12. Sitio público | RFP-01 a RFP-11 | 11 |

Cada requisito tiene un solo módulo responsable: no hay requisitos sin cubrir ni requisitos repartidos entre dos módulos. Esto no impide que los módulos usen datos de otros. Por ejemplo, Pagos lee las deudas de Cuotas y de Eventos, y el Dashboard lee casi todo. La tabla indica quién es **dueño** de cada funcionalidad.

## Requisitos no funcionales

Los [requisitos no funcionales](requisitos-no-funcionales.md) no forman módulos propios. Son condiciones de calidad que todos los módulos deben cumplir: seguridad, aislamiento por escuela, rendimiento, integridad, usabilidad y disponibilidad.

## Fuera de la v1.0

Lo que no entra en la v1.0 está en el [backlog futuro](../01-vision-y-alcance/backlog-futuro.md). Por ejemplo, pagos en línea, envíos automáticos por WhatsApp, avisos por correo, asistencia y categorías propias por escuela.
