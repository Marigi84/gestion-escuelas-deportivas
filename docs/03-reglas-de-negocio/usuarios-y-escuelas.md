# Usuarios y escuelas

## Usuarios de la escuela

**RN-37 – Administradores.** Del lado de la escuela solo usan el sistema los administradores. Los profesores no tienen acceso en la v1.0.

**RN-38 – Gestión de administradores.** Un administrador puede dar de alta y de baja a otros administradores de su misma escuela. Una escuela siempre debe tener al menos un administrador activo.

**RN-39 – Permisos iguales y trazabilidad.** Todos los administradores de una escuela tienen los mismos permisos. Por eso cada operación relevante (pagos, anulaciones, ajustes, condonaciones, bajas) registra qué administrador la hizo y cuándo.

## Escuelas

**RN-40 – Independencia.** Cada escuela se gestiona de forma independiente, con sus propios administradores, configuración y datos ([ADR-001](../adr/0001-sistema-multiescuela.md)).

**RN-41 – Autoregistro.** Una escuela nueva se registra sola en la plataforma y crea su primer administrador, que debe verificar su mail antes de operar.

**RN-42 – Baja de una escuela.** Cuando una escuela deja de usar el sistema, se desactiva y sus datos se conservan durante **6 meses como máximo**. En ese plazo puede exportarlos o reactivarse. Vencido el plazo, se eliminan los datos personales, en línea con la Ley 25.326 de protección de datos personales.

## Superadministrador

**RN-43 – Soporte.** El superadministrador gestiona escuelas y administradores. Para consultar los datos de una escuela (alumnos, pagos) entra en **modo soporte**, y cada acceso queda registrado con fecha, usuario y escuela.
