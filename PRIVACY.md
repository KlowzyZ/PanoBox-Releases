# PanoBox privacy

Applies to PanoBox 2.0.0. Last updated: 17 October 2026. Publisher: [KLOWZY](https://klowzy.com).

## What the app records

While capture is enabled, PanoBox listens for changes to your Windows clipboard in your current user session. Supported entries include text, images and lists of file paths. History can contain copied content, previews, source process name, timestamps, a content hash, pin status and a local use count used for sorting. Templates and app preferences are also stored. PanoBox does not copy the contents of files merely because their paths appear on the clipboard.

Capture can be paused from the tray or the palette; the palette shows when capture is paused. Settings control images, history limits, history expiry (off, 1 hour, 1 day, 7 days or 30 days), password exclusion and a list of excluded apps. Content copied from an excluded app (matched by its Windows process name) is never recorded, whether or not password exclusion is on. The default history limit is 200; pinned entries can outlive that limit and automatic expiry. New installations keep unpinned history for 30 days by default; upgrading does not change an existing installation's expiry setting. Text capture is limited to 100,000 characters. These limits do not make clipboard storage safe for passwords.

When password exclusion is enabled, PanoBox checks known password-manager source names and patterns resembling credentials. It also honors supported clipboard opt-out formats. These checks are best-effort heuristics: other apps, unusual passwords, text inside larger documents, manually entered templates and imported records can still contain secrets. Pause capture before handling sensitive content. The app cannot protect you from other software that can read the clipboard or your user files.

## Local storage and encryption

The installed app stores data in `%LOCALAPPDATA%\PanoBox`. The portable app uses a `Data` folder beside `PanoBox.exe` when it is writable, otherwise `%LOCALAPPDATA%\PanoBox`. Settings → Backup and data shows the active folder. The data folder includes:

| Data | Location |
| --- | --- |
| History, templates and SQLite working files | `panobox.db`, possibly `panobox.db-wal` and `panobox.db-shm` |
| Captured images and previews | `thumbs\` |
| Preferences | `settings.json` |
| Generated QR images | `qr\` |
| Local error logs | `Logs\` |

**PanoBox does not encrypt its database, images, settings, logs or text exports.** Backups are encrypted only when you set a password for them (see below). People or software with access to unencrypted files may read them. Use Windows account protection and device encryption as appropriate. A portable installation in a shared or synchronized folder shares that folder's access and synchronization behavior. Protect USB drives and backups accordingly.

Logs record local error information and exception details. They may expose paths or other contextual data, are not sent automatically, and should be inspected before sharing. A damaged database can be renamed and retained beside the current database for recovery; old copies may still contain clipboard history.

## Network activity and external actions

PanoBox has no accounts, cloud synchronization, advertising, analytics SDK or automatic update polling. Clipboard history, OCR input and QR generation are processed locally; the application does not upload them as part of these functions.

When you explicitly choose **Check for updates**, PanoBox sends an HTTPS request to `api.github.com/repos/KlowzyZ/PanoBox-Releases/releases/latest`. GitHub receives your IP address and ordinary request metadata, including the `PanoBox/<version>` User-Agent. The request does not include clipboard content, templates, a device identifier or a database. GitHub processes connection information under [its privacy statement](https://docs.github.com/en/site-policy/privacy-policies/github-general-privacy-statement). The check reads release metadata; it does not download or install executables. Opening the offered release page is a separate browser action.

Links to `klowzy.com`, GitHub releases, saved websites and email addresses open only through an explicit user action. Opening a saved link, file location or mail action invokes Windows' associated application. That application and the destination service have their own privacy behavior. Windows OCR uses locally installed Turkish or English recognition support; Windows features and language-pack installation are governed separately by Windows settings.

## Plain-text paste

The optional **paste as plain text** shortcut (Ctrl+Shift+Alt+V by default) reads the current clipboard in the active application, replaces it with its plain text and pastes it. The original formatted clipboard content is not kept. The plain text is marked to be excluded from Windows clipboard history and cloud synchronization and is not added to PanoBox history again.

## Optional Windows integration

Startup and Explorer context-menu integration are optional and off by default. If enabled, PanoBox writes per-user Windows registry entries pointing to its executable. Explorer actions deliberately copy a selected text file's contents or a folder path. The copy always happens because you asked for it, but adding it to history follows the same rules as clipboard capture: nothing is recorded while capture is paused, images are skipped when image storage is off, and content that looks like a secret is skipped when password exclusion is on. These are local actions and do not require administrator access.

## Backups, deletion and uninstalling

Backups contain history text and metadata, the referenced image files, templates and preferences, plus a checksum manifest. A backup without a password is an unencrypted `.zip` that anyone with the file can read. With a password, the backup is a `.pbx` file encrypted with AES-256-GCM using a key derived from your password (PBKDF2-SHA256, 600,000 iterations, random salt); it is never written unencrypted. PanoBox does not store or transmit the password, and a forgotten password cannot be recovered. When an encrypted backup is restored, its decrypted contents exist only temporarily in a file in the data folder that Windows deletes when the restore finishes. Text export also contains history text and metadata. Older JSON backups (1.7.0 and earlier) do not contain images. Share backups and exports only after inspecting and sanitizing them. Import only backups you trust: restore checks file names, sizes and checksums before writing, merges into existing data without deleting it, and does not restore startup or Explorer integration or switch off privacy protections that are on.

Deleting an entry removes its database record and its associated app-owned thumbnail where applicable. Clearing unpinned history preserves pinned entries and templates. Generated QR files, logs, separate exports and recovery copies may remain. Deletion is logical removal, not guaranteed secure erasure of SQLite pages, storage media, system backups or Windows clipboard history. PanoBox's clipboard undo state also lives in memory while the app runs.

The installed app can be removed from Windows Settings → Apps; the uninstaller removes the startup and Explorer entries and asks whether to delete `%LOCALAPPDATA%\PanoBox` (the default keeps it). For the portable app, first disable startup and Explorer integration, exit PanoBox from the tray, then remove the app folder and the active data folder. Remove any separate backups, QR exports, synchronized copies and recovery files that you no longer need. Windows clipboard history must be managed separately in Windows settings.

Questions: use the contact channel published on [klowzy.com](https://klowzy.com). Do not send your clipboard database or private content.
