# 05 · Informe final

**Responsable:** Omar Quispe Vargas (auditor líder)

## Para qué es esta carpeta

Aquí se arma el resultado que se presenta al docente y se entrega a Roger. Se construye **al final**, a partir de los papeles de trabajo (`02_`), los hallazgos (`03_`) y los entregables (`04_`). Nadie más edita esta carpeta; si quieres un cambio, avísale a Omar.

## Qué va aquí

| Archivo | Contenido | Estado |
|---|---|---|
| `INFORME_AUDITORIA.md` | 1. Resumen ejecutivo · 2. Antecedentes · 3. Objetivos y alcance · 4. Criterios · 5. Metodología · 6. Resultados y madurez por dominio · 7. Hallazgos · 8. Conclusión · 9. Recomendaciones y hoja de ruta · Anexos | ⬜ |
| `CARTA_DE_GERENCIA.md` | 1–2 páginas para Roger, sin tecnicismos | ⬜ |
| `PRESENTACION.pptx` o `.pdf` | Diapositivas para el docente | ⬜ |
| `INFORME_AUDITORIA.docx` / `.pdf` | Versión final unida y con formato | ⬜ |

## Cómo se une todo en Word/PDF

Los documentos en Markdown se pueden unir automáticamente con [Pandoc](https://pandoc.org), por ejemplo:

```bash
pandoc INFORME_AUDITORIA.md ../03_HALLAZGOS/H-*.md ../04_ENTREGABLES/*.md -o INFORME_AUDITORIA.docx --toc
```

Luego se ajustan la carátula y el formato en Word y se exporta a PDF.
