# PanoBox changelog

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
