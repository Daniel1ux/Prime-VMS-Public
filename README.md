English · [Português](README.pt-BR.md) · [Español](README.es.md)

# PrimeVMS

Free video management software (VMS) for IP cameras and CCTV on Windows. Watch live, record
around the clock, play back and export video from any ONVIF or RTSP camera.

The core product is free, with no per-camera license. Advanced modules are available
on affordable plans.

[Download](https://github.com/Daniel1ux/Prime-VMS-Public/releases/latest) ·
[Website](https://daniel1ux.github.io/Prime-VMS-Public/) ·
[Release notes](https://github.com/Daniel1ux/Prime-VMS-Public/releases)

[![Latest version](https://img.shields.io/github/v/release/Daniel1ux/Prime-VMS-Public?label=version&color=c5e82e&labelColor=0a1626)](https://github.com/Daniel1ux/Prime-VMS-Public/releases/latest)
![Windows 10 and 11](https://img.shields.io/badge/Windows-10%20%7C%2011-0b2545)

## Overview

PrimeVMS is made of three components that you can install on one computer or spread
across your network:

| Component | Role |
|---|---|
| System Manager | Central server. Manages cameras, users, permissions and site settings. Runs as a Windows service. |
| Storage | Recording server. Records cameras to disk, applies retention and serves live and recorded video. Runs as a Windows service. |
| Workstation | Operator application. Live layouts, playback with timeline and export. |

All three come in a single installer. The apps are available in English, Portuguese
and Spanish.

## Features

Included in the free version:

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

## Paid modules

| Module | Availability |
|---|---|
| AI video analytics: people counting, face recognition, license plate recognition for Mercosur plates, smart search and perimeter protection, each with a test mode using real sample videos (AI Engine) | Available, free during the testing phase |
| Additional analytics: loitering, queue detection, fire and smoke, PPE, abandoned objects | In development |
| Prime Cloud: remote and mobile access without opening ports | Coming soon |
| High availability: redundant central server | Coming soon |

Plans are designed for small and mid-size projects.
[Contact Prime Building Technology](https://primebr.com.br/) for a quote.

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

## Updates

Starting with version 1.0.4, PrimeVMS updates from inside the apps.

1. In Workstation, System Manager Console or Storage Console, select
   **Check for updates** in the sidebar or on the sign-in screen. The apps also check
   automatically and show when a new version is available.
2. Review the release notes and select **Update now**. Administrator rights are
   required.
3. PrimeVMS updates every component installed on the computer. It stops the services,
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
| [1.9.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.9.0) (recommended) | 2026-10-20 | `PrimeVMS-Setup-1.9.0.exe`, 622 MB | Yes |
| [1.8.1](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.8.1) | 2026-10-20 | `PrimeVMS-Setup-1.8.1.exe`, 543 MB | Yes |
| [1.8.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.8.0) | 2026-10-20 | `PrimeVMS-Setup-1.8.0.exe`, 543 MB | Yes |
| [1.7.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.7.0) | 2026-10-20 | `PrimeVMS-Setup-1.7.0.exe`, 542 MB | Yes |
| [1.5.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.5.0) | 2026-10-19 | `PrimeVMS-Setup-1.5.0.exe`, 498 MB | Yes |
| [1.4.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.4.0) | 2026-10-18 | `PrimeVMS-Setup-1.4.0.exe`, 497 MB | No (install 1.9.0) |
| [1.3.1](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.3.1) | 2026-10-18 | `PrimeVMS-Setup-1.3.1.exe`, 494 MB | No (install 1.9.0) |
| [1.3.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.3.0) | 2026-10-18 | `PrimeVMS-Setup-1.3.0.exe`, 494 MB | No (install 1.9.0) |
| [1.2.1](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.2.1) | 2026-10-18 | `PrimeVMS-Setup-1.2.1.exe`, 493 MB | No (install 1.9.0) |
| [1.2.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.2.0) | 2026-10-18 | `PrimeVMS-Setup-1.2.0.exe`, 493 MB | No (install 1.9.0) |
| [1.1.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.1.0) | 2026-10-18 | `PrimeVMS-Setup-1.1.0.exe`, 493 MB | No (install 1.9.0) |
| [1.0.6](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.0.6) | 2026-10-18 | `PrimeVMS-Setup-1.0.6.exe`, 315 MB | No (install 1.9.0) |
| [1.0.5](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.0.5) | 2026-10-18 | `PrimeVMS-Setup-1.0.5.exe`, 315 MB | No (install 1.9.0) |
| [1.0.4](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.0.4) | 2026-10-18 | `PrimeVMS-Setup-1.0.4.exe`, 314 MB | No (install 1.9.0) |
| [1.0.3](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.0.3) | 2026-10-17 | `PrimeVMS-Setup-1.0.3.exe`, 314 MB | No (install 1.9.0) |
| [1.0.2](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.0.2) | 2026-06-06 | `PrimeVMS-Setup-1.0.2.exe`, 424 MB | No |
| [1.0.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.0.0) | 2026-06-01 | `PrimeVMS-Setup-1.0.0.exe`, 265 MB | No |

Earlier versions are kept for reference. If you run version 1.4.0 or earlier, install
the latest version with the installer once. Your data is kept, and later versions
update from inside the app.

### Verify the download

```powershell
Get-FileHash .\PrimeVMS-Setup-1.9.0.exe -Algorithm SHA256
```

| File | SHA-256 |
|---|---|
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

**Is PrimeVMS free?**
Yes. Live view, recording, playback, export, users, distributed deployment and updates
are free, with no per-camera license. AI analytics are also free during the current
testing phase. Prime Cloud and high availability will be paid modules.

**Which cameras are supported?**
Any IP camera with ONVIF or RTSP. PrimeVMS finds ONVIF cameras on the network and
detects the stream path.

**Can it replace an NVR?**
PrimeVMS records IP cameras directly on a Windows PC or server, with retention by days.
It can also record from existing recorders that provide RTSP streams.

**How many cameras can I add?**
The free version has no per-camera limit. The practical limit depends on hardware and
network. For larger sites, use a distributed deployment with several recording servers.

**Which languages are available?**
English, Portuguese (Brazil) and Spanish, in the apps, the installer and the release
notes.

## Uninstall

Open **Settings > Apps > PrimeVMS > Uninstall**, or use the "Uninstall PrimeVMS"
shortcut in the Start menu. Services and firewall rules are removed. The database and
recordings in `C:\ProgramData\Prime VMS` and in the selected recording folder are not
deleted.

## License and support

Copyright © 2026 Prime Building Technology. All rights reserved.

The VMS core (System Manager, Storage and Workstation) is free to use for video
management at the licensee's site. Cloud and high-availability modules require a
commercial license; AI modules are free during the testing phase. The operator is responsible for complying with applicable law,
including data protection laws, when capturing, recording and processing images.

PrimeVMS includes third-party components under their own licenses, including
[FFmpeg](https://ffmpeg.org/) and [go2rtc](https://github.com/AlexxIT/go2rtc).

Support: [primebr.com.br](https://primebr.com.br/)
