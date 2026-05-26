---
title: "Fooocus 2.1.0 图像提示（Midjourney 图像提示）"
source: "https://github.com/lllyasviel/Fooocus/discussions/557"
author:
published: 2024-05-18
created: 2026-05-19
description: "Fooocus 2.1.0 Image Prompts (Midjourney Image Prompts)"
tags:
  - "clippings"
taxonomy: { doc_category: [fooocus] }
---
Fooocus 2.1.0 已完成图像提示功能的实现。由于在这个版本之后，几乎包含了 Midjourney 的所有功能，因此版本直接跳到了 2.1.0。

图像提示是 Midjourney 最重要的功能之一。以下是 Midjourney 的横幅：

在 Fooocus 中，它看起来是这样的：

从技术上讲，这个功能基于 IP-Adapter 的混合，Fooocus 团队预先计算出的负嵌入，Fooocus 团队开发的一种注意力破解算法，以及 Fooocus 团队开发的自适应平衡/加权算法。

这些努力的动力是为了与 Midjourney 图像提示达到最佳匹配。在其他软件如 A1111/ComfyUI/InvokeAI 中，IP-Adapter 仍然存在一些开放性问题，例如忽略文本提示，或在使用多张图像时结果过度烧录。这些问题在 Fooocus 中得到了解决，用户可以享受类似 Midjourney 的图像提示体验。

详细差异如下表所示：

|  | Midjourney 图像提示 | IP-Adapter + A1111/ComfyUI/InvokeAI | Fooocus 图像提示 |
| --- | --- | --- | --- |
| 与文本提示一起工作 | 文本提示和图像提示将被混合 | 倾向于忽略文本提示 | 文本提示和图像提示将被混合 |
| 使用多张图像作为输入 | 对于多张图像输入，结果质量不会下降 | 使用更多图像会导致结果质量变差 | 结果质量不会因多个图像输入而下降 |
| 当方法失败（单个图像输入） | 给出不相关但仍然高质量的图像 | 给出相关但低质量且过度曝光的图像 | 给出不相关但仍然高质量的图像 |
| 当方法失败时（多个图像输入） | 部分忽略它无法理解的图像，仍然给出高质量的结果 | 给出相关但低质量且过度曝光的图像 | 部分忽略它无法理解的图像，仍然能给出高质量的结果 |
| 质量影响 | 使用图像提示不会影响输出质量 | 使用图像提示会影响基础模型的质量 | 使用图像提示不会影响输出质量，几乎不 |
| 结果多样性 | 使用图像提示后，结果仍然多样 | 结果倾向于具有小而最小化的变化 | 使用图像提示后结果仍然多样 |

**使用此方法首次会下载 2.5GB 文件！**

## 示例：无文本提示的单图像提示

（非精选随机批次，默认参数，调整后实际结果应更好）

(seed 1234, [这里是有图片](https://github.com/lllyasviel/Fooocus/assets/19834515/3a8aaf95-d37e-440a-83eb-e8d80fb066bb) )

（此示例使用默认风格和 Fooocus V2 风格）

## 示例：带文本提示的单图提示

请注意，在 ComfyUI/A1111 中混合文本和 IP-Adapter 非常困难。Fooocus 没有这个问题。

（非精选随机批次，默认参数，如果调整，实际结果应该会更好）

（此示例使用默认风格和 Fooocus V2 风格）

## 示例：无文本提示的多个图像

请注意，在 ComfyUI/A1111 中混合多个 IP-Adapters 可能会导致结果质量降低。使用 Fooocus 可以在一定程度上解决这个问题。

（非精选随机批次，默认参数，如果调整则实际结果应该会更好）

（此示例使用默认风格和 Fooocus V2 风格）

## 示例：带文本提示的多个图像，甚至多种风格

在 A1111/ComfyUI 中几乎不可能实现，因为 ComfyUI/A1111 中混合文本和 IP-Adapter 非常困难，而混合多个 IP-Adapter 很可能导致 ComfyUI/A1111 的结果质量降低。

（非精选随机批次，默认参数，如果调整参数，实际结果应该会更好）

这张图片太复杂，所以我在这里做了标注：

混合太多元素导致难以辨认，但所有元素都在那里，没有失败或导致质量下降，这与 ComfyUI/A1111/InvokeAI 不同。

## Fooocus 图像提示（高级）

如果你选择“高级”，你将能够使用两种结构控制：

**PyraCanny**: 基于金字塔的 Canny 边缘控制。原因是 SDXL 使用 1024px 图像，而标准 Canny 有时会错过一些高分辨率图像的细节。这种方法使用多种分辨率来检测 Canny 边缘，然后柔和地组合它们，从而捕捉到比 Canny 更多的结构。金字塔部分来自 [“Edge Drawing: A combined real-time edge and segment detector”](https://www.sciencedirect.com/science/article/pii/S1047320312000831) 。使用它时，您将下载 350MB 的控制模型。

**CPDS**: 来自 [“Contrast Preserving Decolorization (CPD)”](http://www.cse.cuhk.edu.hk/leojia/projects/color2gray/index.html) 的结构提取算法。“CPDS”代表 CPD 结构。控制模型由 Fooocus 团队修改——它始于 SAI 的深度控制-lora。使用这种方法的原因是速度快且无需下载预处理器。请注意，我们仅使用图像的结构部分，它并非真正的“去色”。使用它时，您将下载 350MB 的控制模型。

（非随机挑选的批量，默认参数，实际结果如果调整会更好）

（此示例使用默认风格和 Fooocus V2 风格）

（此示例使用默认风格和 Fooocus V2 风格）

（此示例使用默认风格和 Fooocus V2 风格）

### For developers:

在开发者调试模式下，如果你清楚自己在做什么并且确实需要这些功能（去噪强度也可以在开发者模式下设置），你可以将 upscale/vary/inpaint 与上述所有功能混合使用。你也可以通过检查“调试预处理”来获取预处理结果。

但请记住：

如果你在 Fooocus 中通过大量调整高级参数意外得到了满意的结果，你应该尝试复制你的正面提示，重新打开 Fooocus，不做任何更改，然后粘贴提示。你会发现结果会更好，而且所有这些调整都是不必要的。（唯一的例外可能是更改“高级”中的基础模型。）