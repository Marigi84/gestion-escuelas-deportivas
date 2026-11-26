# Preinscripciones y datos de inscripción

**RN-25 – Circuito de preinscripción.** El administrador envía el formulario de inscripción a la familia por WhatsApp o mail. El tutor lo completa y la respuesta ingresa al sistema como **preinscripción**, nunca como alumno activo ([ADR-002](../adr/0002-preinscripciones-con-aprobacion.md)).

**RN-26 – Datos requeridos.**

| Persona | Obligatorios | Opcionales |
|---|---|---|
| Alumno | Nombre y apellido, DNI, fecha de nacimiento, domicilio | Escuela a la que asiste, alergias o condiciones médicas, apto médico |
| Tutor | Nombre, apellido, DNI, teléfono/WhatsApp | Mail, contacto de emergencia |

Cada escuela puede agregar campos propios ([ADR-004](../adr/0004-plataforma-multidisciplina.md)). Los datos de salud se tratan como sensibles.

**RN-27 – Aprobación.** El administrador revisa la preinscripción. Si la aprueba, se crea el alumno y se crea o vincula el tutor. Si la rechaza, se descarta y no genera alumno.

**RN-28 – Carga directa.** El administrador también puede dar de alta un alumno cargando los datos él mismo en el momento, sin pasar por el formulario.

**RN-29 – Duplicados.** El DNI identifica al alumno y al tutor dentro de la escuela. Si ya existe un tutor con ese DNI, se vincula en lugar de crear uno nuevo; si ya existe el alumno, el sistema lo advierte antes de aprobar.
