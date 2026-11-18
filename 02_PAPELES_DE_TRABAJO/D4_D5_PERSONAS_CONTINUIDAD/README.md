# D4 y D5 · Personas, terceros, continuidad e incidentes

**Responsable:** Jhamil Calixto Mamani Quea

## Por qué este dominio

En una empresa pequeña con colaboradores por proyecto y *freelancers*, el riesgo está en las personas: quién entra, qué firma, qué se lleva cuando sale. Y si algo falla (laptop robada, servidor borrado, cuenta perdida), la empresa sobrevive solo si tiene respaldos probados y sabe cómo responder.

## Controles a evaluar (ISO/IEC 27002:2022)

| Control | Pregunta de auditoría | Papel de trabajo |
|---|---|---|
| 6.1 · 6.2 Contratación | ¿Qué se verifica y qué se firma al incorporar a alguien? | PT-D4-01 |
| 6.6 Confidencialidad | ¿Hay NDA con colaboradores y clientes? | PT-D4-01 |
| 6.3 Formación | ¿El equipo recibió alguna capacitación en seguridad? | PT-D4-01 |
| 6.5 · 5.18 Cese | ¿Se retiran los accesos cuando alguien sale? (pedir lista de salidas de los últimos 12 meses) | PT-D4-01 |
| 6.7 · 8.1 Trabajo remoto y equipos | ¿Laptops personales? ¿Cifrado de disco? ¿Bloqueo de pantalla? | PT-D4-02 |
| 5.19–5.22 Proveedores | ¿Hay acuerdos con *freelancers* y proveedores? ¿Qué acceso tienen? | PT-D4-02 |
| 8.13 · 8.14 Respaldos | ¿Qué se respalda, dónde, cada cuánto? ¿Se probó restaurar? | PT-D5-01 |
| 5.29 · 5.30 Continuidad | ¿Qué pasa si cae el servidor o se pierde la cuenta de GitHub o Google Play? | PT-D5-01 |
| 5.24–5.28 Incidentes | ¿Hubo incidentes? ¿Cómo se atendieron? ¿Hay registro? | PT-D5-02 |

## Entregables de mejora a tu cargo (en `04_ENTREGABLES/`)

- P5 · Política de respaldos
- PR1 · Procedimiento de respuesta a incidentes
- PR2 · Procedimiento de alta y baja de personal
- T4 · Registro de incidentes

## Archivos esperados

- [ ] `PT-D4-01_PERSONAL_Y_CONFIDENCIALIDAD.md`
- [ ] `PT-D4-02_TRABAJO_REMOTO_Y_PROVEEDORES.md`
- [ ] `PT-D5-01_RESPALDOS_Y_CONTINUIDAD.md`
- [ ] `PT-D5-02_INCIDENTES.md`
- [ ] `evidencias/`

Referencias: [Propuesta §4.1](../../docs/02_PROPUESTA_AUDITORIA_KETANOLAB.md) · [Manual §7.8 y §13](../../docs/03_MANUAL_DESARROLLO_SEGURO_KETANOLAB.md)
