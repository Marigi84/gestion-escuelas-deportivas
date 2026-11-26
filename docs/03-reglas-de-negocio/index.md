# Reglas de negocio

!!! warning "Próximo capítulo"
    Es el siguiente capítulo acordado y debe completarse **antes de diseñar la base de datos**. Este documento lista los temas a definir y las preguntas abiertas.

Cada regla se registrará con un identificador `RN-XX`, su descripción, el módulo, ejemplos y la fuente (quién la validó y cuándo).

## Temas a definir

### Escuelas
- Alta, desactivación y personalización.
- Conservación de datos al desactivar una escuela.
- Configuración de disciplinas, categorías, vocabulario y campos adicionales.

### Usuarios
- Creación, roles y permisos.
- Administradores de varias escuelas.
- Alcance exacto del superadministrador.

### Alumnos
- Alta, baja, reingreso.
- Cambio de categoría.
- Observaciones e historial.

### Tutores
- Vínculos con alumnos, hermanos.
- Responsable de pago.

### Preinscripciones
- Estados (pendiente, aprobada, rechazada, incompleta).
- Aprobación, correcciones y detección de duplicados.
- Datos obligatorios del formulario.

### Cuotas
- Generación mensual.
- Altas y bajas durante el mes (¿cuota completa o proporcional?).
- Vencimientos, intereses por mora y descuentos (por ejemplo, por hermanos).

### Pagos
- Formas de pago.
- Pagos parciales e imputación a varias cuotas.
- Anulaciones y reembolsos.

### Recibos
- Numeración (por escuela, correlativa, sin saltos).
- Datos obligatorios.
- Inmutabilidad y anulación.
- Carácter fiscal o interno.

### Portal de familias
- Permisos y acceso.
- Recuperación de contraseña.

### Reportes
- Filtros, formatos y campos.
- Protección de datos según el rol.

## Preguntas abiertas para Rojas FC

1. ¿Cuál es el monto de la cuota y varía por categoría?
2. ¿Qué día vence la cuota?
3. ¿Se cobra recargo por mora? ¿Monto fijo o porcentaje? ¿Desde qué día?
4. ¿Hay descuento por hermanos u otros descuentos?
5. ¿Se aceptan pagos parciales?
6. ¿Qué formas de pago se usan (efectivo, transferencia, otra)?
7. ¿Los recibos tienen valor fiscal o son comprobantes internos?
8. ¿Qué datos se piden hoy en la inscripción?
