# Framora

[中文版 README](README.md)

![Framora video creation interface](assets/screenshots/framora-video-create.png)

**Framora** is a desktop AI video creation app for macOS and Windows, built for short-video creators, AI video experimenters, and content teams.

Everything you need lives in one app:

- **AI video generation**: turn prompts or reference images into short videos with mainstream models such as Sora, Veo, Grok, and Seedance;
- **AI workflows**: orchestrate "script → storyboard → image → video → composition" pipelines on a node canvas;
- **Video editing**: canvas plus multi-track timeline for combining video, audio, images, stickers, and subtitles, with local export;
- **Image editing**: inpainting, cleanup, background replacement, upscaling, multi-image fusion, text-to-image, and more on an infinite canvas;
- **Local-first**: all settings and generated assets are encrypted and stored on your own machine. There is no backend server, and nothing is uploaded.

---

## Table of Contents

- [Downloads](#downloads)
- [Installation Guide (Important)](#installation-guide-important)
- [First Run: Get and Configure Your API Key](#first-run-get-and-configure-your-api-key)
- [Global Settings](#global-settings)
- [Pages and Features](#pages-and-features)
- [Disclaimer](#disclaimer)
- [Security and Privacy](#security-and-privacy)

---

## Downloads

Open [GitHub Releases](https://github.com/yanquankun/framora-releases/releases/latest) and pick the installer that matches your device:

| Platform | Device | Installer |
| --- | --- | --- |
| Windows x64 | Windows 10/11 PCs | `Framora-<version>-windows-x64.exe` |
| macOS Apple Silicon | M1 / M2 / M3 / M4 Macs | `Framora-<version>-mac-arm64.dmg` |
| macOS Intel | Intel-based Macs | `Framora-<version>-mac-x64.dmg` |

> Not sure which chip your Mac has? Click the Apple menu → "About This Mac". If the Chip line says Apple M-series, use the Apple Silicon build; if it says Intel, use the Intel build.

---

## Installation Guide (Important)

Current builds are **not yet notarized by Apple or code-signed on Windows** (developer certificates are costly for an indie project; official releases will add them later). Your OS will therefore show a security warning on first launch. This is the standard gate for all unsigned apps — **it does not mean the app is unsafe**. Follow the steps below to proceed.

### macOS

1. Open the downloaded `.dmg` and drag `Framora.app` into the Applications folder.
2. On first launch, if you see "Framora cannot be opened because it is from an unidentified developer":
   - **Right-click (or Control-click) Framora → Open** in the Applications folder, then click "Open" in the dialog;
   - or go to **System Settings → Privacy & Security**, find the blocked Framora entry at the bottom, and click "**Open Anyway**".
3. If you see "Framora is damaged and can't be opened" (common on recent macOS versions), run this command in Terminal and launch again:

```bash
xattr -cr /Applications/Framora.app
```

> This removes the quarantine flag macOS attaches to downloaded files. It does not modify the app itself.

### Windows

1. Double-click the downloaded `.exe` installer.
2. If the blue "Windows protected your PC" (SmartScreen) dialog appears:
   - click "**More info**";
   - then click "**Run anyway**".
3. Complete the setup wizard (custom install location supported) and launch Framora from the desktop or Start menu.

### Notes

- **Only download installers from this repository's GitHub Releases page.** Avoid third-party mirrors to eliminate the risk of tampered binaries.
- ffmpeg and the speech-recognition runtime are bundled. **No extra dependencies are required.**
- The app checks for updates and shows a hint in the title bar when a new version is available.

---

## First Run: Get and Configure Your API Key

Framora does not ship model capacity itself. Generation runs through an **OpenAI-compatible API relay service**, so you need an API key from a relay provider.

### Get an API key

1. Open your relay provider console (the default supported provider is `https://s.lconai.com`).
2. Sign up or sign in.
3. Create or copy your API key (usually starts with `sk-`).

### Configure it in the app

1. Launch Framora. **If no API key is configured, the Settings window opens automatically on the API tab** (you can also open it anytime via the gear button on the right of the title bar).
2. Paste your key into the "API Key" field.
3. Keep the default base URL `https://s.lconai.com`, or change it if you use another OpenAI-compatible provider.
4. Click Save and return to the main window.

![API settings](assets/screenshots/framora-settings-api.png)

> **About key safety**: your key is encrypted and stored locally (see [Security and Privacy](#security-and-privacy)) and is only used to call the provider endpoint you configured. Never share your key, and keep it out of screenshots, public repos, and logs.

---

## Global Settings

Click the **gear button** on the right of the title bar to open the Settings window. It has eight tabs.

### General

App version, platform, runtime mode, and interface language (中文 / English). Language changes sync to the main window instantly.

![General settings](assets/screenshots/framora-settings-general.png)

### API

API key and base URL, encrypted at rest and applied immediately (see [First Run](#first-run-get-and-configure-your-api-key)).

### Models

A read-only, **live** overview of the models available from your relay provider, grouped by capability (video / image / chat) with vendor and pricing. Data is fetched in real time and never persisted locally; manual refresh supported.

![Models overview](assets/screenshots/framora-settings-models.png)

### Skills

Manage local prompt-enhancement packs following the Claude Skill spec. Ships with short-video-script and video-prompt skills; you can import your own and grant them per-surface permissions (workflow chat, prompt assistant, and so on).

![Skills](assets/screenshots/framora-settings-skills.png)

### MCP

Expose Framora's capabilities (video generation, asset queries, workflows, publishing) as a local MCP server for AI tools such as Claude or Cursor. Fine-grained permission groups (read / generate / file / publish) with a built-in self-check. Disabled by default.

### Theme

Light, dark, duck, sketch, and several stylized themes, plus follow-system. Theme changes sync to the main window instantly.

![Theme settings](assets/screenshots/framora-settings-theme.png)

### Storage

View and migrate the data directory (contents are fully migrated when you change location), and set a unified download directory used by video generation, workflows, and editor exports.

![Storage settings](assets/screenshots/framora-settings-storage.png)

### Cache

Per-category disk usage (generated videos, editor assets, workflow outputs, image-editor sessions, logs) with per-category or one-click full cleanup. Clearing cache removes files only — **your API key and workflow configurations are never touched**.

![Cache management](assets/screenshots/framora-settings-cache.png)

---

## Pages and Features

### Video Creation

The home page generates AI videos fast:

- Describe characters, scenes, motion, camera work, and style in the prompt; optionally attach reference images for image-to-video;
- Pick a model and aspect ratio (e.g. vertical `720x1280`); the model list and prices come live from your provider;
- Built-in **prompt checker** (subject / motion / camera / style / structure) and **prompt assistant** (rewrite, expand, compress, to-storyboard, to-English, stronger hook);
- The creative workspace turns trends, links, and notes into a three-beat storyboard;
- Tasks appear in the left list with progress, preview, details, and downloads; finished videos and thumbnails are saved locally.

### AI Workflow

Automate complex pipelines on a node canvas:

![AI workflow](assets/screenshots/framora-workflow.png)

- Nodes for text, prompt optimization, storyboard, image generation, video generation, composition, and publishing, wired together to pass text / image / video results;
- Start from templates (comic-video pipeline, image-to-video) or build from scratch;
- Independent nodes run **in parallel**; each node shows live status and progress;
- A built-in **AI assistant** panel helps with scripts, storyboards, and prompts;
- Workflows keep running **in the background** while you switch pages, and can resume from checkpoints after an app restart;
- Generated images and videos are archived into the workflow's own folder.

### Video Editor

Cut generated results and local footage into a finished piece:

![Video editor](assets/screenshots/framora-video-editor.png)

- Import local video / audio / image assets; files are **referenced in place**, never copied;
- Arrange position, size, and z-order on the canvas; hundreds of stickers included;
- Multi-track timeline with trimming, splitting, drag-arrange, volume control, and waveforms;
- Speech-to-subtitle with visual subtitle editing;
- Export runs on local ffmpeg (hardware encoding preferred) straight into your download directory — nothing goes through a server;
- Moved or deleted source files show a clear "missing" badge instead of failing silently.

### Image Editor

An infinite-canvas AI image workbench:

![Image editor](assets/screenshots/framora-image-editor.png)

- Upload one or more images and pan/zoom freely;
- Capabilities include **inpainting, cleanup, text replacement, full-image rewrite, background replacement, smart cutout, upscaling, photo restoration, multi-image fusion, style transfer, and text-to-image**;
- Draw a selection box as the inpainting mask, or check multiple images as fusion/style references;
- Every result becomes a new layer for comparison and iteration, with single or batch download;
- Custom OpenAI-format image models supported (independent endpoint and key);
- Session history is saved automatically so you can pick up where you left off.

### Usage and Announcements

- The **billing button** in the title bar shows billing and API usage returned by your provider (fetched live, never stored);
- The **notification button** shows app announcements, usage tips, and service status notes.

---

## Disclaimer

By downloading and using Framora you acknowledge and agree to the following:

1. **The software is provided "as is"**, without warranties of any kind, express or implied, including fitness for a particular purpose or error-free operation. The developer is not liable for any direct or indirect damages arising from its use.
2. **Responsibility for AI-generated content.** All videos, images, and text are produced by the third-party AI models you configure. Users are solely responsible for judging and bearing the legality, accuracy, and copyright status of generated results. Do not use this software to create illegal, infringing, deceptive, or harmful content.
3. **Comply with laws and platform terms.** Follow the laws of your jurisdiction and the terms of the model providers and publishing platforms you use. Before publishing generated content to third-party platforms, make sure it complies with their rules, including AI-content labeling requirements.
4. **No affiliation.** This project is not affiliated with OpenAI, Google, xAI, or any model vendor or relay provider. Sora, Veo, Grok, and other names and trademarks belong to their respective owners; the app merely calls the APIs you configure.
5. **API costs.** Model usage fees are settled between you and your relay provider and are unrelated to this software. Understand your provider's pricing and keep your account and key safe.
6. **Service availability.** Endpoint availability, model listings, and pricing are controlled by the provider. No guarantees are made by this software.

## Security and Privacy

Framora is built **local-first**. Our commitments:

### We never store or upload your credentials

- The app has **no backend server and no account system** — there is nothing to sign up for and no "Framora login";
- Your **API key is encrypted and stored only on your own machine**, used solely to call the provider endpoint you configured. It is **never sent to the developer or any third-party server**;
- The developer **cannot see or recover** your key. Keep it safe.

### Local data encryption

- API keys and settings are encrypted with **AES-256-GCM**; the master key is protected by OS-level security (macOS Keychain / Windows DPAPI), so copied config files cannot be decrypted elsewhere;
- Generated videos, images, workflow outputs, and editor assets stay in the local data directory, which you can inspect and migrate in Settings → Storage;
- Imported local files are **referenced in place**, not copied;
- Clearing cache removes file resources only and never touches your key or core settings.

### Network access scope

While running, the app only talks to:

| Target | Purpose |
| --- | --- |
| Your configured relay endpoint | Model list / video, image, text generation / billing queries |
| GitHub (this repository) | Update checks |
| Anonymous error diagnostics | Crash and error logs only, to improve stability; **never includes API keys, prompts, generated content, media files, or personal information** |
| Publishing platforms you explicitly bind | Only after you use the publish feature and complete authorization |

### Recommendations

- Download installers only from the official Releases page and verify file names;
- Never expose your full API key in screenshots, recordings, or public repositories;
- If you suspect a leak, reset the key in your provider console immediately.

---

*Screenshots are for illustration; personally identifiable parts are pixelated. The actual UI may differ in newer versions.*
