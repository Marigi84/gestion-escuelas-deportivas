# Requisitos no funcionales

Cada requisito no funcional tiene una **medida** y una forma de **verificarlo**, para que se pueda probar si se cumple. La columna **Origen** indica de dónde sale el valor:

- **Regla:** sale de una regla de negocio o de un ADR ya acordados.
- **A validar:** es un valor técnico inicial que se confirma con la escuela o en las pruebas de rendimiento.

El volumen de referencia para las pruebas es de **2.000 alumnos, 4.000 tutores, 100.000 cuotas y 50.000 pagos por escuela**, con **20 usuarios simultáneos**.

## Rendimiento

| ID | Requisito | Medida | Verificación | Origen |
|---|---|---|---|---|
| RNF-01 | Las consultas simples responden rápido. | ≤ 2 s en el 95 % de las consultas, con el volumen de referencia. | Prueba de carga sobre la API. | A validar |
| RNF-02 | Las búsquedas y los listados se paginan y filtran en el servidor. | ≤ 3 s en el 95 % de los casos. Ningún pedido devuelve más de 100 filas. | Prueba de carga y revisión de la API. | A validar |
| RNF-03 | Los recibos y los reportes básicos se generan en poco tiempo. | ≤ 5 s en el 95 % de los casos. | Prueba de carga. | A validar |
| RNF-04 | Las consultas frecuentes usan índices. | El plan de ejecución (EXPLAIN) de cada consulta frecuente no recorre la tabla completa con el volumen de referencia. | Revisión de planes con datos de prueba masivos. | A validar |

## Seguridad y privacidad

| ID | Requisito | Medida | Verificación | Origen |
|---|---|---|---|---|
| RNF-05 | Toda operación verifica en el servidor el rol y la escuela del usuario. | El 100 % de los endpoints protegidos rechaza el acceso a datos de otra escuela. | Pruebas de integración que piden datos de otra escuela y esperan un rechazo. | ADR-006 |
| RNF-06 | La base aísla los datos de cada escuela aunque falle el filtro de la aplicación. | Una consulta sin filtro de escuela no devuelve filas de otras escuelas. | Prueba con seguridad por filas activa. | ADR-006 |
| RNF-07 | Las contraseñas se guardan con un algoritmo de hash para contraseñas. | BCrypt o Argon2id; ninguna contraseña en texto plano ni con un hash simple. | Revisión de código y de la base. | A validar |
| RNF-08 | La sesión es segura. | Token en una cookie HttpOnly, Secure y SameSite, con vencimiento. Todo el tráfico va por HTTPS. | Revisión de cabeceras en el navegador. | A validar |
| RNF-09 | El acceso se bloquea después de varios intentos fallidos. | 5 intentos fallidos bloquean el ingreso por 15 minutos. | Prueba de valores límite: 4, 5 y 6 intentos. | RN-46 (los valores, a validar) |
| RNF-10 | Los datos de salud solo los ven los administradores de la escuela. | No aparecen en listados, exportaciones, el portal ni las respuestas de la API para otros roles. | Pruebas por rol. | RN-26, RN-54 |
| RNF-11 | Los recibos solo los descargan los administradores de la escuela y los tutores del alumno. | Cualquier otro usuario recibe un rechazo. | Pruebas por rol. | RN-24, RN-48 |
| RNF-12 | Las consultas a la base son parametrizadas. | Ninguna consulta arma SQL concatenando datos del usuario. | Análisis estático y revisión de código. | A validar |

## Integridad y trazabilidad

| ID | Requisito | Medida | Verificación | Origen |
|---|---|---|---|---|
| RNF-13 | El registro de un pago es atómico. | Si falla cualquier paso, no queda ni operación, ni pago, ni imputación, ni recibo. | Prueba que fuerza un error a mitad de la transacción. | ADR-009, CU-15 |
| RNF-14 | La numeración de recibos no tiene huecos ni repetidos, aunque haya pagos simultáneos. | Dos pagos simultáneos reciben números consecutivos distintos. | Prueba de concurrencia. | RN-21, ADR-009 |
| RNF-15 | La sincronización sin conexión no duplica pagos. | Reenviar la misma operación devuelve la existente. | Prueba de doble envío. | RN-17, CU-16 |
| RNF-16 | Nada contable se borra. | Las cuotas, recargos, pagos y recibos solo cambian de estado. | Revisión del modelo y pruebas de anulación. | ADR-008 |
| RNF-17 | Las operaciones relevantes quedan auditadas. | Cada pago, anulación, ajuste, condonación, baja y acceso en modo soporte registra quién, cuándo y qué cambió. | Pruebas que verifican el registro de auditoría. | RN-39, RN-43, ADR-008 |

## Usabilidad y accesibilidad

| ID | Requisito | Medida | Verificación | Origen |
|---|---|---|---|---|
| RNF-18 | La interfaz se adapta a celular, tablet y computadora. | Se puede usar sin desplazamiento horizontal desde 360 px de ancho. | Pruebas E2E en tres tamaños de pantalla. | A validar |
| RNF-19 | La interfaz cumple una accesibilidad básica. | WCAG 2.1 nivel AA en contraste, navegación con teclado y etiquetas de formularios. | Revisión automática (por ejemplo, axe) y manual. | A validar |
| RNF-20 | Los errores se explican en lenguaje claro. | Cada error indica qué pasó y qué hacer; no muestra mensajes técnicos. | Revisión de pantallas. | A validar |
| RNF-21 | Funciona en los navegadores actuales. | Las dos últimas versiones de Chrome, Edge, Firefox y Safari. | Pruebas E2E. | A validar |
| RNF-22 | Registrar un pago lleva pocos pasos. | Un pago de un alumno y un concepto se registra en 4 pasos o menos. | Prueba con un administrador de la escuela piloto. | A validar |

## Disponibilidad y operación

| ID | Requisito | Medida | Verificación | Origen |
|---|---|---|---|---|
| RNF-23 | Los datos se respaldan y se pueden recuperar. | Respaldo diario (pérdida máxima de 24 h) y recuperación en 4 h o menos. Una restauración de prueba por mes. | Registro de las restauraciones. | A validar |
| RNF-24 | Las fechas del negocio usan la hora de Argentina y todo el texto usa UTF-8. | Vencimientos, recargos y fechas de pago se calculan en America/Argentina/Buenos_Aires. Los acentos y las eñes se ven bien en la interfaz, los PDF y las exportaciones. | Pruebas cerca de la medianoche y con textos con acentos. | Lección del Trabajo Final |
| RNF-25 | Los correos transaccionales llegan en producción. | Se envían por un proveedor de correo que el hosting no bloquee. | Prueba de envío en el entorno de producción. | Lección del Trabajo Final |
| RNF-26 | Sin conexión, la aplicación muestra los últimos datos sincronizados. | Se ve la fecha y hora de la última sincronización. | Prueba en modo avión. | RF-17 |

## Mantenibilidad

| ID | Requisito | Medida | Verificación | Origen |
|---|---|---|---|---|
| RNF-27 | El código está organizado en capas. | Las reglas de negocio están en los servicios, nunca en los controladores ni en la interfaz. | Revisión de código en cada PR. | A validar |
| RNF-28 | Los cambios de la base son migraciones versionadas. | Cada cambio de esquema es una migración de Flyway; no se crean tablas automáticamente. | Revisión del repositorio. | ADR-007 |
| RNF-29 | Las reglas críticas tienen pruebas automáticas. | Al menos 70 % de cobertura de líneas en los servicios de cuotas, pagos y recibos. | Informe de cobertura en la integración continua. | A validar |
| RNF-30 | Los contenedores se ejecutan sin privilegios de administrador. | Ningún contenedor corre como root. | Análisis estático de la imagen. | Lección del Trabajo Final |

## Archivos

| ID | Requisito | Medida | Verificación | Origen |
|---|---|---|---|---|
| RNF-31 | Los archivos (logos y aptos médicos) se guardan fuera de las tablas principales. | Solo PDF, JPG o PNG, de hasta 5 MB. | Pruebas de carga de archivos con valores límite. | A validar |

## Sitio público

| ID | Requisito | Medida | Verificación | Origen |
|---|---|---|---|---|
| RNF-32 | El sitio carga rápido en el celular. | Largest Contentful Paint de 2,5 s o menos en una red móvil 4G. | Lighthouse en modo móvil. | A validar |
| RNF-33 | El contenido se edita aparte del diseño. | Se cambia un texto o una imagen sin tocar los componentes. | Revisión del repositorio del sitio. | A validar |

## Requisitos de dominio

Surgen de leyes o normas que el sistema debe respetar. Se van a validar con asesoramiento antes de que la plataforma la usen escuelas externas.

| ID | Requisito | Norma | Cómo se cumple |
|---|---|---|---|
| RD-01 | Los datos personales se tratan solo con el consentimiento de su titular, que tiene que saber para qué se usan. | Ley 25.326 de Protección de Datos Personales | El formulario de preinscripción informa la finalidad y pide el consentimiento del tutor, en nombre propio y del alumno. |
| RD-02 | El titular puede acceder a sus datos, rectificarlos o pedir que se supriman. | Ley 25.326 | El tutor ve los datos en el portal; las correcciones y bajas las hace el administrador (RN-48). |
| RD-03 | Los datos de salud son datos sensibles y necesitan una protección mayor. | Ley 25.326 | Acceso restringido y separados del alumno (RN-26, RNF-10). |
| RD-04 | Los datos no se conservan más tiempo del necesario. | Ley 25.326 | Las preinscripciones rechazadas se borran a los 30 días y los datos de una escuela dada de baja se anonimizan a los 6 meses (RN-27, RN-42). |
| RD-05 | El recibo es un comprobante interno y no reemplaza a la factura. | Normativa de ARCA (ex AFIP) | El recibo lo indica, y el sistema ofrece un enlace a ARCA para emitir la factura (RN-22). |
