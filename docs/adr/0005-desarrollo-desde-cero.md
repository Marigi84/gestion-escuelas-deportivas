# ADR-005: Desarrollo desde cero reutilizando piezas del Trabajo Final

- **Estado:** Aceptada
- **Fecha:** 2026-11-26

## Contexto

Existe un sistema de gestión para Rojas FC desarrollado como Trabajo Final Integrador ([rojas-fc-gestion](https://github.com/Marigi84/rojas-fc-gestion)), implementado, probado y en línea, con el mismo stack propuesto salvo la base de datos (MySQL). Ese sistema fue diseñado para una sola escuela y con reglas de pago más simples (ver [antecedentes](../01-vision-y-alcance/antecedentes.md)).

## Decisión

El sistema nuevo se desarrolla **desde cero**. Se reutilizan del Trabajo Final las piezas que encajen con el nuevo diseño (por ejemplo, componentes de interfaz, validaciones, pruebas o partes del modelo), revisándolas y adaptándolas.

## Alternativas consideradas

- **Evolucionar el código del Trabajo Final:** más rápido al principio, pero obliga a rehacer el modelo para multiescuela, multidisciplina, pagos parciales y pago familiar, y arrastra decisiones tomadas para otro alcance.

## Consecuencias

- El modelo de datos y la arquitectura se diseñan para el alcance nuevo sin condicionamientos.
- Lleva más tiempo hasta tener un sistema funcionando.
- El Trabajo Final sirve como referencia de reglas, pantallas y casos de prueba.
