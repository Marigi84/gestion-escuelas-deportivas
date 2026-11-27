# Registro de decisiones de arquitectura (ADR)

Cada decisión técnica relevante se documenta con su contexto, la decisión, su estado y sus consecuencias, usando la [plantilla](plantilla.md).

| ADR | Título | Estado |
|---|---|---|
| [ADR-001](0001-sistema-multiescuela.md) | Sistema multiescuela con personalización y aislamiento | Aceptada |
| [ADR-002](0002-preinscripciones-con-aprobacion.md) | Preinscripciones sujetas a aprobación administrativa | Aceptada |
| [ADR-003](0003-pagos-confirmados-por-servidor.md) | Pagos definitivos solo con confirmación del servidor | Aceptada |
| [ADR-004](0004-plataforma-multidisciplina.md) | Plataforma multidisciplina con configuración por escuela | Aceptada |
| [ADR-005](0005-desarrollo-desde-cero.md) | Desarrollo desde cero reutilizando piezas del Trabajo Final | Aceptada |
| [ADR-006](0006-aislamiento-multiescuela.md) | Aislamiento multiescuela con columna de escuela y Row Level Security | Aceptada |
| [ADR-007](0007-stack-tecnologico.md) | Stack tecnológico | Aceptada |
| [ADR-008](0008-historial-y-auditoria.md) | Historial, bajas lógicas y auditoría | Aceptada |
| [ADR-009](0009-numeracion-de-recibos.md) | Numeración correlativa de recibos por escuela | Aceptada |

## ADR a formalizar

- Modo offline controlado (PWA + IndexedDB).
- Estrategia de rendimiento.
- Autenticación (sesiones, bloqueo por intentos, autenticación offline).
- Almacenamiento de archivos (logos, aptos médicos, recibos).
