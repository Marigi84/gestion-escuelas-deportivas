# Alcance de la versión 1.0

## Incluye

### Área pública
- Sitio institucional por escuela, generado a partir de una plantilla configurable (ver [sitio público](../06-sitio-publico/rojas-fc.md)).
- Acceso al formulario de preinscripción.

### Administración
Escuelas, usuarios, alumnos, tutores, categorías, preinscripciones, cuotas, recargos, pagos, recibos, deudas, observaciones, auditoría y reportes.

### Portal de familias
Acceso privado de consulta a los alumnos vinculados: situación de cuotas, deuda, historial de pagos y descarga de recibos.

### Personalización por escuela
- Nombre, logo, colores y datos de contacto.
- Disciplina o disciplinas que dicta.
- Categorías propias, por año de nacimiento o asignadas a mano, con días, horarios y lugar.
- Configuración administrativa: monto de la cuota, vencimiento sugerido, descuento por hermanos, recargos, meses sin cuota y formas de pago.

El vocabulario propio y los campos adicionales del alumno quedan para una versión futura.

### Comunicaciones
- Botón "Compartir por WhatsApp" para recibos y datos de acceso; el envío lo hace el administrador.
- Correos transaccionales: verificación de mail y acceso al portal.

### Acceso
Aplicación web *responsive* y PWA, con funcionamiento offline controlado (ver [ADR pendiente](../adr/index.md#adr-a-formalizar)).

## No incluye en la v1.0

- Pagos en línea.
- Envío automático por WhatsApp Business (los recibos se comparten manualmente).
- Avisos por correo (deuda, vencimientos) y notificaciones push.
- Confirmación completa de pagos offline.
- Módulo de control de asistencia (sí planillas imprimibles).

Ver el [backlog de versiones futuras](backlog-futuro.md).
