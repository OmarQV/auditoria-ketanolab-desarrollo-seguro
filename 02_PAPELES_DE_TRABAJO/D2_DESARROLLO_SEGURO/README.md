# D2 · Desarrollo seguro

**Responsable:** José Luis Quispe Vargas

## Por qué este dominio

Es el corazón de la auditoría: Ketanolab vende software. Aquí se comprueba si el código se escribe, revisa, prueba y publica de forma segura. Los resultados de este dominio alimentan directamente el **Manual de Desarrollo Seguro**, del que también estás a cargo de la versión final.

## Controles a evaluar (ISO/IEC 27002:2022)

| Control | Pregunta de auditoría | Papel de trabajo |
|---|---|---|
| 8.25 Ciclo de vida seguro | ¿Hay un proceso definido de desarrollo? ¿La seguridad aparece en alguna fase? | PT-D2-01 |
| 8.26 · 8.27 Requisitos y arquitectura | ¿Se definen requisitos de seguridad? ¿Se analiza el diseño (modelo de amenazas)? | PT-D2-01 |
| 8.4 Acceso al código fuente | ¿Dónde está el código? ¿Cuentas personales u organización? ¿Quién tiene acceso? | PT-D2-02 |
| 8.28 Codificación segura | ¿Hay secretos en el código (`local.properties`, `.env`)? ¿Validación de entradas, consultas parametrizadas? | PT-D2-02 |
| 8.8 Dependencias | ¿Se revisan las librerías? ¿Hay alertas de vulnerabilidades? | PT-D2-03 |
| 8.29 Pruebas de seguridad | ¿Se hace algún análisis estático, dinámico o de la app móvil? | PT-D2-03 |
| 8.31 · 8.33 Ambientes y datos de prueba | ¿Desarrollo, pruebas y producción están separados? ¿Se usan datos reales en pruebas? | PT-D2-04 |
| 8.32 Gestión de cambios | ¿Hay revisión de código, ramas protegidas, despliegue registrado? | PT-D2-04 |

## Muestra a revisar

| Proyecto | Cómo | Nota de independencia |
|---|---|---|
| NuSimi (repositorio público) | Revisión del repositorio con el checklist del manual §11 | Sin restricción |
| App para ferias | Entrevista + revisión guiada | Solo si no participaste en su desarrollo |
| Monitoreo de obras | Entrevista + revisión guiada | Solo si no participaste en su desarrollo |

## Entregables de mejora a tu cargo (en `04_ENTREGABLES/`)

- M1 · **Manual de Desarrollo Seguro KL-MDS-01**, versión final (borrador en [docs/03_MANUAL](../../docs/03_MANUAL_DESARROLLO_SEGURO_KETANOLAB.md))
- PR3 · Procedimiento de despliegue y entrega al cliente
- T3 · Checklist de seguridad por proyecto

## Archivos esperados

- [ ] `PT-D2-01_PROCESO_DE_DESARROLLO.md`
- [ ] `PT-D2-02_REPOSITORIOS_Y_CODIGO.md`
- [ ] `PT-D2-03_DEPENDENCIAS_Y_PRUEBAS.md`
- [ ] `PT-D2-04_AMBIENTES_Y_CAMBIOS.md`
- [ ] `evidencias/`

Referencias: [Manual](../../docs/03_MANUAL_DESARROLLO_SEGURO_KETANOLAB.md) · [Contexto §5 (O-05, O-06)](../../docs/01_CONTEXTO_KETANOLAB.md)
