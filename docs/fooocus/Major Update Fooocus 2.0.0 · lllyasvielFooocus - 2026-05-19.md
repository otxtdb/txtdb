---
title: "[重大更新] Fooocus 2.0.0"
source: "https://github.com/lllyasviel/Fooocus/discussions/347"
author:
published:
created: 2026-05-19
description: "[Major Update] Fooocus 2.0.0"
tags:
  - "clippings"
taxonomy: { doc_category: [fooocus] }
---
Fooocus 最近完全重写了文本处理引擎，因此版本直接更新至 2.0.0。

1. 新的文本特征处理引擎现已支持多种风格。根据我们的测试，使用多种风格通常能提升图像质量。
2. 在 100 次测试（由 ChatGPT 生成的 100 个提示词）中，V2 默认结果在两位人类评估者的评判下，有 87 次优于 V1 默认结果。
3. 在 100 次测试（由 ChatGPT 生成的 100 个提示词）中，V2 的提示词理解能力在两位人类评估者的评判下，于默认设置及单/多风格模式下，有 81 次优于 V1 的提示词理解能力。
4. 由于上述数据均超过 80%，我们将此版本视为重大更新，并直接将其版本号定为 2.0.0。

Tips:

1. “提示词扩展与原始模式”在风格选项中已更名为"Fooocus V2"。
2. （在大多数情况下）您可以通过在风格选项中关闭"Fooocus V2"来重现之前的 V1 结果（或 V1.0.4 原始结果）。
3. `cinematic-default` 已重命名为 `Default (Slightly Cinematic)` ，该风格的內容保持不变。
4. 所有风格名称均已标准化为空格驼峰式命名，以优化用户界面显示。