# D3 · Infraestructura, nube y accesos

**Responsable:** Alex David Tola Julián

## Por qué este dominio

El software de Ketanolab corre en servidores, dominios y servicios en la nube, y se administra con cuentas. Ya hay indicios públicos de problemas (página por defecto de Apache, certificado de otro dominio, versión del servidor visible). Una sola cuenta sin 2FA o un servidor olvidado basta para un incidente grave.

## Controles a evaluar (ISO/IEC 27002:2022)

| Control | Pregunta de auditoría | Papel de trabajo |
|---|---|---|
| 8.9 · 8.20 Configuración y redes | ¿Qué corre en `ketanolab.com` / `164.68.97.107`? ¿Servicios por defecto, puertos abiertos innecesarios? | PT-D3-01 |
| 8.24 Criptografía | ¿Certificados TLS válidos y del dominio propio? ¿Renovación automática? | PT-D3-01 |
| 8.8 Vulnerabilidades técnicas | ¿Sistema operativo y servidor actualizados? | PT-D3-01 |
| 5.15–5.18 · 8.2 · 8.5 Accesos | ¿Cuentas personales o de empresa? ¿2FA? ¿Gestor de contraseñas? ¿Llaves SSH? ¿Quién es administrador? | PT-D3-02 |
| 5.23 Servicios en la nube | ¿Qué proveedores (VPS, Firebase, Google Play, dominios)? ¿Quién administra cada cuenta? | PT-D3-03 |
| 8.15 · 8.16 Registros y monitoreo | ¿Se guardan y revisan *logs*? | PT-D3-03 |

## Punto de partida

Observaciones O-01 a O-04 del [Contexto §5](../../docs/01_CONTEXTO_KETANOLAB.md): documentarlas como `PT-D3-01` con sus capturas, y confirmarlas con Roger.

**Importante:** solo revisión pasiva o con Roger mostrando la configuración. Nada de escaneos de puertos ni pruebas sin autorización escrita específica.

## Entregables de mejora a tu cargo (en `04_ENTREGABLES/`)

- P2 · Política de control de accesos y contraseñas
- P6 · Política de uso aceptable y trabajo remoto
- P7 · Política de proveedores y servicios en la nube

## Archivos esperados

- [ ] `PT-D3-01_SERVIDOR_DOMINIO_TLS.md`
- [ ] `PT-D3-02_CUENTAS_Y_ACCESOS.md`
- [ ] `PT-D3-03_NUBE_Y_REGISTROS.md`
- [ ] `evidencias/`

Referencias: [Propuesta §4.1](../../docs/02_PROPUESTA_AUDITORIA_KETANOLAB.md) · [Manual §7.7](../../docs/03_MANUAL_DESARROLLO_SEGURO_KETANOLAB.md)
