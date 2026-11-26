# Gestión de Escuelas Deportivas

Plataforma web para centralizar la administración de escuelas deportivas: alumnos, tutores, categorías, preinscripciones, cuotas, pagos, recibos y reportes, con un sitio público y un portal para familias.

El sistema es **multiescuela** y **multidisciplina**: cada escuela configura su deporte, sus categorías, su identidad visual y sus reglas administrativas. La primera implementación es **Rojas Fútbol Club**.

> Estado: **etapa de análisis y diseño**. Todavía no hay código; el repositorio contiene la documentación del proyecto.

## Documentación

La documentación se mantiene como código (*docs-as-code*) en [`docs/`](docs/index.md) y se publica con MkDocs Material.

| Sección | Contenido |
|---|---|
| [Visión y alcance](docs/01-vision-y-alcance/vision.md) | Objetivo, alcance de la v1.0 y backlog futuro |
| [Requisitos](docs/02-requisitos/requisitos-funcionales.md) | Requisitos funcionales, no funcionales e historias de usuario |
| [Reglas de negocio](docs/03-reglas-de-negocio/index.md) | Próximo capítulo a desarrollar |
| [Arquitectura](docs/05-arquitectura/index.md) | Stack propuesto y diagramas |
| [ADR](docs/adr/index.md) | Registro de decisiones de arquitectura |
| [Sitio público](docs/06-sitio-publico/rojas-fc.md) | Relevamiento y diseño del sitio de Rojas FC |
| [Gestión](docs/gestion/roadmap.md) | Roadmap, minutas, riesgos y flujo de trabajo |

## Stack propuesto

- **Frontend:** React, TypeScript, Vite (PWA)
- **Backend:** Java, Spring Boot, JPA/Hibernate, API REST
- **Base de datos:** PostgreSQL

La selección definitiva se formaliza en la etapa de arquitectura (ver [ADR](docs/adr/index.md)).

## Estructura del repositorio

```
docs/        Documentación del proyecto (MkDocs)
frontend/    Aplicación web (pendiente)
backend/     API (pendiente)
.github/     Plantillas de issues y PR, workflows de CI
```

## Gestión del proyecto

El trabajo se planifica en GitHub Projects con issues, hitos e iteraciones. Ver [flujo de trabajo](docs/gestion/flujo-de-trabajo.md) y [CONTRIBUTING.md](CONTRIBUTING.md).

## Ver la documentación localmente

```bash
pip install -r requirements-docs.txt
mkdocs serve
```

## Autora

Marina ([@Marigi84](https://github.com/Marigi84))
