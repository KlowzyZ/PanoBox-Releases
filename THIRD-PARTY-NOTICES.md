# Third-party notices — PanoBox 1.7.0

PanoBox's original code and assets are proprietary to KLOWZY. The components below keep their own licenses. Full upstream license texts and notices accompany the application in `licenses/`; those terms take precedence for the respective third-party components.

The inventory comes from the resolved application dependency lockfile, NuGet package `.nuspec` metadata, included package license/notice files and upstream sources. Development/test packages are not distributed in the application ZIP. Dependency and runtime upgrades require reviewing this inventory and refreshing the accompanying license texts.

| Distributed component | Version | License | Copyright / source |
| --- | --- | --- | --- |
| CommunityToolkit.Mvvm | 8.4.2 | MIT | .NET Foundation and Contributors; [CommunityToolkit/dotnet](https://github.com/CommunityToolkit/dotnet) |
| H.NotifyIcon.Wpf, H.NotifyIcon, H.GeneratedIcons.System.Drawing | 2.4.1 | MIT | HavenDV; [HavenDV/H.NotifyIcon](https://github.com/HavenDV/H.NotifyIcon) |
| Microsoft.Data.Sqlite, Microsoft.Data.Sqlite.Core | 10.0.13 | MIT | Microsoft Corporation; [dotnet/efcore](https://github.com/dotnet/efcore) |
| NHotkey, NHotkey.Wpf | 4.0.0 | Apache-2.0 | Thomas Levesque; [thomaslevesque/NHotkey](https://github.com/thomaslevesque/NHotkey) |
| QRCoder | 1.8.1 | MIT | © 2013–2025 Raffael Herrmann; © 2024–2025 Shane Krueger; [Shane32/QRCoder](https://github.com/Shane32/QRCoder) |
| SQLitePCLRaw.bundle_e_sqlite3, SQLitePCLRaw.core, SQLitePCLRaw.lib.e_sqlite3, SQLitePCLRaw.provider.e_sqlite3 | 2.1.13 | Apache-2.0 | © 2014–2024 SourceGear, LLC (package metadata); [ericsink/SQLitePCL.raw](https://github.com/ericsink/SQLitePCL.raw) |
| SQLite native engine in e_sqlite3 | Included with SQLitePCLRaw native package | Public domain | [SQLite copyright statement](https://www.sqlite.org/copyright.html); see the bundled SQLitePCLRaw notice |
| System.Drawing.Common, Microsoft.Win32.SystemEvents | 10.0.0 | MIT; bundled notices also apply | Microsoft Corporation / .NET Foundation and Contributors; [dotnet/winforms](https://github.com/dotnet/winforms) and [dotnet/runtime](https://github.com/dotnet/runtime) |
| .NET runtime and Windows Desktop runtime | 10.0.13 | MIT; bundled runtime notices also apply | .NET Foundation and Contributors; [dotnet/runtime](https://github.com/dotnet/runtime), [dotnet/wpf](https://github.com/dotnet/wpf), [dotnet/winforms](https://github.com/dotnet/winforms) |
| Microsoft.Windows.SDK.NET projection assemblies | Windows SDK .NET targeting pack 10.0.22621.57 | Windows SDK license terms | © Microsoft Corporation; [Windows SDK](https://aka.ms/WinSDKProjectURL) |
| WinRT.Runtime (C#/WinRT) | 2.2.0.48161 | MIT | © Microsoft Corporation; [microsoft/CsWinRT](https://github.com/microsoft/CsWinRT) |

Microsoft's runtime and System.Drawing notices contain additional third-party attribution and terms; keep the complete files with a redistributed package. No third-party fonts are bundled by PanoBox. Windows OCR is an operating-system feature and is not redistributed as an OCR model in this package.

## License text provenance

- `CommunityToolkit.Mvvm-LICENSE.md` and `CommunityToolkit.Mvvm-NOTICES.txt`: copied unchanged from the official CommunityToolkit.Mvvm 8.4.2 NuGet package.
- `H.NotifyIcon-LICENSE.txt`: [upstream LICENSE.md at the package-declared commit](https://github.com/HavenDV/H.NotifyIcon/blob/bcaaabecf16566dd910a3798fe874014e251b28d/LICENSE.md).
- `Microsoft.Data.Sqlite-LICENSE.txt`: [EF Core license at the package-declared dotnet/dotnet commit](https://github.com/dotnet/dotnet/blob/4099f83977f4d29604a9aeb971fb0a7bc1d5f699/src/efcore/LICENSE.txt).
- `NHotkey-LICENSE.txt`: [upstream LICENSE.md at the package-declared commit](https://github.com/thomaslevesque/NHotkey/blob/0c384a0c2178ed931e8e74d13a79231f9192803b/LICENSE.md). NHotkey is licensed under Apache-2.0.
- `QRCoder-LICENSE.txt`: copied unchanged from the official QRCoder 1.8.1 NuGet package.
- `SQLitePCLRaw-LICENSE.txt` and `SQLitePCLRaw-NOTICE.txt`: [Apache license](https://github.com/ericsink/SQLitePCL.raw/blob/ca835d21508bff43121c65081035840ac5006c4c/LICENSE.TXT) and [complete 2.1-series notice](https://github.com/ericsink/SQLitePCL.raw/blob/ca835d21508bff43121c65081035840ac5006c4c/NOTICE.TXT) from upstream v2.1.12. The 2.1.13 packages declare Apache-2.0 but contain no license text/notice or source commit, and no upstream v2.1.13 tag was available during preparation. The existing full 2.1-series attribution is retained conservatively.
- `System.Drawing.Common-LICENSE.txt`, `System.Drawing.Common-NOTICES.txt` and `Microsoft.Win32.SystemEvents-NOTICES.txt`: copied unchanged from the corresponding official 10.0.0 NuGet packages. Microsoft.Win32.SystemEvents uses the same MIT grant; its package copyright is © Microsoft Corporation.
- `NET-runtime-LICENSE.txt`, `NET-runtime-NOTICES.txt` and `WindowsDesktop-runtime-LICENSE.txt`: copied unchanged from Microsoft.NETCore.App.Runtime.win-x64 10.0.13 and Microsoft.WindowsDesktop.App.Runtime.win-x64 10.0.13 NuGet packages.
- `Windows-SDK-LICENSE.rtf`: the [official license linked by Microsoft.Windows.SDK.NET.Ref 10.0.22621.57](https://aka.ms/WinSDKLicenseURL), retrieved unchanged from Microsoft's `sdk_license.rtf` download. The targeting pack is an implicit Windows framework dependency and is not listed in the application package lockfile.
- `CsWinRT-LICENSE.txt`: [upstream license at commit 8649ee3eeb2445ca2a36d80d878ef60b96a6c65d](https://github.com/microsoft/CsWinRT/blob/8649ee3eeb2445ca2a36d80d878ef60b96a6c65d/LICENSE), identified from the included WinRT.Runtime assembly's informational version.

Third-party component source has not been modified by PanoBox. Attribution does not imply endorsement of PanoBox or KLOWZY.
