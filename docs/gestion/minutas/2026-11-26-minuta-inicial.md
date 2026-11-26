# Minuta inicial – 26/11/2026

**Etapa:** análisis y diseño · **Versión:** 0.1

## 1. Objetivo y visión

Aplicación web rápida, segura y escalable para centralizar la administración de escuelas. Rojas FC será la primera implementación, con posibilidad de incorporar las otras escuelas del mismo propietario y luego instituciones externas. Producto general y personalizable desde su origen.

## 2. Alcance v1.0

Área pública, administración, portal de familias, personalización por escuela, web *responsive* y PWA con offline controlado. Ver [alcance](../../01-vision-y-alcance/alcance-v1.md).

## 3. Roles

Superadministrador, administrador de escuela y tutor/familia. Separación de datos verificada en el servidor. Queda por definir el alcance exacto del superadministrador.

## 4. Preinscripciones

Google Forms → Google Sheets → importación → revisión y aprobación. Ver [ADR-002](../../adr/0002-preinscripciones-con-aprobacion.md).

## 5. Cuotas, pagos y recibos

Cuotas mensuales, vencimientos, deuda e intereses. Recibos numerados en PDF para descargar o compartir por WhatsApp. Pagos definitivos con confirmación del servidor. Pendientes: intereses, descuentos, pagos parciales, imputación, anulaciones y numeración.

## 6. Reportes

Excel, PDF y vista de impresión. Prioridad: alumnos activos por categoría.

## 7. Requisitos no funcionales

Ver [RNF](../../02-requisitos/requisitos-no-funcionales.md).

## 8. Offline

PWA + IndexedDB. Consulta de datos sincronizados, cola local de cambios no críticos, indicadores de estado. Pagos solo online.

## 9. ADR

ADR-001, ADR-002 y ADR-003 aceptadas. Stack propuesto: React/TS/Vite, Spring Boot, PostgreSQL, REST.

## 10. Documentación

Tres documentos vivos: Análisis y Diseño, ADR y Backlog.

## 12. Próximos pasos

Capítulo de **Reglas de Negocio**, luego casos de uso, modelo de datos, arquitectura, API, pantallas, plan de desarrollo y despliegue.

## 13. Puntos a validar

Políticas de cuotas, datos obligatorios del formulario, autenticación offline, resolución de conflictos, condiciones de prueba de rendimiento y carácter fiscal de los recibos.

## Actualización posterior (26/11/2026)

- Se decidió ampliar el alcance a **todas las escuelas deportivas**, con especialización configurable por escuela ([ADR-004](../../adr/0004-plataforma-multidisciplina.md)).
- Se adoptó **docs-as-code** en este repositorio y **GitHub Projects** para la gestión.
