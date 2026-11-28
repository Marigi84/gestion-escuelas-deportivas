# Riesgos, supuestos y restricciones

- Un **riesgo** es algo que todavía puede ocurrir y afectar los objetivos.
- Un **supuesto** es algo que se da por cierto para planificar, pero no está confirmado.
- Una **restricción** es un límite que hay que respetar.
- Un **problema** es algo que ya ocurrió.

## Riesgos

Escalas: **probabilidad (P)** y **impacto (I)** de 1 (bajo) a 3 (alto). La **exposición** es P × I: de 1 a 2 es baja, de 3 a 4 es media y de 6 a 9 es alta. La responsable de todos los riesgos es Marina, como única desarrolladora.

| ID | Riesgo | P | I | P×I | Respuesta | Mitigación (para que no ocurra) | Contingencia (si ocurre) | Estado |
|---|---|---|---|---|---|---|---|---|
| R-02 | Se exponen datos de menores o de otra escuela | 2 | 3 | 6 | Mitigar | Autorización en el servidor, seguridad por filas (ADR-006), pruebas de acceso por rol (RNF-05, RNF-06, RNF-10) y datos ficticios en el repositorio | Cortar el acceso afectado, revisar la auditoría, avisar a la escuela y corregir antes de volver a habilitar | Abierto |
| R-04 | Conflictos o duplicados al sincronizar pagos cargados sin conexión | 2 | 3 | 6 | Mitigar | El servidor confirma todo (ADR-003), con un identificador por operación y aviso de duplicados (RN-12, RNF-15) | Operaciones en espera para que el administrador las revise; anulación con motivo | Abierto |
| R-07 | Pagos o recibos duplicados por operaciones simultáneas | 2 | 3 | 6 | Mitigar | Transacciones con bloqueo y restricciones de unicidad (ADR-009, RNF-13, RNF-14) y pruebas de concurrencia | Anular el pago o recibo duplicado, que queda registrado | Abierto |
| R-08 | Alcance creciente: se sumaron eventos, indumentaria y pagos sin conexión a la v1.0 | 3 | 2 | 6 | Mitigar | Alcance con línea base, prioridad por módulos y cambios registrados en minutas y CHANGELOG | Pasar los módulos de prioridad media a una versión posterior, sin tocar el núcleo | Abierto |
| R-09 | Pérdida de datos por no tener respaldos o porque no se pueden restaurar | 1 | 3 | 3 | Mitigar | Respaldo diario y restauración de prueba mensual (RNF-23) | Restaurar el último respaldo y volver a cargar lo registrado después | Abierto |
| R-10 | El plan gratuito de hosting bloquea el envío de correos (pasó en el Trabajo Final) | 3 | 2 | 6 | Evitar | Proveedor de correo transaccional desde el inicio (RNF-25); el acceso al portal también se comparte por WhatsApp (RN-44) | Compartir el acceso por WhatsApp mientras se cambia de proveedor | Abierto |
| R-11 | Fechas y recargos mal calculados por la zona horaria del servidor (pasó en el Trabajo Final) | 2 | 2 | 4 | Evitar | Hora de Argentina fija para las fechas de negocio y pruebas cerca de la medianoche (RNF-24) | Recalcular los recargos afectados con ajustes registrados | Abierto |
| R-12 | Textos con acentos o eñes que se ven mal en PDF o exportaciones (pasó en el Trabajo Final) | 2 | 1 | 2 | Evitar | UTF-8 en toda la cadena y pruebas con textos con acentos (RNF-24) | Corregir la configuración y volver a generar los archivos | Abierto |
| R-13 | El contenedor se ejecuta con privilegios de administrador (lo detectó el análisis estático en el Trabajo Final) | 2 | 2 | 4 | Evitar | Usuario sin privilegios en la imagen y análisis estático en la integración continua (RNF-30) | Corregir la imagen y volver a desplegar | Abierto |
| R-14 | Demora del primer pedido en servicios gratuitos que se suspenden por inactividad (pasó en el Trabajo Final) | 3 | 1 | 3 | Aceptar | Avisar en la interfaz que está cargando; evaluar un plan pago para producción | Plan con instancia siempre activa | Abierto |
| R-15 | Una sola persona desarrolla todo: una ausencia frena el proyecto | 2 | 2 | 4 | Mitigar | Documentación como código, ADR e issues que permitan retomar el trabajo | Repriorizar el backlog y extender los plazos | Abierto |
| R-16 | Los administradores no adoptan el sistema porque les resulta más lento que la planilla | 2 | 3 | 6 | Mitigar | Validar las pantallas con un administrador real, medir los pasos del pago (RNF-22) y hacer UAT en la escuela piloto | Ajustar los flujos con lo observado antes de sumar otras escuelas | Abierto |
| R-03 | Configurabilidad excesiva por ser multidisciplina | 2 | 2 | 4 | Mitigar | Alcance acotado en [ADR-004](../adr/0004-plataforma-multidisciplina.md): el vocabulario y los campos propios quedan para después | Mover las configuraciones nuevas al backlog futuro | Abierto |
| R-06 | Google Forms o Google Sheets cambian o limitan el acceso | 1 | 2 | 2 | Aceptar | Prueba de concepto de la importación y alta directa como alternativa (RN-28) | Cargar los alumnos con el alta directa mientras se adapta la importación | Abierto |
| R-01 | Reglas de cuotas e intereses sin definir | — | — | — | — | Se documentaron RN-01 a RN-64 | — | Cerrado (27/11/2026) |
| R-05 | Carácter fiscal de los recibos | — | — | — | — | Definido: el recibo es interno, no factura (RN-22) | — | Cerrado (26/11/2026) |

### Matriz de exposición

| Probabilidad \ Impacto | Bajo (1) | Medio (2) | Alto (3) |
|---|---|---|---|
| **Alta (3)** | R-14 | R-08, R-10 | |
| **Media (2)** | R-12 | R-03, R-11, R-13, R-15 | R-02, R-04, R-07, R-16 |
| **Baja (1)** | | R-06 | R-09 |

Los riesgos se revisan al cerrar cada sprint y antes de cada hito.

## Supuestos

| ID | Supuesto | Qué pasa si no se cumple |
|---|---|---|
| S-01 | La escuela piloto valida las reglas de negocio y prueba el sistema antes de usarlo. | Las reglas podrían no reflejar la práctica real; habría que hacer ajustes después de la entrega. |
| S-02 | Los administradores tienen un celular o una computadora con navegador actual, aunque la conexión pueda cortarse. | Habría que bajar los requisitos de navegador o reforzar el modo sin conexión. |
| S-03 | Las familias siguen usando WhatsApp como canal principal. | Habría que reforzar el envío por correo. |
| S-04 | El volumen de cada escuela está dentro del de referencia (2.000 alumnos). Rojas FC tiene alrededor de 140 alumnos activos. | Habría que revisar los índices y el particionado (ADR-006). |
| S-05 | El formulario de Google sigue siendo el canal de preinscripción. | Habría que construir un formulario propio. |

## Restricciones

| ID | Restricción |
|---|---|
| C-01 | El equipo es una sola persona, con dedicación parcial. |
| C-02 | El presupuesto de infraestructura es bajo: planes gratuitos o económicos. |
| C-03 | El repositorio es público y sirve de portafolio: no puede tener datos reales ni secretos. |
| C-04 | Hay que cumplir la Ley 25.326 de protección de datos personales (RD-01 a RD-04). |
| C-05 | El stack está definido en [ADR-007](../adr/0007-stack-tecnologico.md): React, Spring Boot y PostgreSQL. |
