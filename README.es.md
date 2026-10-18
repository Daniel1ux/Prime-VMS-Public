[English](README.md) · [Português](README.pt-BR.md) · Español

# PrimeVMS

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

PrimeVMS tiene tres componentes, que pueden estar en una sola computadora o
distribuidos en la red:

| Componente | Función |
|---|---|
| System Manager | Servidor central. Administra cámaras, usuarios, permisos y datos del sitio. Se ejecuta como servicio de Windows. |
| Storage | Servidor de grabación. Graba las cámaras en disco, aplica la retención y entrega video en vivo y grabado. Se ejecuta como servicio de Windows. |
| Workstation | Aplicación del operador. Mosaicos en vivo, reproducción con línea de tiempo y exportación. |

Los tres vienen en un solo instalador. Las aplicaciones están disponibles en español,
inglés y portugués.

## Funciones

Incluidas en la versión gratuita:

- Descubrimiento automático de cámaras ONVIF y de la ruta del video RTSP. Solo se
  necesitan el usuario y la contraseña de la cámara. Patrones de ruta integrados para
  Hikvision, Annke, Dahua, Intelbras, Axis y Reolink.
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
| Analíticas de video con IA: conteo de personas, reconocimiento facial y lectura de placas Mercosur, con modo de prueba con videos de ejemplo (AI Engine) | Disponible, gratuito en la fase de pruebas |
| Otras analíticas: detección de objetos, cruce de línea, merodeo, detección de filas, fuego y humo, EPP, objetos abandonados, búsqueda inteligente | En desarrollo |
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

## Instalación

1. Descargue `PrimeVMS-Setup-X.Y.Z.exe` de la
   [versión más reciente](https://github.com/Daniel1ux/Prime-VMS-Public/releases/latest).
2. Ejecute el instalador, elija el idioma y acepte el aviso de administrador.
   El instalador todavía no tiene firma de código. Si aparece Windows SmartScreen,
   haga clic en **Más información** y luego en **Ejecutar de todas formas**.
3. Elija el modelo de implementación:
   - **Una sola computadora.** Instala System Manager, Storage y Workstation ya
     conectados entre sí. Adecuado para hasta unas 16 cámaras, sin redundancia de
     grabación.
   - **Distribuida.** Marque las funciones de esta computadora: System Manager en un
     servidor dedicado, Storage en uno o más servidores de grabación y Workstation en
     las computadoras de operación.
4. Abra la Workstation o la Consola del System Manager.

Inicie sesión con el usuario `admin` y la contraseña `admin` y luego cambie la
contraseña.

El idioma elegido en el instalador pasa a ser el predeterminado de las aplicaciones.
Cada usuario puede cambiarlo con el selector de idioma en la pantalla de inicio de
sesión o en la barra lateral.

### Puertos de red

| Puerto (TCP) | Servicio |
|---|---|
| 58100 | System Manager |
| 58200 | Storage |

El instalador agrega estas reglas al Firewall de Windows. En una instalación
distribuida, asegúrese de que la red permita estos puertos entre los servidores y las
Workstations.

## Actualizaciones

A partir de la versión 1.0.4, PrimeVMS se actualiza desde las propias aplicaciones.

1. En la Workstation, la Consola del System Manager o la Consola del Storage, haga clic
   en **Buscar actualizaciones** en la barra lateral o en la pantalla de inicio de
   sesión. Las aplicaciones también verifican solas y avisan cuando hay una versión
   nueva.
2. Lea las notas de la versión y haga clic en **Actualizar ahora**. Se necesitan
   permisos de administrador.
3. PrimeVMS actualiza todos los componentes instalados en la computadora. Detiene los
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
| [1.2.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.2.0) (recomendada) | 18/10/2026 | `PrimeVMS-Setup-1.2.0.exe`, 493 MB | Sí |
| [1.1.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.1.0) | 18/10/2026 | `PrimeVMS-Setup-1.1.0.exe`, 493 MB | Sí |
| [1.0.6](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.0.6) | 18/10/2026 | `PrimeVMS-Setup-1.0.6.exe`, 315 MB | Sí |
| [1.0.5](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.0.5) | 18/10/2026 | `PrimeVMS-Setup-1.0.5.exe`, 315 MB | Sí |
| [1.0.4](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.0.4) | 18/10/2026 | `PrimeVMS-Setup-1.0.4.exe`, 314 MB | Sí |
| [1.0.3](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.0.3) | 17/10/2026 | `PrimeVMS-Setup-1.0.3.exe`, 314 MB | No (instale la 1.2.0) |
| [1.0.2](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.0.2) | 06/06/2026 | `PrimeVMS-Setup-1.0.2.exe`, 424 MB | No |
| [1.0.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.0.0) | 01/06/2026 | `PrimeVMS-Setup-1.0.0.exe`, 265 MB | No |

Las versiones anteriores se conservan como referencia. Si usa la versión 1.0.3 o
anterior, instale la versión más reciente con el instalador una vez. Sus datos se
conservan y las versiones siguientes se actualizan desde la aplicación.

### Verificar la descarga

```powershell
Get-FileHash .\PrimeVMS-Setup-1.2.0.exe -Algorithm SHA256
```

| Archivo | SHA-256 |
|---|---|
| `PrimeVMS-Setup-1.2.0.exe` | `431926639B594119DAFA7CE3C0BA416A16D4D01367AD8AC41868C82FEE70FC33` |
| `PrimeVMS-Setup-1.1.0.exe` | `A10DAC26CA323654E718259BE15B9E6D1442D640C2D9452984F3AF9B934E7B02` |
| `PrimeVMS-Setup-1.0.6.exe` | `B1245763AADB7699C894117A781E11C2044F41A3E84211A3C6E634CA41E087C8` |
| `PrimeVMS-Setup-1.0.5.exe` | `97BAA1164289F40D35D530A1C9AC7A338E73CAA4197B4BF06473DD2FCCFFF746` |
| `PrimeVMS-Setup-1.0.4.exe` | `405B120D9E5BD56915E8CDE0A65D2D55CFD6A9020EB49992CE4177E1E3D71ED4` |
| `PrimeVMS-Setup-1.0.3.exe` | `97B2E821B3182DF8619003B73626AC234D8DA9A407FBD0434E6BDB804F7ED8D0` |
| `PrimeVMS-Setup-1.0.2.exe` | `8810E256670D7D20E791989B38D56D3878F0A753F126A9B990067A2E84FA65E7` |
| `PrimeVMS-Setup-1.0.0.exe` | `827586BE66C64AF0FD3538A8AE00A052ED8CDBF6890F73FD3EABA8DD9448BF0C` |

## Preguntas frecuentes

**¿PrimeVMS es gratuito?**
Sí. Video en vivo, grabación, reproducción, exportación, usuarios, instalación
distribuida y actualizaciones son gratuitos, sin licencia por cámara. Las analíticas
con IA también son gratuitas en la fase de pruebas actual. Prime Cloud y la alta
disponibilidad serán módulos pagos.

**¿Qué cámaras son compatibles?**
Cualquier cámara IP con ONVIF o RTSP. PrimeVMS encuentra las cámaras ONVIF en la red y
detecta la ruta del video.

**¿Reemplaza a un NVR?**
PrimeVMS graba las cámaras IP directamente en una PC o servidor Windows, con retención
por días. También puede grabar desde grabadores existentes que ofrecen RTSP.

**¿Cuántas cámaras puedo agregar?**
La versión gratuita no tiene límite por cámara. El límite práctico depende del hardware
y de la red. En sitios más grandes, use la instalación distribuida con varios
servidores de grabación.

**¿Qué idiomas hay disponibles?**
Español, inglés y portugués (Brasil), en las aplicaciones, el instalador y las notas de
versión.

## Desinstalación

Abra **Configuración > Aplicaciones > PrimeVMS > Desinstalar** o use el acceso directo
"Desinstalar PrimeVMS" del menú Inicio. Se eliminan los servicios y las reglas de
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

PrimeVMS incluye componentes de terceros bajo sus propias licencias, como
[FFmpeg](https://ffmpeg.org/) y [go2rtc](https://github.com/AlexxIT/go2rtc).

Soporte: [primebr.com.br](https://primebr.com.br/)
