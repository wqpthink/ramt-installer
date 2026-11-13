<div align="center">

# RAMT

[简体中文](README.md) · **English**

**One connection. One window. Terminal and files side by side.**

Cross-platform SSH client & SFTP file manager · Windows / macOS / Linux

Terminal · SFTP · Remote Desktop (RDP) · Jump Hosts · SOCKS5 / HTTP Tunnels · Server Monitor · Local API for Scripts & AI Agents

🔒 **Your data stays on your computer** · nothing uploaded, nothing collected · passwords and private keys encrypted by the operating system's credential protection

[![Release](https://img.shields.io/github/v/release/wqpthink/ramt-installer)](https://github.com/wqpthink/ramt-installer/releases/latest)
[![Downloads](https://img.shields.io/github/downloads/wqpthink/ramt-installer/total)](https://github.com/wqpthink/ramt-installer/releases)
![Platform](https://img.shields.io/badge/platform-Windows%20%7C%20macOS%20%7C%20Linux-blue)
![Arch](https://img.shields.io/badge/arch-x64%20%7C%20arm64-blue)
[![Data](https://img.shields.io/badge/data-stays%20on%20your%20computer-brightgreen)](#-data-and-key-security)

[Download](#-download) · [Get started](#-get-started-in-three-steps) · [Features](#-features) · [Data security](#-data-and-key-security) · [FAQ](#-faq) · [Changelog](https://github.com/wqpthink/ramt-installer/releases) · [License](#-license-agreement)

</div>

RAMT puts an interactive SSH terminal and an SFTP file manager in the same tab, sharing one connection; when you need a graphical interface, the same SSH connection also opens the server's remote desktop (RDP), embedded in a tab, without exposing port 3389. Built for developers, DevOps engineers and system administrators: SSH jump hosts (ProxyJump), SOCKS5 and HTTP proxy on a single port, drag-and-drop transfers, server resource monitoring, and a local REST / WebSocket API that lets scripts and AI agents use the hosts you have already configured.

---

## Why RAMT

- 🔒 **Your data stays on your computer**: strictly no access to any private data, no server, nothing uploaded. Passwords and private keys are encrypted and kept only by the operating system's credential protection (Windows DPAPI / macOS Keychain / Linux Secret Service), never written to disk in plain text and never saved as separate key files; a changed server fingerprint shows a red warning and the connection is refused by default. See [Data and key security](#-data-and-key-security).
- 🪟 **Terminal and files in one view**: Terminal on the left, files on the right, in the same tab, with a draggable split. No more two programs and two sets of connections like **PuTTY + WinSCP** or **Xshell + Xftp**.
- 🪜 **Jump hosts, set up once**: give a target host its jump host chain (up to 5 hops) and just click the target to connect; terminal, files, transfers, proxy tunnels and remote desktop all go through the jump hosts automatically.
- 🖥️ **Remote desktop over SSH too**: choose "Open Remote Desktop" on a configured SSH host (jump hosts included) and the server's graphical desktop (GNOME Remote Desktop or xrdp on Linux, or Windows Remote Desktop) opens embedded in a tab, next to the File view if you like. RDP travels through the SSH tunnel, so the server does not expose port 3389 and you need no separate remote desktop client.
- 🌐 **One port, two proxies**: when you reach an internal network through SSH, the same local port serves both **SOCKS5** and **HTTP** proxy - browsers, `curl`, `HTTPS_PROXY` and old tools that only speak HTTP proxy all work directly.
- 🤖 **Usable by scripts and AI agents**: a built-in HTTP API (REST + WebSocket, listening on this computer only by default, optionally on the LAN) lets other programs use the hosts, jump hosts and credentials configured in RAMT to run commands, drive terminals, read and write files, and upload or download. Fingerprint confirmation and passwords are handled through the API, so nobody has to watch the window.
- 📊 **Server status at a glance**: the bottom right corner shows live CPU / GPU, memory and disk usage of the current server (Linux servers) and follows tab switches.
- 🔗 **Configure a host once**: the terminal, file browser, uploads, downloads and remote desktop share one SSH connection, so you enter the password once. When the server runs out of sessions, RAMT opens another connection without asking for the password again.
- 🖱️ **Drag in to upload, drag out to download**: drag files from File Explorer / Finder to upload; select remote files and drag them to the desktop to download (native drag and drop, not a "Save as" dialog).
- ♻️ **Close and reopen, everything is still there**: tab order, split ratio and the current folders are restored and reconnected automatically.
- 🧘 **Nothing extra**: no account, no cloud, no ads, no sidebar - your data stays on your computer.

---

## 📦 Download

Get the latest version from the **[Releases page](https://github.com/wqpthink/ramt-installer/releases/latest)** (`x.y.z` is the version). Every platform has an installer and a portable version, for x64 and ARM64:

| System | Installer (recommended) | Portable (no installation) |
|---|---|---|
| **Windows 10 / 11** (x64) | `RAMT-x.y.z-win-x64-setup.exe` | `RAMT-x.y.z-win-x64-portable.zip` (unpack it and run `RAMT.exe` inside; data is kept in `ramt-data/` in the same folder, so the whole folder can live on a USB drive) |
| **Windows on ARM** (e.g. Snapdragon laptops) | `RAMT-x.y.z-win-arm64-setup.exe` | `RAMT-x.y.z-win-arm64-portable.zip` |
| **macOS** (Apple silicon, M series) | `RAMT-x.y.z-mac-arm64.dmg` | `RAMT-x.y.z-mac-arm64.zip` |
| **macOS** (Intel) | `RAMT-x.y.z-mac-x64.dmg` | `RAMT-x.y.z-mac-x64.zip` |
| **Linux** (x64, Debian / Ubuntu etc.) | `RAMT-x.y.z-linux-amd64.deb` | `RAMT-x.y.z-linux-x86_64.AppImage` (data is kept in `ramt-data/` next to it) |
| **Linux** (ARM64) | `RAMT-x.y.z-linux-arm64.deb` | `RAMT-x.y.z-linux-arm64.AppImage` |

**Updates**: the Windows installer version and the Linux AppImage update with one click inside the app; macOS, deb and the Windows portable version open the download page - install the new version over the old one, your data is kept (for the Windows portable version, unpack the new zip over the old folder; `ramt-data/` stays).

> **First start** (the packages are not code-signed yet)
> - **Windows**: if "Windows protected your PC" appears, click **More info → Run anyway**. Antivirus software on company computers may block it; ask your IT department to allow it.
> - **Windows portable**: first unpack the whole zip into a folder (e.g. `D:\Tools\RAMT`), then run `RAMT.exe` inside it; don't start it from within the zip.
> - **macOS**: drag RAMT into "Applications" and open it; if macOS says the developer cannot be verified, open **System Settings → Privacy & Security** and click **Open Anyway**. If it says the app "is damaged and can't be opened", run `xattr -dr com.apple.quarantine /Applications/RAMT.app` in Terminal and open it again.
> - **Linux deb**: `sudo apt install ./RAMT-x.y.z-linux-amd64.deb` (use the ARM64 file on ARM64).
> - **Linux AppImage**: run `chmod +x RAMT-*.AppImage` first, then double-click it or start it from a terminal.

---

## 🚀 Get started in three steps

1. **New connection**: click the connections button at the top (or press `Ctrl+T`), click "New connection" in the panel toolbar, enter host and user name and choose password or private key authentication.
2. **Open**: double-click a connection to open its terminal; right-click for "Open Terminal", "Open File" or "Open Remote Desktop".
3. **Split view**: in a tab, `Ctrl+Shift+F` shows the File view and `Ctrl+Shift+T` the Terminal view - with both open you get the side-by-side split.

The first time you connect to a server, RAMT shows its host fingerprint; once you confirm it, it is remembered.

---

## ✨ Features

### Connections
- Nested groups, drag and drop to sort and move; fuzzy search finds a connection instantly, however many you have.
- Password / private key authentication; private keys in **OpenSSH, PEM and PPK (PuTTY)** format, including keys with a passphrase; keyboard-interactive authentication is supported too.
- Passwords can be left unsaved and asked for when connecting.
- **Jump hosts (ProxyJump)**: choose "Through jump hosts" as the connection mode and pick jump hosts from your existing connections in order (up to 5, reorderable; jump hosts can be created or edited right there). Every hop uses its own credentials and host fingerprint; several targets can share a jump host; when a connection fails, RAMT tells you which host failed. Jump hosts still in use cannot be deleted.
- "Open Terminal" and "Open File" open a new tab each time by default; to switch to an open tab instead, tick "Reuse open Terminal and File tabs" in **Settings → Connection → Connection behavior**.
- Import / export connections to move to another computer in one step (including the group structure).

### Terminal
- Multiple tabs, the current one easy to spot; when there are too many, they move into a drop-down list on the right.
- Zoom the font of the current terminal only (`Ctrl +` / `Ctrl -` / `Ctrl+mouse wheel`), other tabs stay as they are.
- Search in the terminal, clickable links, full Unicode and CJK wide-character support.
- Right-click "Open current folder in files": the file view goes straight to the folder the shell is in (Linux servers; on other systems the shell has to report its folder with OSC 7), also on servers that limit the number of sessions per connection.
- Heavy output (such as `tail -f` or build logs) does not freeze the window: built-in back-pressure keeps continuous output arriving line by line in real time; dragging the split or resizing the window does not make full-screen programs such as vim or top redraw again and again.
- System text rendering by default, the same glyphs as your IDE; GPU acceleration can be switched on in Settings.
- Font, font size, cursor style, scrollback lines and light / dark / system theme are configurable.

### File view (SFTP file manager)
- Browse, create, rename, delete, copy / cut / paste, show hidden files, copy path.
- Quick preview of text and images.
- "Open terminal here"; drag a file onto the terminal to insert its path.
- Upload files or whole folders; download to a chosen folder or drag straight to the desktop.
- Transfer panel: progress, cancel, retry; large files are streamed in chunks without using much memory; downloads go to a temporary file that is renamed only when complete, so no half-written files are left behind.
- On name conflicts choose overwrite / skip / keep both.

### Remote desktop (RDP)
Choose **Open Remote Desktop** in a connection's context menu or action list. The first time you enter the RDP user name and password (the default address is `127.0.0.1:3389`, the RDP service on the SSH host itself); afterwards it opens directly.

- **Through SSH**: the RDP connection is forwarded through the host's existing SSH connection (jump hosts included) and shares it with terminals and files; closing a remote desktop tab only ends that desktop.
- **Embedded**: each remote desktop has its own tab and can be split with the File view (uploads and downloads stay in the File view); desktops of different hosts can be open at once, while a host has a single remote desktop tab - opening it again returns to that tab instead of connecting twice.
- **Input**: mouse (left / right / middle button, wheel, drag) and keyboard (shortcuts, F1-F12, arrows...). Once you click the desktop it owns the keyboard: every key goes to the remote side, `Ctrl+W`, `Ctrl+Tab` and friends do nothing in RAMT, and clicking toolbar buttons does not take the keyboard away. Input methods (Chinese and others) are the remote desktop's own by default; switch on "Local input method" in the toolbar to type with this computer's input method, the text is then sent as Unicode. The Windows key, `Alt+Tab` and `Ctrl+Alt+Del` are taken by the local system first: in full screen they go to the remote side (when the system allows it), in a window send them with "Send keys" in the toolbar.
- **Full screen and resolution**: full screen (`Ctrl+Alt+Enter`), fit to window / actual size; "Fit to window" always fills the view (keeping the aspect ratio) and grows with it when the main window is maximized or full screen; the resolution is "Fit to window (auto)" or 1024×768 up to 1920×1080, changed live to the new window size when the server supports it (sharpest picture), otherwise the picture is scaled to the window and a hint offers to reconnect at the new size; high-DPI screens get the matching scale factor.
- **A toolbar that takes no room**: the toolbar floats over the top of the remote desktop; after connecting it shows for a few seconds and then slides away, so the desktop fills the whole tab. Move the pointer to the top edge of the desktop, or simply past it, to bring it back right away; it slides away again when you move off. While not connected the toolbar stays visible.
- **Clipboard**: text clipboard shared between this computer and the remote desktop when the server supports it (no files).
- **Security**: TLS (with Network Level Authentication), the server certificate is confirmed on first connect and a change is warned about; the RDP password is encrypted by the system's secure storage, or not saved at all if you prefer.
- **Disconnects**: the tab shows the state and the reason of errors; when SSH drops or the server ends the session it is marked disconnected and reconnects with one click. Remote desktop tabs come back after a restart but only connect when you click "Connect".
- **Server requirements**: an RDP service must already run on the remote side (GNOME Remote Desktop, xrdp or Windows Remote Desktop); RAMT never installs or changes anything on the server.

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
- Without registration you can save **1 connection profile** (jump hosts count too); everything after opening a connection - terminal, File view, remote desktop, uploads and downloads, proxy tunnels, server resource monitor, Local API - works fully.
- **Apply for a registration code**: add the WeChat ID **`starsealun`** and include the machine code of your computer (see next item).
- A registration code is bound to one computer: copy the **machine code** in **Settings → Registration**, send it to the author via WeChat `starsealun`, and paste the registration code issued for that computer; the number of connection profiles is then unlimited. Codes are verified offline, without network access; the settings page shows the licensee and the expiry date (highlighted within 30 days of expiry).
- When a code expires or is removed, RAMT is unregistered again: existing connection profiles are all kept and keep working, you just cannot add new ones.

### Other
- Chinese / English interface.
- Themes: Dark, Light, **Soft Aurora** (a light scheme with a warm misty white background and mint green accents; the terminal switches to the matching deep graphite Lumi Flow colors), or follow the system.
- Checks GitHub for new versions at startup: a new version opens a window with what changed, where you can update right away, choose "Later" or "Skip this version" (newer versions are offered again); the Windows installer version and the Linux AppImage update with one click ("Restart and install"), the other versions open the download page.

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
| Remote desktop full screen on / off | `Ctrl+Alt+Enter` (or the toolbar button) |
| Open Settings | `Ctrl+,` |
| Terminal copy / paste | `Ctrl+Shift+C` / `Ctrl+Shift+V` (`Ctrl+C` also copies when text is selected) |
| Terminal font larger / smaller / reset | `Ctrl +` / `Ctrl -` / `Ctrl 0` |
| Files: rename / delete / refresh / parent folder | `F2` / `Delete` / `F5` / `Backspace` |

> On Windows / Linux, while the cursor is in the terminal, `Ctrl+T` and `Ctrl+W` go to the remote shell (for example Bash's delete-word), so they never close a tab by accident. After you click into a remote desktop, every key (including the shortcuts above and `Alt+F4`) goes to the remote desktop.

---

## 🔐 Data and key security

> **RAMT is strictly forbidden from obtaining any private data of its users.** All data stays on your own computer and is never uploaded. RAMT has no server of its own and sends no data to the author or any third party.

### Everything stays on this computer

- Connection profiles, groups, passwords, private keys, host fingerprints, settings, session layout and logs are stored only in RAMT's data folder on this computer (installer: the system user data folder, e.g. `%APPDATA%\RAMT`; portable: `ramt-data/` next to the program).
- No account, no cloud sync, no analytics, no telemetry, no crash reporting.
- RAMT only goes online in these cases, and none of them sends your configuration or credentials:
  - **Connections you open**: terminal (SSH), File view (SFTP) and remote desktop data travels only between this computer and the servers you configured (and the jump hosts you configured).
  - **Update checks**: only public version information is read from GitHub and installers are downloaded from there; turn off "Check for updates automatically at startup" in **Settings → About**.
- Registration codes are verified offline. The machine code is only used to check the registration code on this computer; it leaves your computer only when you send it to the author yourself to apply for a code.

### Passwords and private keys are kept by the operating system's credential protection

- Saved SSH passwords, private keys, key passphrases, remote desktop passwords and the Local API token are all encrypted by the operating system's credential protection: Windows DPAPI, macOS Keychain, Linux Secret Service (GNOME Keyring / KWallet).
- The encrypted data is kept only in RAMT's data folder on this computer. Only the same operating system user on this computer can decrypt it; copied to another computer or user account it cannot be read.
- **Private keys are not stored separately**: RAMT never creates, copies or saves private key files of its own and never changes your original key file. Key content loaded from a file is kept only in the encrypted form described above.
- Never written to disk in plain text, and never written to logs, configuration or temporary files. Private keys are only used on this computer to sign the SSH authentication; the key itself is never sent to a server or anywhere else.
- Without usable secure storage (e.g. Linux without a keyring) RAMT saves nothing: passwords are asked for at every connection and private keys cannot be saved. With "Ask for passwords on every connection" as the credential storage setting in **Settings → Security**, passwords are not saved.
- **Settings → Security → Clear all saved credentials** removes them all at once.
- The Local API can connect with saved credentials, but no endpoint ever returns a password, private key or passphrase.

### The only exception: exports you make yourself

- For easy migration, **files created by "Export connections" contain passwords and private keys in plain text** (remote desktop passwords are not exported). The file is written only to the local place you choose and RAMT never uploads it. Keep it as safe as a password book and delete it when you no longer need it.

### Other safeguards

| Item | Details |
|---|---|
| Host fingerprints | Must be confirmed on first connect; a change shows a red warning and is refused by default; fingerprints in imported files are always ignored |
| Remote desktop | RDP only goes through the SSH tunnel; the temporary local port listens on `127.0.0.1` only and accepts nothing but its own session; the TLS certificate is confirmed on first use and changes are warned about; the RDP password is stored encrypted, never logged and not included in connection exports |
| Local API | Listens on `127.0.0.1` only by default; every request needs the access token (stored encrypted, can be regenerated at any time, the old token stops working immediately); requests from web pages are refused. When opened to the LAN (`0.0.0.0`) traffic is unencrypted, so only use that on trusted networks; switch the API off in Settings when you don't need it |
| Registration code | Stored in the local database and verified offline (signature and expiry) every time it is used; not included in connection exports, and importing a backup never overwrites it |

---

## 🤔 Is RAMT for you?

**A good fit if you:**
- SSH into servers every day and often upload configuration or download logs.
- Log in to servers with passwords or one-time codes and don't want to type them again and again.
- Need an SSH host to reach internal web pages, databases or APIs.
- Can only reach servers through one or more jump hosts.
- Occasionally need a server's graphical desktop without opening a remote desktop port to the outside.
- Want scripts or AI agents to use SSH, SFTP, terminals and file transfers through a local API.
- Want a clean tool that just works when you open it.

**Not a fit yet** (these features are missing; if you need them, try [Tabby](https://github.com/Eugeny/tabby), [electerm](https://github.com/electerm/electerm) or [WindTerm](https://github.com/kingToolbox/WindTerm)):
- Local and remote port forwarding (`-L` / `-R`), X11 forwarding, agent forwarding
- Other protocols such as Telnet, serial, VNC, or use as a local terminal; the remote desktop transfers no files and no sound
- Syncing settings across devices, `rz` / `sz`, broadcast input to several terminals

---

## ❓ FAQ

**Saved passwords don't work on a new computer?**
Passwords are bound by the system's secure storage to the original computer and user, so copying the data folder cannot decrypt them. Export the connections on the old computer and import them on the new one.

**I used the single-exe portable version before - is my data still there with the zip?**
Up to 0.1.1 the Windows portable version was a single exe with its data in the `ramt-data` folder next to it. Copy that folder into the newly unpacked folder, next to `RAMT.exe`, and your connections, passwords and settings are back (same computer, same system user).

**Do the portable and installer versions share data?**
Not automatically - they use different data folders. Use export / import to move data between them.

**Why did "Open Terminal" open another tab?**
By default every open creates a new tab, so you can work in several terminals at once. To return to the open tab instead, tick "Reuse open Terminal and File tabs" in **Settings → Connection → Connection behavior**. Remote desktops are not affected: a host always has a single remote desktop tab.

**A transfer was still running when I closed RAMT?**
Unfinished transfers show as "Interrupted" at the next start. They do not resume automatically; start them again manually.

**The remote desktop does not connect?**
First check that the RDP service runs on the server (GNOME Remote Desktop, for example, must be enabled on the server with `grdctl` including a user name and password) and that the address and port can be reached from the SSH host; the SSH server must allow TCP forwarding (`AllowTcpForwarding yes`). The error message tells whether SSH, the RDP port, the certificate or the user name / password is the problem.

**The remote desktop looks blurry?**
With "Fit to window", if the server cannot change its resolution to the window size, the picture is scaled and text looks slightly soft. Reconnect when RAMT offers it (the resolution is then requested for the current window size), or switch to "Actual size" in the toolbar for a one-to-one picture.

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

**RAMT froze or crashed - how do I report it?**
Unresponsive windows, crashed processes and similar events are written to `ramt.log` in the data folder (see "Everything stays on this computer" above). Attach this file when you report the problem: the log contains no passwords or private keys, but it can contain host names, user names and file paths, so you may want to look at it before sending it.

---

## 📄 License agreement

RAMT is closed-source software; only installation packages are published. It is free to use (up to 1 saved connection profile); after entering a registration code in **Settings → Registration** the number is unlimited. Installing and using RAMT means you accept the **[license agreement](LICENSE.txt)** (Chinese and English); the `LICENSE.txt` published in this repository is authoritative.

---

## 💬 Feedback

- Contact the author (apply for or replace a registration code, anything else): WeChat **`starsealun`**
- Bugs and feature requests: [open an issue](https://github.com/wqpthink/ramt-installer/issues)
- If RAMT helps you, a ⭐ Star is the best encouragement for the author.

<div align="center"><sub>Made with ❤️ by WQPTHINK</sub></div>
