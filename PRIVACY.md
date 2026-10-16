# PanoBox privacy

Applies to PanoBox 1.7.0. Last updated: 16 October 2026. Publisher: [KLOWZY](https://klowzy.com).

## What the app records

While capture is enabled, PanoBox listens for changes to your Windows clipboard in your current user session. Supported entries include text, images and lists of file paths. History can contain copied content, previews, source process name, timestamps, a content hash, pin status and a local use count used for sorting. Templates and app preferences are also stored. PanoBox does not copy the contents of files merely because their paths appear on the clipboard.

Capture can be paused from the tray. Settings control images, history limits, optional expiry and password exclusion. The default history limit is 200; pinned entries can outlive that limit and automatic expiry. Text capture is limited to 100,000 characters. These limits do not make clipboard storage safe for passwords.

When password exclusion is enabled, PanoBox checks known password-manager source names and patterns resembling credentials. It also honors supported clipboard opt-out formats. These checks are best-effort heuristics: other apps, unusual passwords, text inside larger documents, manually entered templates and imported records can still contain secrets. Pause capture before handling sensitive content. The app cannot protect you from other software that can read the clipboard or your user files.

## Local storage and encryption

If writable, `Data` beside `PanoBox.exe` is used. Otherwise the location is `%LOCALAPPDATA%\PanoBox`. The data folder includes:

| Data | Location |
| --- | --- |
| History, templates and SQLite working files | `panobox.db`, possibly `panobox.db-wal` and `panobox.db-shm` |
| Captured images and previews | `thumbs\` |
| Preferences | `settings.json` |
| Generated QR images | `qr\` |
| Local error logs | `Logs\` |

**PanoBox does not encrypt its database, images, settings, logs or exported backups.** People or software with access to these files may read them. Use Windows account protection and device encryption as appropriate. A portable installation in a shared or synchronized folder shares that folder's access and synchronization behavior. Protect USB drives and backups accordingly.

Logs record local error information and exception details. They may expose paths or other contextual data, are not sent automatically, and should be inspected before sharing. A damaged database can be renamed and retained beside the current database for recovery; old copies may still contain clipboard history.

## Network activity and external actions

PanoBox has no accounts, cloud synchronization, advertising, analytics SDK or automatic update polling. Clipboard history, OCR input and QR generation are processed locally; the application does not upload them as part of these functions.

When you explicitly choose **Check for updates**, PanoBox sends an HTTPS request to `api.github.com/repos/KlowzyZ/PanoBox-Releases/releases/latest`. GitHub receives your IP address and ordinary request metadata, including the `PanoBox/<version>` User-Agent. The request does not include clipboard content, templates, a device identifier or a database. GitHub processes connection information under [its privacy statement](https://docs.github.com/en/site-policy/privacy-policies/github-general-privacy-statement). The check reads release metadata; it does not download or install executables. Opening the offered release page is a separate browser action.

Links to `klowzy.com`, GitHub releases, saved websites and email addresses open only through an explicit user action. Opening a saved link, file location or mail action invokes Windows' associated application. That application and the destination service have their own privacy behavior. Windows OCR uses locally installed Turkish or English recognition support; Windows features and language-pack installation are governed separately by Windows settings.

## Optional Windows integration

Startup and Explorer context-menu integration are optional and off by default. If enabled, PanoBox writes per-user Windows registry entries pointing to its executable. Explorer actions deliberately copy a selected text file's contents or a folder path. These are local actions and do not require administrator access.

## Backups, deletion and uninstalling

JSON backups contain history metadata/text, templates and selected preferences in plain text. Text export also contains history text and metadata. **Image binaries are not embedded in JSON backups**; local image references depend on the original data files. Share exports only after inspecting and sanitizing them. Import only backups you trust.

Deleting an entry removes its database record and its associated app-owned thumbnail where applicable. Clearing unpinned history preserves pinned entries and templates. Generated QR files, logs, separate exports and recovery copies may remain. Deletion is logical removal, not guaranteed secure erasure of SQLite pages, storage media, system backups or Windows clipboard history. PanoBox's clipboard undo state also lives in memory while the app runs.

For complete removal, first disable startup and Explorer integration, exit PanoBox from the tray, then remove the app folder and the active data folder. Remove any separate backups, QR exports, synchronized copies and recovery files that you no longer need. Windows clipboard history must be managed separately in Windows settings.

Questions: use the contact channel published on [klowzy.com](https://klowzy.com). Do not send your clipboard database or private content.
