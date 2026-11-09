<div align="center">

# RAMT

[简体中文](README.md) · **English**

**One connection. One window. Terminal and files side by side.**

Cross-platform SSH client & SFTP file manager · Windows / macOS / Linux

Terminal · SFTP · Jump Hosts · SOCKS5 / HTTP Tunnels · Server Monitor · Local API for Scripts & AI Agents

[![Release](https://img.shields.io/github/v/release/wqpthink/ramt-installer)](https://github.com/wqpthink/ramt-installer/releases/latest)
[![Downloads](https://img.shields.io/github/downloads/wqpthink/ramt-installer/total)](https://github.com/wqpthink/ramt-installer/releases)
![Platform](https://img.shields.io/badge/platform-Windows%20%7C%20macOS%20%7C%20Linux-blue)
![Arch](https://img.shields.io/badge/arch-x64%20%7C%20arm64-blue)

[Download](#-download) · [Get started](#-get-started-in-three-steps) · [Features](#-features) · [FAQ](#-faq) · [Changelog](https://github.com/wqpthink/ramt-installer/releases) · [License](#-license-agreement)

</div>

RAMT puts an interactive SSH terminal and an SFTP file manager in the same tab, sharing one connection. Built for developers, DevOps engineers and system administrators: SSH jump hosts (ProxyJump), SOCKS5 and HTTP proxy on a single port, drag-and-drop transfers, server resource monitoring, and a local REST / WebSocket API that lets scripts and AI agents use the hosts you have already configured.

---

## Why RAMT

- 🪟 **Terminal and files in one view**: Terminal on the left, files on the right, in the same tab, with a draggable split. No more two programs and two sets of connections like **PuTTY + WinSCP** or **Xshell + Xftp**.
- 🪜 **Jump hosts, set up once**: give a target host its jump host chain (up to 5 hops) and just click the target to connect; terminal, files, transfers and proxy tunnels all go through the jump hosts automatically.
- 🌐 **One port, two proxies**: when you reach an internal network through SSH, the same local port serves both **SOCKS5** and **HTTP** proxy - browsers, `curl`, `HTTPS_PROXY` and old tools that only speak HTTP proxy all work directly.
- 🤖 **Usable by scripts and AI agents**: a built-in HTTP API (REST + WebSocket, listening on this computer only by default, optionally on the LAN) lets other programs use the hosts, jump hosts and credentials configured in RAMT to run commands, drive terminals, read and write files, and upload or download. Fingerprint confirmation and passwords are handled through the API, so nobody has to watch the window.
- 📊 **Server status at a glance**: the bottom right corner shows live CPU / GPU, memory and disk usage of the current server (Linux servers) and follows tab switches.
- 🔗 **Configure a host once**: the terminal, file browser, uploads and downloads share one SSH connection, so you enter the password once. When the server runs out of sessions, RAMT opens another connection without asking for the password again.
- 🖱️ **Drag in to upload, drag out to download**: drag files from File Explorer / Finder to upload; select remote files and drag them to the desktop to download (native drag and drop, not a "Save as" dialog).
- 🔒 **Secure by default**: passwords and private keys are encrypted only by the system's secure storage (Windows DPAPI / macOS Keychain / Linux Secret Service) and never written to disk in plain text; a changed server fingerprint shows a red warning and the connection is refused by default.
- ♻️ **Close and reopen, everything is still there**: tab order, split ratio and the current folders are restored and reconnected automatically.
- 🧘 **Nothing extra**: no account, no cloud, no ads, no sidebar - your data stays on your computer.

---

## 📦 Download

Get the latest version from the **[Releases page](https://github.com/wqpthink/ramt-installer/releases/latest)**. Every platform has an installer and a portable version, for x64 and ARM64:

| System | Installer (recommended, one-click updates) | Portable (no installation) |
|---|---|---|
| **Windows 10 / 11** (x64) | `RAMT-x.y.z-win-x64-setup.exe` | `RAMT-x.y.z-win-x64-portable.exe` (a single file; data is kept in `ramt-data/` next to it, so it can live on a USB drive) |
| **Windows on ARM** (e.g. Snapdragon laptops) | `RAMT-x.y.z-win-arm64-setup.exe` | `RAMT-x.y.z-win-arm64-portable.exe` |
| **macOS** (Intel / Apple silicon) | `.dmg` | `.zip` |
| **Linux** (x64 / ARM64) | `.deb` | `.AppImage` (one-click updates; data is kept in `ramt-data/` next to it) |

> **First start** (the packages are not code-signed yet)
> - **Windows**: if "Windows protected your PC" appears, click **More info → Run anyway**. Antivirus software on company computers may block it; ask your IT department to allow it.
> - **macOS**: if macOS says the developer cannot be verified, open **System Settings → Privacy & Security** and click **Open Anyway**.
> - **Linux AppImage**: run `chmod +x RAMT-*.AppImage` first.

---

## 🚀 Get started in three steps

1. **New connection**: click the connections button at the top (or press `Ctrl+T`), click "New connection" in the panel toolbar, enter host and user name and choose password or private key authentication.
2. **Open**: double-click a connection to open its terminal; right-click for "Open Terminal" or "Open File".
3. **Split view**: in a tab, `Ctrl+Shift+F` shows the File view and `Ctrl+Shift+T` the Terminal view - with both open you get the side-by-side split.

The first time you connect to a server, RAMT shows its host fingerprint; once you confirm it, it is remembered.

---

## ✨ Features

### Connections
- Nested groups, drag and drop to sort and move; fuzzy search finds a connection instantly, however many you have.
- Password / private key authentication; private keys in **OpenSSH, PEM and PPK (PuTTY)** format, including keys with a passphrase; keyboard-interactive authentication is supported too.
- Passwords can be left unsaved and asked for when connecting.
- **Jump hosts (ProxyJump)**: choose "Through jump hosts" as the connection mode and pick jump hosts from your existing connections in order (up to 5, reorderable; jump hosts can be created or edited right there). Every hop uses its own credentials and host fingerprint; several targets can share a jump host; when a connection fails, RAMT tells you which host failed. Jump hosts still in use cannot be deleted.
- Import / export connections to move to another computer in one step (including the group structure).

### Terminal
- Multiple tabs; when there are too many, they move into a drop-down list on the right.
- Zoom the font of the current terminal only (`Ctrl +` / `Ctrl -` / `Ctrl+mouse wheel`), other tabs stay as they are.
- Search in the terminal, clickable links, full Unicode and CJK wide-character support.
- Heavy output (such as `tail -f` or build logs) does not freeze the window: built-in back-pressure keeps continuous output arriving line by line in real time.
- System text rendering by default, the same glyphs as your IDE; GPU acceleration can be switched on in Settings.
- Font, font size, cursor style, scrollback lines and light / dark / system theme are configurable.

### File view (SFTP file manager)
- Browse, create, rename, delete, copy / cut / paste, show hidden files, copy path.
- Quick preview of text and images.
- "Open terminal here"; drag a file onto the terminal to insert its path.
- Upload files or whole folders; download to a chosen folder or drag straight to the desktop.
- Transfer panel: progress, cancel, retry; large files are streamed in chunks without using much memory; downloads go to a temporary file that is renamed only when complete, so no half-written files are left behind.
- On name conflicts choose overwrite / skip / keep both.

### SSH tunnels (dynamic port forwarding, like `ssh -D`)
Add them in **Settings → Proxy Tunnels**: choose the connection to go through, the listen address and the port. The tunnel is active whenever that connection has an open session:

```bash
# SOCKS5 (host names resolved on the remote side)
curl --proxy socks5h://127.0.0.1:1080 http://intranet.example/
# HTTP proxy - same port
export HTTPS_PROXY=http://127.0.0.1:1080        # Linux / macOS
$env:HTTPS_PROXY = 'http://127.0.0.1:1080'      # Windows PowerShell
```

Browsers, database clients, Proxifier, Clash and similar tools can point to this port as well.

### Server resource monitor
Switch on "Server resource monitor" in **Settings → Extensions** to see the **CPU / GPU, memory and disk** usage of the current tab's server live in the bottom right corner of the window (refreshed every 2 seconds, highlighted when usage is high). The panel is semi-transparent and does not get in the way, follows tab switches, and stops collecting as soon as you switch it off. Works with Linux servers (GPU requires `nvidia-smi` from the NVIDIA driver); it only reads system information and leaves no files on the server.

### Local API (scripts / automation / AI agents)
**Settings → Local API** shows the address and lets you copy the access token (enabled by default, listening on this computer only at `127.0.0.1:18765`). Other programs use the hosts, jump hosts and credentials configured in RAMT directly over HTTP:

```bash
TOKEN=...   # Settings → Local API → Copy token
curl -H "Authorization: Bearer $TOKEN" http://127.0.0.1:18765/api/v1/hosts
```

- Capabilities: host management, sessions, commands (output, exit code, timeout, cancel), interactive terminals (WebSocket), browsing, reading and writing files, background uploads and downloads with progress events.
- Completely separate from the window: the API uses its own connections and jobs, never takes over or interrupts the sessions in the window, and never shows prompts there - the host fingerprint confirmation on first connect and unsaved passwords are provided in the API requests themselves.
- In Settings you can switch the API off, change the port or open it to the LAN (`0.0.0.0`); changes apply immediately.

All endpoints and error codes are described by the OpenAPI 3.1 document, readable with the token: `http://127.0.0.1:18765/api/v1/openapi.json`.

### Registration
- Without registration you can save **1 connection profile** (jump hosts count too); everything after opening a connection - terminal, File view, uploads and downloads, proxy tunnels, server resource monitor, Local API - works fully.
- **Apply for a registration code**: add the WeChat ID **`starsealun`** and include the machine code of your computer (see next item).
- A registration code is bound to one computer: copy the **machine code** in **Settings → Registration**, send it to the author via WeChat `starsealun`, and paste the registration code issued for that computer; the number of connection profiles is then unlimited. Codes are verified offline, without network access; the settings page shows the licensee and the expiry date (highlighted within 30 days of expiry).
- When a code expires or is removed, RAMT is unregistered again: existing connection profiles are all kept and keep working, you just cannot add new ones.

### Other
- Chinese / English interface.
- Themes: Dark, Light, **Soft Aurora** (a light scheme with a warm misty white background and mint green accents; the terminal switches to the matching deep graphite Lumi Flow colors), or follow the system.
- Checks GitHub for new versions at startup; the installer version updates with one click ("Restart and install").

---

## ⌨️ Keyboard shortcuts

On macOS use `⌘` instead of `Ctrl`.

| Action | Shortcut |
|---|---|
| Open the connections panel (new window) | `Ctrl+T` |
| Close the current tab | `Ctrl+W` |
| Switch tabs | `Ctrl+Tab` / `Ctrl+Shift+Tab` |
| Show / hide the File view | `Ctrl+Shift+F` |
| Show / hide the Terminal view | `Ctrl+Shift+T` |
| Open Settings | `Ctrl+,` |
| Terminal copy / paste | `Ctrl+Shift+C` / `Ctrl+Shift+V` (`Ctrl+C` also copies when text is selected) |
| Terminal font larger / smaller / reset | `Ctrl +` / `Ctrl -` / `Ctrl 0` |
| Files: rename / delete / refresh / parent folder | `F2` / `Delete` / `F5` / `Backspace` |

> On Windows / Linux, while the cursor is in the terminal, `Ctrl+T` and `Ctrl+W` go to the remote shell (for example Bash's delete-word), so they never close a tab by accident.

---

## 🔐 Data and security

| Item | Details |
|---|---|
| Data location | Installer: the system user data folder (e.g. `%APPDATA%\RAMT`); portable: `ramt-data/` next to the program |
| Passwords / private keys | Encrypted by the operating system's secure storage; can only be decrypted on this computer by the current user. On Linux without a usable keyring nothing is saved: passwords are asked for at every connection and private keys cannot be saved |
| Host fingerprints | Must be confirmed on first connect; a change shows a red warning and is refused by default; fingerprints in imported files are always ignored |
| Network | Apart from update checks against GitHub, no third-party services are contacted; no analytics or telemetry |
| Local API | Listens on `127.0.0.1` only by default; every request needs the access token (stored encrypted, can be regenerated at any time, the old token stops working immediately); requests from web pages are refused. When opened to the LAN (`0.0.0.0`) traffic is unencrypted, so only use that on trusted networks; switch the API off in Settings when you don't need it |
| Registration code | Stored in the local database and verified offline (signature and expiry) every time it is used; not included in connection exports, and importing a backup never overwrites it |
| ⚠️ Export files | For easy migration, **exported JSON files contain passwords and private keys in plain text** - keep them as safe as a password book |

---

## 🤔 Is RAMT for you?

**A good fit if you:**
- SSH into servers every day and often upload configuration or download logs.
- Log in to servers with passwords or one-time codes and don't want to type them again and again.
- Need an SSH host to reach internal web pages, databases or APIs.
- Can only reach servers through one or more jump hosts.
- Want scripts or AI agents to use SSH, SFTP, terminals and file transfers through a local API.
- Want a clean tool that just works when you open it.

**Not a fit yet** (these features are missing; if you need them, try [Tabby](https://github.com/Eugeny/tabby), [electerm](https://github.com/electerm/electerm) or [WindTerm](https://github.com/kingToolbox/WindTerm)):
- Local and remote port forwarding (`-L` / `-R`), X11 forwarding, agent forwarding
- Other protocols such as Telnet, serial, RDP, VNC, or use as a local terminal
- Syncing settings across devices, `rz` / `sz`, broadcast input to several terminals, AI assistant

---

## ❓ FAQ

**Saved passwords don't work on a new computer?**
Passwords are bound by the system's secure storage to the original computer and user, so copying the data folder cannot decrypt them. Export the connections on the old computer and import them on the new one.

**Do the portable and installer versions share data?**
Not automatically - they use different data folders. Use export / import to move data between them.

**A transfer was still running when I closed RAMT?**
Unfinished transfers show as "Interrupted" at the next start. They do not resume automatically; start them again manually.

**A tunnel port fails to start?**
Usually the port is already in use: choose another port and click "Retry". The server must also allow TCP forwarding (OpenSSH allows it by default, `AllowTcpForwarding yes`).

**The Local API says the port is already in use?**
Usually another RAMT is running (for example the installer and the portable version at the same time). Choose another port in **Settings → Local API**, or switch the API off if you don't use it.

**"Registration required" - I cannot add more connections?**
Without registration only 1 connection profile can be saved (jump hosts count too). Paste a registration code in **Settings → Registration** to remove the limit; when the code expires the limit applies again, existing connections are not affected.

**New computer or reinstalled system - the registration code no longer works?**
A registration code only works on the computer it was issued for, and the machine code changes when you reinstall the system or switch computers. Send the new machine code (Settings → Registration) to the author via WeChat `starsealun` to get a new registration code.

**The registration code says "retired" or "revoked"?**
The author changed the signing key or revoked that license, so the old code is no longer valid. Add the WeChat ID `starsealun` to contact the author for a new code; entering it restores registration.

**Dragging to the desktop says "Files are ready - drag them out again"?**
Larger files are first downloaded to a local temporary folder; drag them out once more when that is done. For files over 64 MB, right-click "Download to…" is recommended.

---

## 📄 License agreement

RAMT is closed-source software; only installation packages are published. It is free to use (up to 1 saved connection profile); after entering a registration code in **Settings → Registration** the number is unlimited. Installing and using RAMT means you accept the **license agreement**: the installer shows the full text, and after installation it is available at any time in **Settings → About** (the file `LICENSE.txt` in the `resources` folder of the installation). The open-source components used in RAMT and their licenses are listed in `THIRD_PARTY_NOTICES.txt` in the same folder.

---

## 💬 Feedback

- Contact the author (apply for or replace a registration code, anything else): WeChat **`starsealun`**
- Bugs and feature requests: [open an issue](https://github.com/wqpthink/ramt-installer/issues)
- If RAMT helps you, a ⭐ Star is the best encouragement for the author.

<div align="center"><sub>Made with ❤️ by WQPTHINK</sub></div>
