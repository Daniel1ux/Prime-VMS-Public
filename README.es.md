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

NexaVMS tiene tres componentes, que pueden estar en una sola computadora o
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
| [2.7.18](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.7.18) (recomendada) | 26/10/2026 | `PrimeVMS-Setup-2.7.18.exe`, 637 MB | Sí |
| [2.7.17](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.7.17) | 26/10/2026 | `PrimeVMS-Setup-2.7.17.exe`, 637 MB | Sí |
| [2.7.16](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.7.16) | 26/10/2026 | `PrimeVMS-Setup-2.7.16.exe`, 637 MB | Sí |
| [2.7.15](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.7.15) | 26/10/2026 | `PrimeVMS-Setup-2.7.15.exe`, 637 MB | Sí |
| [2.7.14](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.7.14) | 26/10/2026 | `PrimeVMS-Setup-2.7.14.exe`, 637 MB | Sí |
| [2.7.13](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.7.13) | 26/10/2026 | `PrimeVMS-Setup-2.7.13.exe`, 637 MB | Sí |
| [2.7.12](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.7.12) | 26/10/2026 | `PrimeVMS-Setup-2.7.12.exe`, 637 MB | Sí |
| [2.7.11](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.7.11) | 26/10/2026 | `PrimeVMS-Setup-2.7.11.exe`, 637 MB | Sí |
| [2.7.10](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.7.10) | 26/10/2026 | `PrimeVMS-Setup-2.7.10.exe`, 637 MB | Sí |
| [2.7.9](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.7.9) | 26/10/2026 | `PrimeVMS-Setup-2.7.9.exe`, 637 MB | Sí |
| [2.7.8](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.7.8) | 26/10/2026 | `PrimeVMS-Setup-2.7.8.exe`, 637 MB | Sí |
| [2.7.7](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.7.7) | 26/10/2026 | `PrimeVMS-Setup-2.7.7.exe`, 637 MB | Sí |
| [2.7.6](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.7.6) | 26/10/2026 | `PrimeVMS-Setup-2.7.6.exe`, 637 MB | Sí |
| [2.7.5](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.7.5) | 26/10/2026 | `PrimeVMS-Setup-2.7.5.exe`, 637 MB | Sí |
| [2.7.4](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.7.4) | 26/10/2026 | `PrimeVMS-Setup-2.7.4.exe`, 637 MB | Sí |
| [2.7.3](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.7.3) | 26/10/2026 | `PrimeVMS-Setup-2.7.3.exe`, 637 MB | Sí |
| [2.7.2](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.7.2) | 26/10/2026 | `PrimeVMS-Setup-2.7.2.exe`, 636 MB | Sí |
| [2.7.1](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.7.1) | 25/10/2026 | `PrimeVMS-Setup-2.7.1.exe`, 636 MB | Sí |
| [2.7.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.7.0) | 25/10/2026 | `PrimeVMS-Setup-2.7.0.exe`, 636 MB | Sí |
| [2.6.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.6.0) | 25/10/2026 | `PrimeVMS-Setup-2.6.0.exe`, 636 MB | Sí |
| [2.5.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.5.0) | 23/10/2026 | `PrimeVMS-Setup-2.5.0.exe`, 634 MB | Sí |
| [2.4.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.4.0) | 22/10/2026 | `PrimeVMS-Setup-2.4.0.exe`, 633 MB | Sí |
| [2.2.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.2.0) | 21/10/2026 | `PrimeVMS-Setup-2.2.0.exe`, 626 MB | Sí |
| [2.1.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.1.0) | 21/10/2026 | `PrimeVMS-Setup-2.1.0.exe`, 626 MB | SÃ­ |
| [2.0.1](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.0.1) | 20/10/2026 | `PrimeVMS-Setup-2.0.1.exe`, 625 MB | Sí |
| [2.0.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.0.0) | 20/10/2026 | `PrimeVMS-Setup-2.0.0.exe`, 625 MB | Sí |
| [1.9.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.9.0) | 20/10/2026 | `PrimeVMS-Setup-1.9.0.exe`, 622 MB | Sí |
| [1.8.1](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.8.1) | 20/10/2026 | `PrimeVMS-Setup-1.8.1.exe`, 543 MB | Sí |
| [1.8.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.8.0) | 20/10/2026 | `PrimeVMS-Setup-1.8.0.exe`, 543 MB | Sí |
| [1.7.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.7.0) | 20/10/2026 | `PrimeVMS-Setup-1.7.0.exe`, 542 MB | Sí |
| [1.5.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.5.0) | 19/10/2026 | `PrimeVMS-Setup-1.5.0.exe`, 498 MB | Sí |
| [1.4.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.4.0) | 18/10/2026 | `PrimeVMS-Setup-1.4.0.exe`, 497 MB | No (instale la 2.7.18) |
| [1.3.1](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.3.1) | 18/10/2026 | `PrimeVMS-Setup-1.3.1.exe`, 494 MB | No (instale la 2.7.18) |
| [1.3.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.3.0) | 18/10/2026 | `PrimeVMS-Setup-1.3.0.exe`, 494 MB | No (instale la 2.7.18) |
| [1.2.1](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.2.1) | 18/10/2026 | `PrimeVMS-Setup-1.2.1.exe`, 493 MB | No (instale la 2.7.18) |
| [1.2.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.2.0) | 18/10/2026 | `PrimeVMS-Setup-1.2.0.exe`, 493 MB | No (instale la 2.7.18) |
| [1.1.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.1.0) | 18/10/2026 | `PrimeVMS-Setup-1.1.0.exe`, 493 MB | No (instale la 2.7.18) |
| [1.0.6](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.0.6) | 18/10/2026 | `PrimeVMS-Setup-1.0.6.exe`, 315 MB | No (instale la 2.7.18) |
| [1.0.5](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.0.5) | 18/10/2026 | `PrimeVMS-Setup-1.0.5.exe`, 315 MB | No (instale la 2.7.18) |
| [1.0.4](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.0.4) | 18/10/2026 | `PrimeVMS-Setup-1.0.4.exe`, 314 MB | No (instale la 2.7.18) |
| [1.0.3](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.0.3) | 17/10/2026 | `PrimeVMS-Setup-1.0.3.exe`, 314 MB | No (instale la 2.7.18) |
| [1.0.2](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.0.2) | 06/06/2026 | `PrimeVMS-Setup-1.0.2.exe`, 424 MB | No |
| [1.0.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.0.0) | 01/06/2026 | `PrimeVMS-Setup-1.0.0.exe`, 265 MB | No |

Las versiones anteriores se conservan como referencia. Si usa la versión 1.4.0 o
anterior, instale la versión más reciente con el instalador una vez. Sus datos se
conservan y las versiones siguientes se actualizan desde la aplicación.

A partir de la 2.5.0, la instalación debe activarse con una cuenta Nexa VMS, creada en
[nexavms.io](https://nexavms.io), desde la Consola del System Manager. Sin activación, NexaVMS no
graba ni muestra video. La primera activación incluye 30 días de prueba del Professional.

### Verificar la descarga

```powershell
Get-FileHash .\PrimeVMS-Setup-2.7.18.exe -Algorithm SHA256
```

| Archivo | SHA-256 |
|---|---|
| `PrimeVMS-Setup-2.7.18.exe` | `747646A19ACC3A3BAE6BB7D15E341274D4A1D7D29D81AE14421FFBAFF6F127A2` |
| `PrimeVMS-Setup-2.7.17.exe` | `A0D26E80CD4C592A0DA16260CB61C4F249C655382C3300080D78947FF0EA9237` |
| `PrimeVMS-Setup-2.7.16.exe` | `FA5EE73C47F2981838B8C5080517A32886A6585AD679C771CFF85036103E07E4` |
| `PrimeVMS-Setup-2.7.15.exe` | `9682AC8C48FF8D8F209AD57BB607DA8F66AFC072B519EACF49AAB8882F7CFE45` |
| `PrimeVMS-Setup-2.7.14.exe` | `4D8FA295BBE1166703EED5673B77A7B0CDADF36EEDB433201BFAEF469AC47D30` |
| `PrimeVMS-Setup-2.7.13.exe` | `98A19BBEF3DA31AADBEBBE38C5AEB8EE2A6575052714291FABA064363ABCF4BE` |
| `PrimeVMS-Setup-2.7.12.exe` | `AAA5CAF2FC603BAC558E4A3FC24359182EFCEDACFD58EDA40DD44FA3F481F805` |
| `PrimeVMS-Setup-2.7.11.exe` | `43E5457EF3B98673A0F85257CAD71ADDB87979C48BF64E4BB5963748F5525EFB` |
| `PrimeVMS-Setup-2.7.10.exe` | `F141C55616FEA93A95D5F5C89C7E0862B8473DD1EFC8BA1C20931860CC9BB3C9` |
| `PrimeVMS-Setup-2.7.9.exe` | `E9EDE1067C294A008D80FEF245F3CF94015E82E3CAC658F2DD803665884C2BD0` |
| `PrimeVMS-Setup-2.7.8.exe` | `5F7038E5CFA8B59166A27A08780B3D25D3EB06ED8A1747751E71470F5A2E0ADE` |
| `PrimeVMS-Setup-2.7.7.exe` | `D3513D5E7EEF083122D19F63189CDC409A6D44F5C80CB71949789680918C6D92` |
| `PrimeVMS-Setup-2.7.6.exe` | `5F715CE1AAD46EA82EE4971BC5159C5160BC0B0BA4C93991B6DE448BA509BFE0` |
| `PrimeVMS-Setup-2.7.5.exe` | `07B71E570610544BD37DDDEEEE6A91E587969F9DFD1B5ECD9E6CD1963643F2E6` |
| `PrimeVMS-Setup-2.7.4.exe` | `9AB65DBC6E8B75B4C2BCBBF3FA914162A8A1F8C370C6C3EB739C83C1DDF92A02` |
| `PrimeVMS-Setup-2.7.3.exe` | `6794E1F5124F9A1EC80D1EBD16B8F04084888FB69A747E4C2FF6D3A4ED24EEFD` |
| `PrimeVMS-Setup-2.7.2.exe` | `6EF47D5A72822544DD0173EFECEC4EF48B65CF1F4778328A4B5C58E3114DEADD` |
| `PrimeVMS-Setup-2.7.1.exe` | `60387D0AE76CBC3FFDD5D85592402B60176BE4308C5940B91D4E793C1341E2A1` |
| `PrimeVMS-Setup-2.7.0.exe` | `E4E22CC3E2B567C485F1B3A68BA735A247064A06AD76B87C53662205135E37FB` |
| `PrimeVMS-Setup-2.6.0.exe` | `08F72A36753CC5ED2CCBB7CFCF9F2C46F9531E5D4EB710637DB68014F95CEAD1` |
| `PrimeVMS-Setup-2.5.0.exe` | `CAE6D8F2876AAE838D09F29AF7A458B5E7DB2DEA1D15911CE10152A0F6BAFAAD` |
| `PrimeVMS-Setup-2.4.0.exe` | `E2B507AFBDBD440AC0D02A2097F340CF3F907F47AEF63BD42E532DD3A1A465D1` |
| `PrimeVMS-Setup-2.2.0.exe` | `8CF877C5ADBF2343BA6F6367C52883D7343DF1B851C5FD9A56692E7156762D70` |
| `PrimeVMS-Setup-2.1.0.exe` | `105DDD7A8E21FF7225C73A4496866636220BE2C1B3C1BE1C14323ED70C3BB9A1` |
| `PrimeVMS-Setup-2.0.1.exe` | `D9D9BA966B4CC612DB9AB528F2990078868A69952F979048F30F112CC6D19A26` |
| `PrimeVMS-Setup-2.0.0.exe` | `FFACF9BF70416534605FC6CC01DFED300A1BE9AB987BEF64CAF312E783D6C8D8` |
| `PrimeVMS-Setup-1.9.0.exe` | `A1FAEF166392A63B3A873C572CBB858F95722910DADA3C8F1DD52729BD70D43C` |
| `PrimeVMS-Setup-1.8.1.exe` | `05C9E031DC9B8885542728C1BC21659E7D5BCF5964A55D3730BE51B5C3417F46` |
| `PrimeVMS-Setup-1.8.0.exe` | `7198021CE27F554F47385322EB8CE8948BD6BDE0BC88CF6B60B6980F7BDF28E7` |
| `PrimeVMS-Setup-1.7.0.exe` | `E404DAA88A8CBD05562472DEAC84A8F681196FFB809D1BD2F341B3015A28D825` |
| `PrimeVMS-Setup-1.5.0.exe` | `A1190CD79D0F85C933A00C90AF8C03A1F6E60545C028F96B376D1EFD4DE6EEAA` |
| `PrimeVMS-Setup-1.4.0.exe` | `32E47D8F89BA60DF91C06A99D1FADC20965AC7E698FCCDF6DFE072884594209F` |
| `PrimeVMS-Setup-1.3.1.exe` | `DD44CDFEDA869F5A4C0212D7C11464C37627C290ED1AF95EE723246F7F504FD7` |
| `PrimeVMS-Setup-1.3.0.exe` | `51D039F8B7059B46AFB4C38FAF5B7D126B99AF9FCDF7E5FF65C185C4EABDD054` |
| `PrimeVMS-Setup-1.2.1.exe` | `B1816D7EA9E87AE6A2C9E68DC7E7E01E2DA8CB86836BF1865AFCD51E69D0CCFD` |
| `PrimeVMS-Setup-1.2.0.exe` | `431926639B594119DAFA7CE3C0BA416A16D4D01367AD8AC41868C82FEE70FC33` |
| `PrimeVMS-Setup-1.1.0.exe` | `A10DAC26CA323654E718259BE15B9E6D1442D640C2D9452984F3AF9B934E7B02` |
| `PrimeVMS-Setup-1.0.6.exe` | `B1245763AADB7699C894117A781E11C2044F41A3E84211A3C6E634CA41E087C8` |
| `PrimeVMS-Setup-1.0.5.exe` | `97BAA1164289F40D35D530A1C9AC7A338E73CAA4197B4BF06473DD2FCCFFF746` |
| `PrimeVMS-Setup-1.0.4.exe` | `405B120D9E5BD56915E8CDE0A65D2D55CFD6A9020EB49992CE4177E1E3D71ED4` |
| `PrimeVMS-Setup-1.0.3.exe` | `97B2E821B3182DF8619003B73626AC234D8DA9A407FBD0434E6BDB804F7ED8D0` |
| `PrimeVMS-Setup-1.0.2.exe` | `8810E256670D7D20E791989B38D56D3878F0A753F126A9B990067A2E84FA65E7` |
| `PrimeVMS-Setup-1.0.0.exe` | `827586BE66C64AF0FD3538A8AE00A052ED8CDBF6890F73FD3EABA8DD9448BF0C` |

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
