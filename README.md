# PanoBox

**Copy. Find. Paste.** A portable Windows clipboard manager developed by [KLOWZY](https://klowzy.com).

Keep useful text, images and file paths close at hand. Open the palette with **Ctrl+Shift+V**, type to search, and press **Enter** to paste. The current interface is in Turkish; this guide explains the main controls in English.

## Download and run

1. Download the latest stable `PanoBox-<version>-win-x64.zip` and `SHA256SUMS.txt` from [official releases](https://github.com/KlowzyZ/PanoBox-Releases/releases).
2. In PowerShell, run `Get-FileHash .\PanoBox-<version>-win-x64.zip -Algorithm SHA256` and compare the complete hash with `SHA256SUMS.txt`.
3. Extract the ZIP into a folder you control. Run `PanoBox.exe` as your normal Windows user. Keep the documentation and `licenses` folder together with the app.

The portable package targets **Windows 11 22H2 (build 22621) or later, x64**. It includes the .NET runtime; no separate .NET installation is required. OCR uses an installed Turkish or English Windows recognition language and is unavailable when neither is installed. The executable is currently unsigned; Windows may display a SmartScreen warning. A matching checksum detects a changed download, but is not a code signature.

## Everyday use

- **History:** text, images and copied file paths; search, filter, pin, remove duplicates or delete entries. The default history limit is 200; pinned entries are retained separately.
- **Templates:** reusable text with variables such as `{tarih}` (date), `{saat}` (time), `{tarihsaat}` (date and time), `{gun}` (day), `{yil}` (year) and `{pano}` (clipboard).
- **Tools:** local OCR and QR generation, a paste queue, multi-selection, JSON formatting and explicit actions for links, mail and file locations.
- **Appearance:** system, dark and light themes; adjustable text size and density.
- **Control:** pause capture from the tray or the palette (⏸), configure the hotkey, choose optional startup/Explorer integration, or use the manual update check.
- **Privacy controls:** choose how long unpinned history is kept (1 hour to 30 days, or until the item limit), and list apps whose copies are never recorded (for example `Teams` or `mstsc`). Settings suggests source apps already seen in history.

| Key | Action |
| --- | --- |
| Ctrl+Shift+V | Open the palette; configurable in settings |
| Up / Down, Enter | Select and paste |
| Ctrl+F | Focus search |
| Ctrl+1–9 | Paste an item by its displayed position |
| Ctrl+Tab | Switch History / Templates |
| Ctrl+click | Select several items |
| Ctrl+Enter / Shift+Enter | Add to queue / paste the next queued item |
| Ctrl+Shift+Z | Restore an earlier clipboard value; does not undo edits in another app |
| Delete | Delete the selected entry when search is not focused |
| Escape | Hide the palette |

Search accepts several words and Turkish-insensitive matching. Filters include `tur:resim` (images), `tur:metin` (text), `tur:dosya` (files), `uyg:chrome` (source app) and `sabit:1` (pinned).

## Your clipboard is sensitive

History, templates, settings, thumbnails and generated QR images are stored locally. **They are not encrypted by PanoBox.** Password-manager exclusions, your own app exclusion list, clipboard privacy flags and token heuristics reduce accidental capture but cannot identify every secret. Pause capture before copying sensitive information and review saved history when needed. New installations keep unpinned history for 30 days by default; existing installations keep their current setting.

PanoBox has no account, advertising SDK, analytics SDK or automatic update check. Clicking **Check for updates** contacts GitHub and exposes ordinary connection information such as your IP address and app version. Opening a saved link or the website uses your default browser/application. See [PRIVACY.md](PRIVACY.md) for storage, backup and deletion details.

## Data, backup and removal

PanoBox prefers a writable `Data` folder beside `PanoBox.exe`; otherwise it uses `%LOCALAPPDATA%\PanoBox`. Settings shows the active folder and can open it. Exit from the tray before copying data or replacing binaries. Verify an update in a separate folder, then replace application files in your existing installation while retaining your existing `Data` or fallback data folder. A portable folder can be moved or copied: on the next start PanoBox re-links image history to the images in its own `Data\thumbs` folder without moving or deleting files. Never replace or remove your only copy of the data when updating.

Settings offers **Yedekle…** (backup), **Geri yükle…** (restore), **Metin olarak dışa aktar…** (text export) and **Sabitlenmemiş geçmişi temizle…** (clear unpinned entries). A backup is a single `.zip` file containing history, **image files**, templates and preferences, with a SHA-256 manifest. It can be restored into another folder or computer. Restore validates the whole file first (allowed file names, size limits, checksums), adds only missing entries and never deletes existing history; on failure, images written during the attempt are removed. Startup/Explorer integration is not restored, and a backup cannot switch off privacy protections that are on. Older JSON backups remain importable (without images). Backups and exports are **not encrypted** and contain clipboard content.

To remove PanoBox, disable optional startup and Explorer integration in settings, exit from the tray, then delete the app folder and the active data folder. Deleting history is not secure disk erasure and does not erase your separate backups or Windows clipboard history.

## Limits and support

Automatic paste may be blocked in elevated windows or games. Use the app at the same privilege level as the target and paste manually where needed. PanoBox does not need administrator rights. Captured text is limited to 100,000 characters per entry. Expanded templates are limited to 1,048,576 characters; shorten repeated clipboard placeholders if the app reports an oversized result. The original file content is not copied when recording file paths. Clipboard undo restores clipboard content only.

Report ordinary problems in [PanoBox-Releases issues](https://github.com/KlowzyZ/PanoBox-Releases/issues), including Windows version, app version and steps using synthetic data. Do not attach your `Data` folder, clipboard database, sensitive screenshots or unsanitized backups/logs. See [SECURITY.md](SECURITY.md) for vulnerability reporting.

## Development

Application source is maintained in the private `KlowzyZ/PanoBox-Source` repository. The public [PanoBox-Releases](https://github.com/KlowzyZ/PanoBox-Releases) repository holds documentation and binary releases. PanoBox's own source is proprietary; third-party components retain their licenses. See [LICENSE](LICENSE) and [THIRD-PARTY-NOTICES.md](THIRD-PARTY-NOTICES.md).

Maintainers need Windows and the SDK selected by `global.json`. `pwsh ./release.ps1` restores locked dependencies, audits them, runs the Windows test suite, publishes a self-contained x64 build and packages only fresh build output and reviewed documentation. The workflow uploads private build artifacts for review; it does not publish source or create a public release. Output is in `artifacts/`; personal app data is never a release input.

Türkçe: `Ctrl+Shift+V` ile açın, arayın ve `Enter` ile yapıştırın. Veriler yereldir fakat şifrelenmez. Hassas bilgileri kopyalamadan önce tepsiden kaydı duraklatın. Güncellemeler yalnızca sizin başlattığınız denetimde sorgulanır.

Copyright © 2026 KLOWZY. All rights reserved.
