# Arquitectura

!!! info "Propuesta"
    El stack está propuesto en [ADR-007](../adr/0007-stack-tecnologico.md) y el aislamiento multiescuela en [ADR-006](../adr/0006-aislamiento-multiescuela.md).

## Stack propuesto

| Capa | Tecnología |
|---|---|
| Frontend | React, TypeScript, Vite, PWA (IndexedDB para offline) |
| Backend | Java, Spring Boot, JPA/Hibernate |
| API | REST |
| Base de datos | PostgreSQL |
| Integraciones | Google Forms / Google Sheets (preinscripción) |

## Diagrama de contexto (C4 – nivel 1)

```mermaid
flowchart LR
    familia([Familia interesada])
    tutor([Tutor])
    admin([Administrador de escuela])
    super([Superadministrador])

    sistema[Plataforma de gestión<br/>de escuelas deportivas]
    gforms[(Google Forms /<br/>Google Sheets)]

    familia -->|Consulta sitio público| sistema
    familia -->|Completa preinscripción| gforms
    gforms -->|Importación| sistema
    tutor -->|Consulta cuotas y recibos| sistema
    admin -->|Gestiona alumnos, cuotas y pagos| sistema
    super -->|Administra escuelas| sistema
```

## Temas pendientes

- Autenticación (incluida la autenticación offline).
- Sincronización y resolución de conflictos.
- Almacenamiento de archivos (logos, recibos).
- Despliegue y respaldos.
