# Elden Ring Launcher

A Windows launcher for switching between **Seamless Co-op**, **OnlineFix Co-op**, and the **original game**, with built-in launcher and mod updates.

**[Download the launcher](https://github.com/itsMohammedAli/elden-launcher-releases/releases)** — choose the asset ending in **`-online.zip`**.

## What is Seamless Co-op?

[Seamless Co-op by Yui](https://www.nexusmods.com/eldenring/mods/510) changes multiplayer in **Elden Ring** so friends can explore the game together.

- Play with up to five other players.
- Boss victories and normal deaths do not end the session.
- Progression is shared, and normal multiplayer area barriers are removed.
- The mod uses separate saves from the original game, with the default extension `.co2` instead of `.sl2`. Keep backups and do not convert mod saves to vanilla saves.

The mod can contain bugs. This repository distributes a separate launcher; **Yui is the author of Seamless Co-op**. Read the [official mod description](https://www.nexusmods.com/eldenring/mods/510) for its full features and requirements.

## Before you install

- Use **Elden Ring** on Windows.
- For official Seamless Co-op multiplayer, be signed into Steam in online mode. Friends need matching game and mod versions.
- Have an internet connection for the first mod download and future updates.
- Close the game and launcher before replacing launcher files.
- Back up saves and existing game modifications. Switching launcher modes replaces matching game files.

The official mod's supported setup and limitations are described on [Nexus Mods](https://www.nexusmods.com/eldenring/mods/510).

## Which download?

Open [Releases](https://github.com/itsMohammedAli/elden-launcher-releases/releases), expand **Assets**, and select:

| Asset | What to use it for |
| --- | --- |
| **`elden-ring-launcher-…-online.zip`** | **Use this for a fresh install or manual upgrade.** Contains the launcher; the mod downloads from its official source when needed. |
| Source code archives | GitHub repository snapshots, not an installable launcher. |

## Installation

1. Download the **`-online.zip`** asset.
2. In Steam, right-click **Elden Ring** → **Manage → Browse local files**, then open its **Game** folder.
3. Extract the ZIP's **Launcher** folder directly into **Game**. Replace matching launcher files if upgrading.
4. Open **`Game/Launcher/elden_launcher.exe`**.

After the first co-op installation, your folders should look like this:

```text
ELDEN RING/
└── Game/
    ├── eldenring.exe
    ├── ersc_launcher.exe
    ├── SeamlessCoop/
    │   ├── ersc.dll
    │   └── ersc_settings.ini
    └── Launcher/
        ├── elden_launcher.exe
        ├── flutter_windows.dll
        ├── data/
        ├── bundles/
        │   ├── original/
        │   └── online_fix/
        ├── seamless_coop/
        │   └── install-release.ps1
        ├── updater/
        │   └── install-update.ps1
        └── readme.txt
```

Keep all launcher files together. Avoid nesting another **Launcher** folder inside **Launcher**. Existing **`Game/ERLauncher`** installations are also supported.

The ZIP contains the **Launcher** folder. **`ersc_launcher.exe`** and the game's **`SeamlessCoop`** folder are created automatically by the first official mod download. **`Launcher/seamless_coop`** contains the download/install helper script; it is separate from **`Game/SeamlessCoop`**, which contains the installed mod.

### First co-op launch and password

1. Choose **Seamless Co-op** on the launcher's **Play** page. On first use, it downloads and installs the latest stable [official GitHub release](https://github.com/yuiamoroll/EldenRingSeamlessCoopRelease/releases/latest), then starts the mod.
2. After that first installation, close the game if it opened before configuring your session.
3. Open the launcher's **Seamless Co-op** page → **Edit settings**, then set and save a private session password. Everyone in your group must use the same password. You can also edit **`Game/SeamlessCoop/ersc_settings.ini`** in a text editor while the game is closed.
4. Return to **Play** and launch **Seamless Co-op** again.

Existing INI settings and passwords are preserved during later mod updates.

For hosting, joining, and in-game items, follow the [official play instructions](https://www.nexusmods.com/eldenring/mods/510).

## Launcher modes

| Mode | What the launcher does |
| --- | --- |
| **Seamless Co-op** | Restores the original game file set, updates the official mod when needed, and starts `ersc_launcher.exe`. |
| **OnlineFix Co-op** | Restores the supplied OnlineFix file set, updates the official mod when needed, and starts `ersc_launcher.exe`. This is an additional mode provided by this launcher. |
| **Original Game** | Restores the original game file set and starts `eldenring.exe`. No mod download is needed. |

## Launcher settings

- **Play** contains the three game modes.
- **Seamless Co-op** shows installed/latest mod versions, the session password with a show/hide button, and **Edit settings** for the INI form.
- **Settings** contains the saved **Close after launch** switch, game/save folder shortcuts, and manual update checks. Close after launch defaults to enabled.
- The editor includes Elden Ring gameplay options, difficulty scaling, startup volume (0–10), password, save extension, and language. It preserves comments, encoding, and unknown entries, and rejects saves if the INI changed externally while open.
- Save files are under **`%APPDATA%/EldenRing`**. Launcher preferences are stored separately under **`%LOCALAPPDATA%/EldenRing/Launcher`** (falling back to `%APPDATA%`).
- Opening the launcher again activates the existing window. Crash reporting is disabled in the current release.

## Updates

Use **Settings → Check for updates** to check launcher and mod releases again manually. **Check Seamless Co-op updates** in Settings and **Check** on the Seamless Co-op page refresh the mod version check only; checking does not install anything.

The update banner handles available updates:

| Available | Update button |
| --- | --- |
| Launcher only | **Update available** |
| Seamless Co-op only | **Update Seamless Co-op** |
| Both | **Update launcher & Seamless Co-op** |

When both need updating, the mod installs first, then the launcher updates and restarts. A mod-only update keeps the launcher open without starting the game. **Close the game before updating the mod.**

Co-op launches also check for mod updates automatically. Downloads are checked against GitHub's published size and SHA-256 digest before installation. Files included in the mod ZIP are replaced, but existing **`ersc_settings.ini`** and other INI files are preserved. Files absent from the new ZIP are not deleted. A manually installed copy without a launcher verification record may be downloaded again even if it is already current.

A matching checksum verifies the download against that release; it does not independently prove a file is malware-free. Once the mod is installed, verified installed files can be used if the release check is unavailable. Online multiplayer still requires the mod's normal Steam/network connection.

The bottom-left footer displays installed and latest mod versions as plain text. The external-link button in the installation-status panel opens the [Nexus Mods files page](https://www.nexusmods.com/eldenring/mods/510?tab=files). The bottom-right corner shows the launcher version and build.

## Troubleshooting

### Windows Defender / files missing after extraction

If a file disappears, extraction fails, or the launcher reports a missing DLL, check **Windows Security → Virus & threat protection → Protection history** for the affected file and detection name.

False positives are possible, but **a detection must not automatically be assumed to be a false positive**. Keep Defender enabled while investigating. Download only from this repository's releases and the official mod sources, and compare the ZIP's SHA-256 with the digest shown in GitHub's Assets list.

If you believe a detection is incorrect, report the filename and detection name to the relevant maintainer and [submit the file to Microsoft for analysis](https://www.microsoft.com/en-us/wdsi/filesubmission). Keep the file quarantined until its safety has been established; do not disable protection or add broad exclusions just to make it run.

See Microsoft's [Protection History guidance](https://support.microsoft.com/en-us/windows/security/windows-security/protection-history-in-the-windows-security-app).

### Update fails

- Close the game and leave only one launcher window open.
- Check your connection and write permissions for the installation folder, then retry.
- If recovery files are reported, keep them until the issue is resolved.
- For a manual launcher upgrade, close the launcher and extract a fresh **`-online.zip`** into **Game**.

### Installed mod version is unknown

A manually installed version may not be recognized until the launcher installs and verifies the official release. Starting either co-op mode checks and repairs the installation when needed, while preserving existing INI settings.

### Cannot connect to friends

Check that everyone has matching mod/game versions and the same session password. For mod-specific errors, use the [official Nexus page](https://www.nexusmods.com/eldenring/mods/510).

## Credits and links

- **Seamless Co-op author: Yui** — [Nexus Mods](https://www.nexusmods.com/eldenring/mods/510)
- [Official Seamless Co-op GitHub releases](https://github.com/yuiamoroll/EldenRingSeamlessCoopRelease/releases)
- [Launcher downloads](https://github.com/itsMohammedAli/elden-launcher-releases/releases)
