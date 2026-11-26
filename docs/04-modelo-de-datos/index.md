# Modelo de datos

!!! info "Pendiente"
    Se desarrollará después de validar las [reglas de negocio](../03-reglas-de-negocio/index.md): primero el modelo conceptual y luego el relacional.

## Entidades identificadas

```mermaid
erDiagram
    ESCUELA ||--o{ CATEGORIA : define
    ESCUELA ||--o{ DISCIPLINA_ESCUELA : dicta
    ESCUELA ||--o{ PREINSCRIPCION : recibe
    ESCUELA ||--o{ ALUMNO : tiene
    CATEGORIA ||--o{ ALUMNO : agrupa
    ALUMNO }o--o{ TUTOR : "vinculado a"
    ALUMNO ||--o{ CUOTA : genera
    CUOTA }o--o{ PAGO : "imputada en"
    PAGO ||--|| RECIBO : emite
    USUARIO }o--o{ ESCUELA : administra
    TUTOR ||--o| USUARIO : accede
```

Este diagrama es preliminar y solo muestra relaciones principales.
