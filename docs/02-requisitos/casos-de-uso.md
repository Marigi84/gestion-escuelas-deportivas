# Casos de uso

Casos de uso de la v1.0 por actor. Los marcados con ⭐ se detallan abajo y sirven para validar el [modelo de datos](../04-modelo-de-datos/index.md): cada paso indica qué entidades lee o escribe.

## Actores

| Actor | Descripción |
|---|---|
| Tutor | Madre, padre o adulto responsable. Consulta desde el portal de familias. |
| Administrador | Usuario de la escuela con todos los permisos de gestión (RN-37 a RN-39). |
| Superadministrador | Responsable de la plataforma (RN-43). |
| Sistema | Procesos automáticos. |

## Lista de casos de uso

### Tutor

| ID | Caso de uso | Reglas |
|---|---|---|
| CU-01 | Ingresar al portal y cambiar la contraseña inicial | RN-45 a RN-47 |
| CU-02 ⭐ | Consultar la deuda de sus hijos por concepto | RN-48, RN-60 |
| CU-03 | Ver el historial de pagos | RN-48 |
| CU-04 | Descargar un recibo | RN-24 |

### Administrador

| ID | Caso de uso | Reglas |
|---|---|---|
| CU-05 ⭐ | Revisar y aprobar o rechazar una preinscripción | RN-25 a RN-29 |
| CU-06 | Dar de alta un alumno directamente | RN-28 |
| CU-07 | Vincular tutores y hermanos (grupo familiar) | RN-06, RN-29 |
| CU-08 | Dar de baja o reactivar a un alumno | RN-31 a RN-35, RN-63 |
| CU-09 | Actualizar el monto de la cuota | RN-01, RN-02 |
| CU-10 ⭐ | Abrir el mes y anular la apertura | RN-03, RN-05, RN-06, RN-15, RN-61 |
| CU-11 | Marcar un mes como sin cobro | RN-04 |
| CU-12 | Ajustar, condonar o anular una deuda | RN-10, RN-33 |
| CU-13 | Crear un evento y anotar alumnos | RN-55, RN-56 |
| CU-14 | Registrar un pedido de indumentaria | RN-58 |
| CU-15 ⭐ | Registrar un pago | RN-11 a RN-16, RN-19, RN-62 |
| CU-16 ⭐ | Registrar un pago sin conexión y sincronizarlo | RN-17 |
| CU-17 | Anular un pago o un recibo | RN-18, RN-23 |
| CU-18 | Compartir un recibo por WhatsApp | RN-24 |
| CU-19 | Ver el dashboard | RN-49, RN-50 |
| CU-20 | Sacar listados y reportes (por categoría, deudores, recaudación, altas y bajas) | RN-51 a RN-54 |
| CU-21 | Gestionar otros administradores y la configuración de la escuela | RN-38 |
| CU-26 | Ver los participantes de un evento | RN-64 |
| CU-27 | Ver los pedidos de indumentaria | RN-64 |

### Superadministrador

| ID | Caso de uso | Reglas |
|---|---|---|
| CU-22 | Registrar o crear una escuela | RN-41 |
| CU-23 | Entrar a una escuela en modo soporte | RN-43 |

### Sistema

| ID | Caso de uso | Reglas |
|---|---|---|
| CU-24 | Aplicar recargos al vencer una cuota | RN-08, RN-09 |
| CU-25 | Borrar preinscripciones rechazadas a los 30 días y anonimizar escuelas dadas de baja | RN-27, RN-42 |

## Casos detallados

### CU-02 – Consultar la deuda de sus hijos

- **Actor:** tutor.
- **Precondición:** el tutor ingresó al portal (CU-01).

**Flujo principal**

1. El sistema muestra los alumnos vinculados al tutor, de cualquier escuela. *Lee: usuario, tutor, vínculo tutor–alumno, alumno.*
2. Para cada alumno muestra la deuda separada en **cuotas**, **eventos** e **indumentaria**, con el total. *Lee: cuota, recargo, inscripción a evento, pedido, imputación (saldo = importe − imputado).*
3. El tutor abre un concepto y ve el detalle: cada cuota con su mes, vencimiento, recargo y saldo; cada evento o pedido con lo pagado y el saldo. *Lee: mes, cuota, recargo, evento, inscripción, pedido.*
4. Si el alumno tiene saldo a favor, se muestra aparte. *Lee: pago, imputación.*

**Alternativas**

- 2a. El alumno no tiene deuda: se muestra "al día".
- 2b. Hay pagos pendientes de sincronizar (CU-16): no se muestran hasta que el servidor los confirma.

**Reglas:** el tutor solo ve a sus alumnos (RN-48, ADR-006); las cuotas, recargos y deudas anuladas no suman.

### CU-05 – Revisar y aprobar o rechazar una preinscripción

- **Actor:** administrador.
- **Precondición:** hay preinscripciones pendientes importadas del formulario.

**Flujo principal**

1. El administrador abre la lista de preinscripciones pendientes. *Lee: preinscripción.*
2. Elige una y el sistema busca duplicados por DNI. *Lee: tutor (en toda la plataforma), alumno (en la escuela), otras preinscripciones pendientes.*
3. El administrador revisa los datos y, si hace falta, los corrige.
4. Aprueba la preinscripción.
5. El sistema crea el alumno, sus datos de salud y su primera permanencia, y crea o vincula los tutores. *Escribe: alumno, datos de salud, permanencia, tutor, vínculo tutor–alumno, usuario del tutor.*
6. El sistema borra los datos personales de la preinscripción y deja el estado, la fecha, quién la aprobó y el alumno creado. *Escribe: preinscripción, auditoría.*
7. El administrador comparte el acceso al portal por WhatsApp, o el sistema lo envía por mail (RN-44).

**Alternativas**

- 2a. El tutor ya existe: se vincula en lugar de crearlo.
- 2b. El alumno ya existe en la escuela: el sistema ofrece reactivarlo (CU-08) en lugar de crearlo.
- 2c. Hay otra preinscripción pendiente con el mismo DNI: el sistema avisa; el administrador puede rechazar la repetida.
- 4a. El administrador la rechaza: queda rechazada, con quién y cuándo, y sus datos se borran a los 30 días (CU-25).
- 5a. El alumno tiene un hermano en la escuela: el administrador lo vincula al grupo familiar (CU-07).

### CU-10 – Abrir el mes y anular la apertura

- **Actor:** administrador.
- **Precondición:** el mes no está abierto ni marcado como sin cobro.

**Flujo principal**

1. El administrador elige "Abrir mes". El sistema propone el monto vigente, el vencimiento sugerido y los recargos sugeridos. *Lee: monto de cuota, configuración.*
2. El administrador confirma o modifica el monto, la fecha de vencimiento y los escalones de recargo.
3. El sistema crea el mes y una cuota por cada alumno activo, con el monto y el descuento por hermanos si corresponde. *Escribe: mes, cuota. Lee: alumno, permanencia, grupo familiar, configuración.*
4. El sistema imputa los saldos a favor de cada alumno a su nueva cuota. *Lee: pago. Escribe: imputación.*
5. El sistema registra la apertura. *Escribe: auditoría.*

**Alternativas**

- 2a. Si el administrador cambió el monto, el sistema pregunta si es un nuevo monto vigente (CU-09). *Escribe: monto de cuota.*
- 3a. Un alumno se dio de alta a mitad de mes: el administrador ajusta su cuota con el proporcional (CU-12). *Escribe: ajuste.*

**Anular la apertura**

1. El administrador elige "Anular apertura" e indica el motivo.
2. El sistema verifica que ninguna cuota del mes tenga pagos registrados después de la apertura. *Lee: imputación.*
3. Anula el mes y sus cuotas, y revierte las imputaciones de saldo a favor. *Escribe: mes, cuota, imputación, auditoría.*
4. El administrador puede volver a abrir el mes.

- 2a. Alguna cuota tiene pagos: el sistema no permite anular y sugiere corregir con ajustes.

### CU-15 – Registrar un pago

- **Actor:** administrador.
- **Precondición:** el administrador verificó el ingreso (en efectivo o con el comprobante de la transferencia).

**Flujo principal**

1. El administrador elige la forma de pago, el importe total, la fecha de pago (por defecto, hoy) y una descripción opcional. *Lee: forma de pago de la escuela.*
2. Elige los alumnos y, para cada uno, el concepto y el importe: cuotas, un evento o un pedido. El sistema muestra la deuda de cada concepto. *Lee: cuota, recargo, inscripción, pedido, imputación.*
3. El sistema controla que la suma de las partes sea igual al importe total.
4. El sistema verifica si hay una operación con el mismo importe, la misma fecha y los mismos alumnos, y si la hay, pregunta si ya se cargó. *Lee: operación, pago.*
5. El administrador confirma. En una sola transacción, el sistema:
    1. crea la operación y un pago por cada parte; *Escribe: operación, pago.*
    2. imputa cada pago: en cuotas, de la deuda más antigua a la más nueva; en eventos y pedidos, a esa deuda; lo que sobra queda como saldo a favor; *Escribe: imputación.*
    3. emite un recibo por pago con el siguiente número de la escuela; *Escribe: recibo, numerador.*
    4. registra la auditoría. *Escribe: auditoría.*
6. El administrador comparte los recibos (CU-18).

**Alternativas**

- 1a. La fecha de pago es anterior al vencimiento de una cuota que ya tiene recargo: el sistema anula el recargo o lo recalcula (RN-62). *Escribe: recargo.*
- 2a. Un solo alumno y un solo concepto: el paso 2 se completa solo con el importe total.
- 4a. El administrador indica que ya estaba cargada: se cancela el registro.
- 5a. Falla cualquier paso: no se guarda nada y el número de recibo no se consume (ADR-009).

### CU-16 – Registrar un pago sin conexión y sincronizarlo

- **Actor:** administrador.
- **Precondición:** la aplicación está instalada y tiene datos sincronizados de la escuela.

**Flujo principal**

1. Sin conexión, el administrador registra el pago con los mismos datos que en CU-15. La aplicación muestra la deuda de la última sincronización.
2. La aplicación guarda la operación en el dispositivo como **pendiente de sincronizar**, con un identificador generado en el dispositivo. Puede mostrar un comprobante provisorio sin número.
3. Cuando vuelve la conexión, la aplicación envía las operaciones pendientes.
4. El servidor verifica que el identificador no se haya recibido antes. *Lee: operación.*
5. El servidor ejecuta los pasos 4 y 5 de CU-15 con la fecha de pago original y marca la operación como cargada sin conexión. *Escribe: operación, pago, imputación, recibo, numerador, auditoría.*
6. La aplicación muestra los recibos definitivos.

**Alternativas**

- 4a. El identificador ya se había recibido (doble envío): el servidor responde con la operación existente y no la duplica.
- 5a. El servidor detecta un posible duplicado (RN-12): la operación queda en espera hasta que el administrador confirme o descarte.
- 5b. La deuda cambió mientras tanto (por ejemplo, otro administrador cobró lo mismo): el sistema imputa a lo que quede pendiente y lo sobrante queda como saldo a favor; el administrador ve el resultado y puede anular (CU-17).

## Validación del modelo

Al recorrer los casos detallados se confirmó que el modelo conceptual tiene las entidades necesarias. Se suman dos detalles para el DER:

- **Operación:** un identificador generado en el dispositivo (CU-16, paso 2) y un estado "en espera" para los posibles duplicados (CU-16, 5a).
- **Preinscripción:** quién la revisó y cuándo, y el alumno creado, que quedan después de borrar los datos personales (CU-05, paso 6).
