<div align="center">

**English** · [Português](README.pt-BR.md) · [Español](README.es.md)

# PRIME**VMS** — Free VMS software for IP cameras

**Free video management system (VMS) for CCTV: live view, 24/7 recording, playback and export.**
Free core with **no per-camera license fees** · advanced modules on **affordable plans**.

[![Latest version](https://img.shields.io/github/v/release/Daniel1ux/Prime-VMS-Public?label=latest%20version&color=c5e82e&labelColor=0a1626)](https://github.com/Daniel1ux/Prime-VMS-Public/releases/latest)
![Windows 10/11 64-bit](https://img.shields.io/badge/Windows-10%20%2F%2011%20(64--bit)-0b2545)
![ONVIF / RTSP](https://img.shields.io/badge/cameras-ONVIF%20%2F%20RTSP-00e5ff?labelColor=0a1626)
![Languages](https://img.shields.io/badge/languages-EN%20%C2%B7%20PT%20%C2%B7%20ES-c5e82e?labelColor=0a1626)

### [⬇ Download PrimeVMS for free](https://github.com/Daniel1ux/Prime-VMS-Public/releases/latest) · [🌐 Website](https://daniel1ux.github.io/Prime-VMS-Public/)

</div>

**PrimeVMS** is a professional **video management system (VMS)** for Windows — free
**CCTV / NVR software** to record, watch live and play back **IP cameras** from any
brand that supports **ONVIF or RTSP**. The VMS core is **free to use**, with no
per-camera license. You only pay for what adds value: **AI video analytics**,
**cloud access** and **high availability** — on affordable plans.

Made by [Prime Building Technology](https://primebr.com.br/), available in
**English, Portuguese and Spanish**.

---

## Why PrimeVMS

| | PrimeVMS | Traditional VMS |
|---|---|---|
| Core license | **Free** — no per-camera fees | Paid per camera / channel |
| Cameras | **Any ONVIF / RTSP camera** | Often tied to a brand |
| Deployment | **One installer**: single PC → distributed servers | Different products / editions |
| Updates | **One click inside the app**, with automatic rollback | Download and reinstall |
| Advanced features | **Modules on affordable plans** — pay only for what you use | Expensive bundles |
| Languages | **English · Português · Español** | Varies |

## Features — free core

- 📹 **Works with your cameras** — automatic **ONVIF discovery** and RTSP path
  detection (just enter the camera's user and password), with built-in RTSP path
  patterns for Hikvision/Annke, Dahua/Intelbras, Axis and Reolink, plus generic ONVIF/RTSP.
- 🔴 **24/7 recording** to disk (segmented MP4, no re-encoding), with a recording
  catalog and **retention by days**.
- 🖥️ **Live view** in layouts up to 4×4, full screen, **multi-monitor** and video
  wall, with **GPU-accelerated decoding**.
- ⏱️ **Playback** with a 24 h timeline and zoom, **bookmarks**, synchronized
  multi-camera playback and on-screen date/time.
- 📤 **Export** of images and video with **anti-tamper watermark** (logo + date/time).
- 👥 **Users and roles** (administrator, supervisor, operator) enforced on the server.
- 🏢 **Scales with you** — everything on one PC, or a **distributed** setup with a
  central server, several recording servers and many operator stations.
- 🔄 **Automatic updates** — check for updates inside the app; only what changed is
  downloaded, digitally signed, with automatic rollback if anything fails.
- 🌐 **Three languages** — English, Portuguese and Spanish (switch in the app).

## Paid modules — affordable plans

| Module | Status |
|---|---|
| 🤖 **AI video analytics** — people counting | ✅ Available |
| 🤖 More analytics — object detection, line crossing/intrusion, loitering, queue detection, fire & smoke, PPE, face recognition, license plate recognition (LPR), abandoned objects, smart search | 🛠️ In development |
| ☁️ **Prime Cloud** — remote access and mobile **without opening ports** (no NAT setup) | 🔜 Coming soon |
| 🛡️ **High availability** — redundant central server (master/standby) | 🔜 Coming soon |

Plans are priced to fit small and mid-size projects.
**[Contact Prime](https://primebr.com.br/)** for a quote.

## What's in the installer

One installer (`PrimeVMS-Setup-X.Y.Z.exe`) with three components — you choose what
to install on each computer:

| Component | What it does |
|---|---|
| **System Manager** | Central server: cameras, users and permissions, site settings. Runs as a Windows service. |
| **Storage** | Recording server: records cameras, stores and serves recordings. Runs as a Windows service. |
| **Workstation** | Operator station: live layouts, playback timeline, image/video export. |

Services start with Windows and restart automatically if they stop. No .NET or other
runtime needs to be installed.

## Requirements

- **Windows 10 or 11, 64-bit**.
- **Administrator** permission to install and update.
- **IP cameras with ONVIF/RTSP** on the same network.
- Storage: a disk with room for the retention you want (recordings live outside the
  program folder).
- Workstation: a GPU with hardware video decoding is recommended for large layouts.

## Installation

1. Download `PrimeVMS-Setup-X.Y.Z.exe` from the [latest release](https://github.com/Daniel1ux/Prime-VMS-Public/releases/latest).
2. Run it, choose the language (English, Português or Español) and accept the
   administrator prompt.
   > The installer is not code-signed yet. If Windows shows *"Windows protected your
   > PC"*, click **More info → Run anyway**.
3. Choose the **deployment model**:
   - **A single computer (everything on this PC)** — System Manager, Storage and
     Workstation already connected. For small projects (up to about 16 cameras), no
     recording redundancy.
   - **Distributed installation** — select each computer's role: System Manager on a
     dedicated server, Storage on one or more recording servers, Workstation on the
     operator computers.
4. Open the **Workstation** (or the **System Manager Console**).

**First login:** user `admin`, password `admin`. **Change the password right after
signing in.** The language chosen in the installer becomes the apps' language; each
user can change it at any time with the 🌐 **PT · EN · ES** selector.

### Network ports

| Port (TCP) | Service |
|---|---|
| **58100** | System Manager |
| **58200** | Storage |

The installer opens these ports in Windows Firewall. In distributed installations,
make sure the network allows them between servers and Workstations.

## Updates

Since version **1.0.4**, PrimeVMS updates itself **from inside the apps**:

1. In the Workstation, System Manager Console or Storage Console, click
   **⟳ Check for updates** (sidebar or login screen). The apps also check on their own
   and show a **new version** notice.
2. Read what's new and click **Update now** (asks for administrator permission).
3. PrimeVMS updates **everything installed on that computer at once**: stops the
   services, closes the apps, installs, restarts the services, checks they respond on
   the new version and reopens the app. It takes about a minute.

- **Downloads only what changed** — usually about 1 MB, not the whole installer.
- **Digitally signed** — altered or corrupted files are rejected before any change.
- **Rolls back automatically** — if a service fails to start (or power drops midway),
  the previous version is restored.
- **Your data stays** — settings, cameras, users and recordings are kept; the database
  is upgraded automatically.

> Recording pauses for a few seconds during an update. On critical sites, update
> during quiet hours.

**Offline update:** copy a version's update files (`update-manifest.json`,
`update-manifest.json.sig` and the `pack-*.zip` files) to a folder and run, as
administrator:

```
"C:\Program Files\Prime VMS\Updater\PrimeVMS Updater.exe" --apply --source folder:D:\primevms-update
```

## Versions

| Version | Date | Installer | In-app updates |
|---|---|---|---|
| **[1.0.5](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.0.5)** ⭐ recommended | 2026-10-18 | `PrimeVMS-Setup-1.0.5.exe` (315 MB) | ✅ Yes |
| [1.0.4](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.0.4) | 2026-10-18 | `PrimeVMS-Setup-1.0.4.exe` (314 MB) | ✅ Yes |
| [1.0.3](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.0.3) | 2026-10-17 | `PrimeVMS-Setup-1.0.3.exe` (314 MB) | ⚠️ Old channel — install 1.0.5 |
| [1.0.2](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.0.2) | 2026-06-06 | `PrimeVMS-Setup-1.0.2.exe` (424 MB) | ❌ No |
| [1.0.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.0.0) | 2026-06-01 | `PrimeVMS-Setup-1.0.0.exe` (265 MB) | ❌ No |

Older versions are kept for reference only. **If you have 1.0.3 or older**, install the
latest version with the setup once — your data is kept — and from then on update
inside the app. Release notes are on each [release page](https://github.com/Daniel1ux/Prime-VMS-Public/releases).

### Verify your download (optional)

```powershell
Get-FileHash .\PrimeVMS-Setup-1.0.5.exe -Algorithm SHA256
```

| File | SHA-256 |
|---|---|
| `PrimeVMS-Setup-1.0.5.exe` | `97BAA1164289F40D35D530A1C9AC7A338E73CAA4197B4BF06473DD2FCCFFF746` |
| `PrimeVMS-Setup-1.0.4.exe` | `405B120D9E5BD56915E8CDE0A65D2D55CFD6A9020EB49992CE4177E1E3D71ED4` |
| `PrimeVMS-Setup-1.0.3.exe` | `97B2E821B3182DF8619003B73626AC234D8DA9A407FBD0434E6BDB804F7ED8D0` |
| `PrimeVMS-Setup-1.0.2.exe` | `8810E256670D7D20E791989B38D56D3878F0A753F126A9B990067A2E84FA65E7` |
| `PrimeVMS-Setup-1.0.0.exe` | `827586BE66C64AF0FD3538A8AE00A052ED8CDBF6890F73FD3EABA8DD9448BF0C` |

## FAQ

**Is PrimeVMS really free?**
Yes. The VMS core — live view, recording, playback, export, users, distributed
servers and updates — is free, with no per-camera license fees. Only the advanced
modules (AI analytics, Prime Cloud, high availability) are paid, on affordable plans.

**Which cameras are supported?**
Any IP camera with **ONVIF** or **RTSP**, from any manufacturer. PrimeVMS finds ONVIF
cameras on the network and discovers the stream path by itself.

**Is it an NVR replacement?**
PrimeVMS records IP cameras directly on a Windows PC or server (software NVR), with
retention by days, and also works alongside existing recorders that expose RTSP.

**How many cameras can I use?**
There is no license limit per camera in the free core. The practical limit is your
hardware and network; for larger projects, use the distributed installation with
several recording servers.

**Which languages are available?**
English, Portuguese (Brazil) and Spanish — in the apps, the installer and the
release notes.

## Uninstall

**Windows Settings → Apps → PrimeVMS → Uninstall** (or the "Uninstall PrimeVMS"
shortcut in the Start menu). Services and firewall rules are removed. Data (database
and recordings) stays in `C:\ProgramData\Prime VMS` and in the recording folder you
chose, and is **not** deleted automatically.

## License and support

Copyright © 2026 **Prime Building Technology**. All rights reserved.
The VMS core (System Manager, Storage and Workstation) is free to use for managing
video at the licensee's site; AI, cloud and high-availability modules require a
commercial license. The operator is responsible for complying with applicable law
(including data-protection laws such as the LGPD/GDPR) when capturing, recording and
processing images.

PrimeVMS includes third-party components under their own licenses, such as
[FFmpeg](https://ffmpeg.org/) and [go2rtc](https://github.com/AlexxIT/go2rtc).

**Support and contact:** [primebr.com.br](https://primebr.com.br/)
