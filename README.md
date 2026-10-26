# Sprank Studio game data

Downloadable game content. This repository contains the content manifest; the complete data files are attached to [GitHub Releases](https://github.com/huann305/sprank-game-data/releases).

## Loading behavior

- Startup and Home download only `home.zip` (catalog, covers and lightweight previews).
- Menu music downloads separately in the background as `menu.zip`.
- Selecting a zone downloads only `zoneN.zip`. Other zone packages remain untouched.
- The Android app verifies the declared size and SHA256, installs the package atomically, and keeps it locally for offline use.
- Each process pins a manifest version. Publish packages first, then update the manifest.

## Current content

Version: `2026-10-26-v1`. Manifest schema: `1`.

32 zones, 640 mono instrumental loops. Each character has one fixed instrument. No shared backing track or vocals. The APK contains the app shell; game content is delivered separately.

The manifest records each archive URL, SHA256, compressed size, unpacked size and file count. Zone archives preserve `zones/zoneN/` paths; the Home package uses `home/` and `zones/index.json`; menu audio uses `menu/menu_music.flac`.

## Updating content

1. Build immutable ZIP packages under a new release tag.
2. Validate their metadata, checksums, paths and decoded audio.
3. Upload and publish every referenced release asset.
4. Update `manifest.json` on `main` after all package URLs are available.
5. Keep previous release assets available for existing installations.

This data repository does not contain Android source code, credentials, signing keys, or APKs.
