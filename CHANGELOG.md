# PanoBox changelog

## 1.8.0 — 2026-10-17

- Backups are now a single `.zip` archive that includes image files, templates and preferences, with a SHA-256 manifest. They restore into another folder or computer. Restore validates entry names, sizes and checksums first, merges without deleting existing data, never overwrites existing images and removes files it wrote if the restore fails. JSON backups from earlier versions still import.
- Moving or copying a portable installation no longer breaks image history: references are re-linked to the images in the new `Data\thumbs` folder at startup.
- New per-app exclusion list (by process name) in settings, with suggestions from sources already in history. It applies to history capture, clipboard undo memory and Explorer imports, independently of password detection.
- Explorer "copy to PanoBox" actions no longer add to history while capture is paused, or when image storage or password exclusion rules would have skipped the content.
- History expiry presets (1 hour, 1 day, 7 days, 30 days). New installations keep unpinned history for 30 days; existing settings are unchanged.
- The palette shows when capture is paused and can pause/resume it; the tray menu shows the active shortcut and asks before clearing history.
- An unavailable custom shortcut is now reported instead of being replaced silently.
- Settings counts history in SQLite instead of loading every entry, shows the data folder and explains backup and privacy behavior.
- CI actions upgraded to Node 24 releases pinned by commit SHA. Private evidence drafts are stored only for `main`/tag pushes or on request, packages are attached only to fully successful runs, and a manual, dry-run-by-default workflow prunes old drafts.

## 1.7.0 — 2026-10-16

- Hardened backup and text import validation, bounded local file reads and image-file ownership checks.
- Improved clipboard privacy detection, copy/paste target handling, settings validation and crash resilience.
- Made manual update checks use the public release repository, validated release versions and bounded HTTPS responses.
- Refined dark/light styling, keyboard behavior, accessibility labels, settings and KLOWZY product identity.
- Replaced packaging from existing folders with a fresh, Windows-tested build, locked dependencies, complete third-party notices and SHA-256 checksums. Existing clipboard data and development output are excluded.
- Rewrote privacy and support documentation to describe local unencrypted storage, optional network actions, backup limitations and deletion accurately.

## Earlier development builds

The supplied source identified itself as 1.6.0. This history summarizes its original changelog; it does not imply that these builds were publicly published or independently verified.

| Version | Development changes |
| --- | --- |
| 1.6.0 | SQLite and search-cache performance work; capture and thumbnail memory limits |
| 1.5.0 | Duplicate history cleanup |
| 1.4.0 | Text export/import and local QR generation |
| 1.3.0 | Text scaling and optional Explorer actions |
| 1.2.0 | QR generation and clipboard undo history |
| 1.1.0 | Clipboard undo and display density |
| 1.0.0 | Paste queue, use counts and settings improvements |
| 0.9.0 | Tray update check and palette/settings access |
| 0.8.0 | Multi-selection and settings layout |
| 0.7.0 | Search highlighting and empty states |
| 0.6.0 | Smart actions and search operators |
| 0.5.0 | Local OCR, lighter history snapshots and versioned JSON backups |
| 0.4.0 | Multi-monitor positioning and quick-paste shortcuts |
| 0.3.0 | Concurrent storage, cached search and clipboard retry handling |
| 0.2.0 | Templates, light theme and statistics |
| 0.1.0 | Clipboard history, search, pinning, filters, tray, hotkey and SQLite storage |
