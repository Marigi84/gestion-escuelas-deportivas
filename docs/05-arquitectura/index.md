# Arquitectura

!!! info "Propuesta"
    El stack se formalizará mediante ADR en la etapa de arquitectura.

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

- Estrategia de aislamiento multiescuela en la base de datos.
- Autenticación (incluida la autenticación offline).
- Sincronización y resolución de conflictos.
- Almacenamiento de archivos (logos, recibos).
- Despliegue y respaldos.
