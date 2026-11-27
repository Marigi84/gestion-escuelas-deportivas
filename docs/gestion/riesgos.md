# Riesgos

| ID | Riesgo | Impacto | Mitigación |
|---|---|---|---|
| R-01 | Reglas de cuotas e intereses no definidas | Alto | Completar el capítulo de reglas de negocio antes del modelo de datos |
| R-02 | Exposición de datos de menores | Alto | Autorización en servidor, datos de ejemplo ficticios, acceso restringido a recibos |
| R-03 | Configurabilidad excesiva (multidisciplina) | Medio | Alcance acotado en [ADR-004](../adr/0004-plataforma-multidisciplina.md); vocabulario y campos propios quedan para después |
| R-04 | Conflictos de sincronización offline | Alto | Los pagos sin conexión quedan pendientes y solo los confirma el servidor (ADR-003); identificador por dispositivo y aviso de duplicados (RN-12) |
| R-05 | Carácter fiscal de los recibos | Medio | Validar con la escuela si son fiscales o internos |
| R-06 | Integración con Google Sheets no verificada | Bajo | Prueba de concepto de importación |
