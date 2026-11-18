---
title: "KETANOLAB · Propuesta de auditoría y entregables"
date: 2026-11-18
tags:
  - auditoria/ketanolab
  - auditoria/propuesta
---

# KETANOLAB · Propuesta de auditoría de seguridad de la información

> Basada en el [Contexto de la empresa](01_CONTEXTO_KETANOLAB.md). Sirve para dos públicos: **Roger Dante Prado Lafuente** (qué recibe Ketanolab) y el **docente** (qué auditamos, con qué criterios y cómo).

## 1. Resumen de la propuesta

Ketanolab desarrolla software para terceros pero no tiene **ninguna política, norma ni control de seguridad documentado**. Auditarla «contra ISO 27001» daría un resultado obvio: no cumple nada. Por eso proponemos una auditoría que **mida dónde está** y **le deje lo necesario para empezar**:

1. **Auditoría de diagnóstico (análisis de brechas)** frente a ISO/IEC 27001:2022 y los controles de ISO/IEC 27002:2022, enfocada en el proceso de desarrollo de software. Se evalúa con evidencia (entrevistas, revisión de configuraciones, inspección de repositorios y cuentas) y se asigna un **nivel de madurez de 0 a 5** a cada dominio.
2. **Manual de desarrollo seguro de software** ([KL-MDS-01](03_MANUAL_DESARROLLO_SEGURO_KETANOLAB.md)): entregable principal. Se construye a partir de los hallazgos de la auditoría sobre los proyectos que Roger desarrolló o asesoró y de los incidentes recientes (filtración de datos del Estado boliviano en noviembre de 2026, ataques a la cadena de suministro npm, apps hechas con IA que expusieron datos, caídas de la nube). Le sirve a Roger para **desarrollar** con Ketanolab y para **asesorar** a los emprendimientos que acompaña como consultor del Departamento de Emprendimiento e Innovación de la UMSA.
3. **Propuesta de un SGSI mínimo y proporcional** a una microempresa de software: política general, políticas temáticas, controles priorizados, plantillas y una hoja de ruta. No es una certificación ni pretende serlo.

**Título del trabajo:** ***Auditoría de seguridad de la información al desarrollo de software de Ketanolab S.R.L. y propuesta de un Manual de Desarrollo Seguro basado en ISO/IEC 27001:2022 y 27002:2022***

- Título corto (carátula y diapositivas): **Auditoría de seguridad al desarrollo de software · Ketanolab S.R.L.**
- Evolución del título presentado hace dos meses («Auditoría y seguridad al desarrollo»): se mantiene la idea y se precisan la empresa, las normas y el entregable.

## 2. Objetivos

**General:** evaluar el estado de la seguridad de la información en Ketanolab S.R.L., con énfasis en el ciclo de desarrollo de software y la protección de la información de clientes, frente a ISO/IEC 27001:2022 e ISO/IEC 27002:2022, y proponer políticas y controles priorizados para cerrar las brechas.

**Específicos:**

1. Levantar el inventario de activos de información (código, cuentas, servidores, dominios, datos de clientes, datasets, claves de firma).
2. Identificar y valorar riesgos según ISO/IEC 27005:2022.
3. Evaluar la existencia y el funcionamiento de controles en cinco dominios (sección 4) y asignar nivel de madurez.
4. Documentar hallazgos con criterio, condición, causa, efecto y recomendación.
5. Entregar a Ketanolab un kit de políticas, procedimientos y plantillas listo para adoptar, y una hoja de ruta de 12 meses.

## 3. Alcance

**Muestra de proyectos auditados** (software desarrollado o asesorado por Roger):

| Proyecto | Tipo | Por qué se incluye | Quién lo audita |
|---|---|---|---|
| NuSimi / SimiDic | App Android de código abierto (pública) | Código revisable sin acceso especial; permite probar controles de repositorio, secretos y dependencias | Cualquier integrante |
| Infraestructura de Ketanolab (`ketanolab.com`, servidor, GitHub) | Servidor y cuentas | Ya hay indicios públicos (O-01 a O-06) | Auditor de infraestructura |
| Aplicación para ferias | App con registro de usuarios | Datos personales, posibles pagos, picos de carga | Integrante que **no** participe en su desarrollo |
| Monitoreo de obras con visión computacional | Visión computacional + cámaras | Video de trabajadores, cámaras IP, *datasets* | Integrante que **no** participe en su desarrollo |
| 1 o 2 emprendimientos asesorados por Roger (opcional, con permiso del emprendimiento) | Variable | Probar el diagnóstico rápido de 20 preguntas del manual | Auditor líder |

| Incluido | Excluido |
|---|---|
| Proceso de desarrollo de software (móvil y web): requisitos, código, repositorios, pruebas, despliegue, mantenimiento | Pruebas de penetración o escaneos activos sin autorización escrita específica |
| Gestión de accesos y cuentas: GitHub, Google Play/F-Droid, hosting/VPS, dominios, correo, nube, redes sociales | Auditoría financiera o tributaria |
| Infraestructura usada: servidor `164.68.97.107`, dominios, equipos de los desarrolladores (muestra) | Sistemas propios de los clientes (solo la parte que Ketanolab administra) |
| Manejo de información de clientes y usuarios finales, incluidos datasets de visión computacional | Certificación ISO (solo un organismo acreditado puede certificar) |
| Personas y terceros: contratos, confidencialidad, *freelancers*, alta y baja de personal | Proyectos en los que haya participado el integrante que los audite (ver independencia) |
| Respaldos, continuidad e incidentes | |

**Período evaluado:** situación actual (noviembre 2026) y evidencias de los últimos 12 meses.

## 4. Criterios (normas y marcos)

| Referencia | Para qué se usa |
|---|---|
| **ISO/IEC 27001:2022** — cláusulas 4 a 10 y Anexo A (93 controles) | Requisitos del SGSI; base del análisis de brechas y de la Declaración de Aplicabilidad (SoA) |
| **ISO/IEC 27002:2022** | Guía de implementación de cada control; redacción de las políticas |
| **ISO/IEC 27005:2022** | Metodología de evaluación y tratamiento de riesgos |
| **ISO/IEC 27035-1:2023** | Gestión de incidentes |
| **ISO/IEC 27701:2019** (referencia) | Privacidad y datos personales (datasets de imágenes) |
| **ISO/IEC 42001:2023** (referencia opcional) | Buenas prácticas para los proyectos de IA / visión computacional |
| **COBIT 2019** — APO12, APO13, BAI03, BAI06, DSS04, DSS05 | Marco de gobierno de TI visto en clase; niveles de capacidad para la madurez |
| **OWASP Top 10, OWASP ASVS, OWASP MASVS, NIST SP 800-218 (SSDF)** | Criterios técnicos de desarrollo seguro web y móvil |
| Legislación boliviana: CPE (arts. 21, 130), Ley 164 y D.S. 1793, Ley 1322 de Derecho de Autor | Requisitos legales (control 5.31) |

> Nota: la familia correcta es **ISO/IEC 27000** (27001 requisitos, 27002 controles). «ISO 21000» no aplica a este tema.

### 4.1 Controles del Anexo A priorizados para una empresa de desarrollo

ISO/IEC 27001:2022 agrupa los 93 controles en 4 temas: organizacionales (37), de personas (8), físicos (14) y tecnológicos (34). Para Ketanolab priorizamos estos:

| Dominio de auditoría | Controles ISO/IEC 27002:2022 | Qué se revisa en la práctica |
|---|---|---|
| **D1. Gobierno y políticas** | 5.1 Políticas · 5.2 Roles y responsabilidades · 5.9 Inventario de activos · 5.12 Clasificación · 5.31 Requisitos legales · 5.32 Propiedad intelectual · 5.34 Privacidad y datos personales | ¿Existe algún documento? ¿Quién es responsable de qué? ¿Hay inventario de cuentas y activos? ¿Los contratos dicen de quién es el código? |
| **D2. Desarrollo seguro (SDLC)** | 8.4 Acceso al código fuente · 8.25 Ciclo de vida de desarrollo seguro · 8.26 Requisitos de seguridad de aplicaciones · 8.27 Arquitectura segura · 8.28 Codificación segura · 8.29 Pruebas de seguridad · 8.30 Desarrollo externalizado · 8.31 Separación de ambientes · 8.32 Gestión de cambios · 8.33 Información de prueba | Protección de ramas, revisión de código, secretos en repositorios, dependencias vulnerables, ambientes separados, uso de datos reales en pruebas, firma de apps |
| **D3. Accesos, infraestructura y nube** | 5.15 Control de acceso · 5.16 Gestión de identidades · 5.17 Información de autenticación · 5.18 Derechos de acceso · 5.23 Servicios en la nube · 8.2 Privilegios · 8.5 Autenticación segura (2FA) · 8.8 Vulnerabilidades · 8.9 Configuración · 8.15 Registros (logs) · 8.20 Seguridad de redes · 8.24 Criptografía | Cuentas compartidas, 2FA, gestor de contraseñas, llaves SSH, servidor y TLS (ver O-01 a O-03), actualizaciones, logs |
| **D4. Personas y terceros** | 6.1 Verificación · 6.2 Términos de contratación · 6.3 Concienciación y formación · 6.5 Responsabilidades al cese · 6.6 Acuerdos de confidencialidad · 6.7 Trabajo remoto · 5.19–5.22 Seguridad con proveedores · 7.9/8.1 Equipos de usuario | NDA con desarrolladores y clientes, baja de accesos cuando alguien se va, uso de laptops personales, cifrado de disco |
| **D5. Continuidad e incidentes** | 5.24–5.28 Gestión de incidentes · 5.29 Seguridad durante la interrupción · 5.30 Preparación TIC para la continuidad · 8.13 Respaldos · 8.14 Redundancia | ¿Qué pasa si se borra el VPS, se roba una laptop o se pierde la cuenta de GitHub o Google Play? ¿Existen respaldos y se probó restaurar? |

## 5. Metodología y fases

Duración sugerida: **5 semanas** (ajustable al calendario del semestre).

| Fase | Semana | Actividades | Producto |
|---|---|---|---|
| **1. Planificación** | 1 | Carta de autorización firmada por Roger (alcance, confidencialidad, independencia, sin pruebas intrusivas); primera entrevista; solicitud de información | Carta firmada, plan de auditoría, acta de entrevista |
| **2. Levantamiento** | 1–2 | Inventario de activos y cuentas; mapa del proceso de desarrollo; entrevistas a 2–3 desarrolladores | Inventario de activos, diagrama del SDLC actual |
| **3. Evaluación de riesgos** | 2 | Identificar amenazas y vulnerabilidades por activo; valorar probabilidad × impacto (ISO 27005) | Matriz de riesgos (formato del examen del curso) |
| **4. Pruebas de controles** | 2–4 | Lista de verificación por dominio; revisión con autorización de configuración de GitHub, servidor, dominios, una muestra de repositorios y de equipos; *walkthrough* de un despliegue | Papeles de trabajo, evidencias (capturas, exportaciones), nivel de madurez por dominio |
| **5. Hallazgos e informe** | 4–5 | Redacción de hallazgos (criterio, condición, causa, efecto, recomendación); validación con Roger | Informe de auditoría, carta de gerencia |
| **6. Propuesta de mejora** | 4–5 | Redacción de políticas y plantillas; SoA borrador; hoja de ruta | Kit SGSI (sección 7) |
| **7. Presentación** | 5 | Presentación al docente y entrega a Ketanolab | Diapositivas y acta de entrega |

**Técnicas:** entrevista, cuestionario de control interno, observación, inspección documental, revisión de configuraciones y, solo con autorización escrita, herramientas de revisión no intrusivas (por ejemplo, revisión de secretos en repositorios propios, análisis de dependencias, evaluación del certificado TLS).

**Escala de madurez** (basada en COBIT 2019 / CMMI):

| Nivel | Significado |
|---|---|
| 0 Inexistente | No se hace |
| 1 Inicial | Se hace a veces, depende de la persona |
| 2 Repetible | Se hace siempre igual, pero no está escrito |
| 3 Definido | Está documentado y se comunica |
| 4 Gestionado | Se mide y se revisa |
| 5 Optimizado | Se mejora continuamente |

Expectativa realista: hoy Ketanolab estaría entre **0 y 2** en casi todo. La meta de la hoja de ruta es llegar a **nivel 3** en los controles priorizados.

## 6. Equipo de 6 integrantes: roles

| N.º | Integrante | Rol | Responsabilidades | Dominio |
|---|---|---|---|---|
| 1 | Omar Quispe Vargas | **Auditor líder / coordinador** | Planificación, carta de autorización, relación con Roger, consolidación del informe, presentación al docente | Coordinación general |
| 2 | José Luis Gutiérrez Morales | **Auditor de gobierno, legal y políticas** | Cláusulas 4–10 de ISO 27001, roles, inventario de activos, contratos, propiedad intelectual, normativa boliviana; redacción de la política general | D1 |
| 3 | José Luis Quispe Vargas | **Auditor de desarrollo seguro** | Revisión del SDLC, repositorios, ramas, secretos, dependencias, ambientes, firma de apps; checklist OWASP; redacción final del manual | D2 |
| 4 | Alex David Tola Julián | **Auditor de infraestructura y accesos** | Servidor, dominios, TLS, hosting/nube, cuentas, 2FA, llaves, logs, actualizaciones | D3 |
| 5 | Jhamil Calixto Mamani Quea | **Auditor de personas, terceros y continuidad** | NDA, alta y baja de personal, trabajo remoto, proveedores, respaldos, incidentes | D4 y D5 |
| 6 | Amílcar Quispe Santos | **Analista de riesgos y control de calidad** | Matriz de riesgos ISO 27005, SoA, índice de papeles de trabajo, revisión cruzada de evidencias y hallazgos | Transversal |

Regla de independencia: quien haya trabajado en un proyecto de Ketanolab **no** revisa ese proyecto; el líder reasigna. Esto incluye los proyectos actuales con Roger (monitoreo de obras y aplicación para ferias). Si todo el equipo participa en ellos, se declara en el informe como **limitación de independencia** y esos proyectos se presentan como autoevaluación con el checklist del manual, no como auditoría.

## 7. Qué le dejamos a Ketanolab (entregables)

### 7.1 Resultados de la auditoría

| N.º | Entregable | Descripción |
|---|---|---|
| E1 | **Informe de auditoría** | Alcance, criterios, metodología, hallazgos con nivel de riesgo, madurez por dominio, conclusión |
| E2 | **Carta de gerencia** | Resumen ejecutivo de 1–2 páginas para Roger, en lenguaje no técnico |
| E3 | **Inventario de activos de información** | Hoja de cálculo: activo, dueño, ubicación, clasificación, respaldo, acceso |
| E4 | **Matriz de riesgos** | Riesgos valorados con tratamiento propuesto (formato del curso) |
| E5 | **Declaración de Aplicabilidad (SoA) borrador** | Los 93 controles del Anexo A: aplica / no aplica, justificación y estado |

### 7.2 Manual de desarrollo seguro (entregable principal)

| N.º | Entregable | Descripción |
|---|---|---|
| **M1** | [Manual de desarrollo seguro KL-MDS-01](03_MANUAL_DESARROLLO_SEGURO_KETANOLAB.md) | 60 reglas codificadas (R-01 a R-49 y R-60 a R-70) por fase del ciclo de vida, guías para web, móvil, Firebase/Supabase, visión computacional y apps con pagos; niveles de exigencia por etapa del emprendimiento; diagnóstico de 20 preguntas para asesorías; checklist de entrega; respuesta a incidentes; correspondencia con ISO/IEC 27002 8.25–8.33 |
| M2 | Taller de 1 hora para Roger | Cómo usar el manual al asesorar emprendimientos en la UMSA y en Ketanolab (material reutilizable para sus clases) |

El manual reemplaza la política P3 y absorbe P4 del kit de la sección 7.3: el resto de políticas complementa al manual.

### 7.3 Kit de SGSI mínimo (documentos para adoptar)

| N.º | Documento | Contenido esencial | Control |
|---|---|---|---|
| P1 | **Política general de seguridad de la información** | Compromiso de la dirección, objetivos, alcance, roles, revisión anual (1–2 páginas, firmada por Roger) | 5.1 · cl. 5.2 |
| P2 | Política de control de accesos y contraseñas | Cuentas a nombre de la empresa, 2FA obligatorio, gestor de contraseñas, mínimo privilegio, baja inmediata al cese | 5.15–5.18 · 8.5 |
| P3 | Política de desarrollo seguro | Requisitos de seguridad desde el inicio, revisión de código, ramas protegidas, ambientes separados, sin datos reales en pruebas, *checklist* OWASP | 8.25–8.33 |
| P4 | Política de gestión de código fuente y secretos | Repositorios en una organización de GitHub de la empresa, nada de secretos en el código, custodia de claves de firma de apps, licencias | 8.4 · 5.32 |
| P5 | Política de respaldos | Regla 3-2-1, frecuencia por activo, prueba de restauración trimestral | 8.13 |
| P6 | Política de uso aceptable y trabajo remoto | Equipos, cifrado de disco, Wi-Fi pública, bloqueo de pantalla, uso de IA generativa con código de clientes | 6.7 · 8.1 · 5.10 |
| P7 | Política de proveedores y servicios en la nube | Criterios para elegir hosting y SaaS, quién administra cada cuenta | 5.19–5.23 |
| P8 | Política de clasificación y manejo de información de clientes y datos personales | Niveles (público, interno, confidencial), datasets de visión computacional: consentimiento, anonimización, eliminación al cierre del proyecto | 5.12 · 5.34 |
| PR1 | **Procedimiento de respuesta a incidentes** (1 página) | Qué hacer, a quién avisar, cómo registrar; casos: cuenta comprometida, laptop robada, servidor caído | 5.24–5.28 |
| PR2 | Procedimiento de alta y baja de personal | Lista de verificación de accesos al entrar y al salir | 5.18 · 6.5 |
| PR3 | Procedimiento de despliegue y entrega al cliente | Pasos, aprobaciones, acta de entrega, traspaso de credenciales | 8.32 |
| T1 | Plantilla de acuerdo de confidencialidad (NDA) | Para colaboradores y para clientes | 6.6 |
| T2 | Cláusulas tipo de contrato de desarrollo | Propiedad intelectual, confidencialidad, seguridad, soporte | 5.20 · 5.32 |
| T3 | Checklist de seguridad por proyecto (*Definition of Done*) | 15–20 puntos verificables antes de cada entrega (OWASP Top 10 / MASVS) | 8.26 · 8.29 |
| T4 | Registro de incidentes | Hoja simple: fecha, descripción, impacto, acción, lección | 5.26–5.27 |

Todos los documentos se redactan **cortos y aplicables** a un equipo pequeño. Una política de 20 páginas que nadie lee no sirve.

### 7.4 Hoja de ruta sugerida

| Plazo | Acciones (de mayor a menor beneficio por esfuerzo) |
|---|---|
| **Inmediato (0–30 días, «quick wins»)** | 2FA en todas las cuentas críticas · gestor de contraseñas para el equipo · migrar repositorios a una **organización GitHub** de Ketanolab · protección de ramas y *secret scanning*/Dependabot · corregir `ketanolab.com` (web real o apagar Apache, certificado propio, ocultar versión) · respaldo de claves de firma de apps · inventario de cuentas y dominios con dueño y fecha de renovación |
| **Corto plazo (1–3 meses)** | Firmar política general · adoptar P2, P3, P4, P5 · NDA con todo colaborador · primera prueba de restauración de respaldos · checklist T3 en cada proyecto |
| **Mediano plazo (3–6 meses)** | Políticas P6–P8 · procedimiento de incidentes ensayado (simulacro) · capacitación básica del equipo · cláusulas de seguridad en contratos nuevos |
| **12 meses** | Revisión por la dirección (cl. 9.3), auditoría interna (cl. 9.2), actualizar riesgos y SoA. Evaluar si conviene una certificación ISO 27001 según lo pidan los clientes |

## 8. Hallazgos esperados (hipótesis a verificar)

Sirven para preparar las pruebas, no son conclusiones:

| Hipótesis | Prueba que la confirma o descarta |
|---|---|
| Las cuentas críticas dependen de una o dos personas y algunas son personales | Inventario de cuentas y titulares (ya hay indicio: O-05) |
| No hay 2FA en todas las cuentas | Revisión de configuración con el titular |
| Hay secretos o archivos de configuración local en repositorios | Revisión de repositorios con herramienta de detección de secretos, con autorización (indicio: O-06) |
| No hay respaldos probados de servidores y bases de datos | Entrevista + evidencia de último respaldo y restauración |
| El servidor web está desactualizado o mal configurado | Revisión de configuración (indicios: O-01 a O-03) |
| No hay NDA ni cláusulas de propiedad intelectual con colaboradores | Revisión de contratos (muestra) |
| No hay reglas para datasets con imágenes de personas | Entrevista sobre proyectos de visión computacional |

## 9. Requisitos para empezar (pedir a Roger)

1. **Carta de autorización** firmada (modelo del curso: carta modelo del curso (fuera de este repositorio)) con alcance, confidencialidad, declaración de independencia y prohibición de pruebas intrusivas.
2. Una entrevista de 60 minutos (guía en [Contexto §8](01_CONTEXTO_KETANOLAB.md)).
3. Acceso de solo lectura, o sesión guiada, a: GitHub, panel del hosting/VPS, registrador de dominios, Google Play Console.
4. Contratos tipo (cliente y colaborador), si existen.
5. Lista del personal actual y de los que salieron en los últimos 12 meses.

## 10. Cómo lo presentamos al docente

- **Tipo de auditoría:** auditoría de sistemas de seguridad de la información, de diagnóstico y cumplimiento, en una empresa real con autorización.
- **Producto estrella:** el manual de desarrollo seguro, que nace de los hallazgos y de incidentes reales de 2026 y que Roger puede replicar en los emprendimientos que asesora en la UMSA. El impacto va más allá de una sola empresa.
- **Valor del caso:** empresa de software sin documentación, situación frecuente en Bolivia; permite aplicar ISO 27001/27002, ISO 27005, COBIT 2019 y OWASP de forma completa: planificación, riesgo, pruebas, hallazgos, informe y seguimiento.
- **Evidencias:** carta firmada, actas, papeles de trabajo, matriz de riesgos, SoA, informe y kit de políticas.
- **Límites declarados:** no es certificación; no hubo pruebas intrusivas; independencia gestionada.

Estructura de carpetas sugerida (igual al expediente anterior):

```
01_KETANOLAB/
  README.md                         inicio: título, equipo, quién trabaja dónde
  docs/                             contexto, propuesta y manual (borrador)
  01_PLANIFICACION/                 carta, plan, cronograma, actas de entrevistas
  02_PAPELES_DE_TRABAJO/
    D1_GOBIERNO/                    checklists y evidencias por dominio
    D2_DESARROLLO_SEGURO/
    D3_INFRAESTRUCTURA/
    D4_D5_PERSONAS_CONTINUIDAD/
    RIESGOS_Y_SOA/                  matriz de riesgos, SoA, inventario consolidado
  03_HALLAZGOS/                     fichas de hallazgos H-01, H-02…
  04_ENTREGABLES/                   manual final, políticas, procedimientos, plantillas
  05_INFORME_FINAL/                 informe, carta de gerencia, presentación, Word/PDF
```
