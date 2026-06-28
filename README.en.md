# Framora

[Chinese README](README.md)

![Framora video creation interface](assets/screenshots/framora-video-create.png)

Framora is a desktop AI video creation app for creators, AI video experiments, and content teams. It helps you move from prompt planning to AI video generation, local editing, image editing, and workflow orchestration.

## Downloads

Open [GitHub Releases](https://github.com/yanquankun/framora-releases/releases/latest) and choose the installer that matches your device:

| Platform | Device | Download |
| --- | --- | --- |
| Windows | Windows 10/11 PCs | Windows x64 package |
| macOS Apple Silicon | M1 / M2 / M3 / M4 Macs | macOS Apple Silicon package |
| macOS Intel | Intel-based Macs | macOS Intel package |

## First Run: Account And API Key

Framora uses an OpenAI-compatible API service for video, image, and text generation. The default service endpoint is `https://s.lconai.com`.

1. Open your API provider console, for example `https://s.lconai.com`.
2. Create an account or sign in.
3. Create or copy your API Key.
4. Launch Framora. If no API Key is configured, the Settings window opens automatically.
5. Open the API tab and paste your API Key.
6. Keep the default base URL `https://s.lconai.com` unless your provider gives you another endpoint.
7. Save and return to the main window.

Your API Key is encrypted and stored locally. Do not share it in public repositories, screenshots, logs, or chat messages.

## Pages And Features

### Video Creation

- Generate videos from prompts and optional reference images.
- Select model, starting mode, and output size such as vertical `720x1280`.
- Use the creative workspace to organize inspiration, links, notes, and three-part storyboards.
- Track generated videos in the left task list, preview results, open details, and download files.

### Creative Workspace

- Collect trend notes, references, links, and material descriptions.
- Split ideas into hook, development, and reversal scenes.
- Prepare publishing copy and compare model choices.

### Video Editor

- Import local media, arrange clips on the canvas and timeline, and combine video, audio, images, and stickers.
- Export locally through desktop ffmpeg.
- Missing local files are marked clearly instead of silently rendering blank content.

### AI Workflow

- Build node-based pipelines for text, storyboards, images, videos, composition, and publishing.
- Run nodes with visible progress and error states.
- Generated assets are archived into the workflow folder.
- Workflows can keep running while you switch pages.

### Image Editor

- Upload one or more images to an infinite canvas.
- Use inpainting, cleanup, full-image rewrite, background replacement, cutout, upscaling, photo restoration, image fusion, style transfer, and text-to-image.
- Keep each result as a new layer for comparison and iteration.
- Download single images or batches.

### Settings

- General: version, platform, mode, and language.
- API: API Key and base URL.
- Models: available models, capabilities, prices, and sync status.
- Theme: switch visual themes.
- Storage: data directory and download directory.
- Cache: review storage usage and clear cached files.

### Usage Records

Use the title-bar usage entry to check billing and API usage records. If the API Key is missing or invalid, Framora will guide you back to Settings.

### Announcements

Use the notification button in the title bar to read app announcements, model notes, pricing tips, or service messages.

### Local Data And Privacy

- Settings and API credentials are encrypted and stored locally.
- Generated media, workflow outputs, and editor assets are stored in the local data directory.
- Imported local files are referenced in place when possible.
- Clearing cache removes generated file resources but keeps API credentials and core settings.
