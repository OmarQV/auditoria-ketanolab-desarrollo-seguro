# D1 · Gobierno, legal y políticas

**Responsable:** José Luis Gutiérrez Morales

## Por qué este dominio

Ketanolab no tiene ninguna política documentada. Antes de evaluar controles técnicos hay que saber quién decide, qué activos existen, de quién es el código y qué leyes aplican. Sin esto, el resto de la auditoría no tiene base.

## Controles a evaluar (ISO/IEC 27001:2022 cláusulas 4–10 e ISO/IEC 27002:2022)

| Control | Pregunta de auditoría | Papel de trabajo |
|---|---|---|
| Cl. 4–5 · 5.1 Políticas | ¿Existe alguna política o regla escrita de seguridad? ¿La dirección asumió compromisos? | PT-D1-01 |
| 5.2 Roles y responsabilidades | ¿Quién es responsable de la seguridad, de las cuentas, de los respaldos? | PT-D1-01 |
| 5.9 Inventario de activos | ¿Existe una lista de cuentas, dominios, servidores, repositorios y datos, con dueño? | PT-D1-02 |
| 5.12 Clasificación | ¿Se distingue información pública, interna y confidencial de clientes? | PT-D1-02 |
| 5.31 Requisitos legales | ¿Conocen las leyes que aplican (Ley 164, D.S. 1793, Ley 1322, CPE)? | PT-D1-03 |
| 5.32 Propiedad intelectual | ¿Los contratos dicen de quién es el código? ¿Se controlan las licencias (GPL en NuSimi)? | PT-D1-03 |
| 5.34 Privacidad | ¿Cómo se manejan los datos personales de usuarios y los *datasets* de imágenes? | PT-D1-04 |

## Entregables de mejora a tu cargo (en `04_ENTREGABLES/`)

- P1 · Política general de seguridad de la información
- P8 · Política de clasificación y manejo de información de clientes y datos personales
- T1 · Plantilla de acuerdo de confidencialidad (NDA)
- T2 · Cláusulas tipo para contratos de desarrollo
- E3 · Inventario de activos de información (en coordinación con Amílcar)

## Archivos esperados

- [ ] `PT-D1-01_POLITICAS_Y_ROLES.md`
- [ ] `PT-D1-02_INVENTARIO_DE_ACTIVOS.md` (+ `INVENTARIO_ACTIVOS.xlsx`)
- [ ] `PT-D1-03_LEGAL_Y_PROPIEDAD_INTELECTUAL.md`
- [ ] `PT-D1-04_DATOS_PERSONALES.md`
- [ ] `evidencias/`

Referencias: [Propuesta §4.1](../../docs/02_PROPUESTA_AUDITORIA_KETANOLAB.md) · [Contexto §7 (marco legal)](../../docs/01_CONTEXTO_KETANOLAB.md)
