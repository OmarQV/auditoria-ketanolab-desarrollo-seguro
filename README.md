---
title: "KETANOLAB · Inicio del equipo"
date: 2026-11-18
tags:
  - auditoria/ketanolab
  - auditoria/equipo
---

# Auditoría de seguridad al desarrollo de software · Ketanolab S.R.L.

> **Lee esto primero.** Resume en 5 minutos qué empresa auditamos, qué tipo de auditoría hacemos, quién trabaja en cada carpeta y qué toca hacer ahora. El detalle está en [`docs/`](docs/README.md).
>
> 🔒 **Repositorio privado y confidencial.** Contiene debilidades de seguridad de una empresa real. No hacerlo público ni compartirlo fuera del equipo y del docente.

## Título del trabajo

**Auditoría de seguridad de la información al desarrollo de software de Ketanolab S.R.L. y propuesta de un Manual de Desarrollo Seguro basado en ISO/IEC 27001:2022 y 27002:2022**

Título corto: *Auditoría de seguridad al desarrollo de software · Ketanolab S.R.L.*

Es la versión actualizada de la propuesta presentada al docente hace dos meses, «Auditoría y seguridad al desarrollo». No cambia la idea: se precisan la empresa, las normas y el entregable.

## Equipo

| N.º | Integrante | Rol asignado | Dominio |
|---|---|---|---|
| 1 | Omar Quispe Vargas | **Auditor líder / coordinador** | General |
| 2 | José Luis Gutiérrez Morales | Auditor de gobierno, legal y políticas | D1 |
| 3 | José Luis Quispe Vargas | Auditor de desarrollo seguro | D2 |
| 4 | Alex David Tola Julián | Auditor de infraestructura y accesos | D3 |
| 5 | Jhamil Calixto Mamani Quea | Auditor de personas, terceros y continuidad | D4 y D5 |
| 6 | Amílcar Quispe Santos | Analista de riesgos y control de calidad | Transversal |

Qué hace cada rol (detalle en [Propuesta §6](docs/02_PROPUESTA_AUDITORIA_KETANOLAB.md)):

| Rol | Qué hace | Dominio |
|---|---|---|
| Auditor líder / coordinador | Plan, cronograma, relación con Roger, consolida el informe y la presentación | General |
| Gobierno, legal y políticas | Inventario de activos, roles, contratos, propiedad intelectual, leyes bolivianas, política general | D1 |
| Desarrollo seguro | Repositorios, revisión de código, secretos, dependencias, ambientes; redacción final del manual | D2 |
| Infraestructura y accesos | Servidor, dominio, TLS, nube, cuentas, 2FA, registros | D3 |
| Personas, terceros y continuidad | NDA, altas y bajas, trabajo remoto, proveedores, respaldos, incidentes | D4 y D5 |
| Riesgos y control de calidad | Matriz de riesgos ISO 27005, Declaración de Aplicabilidad (SoA), índice de papeles de trabajo, revisión cruzada | Transversal |

## Estructura del repositorio: quién trabaja dónde

```
01_KETANOLAB/
├── README.md                       ← estás aquí
├── docs/                           documentos base (contexto, propuesta, manual borrador)
├── 01_PLANIFICACION/               carta, plan, cronograma, actas
├── 02_PAPELES_DE_TRABAJO/
│   ├── D1_GOBIERNO/
│   ├── D2_DESARROLLO_SEGURO/
│   ├── D3_INFRAESTRUCTURA/
│   ├── D4_D5_PERSONAS_CONTINUIDAD/
│   └── RIESGOS_Y_SOA/
├── 03_HALLAZGOS/                   una ficha por hallazgo
├── 04_ENTREGABLES/                 manual final, políticas, procedimientos, plantillas
└── 05_INFORME_FINAL/               informe, carta de gerencia, presentación, Word/PDF
```

| Carpeta | Responsable | Por qué |
|---|---|---|
| [docs](docs/README.md) | Omar (mantiene) · todos (leen) | Base común: todos trabajamos con el mismo contexto, alcance y criterios |
| [01_PLANIFICACION](01_PLANIFICACION/README.md) | Omar · apoyo José Luis G. | El líder coordina con Roger; José Luis G. prepara la entrevista porque D1 necesita esa información primero |
| [02_PAPELES_DE_TRABAJO/D1_GOBIERNO](02_PAPELES_DE_TRABAJO/D1_GOBIERNO/README.md) | José Luis Gutiérrez Morales | Su dominio: políticas, activos, contratos y leyes |
| [02_PAPELES_DE_TRABAJO/D2_DESARROLLO_SEGURO](02_PAPELES_DE_TRABAJO/D2_DESARROLLO_SEGURO/README.md) | José Luis Quispe Vargas | Su dominio: código y ciclo de desarrollo; alimenta el manual |
| [02_PAPELES_DE_TRABAJO/D3_INFRAESTRUCTURA](02_PAPELES_DE_TRABAJO/D3_INFRAESTRUCTURA/README.md) | Alex David Tola Julián | Su dominio: servidor, dominio, nube y cuentas |
| [02_PAPELES_DE_TRABAJO/D4_D5_PERSONAS_CONTINUIDAD](02_PAPELES_DE_TRABAJO/D4_D5_PERSONAS_CONTINUIDAD/README.md) | Jhamil Calixto Mamani Quea | Su dominio: personas, proveedores, respaldos e incidentes |
| [02_PAPELES_DE_TRABAJO/RIESGOS_Y_SOA](02_PAPELES_DE_TRABAJO/RIESGOS_Y_SOA/README.md) | Amílcar Quispe Santos | Rol transversal: prioriza riesgos y controla la calidad de todos |
| [03_HALLAZGOS](03_HALLAZGOS/README.md) | Cada auditor redacta los suyos · Amílcar consolida | Los hallazgos nacen en cada dominio y se validan con evidencia |
| [04_ENTREGABLES](04_ENTREGABLES/README.md) | Cada uno las políticas de su dominio (ver tabla en la carpeta) | Quien auditó el tema sabe qué control le falta a Ketanolab |
| [05_INFORME_FINAL](05_INFORME_FINAL/README.md) | Omar | El líder une todo en Word y PDF y presenta |

Cada carpeta tiene su propio README con qué evaluar, qué archivos se esperan y plantillas.

## La empresa en 6 líneas

- **Ketanolab S.R.L.**, La Paz, activa desde al menos 2012. Desarrolla apps móviles y web, asesora en visión computacional y marketing.
- Dueño: **Roger Dante Prado Lafuente**. Lidera varios proyectos, es consultor del Departamento de Emprendimiento e Innovación de la UMSA y docente de marketing en maestrías.
- Proyectos conocidos: **SimiDic / NuSimi** (diccionarios de lenguas nativas, código abierto), juegos y apps turísticas. Proyectos actuales con nosotros: **monitoreo de obras con visión computacional** y **aplicación para ferias**.
- **No tiene ninguna política, norma ni procedimiento de seguridad documentado.**
- En fuentes públicas ya encontramos indicios: web caída (página por defecto de Apache), certificado HTTPS de otro dominio, código en una cuenta personal de GitHub, archivo de configuración local subido a un repositorio.
- Contexto actual: filtración de datos de entidades del Estado boliviano (noviembre 2026), ataques a librerías npm y apps hechas con IA que expusieron datos.

Detalle completo: [Contexto de la empresa](docs/01_CONTEXTO_KETANOLAB.md)

## Qué tipo de auditoría hacemos

| Aspecto | Definición |
|---|---|
| Tipo | **Auditoría de sistemas, de seguridad de la información**, de **diagnóstico y cumplimiento (análisis de brechas)** |
| Carácter | Académica, con autorización escrita del propietario. No es certificación ISO |
| Objeto | El **proceso de desarrollo de software** de Ketanolab y una muestra de proyectos que Roger desarrolló o asesoró: NuSimi, infraestructura de Ketanolab, app para ferias, monitoreo de obras |
| Criterios | ISO/IEC 27001:2022 (cláusulas 4–10 y Anexo A), ISO/IEC 27002:2022 (énfasis en controles 8.25–8.33), ISO/IEC 27005 (riesgos), COBIT 2019, OWASP Top 10 / ASVS / MASVS, NIST SSDF, normativa boliviana |
| Técnicas | Entrevistas, cuestionarios, inspección documental, revisión de configuraciones y repositorios, observación. **Sin pruebas intrusivas** |
| Medición | Nivel de madurez de 0 a 5 por dominio (D1 a D5) |
| Resultado | Hallazgos (criterio, condición, causa, efecto, recomendación) → informe → entregables de mejora |

## Qué entregamos

| Para quién | Entregable |
|---|---|
| **Roger / Ketanolab** | **Manual de Desarrollo Seguro KL-MDS-01** (entregable principal), informe de auditoría, carta de gerencia, inventario de activos, matriz de riesgos, SoA, kit de políticas y plantillas, hoja de ruta de 12 meses |
| **Docente** | Expediente completo: propuesta, carta firmada, actas, papeles de trabajo, evidencias, hallazgos, informe y presentación |

Detalle: [Propuesta de auditoría](docs/02_PROPUESTA_AUDITORIA_KETANOLAB.md) · [Manual de desarrollo seguro](docs/03_MANUAL_DESARROLLO_SEGURO_KETANOLAB.md) · [Tabla de entregables y responsables](04_ENTREGABLES/README.md)

## Qué leer y en qué orden

| Orden | Documento | Tiempo | Para qué |
|---|---|---|---|
| 1 | Este README | 5 min | Visión general |
| 2 | [Contexto](docs/01_CONTEXTO_KETANOLAB.md) | 15 min | Conocer la empresa, a Roger, los indicios y las preguntas pendientes |
| 3 | [Propuesta](docs/02_PROPUESTA_AUDITORIA_KETANOLAB.md) | 20 min | Objetivos, alcance, criterios, fases, roles y entregables |
| 4 | [Manual](docs/03_MANUAL_DESARROLLO_SEGURO_KETANOLAB.md) | 30 min | Borrador del entregable principal. Cada uno revisa a fondo las secciones de su dominio |
| 5 | README de tu carpeta | 10 min | Qué evaluar, qué archivos entregar, plantillas |

## Estado al 18/11/2026

| Hecho | Pendiente |
|---|---|
| Investigación pública de la empresa | Carta de autorización firmada por Roger (la gestiona Omar, auditor líder) |
| Contexto, propuesta y borrador del manual | Verificar independencia (quién participa en qué proyecto) |
| Roles asignados y estructura de carpetas | Entrevista con Roger (guía en Contexto §8) |
| Título definido | Confirmar datos: dirección, nombre del departamento de la UMSA, rol de Pedro Terán |
| Observaciones preliminares O-01 a O-07 | |

## Agenda de la primera reunión del equipo (45 min)

1. **Confirmar roles** (tabla de arriba). Si alguien prefiere otro rol, se intercambia en esta reunión.
2. **Independencia:** cada uno declara en qué proyectos con Roger participa (ferias, monitoreo de obras u otros). Nadie audita un proyecto en el que trabaja.
3. **Fechas:** entrevista con Roger y cronograma de 5 semanas (Propuesta §5).
4. **Revisión del manual:** cada responsable de dominio revisa sus reglas y propone cambios en una semana.
5. **Repositorio:** que todos clonen el repo y hagan una prueba de subir un cambio en su carpeta.

## Tareas de la semana 1 por rol

| Rol | Tarea |
|---|---|
| Líder · Omar | Cronograma con fechas reales; coordinar carta y entrevista con Roger |
| Gobierno y legal · José Luis G. | Preparar el cuestionario de la entrevista (Contexto §8) y la plantilla de inventario de activos |
| Desarrollo seguro · José Luis Q. | Revisar el repositorio público NuSimi con la lista de verificación del manual (§11) |
| Infraestructura · Alex | Preparar la lista de verificación de servidor, dominio, TLS y cuentas (D3); documentar O-01 a O-04 como papel de trabajo |
| Personas y continuidad · Jhamil | Preparar las listas de verificación D4 y D5 (NDA, altas y bajas, respaldos, incidentes) |
| Riesgos y calidad · Amílcar | Plantilla de matriz de riesgos (formato del examen) y plantilla de SoA con los 93 controles |

## Cómo trabajar con el repositorio

Con **GitHub Desktop** (más fácil) o con la terminal:

1. **Clonar una sola vez:** `git clone <url-del-repo>`
2. **Antes de empezar cada día, traer cambios:** `git pull` (en GitHub Desktop: *Fetch / Pull origin*)
3. **Trabajar solo en tu carpeta.** Si necesitas cambiar algo de otra, avísale a su responsable.
4. **Guardar y subir:**
   ```bash
   git add .
   git commit -m "D3: papel de trabajo del servidor web"
   git push
   ```
   Empieza el mensaje con tu dominio (`D1:`, `D2:`, `D3:`, `D4:`, `RIESGOS:`, `PLAN:`, `INFORME:`).
5. **Archivos Word y Excel:** Git no puede mezclar dos versiones de uno de ellos. Cada `.docx` / `.xlsx` tiene **un solo dueño**. De preferencia, escribe en Markdown (`.md`).
6. Si `git push` falla, haz `git pull` y vuelve a intentar. Si aparece un conflicto, avisa a Omar antes de borrar nada.

## Reglas del equipo

- **Nada intrusivo:** sin escaneos de puertos, pruebas de penetración ni intentos de acceso, ni siquiera con la carta firmada, salvo que Roger lo autorice por escrito y de forma específica.
- **Nunca subir contraseñas, claves, *tokens* ni datos personales** al repositorio. Tapar o recortar las capturas. Si subiste algo por error, avisa de inmediato: borrarlo no basta, queda en el historial.
- Toda afirmación del informe debe tener **evidencia** (acta, captura, documento) referenciada en un papel de trabajo.
- La información de Roger y de los proyectos es **confidencial**: se comparte solo dentro del equipo y con el docente.
- Videos, audios y archivos pesados van al Drive del equipo; en el repositorio solo el enlace.
