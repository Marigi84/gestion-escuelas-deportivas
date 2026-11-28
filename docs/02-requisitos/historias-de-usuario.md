# Historias de usuario

## Sitio público (heredadas de Rojas FC)

| ID | Historia |
|---|---|
| HU-01 | Como madre, padre o tutor, quiero conocer la propuesta de la escuela, para decidir si es adecuada para mi hijo/a. |
| HU-02 | Como madre, padre o tutor, quiero consultar categorías, edades, días y horarios, para saber si mi hijo/a puede participar. |
| HU-03 | Como persona interesada, quiero contactar a la escuela por WhatsApp, para consultar de forma rápida y directa. |
| HU-04 | Como madre, padre o tutor, quiero completar una preinscripción online, para iniciar el ingreso de mi hijo/a. |
| HU-05 | Como familia de un alumno, quiero conocer las actividades especiales (torneos, campamentos, viajes), para estar informada. |
| HU-06 | Como visitante, quiero ver fotos de entrenamientos, partidos y actividades, para conocer el ambiente de la escuela. |
| HU-07 | Como administrador, quiero actualizar horarios, novedades, actividades y fotos, para mantener la información vigente. |

## Sistema de gestión (a desarrollar)

| ID | Historia |
|---|---|
| HU-08 | Como administrador, quiero importar las preinscripciones desde Google Sheets, para no cargarlas a mano. |
| HU-09 | Como administrador, quiero aprobar o rechazar una preinscripción, para controlar quién ingresa como alumno. |
| HU-10 | Como administrador, quiero registrar un pago y emitir el recibo en PDF, para entregarlo a la familia por WhatsApp. |
| HU-11 | Como administrador, quiero imprimir el listado de alumnos activos por categoría, para usarlo en los entrenamientos. |
| HU-12 | Como tutor, quiero ver la deuda y descargar los recibos de mis hijos, para tener control de los pagos. |
| HU-13 | Como responsable de una escuela, quiero registrarla en la plataforma y configurar su disciplina, para empezar a usar el sistema. |
| HU-14 | Como superadministrador, quiero crear una escuela en nombre de una institución, para incorporarla sin que tenga que registrarse sola. |
| HU-15 | Como administrador, quiero abrir el mes revisando el monto, el vencimiento y los recargos, para que se generen las cuotas solo cuando estén bien. |
| HU-16 | Como administrador, quiero registrar un pago aunque no tenga internet, para no perder el cobro y que se confirme cuando vuelva la conexión. |

## Criterios de aceptación

Las historias principales tienen criterios en formato **Dado / Cuando / Entonces**. Incluyen los casos negativos, porque también hay que probar lo que el sistema no debe permitir. Cada criterio se convierte después en uno o más casos de prueba. Los demás criterios se escriben al planificar el sprint de cada historia.

### HU-09 – Aprobar o rechazar una preinscripción

Caso de uso: [CU-05](casos-de-uso.md#cu-05-revisar-y-aprobar-o-rechazar-una-preinscripcion). Reglas: RN-25 a RN-29.

1. **Aprobación:** dado una preinscripción pendiente sin duplicados, cuando el administrador la aprueba, entonces se crea el alumno activo con su primera permanencia y sus tutores, y la preinscripción queda aprobada sin datos personales.
2. **Tutor existente:** dado un tutor ya registrado con el mismo DNI en cualquier escuela, cuando se aprueba la preinscripción, entonces el tutor se vincula y no se crea otro.
3. **Alumno existente:** dado un alumno de la escuela con el mismo DNI, cuando el administrador abre la preinscripción, entonces el sistema avisa y ofrece reactivarlo en lugar de crear uno nuevo.
4. **Rechazo:** dado una preinscripción pendiente, cuando el administrador la rechaza, entonces no se crea ningún alumno y queda registrado quién la rechazó y cuándo.
5. **Borrado a los 30 días:** dado una preinscripción rechazada hace más de 30 días, cuando corre el proceso diario, entonces sus datos personales se borran.
6. **Ya resuelta:** dado una preinscripción que otro administrador ya aprobó, cuando un segundo administrador intenta aprobarla, entonces el sistema lo rechaza y muestra el estado actual.

### HU-10 – Registrar un pago y emitir el recibo

Caso de uso: [CU-15](casos-de-uso.md#cu-15-registrar-un-pago). Reglas: RN-11 a RN-16, RN-19 a RN-21.

1. **Pago de cuotas:** dado un alumno con las cuotas de marzo y abril impagas, cuando se registra un pago por el importe de una cuota, entonces se cancela marzo (la más antigua) y abril sigue pendiente.
2. **Saldo a favor:** dado un alumno al día, cuando se registra un pago de cuotas, entonces el importe queda como saldo a favor y se imputa al abrirse el mes siguiente.
3. **Pago familiar:** dado una operación de $30.000 repartida entre dos hermanos, cuando la suma de las partes es $30.000, entonces se crea una operación con dos pagos y dos recibos, uno a nombre de cada alumno.
4. **Suma incorrecta:** dado una operación de $30.000, cuando las partes suman $28.000, entonces el sistema no deja confirmar.
5. **Posible duplicado:** dado una operación ya registrada con el mismo importe, la misma fecha y los mismos alumnos, cuando se intenta registrar otra igual, entonces el sistema pregunta si ya se cargó antes de guardarla.
6. **Numeración:** dado que el último recibo de la escuela es el 120, cuando se registran dos pagos al mismo tiempo, entonces reciben los números 121 y 122, sin huecos ni repetidos.
7. **Falla:** dado un error en la emisión del recibo, cuando falla la transacción, entonces no queda guardado ni el pago ni la imputación, y el número no se consume.
8. **Concepto separado:** dado un pago al concepto "evento", cuando se registra, entonces no cancela cuotas aunque el alumno tenga cuotas impagas.

### HU-12 – Ver la deuda y descargar recibos (tutor)

Caso de uso: [CU-02](casos-de-uso.md#cu-02-consultar-la-deuda-de-sus-hijos-por-concepto). Reglas: RN-45, RN-48, RN-60.

1. **Deuda por concepto:** dado un tutor con un hijo que debe una cuota y una seña de un evento, cuando consulta la deuda, entonces la ve separada en cuotas y eventos, con el total.
2. **Varias escuelas:** dado un tutor con un hijo en cada una de dos escuelas, cuando ingresa al portal, entonces ve a los dos alumnos.
3. **Solo sus alumnos:** dado un tutor autenticado, cuando pide la deuda o un recibo de un alumno que no está vinculado a él, entonces el sistema lo rechaza.
4. **Anulados:** dado una cuota anulada, cuando el tutor consulta la deuda, entonces esa cuota no suma.
5. **Recibo:** dado un pago confirmado, cuando el tutor descarga el recibo, entonces obtiene el PDF a nombre del alumno.
6. **Solo consulta:** dado un tutor en el portal, cuando intenta modificar un dato, entonces no hay ninguna opción para hacerlo.

### HU-15 – Abrir el mes

Caso de uso: [CU-10](casos-de-uso.md#cu-10-abrir-el-mes-y-anular-la-apertura). Reglas: RN-01 a RN-06, RN-08, RN-09, RN-61.

1. **Apertura:** dado 3 alumnos activos y 1 dado de baja, cuando el administrador abre el mes, entonces se generan 3 cuotas con el monto confirmado.
2. **Descuento por hermanos:** dado dos hermanos activos en el mismo grupo familiar y un descuento del 10 %, cuando se abre el mes, entonces las dos cuotas tienen el 10 % de descuento.
3. **Saldo a favor:** dado un alumno con $5.000 de saldo a favor, cuando se abre el mes, entonces ese saldo se imputa a su nueva cuota.
4. **Sin duplicar:** dado un mes ya abierto, cuando otro administrador intenta abrirlo, entonces el sistema lo rechaza y no genera cuotas repetidas.
5. **Anulación permitida:** dado un mes abierto sin pagos, cuando el administrador anula la apertura con un motivo, entonces las cuotas quedan anuladas y los saldos a favor vuelven a estar disponibles.
6. **Anulación rechazada:** dado un mes con al menos una cuota pagada después de la apertura, cuando el administrador intenta anularla, entonces el sistema no lo permite.
7. **Recargo:** dado una cuota con saldo al día siguiente del vencimiento y un recargo del 10 %, cuando corre el proceso diario, entonces se aplica un recargo del 10 % sobre el saldo impago, una sola vez.

### HU-16 – Registrar un pago sin conexión

Caso de uso: [CU-16](casos-de-uso.md#cu-16-registrar-un-pago-sin-conexion-y-sincronizarlo). Reglas: RN-12, RN-17.

1. **Pendiente:** dado un administrador sin conexión, cuando registra un pago, entonces queda pendiente de sincronizar, sin número de recibo, y la deuda no cambia en el servidor.
2. **Sincronización:** dado un pago pendiente, cuando vuelve la conexión, entonces el servidor lo confirma con la fecha de pago original y emite el recibo numerado.
3. **Doble envío:** dado un pago que ya se sincronizó, cuando la aplicación lo vuelve a enviar, entonces el servidor no lo duplica.
4. **Posible duplicado:** dado un pago sin conexión igual a otro ya registrado, cuando se sincroniza, entonces queda en espera hasta que el administrador lo confirme o lo descarte.
5. **Aviso:** dado operaciones pendientes en el dispositivo, cuando el administrador intenta cerrar la sesión, entonces la aplicación le avisa que se perderían.
