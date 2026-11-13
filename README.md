English · [Português](README.pt-BR.md) · [Español](README.es.md)

# NexaVMS

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

NexaVMS is made of four components that you can install on one computer or spread
across your network:

| Component | Role |
|---|---|
| System Manager | Central server. Manages cameras, users, permissions and site settings. Runs as a Windows service. |
| Storage | Recording server. Records cameras to disk, applies retention and serves live and recorded video. Runs as a Windows service. |
| Workstation | Operator application. Live layouts, playback with timeline and export. |
| AI server | Analyzes camera video for the AI modules and sends events to the System Manager. Runs on the same computer or on dedicated computers, one or several. Runs as a Windows service. |

All of them come in a single installer. The apps are available in English, Portuguese
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
- For the AI server, at least 8 GB of memory and 10 GB of free space. A compatible
  graphics card handles many more cameras; without one, analysis runs on the processor.

## Installation

1. Download `PrimeVMS-Setup-X.Y.Z.exe` from the
   [latest release](https://github.com/Daniel1ux/Prime-VMS-Public/releases/latest).
2. Run the installer, choose a language and accept the administrator prompt.
   The installer is not code-signed yet. If Windows SmartScreen appears, select
   **More info** and then **Run anyway**.
3. Choose how this computer will take part:
   - **Everything on this computer.** Installs System Manager, Storage and Workstation,
     already connected to each other. Suitable for up to about 16 cameras, without
     recording redundancy. The AI server can be included in the same installation.
   - **AI server only.** For a computer that only analyzes video for an existing Nexa VMS.
     It does not install System Manager, Storage or Workstation. The installer checks the
     hardware, asks for the server name, the address the System Manager will use and the
     password, and can connect it to the System Manager right away or leave that for later.
   - **Choose the parts.** Select the roles for this computer: System Manager on a
     dedicated server, Storage on one or more recording servers, Workstation on the
     operator computers and AI server.
4. Open Workstation or the System Manager Console. On an AI server, the AI Server
   NexaVMS app opens at the end.

Sign in with user `admin` and password `admin`, then change the password. On an AI
server, the user is `admin` and the password is the one chosen in the installer.

The AI models (about 600 MB) download in the background after installation. The progress
appears in the AI server app, under Models.

The language selected in the installer becomes the default for the apps. Each user can
change it from the language selector on the sign-in screen or in the sidebar.

### Network ports

| Port (TCP) | Service |
|---|---|
| 58100 | System Manager |
| 58200 | Storage |
| 58300 | AI server |

The installer adds these rules to Windows Firewall. In a distributed deployment, make
sure the network allows these ports between the servers and the Workstations.

## Nexa Player

Protected exports (`.pvx`) are encrypted with a password and include an integrity check, so they
do not open in regular video players. To watch them, use Nexa Player, free, for Windows. It opens
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
| [2.26.1](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.26.1) (recommended) | 2026-11-13 | `PrimeVMS-Setup-2.26.1.exe`, 646 MB | Yes |
| [2.26.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.26.0) | 2026-11-13 | `PrimeVMS-Setup-2.26.0.exe`, 646 MB | Yes |
| [2.25.2](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.25.2) | 2026-11-12 | `PrimeVMS-Setup-2.25.2.exe`, 646 MB | Yes |

Only the three latest versions are listed. Any earlier installation updates straight to the
latest version from inside the app. If you run version 1.4.0 or earlier, install the latest
version with the installer once. Your data is kept.

Starting with 2.5.0, the installation must be activated with a Nexa VMS account, created at
[nexavms.io](https://nexavms.io), from the System Manager Console. Without activation, NexaVMS does
not record or show video. The first activation includes a 30-day Professional trial.

### Verify the download

```powershell
Get-FileHash .\PrimeVMS-Setup-2.26.1.exe -Algorithm SHA256
```

| File | SHA-256 |
|---|---|
| `PrimeVMS-Setup-2.26.1.exe` | `8A739E6BB064EF62D5D0B2F85614F29387696DF8BAB05BF4ED95724E6B3029E0` |
| `PrimeVMS-Setup-2.26.0.exe` | `9516C595BF79D6A148C739A9310340EEFE6B46641A89531274CE8E02BF6E7CD4` |
| `PrimeVMS-Setup-2.25.2.exe` | `4BDD5F4B857B7AD9D1656ECBEDDCA62233046AB8E7529B1F924FCC79BEE0C09D` |

## FAQ

**Is NexaVMS free?**
Yes. Live view, recording, playback, export, users, distributed deployment and updates
are free, with no per-camera license. AI analytics are also free during the current
testing phase. Prime Cloud and high availability will be paid modules.

**Which cameras are supported?**
Any IP camera with ONVIF or RTSP. NexaVMS finds ONVIF cameras on the network and
detects the stream path.

**Can it replace an NVR?**
NexaVMS records IP cameras directly on a Windows PC or server, with retention by days.
It can also record from existing recorders that provide RTSP streams.

**How many cameras can I add?**
The free version has no per-camera limit. The practical limit depends on hardware and
network. For larger sites, use a distributed deployment with several recording servers.

**Which languages are available?**
English, Portuguese (Brazil) and Spanish, in the apps, the installer and the release
notes.

## Uninstall

Open **Settings > Apps > NexaVMS > Uninstall** (PrimeVMS in installations from before 2.4.0), or use the "Uninstall NexaVMS"
shortcut in the Start menu. Services and firewall rules are removed. The database and
recordings in `C:\ProgramData\Prime VMS` and in the selected recording folder are not
deleted.

## License and support

Copyright © 2026 Prime Building Technology. All rights reserved.

The VMS core (System Manager, Storage and Workstation) is free to use for video
management at the licensee's site. Cloud and high-availability modules require a
commercial license; AI modules are free during the testing phase. The operator is responsible for complying with applicable law,
including data protection laws, when capturing, recording and processing images.

NexaVMS includes third-party components under their own licenses, including
[FFmpeg](https://ffmpeg.org/) and [go2rtc](https://github.com/AlexxIT/go2rtc).

Support: [primebr.com.br](https://primebr.com.br/)
