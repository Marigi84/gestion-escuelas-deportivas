# Preinscripciones y datos de inscripción

**RN-25 – Circuito de preinscripción.** El administrador envía el formulario de inscripción a la familia por WhatsApp o mail. El tutor lo completa y la respuesta ingresa al sistema como **preinscripción**, nunca como alumno activo ([ADR-002](../adr/0002-preinscripciones-con-aprobacion.md)).

**RN-26 – Datos requeridos.**

| Persona | Obligatorios | Opcionales |
|---|---|---|
| Alumno | Nombre y apellido, DNI, fecha de nacimiento, domicilio | Escuela a la que asiste, alergias o condiciones médicas, apto médico |
| Tutor | Nombre, apellido, DNI, teléfono/WhatsApp | Mail, contacto de emergencia |

Los datos de salud (alergias, condiciones médicas y apto médico) son sensibles: solo los ven los administradores de la escuela y no aparecen en listados ni exportaciones. El apto médico es opcional y se guarda como archivo (PDF o imagen), sin control de vencimiento. Los campos propios por escuela quedan para una versión futura ([ADR-004](../adr/0004-plataforma-multidisciplina.md)).

**RN-27 – Aprobación.** Una preinscripción está **pendiente**, **aprobada** o **rechazada**. Como los campos obligatorios se exigen en el formulario, no hay estado "incompleta". El administrador la revisa: si la aprueba, se crea el alumno y se crea o vincula el tutor; si la rechaza, no genera alumno.

**RN-28 – Carga directa.** El administrador también puede dar de alta un alumno cargando los datos él mismo en el momento, sin pasar por el formulario.

**RN-29 – Duplicados.** El DNI identifica al alumno y al tutor dentro de la escuela. Si ya existe un tutor con ese DNI, se vincula en lugar de crear uno nuevo; si ya existe el alumno, el sistema lo advierte antes de aprobar.
