---
title: "如何切换不同版本的 WebUI"
source: "https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/How-to-switch-to-different-versions-of-WebUI"
author:
published:
created: 2026-05-19
description: "Stable Diffusion web UI. Contribute to AUTOMATIC1111/stable-diffusion-webui development by creating an account on GitHub."
tags:
  - "clippings"
taxonomy: { doc_category: [sd-webui] }
---
## 发布候选版本

发布候选版本是指即将作为新版本发布的稳定版。例如，在 1.7.0 正式发布之前，存在 1.7.0-RC 版本，这是一个发布候选版本——它包含所有新功能，并可供测试使用。

### 如何将现有安装切换到发布候选版本

请在 webui 目录中运行以下命令：

```actionscript
git switch release_candidate
git pull
```

### 如何在 master 分支切换回稳定版本：

在 webui 目录下运行以下命令：

```actionscript
git switch master
```

### 如何在新安装的 webui 中获取候选发布版

运行以下命令（这将创建一个名为 `webuirc` 的目录——您可以使用不同的名称，之后也可以重命名该目录）：

```bash
git clone https://github.com/AUTOMATIC1111/stable-diffusion-webui.git webuirc
cd webuirc
git switch release_candidate
```