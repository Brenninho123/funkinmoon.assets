# Moon-Assets

This repository contains the contents of the `assets` folder used by **Friday Night Funkin': Moon Engine** — textures, music, sounds, fonts, animations, and other game data required to run the engine.

Moon Engine is a Psych Engine-based fork of Friday Night Funkin' with mobile support, cross-platform builds, Polymod-based mod compatibility, and multiplayer mod synchronization. This repository is kept separate from the [engine source repository](https://github.com/Brenninho123/Funkin-Moon) so that asset history, binary diffs, and licensing can be tracked independently from code.

## Contents

| Folder | Description |
| --- | --- |
| `preload/` | Assets always loaded on startup: UI, fonts, shared sprites, credits data |
| `songs/` | Chart data, instrumental/vocal tracks and stage assets per song |
| `shared/` | Assets shared across multiple weeks/songs |
| `week1` – `week7`, `weekend1`, `sserafim` | Per-week/story content assets |
| `videos/` | Cutscenes and video content (not embedded by default) |
| `tutorial/` | Tutorial-specific assets |
| `fonts/` | Embedded font files |
| `locales/` | Localization strings for supported languages |

## Requirements

- Git with [Git LFS](https://git-lfs.com/) installed, since most binary assets (audio, video, large textures) are tracked via LFS
- Enough free disk space for a full checkout — audio and video assets make this repository significantly larger than the engine source repository

Clone with LFS enabled:

```
git lfs install
git clone https://github.com/Brenninho123/Moon-Assets.git assets
```

## Using with Moon Engine

This repository is meant to be placed at (or symlinked to) the `assets/` folder inside a Moon Engine checkout before running `lime test <platform>`. The engine's `project.hxp` reads from `assets/preload`, `assets/songs`, `assets/shared`, and the per-week folders listed above, and will fail to build if they are missing.

If you're setting up a fresh clone of the engine:

```
git clone https://github.com/Brenninho123/Funkin-Moon.git
cd Funkin-Moon
git clone https://github.com/Brenninho123/Moon-Assets.git assets
```

## Asset integrity and multiplayer mod sync

When `FEATURE_ASSET_INTEGRITY` is enabled, the engine hashes the contents of `preload/` and `shared/` at build time into `asset-manifest.json`, embedded into the build. This is used to detect corrupted or tampered assets, and — combined with the multiplayer mod compatibility system — to confirm host and client are running matching base assets before a multiplayer match starts.

## Licensing

This repository is subject to **different licensing** than the Moon Engine source code repository. Most assets (art, music, video) are © their original creators and are **not** covered by the source code's license (GPL/Apache, depending on the file). See [`LICENSE.md`](./LICENSE.md) for the full breakdown of what is and isn't redistributable, and under what terms.

If you plan to fork this repository for your own mod or engine, review the license carefully before redistributing — some assets are provided for engine functionality only and are not cleared for reuse in unrelated projects.

## Contributing

Asset contributions (new songs, UI art, localization files) should be opened as pull requests against this repository, not the engine source repository. Please keep binary diffs minimal — avoid re-exporting unchanged files, since this bloats LFS history.

## Related repositories

- [Funkin-Moon](https://github.com/Brenninho123/Funkin-Moon) — Moon Engine source code
