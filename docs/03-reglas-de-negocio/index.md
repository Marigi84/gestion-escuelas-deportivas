# Reglas de negocio

Reglas que gobiernan el comportamiento del sistema. Cada regla tiene un identificador `RN-XX` que se referencia desde historias de usuario, casos de uso y pruebas.

Las reglas se definieron con la escuela piloto, **Rojas Fútbol Club**, el 26/11/2026. Siguiendo [ADR-004](../adr/0004-plataforma-multidisciplina.md), los valores concretos (porcentajes, días, meses) son **configurables por escuela**; los de Rojas FC figuran como valores iniciales.

Los términos del dominio están definidos en el [glosario](glosario.md).

## Capítulos

| Capítulo | Reglas |
|---|---|
| [Cuotas, descuentos y recargos](cuotas.md) | RN-01 a RN-10 |
| [Pagos](pagos.md) | RN-11 a RN-18 |
| [Recibos](recibos.md) | RN-19 a RN-24 |
| [Preinscripciones y datos de inscripción](preinscripciones.md) | RN-25 a RN-29 |
| [Alumnos: altas, bajas y categorías](alumnos.md) | RN-30 a RN-36 |
| [Usuarios y escuelas](usuarios-y-escuelas.md) | RN-37 a RN-43 |
| [Portal de familias](portal.md) | RN-44 a RN-48 |
| [Dashboard y reportes](reportes.md) | RN-49 a RN-54 |
| [Eventos e indumentaria](eventos-e-indumentaria.md) | RN-55 a RN-60 |

Las reglas RN-61 a RN-63 se agregaron después en sus capítulos: RN-61 y RN-62 en [cuotas](cuotas.md) y RN-63 en [pagos](pagos.md).

## Configuración por escuela

| Parámetro | Valor inicial Rojas FC | Regla |
|---|---|---|
| Monto de la cuota | Único para todos los alumnos | RN-01 |
| Frecuencia de actualización | Aprox. 3 veces al año | RN-02 |
| Apertura del mes | Manual por el administrador | RN-03, RN-61 |
| Vencimiento | Variable por mes; se sugiere el día 10 | RN-05 |
| Descuento por hermanos | Porcentaje fijo | RN-06 |
| Recargo por mora | Porcentaje sugerido, confirmado al abrir el mes; un escalón | RN-08, RN-09 |
| Formas de pago | Efectivo y transferencia | RN-11 |
| Categoría | Año de nacimiento, calculada | RN-36 |

## Ejemplo integrado

Con valores ilustrativos: cuota $30.000, descuento por hermanos 10 %, recargo 10 %.

1. Dos hermanos activos: cada cuota queda en $27.000 (RN-06).
2. La familia paga $40.000 por transferencia el día 8. El administrador verifica el comprobante y reparte $27.000 a un hermano y $13.000 al otro (RN-12, RN-16).
3. Se emiten dos recibos; el segundo informa un saldo de $14.000 (RN-19, RN-20).
4. Pasado el vencimiento, el saldo de $14.000 recibe un recargo de $1.400 (RN-08, RN-13).

## Antecedente

Varias reglas evolucionan las del sistema desarrollado como Trabajo Final Integrador para Rojas FC (ver [antecedentes](../01-vision-y-alcance/antecedentes.md)). Las principales diferencias son los pagos parciales, el pago familiar repartido entre hermanos, el descuento por hermanos y el importe proporcional al alta.
