# Alcance de la versión 1.0

## Incluye

### Área pública
- Sitio institucional por escuela, generado a partir de una plantilla configurable (ver [sitio público](../06-sitio-publico/rojas-fc.md)).
- Acceso al formulario de preinscripción.

### Administración
Escuelas, usuarios, alumnos, tutores, categorías, preinscripciones, cuotas, recargos, eventos, indumentaria, pagos, recibos, deudas, observaciones, auditoría y reportes.

### Portal de familias
Acceso privado de consulta a los alumnos vinculados: situación de cuotas, deuda, historial de pagos y descarga de recibos.

### Personalización por escuela
- Nombre, logo, colores y datos de contacto.
- Disciplina o disciplinas que dicta.
- Configuración administrativa: monto de la cuota, vencimiento sugerido, descuento por hermanos, recargos y formas de pago.

La categoría de cada alumno es su año de nacimiento, calculado por el sistema.

Las categorías propias con horarios, el vocabulario propio y los campos adicionales del alumno quedan para una versión futura.

### Comunicaciones
- Botón "Compartir por WhatsApp" para recibos y datos de acceso; el envío lo hace el administrador.
- Correos transaccionales: verificación de mail y acceso al portal.

### Acceso
Aplicación web *responsive* y PWA, con funcionamiento offline controlado, incluido el registro de pagos pendientes de confirmar ([RN-17](../03-reglas-de-negocio/pagos.md)).

## No incluye en la v1.0

- Pagos en línea.
- Envío automático por WhatsApp Business (los recibos se comparten manualmente).
- Avisos por correo (deuda, vencimientos) y notificaciones push.
- Módulo de control de asistencia (sí planillas imprimibles).

Ver el [backlog de versiones futuras](backlog-futuro.md).
