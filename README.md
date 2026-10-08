# Looper (Loop Audio Lab) - downloads

**Looper** is a multi-sample instrument builder from **Loop Audio Lab**. Drag in a folder of
WAV, AIFF or FLAC samples and Looper maps them across the keyboard for you (key zones, velocity
layers, round robins, pitch detection for unlabelled samples), then lets you play and shape them
as an instrument.

- **Formats:** VST3 (Windows x64, macOS), Audio Unit (macOS), standalone app (Windows, macOS)
- **Mapping:** AutoMapper from file names, YIN pitch detection, Review screen, zone editor and
  keyboard-strip editing with undo / redo
- **Engine:** 4-point Hermite playback, round robins (Cycle / Random), disk streaming for big
  libraries, sample looping with crossfades and *Find loop*
- **Sound shaping:** amp ADSR, LP12 / LP24 / BP / HP filter with key tracking, filter envelope,
  velocity to volume / brightness / attack, pitch-bend up / down ranges
- **Library:** patch browser with categories, search, tags, favourites and prev / next stepping,
  plus 8 factory demo patches

This repository only hosts the installers and release notes. Looper is closed-source,
proprietary software; see [EULA.md](EULA.md).

## Download

Get the newest release from the **[Releases page](https://github.com/TheLoopGolf/Looper-releases/releases)**.
Current beta: **[Looper 0.9.0-beta.1](https://github.com/TheLoopGolf/Looper-releases/releases/tag/v0.9.0-beta.1)**.

| File | What it is |
|------|------------|
| `Looper-<version>-windows-x64-setup.exe` | Windows installer (VST3, standalone, factory patches) |
| `Looper-<version>-macos-universal.pkg` | macOS installer (AU, VST3, standalone, factory patches), Apple Silicon + Intel |
| `Looper-<version>-windows-x64-vst3.zip`, `-standalone.zip` | Windows manual-install zips |
| `Looper-<version>-macos-universal-vst3.zip`, `-au.zip`, `-standalone.zip` | macOS manual-install zips (see `INSTALL-macOS.txt`) |
| `Looper-<version>-factory-content.zip` | The factory patches on their own |
| `SHA256SUMS.txt` | SHA-256 checksums of every file |

## Install

### Windows (x64, Windows 10 / 11)

1. Download `Looper-<version>-windows-x64-setup.exe` and run it.
2. The installer is not code-signed yet. If **SmartScreen** says *Windows protected your PC*,
   click **More info -> Run anyway**.
3. Accept the licence agreement, then pick *Full* (VST3 + factory patches + standalone app) or
   *VST3 plug-in and factory patches*.
   - VST3 -> `C:\Program Files\Common Files\VST3\Looper.vst3`
   - Factory patches -> `C:\ProgramData\Loop Audio Lab\Looper\Factory`
   - Standalone -> `C:\Program Files\Loop Audio Lab\Looper\Looper.exe` (Start menu: *Looper*)
4. Rescan plug-ins in your DAW. Uninstall from *Settings -> Apps -> Looper*; your own patches in
   `Documents\Loop Audio Lab\Looper\Patches` are never touched.

Manual install instead: unzip `Looper-<version>-windows-x64-vst3.zip` into
`C:\Program Files\Common Files\VST3`, and (optional) unzip
`Looper-<version>-factory-content.zip` into `C:\ProgramData\Loop Audio Lab\Looper`.

### macOS (11.0+, Apple Silicon and Intel)

1. Download `Looper-<version>-macos-universal.pkg` and open it.
2. It is not signed with an Apple Developer ID yet, so **Gatekeeper** may refuse to open it.
   Then either go to **System Settings -> Privacy & Security**, scroll down and click
   **Open Anyway**, or clear the download's quarantine flag in Terminal and open it again:

   ```bash
   xattr -d com.apple.quarantine ~/Downloads/Looper-<version>-macos-universal.pkg
   # or install without the GUI:
   sudo installer -pkg ~/Downloads/Looper-<version>-macos-universal.pkg -target /
   ```
3. *Customize* lets you leave out the VST3, the Audio Unit, the standalone app or the factory patches:
   - VST3 -> `/Library/Audio/Plug-Ins/VST3/Looper.vst3`
   - Audio Unit -> `/Library/Audio/Plug-Ins/Components/Looper.component`
   - Standalone -> `/Applications/Looper.app`
   - Factory patches -> `/Library/Application Support/Loop Audio Lab/Looper/Factory`
4. Restart your DAW or rescan (Logic Pro: Settings -> Plug-in Manager -> select Looper ->
   **Reset & Rescan Selection**). The installer already removes the quarantine flag from the
   installed plug-ins; if a DAW still refuses to load Looper, run
   `sudo xattr -dr com.apple.quarantine /Library/Audio/Plug-Ins/Components/Looper.component /Library/Audio/Plug-Ins/VST3/Looper.vst3 /Applications/Looper.app`.

Manual install from the zips (ad-hoc signed, not notarized; `INSTALL-macOS.txt` has the same steps):

```bash
mkdir -p ~/Library/Audio/Plug-Ins/VST3 ~/Library/Audio/Plug-Ins/Components
cp -R Looper.vst3 ~/Library/Audio/Plug-Ins/VST3/
cp -R Looper.component ~/Library/Audio/Plug-Ins/Components/
xattr -dr com.apple.quarantine ~/Library/Audio/Plug-Ins/VST3/Looper.vst3
xattr -dr com.apple.quarantine ~/Library/Audio/Plug-Ins/Components/Looper.component
killall -9 AudioComponentRegistrar 2>/dev/null || true
# factory patches (optional)
mkdir -p ~/Library/"Application Support"/"Loop Audio Lab"/Looper
unzip Looper-<version>-factory-content.zip -d ~/Library/"Application Support"/"Loop Audio Lab"/Looper/
```

Uninstall: `sudo rm -rf /Library/Audio/Plug-Ins/VST3/Looper.vst3 /Library/Audio/Plug-Ins/Components/Looper.component /Applications/Looper.app "/Library/Application Support/Loop Audio Lab/Looper"`.

## Why the security warnings?

Looper is in beta and the builds are **not code-signed** yet: there is no Windows Authenticode
certificate and no Apple Developer ID / notarization. Windows SmartScreen and macOS Gatekeeper
therefore warn about an "unknown publisher" / "unidentified developer". The steps above are the
standard way to open unsigned software. You can check that a download is intact with
`SHA256SUMS.txt` (`sha256sum -c SHA256SUMS.txt` on Linux, `shasum -a 256 <file>` on macOS,
`certutil -hashfile <file> SHA256` on Windows).

## Feedback and bugs

Open an issue in this repository. Please include the line from **Settings -> About -> Copy
version info**, your OS and DAW.

## Licence

Copyright (c) 2026 Loop Audio Lab. All rights reserved. Use of Looper is governed by the
[Looper Beta End User Licence Agreement](EULA.md). Looper uses the JUCE framework under the
JUCE licence and other third-party components listed in [THIRD-PARTY-NOTICES.md](THIRD-PARTY-NOTICES.md)
and in the About panel (Settings -> About).
