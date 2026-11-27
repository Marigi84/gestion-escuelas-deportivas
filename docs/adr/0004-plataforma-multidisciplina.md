# ADR-004: Plataforma multidisciplina con configuración por escuela

- **Estado:** Aceptada
- **Fecha:** 2026-11-26

## Contexto

El proyecto nació como sistema para escuelas de fútbol. Se decidió ampliarlo a **cualquier escuela deportiva** (fútbol, hockey, natación, básquet, artes marciales, etc.), de modo que cada una pueda personalizar su especialización.

## Decisión

- El núcleo administrativo (alumnos, tutores, cuotas, pagos, recibos, reportes) es **independiente de la disciplina**.
- Cada escuela configura:
    - una o varias **disciplinas**;
    - sus **categorías** (por edad, nivel, género o turno);
    - el **vocabulario** de la interfaz (por ejemplo, "profe" o "entrenador", "categoría" o "nivel", "alumno" o "jugador");
    - **campos adicionales** del alumno (por ejemplo, posición, cinturón, talle).
- El sitio público es una **plantilla** que cada escuela completa con su contenido.
- Las funcionalidades específicas de un deporte (estadísticas, torneos) se agregan como **módulos opcionales**.
- Rojas Fútbol Club es la primera escuela, configurada con la disciplina fútbol.

## Alternativas consideradas

- **Sistema solo para fútbol:** más simple al principio, pero obliga a reescribir para otras disciplinas.
- **Una versión por deporte:** multiplica el mantenimiento.

## Consecuencias

- Mayor alcance de mercado y reutilización.
- Diseño más cuidadoso del modelo de datos (categorías y campos configurables).
- Hay que limitar la configurabilidad para no complicar la v1.0.

## Alcance en la v1.0

Decidido el 2026-11-26:

- **Configurable:** nombre, logo, colores, contacto, disciplina, categorías con días, horarios y lugar, monto de la cuota, vencimiento sugerido, descuento por hermanos, recargos, meses sin cuota y formas de pago.
- **Criterio de categoría:** por año de nacimiento (calculada) o asignada a mano ([RN-36](../03-reglas-de-negocio/alumnos.md)).
- **Para una versión futura:** vocabulario propio y campos adicionales del alumno.
