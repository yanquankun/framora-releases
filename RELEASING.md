# Release Upload Guide

This document is for maintainers. The public `README.md` should stay user-facing and should not describe internal update logic.

## Recommended Command

From the private source repository, run:

```bash
pnpm release:github
```

The command shows the current `package.json` version, asks for the target version, asks for Chinese and English release notes, builds the three platform installers, uploads only installer assets, and updates `latest.json`.

## Required Installer Assets

Every public release should upload these three platform-specific packages:

| Platform | Suggested asset label | Typical file |
| --- | --- | --- |
| Windows | `Windows x64` | `Framora-<version>-windows-x64.exe` or `.zip` |
| macOS Apple Silicon | `macOS Apple Silicon` | `Framora-<version>-mac-arm64.dmg` |
| macOS Intel | `macOS Intel` | `Framora-<version>-mac-x64.dmg` |

Do not upload `.blockmap` files as user-facing installers. They are update metadata, not installable packages.

## Manual Build Commands

From the private source repository:

```bash
pnpm dist:win:x64
pnpm dist:mac:arm64
pnpm dist:mac:x64
```

Use the actual files generated under `release/`. If needed, copy or rename them into clear platform names before upload.

## Upload Command

`gh release upload` supports display labels by appending `#Label` after the file path.

```bash
gh release upload v0.0.2 \
  "release/Framora-0.0.2-windows-x64.exe#Windows x64" \
  "release/Framora-0.0.2-mac-arm64.dmg#macOS Apple Silicon" \
  "release/Framora-0.0.2-mac-x64.dmg#macOS Intel" \
  --repo yanquankun/framora-releases \
  --clobber
```

If a release does not yet have all three real installer files, keep the missing platform listed as pending in the release notes. Do not upload placeholder files.

Do not upload source archives manually. The release should only attach the user-facing installer assets listed above.
