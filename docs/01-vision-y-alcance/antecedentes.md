# Antecedentes

Este proyecto parte de dos trabajos previos para Rojas Fútbol Club.

## Sitio institucional

[rojas-fc-landing](https://github.com/Marigi84/rojas-fc-landing): landing page institucional desarrollada con React, Vite y TypeScript. Su relevamiento se resume en [Sitio público](../06-sitio-publico/rojas-fc.md).

## Sistema de gestión (Trabajo Final Integrador)

[rojas-fc-gestion](https://github.com/Marigi84/rojas-fc-gestion): sistema web de gestión administrativa desarrollado como Trabajo Final Integrador de la Tecnicatura Universitaria en Programación (UTN).

- **Stack:** React + TypeScript + Vite, Spring Boot + JPA, MySQL, JWT.
- **Implementado y probado:** autenticación y roles, alumnos, responsables y categorías por año de nacimiento, cuotas con generación automática, interés y morosidad, pagos y recibos con anulación, dashboard y portal del responsable.
- **Quedó fuera:** preinscripción en línea, eventos e indumentaria, reportes y exportación, recibos por WhatsApp y en PDF, funcionamiento sin conexión.

## Qué cambia en este proyecto

| Tema | Trabajo Final | Este proyecto |
|---|---|---|
| Escuelas | Una sola (Rojas FC) | Multiescuela y multidisciplina ([ADR-001](../adr/0001-sistema-multiescuela.md), [ADR-004](../adr/0004-plataforma-multidisciplina.md)) |
| Pagos | Solo cuota completa, un pago por cuota | Pagos parciales, adelantados y pago familiar repartido entre hermanos |
| Descuentos | No había | Descuento por hermanos |
| Alta a mitad de mes | Empieza a pagar el mes siguiente | Proporcional cargado por el administrador |
| Recargo | Un único interés | Hasta dos escalones, con condonación |
| Base de datos | MySQL | PostgreSQL (propuesto, a formalizar en ADR) |
