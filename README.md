English · [Português](README.pt-BR.md) · [Español](README.es.md)

# NexaVMS

Video management software (VMS) for IP cameras and CCTV on Windows. Watch live, record
around the clock, play back and export video from any ONVIF or RTSP camera.

Nexa VMS is licensed per camera in the Basic and Professional editions. Prices are available
on request. See [Access and licenses](#access-and-licenses).

[Download](https://github.com/Daniel1ux/Prime-VMS-Public/releases/latest) ·
[Website](https://daniel1ux.github.io/Prime-VMS-Public/) ·
[Release notes](https://github.com/Daniel1ux/Prime-VMS-Public/releases)

[![Latest version](https://img.shields.io/github/v/release/Daniel1ux/Prime-VMS-Public?label=version&color=c5e82e&labelColor=0a1626)](https://github.com/Daniel1ux/Prime-VMS-Public/releases/latest)
![Windows 10 and 11](https://img.shields.io/badge/Windows-10%20%7C%2011-0b2545)

## Overview

NexaVMS is made of three components that you can install on one computer or spread
across your network:

| Component | Role |
|---|---|
| System Manager | Central server. Manages cameras, users, permissions and site settings. Runs as a Windows service. |
| Storage | Recording server. Records cameras to disk, applies retention and serves live and recorded video. Runs as a Windows service. |
| Workstation | Operator application. Live layouts, playback with timeline and export. |

All three come in a single installer. The apps are available in English, Portuguese
and Spanish.

## Features

Included in every edition:

- Automatic discovery of ONVIF cameras and of the RTSP stream path. Only the camera
  user name and password are needed. Built-in path patterns for Hikvision, Annke,
  Dahua, Intelbras, Axis and Reolink.
- Network camera search and bulk registration: add many cameras at once, with a reading
  of each camera's ONVIF features.
- Continuous recording to disk in segmented MP4, without re-encoding, with retention by
  days.
- Live view in layouts up to 4×4, full screen, multiple monitors and video wall, with
  hardware-accelerated decoding.
- Playback with a 24-hour timeline, zoom, bookmarks and synchronized playback of
  several cameras.
- Image and video export with a watermark (logo, date and time).
- Users with administrator, supervisor and operator roles, enforced by the server.
- Single-computer or distributed deployment with several recording servers.
- Updates from inside the app.

## Modules

| Module | Availability |
|---|---|
| AI video analytics (AI Engine): facial recognition, license plate reading (Brazil and other countries), people counting, smart search, perimeter protection, PPE, abandoned objects, fire and smoke, crowd and loitering | Available, licensed per channel or site-wide |
| Nexa Cloud: remote and mobile access without opening ports | Available |
| High availability: redundant central server (Enterprise) | Coming soon |

## Access and licenses

Nexa VMS is offered in the Basic and Professional editions, licensed per camera. Prices are
on request. The editions are described at [nexavms.io/precos](https://nexavms.io/precos).

To evaluate Nexa VMS:

1. Create an account at [nexavms.io/conta](https://nexavms.io/conta).
2. Install Nexa VMS and activate the installation in the System Manager Console with that
   account.
3. The Nexa VMS team reviews new accounts and releases a trial of the Professional edition.
   The trial lasts 24 hours by default, and the team can extend it.

Without activation, Nexa VMS does not record or show video. For access, licenses and prices,
contact [support@nexavms.io](mailto:support@nexavms.io).

## Requirements

- Windows 10 or Windows 11, 64-bit.
- Administrator rights to install and update.
- IP cameras with ONVIF or RTSP on the same network.
- For Storage, a disk sized for the retention you need. Recordings are kept outside
  the program folder.
- For Workstation, a graphics card with hardware video decoding is recommended for
  large layouts.

## Installation

1. Download `PrimeVMS-Setup-X.Y.Z.exe` from the
   [latest release](https://github.com/Daniel1ux/Prime-VMS-Public/releases/latest).
2. Run the installer, choose a language and accept the administrator prompt.
   The installer is not code-signed yet. If Windows SmartScreen appears, select
   **More info** and then **Run anyway**.
3. Choose a deployment model:
   - **Single computer.** Installs System Manager, Storage and Workstation, already
     connected to each other. Suitable for up to about 16 cameras, without recording
     redundancy.
   - **Distributed.** Select the roles for this computer: System Manager on a dedicated
     server, Storage on one or more recording servers and Workstation on the operator
     computers.
4. Open Workstation or the System Manager Console.
5. In the System Manager Console, activate the installation with your Nexa VMS account.
   See [Access and licenses](#access-and-licenses).

Sign in with user `admin` and password `admin`, then change the password.

The language selected in the installer becomes the default for the apps. Each user can
change it from the language selector on the sign-in screen or in the sidebar.

### Network ports

| Port (TCP) | Service |
|---|---|
| 58100 | System Manager |
| 58200 | Storage |

The installer adds these rules to Windows Firewall. In a distributed deployment, make
sure the network allows these ports between the servers and the Workstations.

## Nexa Player

Protected exports (`.pvx`) are encrypted with a password and include an integrity check, so they
do not open in regular video players. To watch them, use Nexa Player for Windows. It opens
`.pvx` packages, exported folders and MP4 files, and shows whether each video is intact and signed.

- [Download Nexa Player (zip, no installation)](https://github.com/Daniel1ux/Prime-VMS-Public/releases/latest/download/NexaPlayer-win-x64.zip)
- [Download the Nexa Player installer](https://github.com/Daniel1ux/Prime-VMS-Public/releases/latest/download/NexaPlayer-Setup.exe)

1. Download `NexaPlayer-win-x64.zip`, right-click it and select **Extract All**.
2. Open `PrimePlayer.exe` in the extracted folder. If Windows SmartScreen appears, select
   **More info** and then **Run anyway**.
3. Select **Open file**, choose the `.pvx` file and enter the password. The list shows whether
   each video is intact and signed.

The password is not stored in the package. Ask the person who made the export. These links always
point to the latest version.

## Updates

Starting with version 1.0.4, NexaVMS updates from inside the apps.

1. In Workstation, System Manager Console or Storage Console, select
   **Check for updates** in the sidebar or on the sign-in screen. The apps also check
   automatically and show when a new version is available.
2. Review the release notes and select **Update now**. Administrator rights are
   required.
3. NexaVMS updates every component installed on the computer. It stops the services,
   closes the apps, installs the new version, starts the services, checks that they
   respond and reopens the app. The process takes about a minute.

How updates work:

- Only changed files are downloaded, usually about 1 MB.
- Each release is digitally signed. Modified or corrupted files are rejected before
  anything is changed.
- If a service fails to start, or the computer loses power during the update, the
  previous version is restored automatically.
- Settings, cameras, users and recordings are kept. The database is upgraded
  automatically.

Recording pauses for a few seconds during an update. On critical sites, update during
low-activity hours.

### Offline update

Copy the update files of a release (`update-manifest.json`, `update-manifest.json.sig`
and the `pack-*.zip` files) to a folder, then run as administrator:

```
"C:\Program Files\Prime VMS\Updater\PrimeVMS Updater.exe" --apply --source folder:D:\primevms-update
```

## Versions

| Version | Date | Installer | In-app updates |
|---|---|---|---|
| [2.11.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.11.0) (recommended) | 2026-10-28 | `PrimeVMS-Setup-2.11.0.exe`, 637 MB | Yes |
| [2.10.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.10.0) | 2026-10-28 | `PrimeVMS-Setup-2.10.0.exe`, 637 MB | Yes |
| [2.9.1](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.9.1) | 2026-10-27 | `PrimeVMS-Setup-2.9.1.exe`, 637 MB | Yes |
| [2.9.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.9.0) | 2026-10-27 | `PrimeVMS-Setup-2.9.0.exe`, 637 MB | Yes |
| [2.8.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.8.0) | 2026-10-27 | `PrimeVMS-Setup-2.8.0.exe`, 637 MB | Yes |
| [2.7.18](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.7.18) | 2026-10-26 | `PrimeVMS-Setup-2.7.18.exe`, 637 MB | Yes |
| [2.7.17](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.7.17) | 2026-10-26 | `PrimeVMS-Setup-2.7.17.exe`, 637 MB | Yes |
| [2.7.16](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.7.16) | 2026-10-26 | `PrimeVMS-Setup-2.7.16.exe`, 637 MB | Yes |
| [2.7.15](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.7.15) | 2026-10-26 | `PrimeVMS-Setup-2.7.15.exe`, 637 MB | Yes |
| [2.7.14](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.7.14) | 2026-10-26 | `PrimeVMS-Setup-2.7.14.exe`, 637 MB | Yes |
| [2.7.13](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.7.13) | 2026-10-26 | `PrimeVMS-Setup-2.7.13.exe`, 637 MB | Yes |
| [2.7.12](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.7.12) | 2026-10-26 | `PrimeVMS-Setup-2.7.12.exe`, 637 MB | Yes |
| [2.7.11](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.7.11) | 2026-10-26 | `PrimeVMS-Setup-2.7.11.exe`, 637 MB | Yes |
| [2.7.10](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.7.10) | 2026-10-26 | `PrimeVMS-Setup-2.7.10.exe`, 637 MB | Yes |
| [2.7.9](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.7.9) | 2026-10-26 | `PrimeVMS-Setup-2.7.9.exe`, 637 MB | Yes |
| [2.7.8](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.7.8) | 2026-10-26 | `PrimeVMS-Setup-2.7.8.exe`, 637 MB | Yes |
| [2.7.7](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.7.7) | 2026-10-26 | `PrimeVMS-Setup-2.7.7.exe`, 637 MB | Yes |
| [2.7.6](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.7.6) | 2026-10-26 | `PrimeVMS-Setup-2.7.6.exe`, 637 MB | Yes |
| [2.7.5](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.7.5) | 2026-10-26 | `PrimeVMS-Setup-2.7.5.exe`, 637 MB | Yes |
| [2.7.4](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.7.4) | 2026-10-26 | `PrimeVMS-Setup-2.7.4.exe`, 637 MB | Yes |
| [2.7.3](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.7.3) | 2026-10-26 | `PrimeVMS-Setup-2.7.3.exe`, 637 MB | Yes |
| [2.7.2](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.7.2) | 2026-10-26 | `PrimeVMS-Setup-2.7.2.exe`, 636 MB | Yes |
| [2.7.1](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.7.1) | 2026-10-25 | `PrimeVMS-Setup-2.7.1.exe`, 636 MB | Yes |
| [2.7.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.7.0) | 2026-10-25 | `PrimeVMS-Setup-2.7.0.exe`, 636 MB | Yes |
| [2.6.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.6.0) | 2026-10-25 | `PrimeVMS-Setup-2.6.0.exe`, 636 MB | Yes |
| [2.5.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.5.0) | 2026-10-23 | `PrimeVMS-Setup-2.5.0.exe`, 634 MB | Yes |
| [2.4.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.4.0) | 2026-10-22 | `PrimeVMS-Setup-2.4.0.exe`, 633 MB | Yes |
| [2.2.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.2.0) | 2026-10-21 | `PrimeVMS-Setup-2.2.0.exe`, 626 MB | Yes |
| [2.1.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.1.0) | 2026-10-21 | `PrimeVMS-Setup-2.1.0.exe`, 626 MB | Yes |
| [2.0.1](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.0.1) | 2026-10-20 | `PrimeVMS-Setup-2.0.1.exe`, 625 MB | Yes |
| [2.0.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.0.0) | 2026-10-20 | `PrimeVMS-Setup-2.0.0.exe`, 625 MB | Yes |
| [1.9.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.9.0) | 2026-10-20 | `PrimeVMS-Setup-1.9.0.exe`, 622 MB | Yes |
| [1.8.1](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.8.1) | 2026-10-20 | `PrimeVMS-Setup-1.8.1.exe`, 543 MB | Yes |
| [1.8.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.8.0) | 2026-10-20 | `PrimeVMS-Setup-1.8.0.exe`, 543 MB | Yes |
| [1.7.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.7.0) | 2026-10-20 | `PrimeVMS-Setup-1.7.0.exe`, 542 MB | Yes |
| [1.5.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.5.0) | 2026-10-19 | `PrimeVMS-Setup-1.5.0.exe`, 498 MB | Yes |
| [1.4.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.4.0) | 2026-10-18 | `PrimeVMS-Setup-1.4.0.exe`, 497 MB | No (install 2.11.0) |
| [1.3.1](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.3.1) | 2026-10-18 | `PrimeVMS-Setup-1.3.1.exe`, 494 MB | No (install 2.11.0) |
| [1.3.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.3.0) | 2026-10-18 | `PrimeVMS-Setup-1.3.0.exe`, 494 MB | No (install 2.11.0) |
| [1.2.1](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.2.1) | 2026-10-18 | `PrimeVMS-Setup-1.2.1.exe`, 493 MB | No (install 2.11.0) |
| [1.2.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.2.0) | 2026-10-18 | `PrimeVMS-Setup-1.2.0.exe`, 493 MB | No (install 2.11.0) |
| [1.1.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.1.0) | 2026-10-18 | `PrimeVMS-Setup-1.1.0.exe`, 493 MB | No (install 2.11.0) |
| [1.0.6](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.0.6) | 2026-10-18 | `PrimeVMS-Setup-1.0.6.exe`, 315 MB | No (install 2.11.0) |
| [1.0.5](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.0.5) | 2026-10-18 | `PrimeVMS-Setup-1.0.5.exe`, 315 MB | No (install 2.11.0) |
| [1.0.4](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.0.4) | 2026-10-18 | `PrimeVMS-Setup-1.0.4.exe`, 314 MB | No (install 2.11.0) |
| [1.0.3](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.0.3) | 2026-10-17 | `PrimeVMS-Setup-1.0.3.exe`, 314 MB | No (install 2.11.0) |
| [1.0.2](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.0.2) | 2026-06-06 | `PrimeVMS-Setup-1.0.2.exe`, 424 MB | No |
| [1.0.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.0.0) | 2026-06-01 | `PrimeVMS-Setup-1.0.0.exe`, 265 MB | No |

Earlier versions are kept for reference. If you run version 1.4.0 or earlier, install
the latest version with the installer once. Your data is kept, and later versions
update from inside the app.

Starting with 2.5.0, the installation must be activated with a Nexa VMS account from the System
Manager Console. Without activation, NexaVMS does not record or show video. See
[Access and licenses](#access-and-licenses).

### Verify the download

```powershell
Get-FileHash .\PrimeVMS-Setup-2.11.0.exe -Algorithm SHA256
```

| File | SHA-256 |
|---|---|
| `PrimeVMS-Setup-2.11.0.exe` | `601EB0D23E60A71C0E2B256B0CD668C10742901445EC3CC9E414033E50DCF1DF` |
| `PrimeVMS-Setup-2.9.1.exe` | `47EF3D35A556C95A0542D4B93FC70CC56CAE5BDEDD120378048BE76CD406E79D` |
| `PrimeVMS-Setup-2.9.0.exe` | `FAD438DA95913185F893567CC8085321FE369BD54298A77345AF100339BF0B2F` |
| `PrimeVMS-Setup-2.8.0.exe` | `53B71D15C45345FF9BE9A4155B59E57B3D8E00E0507698F8D0B0F5482F1E51AF` |
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

## FAQ

**How do I get access to Nexa VMS?**
Create an account at [nexavms.io/conta](https://nexavms.io/conta), install Nexa VMS and
activate it in the System Manager Console. The Nexa VMS team reviews new accounts and releases
a trial of the Professional edition, 24 hours by default, which the team can extend.

**How much does it cost?**
Basic and Professional are licensed per camera. Prices are on request: contact
[support@nexavms.io](mailto:support@nexavms.io).

**Which cameras are supported?**
Any IP camera with ONVIF or RTSP. NexaVMS finds ONVIF cameras on the network and
detects the stream path.

**Can it replace an NVR?**
NexaVMS records IP cameras directly on a Windows PC or server, with retention by days.
It can also record from existing recorders that provide RTSP streams.

**How many cameras can I add?**
It depends on the edition, the hardware and the network. The limits of each edition are at
[nexavms.io/precos](https://nexavms.io/precos). For larger sites, use a distributed deployment
with several recording servers.

**Which languages are available?**
English, Portuguese (Brazil) and Spanish, in the apps, the installer and the release
notes.

## Uninstall

Open **Settings > Apps > NexaVMS > Uninstall** (PrimeVMS in installations from before 2.4.0), or use the "Uninstall NexaVMS"
shortcut in the Start menu. Services and firewall rules are removed. The database and
recordings in `C:\ProgramData\Prime VMS` and in the selected recording folder are not
deleted.

## License and support

Copyright © 2026 Prime Systems and Controls LLC. Nexa VMS is a trade name of Prime Systems and
Controls LLC.

Using Nexa VMS requires an active license or a trial released by the Nexa VMS team. The
operator is responsible for complying with applicable law, including data protection laws,
when capturing, recording and processing images.

NexaVMS includes third-party components under their own licenses, including
[FFmpeg](https://ffmpeg.org/) and [go2rtc](https://github.com/AlexxIT/go2rtc).

Support: [support@nexavms.io](mailto:support@nexavms.io) · [nexavms.io](https://nexavms.io)
