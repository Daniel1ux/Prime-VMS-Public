[English](README.md) · [Português](README.pt-BR.md) · Español

# NexaVMS

Software de gestión de video (VMS) gratuito para cámaras IP y CCTV en Windows. Vea en
vivo, grabe las 24 horas, reproduzca y exporte video de cualquier cámara ONVIF o RTSP.

El núcleo del producto es gratuito, sin licencia por cámara. Los módulos avanzados
están disponibles en planes accesibles.

[Descargar](https://github.com/Daniel1ux/Prime-VMS-Public/releases/latest) ·
[Sitio web](https://daniel1ux.github.io/Prime-VMS-Public/es/) ·
[Notas de versión](https://github.com/Daniel1ux/Prime-VMS-Public/releases)

[![Versión más reciente](https://img.shields.io/github/v/release/Daniel1ux/Prime-VMS-Public?label=versi%C3%B3n&color=c5e82e&labelColor=0a1626)](https://github.com/Daniel1ux/Prime-VMS-Public/releases/latest)
![Windows 10 y 11](https://img.shields.io/badge/Windows-10%20%7C%2011-0b2545)

## Descripción general

NexaVMS tiene cuatro componentes, que pueden estar en una sola computadora o
distribuidos en la red:

| Componente | Función |
|---|---|
| System Manager | Servidor central. Administra cámaras, usuarios, permisos y datos del sitio. Se ejecuta como servicio de Windows. |
| Storage | Servidor de grabación. Graba las cámaras en disco, aplica la retención y entrega video en vivo y grabado. Se ejecuta como servicio de Windows. |
| Workstation | Aplicación del operador. Mosaicos en vivo, reproducción con línea de tiempo y exportación. |
| Servidor de IA | Analiza el video de las cámaras para los módulos de IA y envía los eventos al System Manager. Va en la misma computadora o en computadoras propias, una o varias. Se ejecuta como servicio de Windows. |

Todos vienen en un solo instalador. Las aplicaciones están disponibles en español,
inglés y portugués.

## Funciones

Incluidas en la versión gratuita:

- Descubrimiento automático de cámaras ONVIF y de la ruta del video RTSP. Solo se
  necesitan el usuario y la contraseña de la cámara. Patrones de ruta integrados para
  Hikvision, Annke, Dahua, Intelbras, Axis y Reolink.
- Búsqueda de cámaras en la red y registro por lotes: agregue varias cámaras a la vez, con
  la lectura de las funciones ONVIF de cada una.
- Grabación continua en disco en MP4 segmentado, sin recodificar, con retención por
  días.
- Video en vivo en mosaicos de hasta 4×4, pantalla completa, varios monitores y
  videowall, con decodificación acelerada por hardware.
- Reproducción con línea de tiempo de 24 horas, zoom, marcadores y reproducción
  sincronizada de varias cámaras.
- Exportación de imágenes y videos con marca de agua (logotipo, fecha y hora).
- Usuarios con perfiles de administrador, supervisor y operador, aplicados por el
  servidor.
- Instalación en una sola computadora o distribuida, con varios servidores de
  grabación.
- Actualización desde la propia aplicación.

## Módulos pagos

| Módulo | Disponibilidad |
|---|---|
| Analíticas de video con IA: conteo de personas, reconocimiento facial, lectura de placas Mercosur, búsqueda inteligente y protección perimetral, cada una con modo de prueba con videos reales (AI Engine) | Disponible, gratuito en la fase de pruebas |
| Otras analíticas: merodeo, detección de filas, fuego y humo, EPP, objetos abandonados | En desarrollo |
| Prime Cloud: acceso remoto y móvil sin abrir puertos | Próximamente |
| Alta disponibilidad: servidor central redundante | Próximamente |

Los planes están pensados para proyectos pequeños y medianos.
[Contacte a Prime Building Technology](https://primebr.com.br/) para una cotización.

## Requisitos

- Windows 10 o Windows 11, 64 bits.
- Permisos de administrador para instalar y actualizar.
- Cámaras IP con ONVIF o RTSP en la misma red.
- Para el Storage, un disco con espacio para la retención que necesite. Las
  grabaciones se guardan fuera de la carpeta del programa.
- Para la Workstation, se recomienda una tarjeta de video con decodificación por
  hardware en mosaicos grandes.
- Para el servidor de IA, al menos 8 GB de memoria y 10 GB libres. Una tarjeta de video
  compatible atiende muchas más cámaras; sin ella, el análisis corre en el procesador.

## Instalación

1. Descargue `PrimeVMS-Setup-X.Y.Z.exe` de la
   [versión más reciente](https://github.com/Daniel1ux/Prime-VMS-Public/releases/latest).
2. Ejecute el instalador, elija el idioma y acepte el aviso de administrador.
   El instalador todavía no tiene firma de código. Si aparece Windows SmartScreen,
   haga clic en **Más información** y luego en **Ejecutar de todas formas**.
3. Elija cómo va a participar esta computadora:
   - **Todo en este equipo.** Instala System Manager, Storage y Workstation ya
     conectados entre sí. Adecuado para hasta unas 16 cámaras, sin redundancia de
     grabación. El servidor de IA se puede incluir en la misma instalación.
   - **Solo el servidor de IA.** Para una computadora que solo analiza video para un
     Nexa VMS que ya existe. No instala System Manager, Storage ni Workstation. El
     instalador revisa el hardware, pide el nombre del servidor, la dirección que usará el
     System Manager y la contraseña, y puede conectarlo al System Manager en ese momento
     o dejarlo para después.
   - **Elegir las partes.** Marque las funciones de esta computadora: System Manager en
     un servidor dedicado, Storage en uno o más servidores de grabación, Workstation en
     las computadoras de operación y servidor de IA.
4. Abra la Workstation o la Consola del System Manager. En el servidor de IA, la
   aplicación Servidor de IA NexaVMS se abre al final.

Inicie sesión con el usuario `admin` y la contraseña `admin` y luego cambie la
contraseña. En el servidor de IA, el usuario es `admin` y la contraseña es la elegida en
el instalador.

Los modelos de IA (unos 600 MB) se descargan en segundo plano después de la instalación.
El avance aparece en la aplicación del servidor de IA, en Modelos.

El idioma elegido en el instalador pasa a ser el predeterminado de las aplicaciones.
Cada usuario puede cambiarlo con el selector de idioma en la pantalla de inicio de
sesión o en la barra lateral.

### Puertos de red

| Puerto (TCP) | Servicio |
|---|---|
| 58100 | System Manager |
| 58200 | Storage |
| 58300 | Servidor de IA |

El instalador agrega estas reglas al Firewall de Windows. En una instalación
distribuida, asegúrese de que la red permita estos puertos entre los servidores y las
Workstations.

## Nexa Player

La exportación protegida (`.pvx`) va cifrada con contraseña y tiene verificación de integridad, por
eso no se abre en reproductores de video comunes. Para verla, use Nexa Player, gratuito, para
Windows. Abre paquetes `.pvx`, carpetas exportadas y archivos MP4, y muestra si cada video está
íntegro y firmado.

- [Descargar Nexa Player (zip, sin instalar)](https://github.com/Daniel1ux/Prime-VMS-Public/releases/latest/download/NexaPlayer-win-x64.zip)
- [Descargar el instalador de Nexa Player](https://github.com/Daniel1ux/Prime-VMS-Public/releases/latest/download/NexaPlayer-Setup.exe)

1. Descargue `NexaPlayer-win-x64.zip`, haga clic derecho sobre él y elija **Extraer todo**.
2. Abra `PrimePlayer.exe` en la carpeta extraída. Si aparece el aviso de SmartScreen, haga clic en
   **Más información** y luego en **Ejecutar de todas formas**.
3. Haga clic en **Abrir archivo**, elija el archivo `.pvx` y escriba la contraseña. La lista
   muestra si cada video está íntegro y firmado.

La contraseña no se guarda en el paquete. Pídala a quien hizo la exportación. Los enlaces siempre
llevan a la versión más reciente.

## Actualizaciones

A partir de la versión 1.0.4, NexaVMS se actualiza desde las propias aplicaciones.

1. En la Workstation, la Consola del System Manager o la Consola del Storage, haga clic
   en **Buscar actualizaciones** en la barra lateral o en la pantalla de inicio de
   sesión. Las aplicaciones también verifican solas y avisan cuando hay una versión
   nueva.
2. Lea las notas de la versión y haga clic en **Actualizar ahora**. Se necesitan
   permisos de administrador.
3. NexaVMS actualiza todos los componentes instalados en la computadora. Detiene los
   servicios, cierra las aplicaciones, instala la nueva versión, inicia los servicios,
   verifica que respondan y vuelve a abrir la aplicación. El proceso tarda alrededor de
   un minuto.

Cómo funciona la actualización:

- Solo se descargan los archivos modificados, normalmente alrededor de 1 MB.
- Cada versión tiene firma digital. Los archivos alterados o dañados se rechazan antes
  de cualquier cambio.
- Si un servicio no inicia, o si se corta la energía durante la actualización, la
  versión anterior se restaura automáticamente.
- La configuración, las cámaras, los usuarios y las grabaciones se conservan. La base
  de datos se actualiza automáticamente.

La grabación se pausa unos segundos durante la actualización. En sitios con grabación
crítica, actualice en horarios de menor actividad.

### Actualización sin internet

Copie los archivos de actualización de una versión (`update-manifest.json`,
`update-manifest.json.sig` y los archivos `pack-*.zip`) a una carpeta y ejecute como
administrador:

```
"C:\Program Files\Prime VMS\Updater\PrimeVMS Updater.exe" --apply --source folder:D:\actualizacion-primevms
```

## Versiones

| Versión | Fecha | Instalador | Actualización en la app |
|---|---|---|---|
| [2.22.1](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.22.1) (recomendada) | 06/11/2026 | `PrimeVMS-Setup-2.22.1.exe`, 643 MB | Sí |
| [2.22.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.22.0) | 06/11/2026 | `PrimeVMS-Setup-2.22.0.exe`, 643 MB | Sí |
| [2.21.2](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.21.2) | 05/11/2026 | `PrimeVMS-Setup-2.21.2.exe`, 644 MB | Sí |

Solo se publican las tres últimas versiones. Cualquier instalación anterior se actualiza
directamente a la más reciente desde la aplicación. Si usa la versión 1.4.0 o anterior,
instale la más reciente con el instalador una vez; sus datos se conservan.

A partir de la 2.5.0, la instalación debe activarse con una cuenta Nexa VMS, creada en
[nexavms.io](https://nexavms.io), desde la Consola del System Manager. Sin activación, NexaVMS no
graba ni muestra video. La primera activación incluye 30 días de prueba del Professional.

### Verificar la descarga

```powershell
Get-FileHash .\PrimeVMS-Setup-2.22.1.exe -Algorithm SHA256
```

| Archivo | SHA-256 |
|---|---|
| `PrimeVMS-Setup-2.22.1.exe` | `A7F25D25DA6223A2F257EFE3D0869686459014B9F50EFAC091CF847F6A00B177` |
| `PrimeVMS-Setup-2.22.0.exe` | `0F990FB52186E6821A20FF9DD66C6DC4CD95FBD397D84720C90037AB88A767F4` |
| `PrimeVMS-Setup-2.21.2.exe` | `4ACAF397A557D487D7EC6643099803D4ED8E6B4E082DD87331F700FDF7498DE2` |

## Preguntas frecuentes

**¿NexaVMS es gratuito?**
Sí. Video en vivo, grabación, reproducción, exportación, usuarios, instalación
distribuida y actualizaciones son gratuitos, sin licencia por cámara. Las analíticas
con IA también son gratuitas en la fase de pruebas actual. Prime Cloud y la alta
disponibilidad serán módulos pagos.

**¿Qué cámaras son compatibles?**
Cualquier cámara IP con ONVIF o RTSP. NexaVMS encuentra las cámaras ONVIF en la red y
detecta la ruta del video.

**¿Reemplaza a un NVR?**
NexaVMS graba las cámaras IP directamente en una PC o servidor Windows, con retención
por días. También puede grabar desde grabadores existentes que ofrecen RTSP.

**¿Cuántas cámaras puedo agregar?**
La versión gratuita no tiene límite por cámara. El límite práctico depende del hardware
y de la red. En sitios más grandes, use la instalación distribuida con varios
servidores de grabación.

**¿Qué idiomas hay disponibles?**
Español, inglés y portugués (Brasil), en las aplicaciones, el instalador y las notas de
versión.

## Desinstalación

Abra **Configuración > Aplicaciones > NexaVMS > Desinstalar** (PrimeVMS en las instalaciones anteriores a la 2.4.0) o use el acceso directo
"Desinstalar NexaVMS" del menú Inicio. Se eliminan los servicios y las reglas de
firewall. La base de datos y las grabaciones en `C:\ProgramData\Prime VMS` y en la
carpeta de grabación elegida no se borran.

## Licencia y soporte

Copyright © 2026 Prime Building Technology. Todos los derechos reservados.

El núcleo VMS (System Manager, Storage y Workstation) es de uso gratuito para la
gestión de video del sitio del licenciatario. Los módulos de nube y alta
disponibilidad requieren licencia comercial; los módulos de IA son gratuitos en la fase
de pruebas. El operador es responsable de cumplir la
legislación aplicable, incluidas las leyes de protección de datos, al captar, grabar y
tratar imágenes.

NexaVMS incluye componentes de terceros bajo sus propias licencias, como
[FFmpeg](https://ffmpeg.org/) y [go2rtc](https://github.com/AlexxIT/go2rtc).

Soporte: [primebr.com.br](https://primebr.com.br/)
