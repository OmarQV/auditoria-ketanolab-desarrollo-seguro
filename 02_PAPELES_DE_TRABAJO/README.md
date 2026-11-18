# 02 · Papeles de trabajo

Aquí cada auditor documenta **lo que revisó, cómo lo revisó y qué encontró**, con su evidencia. Los papeles de trabajo son la prueba de que el informe final está sustentado: si algo no está aquí, no puede ir al informe.

## Quién trabaja en cada subcarpeta

| Carpeta | Responsable | Qué evalúa |
|---|---|---|
| [D1_GOBIERNO](D1_GOBIERNO/README.md) | José Luis Gutiérrez Morales | Políticas, roles, inventario de activos, contratos, propiedad intelectual, leyes |
| [D2_DESARROLLO_SEGURO](D2_DESARROLLO_SEGURO/README.md) | José Luis Quispe Vargas | Ciclo de desarrollo, repositorios, código, secretos, dependencias, ambientes |
| [D3_INFRAESTRUCTURA](D3_INFRAESTRUCTURA/README.md) | Alex David Tola Julián | Servidor, dominio, TLS, nube, cuentas, 2FA, registros |
| [D4_D5_PERSONAS_CONTINUIDAD](D4_D5_PERSONAS_CONTINUIDAD/README.md) | Jhamil Calixto Mamani Quea | Personal, NDA, trabajo remoto, proveedores, respaldos, incidentes |
| [RIESGOS_Y_SOA](RIESGOS_Y_SOA/README.md) | Amílcar Quispe Santos | Matriz de riesgos, Declaración de Aplicabilidad, control de calidad |

Cada uno trabaja **solo en su carpeta**. Así no hay conflictos al subir cambios a GitHub.

## Nombres de archivos

| Tipo | Formato | Ejemplo |
|---|---|---|
| Papel de trabajo | `PT-<dominio>-<n.º>_<tema>.md` | `PT-D3-01_SERVIDOR_WEB.md` |
| Evidencia | `evidencias/EV-<dominio>-<n.º>_<descripcion>.<ext>` | `evidencias/EV-D3-01_cabeceras_http.png` |

## Plantilla de papel de trabajo

Copia este bloque en cada `PT-…md`:

```markdown
# PT-D?-0? · <Tema>

| Campo | Detalle |
|---|---|
| Auditor | |
| Fecha | |
| Control(es) ISO/IEC 27002:2022 | ej. 8.9, 8.24 |
| Objetivo de la prueba | Qué queremos comprobar |
| Técnica | Entrevista / inspección / observación / revisión de configuración |
| Fuente | Quién o qué sistema dio la información |

## Procedimiento
1. Paso realizado
2. …

## Resultado
Qué se encontró (hechos, no opiniones).

## Evidencia
- EV-D?-0? · descripción

## Conclusión
☐ Cumple · ☐ Cumple parcialmente · ☐ No cumple · ☐ No aplica
Nivel de madurez (0–5):
¿Genera hallazgo? ☐ Sí → H-?? · ☐ No
```

## Reglas para evidencias

- **Tapar** contraseñas, *tokens*, correos personales, IP internas y rostros antes de subir una captura.
- Solo capturas o documentos que Roger autorizó.
- Archivos pesados (videos, exportaciones grandes) van al Drive del equipo; aquí solo el enlace.
