# ADR-006: Aislamiento multiescuela con columna de escuela y Row Level Security

- **Estado:** Propuesta
- **Fecha:** 2026-11-26

## Contexto

[ADR-001](0001-sistema-multiescuela.md) exige que cada escuela vea solo su información y que la separación se verifique en el servidor. Además:

- un usuario puede administrar más de una escuela ([RN-40](../03-reglas-de-negocio/usuarios-y-escuelas.md));
- un tutor tiene una sola cuenta para toda la plataforma y puede tener hijos en varias escuelas ([RN-45](../03-reglas-de-negocio/portal.md));
- el superadministrador accede a una escuela solo en modo soporte auditado ([RN-43](../03-reglas-de-negocio/usuarios-y-escuelas.md)).

El volumen esperado es bajo (decenas de escuelas, miles de alumnos).

## Decisión

- **Una base y un esquema compartidos.** Cada tabla con datos de una escuela tiene la columna `escuela_id` (no nula, con clave foránea e índice).
- **Entidades globales:** escuela, usuario y persona (tutor). La relación con cada escuela se guarda en tablas de vínculo: usuario–escuela (permisos de administrador) y tutor–alumno (el alumno ya pertenece a una escuela).
- **Doble barrera:**
    1. En la aplicación, cada consulta filtra por la escuela activa de la sesión, que se valida contra los permisos del usuario.
    2. En PostgreSQL, *Row Level Security* sobre las tablas con `escuela_id`, usando la escuela activa que la aplicación fija en cada transacción.
- El modo soporte del superadministrador fija la escuela activa como cualquier otra sesión y registra el acceso.

## Alternativas consideradas

- **Esquema por escuela:** aísla mejor, pero complica las migraciones, las consultas de un tutor con hijos en varias escuelas y los reportes de plataforma.
- **Base por escuela:** el aislamiento más fuerte, con un costo de operación desproporcionado para el volumen previsto.
- **Solo filtro en la aplicación:** más simple, pero un olvido en una consulta expone datos de menores.

## Consecuencias

- Las claves únicas de negocio incluyen la escuela (por ejemplo, DNI del alumno por escuela, número de recibo por escuela).
- Se necesitan pruebas automáticas de aislamiento: un usuario de la escuela A nunca obtiene datos de la escuela B.
- RLS agrega una configuración por transacción; si complicara el desarrollo, puede postergarse sin cambiar el modelo, porque la columna `escuela_id` ya está.
