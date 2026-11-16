# Blackbox for Windows: downloads

Installers for **Blackbox**, which explains why a Windows PC crashed, froze or slowed down, from evidence recorded before, during and after it happened.

**[Download the latest version](https://github.com/Inas1234/blackbox-releases/releases/latest)**

This repository only holds the published installers and their release notes. It contains no source code.

## Installing
- Windows 11, 64-bit.
- Run `Blackbox_<version>_x64-setup.exe`. Windows asks for administrator approval once, because setup registers the background service that does the recording.
- The installer is **not code-signed yet**, so Windows SmartScreen may say "Windows protected your PC". Choose **More info**, then **Run anyway**. Each release lists the installer's SHA-256 so you can check the file first:
  ```powershell
  Get-FileHash .\Blackbox_<version>_x64-setup.exe -Algorithm SHA256
  ```

## What gets installed
| Part | Runs as | When it runs |
|---|---|---|
| Blackbox app and tray icon | You | At sign-in (can be switched off in Settings) |
| `Project Blackbox` service, the recorder | LocalSystem | Starts with Windows and restarts itself if it ever stops. The app can start it again without administrator rights. |
| `Project Blackbox Crash-File Helper` | LocalSystem | Only when the recorder needs to read a crash file. Closes after 5 minutes idle. |

Recordings stay on your PC in `C:\ProgramData\ProjectBlackbox`. Nothing is uploaded.

## Updates
From version 0.1.1, the app asks GitHub once a day for the newest release in this repository and offers a **Download** button when there is one (tray menu, one Windows notification, and Settings). The request carries only the app version. Turn it off in Settings → Updates. Version 0.1.0 has no update check: install 0.1.1 over it once.

## Uninstalling
Settings → Apps → Installed apps → Blackbox → Uninstall. Both services are removed. Tick **Delete the application data** to remove the recordings too.

## Reporting a problem
Use the bug report page on the Blackbox website, or open an issue in this repository.
