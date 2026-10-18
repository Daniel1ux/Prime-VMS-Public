<div align="center">

[English](README.md) · [Português](README.pt-BR.md) · **Español**

# PRIME**VMS** — Software VMS gratis para cámaras IP

**Sistema de gestión de video (VMS) gratuito para CCTV: en vivo, grabación 24/7, reproducción y exportación.**
Núcleo gratis **sin licencia por cámara** · módulos avanzados con **planes accesibles**.

[![Versión más reciente](https://img.shields.io/github/v/release/Daniel1ux/Prime-VMS-Public?label=versi%C3%B3n%20m%C3%A1s%20reciente&color=c5e82e&labelColor=0a1626)](https://github.com/Daniel1ux/Prime-VMS-Public/releases/latest)
![Windows 10/11 64-bit](https://img.shields.io/badge/Windows-10%20%2F%2011%20(64--bit)-0b2545)
![ONVIF / RTSP](https://img.shields.io/badge/c%C3%A1maras-ONVIF%20%2F%20RTSP-00e5ff?labelColor=0a1626)
![Idiomas](https://img.shields.io/badge/idiomas-ES%20%C2%B7%20EN%20%C2%B7%20PT-c5e82e?labelColor=0a1626)

### [⬇ Descargar PrimeVMS gratis](https://github.com/Daniel1ux/Prime-VMS-Public/releases/latest) · [🌐 Sitio web](https://daniel1ux.github.io/Prime-VMS-Public/es/)

</div>

**PrimeVMS** es un **sistema de gestión de video (VMS)** profesional para Windows —
**software de CCTV / NVR gratuito** para grabar, ver en vivo y reproducir **cámaras IP**
de cualquier marca compatible con **ONVIF o RTSP**. El núcleo del VMS es de **uso
gratuito**, sin licencia por cámara. Solo paga por lo que aporta valor: **analíticas de
video con IA**, **acceso en la nube** y **alta disponibilidad** — en planes accesibles.

Desarrollado por [Prime Building Technology](https://primebr.com.br/), disponible en
**español, inglés y portugués**.

---

## Por qué PrimeVMS

| | PrimeVMS | VMS tradicional |
|---|---|---|
| Licencia del núcleo | **Gratis** — sin costo por cámara | Pago por cámara / canal |
| Cámaras | **Cualquier cámara ONVIF / RTSP** | A menudo atado a un fabricante |
| Implementación | **Un instalador**: una PC → servidores distribuidos | Productos / ediciones diferentes |
| Actualizaciones | **Un clic dentro de la aplicación**, con reversión automática | Descargar y reinstalar |
| Funciones avanzadas | **Módulos con planes accesibles** — pague solo lo que use | Paquetes caros |
| Idiomas | **Español · English · Português** | Varía |

## Funciones — núcleo gratis

- 📹 **Funciona con sus cámaras** — **descubrimiento ONVIF** automático y detección
  de la ruta RTSP (solo ingrese el usuario y la contraseña de la cámara), con patrones
  RTSP integrados para Hikvision/Annke, Dahua/Intelbras, Axis y Reolink, además de
  ONVIF/RTSP genérico.
- 🔴 **Grabación 24/7** en disco (MP4 segmentado, sin recodificar), con catálogo de
  grabaciones y **retención por días**.
- 🖥️ **En vivo** en mosaicos de hasta 4×4, pantalla completa, **multimonitor** y
  videowall, con **decodificación acelerada por GPU**.
- ⏱️ **Reproducción** con línea de tiempo de 24 h y zoom, **marcadores**, reproducción
  sincronizada de varias cámaras y fecha/hora en el video.
- 📤 **Exportación** de imágenes y videos con **marca de agua antifraude** (logotipo +
  fecha/hora).
- 👥 **Usuarios y perfiles** (administrador, supervisor, operador) aplicados en el
  servidor.
- 🏢 **Crece con usted** — todo en una sola PC, o una instalación **distribuida** con
  servidor central, varios servidores de grabación y varias estaciones de operación.
- 🔄 **Actualización automática** — busque actualizaciones dentro de la aplicación;
  solo se descarga lo que cambió, con firma digital y reversión automática si algo falla.
- 🌐 **Tres idiomas** — español, inglés y portugués (se cambia en la aplicación).

## Módulos pagos — planes accesibles

| Módulo | Estado |
|---|---|
| 🤖 **Analíticas de video con IA** — conteo de personas | ✅ Disponible |
| 🤖 Más analíticas — detección de objetos, cruce de línea/intrusión, merodeo, detección de filas, fuego y humo, EPP, reconocimiento facial, lectura de placas (LPR), objetos abandonados, búsqueda inteligente | 🛠️ En desarrollo |
| ☁️ **Prime Cloud** — acceso remoto y móvil **sin abrir puertos** (sin configurar NAT) | 🔜 Próximamente |
| 🛡️ **Alta disponibilidad** — servidor central redundante (principal/respaldo) | 🔜 Próximamente |

Planes pensados para proyectos pequeños y medianos.
**[Contacte a Prime](https://primebr.com.br/)** para una cotización.

## Qué incluye el instalador

Un solo instalador (`PrimeVMS-Setup-X.Y.Z.exe`) con los tres componentes — usted elige
qué instalar en cada computadora:

| Componente | Qué hace |
|---|---|
| **System Manager** | Servidor central: cámaras, usuarios y permisos, configuración del sitio. Se ejecuta como servicio de Windows. |
| **Storage** | Servidor de grabación: graba las cámaras, guarda y entrega las grabaciones. Se ejecuta como servicio de Windows. |
| **Workstation** | Estación del operador: mosaico en vivo, reproducción con línea de tiempo, exportación. |

Los servicios inician con Windows y se reinician automáticamente si se detienen. No hace
falta instalar .NET ni otro programa.

## Requisitos

- **Windows 10 u 11, 64 bits**.
- Permiso de **administrador** para instalar y actualizar.
- **Cámaras IP con ONVIF/RTSP** en la misma red.
- Para el Storage: un disco con espacio para la retención deseada (las grabaciones
  quedan fuera de la carpeta del programa).
- Para la Workstation: se recomienda una tarjeta de video con decodificación por
  hardware para mosaicos grandes.

## Instalación

1. Descargue `PrimeVMS-Setup-X.Y.Z.exe` de la [versión más reciente](https://github.com/Daniel1ux/Prime-VMS-Public/releases/latest).
2. Ejecútelo, elija el idioma (English, Português o Español) y acepte el aviso de
   administrador.
   > El instalador todavía no tiene firma digital de código. Si Windows muestra
   > *"Windows protegió su PC"*, haga clic en **Más información → Ejecutar de todas formas**.
3. Elija el **modelo de implementación**:
   - **Una sola computadora (todo en esta PC)** — System Manager, Storage y Workstation
     ya conectados. Para proyectos pequeños (hasta unas 16 cámaras), sin redundancia de
     grabación.
   - **Instalación distribuida** — marque la función de cada computadora: System Manager
     en un servidor dedicado, Storage en uno o más servidores de grabación y Workstation
     en las computadoras de operación.
4. Abra la **Workstation** (o la **Consola del System Manager**).

**Primer acceso:** usuario `admin`, contraseña `admin`. **Cambie la contraseña apenas
ingrese.** El idioma elegido en el instalador se convierte en el idioma de las
aplicaciones; cada usuario puede cambiarlo cuando quiera con el selector 🌐 **PT · EN · ES**.

### Puertos de red

| Puerto (TCP) | Servicio |
|---|---|
| **58100** | System Manager |
| **58200** | Storage |

El instalador abre estos puertos en el Firewall de Windows. En instalaciones
distribuidas, asegúrese de que la red los permita entre los servidores y las
Workstations.

## Actualizaciones

Desde la versión **1.0.4**, PrimeVMS se actualiza **desde dentro de las aplicaciones**:

1. En la Workstation, la Consola del System Manager o la Consola del Storage, haga clic
   en **⟳ Buscar actualizaciones** (barra lateral o pantalla de inicio de sesión). Las
   aplicaciones también verifican solas y avisan cuando hay una **nueva versión**.
2. Revise las novedades y haga clic en **Actualizar ahora** (pide permiso de
   administrador).
3. PrimeVMS actualiza **todo lo instalado en esa computadora de una vez**: detiene los
   servicios, cierra las aplicaciones, instala, inicia los servicios, verifica que
   respondan con la nueva versión y vuelve a abrir la aplicación. Tarda alrededor de un
   minuto.

- **Descarga solo lo que cambió** — normalmente alrededor de 1 MB, no el instalador
  completo.
- **Firma digital** — los archivos alterados o dañados se rechazan antes de cualquier
  cambio.
- **Revierte automáticamente** — si un servicio no inicia (o se corta la energía a mitad
  de camino), se restaura la versión anterior.
- **Sus datos se conservan** — configuración, cámaras, usuarios y grabaciones se
  mantienen; la base de datos se actualiza automáticamente.

> La grabación se pausa por unos segundos durante la actualización. En sitios con
> grabación crítica, actualice en horarios de menor actividad.

**Actualización sin internet:** copie los archivos de actualización de una versión
(`update-manifest.json`, `update-manifest.json.sig` y los `pack-*.zip`) a una carpeta y
ejecute, como administrador:

```
"C:\Program Files\Prime VMS\Updater\PrimeVMS Updater.exe" --apply --source folder:D:\actualizacion-primevms
```

## Versiones

| Versión | Fecha | Instalador | Actualización en la app |
|---|---|---|---|
| **[1.0.5](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.0.5)** ⭐ recomendada | 18/10/2026 | `PrimeVMS-Setup-1.0.5.exe` (315 MB) | ✅ Sí |
| [1.0.4](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.0.4) | 18/10/2026 | `PrimeVMS-Setup-1.0.4.exe` (314 MB) | ✅ Sí |
| [1.0.3](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.0.3) | 17/10/2026 | `PrimeVMS-Setup-1.0.3.exe` (314 MB) | ⚠️ Canal antiguo — instale la 1.0.5 |
| [1.0.2](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.0.2) | 06/06/2026 | `PrimeVMS-Setup-1.0.2.exe` (424 MB) | ❌ No |
| [1.0.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.0.0) | 01/06/2026 | `PrimeVMS-Setup-1.0.0.exe` (265 MB) | ❌ No |

Las versiones antiguas se conservan solo como referencia. **Si tiene la 1.0.3 o
anterior**, instale la versión más reciente con el instalador una vez — sus datos se
conservan — y desde entonces actualice dentro de la aplicación. Las novedades de cada
versión están en la página de cada [release](https://github.com/Daniel1ux/Prime-VMS-Public/releases).

### Verificar la descarga (opcional)

```powershell
Get-FileHash .\PrimeVMS-Setup-1.0.5.exe -Algorithm SHA256
```

| Archivo | SHA-256 |
|---|---|
| `PrimeVMS-Setup-1.0.5.exe` | `97BAA1164289F40D35D530A1C9AC7A338E73CAA4197B4BF06473DD2FCCFFF746` |
| `PrimeVMS-Setup-1.0.4.exe` | `405B120D9E5BD56915E8CDE0A65D2D55CFD6A9020EB49992CE4177E1E3D71ED4` |
| `PrimeVMS-Setup-1.0.3.exe` | `97B2E821B3182DF8619003B73626AC234D8DA9A407FBD0434E6BDB804F7ED8D0` |
| `PrimeVMS-Setup-1.0.2.exe` | `8810E256670D7D20E791989B38D56D3878F0A753F126A9B990067A2E84FA65E7` |
| `PrimeVMS-Setup-1.0.0.exe` | `827586BE66C64AF0FD3538A8AE00A052ED8CDBF6890F73FD3EABA8DD9448BF0C` |

## Preguntas frecuentes

**¿PrimeVMS es realmente gratis?**
Sí. El núcleo del VMS — en vivo, grabación, reproducción, exportación, usuarios,
servidores distribuidos y actualizaciones — es gratuito, sin licencia por cámara. Solo
los módulos avanzados (analíticas con IA, Prime Cloud, alta disponibilidad) son pagos,
en planes accesibles.

**¿Qué cámaras son compatibles?**
Cualquier cámara IP con **ONVIF** o **RTSP**, de cualquier fabricante. PrimeVMS
encuentra las cámaras ONVIF en la red y descubre solo la ruta del video.

**¿Reemplaza a un NVR/DVR?**
PrimeVMS graba las cámaras IP directamente en una PC o servidor Windows (NVR por
software), con retención por días, y también funciona junto con grabadores que ya
ofrecen RTSP.

**¿Cuántas cámaras puedo usar?**
No hay límite de licencia por cámara en el núcleo gratis. El límite práctico es el
hardware y la red; para proyectos más grandes, use la instalación distribuida con
varios servidores de grabación.

**¿Qué idiomas hay disponibles?**
Español, inglés y portugués (Brasil) — en las aplicaciones, el instalador y las notas
de versión.

## Desinstalación

**Configuración de Windows → Aplicaciones → PrimeVMS → Desinstalar** (o el acceso
directo "Desinstalar PrimeVMS" del menú Inicio). Se eliminan los servicios y las reglas
de firewall. Los datos (base de datos y grabaciones) quedan en `C:\ProgramData\Prime VMS`
y en la carpeta de grabación elegida, y **no se borran** automáticamente.

## Licencia y soporte

Copyright © 2026 **Prime Building Technology**. Todos los derechos reservados.
El núcleo VMS (System Manager, Storage y Workstation) es de uso libre para la gestión
de video del sitio del licenciatario; los módulos de Inteligencia Artificial, acceso en
la nube y alta disponibilidad requieren licencia comercial. El operador es responsable
de cumplir la legislación aplicable (incluidas las leyes de protección de datos) al
captar, grabar y tratar imágenes.

PrimeVMS incluye componentes de terceros bajo sus propias licencias, como
[FFmpeg](https://ffmpeg.org/) y [go2rtc](https://github.com/AlexxIT/go2rtc).

**Soporte y contacto:** [primebr.com.br](https://primebr.com.br/)
