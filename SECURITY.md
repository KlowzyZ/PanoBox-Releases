# PanoBox security

## Reporting a vulnerability

Use the contact channel published on [klowzy.com](https://klowzy.com) for a private report. Mention PanoBox, the affected version, Windows version, impact and reproduction steps using synthetic clipboard content. Ask for a private transfer channel before sending anything sensitive. Do not publish exploit details in a public issue while a fix is being coordinated.

Do not attach real clipboard history, `Data`, database files, backups, access tokens, personal paths or unsanitized screenshots/logs. Ordinary bugs can be reported in [PanoBox-Releases issues](https://github.com/KlowzyZ/PanoBox-Releases/issues).

## Supported version and boundaries

Use the latest stable release from [KlowzyZ/PanoBox-Releases](https://github.com/KlowzyZ/PanoBox-Releases/releases). Version 2.0.x is the current supported line. Earlier development builds should be replaced. There is no guaranteed response-time commitment.

PanoBox is a Windows desktop app that intentionally reads and writes the current user's clipboard, stores local history and can simulate a paste action. It is not a secret vault or a defense against malicious software running as the same user. Local history and text exports are not encrypted; backups are encrypted only when a backup password is set, and that protection depends on the password's strength. Password exclusions are heuristics and cannot promise that every secret is rejected. Backups are sensitive input and should come from a trusted source. Restore accepts only the expected file names inside a backup archive, enforces per-file and total size limits, verifies SHA-256 checksums before writing and never overwrites existing image files.

Run as a normal Windows user. Automatic paste into elevated apps or games may be blocked by Windows; raising PanoBox's privilege level is not required for normal use. Optional startup and Explorer entries are scoped to the current user. The app does not require a network listener or administrator rights.

## Updates and distribution

Update checks are manual, read bounded release metadata over HTTPS and offer a release-page link. PanoBox does not automatically download or execute updates. The installer and executable are currently unsigned. SHA-256 checksums can detect a corrupted or altered download when compared against a trusted release page; they are not a publisher code signature.

Maintainers restore dependencies in locked mode, audit direct and transitive NuGet packages, run tests on Windows and package only fresh publish output with documentation and licenses. Source belongs in the private repository. Never upload development `bin`/`obj`, existing release folders, clipboard databases, settings, logs, signing material or credentials to either repository or release assets. Public releases contain only reviewed binaries and documentation.
