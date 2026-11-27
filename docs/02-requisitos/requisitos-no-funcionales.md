# Requisitos no funcionales

!!! note "Borrador"
    La minuta menciona borradores RNF-01 a RNF-33. Aquí se agrupan por categoría los acordados; la numeración detallada se conciliará con esos borradores.

## Rendimiento

- Paginación y filtros resueltos en el servidor.
- Índices y consultas optimizadas.
- Carga bajo demanda y respuestas livianas; no cargar todo el historial al abrir una pantalla.

### Objetivos preliminares (a validar)

| Operación | Objetivo |
|---|---|
| Consulta simple | ≤ 2 s |
| Búsqueda paginada | ≤ 3 s |
| Recibo o reporte básico | ≤ 5 s |

Volumen de referencia para pruebas: 2.000 alumnos, 4.000 tutores, 100.000 cuotas y 50.000 pagos. Las condiciones de prueba todavía no están definidas y no se hicieron mediciones.

## Escalabilidad y mantenibilidad

- Arquitectura modular.
- Incorporar nuevas escuelas, disciplinas y funcionalidades sin reescrituras innecesarias.

## Seguridad y privacidad

- Autenticación y autorización por rol y escuela, verificada en el servidor.
- Contraseñas con hash seguro.
- Protección de datos de menores: los datos de salud solo los ven los administradores de la escuela y no salen en listados ni exportaciones.
- Anonimización de datos personales al vencer el plazo de conservación de una escuela dada de baja.
- Acceso restringido a recibos.

## Integridad y trazabilidad

- Validaciones de datos.
- Transacciones para pagos.
- Auditoría y conservación del historial.
- Bajas lógicas cuando corresponda.

## Usabilidad y disponibilidad

- Interfaz *responsive* (celular, tablet y computadora).
- Accesibilidad básica.
- Mensajes claros y manejo de errores.
- Compatibilidad con navegadores modernos.
- Respaldos con recuperación documentada.

## Archivos

- Almacenamiento adecuado de logos y documentos, sin sobrecargar las tablas principales.

## Sitio público

- Carga rápida en dispositivos móviles.
- Información de contacto visible y fácil de encontrar.
- Diseño claro, moderno y alineado con la identidad de cada escuela.
- Contenido editable separado de la estructura visual.
