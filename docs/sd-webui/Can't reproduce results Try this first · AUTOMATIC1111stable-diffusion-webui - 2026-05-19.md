---
title: "无法复现结果？请先尝试此方法"
source: "https://github.com/AUTOMATIC1111/stable-diffusion-webui/discussions/13093"
author:
published:
created: 2026-05-19
description: "Can't reproduce results? Try this first"
tags:
  - "clippings"
taxonomy: { doc_category: [sd-webui] }
---
当人们表示无法生成相同的结果时，他们（有时含糊地）主要指的是以下两点：  
\- 将之前生成的精确图像作为基准或合理性检查进行复现  
\- 复现之前相同的整体像素质量和/或提示词准确度

如果您遇到上述任一情况，请检查或记住以下几点：

检查您的基本设置：采样器、步数、CFG、Clip Skip、分辨率、检查点等。

[![image](https://private-user-images.githubusercontent.com/66507343/265919002-33eb985a-8f18-420d-98e9-7192cf9deb8a.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzkyMDYxMDYsIm5iZiI6MTc3OTIwNTgwNiwicGF0aCI6Ii82NjUwNzM0My8yNjU5MTkwMDItMzNlYjk4NWEtOGYxOC00MjBkLTk4ZTktNzE5MmNmOWRlYjhhLnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNjA1MTklMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjYwNTE5VDE1NTAwNlomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPWE0NWZiMzFkOTIzMjYxNjJhN2E1YWI3NmI2MjM0ZDMyNzExMGQwY2I0MmNiZWFhMTBiZTI4MjZmNjU2ODEzYzYmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JnJlc3BvbnNlLWNvbnRlbnQtdHlwZT1pbWFnZSUyRnBuZyJ9.LcEVP2RSWYdhi8VjVxrTIopa9qbyZHwREmt84SDAUj0)](https://private-user-images.githubusercontent.com/66507343/265919002-33eb985a-8f18-420d-98e9-7192cf9deb8a.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzkyMDYxMDYsIm5iZiI6MTc3OTIwNTgwNiwicGF0aCI6Ii82NjUwNzM0My8yNjU5MTkwMDItMzNlYjk4NWEtOGYxOC00MjBkLTk4ZTktNzE5MmNmOWRlYjhhLnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNjA1MTklMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjYwNTE5VDE1NTAwNlomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPWE0NWZiMzFkOTIzMjYxNjJhN2E1YWI3NmI2MjM0ZDMyNzExMGQwY2I0MmNiZWFhMTBiZTI4MjZmNjU2ODEzYzYmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JnJlc3BvbnNlLWNvbnRlbnQtdHlwZT1pbWFnZSUyRnBuZyJ9.LcEVP2RSWYdhi8VjVxrTIopa9qbyZHwREmt84SDAUj0)

检查您是否在“额外”复选框部分使用了选项检查您是否使用了高分辨率修复及其特定设置：分辨率、放大倍数或放大至尺寸等。

请记住启用高分辨率修复的新方法：如果下拉菜单/手风琴展开 = 已启用，如果收缩 = 已禁用。

检查 Upscale 是否未在高解析度修复中因低去噪而回退到潜在空间。检查您的提示词，诸如： `word, word:1.9, meme prompt engineering (1:999:6969)` 等提示词在更新前可能以某种方式被奇迹般地正确解析，但现在可能会导致过度处理。尝试使用较低的权重或完全不使用。

在“设置 > 兼容性”中检查 `Use old emphasis implementation. Can be useful to reproduce old seeds.` 以重现旧的提示风格，这仍可能对这类提示有所帮助。

同时检查那里的其他兼容性设置。  检查您的负面提示词，与上述相同。

检查您的提示词是否使用了嵌入模型（embeddings），并确认它们仍位于 embeddings 文件夹中。

检查您的提示词是否使用了超网络（hypernetworks），并确认它们仍位于 models/hypernetworks 文件夹中。

检查您的提示词是否使用了 LoRA，并确认它们仍位于 models/Lora 文件夹或 models/Lycoris 文件夹中。

检查并尝试使用内置的 LoRA/Lycoris/Loha 等支持功能，而非依赖扩展程序。使用内置支持时，您可以将所有类型的 LoRA 放在同一个 LoRA 文件夹中，并使用 `<lora:name:strength>` 进行添加，无需区分类型。

请尝试使用内置的 LoRA 支持功能，或您之前使用的任意扩展程序。在“扩展”选项卡中禁用其中一项，然后测试哪种方式能为您提供所需的具体结果。如果使用内置的 LoRA 支持功能，请在“设置”中的“兼容性”部分检查此选项 ` Lora/Networks: use old method that takes longer when you have multiple Loras active and produces same results as kohya-ss/sd-webui-additional-networks extension` 。

检查您的 VAE 并确保其正确应用。将 VAE 文件放置于 models/VAE 目录中，并从下拉菜单中手动选择它们。在“设置”> "VAE"中检查选项，如果您不希望启用 TAESD 相关选项，请确认它们未被激活。您可以将上述任何选项添加到主界面，以便在“设置”> “用户界面”> “主界面 - txt2img 和 img2img 中的选项”中更快访问；请注意，您可以分别为这两个标签页设置独立的选项。

您还可以在此处添加“恢复人脸”和“平铺”选项。请重启用户界面以使更改生效。  在此处添加的任何选项都会显示在主要 txt2img 或 img2img 设置框中的 seed 下方。检查您的 launch.bat 中的启动参数，确认它们是否仍为您所需的配置。检查优化方法，以防其已更改。请注意，某些优化选项是非确定性的，这意味着您无论如何都会看到细微的变化。这取决于它们的版本，例如较新版本的 xformers 就可以防止这种情况发生。

检查是否存在之前使用过的其他优化选项。检查您的采样器参数，看看是否使用了非默认值，例如某些（可能已过时）指南（如 NAI 指南等）可能会建议的值。检查“设置”>“Stable Diffusion”中的选项。特别是这些选项检查您是否未使用额外的扩展：Adetailer、ControlNet、CFG 调度等。

检查您是否未使用注入额外提示的扩展程序：如通配符扩展、UmiAI、Stylepile、CloneCleaner、Model Keyword 等。

检查您的扩展程序是否未被启用或禁用。确认您不打算使用的扩展程序未被启用，并从扩展程序文件夹中删除它们以卸载。检查您的超分辨率选项检查您的 img2img 选项检查此页面：  
[https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Seed-breaking-changes](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Seed-breaking-changes)

最后一种方法是删除您的 venv 文件夹，让 launch.bat 重新创建它，以防是依赖问题。

此外，请注意 FP16 与 FP32 模型的区别，将图像上采样至 FP32 也可能改变图像效果。此处其他优化措施（？）或许也会产生影响。

[https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Optimizations](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Optimizations)

如果仍有问题？欢迎发帖讨论，但请务必提供您的提示词和设置参数，因为仅模糊地表示“遇到问题”很难推测您期望得到的结果。