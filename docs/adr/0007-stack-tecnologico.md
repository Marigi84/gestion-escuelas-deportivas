# ADR-007: Stack tecnológico

- **Estado:** Propuesta
- **Fecha:** 2026-11-26

## Contexto

La minuta inicial propuso React con TypeScript, Spring Boot y PostgreSQL. El sistema anterior para Rojas FC usaba el mismo stack con MySQL ([antecedentes](../01-vision-y-alcance/antecedentes.md)). El modelo de datos necesita una base definida antes de diseñarse.

## Decisión

| Capa | Tecnología |
|---|---|
| Frontend | React + TypeScript + Vite, PWA |
| Backend | Java (versión LTS vigente) + Spring Boot + Spring Data JPA |
| API | REST con JSON, documentada con OpenAPI |
| Base de datos | PostgreSQL |
| Migraciones | Flyway, versionadas en el repositorio |

PostgreSQL se elige sobre MySQL por:

- *Row Level Security* nativo para el aislamiento multiescuela ([ADR-006](0006-aislamiento-multiescuela.md));
- tipo `jsonb` para la auditoría y configuraciones flexibles;
- restricciones más expresivas (`CHECK`, índices parciales) para reglas como "una escuela siempre tiene un administrador activo".

## Alternativas consideradas

- **MySQL:** conocido por el sistema anterior, pero sin RLS y con menos soporte para restricciones e índices parciales.
- **Node.js en el backend:** un solo lenguaje en todo el proyecto, pero se pierde la experiencia previa en Spring Boot.

## Consecuencias

- El esquema se crea solo con migraciones Flyway; nunca con generación automática de Hibernate.
- Lo que se reutilice del sistema anterior hay que adaptarlo de MySQL a PostgreSQL.
