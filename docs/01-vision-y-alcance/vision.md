# Visión del producto

## Objetivo

Desarrollar una aplicación web **rápida, segura y escalable** para centralizar la administración de escuelas deportivas.

## Visión

- **Rojas Fútbol Club** es la primera implementación.
- Luego se incorporarán las otras escuelas del mismo propietario.
- Más adelante, la plataforma podrá ofrecerse a instituciones externas.
- El producto es **general y personalizable desde su origen**: cada escuela configura su disciplina, categorías, vocabulario, identidad visual y reglas administrativas.

## Problema que resuelve

Las escuelas deportivas suelen administrar alumnos, cuotas y pagos con planillas sueltas, mensajes de WhatsApp y recibos manuales. Eso provoca:

- información dispersa y duplicada;
- dificultad para conocer la deuda real de cada familia;
- falta de trazabilidad de pagos y recibos;
- poca visibilidad institucional para atraer nuevos alumnos.

## Usuarios

| Rol | Necesidad principal |
|---|---|
| Familias interesadas | Conocer la propuesta, categorías y horarios, y preinscribirse |
| Tutores / familias | Consultar la situación de cuotas, deuda, pagos y recibos de sus hijos |
| Administrador de escuela | Gestionar alumnos, preinscripciones, cuotas, pagos y reportes |
| Superadministrador | Administrar la plataforma y las escuelas |

## Principios

1. **Multiescuela con aislamiento:** cada escuela ve solo su información ([ADR-001](../adr/0001-sistema-multiescuela.md)).
2. **Multidisciplina:** el núcleo administrativo no depende del deporte ([ADR-004](../adr/0004-plataforma-multidisciplina.md)).
3. **Integridad primero:** los pagos definitivos se confirman en el servidor ([ADR-003](../adr/0003-pagos-confirmados-por-servidor.md)).
4. **Protección de datos de menores** en todo el diseño.
