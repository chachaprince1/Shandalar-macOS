# Shandalar for macOS

Classic **Shandalar / ManaLink 1.3.2** packaged for modern **Apple Silicon and Intel Macs**.

This project makes the old **Home of the Underdogs (HOTU)** version of Shandalar easy to launch on modern macOS without requiring users to manually configure a Windows compatibility environment.

## Download

Download the newest version from the **Releases** section of this repository.

Current release:

**[Shandalar for macOS Basic 1.1.2 — Build 21](https://github.com/chachaprince1/Shandalar-macOS/releases/tag/v1.1.2)**

[Download the application ZIP](https://github.com/chachaprince1/Shandalar-macOS/releases/download/v1.1.2/Shandalar-macOS-basic-1.1.2-universal.zip). Do not use the automatically generated “Source code” archives; those are not the Mac app.

## What's new in 1.1.2?

Balanced (60,000 cycles) is now the default, giving audio more processing headroom. The affected M1 Max / Sequoia reporter confirmed smooth sound at 60,000 and reproduced stutter at the previous 100,000 setting. This supports the new default, not a promise of perfect audio on every Mac.

There is one app, with no startup test chooser. Choose **Shandalar > Performance…** in the Mac menu (or the launcher's Dock menu) for a remembered next-launch setting: Balanced, Extra audio headroom (40,000), or the previous higher budget (100,000). Lower settings may slow card loading or movement; higher settings may bring stutter back. Saving does not retime the current game.

Diagnostics now include active/next-launch profiles and bounded clock-progress summaries. No sound is recorded or uploaded; this is not automatic tuning or direct audio-dropout detection. Original assets, audio buffers, the bundled Windows image and save handling are unchanged. A verified, backed-up one-time startup update prevents obsolete Windows 98 daylight-saving rules from blocking launch with a clock prompt; it does not change your Mac's clock or time zone. No walking-speed patch is included. The optional Audio Test 1 is superseded by this release.

Close older copies before updating and keep Application Support and backups. Please share remaining performance problems in [issue #5](https://github.com/chachaprince1/Shandalar-macOS/issues/5); the overworld input-lag question remains open.

## What's new in 1.1.1?

Fixes the **`MAGIC3.fce` launch error after saving and reopening**, reported in [issue #3](https://github.com/chachaprince1/Shandalar-macOS/issues/3), [issue #4](https://github.com/chachaprince1/Shandalar-macOS/issues/4), and on Reddit. These numbered files are saved campaign portraits, not immutable game artwork. The launcher now preserves them as player data and includes them in verified save imports; checks on actual game assets remain enabled.

**Close the old app and replace it with the new one. Keep Application Support and your backups; no campaign reset is needed.** This is a save-verification hotfix, not an audio/performance fix. All 1.1.0 runtime resources and CPU/audio settings remain unchanged.

## Inherited from 1.1.0

This is the **Basic** release, combining the improvements since public 1.0.9—not the separate HD project.

* One continuous, cursor-free “Shandalar Materializing…” loading image; hidden DOS popup, Windows taskbar and emulator banners; original skull icon on black.
* Quiet, normal shutdown without redisplaying the loading art. Fixes the closing overlay that could cover a running duel.
* Separate Basic campaign data, backed-up save/deck import from older installations, and checks on the actual original game inside the Windows disk.
* Protection against two app copies opening the same campaign, responsive startup progress, and verified backups.
* Native ARM runtime selection on Apple Silicon, even when the launcher starts under Rosetta.
* Fixes a false verification failure caused by the game's generated statistics-screen cache.

**No original game artwork, fonts, sprites, card pool or gameplay binaries have been replaced.** The existing 1024×768/16-bit Metal presentation is retained.

## What version of Shandalar is this?

This follows the classic MicroProse progression:

**Original Shandalar → Spells of the Ancients → Duels of the Planeswalkers → ManaLink 1.3.2**

So this is more than the original 1997 release.

* **Spells of the Ancients** adds additional cards and features.
* **Duels of the Planeswalkers** includes the earlier material and expands the game further.
* **ManaLink 1.3.2** is Mok's unofficial update, which adds bug fixes, compatibility improvements, and exposes some additional cards already implemented by MicroProse.

This is the familiar **HOTU "vanilla+" version of classic Shandalar**.

It is not one of the later community builds that adds Ice Age, Mirage, or thousands of newer cards.

## System requirements

* **macOS 14 or later**
* **Apple Silicon Mac** (primary tested platform); Intel binaries are included, but physical Intel hardware is unverified
* Approximately 656 MB for the download, plus space for the app, runtime/game data and verified backups

## How to use it

1. Close every older Shandalar copy before upgrading.
2. Download and unzip the application ZIP, then open **Shandalar.app**.
3. Allow first-launch preparation and its backed-up migration to finish. Supported saves/decks from a closed older installation are imported; the old disk is left intact.
4. Play normally. When finished, **exit from inside Shandalar** so Windows and the runtime shut down normally.

Keep the older data folder and backups until you have checked the upgrade. Only one app copy should use a campaign at a time.

## What this macOS version does

The Shandalar gameplay and card data are left unchanged.

The macOS package provides the surrounding compatibility environment needed to run the old Windows game reliably on Apple Silicon.

Current features include:

* Launches as a normal macOS application
* No separate Windows installation required
* Installs the required Windows Sound Blaster driver
* Waits for DirectSound to become ready before launching Shandalar
* Disables obsolete Windows 98 startup/Welcome audio that can interfere with game sound
* Uses the native Metal presenter at the game's maximum supported 1024×768/16-bit mode
* Shows a continuous Shandalar startup image and keeps Windows desktop icons and taskbar out of normal startup/play
* Uses a non-blocking startup path so the Windows guest cannot stall on synchronous registry imports
* Retains deterministic guest CPU pacing; the five-colour lair reveal is not universally resolved
* Suppresses the disruptive Windows 98 post-crash ScanDisk screen after an abnormal prior exit, while retaining verified image backups
* Automatically applies the required audio repair to existing installations
* Preserves affected files with SHA-256-backed-up migration behavior
* Automatically creates verified campaign backups
* Automatically recovers from a missing or incomplete live runtime image

## Save data and runtime files

From 1.1.0, Basic uses its own data folder, separate from legacy/HD installations. Upgrades preserve the old disk and a verified snapshot, then copy only supported saves and decks—not HD art, fonts or renderer files.

On first launch, writable game and runtime data are created in:

~/Library/Application Support/Shandalar Basic

Before every launch, the app creates and SHA-256-verifies a complete campaign backup.

The **three newest verified backups** are retained automatically.

If the live runtime image becomes missing or incomplete, relaunching the app automatically restores the newest verified backup.

## Diagnostics

If something goes wrong, diagnostic information and recovery instructions are written to:

~/Library/Application Support/Shandalar Basic/Logs/diagnostics.txt

If you report a problem, including the contents of this file may help identify the cause.

## Testing and known limitations

1.1.2 passed full package acceptance, ARM/x86_64 profile/persistence/timing tests, original-file verification and archive checks. Isolated native tests verified campaign resume, the native Performance menu, next-launch persistence, fresh-install and existing-campaign clock migration, normal quit and reopen. This does not constitute a new exhaustive campaign playthrough.

1.1.1 passed ARM and x86_64 policy/import regression tests, full installed-game and package acceptance. An isolated changed-portrait disk reproduced the 1.1.0 error; 1.1.1 accepted the same disk without changing the portrait and booted to the title, with normal exit. This is not affected-reporter confirmation or a new full gameplay qualification.

1.1.0 passed package integrity, original-file, architecture/macOS-minimum, archive and startup-presentation checks. Local testing reached a live duel; user testing reported no issues, and normal exit plus post-duel reopen passed.

This does **not** certify every Mac. The **M1 Max with 64 GB on Sequoia** reporter confirmed smooth audio at the new default, but the final packaged release and every other Mac are not universally qualified. Overworld input lag remains under investigation. **Physical Intel performance is not qualified by local testing**, although Intel binaries are included. The slow five-colour lair reveal is **not claimed fixed** by this release.

If you report a problem, include your version, Mac model/chip, RAM, macOS version, exact screen/action and whether it repeats. Review diagnostics for personal information before posting.

## Signing

This release is **locally/ad-hoc signed**.

It is **not currently notarized with an Apple Developer ID**.

## Project lineage

**MicroProse Shandalar
→ Spells of the Ancients
→ Duels of the Planeswalkers
→ ManaLink 1.3.2
→ Home of the Underdogs release
→ Shandalar for macOS**

## Reporting problems

Please open an **Issue** and include:

* Mac model
* Apple Silicon chip
* macOS version
* What happened
* What you expected to happen
* Whether the problem happens every time
* Relevant contents of diagnostics.txt, if available

## Release history

### 1.1.2 — Build 21 (Basic)

* Uses reporter-tested 60,000 cycles by default for audio headroom; previous 100,000 and extra-headroom 40,000 remain optional.
* One app with a remembered native Performance menu; changes apply next launch, not during live play.
* Adds local clock diagnostics without recording audio or claiming automatic stutter detection.
* Prevents the obsolete Windows daylight-saving prompt through a backed-up one-time guest update, verified after normal exit. Your Mac clock/time zone is not changed.
* Preserves original game bytes, save location and bundled Windows image. No HD assets, extra cards or walking-speed patch.

### 1.1.1 — Build 18 (Basic)

* Fixes the false `MAGIC3.fce` original-file error after saving and reopening (GitHub #3/#4 and Reddit).
* Preserves numbered campaign portraits in place and includes them in checksum-verified save imports. No save reset, guest migration or change to original game assets.
* Keeps all 1.1.0 runtime/configuration/asset hashes unchanged. Does not claim a new audio or lair-reveal fix.

### 1.1.0 — Build 17 (Basic)

* Combines the work since public 1.0.9: one continuous cursor-free loading image, hidden DOS/Windows/emulator chrome, original skull icon on black, and quiet normal shutdown.
* Fixes the closing overlay covering a live duel and a false original-file check on a generated statistics-screen cache.
* Separates Basic saves/runtime data from legacy/HD installations, with verified save/deck import and original installed-game checks.
* Adds single-session protection, responsive startup preparation, traceable packaging, and native ARM routing even when the Mac launcher starts under Rosetta.
* Preserves original game assets and 1024×768 Metal presentation. No HD assets or additional cards.
* Local duel testing, clean shutdown, reopen and package checks passed. M1 Max/Sequoia audio and physical Intel performance remain unverified; no new lair-reveal fix is claimed.

### 1.0.9 — Build 10 (Basic)

* Fixes the `EXC_BAD_ACCESS (SIGBUS)` crash report that could appear after quitting the game. Opening Shandalar straight from the unzipped download made macOS run it from a temporary read-only App Translocation mount, which macOS then discarded while the launcher was still shutting the guest down.
* Shandalar now detects a translocated launch before doing anything else, offers to move itself into your Applications folder, clears the quarantine flag that caused the translocation, and relaunches from there.
* Normal launches also clear a leftover quarantine flag, so a copy moved by hand stops translocating too.
* On older builds, moving `Shandalar.app` into Applications by hand avoids the same crash.
* No change to the guest image, DOSBox-X configuration, or the supplied HOTU / ManaLink 1.3.2 payload.

### 1.0.8 — Build 9 (Basic)

* Uses `core=normal` with `cycles=fixed 100000` to reduce pacing jitter during Shandalar's guest-side five-colour lair-entry pixel reveal.
* Corrects the earlier diagnosis: this reveal is not `Mtgend.avi`; the original `Dungeon*.spr` assets remain intact.
* Migrates Windows 98 `MSDOS.SYS` from `AutoScan=1` to `AutoScan=0` after creating a verified pre-migration backup, preventing the blue post-crash ScanDisk screen from interrupting launch.

### 1.0.7 — Build 8 (Basic)

* Fixed the slow/apparently stuck boot caused by blocking `regedit /s` startup imports under Windows 98 emulation.
* Startup presentation and startup-audio muting now run through direct Win32 helpers; the original game files remain unchanged.
* Keeps the native Metal/fullscreen 1024×768 presentation, universal Apple Silicon/Intel launcher, Shandalar boot logo and wallpaper, hidden desktop chrome, audio repair, verified backups, and 1,275-file HotU/ManaLink 1.3.2 payload.

### 1.0.6 — Build 7

* Adjusted the separate timed lair-entry Indeo AVI path by disabling render-on-demand and host-vsync pacing. The five-colour reveal is a guest-side software effect and is addressed separately in 1.0.8.

### 1.0.2 — Build 3

* Added Windows Sound Blaster driver setup
* Added DirectSound readiness check before game launch
* Disabled Windows 98 loading/Welcome music that could interfere with game audio
* Added one-time audio repair for existing installations
* Added SHA-256-backed-up migration behavior
* Added automatic campaign backups
* Added automatic recovery from missing or partial runtime images
* Verified application bundle and release packaging

## Scope

This build supports the supplied **HOTU / ManaLink 1.3.2** release only.

It is intentionally not a universal Windows 98 compatibility environment or multi-version Shandalar launcher.
