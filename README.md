# Shandalar for macOS

Classic **Shandalar / ManaLink 1.3.2** packaged for modern **Apple Silicon and Intel Macs**.

This project makes the old **Home of the Underdogs (HOTU)** version of Shandalar easy to launch on modern macOS without requiring users to manually configure a Windows compatibility environment.

## Download

Download the newest version from the **Releases** section of this repository.

Current release:

**Shandalar for macOS Basic 1.0.7 — Build 8**

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

* **Apple Silicon or Intel Mac**
* **macOS 14 or later**
* Approximately 656 MB for the release download, plus runtime/game data

## How to use it

1. Download and unzip the latest release.
2. Open **Shandalar.app**.
3. Play normally.
4. When finished, **exit from inside Shandalar**.

The emulated Windows 98 environment and Mac runtime will then shut down automatically.

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
* Applies the Shandalar wallpaper, branded Windows boot logo, hidden desktop icons, and auto-hidden taskbar
* Uses a non-blocking startup path so the Windows guest cannot stall on synchronous registry imports
* Automatically applies the required audio repair to existing installations
* Preserves affected files with SHA-256-backed-up migration behavior
* Automatically creates verified campaign backups
* Automatically recovers from a missing or incomplete live runtime image

## Save data and runtime files

On first launch, writable game and runtime data are created in:

~/Library/Application Support/Shandalar

Before every launch, the app creates and SHA-256-verifies a complete campaign backup.

The **three newest verified backups** are retained automatically.

If the live runtime image becomes missing or incomplete, relaunching the app automatically restores the newest verified backup.

## Diagnostics

If something goes wrong, diagnostic information and recovery instructions are written to:

~/Library/Application Support/Shandalar/Logs/diagnostics.txt

If you report a problem, including the contents of this file may help identify the cause.

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

### 1.0.7 — Build 8 (Basic)

* Fixed the slow/apparently stuck boot caused by blocking regedit /s startup imports under Windows 98 emulation.
* Startup presentation and startup-audio muting now run through direct Win32 helpers; the original game files remain unchanged.
* Keeps the native Metal/fullscreen 1024×768 presentation, universal Apple Silicon/Intel launcher, Shandalar boot logo and wallpaper, hidden desktop chrome, audio repair, verified backups, and 1,275-file HotU/ManaLink 1.3.2 payload.

### 1.0.6 — Build 7

* Fixed the timed lair-entry intro movie path by disabling render-on-demand and host-vsync pacing.

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
