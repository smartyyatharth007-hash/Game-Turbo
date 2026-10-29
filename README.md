⚡ GAMING TURBO — Desktop Edition
v2.0.0 · Native Windows App · No Install · 100% Offline

One small .exe that turns your PC into a boosted, game-focused machine: real hardware detection, one-click performance boost, automatic game library scanning, "can it run it?" spec checks, real benchmarks, APK installation into Android emulators, and a Gaming Session that automatically disables Windows extras while you play — and restores everything when you're done.

📦 Quick Start
Step
Action
1	Extract the zip anywhere (Desktop is fine)
2	Double-click GamingTurbo.exe
3	If SmartScreen appears → More info → Run anyway

That's it. Nothing is installed, no internet is needed, no account is required.
Your profile and settings live in %LOCALAPPDATA%\GamingTurbo\ on your own disk.

First run? The SmartScreen warning is normal for unsigned indie software. Your antivirus may also glance at it once — the app is a single normal program and touches only safe, reversible, per-user Windows settings.

🖥️ System Requirements
Requirement
Minimum
OS	Windows 10 or Windows 11 (64-bit or 32-bit)
Runtime	.NET Framework 4.8 — already built into Windows, zero installs
Disk	~1 MB for the app itself
Internet	Not required — the app is fully offline
Admin rights	Only for specific actions (image backup, system restore points) — the app asks via the normal Windows UAC prompt

🎛️ Feature Tour (9 Modules)
1. Dashboard
Real hardware detection via WMI: CPU model and cores, RAM sticks and totals, GPU with VRAM, disk layout — plus a live pulse of RAM and CPU usage. The app detects whether you are on a laptop or a desktop PC (battery presence + chassis type) and adjusts its recommendations accordingly. Your profile name and neon avatar show up here.

2. Boost Center
One click performs a real sequence: closes background apps from an editable kill list (OneDrive, Teams, Spotify, and more), clears temp files, trims process working sets to free RAM, flushes the DNS cache, switches to the High Performance power plan (your previous plan is remembered and restored), and enables Windows Game Mode. Every step is logged in the console panel so you can see exactly what happened.

3. Games Library
Auto-scans your machine for games: reads Steam library folders and app manifests, Epic Games launcher manifests, and the Windows installed-programs registry. Star games into MY ROSTER for quick access, add any custom .exe, launch with one click, and open INFO for automatic game details.

4. Spec Check — "Can this PC run it?"
A built-in database of 31 game requirement profiles (Cyberpunk 2077, Elden Ring, Fortnite, GTA V, Valorant, and more) is compared against your real CPU tier, GPU tier, and RAM. You get a clear verdict — READY RECOMMENDED / MINIMUM / BELOW — plus gap-based upgrade recommendations ("+1 RAM stick", "GPU one tier up", etc.).

5. Benchmark
Real tests, real numbers, measured on your machine:

CPU — single-core and all-core math throughput (Mops)
RAM — memory bandwidth (GB/s)
Disk — write and read speed on your system drive (MB/s, 512 MB test)
GPU — compositing FPS via a live DirectX render test
Results get a LOW / MID / HIGH / ULTRA badge per component and a composite Turbo Score with a grade, saved to a local history so you can compare before/after tweaks.

6. APK Runner
Install .apk files into Android emulators. The app detects BlueStacks / LDPlayer / Nox / MuMu / Google Play Games / generic ADB, starts the emulator, connects over ADB, installs the APK, finds the new package, and launches it. If no emulator is installed, the page shows a setup guide — Windows itself cannot run APKs; an Android runtime is required, and this app drives it for you.

7. Gaming Session ⭐
The star feature. Tick what should be disabled while you play — Widgets, chat, Copilot button, toast notifications, transparency effects, animations, taskbar animations, Xbox Game DVR, background capture — pick a game, and hit LAUNCH & START SESSION.

Every setting is snapshotted before anything changes
Gaming values are applied
When the game process exits, everything is restored automatically (watched live, 2-second polling)
If your PC loses power mid-game, the app detects the stale snapshot on next launch and offers to restore it
8. Backup Center
Generates a real full-system image backup script using Windows' built-in wbadmin, targeting a second drive (the app elevates itself via UAC when you run it), plus one-click System Restore points through WMI.

9. Settings
Profile name + neon avatar, sound effects on/off, editable boost kill list, start-with-Windows (via a Startup shortcut), and restart-as-admin.

🧭 Navigation
Left sidebar = the 9 sections
Every page has a BACK button (top-left)
ESC always takes you back or closes dialogs
Log file for troubleshooting: %LOCALAPPDATA%\GamingTurbo\gamingturbo.log
🛠️ Building From Source
The complete C# source code is included in the Source-Code/ folder — the app is yours to modify.

Requirements: the .NET SDK (any modern version, e.g. 8) — download free from dotnet.microsoft.com

bash

cd Source-Code
dotnet build -c Release
The finished exe appears in Source-Code/bin/Release/. The project targets .NET Framework 4.8 (net48) with WPF, so the output runs on any stock Windows 10/11 machine with zero additional installs.

Source Map
File
What it does
App.cs	Entry point: single-instance mutex, global exception handler + logging
MainWindow.cs	Shell: sidebar nav, page routing + back history, toasts, modals, profile system
Pages1.cs – Pages4.cs	The nine pages (Dashboard, Boost, Games, Spec, Bench, APK, Session, Backup, Settings)
T.cs	Neon RGB palette, frozen brushes/gradients, glow helpers
Ui.cs	Programmatic UI system: dark button/card/meter/list/combobox templates
Data.cs	31-game requirements DB, 80+ GPU tier table, 90+ CPU tier table, kill list, fuzzy matcher
SysInfo.cs	WMI hardware detection: CPU/RAM/GPU/disks/battery/chassis → laptop vs desktop
SoftwareScan.cs	Steam/Epic/registry game scanning and classification
Boost.cs	Kill list, temp purge, RAM trim, DNS flush, power plan + Game Mode
SpecCheck.cs	Verdict engine with gap-based recommendations
Benchmark.cs	CPU/RAM/disk/GPU measurement + Turbo Score
ApkRunner.cs	Emulator detection, ADB connect → install → launch pipeline
GameSession.cs	Snapshot → apply → process watch → auto-restore with crash recovery
BackupCenter.cs	wbadmin image script generator + System Restore points
Store.cs	JSON config persistence in %LOCALAPPDATA%\GamingTurbo\

📖 Honest Limits (so you know what's real)
Google sign-in — real "Sign in with Google" requires your own OAuth client credentials and internet calls. This build is fully local, so it uses local profiles instead (explained inside the app too).
APKs — Windows cannot run them natively. The app automates installation into whichever Android emulator you have.
Benchmark numbers — measured on your machine, relative to this test suite. Perfect for before/after comparisons; not for leaderboard bragging.
Backup script — needs admin rights (asks via UAC) and a second drive for image backups.
Boost / Gaming Session — only touch safe, reversible, per-user Windows settings. Nothing is deleted permanently, everything is restored.
Privacy: the app makes no network calls, collects nothing, and sends nothing anywhere. All data stays in %LOCALAPPDATA%\GamingTurbo\.

🧯 Troubleshooting
Problem
Fix
App did not start	Right-click GamingTurbo.exe → Properties → Unblock → run again
Boost shows 0 MB freed	Nothing needed cleaning — that's a good thing
APK install fails	Open your emulator once, enable ADB debugging in its settings, hit REFRESH, retry
Session didn't restore a setting	Check the log; on next launch the app detects stale snapshots and offers restore
Backup script errors	Run the app as admin, confirm the target drive has enough free space
Where are my settings?	%LOCALAPPDATA%\GamingTurbo\ — delete that folder to reset the app

🗑️ Uninstall
Delete GamingTurbo.exe
Optionally delete %LOCALAPPDATA%\GamingTurbo\
If you enabled start-with-Windows: delete the Gaming Turbo shortcut in shell:startup
📜 Version History
v2.0.0 — Desktop Edition reborn as a native WPF app: real WMI hardware detection, laptop/desktop detection, Steam/Epic/registry game scanning, 31-game spec-check DB, real CPU/RAM/disk/GPU benchmarks, ADB-driven APK runner, snapshot-based Gaming Session with crash recovery, wbadmin backup center, neon RGB theme throughout.

Gaming Turbo runs entirely on your machine — by design. Enjoy the turbo. ⚡
