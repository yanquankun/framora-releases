# Framora Releases

[中文](#中文) | [English](#english)

This repository hosts public release metadata, release notes, and download pages for Framora.

![Framora video creation screen](assets/screenshots/framora-video-create.png)

## 中文

Framora（帧序）是一个面向视频创作的桌面应用，当前重点覆盖 AI 视频生成、视频编辑、工作流编排、图片编辑与本地素材管理。

### 当前定位

- AI 视频生成：通过文本提示词与参考图片生成视频，并展示任务状态。
- 浏览器内编辑：提供时间轴、画布与导出能力，用于基础视频编辑。
- 创意工作流：支持以节点方式组织灵感、分镜、素材读取与发布联动。
- 本地桌面体验：基于 Electron 分发，生成结果、素材与设置保存在本机。

### 下载与更新

最新版本入口：[GitHub Releases](https://github.com/yanquankun/framora-releases/releases/latest)

应用内更新检查读取本仓库根目录的 [`latest.json`](latest.json)。当远程版本高于本地版本时，Framora 标题栏会显示“更新”按钮；点击后打开 GitHub 的最新发布页。本仓库不保存源码，只保存面向用户可公开访问的发布信息与下载入口。

### 截图

![Framora 视频创建界面](assets/screenshots/framora-video-create.png)

### 版本清单

```json
{
  "version": "0.0.2",
  "releaseUrl": "https://github.com/yanquankun/framora-releases/releases/tag/v0.0.2",
  "latestUrl": "https://github.com/yanquankun/framora-releases/releases/latest"
}
```

### 后续文档占位

后续可以继续在这里补充：

- 安装说明
- 功能介绍
- 常见问题
- 隐私与本地数据说明
- 版本变更记录

<details>
<summary>English</summary>

## English

Framora is a desktop video creation app focused on AI video generation, browser-based editing, workflow orchestration, image editing, and local media management.

### Product Scope

- AI video generation: create videos from text prompts and optional reference images, with task status feedback.
- In-browser editing: use a timeline, canvas, and export flow for basic video editing.
- Creative workflows: organize inspiration, storyboards, local media, and publishing steps through workflow nodes.
- Desktop-first storage: distributed through Electron, with generated media, assets, and settings stored locally.

### Downloads And Updates

Latest release page: [GitHub Releases](https://github.com/yanquankun/framora-releases/releases/latest)

The app checks the public [`latest.json`](latest.json) file in this repository. When the remote version is newer than the local app version, Framora shows an "Update" button in the title bar. Clicking the button opens the latest GitHub release page. This repository does not contain source code; it only hosts public release metadata and download entry points.

### Screenshot

![Framora video creation screen](assets/screenshots/framora-video-create.png)

### Release Manifest

```json
{
  "version": "0.0.2",
  "releaseUrl": "https://github.com/yanquankun/framora-releases/releases/tag/v0.0.2",
  "latestUrl": "https://github.com/yanquankun/framora-releases/releases/latest"
}
```

### Future Documentation

This README can later be expanded with:

- Installation guide
- Feature overview
- FAQ
- Privacy and local data notes
- Changelog

</details>
