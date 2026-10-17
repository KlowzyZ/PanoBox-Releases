# PanoBox

**Copy. Find. Paste.** A local clipboard manager for Windows, developed by [KLOWZY](https://klowzy.com).

Keep useful text, images and file paths close at hand. Open the palette with **Ctrl+Shift+V**, type to search, and press **Enter** to paste. The interface is available in **English and Turkish**.

## Download and install

Download from [official releases](https://github.com/KlowzyZ/PanoBox-Releases/releases), together with `SHA256SUMS.txt`. Before running a file, compare its hash in PowerShell: `Get-FileHash .\<file> -Algorithm SHA256`.

- **Installer** — `PanoBox-<version>-win-x64-Setup.exe`. Installs for your Windows account only (no administrator rights), adds a Start menu entry, optional desktop shortcut and optional startup at sign-in, and can be removed from Windows Settings → Apps. Data is stored in `%LOCALAPPDATA%\PanoBox`. Upgrading keeps your data.
- **Portable** — `PanoBox-<version>-win-x64.zip`. Extract it into a folder you control and run `PanoBox.exe`. Data is stored in a `Data` folder next to the app (or `%LOCALAPPDATA%\PanoBox` if that folder is not writable). Keep the documentation and `licenses` folder with the app.

Both target **Windows 11 22H2 (build 22621) or later, x64** and include the .NET runtime. OCR uses an installed Turkish or English Windows recognition language. The files are currently unsigned, so Windows SmartScreen may show a warning; a matching checksum detects a changed download but is not a code signature.

Moving from the portable ZIP to the installer: create a backup in the portable copy (Settings → Backup and data), install, then restore it.

## Everyday use

- **History:** text, images and copied file paths; search, filter, pin, remove duplicates or delete entries. The default limit is 200 entries; pinned entries are kept separately.
- **Templates:** reusable text with variables — `{date}`/`{tarih}`, `{time}`/`{saat}`, `{datetime}`/`{tarihsaat}`, `{day}`/`{gun}`, `{year}`/`{yil}` and `{clipboard}`/`{pano}`. Create and edit them in Settings → Templates, with a live preview, or turn any text entry into a template from the palette.
- **Paste as plain text:** press **Ctrl+Shift+Alt+V** in any app to paste the current clipboard without formatting (configurable in Settings → General; the clipboard is replaced with its plain text). File entries can also be pasted as a list of paths.
- **Tools:** local OCR and QR generation, a paste queue, multi-selection, JSON formatting and explicit actions for links, email and file locations.
- **Appearance:** English or Turkish (or follow Windows), system, dark and light themes, adjustable text size and density.
- **Control:** pause capture from the tray or the palette (⏸), configure shortcuts, choose optional startup/Explorer integration, or use the manual update check.
- **Privacy controls:** choose how long unpinned history is kept (1 hour to 30 days, or until the entry limit), and list apps whose copies are never recorded (for example `Teams` or `mstsc`). Settings suggests source apps already seen in history.

| Key | Action |
| --- | --- |
| Ctrl+Shift+V | Open the palette (configurable) |
| Ctrl+Shift+Alt+V | Paste the clipboard as plain text (configurable) |
| Up / Down, Enter | Select and paste |
| Ctrl+C | Copy the selected entry without pasting |
| Ctrl+F | Focus search |
| Ctrl+1–9 | Paste an entry by its displayed position |
| Ctrl+Tab | Switch History / Templates |
| Ctrl+click | Select several entries |
| Ctrl+Enter / Shift+Enter | Add to queue / paste the queue |
| Ctrl+Shift+Z | Restore an earlier clipboard value; does not undo edits in another app |
| Delete | Delete the selected entry when search is not focused |
| Escape | Hide the palette |

**Search** matches every word, ignoring Turkish accents and case, and ranks matches at the start of an entry or of a word first. Use `"exact phrase"`, `-word` to exclude, and filters: `type:image|text|file` (`tur:resim|metin|dosya`), `app:chrome` (`uyg:`), `pinned:1` (`sabit:1`), `after:yesterday`, `before:2026-01-31`, `after:7d` or `after:2w` (`sonra:`, `once:`, `bugun`, `dun`).

## Your clipboard is sensitive

History, templates, settings, thumbnails and generated QR images are stored locally and **are not encrypted by PanoBox**. Password-manager exclusions, your app exclusion list, clipboard privacy flags and token heuristics reduce accidental capture but cannot identify every secret. Pause capture before copying sensitive information and review saved history when needed. New installations keep unpinned history for 30 days by default; existing installations keep their setting.

PanoBox has no account, advertising, analytics or automatic update check. **Check for updates** contacts GitHub and exposes ordinary connection information such as your IP address and app version. See [PRIVACY.md](PRIVACY.md).

## Backup, restore and removal

Settings → **Backup and data** shows where your data is and offers backup, restore, text export/import, duplicate removal and clearing unpinned history.

- A backup contains history, **image files**, templates and preferences in one file that restores into another folder or PC. Restore checks the whole file first (allowed file names, size limits, checksums), adds only missing entries and never deletes existing history; on failure, images written during the attempt are removed. Startup/Explorer integration is not restored, and a backup cannot switch off privacy protections that are on. Backups from 1.7.0 and earlier (JSON) remain importable, without images.
- **Optional password protection:** with a password, the backup is a `.pbx` file encrypted with AES-256-GCM (key from PBKDF2-SHA256, 600,000 iterations). It is written encrypted from the start, and restore verifies the whole file before using it. PanoBox does not store the password; **a forgotten password cannot be recovered.** Without a password the backup is an unencrypted `.zip`.
- A portable folder can be moved or copied: on the next start PanoBox re-links image history to the images in its own `Data\thumbs` folder without moving or deleting files. Exit from the tray before copying data or replacing files, and never remove your only copy of the data when updating.

To remove the **installed** app, use Windows Settings → Apps; the uninstaller removes startup and Explorer entries and asks whether to delete your data (default: keep). To remove the **portable** app, disable startup and Explorer integration in Settings, exit from the tray, then delete the app folder and its data folder. Deleting history is not secure disk erasure and does not affect separate backups or Windows clipboard history.

## Limits and support

Automatic paste may be blocked in elevated windows or games; use the app at the same privilege level as the target, or paste manually. Captured text is limited to 100,000 characters per entry and expanded templates to 1,048,576 characters. File history records paths, not file contents.

Report problems in [PanoBox-Releases issues](https://github.com/KlowzyZ/PanoBox-Releases/issues) with your Windows version, app version and steps using synthetic data. Do not attach your data folder, database, backups or sensitive screenshots. See [SECURITY.md](SECURITY.md) for vulnerability reporting.

## Development

Application source is maintained in the private `KlowzyZ/PanoBox-Source` repository; [PanoBox-Releases](https://github.com/KlowzyZ/PanoBox-Releases) holds documentation and binaries. PanoBox is proprietary; third-party components keep their licenses. See [LICENSE](LICENSE) and [THIRD-PARTY-NOTICES.md](THIRD-PARTY-NOTICES.md).

Maintainers need Windows, the SDK selected by `global.json` and Inno Setup 6. `pwsh ./release.ps1` restores locked dependencies, audits them, runs the Windows tests, publishes a self-contained x64 build, and creates the portable ZIP and the installer from the same staged files, with SHA-256 checksums. Personal app data is never a release input.

Türkçe: Paleti `Ctrl+Shift+V` ile açın, arayın ve `Enter` ile yapıştırın. Arayüz dili Ayarlar → Genel bölümünden seçilir. Veriler yereldir; yedekler isteğe bağlı olarak parolayla şifrelenebilir.

Copyright © 2026 KLOWZY. All rights reserved.
