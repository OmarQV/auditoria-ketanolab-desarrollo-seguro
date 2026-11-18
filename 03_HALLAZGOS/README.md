# 03 · Hallazgos

**Consolida:** Amílcar Quispe Santos · **Redacta cada ficha:** el auditor del dominio que lo encontró

## Para qué es esta carpeta

Un hallazgo es una diferencia entre lo que **debería** pasar (criterio: la norma) y lo que **pasa** (condición: lo que vimos). Aquí va una ficha por hallazgo. Las fichas pasan tal cual al informe final, por eso deben estar completas y respaldadas por un papel de trabajo.

## Nombres de archivos

`H-<dominio>-<n.º>_<titulo_corto>.md`, por ejemplo `H-D3-01_CERTIFICADO_TLS_DE_OTRO_DOMINIO.md`.
Cada auditor numera sus propios hallazgos, así nadie choca con otro. Al cierre, Amílcar arma el índice `INDICE_HALLAZGOS.md` ordenado por nivel de riesgo, y esa es la numeración del informe.

## Plantilla de hallazgo

```markdown
# H-D?-?? · <Título>

| Campo | Detalle |
|---|---|
| Dominio | D? |
| Auditor | |
| Papel de trabajo | PT-D?-0? |
| Nivel de riesgo | Alto / Medio / Bajo (según matriz de riesgos) |

**Criterio:** qué exige la norma (ISO/IEC 27002:2022 control X.XX, regla R-XX del manual).

**Condición:** qué encontramos, con hechos y fechas.

**Causa:** por qué ocurre.

**Efecto:** qué puede pasar si no se corrige (en lenguaje de negocio).

**Recomendación:** qué hacer, concreto y realista para una empresa pequeña.

**Evidencia:** EV-D?-0?

**Comentario de Ketanolab:** (respuesta de Roger al validar el hallazgo)
```
