---
title: "KETANOLAB · Manual de desarrollo seguro de software"
date: 2026-11-18
version: "1.0 (borrador para revisión)"
tags:
  - auditoria/ketanolab
  - auditoria/entregable
  - seguridad/desarrollo-seguro
---

# Manual de desarrollo seguro de software

**Ketanolab S.R.L. · Código KL-MDS-01 · Versión 1.0 (borrador)**

| Control del documento | |
|---|---|
| Elaborado por | Equipo de auditoría de sistemas (6 integrantes), Auditoría de Sistemas, Semestre II-2026 |
| Propuesto a | Roger Dante Prado Lafuente, propietario de Ketanolab S.R.L. |
| Aprobado por | *(firma del propietario al adoptarlo)* |
| Base normativa | ISO/IEC 27001:2022 (Anexo A 8.25–8.33), ISO/IEC 27002:2022, ISO/IEC 27005:2022, ISO/IEC 27034, OWASP (Top 10, ASVS, MASVS), NIST SP 800-218 (SSDF) |
| Revisión | Anual o después de un incidente grave |
| Documentos relacionados | [Contexto](01_CONTEXTO_KETANOLAB.md) · [Propuesta de auditoría](02_PROPUESTA_AUDITORIA_KETANOLAB.md) |

---

## 1. Para qué sirve este manual

Este manual reúne, en un solo lugar y en lenguaje práctico, **qué debe cumplir un software para considerarse desarrollado de forma segura**. Se basa en la familia ISO/IEC 27000 y en guías técnicas reconocidas. Tiene tres usos:

| Uso | Quién | Cómo usarlo |
|---|---|---|
| **Desarrollar** | Ketanolab y sus equipos de proyecto | Aplicar las reglas de la sección 7 en cada fase y cerrar cada entrega con el checklist de la sección 11 |
| **Asesorar** | Roger como asesor de emprendimientos (UMSA y otros) | Usar el diagnóstico rápido de la sección 10 y los niveles de la sección 9 para decirle a cada emprendimiento qué es lo mínimo según su etapa |
| **Exigir y auditar** | Ketanolab frente a proveedores, *freelancers* o clientes | Pedir el cumplimiento del nivel que corresponda (sección 9) y verificarlo con el checklist |

Regla de oro: **la seguridad se decide desde la idea, no al final.** Corregir una falla en diseño cuesta poco; corregirla después de una filtración puede costar el negocio.

## 2. Alcance

Aplica a todo software que Ketanolab desarrolle, mantenga o asesore: aplicaciones web y APIs, aplicaciones móviles, *backends* en servicios en la nube (Firebase, Supabase y similares), sistemas de visión computacional e IA, y la infraestructura que los soporta (servidores, dominios, repositorios, cuentas de tiendas de apps).

## 3. Marco normativo

| Referencia | Qué aporta a este manual |
|---|---|
| **ISO/IEC 27001:2022** | Requisito de establecer reglas de desarrollo seguro como parte del SGSI. Controles del Anexo A 8.25 a 8.33 |
| **ISO/IEC 27002:2022** | Guía de cada control: 8.4 acceso al código fuente, 8.25 ciclo de vida seguro, 8.26 requisitos de seguridad, 8.27 arquitectura segura, 8.28 codificación segura, 8.29 pruebas, 8.30 desarrollo externalizado, 8.31 separación de ambientes, 8.32 gestión de cambios, 8.33 información de prueba |
| **ISO/IEC 27005:2022** | Cómo identificar y valorar riesgos (usado en el modelo de amenazas) |
| **ISO/IEC 27034** | Seguridad de aplicaciones: controles de seguridad integrados al ciclo de vida |
| **ISO/IEC 27017 / 27018** | Seguridad en la nube y protección de datos personales en la nube |
| **ISO/IEC 27701** | Gestión de la privacidad (datos personales, imágenes de personas) |
| **ISO/IEC 42001:2023** | Gestión de sistemas de IA (proyectos de visión computacional) |
| **OWASP Top 10** (edición 2025) | Los 10 riesgos más críticos en aplicaciones web |
| **OWASP ASVS 5.0** | Lista verificable de requisitos de seguridad para aplicaciones web y APIs |
| **OWASP MASVS / MASTG** | Requisitos y pruebas de seguridad para apps móviles |
| **NIST SP 800-218 (SSDF)** | Prácticas de desarrollo seguro y cadena de suministro de software |
| Normativa boliviana | CPE arts. 21 y 130 (privacidad), Ley 164 y D.S. 1793 (TIC y documentos electrónicos), Ley 1322 (derecho de autor sobre el software) |

## 4. Por qué ahora: incidentes recientes y lo que enseñan

Los incidentes de 2026 muestran que la mayoría de los ataques **no son sofisticados**: aprovechan configuraciones por defecto, accesos sin control, credenciales robadas y dependencias comprometidas.

| Incidente (2026) | Qué pasó | Lección | Regla del manual |
|---|---|---|---|
| **Filtración de datos de entidades del Estado boliviano** (15–17 nov 2026) | El Gobierno confirmó ataques informáticos para filtrar datos de instituciones del Órgano Ejecutivo; se reportaron accesos no autorizados al sistema Sinacom de Senarecom y un incidente en la Cancillería. El colectivo Hacking Bolivia denunció la venta de datos en la *dark web* y afirma que al menos 30 instituciones públicas fueron atacadas (cifra no confirmada oficialmente) | Los sistemas que desarrollamos para clientes, incluidos los públicos, son blanco real en Bolivia. Sin registros (*logs*) ni respaldos no se puede saber qué se robó ni recuperarse | R-42 a R-46, sección 13 |
| **Ataques a la cadena de suministro en npm** (Axios, marzo 2026; gusano «Shai-Hulud», abril–mayo; otras campañas durante el año) | Atacantes tomaron cuentas de mantenedores o *pipelines* de CI/CD y publicaron versiones maliciosas de librerías muy usadas, que roban credenciales al instalarse | Instalar una dependencia equivale a ejecutar código de un tercero. Hay que fijar versiones, revisar actualizaciones y proteger las cuentas y *tokens* de publicación | R-20 a R-25 |
| **Apps hechas con IA («vibe coding») que exponen datos** (Moltbook, ene 2026; aplicaciones en Lovable y otras plataformas) | Bases de datos en Supabase o Firebase **sin reglas de acceso** (por ejemplo, sin *Row Level Security*) dejaron expuestos *tokens*, correos y datos de miles de usuarios. El código generado por IA omitía controles de autenticación | La IA acelera el desarrollo, pero no garantiza seguridad. Todo código generado se revisa, y todo *backend* como servicio se configura con reglas de acceso por usuario | R-10 a R-12, R-60 a R-63 |
| **Caídas de servicios en la nube** (19 caídas importantes de AWS, Azure, Google Cloud y Cloudflare en 2026 según un registro independiente) | Regiones o servicios enteros fuera de línea por horas | Depender de un único proveedor sin plan B ni respaldos externos es un riesgo de continuidad | R-44, R-45 |
| **Observaciones de la auditoría a Ketanolab** (18 nov 2026) | Servidor con página por defecto de Apache, certificado TLS de otro dominio, versión del servidor visible, código en una cuenta personal de GitHub, archivo `local.properties` versionado | Los mismos errores básicos que aprovechan los atacantes también están presentes en casa | R-04, R-26 a R-28, R-37, R-38, R-49 |

> Las cifras de prensa y de investigadores se citan como referencia; deben verificarse en las fuentes primarias (sección 15).

## 5. Principios

1. **Seguro por diseño:** la seguridad es un requisito más, igual que la funcionalidad.
2. **Mínimo privilegio:** cada usuario, servicio y persona del equipo tiene solo el acceso que necesita.
3. **Negar por defecto:** todo lo que no está permitido explícitamente está prohibido.
4. **Nunca confiar en la entrada:** todo dato que viene del usuario, de otra app o de la red se valida en el servidor.
5. **Defensa en profundidad:** más de una barrera; si una falla, otra contiene el daño.
6. **Minimizar datos:** no recolectar ni guardar datos que el negocio no necesita.
7. **Secretos fuera del código:** ninguna contraseña, clave o *token* en el repositorio.
8. **Todo cambio es trazable:** quién cambió qué, cuándo y por qué.
9. **Fallar de forma segura:** un error no debe mostrar información interna ni abrir accesos.
10. **Proporcionalidad:** los controles crecen con el riesgo del proyecto (sección 9).

## 6. Roles mínimos

En un equipo pequeño una misma persona puede tener varios roles, pero **quien escribe un cambio no debe ser el único que lo aprueba**.

| Rol | Responsabilidad |
|---|---|
| Responsable del proyecto | Define el nivel de seguridad (sección 9), aprueba excepciones y la entrega |
| Desarrollador | Aplica las reglas de este manual y el checklist de la sección 11 |
| Revisor | Revisa el código de otro antes de integrarlo a la rama principal |
| Responsable de cuentas | Custodia las cuentas de la empresa (repositorios, nube, dominios, tiendas), el 2FA y los respaldos |

## 7. Reglas por fase del ciclo de vida

Cada regla tiene un código (R-xx) para poder citarla en revisiones, auditorías y contratos. **[M]** = obligatoria en todo proyecto; **[R]** = recomendada, obligatoria desde el nivel 2 o 3 (sección 9).

### 7.0 Idea y modelo de negocio · ISO 27002 5.8, 5.34

| Código | Regla |
|---|---|
| R-01 [M] | Identificar desde el lienzo del modelo de negocio **qué datos** maneja el producto (personales, financieros, de salud, imágenes de personas, ubicación) y **qué pasaría si se filtran**, se alteran o no están disponibles |
| R-02 [M] | Aplicar minimización: si un dato no es necesario para generar valor, no se recolecta |
| R-03 [R] | Incluir el costo de seguridad (hosting adecuado, respaldos, revisiones) en el presupuesto y en la cotización al cliente |
| R-04 [M] | Registrar cuentas, dominios y repositorios **a nombre de la empresa o del cliente**, nunca solo en una cuenta personal; documentar quién es el dueño de cada uno |

### 7.1 Requisitos · ISO 27002 8.26

| Código | Regla |
|---|---|
| R-05 [M] | Cada proyecto define requisitos de seguridad junto a los funcionales: autenticación, roles y permisos, datos sensibles, registros, respaldos, disponibilidad esperada |
| R-06 [R] | Tomar como base los requisitos del nivel 1 de OWASP ASVS (web) o MASVS-L1 (móvil) y elegir los que aplican |
| R-07 [M] | Si se manejan datos personales: definir el consentimiento, la finalidad, el tiempo de conservación y cómo se eliminan |

### 7.2 Diseño y arquitectura · ISO 27002 8.27, 5.8

| Código | Regla |
|---|---|
| R-08 [M] | Hacer un **modelo de amenazas de una página** (Anexo B) antes de programar: qué se protege, quién podría atacar, por dónde y qué control lo evita. Usar STRIDE como guía |
| R-09 [M] | Separar ambientes: desarrollo, pruebas y producción con datos y credenciales distintos (ISO 27002 8.31) |
| R-10 [M] | La autorización se verifica **en el servidor o en las reglas de la base de datos**, nunca solo en la interfaz o en la app móvil |
| R-11 [M] | Cada consulta a datos verifica que el registro pertenece al usuario o a su organización (evita el acceso a datos ajenos cambiando un ID, falla n.º 1 de OWASP) |
| R-12 [R] | Preferir servicios gestionados con buena reputación para autenticación y pagos, en lugar de construirlos desde cero |

### 7.3 Codificación segura · ISO 27002 8.28

| Código | Regla |
|---|---|
| R-13 [M] | Validar toda entrada en el servidor (tipo, longitud, formato, rango) con listas de valores permitidos |
| R-14 [M] | Usar consultas parametrizadas u ORM; nunca concatenar texto del usuario en SQL, comandos del sistema o rutas de archivos |
| R-15 [M] | Codificar la salida según el contexto (HTML, JavaScript, URL) para evitar XSS; usar las protecciones del *framework* |
| R-16 [M] | Contraseñas almacenadas solo con algoritmos de *hash* para contraseñas (Argon2id, bcrypt o scrypt). Nunca MD5, SHA-1 o cifrado reversible |
| R-17 [M] | No inventar criptografía: usar librerías estándar, TLS 1.2 o superior y algoritmos actuales (AES-GCM, ChaCha20) (ISO 27002 8.24) |
| R-18 [M] | Los mensajes de error al usuario son genéricos; el detalle técnico va solo al registro interno |
| R-19 [M] | **Todo código generado por IA** (Copilot, ChatGPT, Claude, Cursor, Lovable u otros) se revisa con el mismo rigor que el de un desarrollador nuevo. No pegar en asistentes de IA código o datos confidenciales del cliente sin autorización |

### 7.4 Dependencias y cadena de suministro · ISO 27002 8.8, 8.30, 5.21

| Código | Regla |
|---|---|
| R-20 [M] | Usar archivos de bloqueo (`package-lock.json`, `poetry.lock`, `gradle.lockfile`) y versionarlos; instalar en CI con `npm ci` o equivalente |
| R-21 [M] | Activar alertas automáticas de vulnerabilidades en dependencias (Dependabot o Renovate) y atender las críticas en 7 días como máximo |
| R-22 [R] | No actualizar a una versión publicada hace menos de unos días, salvo parche de seguridad; revisar las notas de cambio |
| R-23 [R] | Desactivar o revisar *scripts* de instalación de paquetes (`npm config set ignore-scripts true` cuando sea posible) |
| R-24 [M] | Antes de agregar una librería: verificar que esté mantenida, que sea popular y que el nombre sea el correcto (evitar paquetes falsos con nombres parecidos) |
| R-25 [R] | Generar un inventario de componentes (SBOM) en proyectos de nivel 3 |

### 7.5 Secretos, cuentas y código fuente · ISO 27002 5.17, 8.4, 8.5

| Código | Regla |
|---|---|
| R-26 [M] | Ningún secreto en el repositorio: usar variables de entorno o un gestor de secretos. Ignorar con `.gitignore` los archivos `.env`, `local.properties`, `google-services.json` con claves privadas, `*.jks` y `*.keystore` |
| R-27 [M] | Activar detección de secretos (GitHub *secret scanning* o *gitleaks*) en todos los repositorios. Si un secreto se filtró, **se rota de inmediato**: borrarlo del historial no es suficiente |
| R-28 [M] | Repositorios en una **organización** de GitHub o GitLab de la empresa, con 2FA obligatorio para todos los miembros y permisos por equipo |
| R-29 [M] | Proteger la rama principal: cambios solo mediante *pull request* con al menos una revisión y pruebas automáticas aprobadas (ISO 27002 8.32) |
| R-30 [M] | Usar un gestor de contraseñas de equipo (Bitwarden, 1Password o similar). Prohibido compartir contraseñas por WhatsApp o correo |
| R-31 [M] | Al salir una persona del proyecto, retirar todos sus accesos el mismo día (ISO 27002 5.18) |

### 7.6 Pruebas de seguridad · ISO 27002 8.29, 8.33

| Código | Regla |
|---|---|
| R-32 [M] | Análisis estático (SAST) automático en cada *pull request* (Semgrep, CodeQL, SonarQube Community) |
| R-33 [R] | Análisis dinámico (DAST) antes de cada versión mayor con OWASP ZAP sobre el ambiente de pruebas |
| R-34 [M] | Probar manualmente los casos de abuso del modelo de amenazas: acceder a datos de otro usuario, subir un archivo malicioso, repetir peticiones |
| R-35 [M] | No usar datos personales reales en pruebas; si es imprescindible, anonimizarlos (ISO 27002 8.33) |
| R-36 [R] | Apps móviles: analizar el APK/IPA con MobSF antes de publicar |

### 7.7 Despliegue y configuración · ISO 27002 8.9, 8.20, 8.24, 8.31

| Código | Regla |
|---|---|
| R-37 [M] | HTTPS en todo, con certificado válido **del propio dominio** (Let's Encrypt es gratuito) y renovación automática |
| R-38 [M] | Endurecer el servidor: eliminar páginas y servicios por defecto, ocultar versiones (`ServerTokens Prod`, `ServerSignature Off` en Apache), cerrar puertos no usados, acceso SSH solo con llave y sin usuario *root* |
| R-39 [M] | Encabezados de seguridad HTTP: `Strict-Transport-Security`, `Content-Security-Policy`, `X-Content-Type-Options`, `X-Frame-Options` o `frame-ancestors`; CORS restringido a los dominios propios |
| R-40 [M] | Despliegue reproducible y registrado (CI/CD o *script* versionado), nunca editar archivos a mano en producción |
| R-41 [R] | Los *tokens* de CI/CD tienen el mínimo permiso y caducan; preferir credenciales temporales (OIDC) |

### 7.8 Operación: registros, parches, respaldos e incidentes · ISO 27002 8.13, 8.15, 8.16, 5.24–5.30

| Código | Regla |
|---|---|
| R-42 [M] | Registrar eventos de seguridad: inicios de sesión (exitosos y fallidos), cambios de permisos, accesos a datos sensibles, errores. Sin contraseñas ni datos personales completos en los registros. Conservar al menos 90 días |
| R-43 [M] | Aplicar parches críticos del sistema operativo, servidor y dependencias en 7 días como máximo |
| R-44 [M] | Respaldos con la **regla 3-2-1** (3 copias, 2 medios, 1 fuera del proveedor principal), cifrados, y **una prueba de restauración por trimestre** |
| R-45 [R] | Definir cuánto tiempo puede estar caído el sistema (RTO) y cuántos datos se pueden perder (RPO), y diseñar respaldos acordes |
| R-46 [M] | Tener a mano el procedimiento de respuesta a incidentes de la sección 13 |

### 7.9 Entrega al cliente y retiro · ISO 27002 5.14, 8.10

| Código | Regla |
|---|---|
| R-47 [M] | Acta de entrega: código, documentación, credenciales (por canal seguro), cuentas transferidas y lista de dependencias |
| R-48 [M] | Al terminar el contrato, eliminar de forma segura los datos del cliente que Ketanolab ya no necesita y dejar constancia |
| R-49 [M] | Al dar de baja un sistema o servidor: apagar, borrar datos, liberar o mantener el dominio para evitar suplantación |

## 8. Guías por tipo de proyecto

### 8.1 Aplicaciones web y APIs (OWASP Top 10 2025 y ASVS)

| Riesgo OWASP Top 10:2025 | Control mínimo |
|---|---|
| A01 Control de acceso roto | R-10, R-11; pruebas de acceso a datos de otro usuario |
| A02 Configuración de seguridad incorrecta | R-38, R-39; sin páginas ni cuentas por defecto |
| A03 Fallas en la cadena de suministro de software | R-20 a R-25 |
| A04 Fallas criptográficas | R-16, R-17, R-37 |
| A05 Inyección | R-13, R-14, R-15 |
| A06 Diseño inseguro | R-08 (modelo de amenazas) |
| A07 Fallas de autenticación | 2FA para administradores, límite de intentos, sesiones que caducan, recuperación de cuenta segura |
| A08 Fallas de integridad de software o datos | Firmar artefactos, verificar origen de actualizaciones, no deserializar datos no confiables |
| A09 Fallas en registros y alertas | R-42 y alertas ante eventos anómalos |
| A10 Manejo incorrecto de condiciones excepcionales | R-18; fallar de forma segura |

*Verificar la redacción final de la edición 2025 en owasp.org/Top10.*

APIs: autenticación en todos los *endpoints*, límite de peticiones (*rate limiting*), no devolver más campos de los necesarios, documentar con OpenAPI y no publicar en producción la documentación interactiva sin protección.

### 8.2 Aplicaciones móviles (OWASP MASVS)

- La app es un cliente **no confiable**: toda regla de negocio y autorización vive en el servidor (R-10).
- Ninguna clave privada ni secreto de servidor dentro del APK/IPA; asumir que cualquiera puede descompilar la app.
- Datos sensibles en el dispositivo solo cifrados (Android Keystore / iOS Keychain; EncryptedSharedPreferences).
- Usar **Play App Signing** y guardar la clave de carga con respaldo y acceso restringido; perderla impide actualizar la app.
- Tráfico solo por HTTPS; `android:usesCleartextTraffic="false"`; `android:allowBackup` desactivado si hay datos sensibles; `debuggable` desactivado en producción.
- Pedir solo los permisos necesarios (cámara, ubicación) y explicar para qué.
- Ofuscar y minimizar en producción (R8/ProGuard).

### 8.3 *Backends* como servicio (Firebase, Supabase y similares)

Es la causa de muchas de las filtraciones de 2026. Reglas específicas:

| Código | Regla |
|---|---|
| R-60 [M] | Supabase: **activar Row Level Security en todas las tablas** y escribir políticas por usuario. La clave `service_role` nunca va en el cliente |
| R-61 [M] | Firebase: reglas de Firestore, Realtime Database y Storage que **nunca** queden en modo de prueba (`allow read, write: if true`); verificar con el simulador de reglas |
| R-62 [M] | Restringir las claves de API del cliente por aplicación, dominio o paquete, y activar App Check o equivalente |
| R-63 [M] | Antes de publicar, probar el acceso a los datos **con la clave pública y sin iniciar sesión**; si se ven datos, el sistema no se publica |

### 8.4 Visión computacional, cámaras e IA (ISO/IEC 27701, 42001)

Aplica directamente al proyecto de **monitoreo de obras para constructoras**.

| Código | Regla |
|---|---|
| R-64 [M] | Informar a los trabajadores y visitantes que hay cámaras (letreros en obra) y acordar con la constructora la finalidad: seguridad industrial y avance de obra, no vigilancia personal fuera de lo acordado |
| R-65 [M] | Cámaras IP: cambiar contraseñas por defecto, actualizar *firmware*, **no exponer RTSP ni paneles de administración a internet**; conectar mediante VPN o túnel cifrado |
| R-66 [M] | Video y *datasets* cifrados en reposo y en tránsito; acceso solo a personas autorizadas; conservación limitada (por ejemplo 30 a 90 días según contrato) y eliminación automática |
| R-67 [R] | Procesar en el dispositivo o en el borde (*edge*) cuando sea posible y enviar solo resultados (conteos, alertas, métricas) en lugar de video completo |
| R-68 [R] | Difuminar rostros en imágenes que se usen para entrenar o mostrar a terceros, salvo que la finalidad lo requiera y esté autorizada |
| R-69 [M] | Documentar el origen y la licencia de cada *dataset* y modelo preentrenado; no usar datos de un cliente para entrenar modelos de otro sin autorización escrita |
| R-70 [R] | Registrar la versión del modelo en producción, sus métricas y sus limitaciones conocidas (falsos positivos y negativos) |

### 8.5 Aplicaciones con registro de usuarios y pagos (ej. aplicación para ferias)

- Datos de expositores y visitantes: recolectar solo lo necesario, con consentimiento explícito para usos de marketing.
- Pagos: usar una pasarela certificada; **nunca almacenar datos de tarjetas**; validar en el servidor el monto y el estado del pago (no confiar en lo que dice la app).
- Códigos QR de acceso o descuentos firmados o de un solo uso para evitar falsificación y reutilización.
- Preparar la infraestructura para picos de tráfico el día de la feria (prueba de carga) y tener un plan si el sistema cae durante el evento.

## 9. Niveles de exigencia según la etapa del emprendimiento

Pensado para que Roger asesore emprendimientos de distinto tamaño sin exigir lo mismo a todos.

| Nivel | Cuándo aplica | Reglas exigidas |
|---|---|---|
| **Nivel 1 · Prototipo / MVP** | Validación con pocos usuarios, sin datos sensibles reales | Todas las **[M]** de 7.0, 7.3 y 7.5; R-37; R-60 a R-63 si usa BaaS; R-44 (al menos respaldo semanal) |
| **Nivel 2 · Producto con clientes** | Usuarios reales, cobros o contratos con empresas | Todas las **[M]** del manual + R-06, R-21, R-33, R-45 |
| **Nivel 3 · Escala o datos sensibles** | Datos de salud, financieros, de menores, video de personas, entidades públicas o más de 10 000 usuarios | Todas las reglas **[M]** y **[R]**; revisión de seguridad externa anual; política de privacidad formal; SBOM |

## 10. Diagnóstico rápido para asesoría de emprendimientos

Veinte preguntas que Roger puede hacer en una sesión de asesoría. Cada «No» es una brecha; el resultado se lleva a la hoja de ruta del emprendimiento.

| N.º | Pregunta | Regla |
|---|---|---|
| 1 | ¿Saben qué datos personales o sensibles maneja su producto y qué pasaría si se filtran? | R-01 |
| 2 | ¿Las cuentas (dominio, nube, repositorio, tiendas) están a nombre de la empresa y no de una sola persona? | R-04 |
| 3 | ¿Todas las cuentas críticas tienen 2FA? | R-28 |
| 4 | ¿Usan un gestor de contraseñas en lugar de compartir claves por chat? | R-30 |
| 5 | ¿Hay algún secreto (clave, contraseña, *token*) en el código o en el repositorio? | R-26, R-27 |
| 6 | ¿Alguien distinto del autor revisa el código antes de publicarlo? | R-29 |
| 7 | ¿Revisan el código generado por IA antes de usarlo? | R-19 |
| 8 | ¿Los permisos se validan en el servidor o en las reglas de la base de datos? | R-10, R-11 |
| 9 | Si usan Firebase o Supabase, ¿probaron leer datos sin iniciar sesión? | R-63 |
| 10 | ¿Tienen alertas de vulnerabilidades en dependencias activadas? | R-21 |
| 11 | ¿Separan desarrollo, pruebas y producción? | R-09 |
| 12 | ¿Usan datos reales en pruebas? | R-35 |
| 13 | ¿Todo el sitio funciona con HTTPS y certificado válido? | R-37 |
| 14 | ¿El servidor tiene parches al día y sin servicios por defecto? | R-38, R-43 |
| 15 | ¿Tienen respaldos fuera del proveedor principal y probaron restaurarlos? | R-44 |
| 16 | ¿Registran inicios de sesión y errores, y alguien los revisa? | R-42 |
| 17 | ¿Saben qué hacer y a quién avisar si los hackean mañana? | R-46 |
| 18 | ¿Quitan accesos el mismo día que alguien deja el equipo? | R-31 |
| 19 | ¿Tienen acuerdos de confidencialidad y de propiedad intelectual con el equipo y los *freelancers*? | ISO 27002 6.6, 5.32 |
| 20 | ¿Su política de privacidad dice lo que realmente hacen con los datos? | R-07 |

**Lectura:** 18–20 «Sí»: bien encaminado · 12–17: atender brechas en 1 a 3 meses · menos de 12: riesgo alto; priorizar preguntas 2, 3, 5, 8, 9 y 15 antes de seguir creciendo.

## 11. Checklist de entrega (*Definition of Done* de seguridad)

Ningún cambio o versión se entrega si falta un punto aplicable:

- [ ] Requisitos de seguridad del proyecto revisados (R-05)
- [ ] Modelo de amenazas actualizado si cambió la arquitectura (R-08)
- [ ] Revisión de código por otra persona, incluido el código generado por IA (R-19, R-29)
- [ ] SAST sin hallazgos críticos ni altos abiertos (R-32)
- [ ] Sin secretos detectados en el repositorio (R-27)
- [ ] Dependencias sin vulnerabilidades críticas conocidas (R-21)
- [ ] Autorización verificada en el servidor; prueba de acceso a datos de otro usuario realizada (R-10, R-11, R-34)
- [ ] Reglas de BaaS verificadas sin sesión iniciada (R-63)
- [ ] HTTPS y encabezados de seguridad activos (R-37, R-39)
- [ ] Registros de seguridad funcionando (R-42)
- [ ] Respaldo previo al despliegue realizado (R-44)
- [ ] Cambio registrado en el historial y desplegado con el procedimiento definido (R-40)

## 12. Herramientas gratuitas recomendadas

| Necesidad | Herramientas |
|---|---|
| Gestor de contraseñas | Bitwarden (plan gratuito u *Organizations*), KeePassXC |
| Detección de secretos | GitHub *secret scanning*, gitleaks, trufflehog |
| Dependencias | Dependabot, Renovate, `npm audit`, OSV-Scanner, Trivy |
| Análisis estático (SAST) | Semgrep, CodeQL, SonarQube Community |
| Análisis dinámico (DAST) | OWASP ZAP |
| Apps móviles | MobSF |
| TLS y encabezados | SSL Labs (ssllabs.com), securityheaders.com, Let's Encrypt |
| Modelo de amenazas | OWASP Threat Dragon, una hoja de cálculo |
| Respaldos | restic, BorgBackup, respaldos gestionados del proveedor + copia externa |

## 13. Respuesta a incidentes (una página)

| Paso | Qué hacer | Tiempo |
|---|---|---|
| 1. Detectar y avisar | Quien detecte algo extraño (acceso desconocido, datos expuestos, servicio caído, mensaje de extorsión) avisa al responsable del proyecto y a Roger | Inmediato |
| 2. Contener | Cambiar contraseñas y rotar claves afectadas, cerrar sesiones activas, aislar el servidor o desactivar la función comprometida. **No borrar evidencia** | Primeras 2 horas |
| 3. Evaluar | Qué sistemas y datos se afectaron, desde cuándo, cuántas personas | Primeras 24 horas |
| 4. Comunicar | Informar al cliente afectado; si hay datos personales de usuarios, acordar con el cliente la comunicación a los afectados. En entidades públicas, coordinar con su unidad de sistemas y el Centro de Gestión de Incidentes Informáticos (CGII) de AGETIC | Primeras 72 horas |
| 5. Recuperar | Restaurar desde respaldo verificado, corregir la causa, monitorear de cerca | Según RTO |
| 6. Aprender | Registrar el incidente (fecha, causa, impacto, acciones) y actualizar este manual si corresponde | Dentro de 2 semanas |

## 14. Cumplimiento y excepciones

- El incumplimiento de una regla **[M]** se registra como hallazgo en la revisión del proyecto.
- Una excepción solo es válida si el responsable del proyecto la aprueba por escrito, con la razón, el riesgo aceptado y la fecha de revisión.
- En contratos con *freelancers* o proveedores se debe citar este manual y el nivel exigido (ISO 27002 8.30).

---

## Anexo A. Correspondencia con ISO/IEC 27002:2022

| Control ISO/IEC 27002:2022 | Reglas del manual |
|---|---|
| 5.8 Seguridad de la información en la gestión de proyectos | R-01, R-03, R-08 |
| 5.17 Información de autenticación | R-16, R-30 |
| 5.18 Derechos de acceso | R-31 |
| 5.24–5.28 Gestión de incidentes | R-46, sección 13 |
| 5.30 Preparación de las TIC para la continuidad | R-44, R-45 |
| 5.32 Derechos de propiedad intelectual | R-04, R-69 |
| 5.34 Privacidad y protección de datos personales | R-02, R-07, R-64 a R-68 |
| 8.4 Acceso al código fuente | R-26 a R-29 |
| 8.5 Autenticación segura | R-28, 8.1 A07 |
| 8.8 Gestión de vulnerabilidades técnicas | R-21, R-43 |
| 8.9 Gestión de la configuración | R-38, R-61, R-62 |
| 8.13 Respaldo de la información | R-44 |
| 8.15 / 8.16 Registro y monitoreo | R-42 |
| 8.24 Uso de criptografía | R-16, R-17, R-37, R-66 |
| 8.25 Ciclo de vida de desarrollo seguro | Todo el capítulo 7 |
| 8.26 Requisitos de seguridad de aplicaciones | R-05 a R-07 |
| 8.27 Arquitectura y principios de ingeniería segura | Sección 5, R-08 a R-12 |
| 8.28 Codificación segura | R-13 a R-19 |
| 8.29 Pruebas de seguridad | R-32 a R-36 |
| 8.30 Desarrollo externalizado | Sección 14, R-24 |
| 8.31 Separación de ambientes | R-09 |
| 8.32 Gestión de cambios | R-29, R-40 |
| 8.33 Información de prueba | R-35 |

## Anexo B. Plantilla de modelo de amenazas (una página)

| Campo | Contenido |
|---|---|
| Proyecto y versión | |
| Qué protegemos | Datos y funciones críticas (ej. video de obra, datos de expositores, pagos) |
| Diagrama | Usuarios → app → API → base de datos → servicios externos (marcar dónde cambia el nivel de confianza) |
| Quién podría atacar | Usuario curioso, competidor, ex empleado, atacante automatizado |

| Amenaza (STRIDE) | Ejemplo en el proyecto | Probabilidad (1–3) | Impacto (1–3) | Riesgo (P×I) | Control | Regla |
|---|---|---|---|---|---|---|
| Suplantación | Robo de cuenta de administrador | | | | 2FA | R-28 |
| Manipulación | Cambiar el monto de un pago desde la app | | | | Validación en servidor | R-10 |
| Repudio | Un usuario niega haber borrado datos | | | | Registros | R-42 |
| Divulgación de información | Base de datos sin reglas de acceso | | | | RLS / reglas | R-60, R-61 |
| Denegación de servicio | Caída el día de la feria | | | | Prueba de carga, límites | Sección 8.5 |
| Elevación de privilegios | Usuario normal accede al panel de administrador | | | | Control de acceso por rol | R-11 |

## 15. Fuentes

**Normas y guías**
- ISO/IEC 27001:2022 y 27002:2022: <https://www.iso.org/standard/27001> · <https://www.iso.org/standard/75652.html>
- OWASP Top 10: <https://owasp.org/Top10/> · OWASP ASVS: <https://owasp.org/www-project-application-security-verification-standard/> · OWASP MASVS: <https://mas.owasp.org/>
- NIST SP 800-218 (SSDF): <https://csrc.nist.gov/pubs/sp/800/218/final>

**Incidentes citados (2026)**
- Los Tiempos, «El Gobierno confirma ciberataque a entidades del Estado», 17/11/2026: <https://www.lostiempos.com/actualidad/seguridad/20261117/gobierno-confirma-ciberataque-entidades-del-estado>
- Opinión, «El gobierno confirma ataque informático para filtración de datos, Hacking Bolivia habla de más de 30 casos», 17/11/2026: <https://www.opinion.com.bo/pais/gobierno-confirma-ataque-informatico-filtracion-datos-hacking-bolivia-habla-mas-30-casos/20261117172057999287.html>
- Infobae, «Denuncian robo y venta de datos de cuatro páginas estatales de Bolivia en la dark web», 17/11/2026: <https://www.infobae.com/america/america-latina/2026/11/17/denuncian-robo-y-venta-de-datos-de-cuatro-paginas-estatales-de-bolivia-en-la-dark-web/>
- Trend Micro, «Axios NPM Package Compromised», 2026: <https://www.trendmicro.com/en_us/research/26/c/axios-npm-package-compromised.html>
- Palo Alto Unit 42, «The npm Threat Landscape», 2026: <https://unit42.paloaltonetworks.com/monitoring-npm-supply-chain-attacks/>
- Cyber Security Agency of Singapore, aviso AD-2026-009 sobre ataque a la cadena de suministro npm: <https://www.csa.gov.sg/alerts-and-advisories/advisories/ad-2026-009/>
- Cloud Security Alliance, «Vibe Coding Security Debt», abril 2026: <https://labs.cloudsecurityalliance.org/research/csa-research-note-ai-codegen-vulnerability-debt-2026>
- The Next Web, caso Lovable y apps expuestas: <https://thenextweb.com/news/lovable-vibe-coding-security-crisis-exposed>
- Control Plane, *Cloud Outage Tracker*: <https://controlplane.com/blog/post/cloud-outage-tracker>
