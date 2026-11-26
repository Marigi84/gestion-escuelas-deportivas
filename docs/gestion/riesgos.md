# Riesgos

| ID | Riesgo | Impacto | Mitigación |
|---|---|---|---|
| R-01 | Reglas de cuotas e intereses no definidas | Alto | Completar el capítulo de reglas de negocio antes del modelo de datos |
| R-02 | Exposición de datos de menores | Alto | Autorización en servidor, datos de ejemplo ficticios, acceso restringido a recibos |
| R-03 | Configurabilidad excesiva (multidisciplina) | Medio | Acotar qué es configurable en la v1.0 |
| R-04 | Conflictos de sincronización offline | Medio | Offline limitado a datos no críticos; pagos solo online (ADR-003) |
| R-05 | Carácter fiscal de los recibos | Medio | Validar con la escuela si son fiscales o internos |
| R-06 | Integración con Google Sheets no verificada | Bajo | Prueba de concepto de importación |
