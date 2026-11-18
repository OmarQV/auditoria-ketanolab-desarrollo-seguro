---
title: "KETANOLAB · Contexto de la empresa"
date: 2026-11-18
tags:
  - auditoria/ketanolab
  - auditoria/contexto
---

# KETANOLAB · Contexto de la empresa a auditar

> Documento de contexto para la auditoría académica de sistemas (Auditoría de Sistemas, Semestre II-2026).
> Reemplaza el caso IRUPANA (caso anterior, fuera de este repositorio), descartado por tiempo. La propuesta de trabajo está en [Propuesta de auditoría](02_PROPUESTA_AUDITORIA_KETANOLAB.md).

| Información principal | Detalle |
|---|---|
| Razón social | **Ketanolab S.R.L.** (se presenta como «KetanoLab» / «Ketano Lab») |
| Rubro | Desarrollo de software: aplicaciones móviles, aplicaciones web, asesoría en visión computacional y marketing digital |
| Ubicación | La Paz, Bolivia. Un directorio empresarial registra la dirección **Calle Cuba N.º 1673, zona Miraflores** (por confirmar en entrevista) |
| Propietario / responsable | **Roger Dante Prado Lafuente**, dueño de la empresa; líder de varios proyectos de software; consultor del Departamento de Emprendimiento e Innovación de la UMSA; docente de marketing en maestrías (ver §3.1) |
| Otra persona vinculada públicamente | **Pedro Terán**: citado en 2012 como oficial de Marketing de KetanoLab; titular de la cuenta GitHub `KetanoLab` (rol actual por confirmar) |
| Antigüedad | Activa al menos desde **2012** (lanzamiento público de SimiDic) |
| Sitio web | `ketanolab.com` (actualmente sin contenido propio, ver §5); `ketanolabsrl.com` (no resuelve) |
| Presencia pública | [Facebook](https://www.facebook.com/KetanoLab) · [GitHub](https://github.com/KetanoLab) · apps en Google Play y F-Droid |
| Documentación de seguridad | **No existe**: sin políticas, normas, procedimientos ni controles documentados (declarado por el propietario al equipo) |
| Relación con el equipo | Integrantes del equipo han trabajado con Ketanolab en proyectos de app móvil y web (ver §6, independencia) |
| Tipo de trabajo propuesto | Auditoría académica de diagnóstico de seguridad de la información con base en la familia ISO/IEC 27000 |
| Título del trabajo | *Auditoría de seguridad de la información al desarrollo de software de Ketanolab S.R.L. y propuesta de un Manual de Desarrollo Seguro basado en ISO/IEC 27001:2022 y 27002:2022* |
| Equipo auditor | Omar Quispe Vargas (auditor líder) · José Luis Gutiérrez Morales · José Luis Quispe Vargas · Alex David Tola Julián · Jhamil Calixto Mamani Quea · Amílcar Quispe Santos |

---

## 1. ¿A qué se dedica Ketanolab?

Ketanolab es una empresa boliviana pequeña de **desarrollo de software a medida**. La prensa la describió en 2012 como una «empresa boliviana especializada en el desarrollo de aplicaciones móviles» ([Los Tiempos, 15/10/2012](https://www.lostiempos.com/tendencias/bienestar/20121015/lanzan-simidic-primer-diccionario-aymara-quechua-guarani-android)). Un directorio empresarial boliviano la lista con servicios de ingeniería de software y sistemas, diseño web, desarrollo de software, seguridad y soporte de sistemas, capacitación y consultoría en estrategia tecnológica.

Según lo conocido por el equipo por trabajo directo con la empresa, sus líneas actuales son:

| Línea de servicio | Descripción | Información que maneja (relevante para la auditoría) |
|---|---|---|
| Aplicaciones móviles | Desarrollo Android (Java/Kotlin) y publicación en tiendas | Código fuente, claves de firma de APK/AAB, cuentas de Google Play/F-Droid, datos de usuarios finales |
| Aplicaciones web | Sistemas web a medida para clientes | Código, bases de datos de clientes, credenciales de servidores y hosting, dominios |
| Visión computacional (asesoría) | Asesoría a proyectos de visión por computadora / IA | Datasets de imágenes y video (posibles datos personales: rostros, placas), modelos entrenados, GPU/nube |
| Marketing digital | Apoyo en marketing y presencia digital | Cuentas de redes sociales propias y de clientes, datos de contacto, accesos a páginas |
| Proyectos con instituciones | Trabajo con fundaciones y entidades públicas (ej. Fundación ILLA, coordinación con el Ministerio de Educación) | Contenido de terceros, propiedad intelectual compartida, requisitos de entidades públicas |

Modelo operativo probable (a validar en entrevista): equipo reducido y variable por proyecto, **trabajo remoto** o híbrido, colaboradores externos o *freelance*, uso de servicios en la nube (GitHub, hosting VPS, Google Workspace o similares) y equipos personales para desarrollar.

## 2. Proyectos públicos identificados

| Proyecto | Año | Descripción | Fuente |
|---|---|---|---|
| **SimiDic** | 2012 | Primer diccionario aimara, quechua y guaraní para Android, gratuito y de código abierto (GPLv3). Desarrollado con la **Fundación ILLA** y coordinado con el Ministerio de Educación. Paquete `com.ketanolab.simidic` | [Los Tiempos](https://www.lostiempos.com/tendencias/bienestar/20121015/lanzan-simidic-primer-diccionario-aymara-quechua-guarani-android) · [SourceForge](https://sourceforge.net/projects/simidic/) · [GitHub](https://github.com/KetanoLab) |
| **NuSimi** | 2022 | Sucesor de SimiDic reescrito en **Kotlin**: 30 diccionarios de 11 lenguas nativas (aimara, guaraní, mapuche, mochó, mojeño, mosetén, movima, quechua, takana, tsimane', uru), funciona sin internet. GPL-3.0. Publicado en Google Play y F-Droid. Paquete `com.ketanolab.nusimi` | [F-Droid (Fossdroid)](https://fossdroid.com/a/nusimi.html) · [GitHub Nusimi-android](https://github.com/KetanoLab/Nusimi-android) |
| **Cacho de cacho** | — | Juego del cacho (dados) para Android, Java | [GitHub](https://github.com/KetanoLab/cacho-de-cacho) |
| **Bolivia Turística** | 2013 | App Android de lugares y eventos turísticos, basada en una app del Carnaval de Oruro | [GitHub](https://github.com/KetanoLab) |
| Proyectos privados con el equipo | Recientes | App móvil y aplicación web desarrolladas con integrantes del equipo; asesorías en visión computacional y marketing | Conocimiento directo del equipo (detallar en entrevista) |

Stack tecnológico observable: **Android (Java, Kotlin, Gradle, Fastlane)**, GitHub como repositorio, servidor **Apache 2.4.58 sobre Ubuntu** en un VPS (IP `164.68.97.107`). El stack web y de visión computacional (Python, frameworks, nube, GPU) debe levantarse en la entrevista.

## 3. Personas e interlocutores

| Persona | Rol | Uso en la auditoría |
|---|---|---|
| Roger Dante Prado Lafuente | Propietario de Ketanolab | Interlocutor principal, firma la carta de autorización y recibe el informe |
| Pedro Terán | Marketing (2012); titular de la cuenta GitHub `KetanoLab` | Confirmar si sigue vinculado y quién controla repositorios y cuentas de la empresa |
| Desarrolladores / colaboradores | Por identificar | Entrevistas cortas sobre forma de trabajo, accesos y equipos |
| Clientes | Por identificar | Solo como contexto (contratos, datos que entregan), sin contactarlos |

### 3.1 Perfil actual de Roger Dante Prado Lafuente

Información proporcionada por el equipo (no hay fuentes públicas en internet que la confirmen; validar en entrevista):

| Ámbito | Actividad | Por qué importa para la auditoría |
|---|---|---|
| Ketanolab | Dueño; lidera distintos proyectos de software (móvil, web, visión computacional) | Decide cómo se desarrolla; es quien adoptaría las políticas |
| UMSA | **Consultor del Departamento de Emprendimiento e Innovación**, unidad creada recientemente (2025–2026) y encargada por el Rectorado. Apoya emprendimientos de desarrollo de software, comercio y otros rubros | Asesora a muchos emprendimientos que construyen software. Un **manual de desarrollo seguro** le permite multiplicar las buenas prácticas en todos ellos |
| Docencia | Clases de marketing en maestrías y materias universitarias | Facilidad para difundir y capacitar con el material que entreguemos |
| Asesoría de software | Modelo de negocio, contactos, «aterrizar» el software en el mercado | La seguridad debe presentarse en lenguaje de negocio: riesgo, costo, confianza del cliente |

> Nota: en las fuentes públicas de la UMSA aparecen el DIPGIS (Vicerrectorado) y el Centro de Innovación y Desarrollo Empresarial (CIDE); el nombre y la dependencia exactos del departamento donde trabaja Roger deben confirmarse con él.

### 3.2 Proyectos actuales con el equipo

| Proyecto | Descripción | Información sensible que maneja |
|---|---|---|
| **Monitoreo de obras con visión computacional** | Sistema para constructoras: cámaras en obra, detección y seguimiento con modelos de visión por computadora | Video de trabajadores (datos personales e imagen), ubicación de obras, cámaras IP expuestas a internet, modelos entrenados, datos del cliente constructor |
| **Aplicación para ferias** | App para ferias (expositores, visitantes, comercio) | Datos de registro de expositores y visitantes, posibles pagos, publicaciones |

Roger aporta en estos proyectos contactos, modelo de negocio y orientación para llevarlos al mercado. Esta relación debe declararse en la carta de autorización (ver §6).

## 4. Situación de seguridad declarada

El propietario reconoce que la empresa **no tiene documentación formal**: no hay política de seguridad de la información, normas internas, procedimientos, roles de seguridad, ni controles documentados. Esto es habitual en una microempresa de software, pero tiene consecuencias concretas para su negocio:

- El conocimiento y los accesos (servidores, dominios, tiendas de apps, claves de firma) suelen estar en **pocas personas**; si una se va, la empresa puede perder el control de sus activos.
- Los clientes y entidades públicas cada vez piden **evidencia de seguridad** (cláusulas de confidencialidad, desarrollo seguro, manejo de datos personales) para contratar.
- En proyectos de visión computacional se manejan **imágenes de personas**, lo que exige reglas sobre consentimiento, almacenamiento y eliminación de datos.
- Sin respaldos y procedimientos probados, un incidente (robo de laptop, cuenta comprometida, borrado de un servidor) puede ser irreversible. El caso Irupana (caso anterior, fuera de este repositorio) (pérdida de ocho gestiones en OneDrive) es un ejemplo cercano.

## 5. Observaciones preliminares de fuentes públicas (OSINT pasivo)

Revisión realizada el **18/11/2026**, solo con información pública y consultas normales (DNS, una petición HTTP a la página principal, perfiles públicos). **No se ejecutó ningún escaneo ni prueba intrusiva.** Son indicios a confirmar con el propietario, no hallazgos de auditoría.

| N.º | Observación | Posible implicancia | Control ISO/IEC 27002:2022 relacionado |
|---|---|---|---|
| O-01 | `ketanolab.com` y `www.ketanolab.com` resuelven a `164.68.97.107` y muestran la **página por defecto de Apache** («Apache2 Ubuntu Default Page: It works»), modificada por última vez el 18/03/2025 | El equipo confirma que la web corporativa ya no está activa; el servidor sigue encendido y expuesto sin propósito claro | 5.9 Inventario de activos · 8.9 Gestión de la configuración |
| O-02 | El certificado HTTPS presentado pertenece a **otro dominio** (`gitea.technogroup.bg`) | Error de configuración TLS o servidor compartido con terceros; el navegador muestra alerta de seguridad a visitantes | 8.24 Uso de criptografía · 5.23 Servicios en la nube · 5.22 Proveedores |
| O-03 | El servidor anuncia su versión exacta (`Server: Apache/2.4.58 (Ubuntu)`) | Facilita a un atacante buscar vulnerabilidades conocidas | 8.8 Gestión de vulnerabilidades técnicas · 8.9 Configuración |
| O-04 | El dominio `ketanolabsrl.com`, publicado en el perfil de GitHub, **no resuelve** | Información de contacto desactualizada; riesgo de que un tercero registre el dominio y suplante a la empresa | 5.9 Inventario · 5.7 Inteligencia de amenazas |
| O-05 | La cuenta `KetanoLab` en GitHub es una **cuenta personal** (a nombre de Pedro Terán), no una *organización* de GitHub | La propiedad del código depende de una persona; sin roles, sin auditoría de accesos, riesgo de pérdida de control | 5.15 Control de acceso · 5.18 Derechos de acceso · 8.4 Acceso al código fuente · 5.32 Propiedad intelectual |
| O-06 | El repositorio `Nusimi-android` tiene versionado el archivo `local.properties` y no tiene `SECURITY.md` | `local.properties` suele contener rutas locales y a veces secretos (claves de firma, API keys); no hay canal para reportar vulnerabilidades | 8.4 Código fuente · 8.28 Codificación segura · 5.5/5.6 Contacto con autoridades y grupos |
| O-07 | Los proyectos públicos usan licencia **GPL-3.0** y dependen de contenido de terceros (diccionarios de autores bolivianos y peruanos) | Necesidad de controlar licencias de software y derechos de contenido, propios y de clientes | 5.32 Derechos de propiedad intelectual · 5.31 Requisitos legales |

## 6. Independencia del equipo auditor

Integrantes del equipo han trabajado con Ketanolab en proyectos de desarrollo y actualmente trabajan con Roger en el monitoreo de obras con visión computacional y en la aplicación para ferias. Por ética de auditoría (y para que el docente lo valore), esto debe **declararse por escrito** en la carta de autorización y manejarse así:

- Ningún integrante audita un proyecto o sistema en el que haya participado; esas áreas se asignan a otro integrante.
- El trabajo se presenta como **auditoría académica de diagnóstico**; las políticas y plantillas que el equipo entregue son **recomendaciones**, y el informe distingue entre lo evaluado (hallazgos) y lo propuesto (mejoras).
- La relación de amistad con el propietario se declara; las conclusiones se sustentan solo en evidencia.

## 7. Marco legal y normativo de referencia (Bolivia)

| Norma | Aplicación a Ketanolab |
|---|---|
| Constitución Política del Estado (arts. 21, 130 — privacidad y acción de protección de privacidad) | Manejo de datos personales de usuarios y de datasets de imágenes |
| Ley N.º 164 de Telecomunicaciones y TIC (2011) y D.S. N.º 1793 | Documentos y firma electrónica, comercio electrónico, desarrollo de contenidos y aplicaciones |
| Ley N.º 1322 de Derecho de Autor | Protección del software como obra; titularidad del código entre empresa, empleados y clientes |
| Lineamientos de AGETIC (Plan Institucional de Seguridad de la Información para entidades públicas) | Requisitos que pueden exigirle entidades públicas clientes |
| Código de Comercio | Conservación de documentación de la S.R.L. |

A la fecha de este documento Bolivia **no cuenta con una ley general de protección de datos personales** vigente equivalente al RGPD; se usará como buena práctica ISO/IEC 27701 / 27002 control 5.34. *Verificar vigencia antes de la entrega final.*

## 8. Lo que falta saber (para la primera entrevista)

1. Número de personas (fijas, *freelance*, practicantes) y si firman contratos o acuerdos de confidencialidad.
2. Inventario: cuentas (GitHub, Google Play, hosting, dominios, correo, nube, redes sociales), quién es dueño de cada una y si usan 2FA.
3. Cómo se desarrolla: metodología, ramas, revisiones de código, ambientes (desarrollo/pruebas/producción), despliegue.
4. Dónde se guardan las credenciales, claves de firma de apps y llaves SSH.
5. Respaldos de código, bases de datos y documentos: dónde, cada cuánto, si alguna vez se probó restaurar.
6. Qué datos de clientes y de usuarios finales se manejan; datasets de visión computacional y su origen.
7. Contratos con clientes: cláusulas de propiedad intelectual, confidencialidad, soporte y garantía.
8. Incidentes pasados (cuentas robadas, caídas, pérdida de información) y cómo se resolvieron.
9. Situación de `ketanolab.com` y del servidor `164.68.97.107` (ver §5).
10. Rol actual de Pedro Terán y titularidad de la cuenta GitHub.

## 9. Fuentes

- Los Tiempos, «Lanzan SimiDic, el primer diccionario aymara, quechua y guaraní para Android», 15/10/2012: <https://www.lostiempos.com/tendencias/bienestar/20121015/lanzan-simidic-primer-diccionario-aymara-quechua-guarani-android>
- GitHub KetanoLab (perfil y repositorios): <https://github.com/KetanoLab> · <https://github.com/KetanoLab/Nusimi-android> · <https://github.com/KetanoLab/cacho-de-cacho>
- NuSimi en F-Droid (Fossdroid): <https://fossdroid.com/a/nusimi.html>
- SimiDic en SourceForge: <https://sourceforge.net/projects/simidic/> · Apptopia: <https://apptopia.com/google-play/app/com.ketanolab.simidic/about>
- Facebook Ketano Lab: <https://www.facebook.com/KetanoLab>
- Directorio empresarial de Bolivia (ficha de Ketanolab S.R.L., dirección y servicios): <https://www.directorio.com.bo>
- Perfil profesional público de un ex jefe de proyectos de KETANOLAB SRL (2019): LinkedIn
- Consulta DNS y cabeceras HTTP de `ketanolab.com`, 18/11/2026 (equipo auditor)
- Información proporcionada por el equipo sobre el propietario, servicios actuales y proyectos conjuntos (18/11/2026): rol en la UMSA, docencia, proyectos de monitoreo de obras y aplicación para ferias
- UMSA, documentos públicos del DIPGIS y del Centro de Innovación y Desarrollo Empresarial: <https://dipgis.umsa.bo> · <https://www.umsa.bo/documents/228759/345812/CIDE.pdf>
- Manual de desarrollo seguro derivado de este contexto: [Manual de desarrollo seguro](03_MANUAL_DESARROLLO_SEGURO_KETANOLAB.md)
