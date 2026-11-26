# Cómo contribuir

## Flujo de trabajo

1. Todo trabajo parte de un **issue** del tablero (historia, tarea, documentación o bug).
2. Se crea una rama desde `main` con el formato `tipo/descripcion-corta`, por ejemplo `docs/reglas-de-cuotas` o `feat/alta-de-alumnos`.
3. Los commits siguen [Conventional Commits](https://www.conventionalcommits.org/es/):
   - `docs:` documentación
   - `feat:` nueva funcionalidad
   - `fix:` corrección
   - `refactor:`, `test:`, `chore:`, `ci:`
4. Se abre un **Pull Request** que referencia el issue (`Closes #N`) y completa la plantilla.
5. Se fusiona a `main` cuando pasa la revisión y los checks.

## Decisiones de arquitectura

Toda decisión técnica relevante se registra como ADR en [`docs/adr/`](docs/adr/index.md) usando la [plantilla](docs/adr/plantilla.md).

## Datos personales

El sistema maneja datos de menores. **Nunca** se suben al repositorio datos reales de alumnos, tutores o pagos. Los datos de ejemplo deben ser ficticios.
