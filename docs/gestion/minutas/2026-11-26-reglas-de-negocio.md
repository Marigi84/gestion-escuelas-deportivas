# Minuta – Reglas de negocio de cuotas y pagos – 26/11/2026

**Participantes:** Marina · **Escuela de referencia:** Rojas FC

## Decisiones

- Cuota de monto único, actualizada unas 3 veces al año, con historial de vigencias.
- Descuento por hermanos: mismo porcentaje para todos los hermanos, sin importar cuántos sean. No hay otros descuentos.
- Se cobra el mes en curso. Vencimiento el día 10 o el siguiente día hábil. Enero sin cuota (configurable).
- Recargo porcentual configurable sobre el saldo de la cuota con descuento; posibilidad de un segundo escalón; el administrador puede condonarlo.
- Pagos parciales y adelantados permitidos; se cancela primero la deuda más antigua; un aumento posterior deja la diferencia pendiente.
- Formas de pago: efectivo y transferencia verificada con comprobante. Una transferencia puede cubrir a varios hermanos y se reparte en un pago por alumno.
- Recibo interno en PDF, automático, uno por alumno, con saldo pendiente; enlace a ARCA si hace falta factura; anulaciones con historial.
- Datos obligatorios y opcionales de inscripción definidos; el administrador puede cargar alumnos directamente.

Detalle en [Reglas de negocio](../../03-reglas-de-negocio/index.md).

## Segunda parte

- Alta a mitad de mes con proporcional manual; las cuotas corren hasta la baja; la deuda se conserva; ajustes manuales con historial.
- Reactivación por el administrador, que decide si exige la deuda previa. Categoría = año de nacimiento.
- Solo administradores, con iguales permisos; escuelas independientes; profesores sin acceso en la v1.0.
- Autoregistro de escuelas con verificación de mail; baja con conservación de datos por 6 meses; superadministradora en modo soporte auditado.
- Portal: acceso por WhatsApp o mail, DNI como usuario y contraseña inicial con cambio obligatorio; el tutor solo consulta.
- Dashboard con deuda, cuotas adeudadas, deudores y recaudación ocultable; reportes de recaudación, tutores y altas/bajas.
- Se revisó el Trabajo Final de Rojas FC y se incorporaron sus mejoras pendientes al backlog.

## Próximos pasos

- Confirmar el día de vencimiento (el Trabajo Final indica el día 13).
- Decidir si se parte del código del Trabajo Final.
- Luego: casos de uso y modelo de datos.
