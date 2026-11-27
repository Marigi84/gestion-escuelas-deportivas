# Glosario

Términos del dominio, con el sentido preciso que tienen en las reglas y en el modelo de datos.

| Término | Definición | Reglas |
|---|---|---|
| **Escuela** | Institución que usa la plataforma, con su configuración, sus administradores y sus datos aislados del resto. | RN-40, ADR-001 |
| **Disciplina** | Deporte que dicta una escuela (fútbol, hockey, natación, etc.). | ADR-004 |
| **Categoría** | Grupo de alumnos de una escuela, con días, horarios y lugar. Se calcula por año de nacimiento o se asigna a mano. | RN-36 |
| **Alumno** | Persona inscripta en una escuela. Pertenece a una sola escuela. | RN-27, RN-28 |
| **Tutor** | Persona adulta vinculada a uno o más alumnos, con una sola cuenta para toda la plataforma. | RN-29, RN-45 |
| **Hermanos** | Alumnos de una misma escuela que el administrador vincula como tales; habilitan el descuento. | RN-06 |
| **Preinscripción** | Solicitud de ingreso recibida desde el formulario. Está pendiente, aprobada o rechazada, y nunca es un alumno por sí misma. | RN-25, RN-27 |
| **Permanencia** | Período entre un alta y una baja de un alumno. Un alumno puede tener varias. | RN-35 |
| **Apertura del mes** | Acción del administrador que confirma monto, vencimiento y recargo de un mes y genera sus cuotas. | RN-03 |
| **Cuota** | Importe mensual que debe un alumno por un mes abierto. Guarda el monto y el descuento vigentes al generarse. | RN-02, RN-03, RN-06 |
| **Recargo** | Importe porcentual que se suma al saldo impago de una cuota vencida. Hasta dos escalones. | RN-08, RN-09 |
| **Condonación** | Decisión del administrador de no aplicar un recargo, con motivo. | RN-10 |
| **Ajuste** | Modificación manual del importe de una cuota o deuda, con valor anterior, nuevo y motivo. | RN-33 |
| **Saldo** | Lo que falta pagar de una cuota o recargo. | RN-13, RN-20 |
| **Deuda** | Suma de saldos impagos de un alumno. | RN-32, RN-49 |
| **Saldo a favor** | Importe pagado por adelantado que todavía no se imputó a ninguna cuota. | RN-15 |
| **Operación** | Ingreso de dinero registrado una vez (un efectivo o una transferencia), que puede repartirse entre hermanos. | RN-16 |
| **Pago** | Parte de una operación asignada a un alumno. Cada pago genera un recibo. | RN-16, RN-19 |
| **Imputación** | Aplicación de un pago a las deudas del alumno, empezando por la más antigua. | RN-14 |
| **Anulación** | Cambio de estado de un pago o recibo a anulado, con motivo, usuario y fecha. Nunca se borra. | RN-18, RN-23 |
| **Recibo** | Comprobante interno, no fiscal, numerado por escuela y emitido a nombre del alumno. | RN-19 a RN-23 |
| **Administrador** | Usuario con permisos sobre una o más escuelas. Todos los administradores de una escuela tienen los mismos permisos. | RN-37 a RN-39 |
| **Superadministrador** | Responsable de la plataforma. Gestiona escuelas y administradores. | RN-43 |
| **Modo soporte** | Acceso auditado del superadministrador a los datos de una escuela. | RN-43 |
| **Anonimización** | Reemplazo de los datos personales por valores neutros, conservando importes y numeraciones. | RN-42, ADR-008 |
