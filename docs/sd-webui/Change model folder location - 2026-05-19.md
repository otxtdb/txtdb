---
title: "更改模型文件夹位置"
source: "https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Change-model-folder-location"
author:
published:
created: 2026-05-19
description: "Stable Diffusion web UI. Contribute to AUTOMATIC1111/stable-diffusion-webui development by creating an account on GitHub."
tags:
  - "clippings"
taxonomy: { doc_category: [sd-webui] }
---
有时将模型移动到另一个位置可能很有用。原因可能包括：

- 主磁盘空间不足
- 您正在多个工具中使用模型，不希望重复存储它们

默认模型文件夹位于 `stable-diffusion-webui/models`

## macOS 访达

- 在访达中打开两个窗口，例如 `stable-diffusion-webui/models/Stable-diffusion` 和存放模型的文件夹。
- 从模型文件夹拖拽模型到目标文件夹时，按住 option ⌥ + command ⌘
- 这将创建快捷方式而非移动模型

## 命令行

- 假设您的模型 `openjourney-v4.ckpt` 存储在 `~/ai/models/`
- 现在，我们为此模型创建一个符号链接（即别名）
- 打开终端并导航至您的 Stable Diffusion 模型文件夹，例如 `cd ~/stable-diffusion-webui/models/Stable-diffusion`
- 为您的模型创建符号链接至 `ln -sf  ~/ai/models/openjourney-v4.ckpt`