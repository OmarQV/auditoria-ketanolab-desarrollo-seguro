# 04 · Entregables para Ketanolab

Lo que le dejamos a Roger para que Ketanolab empiece a trabajar con seguridad. Cada documento lo redacta el responsable del dominio relacionado. Deben ser **cortos y aplicables** a un equipo pequeño (1 a 3 páginas por política).

| Código | Documento | Responsable | Estado |
|---|---|---|---|
| **M1** | **Manual de Desarrollo Seguro KL-MDS-01** (versión final; borrador en [docs](../docs/03_MANUAL_DESARROLLO_SEGURO_KETANOLAB.md)) | José Luis Quispe Vargas | 🟡 Borrador |
| P1 | Política general de seguridad de la información | José Luis Gutiérrez Morales | ⬜ |
| P2 | Política de control de accesos y contraseñas | Alex David Tola Julián | ⬜ |
| P5 | Política de respaldos | Jhamil Calixto Mamani Quea | ⬜ |
| P6 | Política de uso aceptable y trabajo remoto | Alex David Tola Julián | ⬜ |
| P7 | Política de proveedores y servicios en la nube | Alex David Tola Julián | ⬜ |
| P8 | Política de clasificación de información y datos personales | José Luis Gutiérrez Morales | ⬜ |
| PR1 | Procedimiento de respuesta a incidentes | Jhamil Calixto Mamani Quea | ⬜ |
| PR2 | Procedimiento de alta y baja de personal | Jhamil Calixto Mamani Quea | ⬜ |
| PR3 | Procedimiento de despliegue y entrega al cliente | José Luis Quispe Vargas | ⬜ |
| T1 | Plantilla de acuerdo de confidencialidad (NDA) | José Luis Gutiérrez Morales | ⬜ |
| T2 | Cláusulas tipo para contratos de desarrollo | José Luis Gutiérrez Morales | ⬜ |
| T3 | Checklist de seguridad por proyecto | José Luis Quispe Vargas | ⬜ |
| T4 | Registro de incidentes | Jhamil Calixto Mamani Quea | ⬜ |
| E3 | Inventario de activos de información | José Luis Gutiérrez Morales + Amílcar | ⬜ |
| E4 | Matriz de riesgos | Amílcar Quispe Santos | ⬜ |
| E5 | Declaración de Aplicabilidad (SoA) | Amílcar Quispe Santos | ⬜ |
| — | Hoja de ruta de 12 meses | Omar Quispe Vargas | ⬜ |

P3 y P4 del kit original quedan dentro del manual M1. Detalle de cada documento: [Propuesta §7](../docs/02_PROPUESTA_AUDITORIA_KETANOLAB.md).

## Nombres de archivos

`<código>_<NOMBRE>.md`, por ejemplo `P2_POLITICA_CONTROL_DE_ACCESOS.md`. Escribir en Markdown para poder unir todo en Word/PDF al final.

## Encabezado de cada política

```markdown
# <Código> · <Nombre>

| Ketanolab S.R.L. | |
|---|---|
| Versión | 1.0 (propuesta) |
| Base | ISO/IEC 27002:2022 controles X.XX |
| Aprobado por | Roger Dante Prado Lafuente *(al adoptarla)* |

## 1. Objetivo
## 2. Alcance
## 3. Reglas
## 4. Responsables
## 5. Revisión
```
